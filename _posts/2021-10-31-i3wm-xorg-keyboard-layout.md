---
title: Настройка раскладки клавиатуры в i3wm - это просто!
excerpt: Рассмотрим несколько способов настройки и управления раскладкой клавиатуры в оконном менеджере i3, а если быть точнее, то в xorg
keywords: i3wm, i3, раскладка клавиатуры, keyboard layout i3wm
tags: i3wm linux Xorg
slug: i3wm-keyboard-layout
mainImage: /assets/articles/i3wm-keyboard-layout/i3wm-keyboard-layout.png
---

<img alt="Логотип i3wm на пишущей машинке" src="/assets/articles/i3wm-keyboard-layout/i3wm-keyboard-layout.png"/>

Зачастую у новичков и не только при первичной [настройке i3](/2020-01-05-installing-and-configuring-i3wm-on-arch-linux) возникает вопрос, как
настроить необходимые раскладки для клавиатуры, и привычное переключение между ними. В этой статье
постараемся решить данную задачу.
<!--more-->

## Предисловие

Спойлер: [решение тут](#решение)
{:.info}

К сожалению или к счастью, `i3wm` это всего лишь оконный менеджер, и он нам не предоставляет никаких штатных механизмов для настройки раскладки,
как это делают полноценные среды рабочего стола (Gnome, KDE, и т.д.). Нет как настроек в конфигах, так и естественно никакого UI. И с одной стороны это
правильно, т.к. инструмент отрисовки окон не берет на себя лишних обязанностей, оставаясь минималистичным.

С другой стороны менее опытных пользователей,
жаждущих оценить тайлинг, может оттолкнуть необходимость настройки таких базовых вещей, которые мы привыкли видеть рабочими если не сразу после установки,
то как минимум после недолгих манипуляций в настройках, разделе настройки клавиатуры, или языков.

В сети разбросано много информации
по этому поводу. Нельзя сказать, что вся она не рабочая, но множество инструкций по каким - либо причинам у меня не заработали. Возможно они
работают у кого - то другого. Возможно часть информации устарело. И это нормально, ведь всегда существует *временной, хардверный и софтверный контекст*, в котором находится конкретный пользователь.

Ниже предложенное решение у меня
работает в `Arch` и `Manjaro`. Может в теории подойти и для других дистрибутивов, таких как `Debian`, `Ubuntu` и прочих,
так и для других *окружений рабочего стола* и *оконных менеджеров*, работающих из под `Xorg`.

Все далее описанное составляет выжимку из мною прочитанного и переработанного материала
из [списка полезных материалов](#полезные-материалы), а также различных топиков на форумах, заметок и статей на бескрайних просторах сети.

На старте имеем одну английскую раскладку, установленную по умолчанию `us`. Будем устанавливать дополнительно вторую русскую раскладку `ru`.
Но если нужна другая, или больше двух, то это тоже можно. Посмотреть *аббревиатуры доступных раскладок* можно командой:

```bash
localectl list-x11-keymap-layouts
```

Переключение будем делать по сочетанию `Alt + Shift`, но вы можете выбрать иное сочетание.
Посмотреть *доступные сочетания клавиш* можно командой:

```bash
localectl list-x11-keymap-options
```

Также можно при желании задать *вариант расположения клавиш*, типа `dvorak`, что мне не нужно. Но посмотреть доступные варианты можно командой:

```
localectl list-x11-keymap-variants
```

## Решение

К сожалению, полноценный результат достигается только после выполнения нескольких пунктов одновременно, о них и поговорим.

Для определения раскладок клавиатуры сервер Xorg использует [клавиатурное расширение X (XKB)](https://wiki.archlinux.org/title/X_keyboard_extension).
Посмотрим текущие настройки xkb следующей командой:

```bash
setxkbmap -print -verbose 10
```

Вывод будет примерно таким, и он довольно скудный:

```
Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
layout:     us
Trying to build keymap using the following components:
xkb_keymap {
};
```

### 1. setxkbmap

С помощью утилиты `setxkbmap` можно настроить раскладку **в рамках текущей пользовательской сессии**. Под наши требования команда будет выглядеть так:

```bash
setxkbmap -model pc105 -layout us,ru -option grp:alt_shift_toggle
```

После ее ввода при нажатии `Alt + Shift` у нас *уже должна переключаться раскладка на русский и обратно*.

Посмотрим как изменился вывод команды `setxkbmap -print -verbose 10`:

```
Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     us,ru
options:    grp:alt_shift_toggle
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us+ru:2+inet(evdev)+group(alt_shift_toggle)
geometry:   pc(pc105)
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+us+ru:2+inet(evdev)+group(alt_shift_toggle)"	};
	xkb_geometry  { include "pc(pc105)"	};
};
```

Видим, что изменения применились.

`pc105` - это модель клавиатуры, в большинстве случаев подойдет `pc104` или `pc105`.
Список доступных моделей можно посмотреть тут:

```bash
localectl list-x11-keymap-models
```


Но так как действие команды распространяется только на текущую сессию, то команду прийдется вводить вручную после каждой перезагрузки, что не очень.
Поэтому можно **поставить ее на автозапуск** при старте, и сделать это можно несколькими способами.

#### а) Прописать в .xprofile

Файл [.xprofile](https://wiki.archlinux.org/title/Xprofile_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)) / [(EN)](https://wiki.archlinux.org/title/Xprofile)
позволяет выполнять команды при старте сессии.

Создадим `~/.xprofile` (или `/etc/xprofile`) и пропишем в него вышеупомянутую команду.
Убедимся также, что в файле `~/.xinitrc` (или `/etc/X11/xinit/xinitrc`) существуют следующие строки для запуска `.xprofile`:

```
[ -f /etc/xprofile ] && . /etc/xprofile
[ -f ~/.xprofile ] && . ~/.xprofile
```

#### б) Прописать в конфиге i3

Отредактировать конфиг `~/.config/i3/config`, добавим в него строку:

```bash
exec --no-startup-id setxkbmap -model pc105 -layout us,ru -option grp:alt_shift_toggle
```

В принципе, кому - то этих настроек уже может хватить для комфортной повседневной работы.
Но бывают случаи, когда раскладка по каким - то неизвестным мне причинам слетает сама собой, т.е. просто хоткей перестает реагировать. Приходится
повторно исполнять команду вручную, и происходит это обычно в самый неподходящий момент.

Возможно это случается при отключении/подключении клавиатуры. Часто это стало случаться при переходе на беспроводную **bluetooth** клавиатуру.
Возможно сбрасываются настройки при выходе из спящего режима, но это не точно.

Далее рассмотрим еще несколько способов, которые не конфликтуют с `setxkbmap`.

### 2. Настройка конфига Xorg

Подробнее всего [настройку раскладки клавиатуры в xorg](https://wiki.archlinux.org/title/Xorg_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)/Keyboard_configuration_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)) /   [(EN)](https://wiki.archlinux.org/title/Xorg/Keyboard_configuration)
описывает **Arch Wiki**.

Нам необходимо создать файл `/etc/X11/xorg.conf.d/00-keyboard.conf`, в котором будут прописаны наши требования на языке конфигов `Xorg`.
Итоговый файл конфига будет выглядеть примерно так:

```bash
# /etc/X11/xorg.conf.d/00-keyboard.conf
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "us,ru"
        Option "XkbModel" "pc105"
        Option "XkbOptions" "grp:alt_shift_toggle"
EndSection
```

Можно как вручную создать данный файл, так и сгенерировать его при помощи утилиты `localectl`:

```bash
sudo localectl set-x11-keymap us,ru pc105 "" grp:alt_shift_toggle
```

На данном этапе у многих, согласно форумам, проблема полностью решается. Но не всегда, как показал мой случай.
Поэтому дополнить решение поможет следующий способ, также не конфликтующий с предыдущими, а дополняющий их.

### 3. Настройка параметров в /etc/default/keyboard

Где - то на просторах сети на очередном топике форума какой - то добрый человек
оставил комментарий такому - же бедолаге как я, который боролся со сбросом настроек клавиатуры. А именно продублировать
значения из `00-keyboard.conf` в некоторый **конфигурационный файл клавиатуры** `/etc/default/keyboard`.
Откроем и отредактируем его, чтобы получилось примерно следующее содержание:

```bash
# /etc/default/keyboard
XKBMODEL="pc105"
XKBLAYOUT="us,ru"
XKBVARIANT=""
XKBOPTIONS="grp:alt_shift_toggle"

BACKSPACE="guess"
```

Как вы уже поняли, тут находятся те же самые параметры с теми же значениями
(за исключением `BACKSPACE="guess"`, непонятно что это, оставим как было).

Очень жаль, что практически во всех мануалах упускают эту конфигурацию, и что о ней нет упоминания на arch wiki, в разделе конфигурации клавиатуры.
Также искренне жаль, что такая базовая функциональность начинает работать только после обильного поиска решения проблемы в интернете,
и не без танцев с бубном. Ведь дублирование значений конфигурации по двум разным файлам это как минимум странно.
Очень здорово, что теперь есть эта статья!

### 4. Раскладка в консоли

Для того, чтобы раскладка корректно работала еще и в консоли, необходимо отредактировать
`/etc/vconsole.conf`, присвоив следующие значения параметрам:

```bash
# /etc/vconsole.conf

KEYMAP=ruwin_alt_sh-UTF-8
FONT=cyr-sun16

USECOLOR=yes
```

Этого должно быть уже достаточно, почитать [подробнее можно на Arch Wiki](https://wiki.archlinux.org/title/Linux_console_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)/Keyboard_configuration_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)) / [(EN)](https://wiki.archlinux.org/title/Linux_console/Keyboard_configuration)

## Заключение

Мы настроили раскладку клавиатуры, и теперь то все наконец **должно заработать как надо**!

В такие моменты конечно чувствуется продуманность из коробки полноценных окружений рабочего стола, или же проприетарных и/или платных ОС, таких как винда или макос.
Но если вы дочитали до этого момента, т.е. прошли все ритуалы настройки раскладки в `Xorg` и в `i3`, то наверное вы, также как и я, не готовы променять
ту свободу и гибкость, которую дает нам `linux`, `open source`, свободное програмное обеспечение ни на что. Изучайте linux, его экосистему.
Его возможности безграничны!

## Полезные материалы

- [Xorg (Русский)/Keyboard configuration (Русский)](https://wiki.archlinux.org/title/Xorg_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)/Keyboard_configuration_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)) / [Xorg/Keyboard configuration (EN)](https://wiki.archlinux.org/title/Xorg/Keyboard_configuration)
- [xprofile (Русский)](https://wiki.archlinux.org/title/Xprofile_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)) / [xprofile (EN)](https://wiki.archlinux.org/title/Xprofile)
- [X keyboard extension](https://wiki.archlinux.org/title/X_keyboard_extension)
- [Linux console (Русский)/Keyboard configuration (Русский)](https://wiki.archlinux.org/title/Linux_console_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)/Keyboard_configuration_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)) / [Linux console/Keyboard configuration (EN)](https://wiki.archlinux.org/title/Linux_console/Keyboard_configuration)
- [Xorg InputClass section config documentation](https://www.x.org/releases/current/doc/man/man5/xorg.conf.5.xhtml#heading9)

## Комментарии

Если вы заметили неточность, знаете больше способов, у вас есть вопросы, или просто хотите это обсудить,
то [комментарии к данной статье можно оставить под постом в телеграме](https://t.me/igancev_ru/12).
