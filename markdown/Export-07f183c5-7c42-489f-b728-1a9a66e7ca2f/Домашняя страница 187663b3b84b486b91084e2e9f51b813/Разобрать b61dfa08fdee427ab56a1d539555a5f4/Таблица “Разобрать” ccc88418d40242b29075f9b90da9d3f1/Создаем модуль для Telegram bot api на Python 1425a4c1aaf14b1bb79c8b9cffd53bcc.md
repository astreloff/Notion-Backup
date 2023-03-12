# Создаем модуль для Telegram bot api на Python

Date [HIDE]: October 2, 2022 8:11 AM
Без разбора: 160 дней
Добавлено: 02.10.2022
Разобрано: No
Ссылка: https://habr.com/ru/post/677456/
Темы: https://www.notion.so/Python-56ea1d4987c94572bc191d10854812ef

[%D0%A1%D0%BE%D0%B7%D0%B4%D0%B0%D0%B5%D0%BC%20%D0%BC%D0%BE%D0%B4%D1%83%D0%BB%D1%8C%20%D0%B4%D0%BB%D1%8F%20Telegram%20bot%20api%20%D0%BD%D0%B0%20Python%201425a4c1aaf14b1bb79c8b9cffd53bcc/Unknown%20file](%D0%A1%D0%BE%D0%B7%D0%B4%D0%B0%D0%B5%D0%BC%20%D0%BC%D0%BE%D0%B4%D1%83%D0%BB%D1%8C%20%D0%B4%D0%BB%D1%8F%20Telegram%20bot%20api%20%D0%BD%D0%B0%20Python%201425a4c1aaf14b1bb79c8b9cffd53bcc/Unknown%20file)

Привет! Я непрофессиональный разработчик, программирование - это мое хобби. И "подхобби" этого хобби - брать готовые инструменты и создавать их аналоги, просто, чтобы разобраться в интересной теме (а еще переделать всё по своему желанию :)). В этот раз, я решил закодить аналог для таких модулей как aiogram или асинхронная версия PyTelegramBotApi.

## Дисклеймер

В этой статье будет оочень много решений, которые вам покажутся странными, в моем коде будет очень много уязвимостей, проблем и т.д. Я плохо знаком с темой и не буду использовать свое решение в серьезных проектах. Поэтому, я буду очень рад, если вы уделите мне немного вашего времени и напишете об основных проблемах моего модуля в комментариях. В целом, ради этого я и пишу статью. Спасибо!)

## Проблема pyTelegramBotApi

До написания этой статьи, я некоторое время пользовался модулем pyTelegramBotApi, за это время, мне приходилось несколько раз залезать в его исходный код и я заметил деталь, которая мне совсем не понравилась - это многократное дублирование кода. Например, первая же функция process_updates, которая делит апдейты, полученные от телеграма на типы и запускает для каждого из них свою функцию process_..._updates, встречает нас вот таким:

```
new_messages = None
new_edited_messages = None
# Тут еще 11 таких же присвоений
chat_join_request = None

for update in updates:
    logger.debug('Processing updates: {0}'.format(update))
    if update.message:
        if new_messages is None: new_messages = []
        new_messages.append(update.message)
    if update.edited_message:
        if new_edited_messages is None: new_edited_messages = []
        new_edited_messages.append(update.edited_message)
    ... # Тут еще 11 таких же условий
    if update.chat_join_request:
        if chat_join_request is None: chat_join_request = []
        chat_join_request.append(update.chat_join_request)
if new_messages:
    await self.process_new_messages(new_messages)
if new_edited_messages:
    await self.process_new_edited_messages(new_edited_messages)
... # И тут еще 11 таких же условий
if chat_join_request:
    await self.process_chat_join_request(chat_join_request)
```

Кроме того, определение каждого метода, повторяющего методы Telegram Bot Api, выглядит так:

```
async def send_message(
        self, chat_id: Union[int, str], text: str,
        parse_mode: Optional[str]=None,
        entities: Optional[List[types.MessageEntity]]=None,
        disable_web_page_preview: Optional[bool]=None,
        disable_notification: Optional[bool]=None,
        protect_content: Optional[bool]=None,
        reply_to_message_id: Optional[int]=None,
        allow_sending_without_reply: Optional[bool]=None,
        reply_markup: Optional[REPLY_MARKUP_TYPES]=None,
        timeout: Optional[int]=None) -> types.Message:
```

Таким образом, внутри модуля содержится полная копия документации API, в том числе, в нем описаны все аргументы методов.

На мой взгляд это:

1. Бессмысленно.
2. Приводит к таким ситуациям, когда API был обновлен, а модуль еще нет - и разработчику модуля приходится реализовывать в нем ровно ту же логику, которая была добавлена в API. Я лично столкнулся с ситуацией, когда мне пришлось самому дописывать модуль, так как вышла новая версия api, и разработчик еще не успел его обновить.
3. И, если я не ошибаюсь, нарушает принцип DRY: именно потому, что одно изменение логики должно быть реализовано и в коде API, и в коде модуля.

## Задумка

Поэтому, я решил сделать свой модуль, который постараюсь лишить всех этих недостатков. Модуль этот должен быть "light" - то есть не должен содержать никакого дублирования работы API. И например, если кто-то захочет использовать метод API "sendHolography", модуль не должен этому препятствовать, так как это дублирование работы API, который все равно пришлет ошибку:

```
{"ok":false,"error_code":404,"description":"Not Found"}
```

Или не пришлет, если к этому моменту появятся голографические мониторы и с ними метод "sendHolography". А модуль, в отличии от pyTelegramBotApi будет автоматически готов к такому обновлению.

## Начинаем

Создаю класс Bot, он должен содержать все методы Telegram Bot Api, но чтобы модуль не зависел от актуального набора методов, определю метод __getattr__. Он должен возвращать некие объекты, вызов которых будет выполнять метод, это будет вложенная функция. Также, переименовываю её и преобразовываю в метод - чтобы все было красиво. И добавляю этот метод в кэш, чтобы не создавать его заново в следующий раз.

```
from types import MethodType
class Bot:
    def __init__(self):
        self.cache = {}

    def __getattr__(self, attr: str):
        if attr in cache: return self.cache[attr]

        url = "/bot"+self._token+"/"+snake_case_to_camel_case(attr)
      	async def function(bot, **kwargs):
          	pass
        method = MethodType(function, self)
        self.cache[attr] = method
        return method

```

Чтобы делать асинхронные get запросы, нужно создать объект aiohttp.ClientSession, однако если попытаться создать её в Bot.__init__, выйдет ошибка:

```
The object should be created within an async function
```

Сделать __init__ асинхронным тоже невозможно - асинхронная функция возвращает корутину, при создании объекта появляется ошибка:

```
TypeError: __init__() should return None, not 'coroutine'
```

Поэтому применю своего рода костыль - переопределю функцию Bot.__new__ как асинхронную, создам сессию в ней. В таком случае, вызвав __new__ при создании объекта, пользователь получит корутину, а потом, после await, вернется сам объект:

```
def __init__(self, token: str):
    self._http_exceptions = {}
    self._token = token
    self.cache = {}

async def __new__(cls, *args, **kwargs):
    obj = super().__new__(cls)
    obj._session = aiohttp.ClientSession(url)
    obj.__init__(*args, **kwargs)
    return obj
```

В предыдущем блоке кода вы можете заметить переменную _http_exceptions. Зачем она нужна? Я могу создать по классу исключения для каждого http кода ошибки, который отправляет telegram, но что если в telegram bot api добавятся новые методы, которые будут отправлять новые коды ошибок? Или, может быть, выйдет новая версия http, в которой будут добавлены новые коды ошибок? В таком случае, придется обновлять библиотеку! Есть решение лучше!)

```
class Bot:
		...
    def get_http_exception(self, number: int):
        if number in self._http_exceptions:
            return self._http_exceptions[number]
        else:
            HttpException = type(f"TelegramError{number}", (TelegramError,), {})
            self._http_exceptions[number] = HttpException
            return HttpException
```

Первый аргумент конструктора класса type - название класса, второй - кортеж классов, от которых создаваемый должен наследоваться, а третий - словарь атрибутов класса. Таким образом, если какая-то ошибка запрашивается в первый раз, для нее создается свой класс, наследующийся от TelegramError и сохраняется в словарь Bot._http_exceptions.

Теперь можно написать ту самую вложенную функцию, которая будет превращаться в разные методы и отправлять запросы на сервер.

```
async def function(bot, **kwargs):
  async with bot._session.get(url, params=kwargs) as response:
    response_data = await response.json()
    if response_data["ok"]:
        return response_data["result"]
    else:
        raise bot.get_http_exception(response_data["error_code"])(
          response_data["description"]
        )
```

Если получаю http ошибку - создаю нужное исключение и бросаю его.

Теперь нужно создать систему, которая будет постоянно запрашивать у сервера обновления, и, если они есть, запускать нужный обработчик сообщений. В PyTelegramBotApi выбор нужного обработчика реализован с помощью системы фильтров, например:

```
@bot.message_handler(commands=["start", help])
def handler1: ... #для команд /start и /help

@bot.message_handler(content_types=["photo"], chat_types=["private"])
def handler2: ... #для фотографий в личных чатах

@bot.message_handler(func=lambda msg: msg.from_user.id in admins)
def handler3: ... #для сообщений, отправители которых в списке админов.
```

Меня не устраивает этот подход по такой причине: допустим, мне нужно, чтобы один из обработчиков запускался только при получении сообщения, про которого в базе данных написано, что он админ или владелец. При этом работа самого обработчика должна зависеть от того, пользователь все таки админ или владелец. Получается, что мне нужно будет сделать два запроса к базе данных: один в фильтре, а другой в обработчике и это не эффективно. Да, можно разделить этот обработчик на два: один для сообщений от админов, а другой для сообщений от владельцев. Но тогда часть логики, общую для админов и владельцев придется выносить в отдельные функции, что не удобно.

Поэтому, я выбрал другой вариант. Пусть первым запускается первый определенный обработчик. В нем разработчик может добавить какое-то условие - и по нему выбрасывать исключение с названием NextHandler. В таком случае вызывается следующий обработчик. Если же обработчик выполняется без исключений, событие считается обработанным.

```
class NextHandler(Exception):
    def __init__(self):
        self.args = ("don't use this error outside of light_telegram_bot handler",)
```

```
class BotPolling:
    def __init__(self, bot, start_offset=0):
        self._handlers = []
        self._bot = bot
        self._offset = start_offset

    async def start(self, timeout=60, **kwargs):
        try:
            while 1:
                updates = await self._bot.get_updates(
                  	timeout=timeout,
                  	offset=self._offset,
                  	**kwargs
                )
                if updates:
                    self._offset = updates[-1]["update_id"]+1
                for update in updates:
                    for handler in self._handlers:
                        try:
                            await handler(update)
                        except NextHandler:
                            pass
                        else:
                            break
        except Exception:
            raise LightTelegramBotPollingError()

    def handler(self, f):
        self._handlers.append(f)
```

И вот, для сравнения, вот те же три обработчики в моем модуле:

```
@bot.handler()
def handler1(message):
	if not test_commands(message.text, ["start", "help"]):
  	raise NextHandler()

@bot.handler()
def handler2(message):
	if not ("photo" in message) and message.chat_type == "private"
  	raise NextHandler()

@bot.handler()
def handler3(message):
  if not msg["from_user"]["id"] in admins:
    raise NextHandler()
```

Да, получилось длиннее, но, зато, гораздо более универсально. Остается доделать несколько вещей, не заслуживающих упоминания. И вуаля!

Код модуля целиком вы можете посмотреть в репозитории [light_telegram_bot](https://github.com/Chebotarev-Alexey/light_telegram_bot), установить его можно с помощью pip install light_telegram_bot. Спасибо за прочтение статьи!