# Stable Diffusion

Ссылка: https://huggingface.co/CompVis
Стили: All, Main Model

<aside>
<img src="https://www.notion.so/icons/info-alternate_gray.svg" alt="https://www.notion.so/icons/info-alternate_gray.svg" width="40px" /> **Системные требования**

Видеокарта NVIDIA 6GB+. Возможно запустить на слабых видеокартах, видеокартах от AMD или на процессоре, но в результате генерация занимает долгое время и на выходе изображение получается низкого качества, поэтому перечисленные варианты не рассматриваются.

</aside>

# **Описание**

Модель генерации (generation model) для создания изображений из текста, которая понимает взаимосвязи между словами и изображениями, выпущенная стартапом StabilityAI в 2022 году.

**Есть 2 вида модели:**

1. Модель на 4GB универсальна и позволяет генерировать изображения в различных стилях.
2. Модель на 7GB лучше подходит для дообучения.

# **Установка**

1. Скачиваем модель.
**Примечание:** При необходимости, создать аккаунт. В данном случае скачивается стандартная модель Stable Diffusion.
    1. [https://huggingface.co/CompVis/stable-diffusion-v1-4](https://huggingface.co/CompVis/stable-diffusion-v1-4)
    2. [https://huggingface.co/CompVis/stable-diffusion-v-1-4-original](https://huggingface.co/CompVis/stable-diffusion-v-1-4-original)
    3. [https://huggingface.co/runwayml/stable-diffusion-v1-5](https://huggingface.co/runwayml/stable-diffusion-v1-5)
2. Переместить скачанную модель в папку `/models`.