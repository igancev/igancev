---
title: Kodi и Elementum - наилучший способ для домашнего просмотра кино в 4K онлайн
excerpt: Рассмотрим опенсорсный медиацентр Kodi в связке с бесплатным, но феноменальным плагином Elementum для просмотра кино и сериалов онлайн в 4K. Без рекламы, регистрации, и смс
keywords: смотреть фильмы онлайн, бесплатный просмотр фильмов 4K, просмотр торрентов онлайн, просмотр торрентов на андроид , android tv,  kodi, elementum, watch 4k movies, watch torrents online, open source
key: watch-movies-with-kodi-end-elementum
tags: kodi elementum torrents movie
slug: watch-movies-with-kodi-end-elementum
mainImage: /assets/articles/kodi/kodi-logo.png
---

![kodi logo](/assets/articles/kodi/kodi-logo.png)

Рассмотрим популярный, опенсорсный медиацентр Kodi в связке с феноменальным, но малоизвестным плагином Elementum, 
позволяющим подбирать кино и сериалы в 4K с торрентов и смотреть онлайн! Без рекламы, регистрации, и смс.

Я не призываю никого прямо или косвенно ущимлять чьи либо авторские права. 
А если вам так показалось - **то вам показалось**! 😁🤡☠️
{:.warning}

## Вступление

### Kodi

[Kodi](https://kodi.tv/) - это опенсорсный медиацентр, по-настоящему мощный софт, медиа комбайн, с поддержкой установки различным
плагинов, расширяющих его функциональность. Kodi можно установить на кучу платформ, таких как **Linux, Windows, Android,
Raspberry Pi, macOS, iOS, tvOS**. Как приложение, или даже как операционную систему ([LibreELEC](https://libreelec.tv/)) на девайс, что актуально, например, 
для Raspberry Pi. 

### Elementum

[Elementum](https://elementumorg.github.io/) - это опенсорсный проект, плагин, который устанавливается на Kodi.
Он позволяет **искать торрент файлы** фильмов и сериалов на любимых **торрент трекерах**, а также **смотреть их онлайн**.

### Преимущества 💪🤟

1. **Бесплатно.** Полностью.
2. **Без рекламы**. Да, да.
3. **Любое качество**: 4K, FullHD, 720p, 480p, и т.д. На вкус, цвет, размер.
4. **Торренты** во всей красе. Вы и так все знаете, не маленькие.
5. **Богатейший выбор контента**. Доступно все, что есть на подключенных вами торрент трекерах.
6. **Не нужно много места на диске**. Для онлайн просмотра фильма в _BlueRay 30GB_ будет достаточно флешки объемом 8гб, с установленной на ней ОС. Чудеса!   
7. **Мультиплатформенность.** Работает на **Linux, Windows, Android,
   Raspberry Pi, macOS, iOS, tvOS**, и т.д.
8. **Широкий выбор торрент-трекеров**, в которых осуществляется поиск торрент файлов
9. **Open Source.** Открытый исходный код всех компонентов. Ваши устройства под вашим контролем! Спасибо сообществу 

### Недостатки 🙈

1. **Порог входа.** Не каждая домохозяйка осилит настройку. Будет кстати скилл сына маминой подруги 🙍‍♂️.
2. **Может потребоваться [VPN](/2022-03-13-simple-and-fast-install-vpn-wireguard-docker)** для доступа к 
  заблокированным торрент-трекерам. Но _только в момент поиска торрентов_. Для просмотра VPN не нужен, если конечно
  не блокируется сам _BitTorrent_ протокол.
3. Натянутая вкусовщина, но на мой субъективный взгляд **не очень удобный** вид предпросмотра контента в каталоге. Но с этим можно
  жить.

### Аналоги

Буду признателен, если напишете [в комментариях к посту в телеграме](https://t.me/igancev_ru/22), **какой софт используете вы** для сих целей.
Или гаджеты, сервисы. 
Почти уверен, что лучше этой сладкой связки быть ничего не может.

---

## Настройка

### Установка Kodi

Нам потребуется девайс, на который можно установить Kodi. Самый логичный кейс - это телевизор или **приставка 
на Android TV**, т.к. мы все - таки хотим смотреть кино. Но это вполне может быть как ваш ноутбук или смартфон. 

Еще очень классным кейсом является **Raspberry Pi, которая превращается в приставку к ТВ** с помощью установки на нее
операционной системы [LibreELEC](https://libreelec.tv/). Это операционка, которая загружает только Kodi, и ничего 
больше.

Все источники и мануалы, откуда можно скачать Kodi, есть [на официальном сайте](https://kodi.tv/download/), я не
буду заострять на этом внимание. Например, для android все предельно просто, т.к. приложение ставится из Play Store.
С другими платформами тоже проблем особых быть не должно.

Так выглядит Kodi после установки:

![Kodi first start](/assets/articles/kodi/kodi-start.png)

### Установка Elementum

[//]: # (Я буду показывать на примере )

[//]: # ({:.info})

Elementum является дополнением/плагином для Kodi. Его надо предварительно скачать, а затем установить из UI интерфейса
Kodi.

Шаги установки: 

#### 1. Скачать c [официального сайта Elementum](https://elementumorg.github.io/) `zip` архив дополнения

Скачиваем `Universal` zip-архив, чтобы не заморачиваться с выбором платформы и архитектуры вашего девайса. Universal в
себе содержит все поддерживаемые архитектуры.

![Elementum download page](/assets/articles/kodi/elementum-download.png)

#### 2. Включить в настройках Kodi возможность установки дополнений из _неизвестных_ источников

Для этого в Kodi перейдем в `Настройки` -> `Система` -> `Дополнения`, и в графе `Неизвестные источники` **включим** 
переключатель

![kodi settings enable unknown sources](/assets/articles/kodi/kodi-enable-unknown-sources.png)

#### 3. Установить дополнение _из скачанного zip архива_

Теперь можно установить скачанное дополнение. Перейдем в раздел `Дополнения` -> `Браузер дополнений`, где выберем пункт
`Установить из zip файла`. 

![kodi addons settings install from zip archive](/assets/articles/kodi/kodi-install-zip.png)

Появится окно, в котором нужно будет выбрать ранее скаченный zip архив elementum - а, и нажать `ОК`

![kodi addons settings install from zip archive choose zip file in popup](/assets/articles/kodi/kodi-install-zip-2.png)

Нужно будет немного подождать, пока Kodi покажет уведомление об успешной установке дополнения.

#### 4. Установить Burst

`Burst` - это неотъемлемая часть Elementum, без которой он не заработает. Он дает возможность поиска по
различным провайдерам (читай торрент-трекерам). Он может установиться автоматически, но в
этот раз этого не произошло, и я увидел сообщение о том, что `Burst` надо доустановить вручную из репозитория. 

![Сообщение о том, что Burst не установился автоматически](/assets/articles/kodi/burst-not-installed-automatically.png)

Сделаем это. Перейдем в раздел `Дополнения` -> `Установить из репозитория` -> `ElementumOrg repository`
-> `Программные дополнения` -> `Elementum Burst`, и нажмем на кнопку `Установить`

![Страница в настройках с установкой Burst](/assets/articles/kodi/burst-install-screen.png)

Дополнение будет скачано, установлено, о чем Kodi нас уведомит всплывающим уведомлением.

#### 5. Настроить провайдера Burst

При поиске интересующего фильма он должен искаться в конкретных торрент трекерах, список которых **нужно
настроить единоразово**.

Перейдем в раздел `Дополнения` -> `Elementum` -> `Настройки провайдера Elementum Burst`, где в списке
трекеров включим интересующие любимые трекеры, а другие выключим.

Я использую 2 своих любимых трекера: 

- RuTracker
- NNM-Club

По опыту, их хватает с головой для поиска любых фильмов и сериалов, в любом качестве. Слишком много
трекеров тоже лучше не включать, т.к. чем длиннее список, тем дольше будет происходить этап поиска раздач по каждому
из списка.

При настройке `RuTracker` и `NNM-Club` нужно ввести логин и пароль от аккаунтов на соответствующих ресурсах.
Поэтому если у вас их нет, то необходимо их будет сначала зарегистрировать

![Настройки списка трекеров в Burst](/assets/articles/kodi/burst-tracker-settings.png)

На этом настройка завершена, ура! Перед первым использованием желательно перезапустить Kodi, а в идеале вовсе 
перезагрузить систему. Может у вас и сразу все заработает, но при крайней настройке мне помог только волшебный reboot 😃

## Как пользоваться

Наконец настройка закончена, пора бы и отдохнуть! Покушать попкорн под приятную организму жидкость, и включить
для просмотра фильм или сериал через **Kodi + Elementum**. Без надоедливой рекламы, бесплатно, онлайн (без предварительной 
загрузки), и в хорошем качестве. Не сказка ли? 😉

Заходим в `Дополнения` -> `Elementum`

**Внимание!** Если в вашей локации интернет провайдером заблокированы ваши торрент-трекеры, то перед
заходом в Elementum стоит [включить VPN](/2022-03-13-simple-and-fast-install-vpn-wireguard-docker).
Стоит отметить, что VPN нужен **только на стадии поиска раздач в трекерах**. После того, как нужная раздача 
найдена и выбрана, запускать просмотр лучше будет без VPN, чтобы скорость загрузки при онлайн просмотре была выше.
{:.info}

Проваливаемся в `Фильмы` или `Сериалы`. Из списка подборок выбираем понравившийся фильм по описанию,
или ищем по наименованию необходимый через `Поиск`. Кликаем по интересующему фильму, начнется поиск
раздач на настроенных нами трекерах.

![Экран выбора фильма в Kodi Elementum](/assets/articles/kodi/choose-movie.png)

Результаты будут показаны списком, отсортированные по количеству сидов
(сид, seeder, или тот, кто раздает файлы в раздаче).

![Экран выбора фильма в Kodi Elementum](/assets/articles/kodi/tracker-results.png)

Выбираем раздачу с нужным качеством, запускаем просмотр! И после недолгой буферизации
смотрим. Можно без угрызений совести употребить двойную порцию попкорна,
ведь мы его заслужили! 🍿🍿 

---

## Заключение

Настройка занимает какое - то время, и не факт, что она точно обернется успехом на вашем
девайсе. В процессе можно столкнуться со сложностями, с которыми я не столкнулся, и это нормально.
Возникающие ошибки должны решаться поиском в гугле, ну или на крайняк заменой девайсов.
Но результат стоит затраченных усилий. Настраиваешь один раз, а пользуешься потом годами.

## Комментарии

Если есть желание обсудить эту тему, то сделать это можно под [постом данной статьи в
телеграм канале](https://t.me/igancev_ru/22), на который также можно подписаться, чтобы не пропустить новые
материалы. Всем добра! 🤚