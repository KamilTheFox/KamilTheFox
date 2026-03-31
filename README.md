# 🦊 Kamil — Fox Hard & Softness

**Security researcher · Systems engineer · Game developer**

*"Control over machines, not people"*

---

## Обо мне

Магистрант Университета Сириус по направлению **критической информационной инфраструктуры и информационной безопасности**. Пишу на C++, C#, Python и Java. Строю собственную распределённую инфраструктуру FoxInfra — серверы в Казани, Москве, Сочи и Нидерландах, связанные WireGuard mesh-сетью.

Люблю задачи, где нужно понять систему изнутри: реализовывать протоколы с нуля, оптимизировать производительность до последнего байта, автоматизировать всё, что можно автоматизировать.

Победитель хакатона с проектом **МетроАй** — система детекции дефектов вагонов метро на базе синтетических данных Stable Diffusion.

---

## CUDA / GPU Computing

*Два проекта, которые шли последовательно — от учебного до боевого.*

### [KuznechicInGPU](https://github.com/KamilTheFox/KuznechicInGPU) — ГОСТ Р 34.12-2015 на GPU
**500 МБ/с** шифрования российским стандартом «Кузнечик» на RTX 3060.

Алгоритм принципиально плохо ложится на GPU из-за цепочки последовательных зависимостей в линейном преобразовании L. Решение — алгебраическое преобразование S∘L в предвычисленные T-таблицы (64 КБ в Shared Memory), CPython C Extension для обхода GIL, асинхронный конвейер с двойной буферизацией.

Путь от наивной реализации (<85 МБ/с) до 500 МБ/с задокументирован пошагово. Корректность подтверждена по официальным тестовым векторам ГОСТ. Side-channel анализ: закрыты Timing Attacks и Cache-Timing Attacks.

`CUDA` `·` `C` `·` `Python` `·` `CPython Extension` `·` `FastAPI` `·` `Docker` `·` `ГОСТ Р 34.12-2015`

---

### [MD5Rainbow](https://github.com/KamilTheFox/MD5Rainbow) — входная точка в CUDA
Rainbow-таблицы для MD5 на GPU. Первый проект на CUDA — здесь отрабатывалась базовая модель параллелизма: один поток = одна цепочка, передача данных через CuPy, запись в PostgreSQL.

Именно здесь появилось понимание blocks/threads, управления памятью через `cp.asarray` и `cp.RawModule`, и того как вообще писать CUDA kernels из Python. Это фундамент на котором строился Кузнечик.

`CUDA` `·` `Python` `·` `CuPy` `·` `PostgreSQL` `·` `MD5`

---

## Публичные проекты

### [SerializatorFox.Net](https://github.com/KamilTheFox/SerializatorFox.Net)
Собственный бинарный сериализатор для .NET 8. Использует MurmurHash для идентификации полей вместо строковых ключей — это даёт наиболее компактный payload среди протестированных решений (885 байт против 1088 у MessagePack LZ4). Поддерживает полиморфизм без ручного управления индексами. Roadmap: Source Generators для устранения рефлексии и переход с GZip на LZ4.

`C#` `·` `.NET 8` `·` `MurmurHash` `·` `Binary serialization` `·` `Benchmarks`

---

### [CertificateCollectorRm94](https://github.com/KamilTheFox/CertificateCollectorRm94)
Настольное Windows-приложение для оформления, учёта и управления сертификатами страхования автостекол. Написано для реального страхового агента — используется в продакшене с момента выпуска.

`C#` `·` `.NET Framework 4.7.2` `·` `Windows Forms` `·` `Excel Interop`

---

### [MLTaxi](https://github.com/KamilTheFox/MLTaxi)
ML-сервис предсказания оптимальной ставки для водителей такси. LightGBM + XGBoost ensemble, FastAPI, Docker, развёрнут на продакшене. Включает валидацию входных данных, логирование ошибок, Swagger-документацию и веб-интерфейс.

`Python` `·` `LightGBM` `·` `XGBoost` `·` `FastAPI` `·` `Docker`

---

### [TMXHackathon](https://github.com/KamilTheFox/TMXHackathon)
Проект с хакатона ТМХ (ТрансМашХолдинг). Геймификация краудсорсинга и сервис генерации синтетических данных.

`Python` `·` `Unity` `·` `3D` `·` `ML` `·` `Docker`

---

### [VulpesTool](https://github.com/KamilTheFox/VulpesTool)
Unity Editor toolkit — набор атрибутов для визуальной организации Inspector'а, сериализации интерфейсов, умных кнопок, EnumSearchWindow с поиском и поддержкой Flags. Переиспользуемый пакет для ускорения разработки в Unity.

`C#` `·` `Unity` `·` `Editor Extensions` `·` `Attributes`

---

### [JpegCPP](https://github.com/KamilTheFox/JpegCPP)
Реализация JPEG-кодека на C++ с нуля. Makefile-сборка, классическая структура include/src/obj.

`C++` `·` `Image compression` `·` `Low-level`

---

### [TelegramBotMatchSirius](https://github.com/KamilTheFox/TelegramBotMatchSirius) `·` [Tweener](https://github.com/KamilTheFox/Tweener) `·` [Routing\_Sirius](https://github.com/KamilTheFox/Routing_Sirius) `·` [Fox-WinForms](https://github.com/KamilTheFox/Fox-WinForms) `·` [FoxHackDiggerGame](https://github.com/KamilTheFox/FoxHackDiggerGame) `·` [ExampleParallelForC-CPP](https://github.com/KamilTheFox/ExampleParallelForC-CPP) `·` [ArrayBoolean](https://github.com/KamilTheFox/ArrayBoolean)

Экспериментальные проекты — Telegram-боты, анимационные системы, маршрутизация, WinForms, игры, параллельное программирование.

---

## Закрытые проекты

| Проект | Описание | Стек |
|--------|----------|------|
| **FoxWG** | Кастомная реализация WireGuard с обфускацией трафика (FoxWG Ultra) — математические модели симуляции человеческого поведения, DPI evasion, SNI proxy | C, Python, iptables |
| **ML Vulnerability Deduplication** | ML-система дедупликации уязвимостей для систем управления уязвимостями | Python, NLP |
| **foxhardsoftness.ru** | Персональный сайт на ASP.NET с CI/CD pipeline | C#, ASP.NET, GitHub Actions |
| **Game Launcher** | Кроссплатформенный лаунчер на C++ для Unity-игры | C++, CMake |
| **Unity Game** | Игра, к которой разрабатывается лаунчер | C#, Unity |

---

## Навыки

**Языки:** C++, C#, Python, Java

**Инфраструктура:** Docker, Kubernetes, WireGuard, iptables, Prometheus, Grafana, nginx

**Базы данных:** MongoDB, PostgreSQL, Redis

**ML/AI:** PyTorch, LightGBM, XGBoost, Stable Diffusion, Ollama, BertTopic, all-MiniLM-L6-v2

**Безопасность:** реверс-инжиниринг, сетевая безопасность, обфускация трафика, анализ уязвимостей

**Gamedev:** Unity, C# scripting, Editor extensions

---

## Инфраструктура FoxInfra

Собственная распределённая сеть серверов — Россия (Казань, Москва, Сочи) и Нидерланды, связанная WireGuard mesh. Два сервера с RTX 3060 для Stable Diffusion и LLM inference (Ollama). Полное разделение сетевых сегментов по принципу минимальных привилегий.

---

**foxhardsoftness.ru** — "hard" infrastructure meets "soft" creativity 🦊
