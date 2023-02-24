# NovelAI (NAI)

Стили: Anime

# **Описание**

Украденная модель из платного сервиса NovelAI для сочинения историй (аналог AI Dungeon), виртуального общения и генерации изображений по описанию. NovelAI дотренировывали на базе модели Stable Diffusion, используя арты и теги с Danbooru, но без имен художников (это пока очень деликатная тема с авторским правом и прочим).

- ❓ Управляется в первую очередь через негативные запросы, позволяющие убирать ненужные детали .
- Обучение проводилось на изображениях с Danbooru (тематика аниме, фурри, пони и т.п.).
- Обучение проводилось без указания имен художников (т.к. очень деликатная тема с авторским правом и прочим), поэтому управлять стилями через имена художников трудно.
- Хорошо справляется с анатомией, но однообразна в плане стиля.

# Примеры

![Untitled](NovelAI%20(NAI)%20fabe944debab4d6b9dda9d03cc90924c/Untitled.png)

# **Установка**

1. Установить сборку Stable Diffusion от AUTOMATIC1111 ([**Описание**](Stable%20Diffusion%208a76b17617194cd4aa42612ecbbb30ff.md)).
2. Скачать модель NovelAI (NSFW или SFW версию).
**Ссылка:** `magnet:?xt=urn:btih:5bde442da86265b670a3e5ea3163afad2c6f8ecc&dn=novelaileak`
3. Переименовать `model.ckpt` в папке `animefull-final-pruned` на `**любоеназвание**.ckpt`.
**Пример:** `novelai.ckpt`.
4. Переименовать `animevae.pt` на название которое мы дали предыдущему файлу и добавить в название `.vae.pt`.
**Пример:** `novelai.vae.pt`.
5. Создать папку `hypernetworks` в директории `\stable-diffusion-webui\models` и переместить в неё файлы `aini.pt`, `anime.pt`, `anime_2.pt` и т.д. из папки `modules`.
6. Перенести в папку `\models\Stable-diffusion\` с основными моделями ранее переименованный файл `novelai.ckpt` и файл `novelai.vae.pt`.
7. Запустить Stable Diffusion, выбрать модель `novelai.ckpt` и в настройках, в разделе "Stable Diffusion" выбрать finetune hypernetwork.

---

1. Установить WebUI от [Automatic1111](https://github.com/AUTOMATIC1111/stable-diffusion-webui).
2. Скачать модель NovelAI, модули и другие необходимые файлы через торрент-клиент:
`magnet:?xt=urn:btih:5bde442da86265b670a3e5ea3163afad2c6f8ecc&dn=novelaileak`
3. Переименовать скачанные файлы:
    1. **model.ckpt** в **novelai.ckpt**
    2. **animevae.pt** в **novelai.vae.pt**
    3. **Примечание:** Так же можно взять вместо NSFW-модель цензурную версию (SFW-модель).
    
    ![Переименование файлов](NovelAI%20(NAI)%20fabe944debab4d6b9dda9d03cc90924c/Untitled%201.png)
    
    Переименование файлов
    
4. Переместить файлы в папку с Stable Diffusion:
    1. Файлы **novelai.ckpt** и **novelai.vae.pt** в `\stable-diffusion-webui\models\Stable-diffusion`.
    2. Файлы из папки modules (**aini.pt, anime.pt** и т.д.) в `\stable-diffusion-webui\modules\hypernetworks` или в `\stable-diffusion-webui\models\hypernetworks`.
5. Запустить Stable Diffusion и выбрать модель NovelAI:
    
    ![Выбор модели NovelAI](NovelAI%20(NAI)%20fabe944debab4d6b9dda9d03cc90924c/Untitled%202.png)
    
    Выбор модели NovelAI
    
6. При необходимости, выбрать один из вариантов гиперсети (Hyperetwork) в настройках.
    
    ![Выбор варианта Hyperetwork](NovelAI%20(NAI)%20fabe944debab4d6b9dda9d03cc90924c/Untitled%203.png)
    
    Выбор варианта Hyperetwork
    

# Использование гиперсетей (Hypernetworks)

Использование файлов `Hypernetwork.pt` может внести уникальные изменения в вывод NAI в зависимости от того, какой из них вы используете.

**Чтобы включить их:**

- Создайте папку `/stable-diffusion-webui/models/hypernetworksfolder`, если она еще не существует.
- Вставьте ваши модули `.pt` (аниме, айни, фурри и т.д.) в папку hypernetworks
- Перезагрузите WebUI.
- В закладке "**Settings**” выберите ваш `.pt` в разделе Stable Diffusion finetune hypernetwork и нажмите кнопку “**apply**”.

**Примеры:**

```
**Prompt:** cute girl, upper body, art by имя художника

**Negative prompt:** lowres, bad anatomy, bad hands, text, error, missing fingers, extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts,signature, watermark, username, blurry, artist name

**Sampling Steps:** 28
**Sampling Method:** Euler
**Resolution:** 512x768
**CFG Scale:** 12
**Seed:** 80495232
```

# Настройка запуска NovelAI по умолчанию

1. Если вы хотите запускать NovelAI по умолчанию, сделайте следующее:
**Примечание:** В противном случае, вы можете просто выбрать его в выпадающем списке WebUI.
    1. Редактируйте webui-user.bat в блокноте и добавьте `NAI.ckpt`:
    COMMANDLINE_ARGS=--ckpt nai.ckpt

# Настройка как в абонентской подписке Novel AI

Можно создать результаты, идентичные текущему обслуживанию NovelAI, сделав следующее:

1. Set the sampler to Euler (Not Euler A).
2. Use 28 Steps.
3. Set CFG Scale to 11.
4. Use prompts: masterpiece, best quality at the beginning of all positive prompts
5. Use negative prompts: nsfw (nsfw is optional, and toggled on the site), lowres, bad anatomy, bad hands, text, error, missing fingers, extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts, signature, watermark, username, blurry, artist name as the negative prompt.
6. In the Settings tab, change Ignore last layers of CLIP model to 2 and apply.