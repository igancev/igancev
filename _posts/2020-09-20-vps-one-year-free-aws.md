---
title: Бесплатный VPS на 1 год на AWS EC2 Amazon
excerpt: Зарегистрируем аккаунт на Amazon и создадим свой собственный виртуальный сервер под свои нужды (VPN, сайт), бесплатно, на период в 1 год
keywords: vps, aws, free, vds, amazon, ec2, free tier, бесплатный сервер, vps бесплатно, свой vpn
tags: vps linux free server amazon aws ec2
slug: free-vps-for-one-year-aws
mainImage: /assets/articles/aws-free/create-new-aws-account.png
---

Это **не** реклама amazon и их облачных сервисов. Обмана и моей
наживы тоже нет. Вы просто получите в пользование виртуальный сервер
с 1-м ядром CPU, 1 GB RAM, и 30 GB SSD сроком на один год,
бесплатно, и абсолютно легально. Об уровне бесплатного доступа можно почитать
[тут](https://aws.amazon.com/free).

Данный вариант не требует сверхспособностей. Но скорее всего понадобится время
и некоторая доля упорства, чтобы получить желаемый результат. И если
для вас время более ценный ресурс, чем плата в среднем 5$ в месяц за
аналогичный сервер, то возможно этот вариант не для вас.
{:.info}

## Для каких целей

Данный вариант отлично подходит для вспомогательных нужд, таких как
[VPN сервер](/2021-02-21-vpn-wireguard-docker), тестовая площадка, или для любых других целей, для которых будет
достаточно предоставленных мощностей. Важно помнить, что через 12 месяцев
либо прийдется платить, либо сервер превратится в тыкву.

Минусов я не нашел, разве что заморочка с регистрацией. Все - таки это не для
ленивых, т.к. тут не 2 раза мышкой кликнуть. Особенно, если вы будете пытаться
по минимуму использовать настоящие ваши контактные данные,
подробнее об этом дальше. В остальном сервер стабильно работает, подводных
камней в этом плане нет.

Не многие знают, что у Amazon уже не один год действует эта программа. Также
не у всех есть лишние средства на содержание своего сервера при старте проекта.
В любом случае лишняя машина на год не помешает никому. Начнем регистрацию.

## Почтовый ящик

Нам понадобится почтовый ящик. Можете зарегистрировать где угодно,
или использовать имеющийся. Я же предпочитаю использовать один из сервисов,
предоставляющих **временную электронную почту**, коих гугл выдает в
результатах поиска предостаточно, рекламировать никакой из них не буду.
Правда не любой подобный временный email с онлайн-сервисов принимается амазоном.


## Банковская карта

Да, Amazon просит привязать банковскую карту к аккаунту, как они пишут для
подтверждения личности. **Не рекомендую привязывать реальную банковскую карту**
по двум причинам:

1. По истечении 12 месяцев, если не выключить используемый экземпляр
виртуального сервера, деньги за него могут списаться автоматически, что может
стать для Вас сюрпризом. Если все - таки пойдете на это, то не поленитесь
поставить себе напоминание **через 11 месяцев и 3 недели** зайти в аккаунт,
и потушить все платные сервисы.

2. В сети читал про случаи, когда злоумышленники угоняли аккаунт, и
автоматически создавали множество самых мощных серверов, используя их для
майнинга. Хозяину аккаунта в таком случае выставляется счет с крупной суммой.
Хоть и такие случаи решаются через поддержку, но лучше быть спокойным, что с
твоей карты никто ничего не спишет.

Раньше прекрасно работал вариант, когда можно было воспользоваться
**виртуальной картой Яндекс.Денег**, и сразу после прохождения регистрации
ее заблокировать. Но, к моменту написания статьи Яндекс ввел ограничение на
оплату зарубежных сервисов, предоставляющих услуги по подписке. Попробуйте,
может быть что - то поменялось. У меня на данный момент приняло **виртуальную
карту Kiwi**. На статусе `Минимальный` Kiwi кошелька она отображается как
платная, 200р/год. Но при получении статуса кошелька `Основной` появляется
возможность создать карту бесплатно. Реквизиты карты предоставляются мгновенно.

Можно попробовать воспользоваться виртуальными картами других провайдеров.
Если ничего подходящего не удастся найти по каким - либо причинам, можно
рассмотреть возможность воспользоваться реальной пластиковой банковской картой,
у которой например заканчивается срок действия, как вариант.

На момент регистрации баланс на карте должен быть чуть больше одного доллара
в рублевом эквиваленте на текущий курс.
Amazon заблокирует на карте 1 доллар, и вернет его в течение пяти дней.
В случае с Яндексом, сумма возвращалась даже после того, как
виртуальная карта уже была заблокирована.

Автор статьи **не несет никакой финансовой или любой другой ответственности** за
совершаемые Вами действия. Вы сами по своей воле распоряжаетесь данными
о себе, о своих банковских картах, и т.д. Любые списания с вашей карты,
которые могут произойти после ввода ее реквизитов в amazon - дело лично вас и
amazon. Всегда будьте бдительны.
{:.warning}

## Номер телефона

Потребуется, чтобы получить смс сообщение верификации. Использовать свой, соседа,
или воспользоваться онлайн-сервисом - выбор каждого.

## Регистрация аккаунта

### Начало регистрации

Заходим на [console.aws.amazon.com](https://console.aws.amazon.com), и нажимаем
кнопку `Create a new AWS account`

![Кнопка создания аккаунта на сайте console.aws.amazon.com](/assets/articles/aws-free/create-new-aws-account.png)

### Email/password

Вводим email и сложный пароль

![Страница регистрации aws с полями ввода email и пароля](/assets/articles/aws-free/fill-email-and-password.png)

### Контактная информация

Заполняем контактную информацию и телефон

![Форма заполнения контактной информации при регистрации аккаунта amazon aws](/assets/articles/aws-free/contact-information.png)

### Реквизиты карты

Затем появится стандартный экран с полями для ввода
информации о банковской карте. Вводим данные подготовленной виртуальной или
реальной карты. Не забываем о баллансе на карте, он должен быть чуть больше
1 доллара США по текущему рублевому курсу. Амазон спишет доллар, и вернет
его через время.

### Подтверждение смс

После ввода реквизитов карты появится экран подтверждения по мобильному
телефону. Лучше выбрать вариант с подтверждением по смс, и дождаться смс кода.
Все стандартно, получаем код в смс, вводим в окошке. Также необходимо
ввести очень нечитабельную капчу. Я ее ввел раза с 10 - го,
уж очень она сложная.

![Экран подтверждения личности по номеру телефона при регистрации аккаунта amazon aws](/assets/articles/aws-free/phone-aws.png)

### Тарифный план

После чего amazon покажет экран об успешном подтверждении личности, и попросит
выбрать тарифный план, где нужно выбрать **Basic Plan**, т.е.
нажать кнопку **Free**

![Экран выбора тарифного плана после прохождения подтверждения личности при регистрации аккаунта amazon aws](/assets/articles/aws-free/support-plan-aws.png)

На этом регистрация аккаунта окончена. Теперь у нас есть аккаунт на амазоне
с возможностью заказа бесплатного сервера на год, чем и воспользуемся.

## Запуск виртуальной машины EC2

### Переходим в EC2

Войдем в только что созданный аккаунт, и перейдем в раздел `Services` -> `EC2`

![Раздел Services -> EC2](/assets/articles/aws-free/services-ec2.png)

### Выбор региона

Крайне желательно выбрать географический регион расположения
сервера ближе к той части планеты,
откуда планируется его использовать. Все просто: чем дальше дата центр
будет располагаться от целевой аудитории, тем выше пинг, отклик. По умолчанию
обычно выбран регион *US East (Ohio)us-east-2*, Америка, что для меня не
очень приемлемо.

Внимание! Не факт, что создание экземпляра сервера пройдет успешно
в выбранном Вами регионе. Но попробовать стоит. Если
[возникнут проблемы, описанные в конце статьи](#проблемы)
, то всегда регион можно выбрать другой, и попробовать
сделать то же самое в нем.
{:.warning}

Вы выбирайте удобный для Вас регион. Наиболее комфортное расположение
из предлагаемых для меня - город Франкфурт,
Германия. Выберу его из верхнего меню

![Aws выбор географического региона aws-region.png](/assets/articles/aws-free/aws-region.png)

### Key pairs

Перед непосредственным созданием виртуальной машины, нам необходимо позаботиться
о том, как мы, после ее создания, попадем на нее через SSH. Для этого
предварительно в настройках
необходимо добавить реквизиты подключения, а конкретно "пару ключей" (Key Pair).
Там есть возможность создать пару в формате `pem` или `ppk`, кому как угодно.
Я же покажу удобный мне вариант импортирования уже существующего RSA ключа.

![Пункт меню импорта ключа amazon](/assets/articles/aws-free/import-key-pair-amazon-1.png)

#### Генерация RSA

Если у вас его нет, то сгенерировать его на локальной машине Linux/Mac
можно следующей командой:

```bash
ssh-keygen -t rsa -b 2048 -C "email@example.com"
```

Пользователям Windows - гугл в помощь, или попробуйте создать ключ
в `pem` или `ppk`. Подключаться вероятно к серверу Вы будете
через программу `PuTTY`.
Ну а в целом, конечно же, переходите на Linux, изучайте его,
он прекрасен! Не пожалеете! :-)
{:.info}

Будет предложено ввести кастомное имя и расположение ключа, следует оставить
значение по умолчанию `/home/user/.ssh/id_rsa`
(где `user` - имя Вашего пользователя системы) просто нажав `enter`. Далее
будет предложено ввести `passphrase` для генерируемого ключа, я предпочитаю
оставить его пустым, 2 раза прожав `enter`. Пара ключей сгенерирована, и
располагается в домашней директории в каталоге `/home/user/.ssh/`, где
`/home/user/.ssh/id_rsa` - приватный ключ, который стоит хранить в секрете, и
`/home/user/.ssh/id_rsa.pub` - публичный ключ.

#### Импорт RSA в Key pairs

Необходимо скопировать
содержимое публичного ключа, например предварительно распечатав его в
консоли командой

```bash
cat /home/user/.ssh/id_rsa.pub
```

и вставить его в текстовое поле

![Добавление RSA ключа amazon ec2](/assets/articles/aws-free/import-key-pair-amazon-2.png)

В поле "Name" укажем произвольное имя ключа, и вносим изменения кнопкой
`Import key pair`.

### Создание инстанса

Переходим в раздел `Instances`, и нажимаем кнопку `Launch instances`

![Кнопка создания инстанса ec2 amazon в разделе Instances](/assets/articles/aws-free/launch-aws-ec2.png)

### 1. Choose AMI

Попадем на этап конструирования нашего инстанса vps. Первым шагом нас попросит
выбрать образ, на основе которого будет создана машина. На текущем бесплатном
тарифе нам доступны образы с меткой `Free tier eligible`. Я выбираю наиболее
подходящий под мои задачи образ `Ubuntu Server 20.04 LTS`.

![Выбор образа создаваемой виртуальной машины ec2 amazon ubuntu](/assets/articles/aws-free/choose-ami-ubuntu-ec2.png)

### 2. Choose Instance Type

На втором шаге оставляем предвыбранный вариант типа инстанса `t2.micro`,
подходящий под условия бесплатного использования, с харрактеристиками
*1 vCPUs, 2.5 GHz, Intel Xeon Family, 1 GiB memory*

![Выбор типа экземпляра ec2 amazon](/assets/articles/aws-free/choose-instance-type-ec2.png)

### 3. Configure Instance

На третьем шаге все оставляем как есть, значения по умолчанию.

### 4. Add Storage

На четвертом шаге **Add Storage** необходимо увеличить дисковое пространство
монтируемого корневого тома с предустановленных 8GB
до максимально доступных для бесплатного тарифа 30 GB

![Увеличение объема диска на шаге Add Storage](/assets/articles/aws-free/storage-30-gb-ec2.png)

### 5. Add Tags

Тэги нам не нужны, можно пропустить этот шаг

### 6. Configure Security Group

На данном шаге нам необходимо определить правила доступности нашего сервера
извне, т.е. правила брандмауэра, контролирующего поток трафика.



Если Вы точно знаете какие порты Вам потребуются - самое время их открыть на
данном шаге. В любом случае к данным настройкам можно будет вернуться позже.

Самое главное - открыть 22 порт, иначе по SSH не получится подключиться
{:.info}

**Новичкам**, кто не понимает что это и для каких целей, можно посоветовать
открыть все возможное по максимуму. Но будьте внимательны, это не правильно с
точки зрения безопасности.
Обязательно изучите что этот вопрос, восполните пробелы
в знаниях, чтобы в дальнейшем
держать открытыми только те соединения, которые используются по факту. Все
остальное должно быть закрыто, не торчать наружу. Я привожу пример на скриншоте
**как открыть все соединения**

![Configure Security Group, firewall settings настройки фаервола ec2 aws](/assets/articles/aws-free/security-ec2.png)

### 7. Review

Проверяем, что все выбрали правильно, и жмем кнопку `Launch`. Появится
диалоговое окно, в котором нужно выбрать существующую пару ключей, ранее
нами созданную. В первом дропдауне выбираем пункт
`Choose an existing key pair`, а во втором пункт с именем пары ключей,
[которое назначали при импорте](#импорт-rsa-в-key-pairs). Ставим галочку,
и жмем кнопку `Launch Instances`.

![Aws choose key pair выбор ранее созданной пары ключей.png](/assets/articles/aws-free/aws-choose-key-pair.png)

При успешном создании в меню аккаунта `Instances` наконец появится заветная
машина, и ее публичный ip адрес, который нам понадобится для входа на нее.

![Список инстансов ec2 и ip адрес созданного экземпляра](/assets/articles/aws-free/list-of-instance-aws.png)

Остается только дождаться ее инициализации.
Примерно через 2-5 минут `Status check` засветится зеленым, и
можно будет подключаться под именем пользователя `ubuntu`

## Подключение по ssh

```bash
ssh ubuntu@ip-адрес-вашего-ec2-инстанса-amazon
```

При первом входе нас попросят согласия на добавление нового ip адреса в список
известных хостов, поэтому пишем в консоли `yes`, и нажимаем `enter`.
После чего мы наконец попадем на долгожданную машину.

![Ssh вход на сервер](/assets/articles/aws-free/ssh-ec2.png)

Наш пользователь `ubuntu` имеет права администратора через `sudo`. Обновим
кеш репозиториев и систему командой

```bash
sudo apt update && sudo apt upgrade -y
```

На этом цель достигнута. Далее можно делать с ней что угодно,
в зависимости от наших нужд. В дальнейшем я планирую выпустить одну или
несколько статей о том, как можно с пользой использовать подобную машину.
Один из самых очевидных вариантов использования - [поднять свой VPN сервер](/2021-02-21-vpn-wireguard-docker).
Можно разместить там свой сайт. Вынести туда какой - нибудь микросервис,
воркер для фоновых задач, или просто поковыряться, потренироваться в настройке
чего - либо. Придумать можно много чего интересного.

## Проблемы

На самом деле в данном процессе что угодно может пойти не так, как я описываю.
Amazon давно и все успешнее борется с халявщиками, распознавая подозрительную
активность. Также условия с течением времени могут меняться. Если раньше сразу
после регистрации я мог без труда выбрать регион "Франция Париж", то сейчас
ни в Париже, ни во Франкфурте не удается создать инстанс. На последнем этапе
выдает ошибку:

```
Error: Launch Failed

This account is currently blocked and not recognized as a valid account.
Please contact aws-verification@amazon.com if you have questions.
```

![Ошибка создания инстанса ec2](/assets/articles/aws-free/create-instance-error.png)

[На Stackoverflow](https://stackoverflow.com/questions/46649542/aws-ec2-cant-launch-an-instance-account-blocked)
люди пишут, что изначально можно создавать EC2 только
в трех регионах США, поэтому мне временно пришлось вернуть регион
*US East (Ohio)us-east-2*.

Из Европы туда пинг
будет достаточно высокий (по факту ~ 160ms)

![Ошибка создания инстанса ec2](/assets/articles/aws-free/ping-Ohio.png)

для повседневных нужд это конечно же
очень много, если [использовать сервер как VPN](/2021-02-21-vpn-wireguard-docker).
Но для задач, где отклик не
критичен, такой сервер тоже вполне может сгодиться. Есть еще вариант написать
в поддержку Amazon, попросив открыть возможность на бесплатном тарифе
использовать другие регионы. Но во - первых, они отвечают очень долго,
а во - вторых, есть вероятность, что они откажут.
Но попробовать все равно стоит. Если у кого - то есть с этим опыт - прошу
поделиться :-)

## Итог

Мораль сей басни такова, что бесплатный сыр всегда только в мышеловке.
Мы, ради получения дешевого сервера в бесплатное пользование на год
должны пройти все эти мучения, выложить амазону кучу данных о себе. Стоит
конечный результат того или нет - пусть каждый решает для себя сам.

Всем добра, и хорошего настроения!
