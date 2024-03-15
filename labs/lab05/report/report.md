---
## Front matter
title: "Отчёт по лабораторной работе №5"
subtitle: "Настройка рабочей среды"
author: "Чекмарев Александр Дмитриевич | Группа НПИбд-02-23"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение навыков работы с pass и chezmoi


# Выполнение лабораторной работы

## Менеджер паролей pass

### Установка


Установим pass

![Рис 1.1.1: установка pass](image/Screenshot_1.png)

Установим gopass

![Рис 1.1.2: установка gopass](image/Screenshot_2.png)

### Настройка

Посмотрим список ключей: gpg --list-secret-keys

![Рис 1.2.1: просмотр ключей](image/Screenshot_3.png)

Если ключа нет, то можно создать новый (мне не нужно):  
gpg --full-generate-key


Инициализируем хранилище и создадим структуру:   

pass init <gpg-id or email>  
pass git init

![Рис 1.2.2: инициализация хранилища и создание структуры](image/Screenshot_5.png)

Также можно задать адрес репозитория на хостинге (репозиторий необходимо предварительно создать).
Создадим репозиторий на сайте гитхаб:

![Рис 1.2.3: создание репозитория](image/Screenshot_6.png)

Зададим адрес репозитория на хостинге:   

pass git remote add origin git@github.com:<git_username>/<git_repo>.git

![Рис 1.2.4: адрес репозитория](image/Screenshot_7.png)

Для синхронизации выполним следующие команда:  

pass git pull

![Рис 1.2.5: проверка файлов на актуальность](image/Screenshot_8.png)

pass git push

![Рис 1.2.6: отправка](image/Screenshot_9.png)


**Прямые изменения**

Следует заметить, что отслеживаются только изменения, сделанные через сам gopass (или pass).
Если изменения сделаны непосредственно на файловой системе, необходимо вручную закоммитить и выложить изменения:  

cd ~/.password-store/  
git add .  
git commit -am 'edit manually'  
git push

![Рис 1.2.7: коммит](image/Screenshot_10.png)

Проверить статус синхронизации можно командой  

pass git status

![Рис 1.2.8: проверка статуса](image/Screenshot_11.png)


### Настройка интерфейса с браузером


Для взаимодействия с браузером используется интерфейс native messaging.
Поэтому кроме плагина к браузеру устанавливается программа, обеспечивающая интерфейс native messaging.
Плагин browserpass для Firefox: https://addons.mozilla.org/en-US/firefox/addon/browserpass-ce/.

![Рис 1.3.1: установка расширения](image/Screenshot_12.1.png)

Интерфейс для взаимодействия с браузером (native messaging)

Репозиторий: https://github.com/browserpass/browserpass-native  

dnf copr enable maximbaz/browserpass

![Рис 1.3.2: включение репозитория](image/Screenshot_12.png)

dnf install browserpass

![Рис 1.3.3: установка browserpass](image/Screenshot_13.png)


### Сохранение пароля

Добавить новый пароль

Выполним:  

pass insert [OPTIONAL DIR]/[FILENAME]

![Рис 1.4.1: добавление пароля для файла](image/Screenshot_14.png)

OPTIONAL DIR: необязательное имя каталога, определяющее файловую структуру для вашего хранилища паролей;
FILENAME: имя файла, который будет использоваться для хранения пароля.
Отобразим пароль для указанного имени файла:  

pass [OPTIONAL DIR]/[FILENAME]

![Рис 1.4.2: отображение пароля](image/Screenshot_15.png)

Заменим существующий пароль:  

pass generate --in-place FILENAME

![Рис 1.4.3: замена пароля](image/Screenshot_16.png)


## Управление файлами конфигурации

### Дополнительное программное обеспечение


Установим дополнительное программное обеспечение:  
  
sudo dnf -y install \  
     dunst \  
     fontawesome-fonts \  
     powerline-fonts \  
     light \  
     fuzzel \  
     swaylock \  
     kitty \  
     waybar swaybg \  
     wl-clipboard \  
     mpv \  
     grim \  
     slurp  
	 
![Рис 2.1.1: установка программ](image/Screenshot_17.png)

Установим шрифты:  

sudo dnf copr enable peterwu/iosevka

![Рис 2.1.2: включение репозитория](image/Screenshot_18.png)

sudo dnf search iosevka

![Рис 2.1.3: установка шрифтов](image/Screenshot_19.png)

sudo dnf install iosevka-fonts iosevka-aile-fonts iosevka-curly-fonts iosevka-slab-fonts iosevka-etoile-fonts iosevka-term-fonts

![Рис 2.1.4: установка](image/Screenshot_20.png)

### Установка

Установка бинарного файла. Скрипт определяет архитектуру процессора и операционную систему и скачивает необходимый файл:
с помощью wget:  

sh -c "$(wget -qO- chezmoi.io/get)"

![Рис 2.2.1: установка бинарного файла](image/Screenshot_21.png)

### Создание собственного репозитория с помощью утилит

Будем использовать утилиты командной строки для работы с github.
Создадим свой репозиторий для конфигурационных файлов на основе шаблона:  

gh repo create dotfiles --template="yamadharma/dotfiles-template" --private

![Рис 2.3.1: создание репозитория](image/Screenshot_22.png)

### Подключение репозитория к своей системе

Инициализируем chezmoi с нашим репозиторием dotfiles:  

chezmoi init git@github.com:<username>/dotfiles.git

![Рис 2.4.1: инициализация](image/Screenshot_23.png)


Проверим, какие изменения внесёт chezmoi в домашний каталог, запустив:  

chezmoi diff

![Рис 2.4.2: фрагмент проверки](image/Screenshot_24.png)


Если нас устраивают изменения, внесённые chezmoi, запустим:  

chezmoi apply -v

![Рис 2.4.3: фрагмент внесения изменений](image/Screenshot_25.png)


### Использование chezmoi на нескольких машинах

На второй машине инициализируйте chezmoi с репозиторием dotfiles:  

chezmoi init https://github.com/<username>/dotfiles.git

Или через ssh:  

chezmoi init git@github.com:<username>/dotfiles.git

![Рис 2.5.1: инициализация](image/Screenshot_26.png)

Проверим, какие изменения внесёт chezmoi в домашний каталог, запустив:  

chezmoi diff

![Рис 2.5.2: проверка](image/Screenshot_27.png)


Если вас устраивают изменения, внесённые chezmoi, запустите:  

chezmoi apply -v

![Рис 2.5.3: применим изменения](image/Screenshot_28.png)


Если вас не устраивают изменения в файле, отредактируйте его с помощью:  

chezmoi edit file_name

Также можно вызвать инструмент слияния, чтобы объединить изменения между текущим содержимым файла, файлом в вашей рабочей копии и измененным содержимым файла:  

chezmoi merge file_name

При существующем каталоге chezmoi можно получить и применить последние изменения из вашего репозитория:  

chezmoi update -v

![Рис 2.5.4: применим последние изменения](image/Screenshot_29.png)


### Настройка новой машины с помощью одной команды

Можно установить свои dotfiles на новый компьютер с помощью одной команды:  

chezmoi init --apply https://github.com/<username>/dotfiles.git  

Через ssh:   

chezmoi init --apply git@github.com:<username>/dotfiles.git

![Рис 2.6.1: устнаовка dotfiles](image/Screenshot_30.png)

## Ежедневные операции c chezmoi

1. Извлечем последние изменения из репозитория и примените их

Можно извлечь изменения из репозитория и применить их одной командой:  

chezmoi update

![Рис 3.1.1: проверка актуальности файлов](image/Screenshot_31.png)

Это запускается git pull --autostash --rebase в вашем исходном каталоге, а затем chezmoi apply.

2. Извлечем последние изменения из своего репозитория и посмотрим, что изменится, фактически не применяя изменения

Выполним:  

chezmoi git pull -- --autostash --rebase && chezmoi diff

![Рис 3.1.2: извлечение последних изменений](image/Screenshot_32.png)

Это запускается git pull --autostash --rebase в вашем исходном каталоге, а chezmoi diff затем показывает разницу между целевым состоянием, вычисленным из вашего исходного каталога, и фактическим состоянием.

Если мы довольны изменениями, то можем применить их:  

chezmoi apply

![Рис 3.1.3: применение изменений](image/Screenshot_33.png)


3. Автоматически фиксируйте и отправляйте изменения в репозиторий

Можно автоматически фиксировать и отправлять изменения в исходный каталог в репозиторий.
Эта функция отключена по умолчанию.
Чтобы включить её, добавим в файл конфигурации ~/.config/chezmoi/chezmoi.toml следующее:  
  
[git]  
    autoCommit = true  
    autoPush = true  
	
![Рис 3.1.4: демонстрация файла](image/Screenshot_34.png)

Всякий раз, когда в исходный каталог вносятся изменения, chezmoi фиксирует изменения с помощью автоматически сгенерированного сообщения фиксации и отправляет их в ваш репозиторий.
Будьте осторожны при использовании autoPush. Если ваш репозиторий dotfiles является общедоступным, и вы случайно добавили секрет в виде обычного текста, этот секрет будет отправлен в ваш общедоступный репозиторий.

# Выводы

Я научился пользоваться pass и chezmoi


# Список литературы{.unnumbered}

::: {#refs}
:::
