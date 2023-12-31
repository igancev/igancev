---
title: Первичная настройка Arch Linux после установки
excerpt: В данной статье я опишу действия и настройки, которые выполняю сразу после установки Arch Linux.
keywords: Arch Linux первичная настройка после установки first settings
key: settingsArch
tags: Linux Arch
slug: initial-configuration-of-arch-linux
mainImage: /assets/articles/settingsArch/pacman-colors.png
---

В данной статье я опишу действия, которые выполняю после установки системы.
Тут будет установка самых необходимых программ,
а также то, какие настройки, конфигурации, и прочее
вношу я конкретно под себя.

<!--more-->

Это не означает, что Вам нужно
все поголовно, и тем более бездумно копировать, нет конечно.
Но на первых парах это может помочь Вам в построении по кирпичиком
Вашей собственной, индивидуальной системы. Ведь все мы разные, со
своими вкусами, предпочтениями, и прочим. Я не навязываю свое мнение
никому, и уважаю чужие мнения на этот
счет. Итак поехали!

## Pacman в цвете

Первым делом на голом арче хочется, и чуть ли не обязательно, включить
отображение цветов в пакетном менеджере pacman. Ведь без них вывод
pacman - а просто скучен) Не говоря уже о том, что сложнее воспринимается.
Для этого откроем на редактирование файл `/etc/pacman.conf`

```bash
sudo vim /etc/pacman.conf
```

и найдем в нем строку `#Colors`. Раскомментируем ее, т.е. удалим впереди
стоящий символ решетки, и сохраним файл.

после чего вывод pacman будет окрашен

```bash
pacman -Ss networkmanager
```

![Вывод команды sudo pacman -Ss networkmanager](/assets/articles/settingsArch/pacman-colors.png)

## Обновление

Далее обновим кэш репозиториев пакетного менеджера pacman, и заодно систему

```bash
sudo pacman -Syyuu
```

## Включение синхронизации времени

За синхронизацию системных часов по сети отвечает служба `systemd-timesyncd`,
которая доступна вместе с `systemd`. По умолчанию синхронизация выключена.
Для включения необходимо выполнить команду:

```bash
timedatectl set-ntp true
```

Проверить состояние службы можно командой `timedatectl status`.
Подробнее о службе можно узнать [тут](https://wiki.archlinux.org/index.php/Systemd-timesyncd_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)).

## Программы

Установим git, он нам понадобится в любом случае

```bash
sudp pacman -S git
```

Так как скоро мы будем устанавливать графическое окружение, то в нем нам
потребуется терминал. Я буду ставить себе оконный менеджер i3wm, и мне
понадобится минималистичный легкий эмулятор терминала,
под роль которого хорошо подходит на мой взгляд alacritty.
Также нам потребуется браузер, я предпочитаю firefox.

```bash
sudo pacman -S alacritty firefox
```

Установлю сразу несколько пакетов с шрифтами, которые мне импонируют.
Я привык к убунтовским шрифтам, + установлю популярный набор шрифтов hack

```bash
sudo pacman -S ttf-hack ttf-ubuntu-font-family
```

## yay, пакетный менеджер AUR

До этого момента я набирал текст в `vim`. Люблю этот редактор, но из - за того,
что редко пользуюсь, приходится все время заново обучаться его фишкам.
Поэтому для ускорения процесса настройки + написания статей уж очень
хочется привычный `sublime`. Но увы его нет в репозиториях арча. И
Вы наверняка уже слышали об AUR, пользовательских репозиториях.
Работать с ними можно без всяких утилит, но упрощают процесс скачивания и
сборки пакетные менеджеры для AUR, каковым является `yay`. `yay` написан на go,
популярен стал после того, как загнулся `yaourt`, звучит и коротко пишется.
К тому же у него свободная лицензия GPL-3.0.
Поэтому это мой выбор) Установим свободный `yay`, и затем несвободный,
проприетарный `sublime`. Инструкцию по
установке `yay` можно взять с репозитория на github
[https://github.com/Jguer/yay](https://github.com/Jguer/yay)

### Установка yay

```bash
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

```bash
# запустим yay убедиться что он установился + обновить кэш
yay
```

yay еще прекрасен тем, что интерфейс использования схож с pacman.

Найдем пакет sublime в AUR, выберем подходящий, и установим

### Установка sublime

```bash
yay -Ss sublime

# можно и без приставки aur, но так копировать удобнее из выдачи
# поиска из прошлой команды двойным кликом по наименованию пакета.
yay -S aur/sublime-text-dev
```

yay заботливо склонирует за нас и соберет программу.

## Звук

В системе по умолчанию не будет работать звук. Установим звуковой сервер

```bash
sudo pacman -S pulseaudio
```

а также (на будущее) графическую утилиту для настройки звука `pavucontrol`

```bash
sudo pacman -S pavucontrol
```

![Графическая утилита для настройки звука в linux pavucontrol](/assets/articles/settingsArch/pavucontrol.png)

## Что дальше

Интернет у нас настроен, язык переключается, кириллица отображается,
все это мы настроили еще [на этапе установки
системы](/2019-11-30-install-arch-linux).

Мы настроили вывод pacman в цвете, обновили систему, установили пакетный
менеджер для AUR `yay`, и установили несколько программ.
Следующим шагом будет
[установка графического окружения](/2020-01-05-installing-and-configuring-i3wm-on-arch-linux),
в моем случае это оконный менеджер [`i3wm`](https://i3wm.org).
После его установки через `firefox` мы сразу сможем гуглить, в `sublime`
более удобно редактировать конфиги, а через эмулятор терминала
`alacritty` настраивать дальше систему под себя.
