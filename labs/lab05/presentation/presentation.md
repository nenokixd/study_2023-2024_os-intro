---
## Front matter
lang: ru-RU
title: Лабораторная работа №5
subtitle: Настройка рабочей среды
author:
  - Чекмарев Александр Дмитриевич | Группа НПИбд-02-23
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 14 марта 2024

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
 
 
 ## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Чекмарев Александр Дмитриевич
  * Группа НПИбд-02-23
  * Российский университет дружбы народов
  * <https://github.com/nenokixd?tab=repositories>

:::
::: {.column width="30%"}


:::
::::::::::::::

# Вводная часть


## Объект и предмет исследования

- Настройка рабочей среды linux

## Цель работы

- Получение навыков работы с pass и chezmoi


# Менеджер паролей pass

## Установка pass

- Установим pass

![](image/Screenshot_1.png)

## Установка gopass

- Установим gopass

![](image/Screenshot_2.png)


## Просмотр списка ключей

- Посмотрим список ключей

![](image/Screenshot_3.png)

## Инициализация хранилища и создание структуры

- Инициализируем хранилище и создаем структуру

![](image/Screenshot_5.png){#fig:001 width=80%}

## Создание репозитория

- Создадим репозиторий на сайте гитхаб:

![](image/Screenshot_6.png)

## Настройка репозитория

- Зададим адрес репозитория на хостинге ![](image/Screenshot_7.png)

- Для синхронизации выполним следующие команда ![](image/Screenshot_8.png)

![](image/Screenshot_9.png)

## Настройка пароля

- Следует заметить, что отслеживаются только изменения, сделанные через сам gopass (или pass).
- Если изменения сделаны непосредственно на файловой системе, необходимо вручную закоммитить и выложить изменения:

![](image/Screenshot_10.png){#fig:001 width=70%}

- Проверка статуса синхронизации ![](image/Screenshot_11.png)

## Установка плагина browserpass

- Плагин browserpass для Firefox

![https://addons.mozilla.org/en-US/firefox/addon/browserpass-ce/](image/Screenshot_12.1.png)


## Интерфейс для взаимодействия

- Интерфейс для взаимодействия с браузером (native messaging)

![](image/Screenshot_12.png)

## Установка  browserpass

- Непосредственно установка на сам linux

![](image/Screenshot_13.png)


## Сохранение пароля

- Добавить новый пароль

![](image/Screenshot_14.png)

- Отобразим пароль

![](image/Screenshot_15.png)

## Заменя пароля

- Заменим существующий пароль

![](image/Screenshot_16.png)


# Управление файлами конфигурации

## Дополнительное программное обеспечение

- Установим дополнительные программные обеспечения

![](image/Screenshot_17.png)


## Установка шрифтов

- Непосредственно сама установка шрифтов

![](image/Screenshot_20.png)

## Установка бинарного файл

- Установим бинарный файл. Скрипт определяет архитектуру процессора и операционную систему и скачивает необходимый файл:
с помощью wget:

![](image/Screenshot_21.png)


## Создание собственного репозитория с помощью утилит

- Создадим свой репозиторий для конфигурационных файлов на основе шаблона

![](image/Screenshot_22.png)

## Инициализация chezmoi

- Инициализируем chezmoi с нашим репозиторием dotfiles:

![](image/Screenshot_23.png)

## Внесение изменений

- Если нас устраивают изменения, внесённые chezmoi, запустим chezmoi apply -v

![](image/Screenshot_25.png)


## Инициализация chezmoi на второй машине и проверка изменений

- На второй машине инициализируем chezmoi с репозиторием dotfiles через ssh:

![](image/Screenshot_26.png)

- Проверим, какие изменения внесёт chezmoi в домашний каталог

![](image/Screenshot_27.png)

## Внесение изменений

- Если нас устраивают изменения, внесённые chezmoi, запустим chezmoi apply -v

![](image/Screenshot_28.png){#fig:001 width=50%}

- При существующем каталоге chezmoi можно получить и применить последние изменения из нашего репозитория

![](image/Screenshot_29.png)


## Настройка новой машины с помощью одной команды

- Можно установить свои dotfiles на новый компьютер с помощью одной команды через ssh

![](image/Screenshot_30.png)


# Ежедневные операции c chezmoi

## Извлечение последних изменений из репозитория и применения их

- Можно извлечь изменения из репозитория и применить их одной командой

![](image/Screenshot_31.png)

- Это запускается git pull --autostash --rebase в вашем исходном каталоге, а затем chezmoi apply.

## Извлечение последних изменений из репозитория и просмотр изменений, фактически не применяя изменения

- Выполним:

![](image/Screenshot_32.png)

- Это запускается git pull --autostash --rebase в вашем исходном каталоге, а chezmoi diff затем показывает разницу между целевым состоянием, вычисленным из вашего исходного каталога, и фактическим состоянием.

## Внесение изменений

- Если мы довольны изменениями, то можем применить их

![](image/Screenshot_33.png)


## Автоматическое фиксирование и отправка изменений в репозиторий

- Можно автоматически фиксировать и отправлять изменения в исходный каталог в репозиторий.
- Эта функция отключена по умолчанию.
- Чтобы включить её, добавим в файл конфигурации ~/.config/chezmoi/chezmoi.toml следующее:

![](image/Screenshot_34.png)

 
## Вывод:

Я научился пользоваться pass и chezmoi





