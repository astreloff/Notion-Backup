# Mo Di Diffusion

Ссылка: https://huggingface.co/nitrosocke/mo-di-diffusion
Стили: Disney

# Описание

# Установка

<aside>
<img src="https://www.notion.so/icons/info-alternate_gray.svg" alt="https://www.notion.so/icons/info-alternate_gray.svg" width="40px" /> **Использование стиля модели**

Use the tokens **modern disney** style in your prompts for the effect.

</aside>

<aside>
<img src="https://www.notion.so/icons/info-alternate_gray.svg" alt="https://www.notion.so/icons/info-alternate_gray.svg" width="40px" /> **Включение NSFW**

Для генерации моделью NSFW-контента необходимо создать новую ячейку и в ней указать следующий код:

def dummy_checker(images, **kwargs): return images, False

[pipe.safety](http://pipe.safety/)_checker = dummy_checker

</aside>

**Prompt and settings for Lara Croft:**

**modern disney lara croft** *Steps: 50, Sampler: Euler a, CFG scale: 7, Seed: 3940025417, Size: 512x768*

**Prompt and settings for the Lion:**

**modern disney (baby lion) Negative prompt: person human** *Steps: 50, Sampler: Euler a, CFG scale: 7, Seed: 1355059992, Size: 512x512*

**Videogame Characters rendered with the model:**

![Untitled](Mo%20Di%20Diffusion%20d4bb9a37a28e49d88c299e8fb193e903/Untitled.png)

**Animal Characters rendered with the model:**

![Untitled](Mo%20Di%20Diffusion%20d4bb9a37a28e49d88c299e8fb193e903/Untitled%201.png)

**Cars and Landscapes rendered with the model:**

![Untitled](Mo%20Di%20Diffusion%20d4bb9a37a28e49d88c299e8fb193e903/Untitled%202.png)