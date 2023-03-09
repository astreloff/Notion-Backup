# Выбор нескольких элементов через условие AND

<aside>
<img src="https://www.notion.so/icons/info-alternate_gray.svg" alt="https://www.notion.so/icons/info-alternate_gray.svg" width="40px" /> В данном примере берется время прибытия в реальном времени с карт Яндекс. Для этого необходимо обратиться к элементу имеющему несколько классов.

</aside>

Для получения нескольких элементов можно использовать следующий селектор: `//*[contains(@class, 'masstransit-prognoses-view__title') and contains(@class, '_live')]`.