# Virtual Reallity (VR)

---

### Повышение производительности PC/PCVR игр

1. Использовать технологии **AMD FidelityFX (FSR)**, **NVIDIA Image Scaling** или **NDIAI DLSS** (не актуально из-за маленькой поддержки игр).
    1. [https://github.com/fholger/vrperfkit](https://github.com/fholger/vrperfkit) (Новая версия)
    2. [https://github.com/fholger/openvr_fsr](https://github.com/fholger/openvr_fsr) (Старая версия)
    3. [https://youtu.be/IXir0Y86N84](https://youtu.be/IXir0Y86N84) (Пример технологии NDIAI DLSS)
    4. Recommend running sharpness up to 1.0 and setting render scale to 0.77, I made a few other tweaks to foveated rendering that further optimized.
2. Использовать **Oculus Asynchronous Spacewarp (ASW)** и **Virtual Desktop's Synchronous Spacewarp (SSW)**.
    1. Что такое ASW, ATV, Reprojection, Motion Smoothing и Timewarp ([https://vk.com/@str_vr-chto-takoe-asw-atv-reprojection-motion-smoothing-i-timewarp](https://vk.com/@str_vr-chto-takoe-asw-atv-reprojection-motion-smoothing-i-timewarp))
    2. Сравнение Air Link (ASW) vs Virtual Desktop (SSW) ([https://youtu.be/zH7qCsey2to](https://youtu.be/zH7qCsey2to))
    3. Про Oculus ASW ([https://vr419.ru/blog/kak-zapuskat-vr-pk-igry-na-oculus-bez-steam-vr-i-zachem-eto-nuzhno/#:~:text=как что делать.-,Про Oculus ASW,-Я уже писал](https://vr419.ru/blog/kak-zapuskat-vr-pk-igry-na-oculus-bez-steam-vr-i-zachem-eto-nuzhno/#:~:text=%D0%BA%D0%B0%D0%BA%20%D1%87%D1%82%D0%BE%20%D0%B4%D0%B5%D0%BB%D0%B0%D1%82%D1%8C.-,%D0%9F%D1%80%D0%BE%20Oculus%20ASW,-%D0%AF%20%D1%83%D0%B6%D0%B5%20%D0%BF%D0%B8%D1%81%D0%B0%D0%BB))
    4. Для Oculus Asynchronous Spacewarp (ASW) необходимо стабильное Wi-Fi соединение.
        1. Включить пункт Mobile ASW в Oculus Debug Tool ([https://youtu.be/o02rncADNsQ](https://youtu.be/o02rncADNsQ))
3. **Использовать OpenComposite вместо Steam VR**
    1. Некоторым играм для работы нужен Steam VR и у нее нет нативной поддержки Oculus SDK — ее невозможно запустить минуя Steam VR. Для них можно использовать OpenComposite.
    Подходит для небольшого количества игр. ([https://gitlab.com/znixian/OpenOVR](https://gitlab.com/znixian/OpenOVR))
4. **Корректный способ запуска игры через Virtual Desktop
+ доп. инфа для [“Плоские” игры через ReShade ([https://www.youtube.com/watch?v=FBtC3zzyK34](https://www.youtube.com/watch?v=FBtC3zzyK34))](Virtual%20Reallity%20(VR)%20764db54c8c334485a6a55824979dd280.md)** 
    1. Всё про Virtual Desktop: настройки, запуск игр, управление ([https://youtu.be/5WmCo6h_7k0](https://youtu.be/5WmCo6h_7k0))

### Варианты мониторинга производительности

1. **OVR Advanced Settings** — приложение панели мониторинга для виртуальной реальности, которое позволяет получить доступ ко многим настройкам и предоставляет множество полезных функций, таких как таймеры, настройки звука, push-to-talk и многое другое. ([https://store.steampowered.com/app/1009850/OVR_Advanced_Settings/](https://store.steampowered.com/app/1009850/OVR_Advanced_Settings/))
2. **fpsVR** — утилита для SteamVR предназначенная для отслеживания FPS, времени кадра и других показателей производительности во внутриигровом оверлее. Удобное изменение настроек SteamVR в оверлее настроек в дашборде SteamVR. Отслеживание скручивания кабеля гарнитуры и другие полезные функции. ([https://store.steampowered.com/app/908520/fpsVR/](https://store.steampowered.com/app/908520/fpsVR/))

### Как играть не в VR игры в VR?

- Universal Unreal Engine VR Injector / UnrealVR ([https://github.com/TheNewJavaman/unreal-vr](https://github.com/TheNewJavaman/unreal-vr))
- “Плоские” игры через ReShade ([https://www.youtube.com/watch?v=FBtC3zzyK34](https://www.youtube.com/watch?v=FBtC3zzyK34))

### Как запускать PCVR игры через API Steam VR или Oculus SDK?

- Параметр для запуска игры с помощью API Steam VR, а не через Oculus SDK (`-vrmode openvr`).
- Схема запуска игры из магазина Oculus (лучший вариант запуска игры для Oculus): Игра/Приложение > Oculus API > Oculus Runtime > Шлем.
- Схема запуска игры из Steam VR: Игра/Приложение > SteamVR API > SteamVR Runtime > Oculus API > Oculus Runtime > Шлем.
- Большая часть игр при игре через Air Link сама будет запускаться без Steam VR, напрямую в Oculus, т.к. именно через Air Link Oculus Quest видится как обычный проводной шлем.
- По ссылке есть таблица, в которой перечислены игры, которые вообще можно запустить без Steam VR в теории и так же описаны способы как это сделать. ([https://www.reddit.com/r/oculus/wiki/steamgameswithnativesupport/](https://www.reddit.com/r/oculus/wiki/steamgameswithnativesupport/))