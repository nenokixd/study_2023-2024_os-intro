---
## Front matter
lang: ru-RU
title: Лабораторная работа №1
subtitle: Установка ОС Linux
author:
  - Чекмарев Александр Дмитриевич | Группа НПИбд-02-23
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 27 февраля 2024

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

- Установка ОС Linux на VirtualBox

## Цель работы

- Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, 
настройки минимально необходимых для дальнейшей работы сервисов.


# Ход лаборатороной работы

## Установка Virtualbox и Linux Fedora Sway Spin 39

- Скачаем и установим виртуальную машину

![Сайт: https://www.virtualbox.org/wiki/Downloads](image/рис 2.1.png){#fig:001 width=70%}

## Скачивание дистрибутива Fedora 

- Теперь нужно скачать дистрибутив Linux Fedora 39

![Сайт: https://fedoraproject.org/spins/sway/download ](image/рис 2.2.png){#fig:001 width=70%}

## Настройки для Fedora

- Выбираем iso образ, название, место
- Выделяем ОЗУ
- Выделяем 80 гб

![](image/рис 2.3.png){#fig:001 width=35%} ![](image/рис 2.4.png){#fig:001 width=35%}

![](image/рис 2.5.png){#fig:001 width=35%}

## Установка операционной системы

- Выбираем Русский язык, жесткий диск и включаем root права для пользователя

![](image/рис 2.6.png){#fig:001 width=35%} ![](image/рис 2.7.png){#fig:001 width=35%}

![](image/рис 2.8.png){#fig:001 width=35%}


## Настройка аккаунта пользователя и установка

- Создаем пользователя и приступаем к установке

![](image/рис 2.9.png){#fig:001 width=40%}![](image/рис 2.10.png){#fig:001 width=40%}

## Обновление пакетов

- Обновим все пакеты

![](image/рис 2.11.png)

## Установка tmux

- установим tmux

![](image/рис 2.12.png)

## Установка программного обеспечения для создания документации

- Установим pandoc
- Скачаем необходимую версию pandoc-crossref и поместим его в каталог /usr/local/bin.

![](image/рис 2.13.png){#fig:001 width=30%} ![https://github.com/lierdakil/pandoc-crossref/releases](image/рис 2.14.png){#fig:001 width=30%}

![](image/рис 2.15.png){#fig:001 width=30%}

## Установка TexLive

- Установим дистрибутив TeXlive: dnf -y install texlive-scheme-full

![](image/рис 2.16.png){#fig:001 width=60%}


## Вывод:

Я приобрел практические навыки установки операционной системы на виртуальную машину и настройки минимально необходимые для дальнейшей работы с Линуксом.



