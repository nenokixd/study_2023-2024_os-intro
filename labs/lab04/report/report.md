---
## Front matter
title: "Отчёт по лабораторной работе №4"
subtitle: "Продвинутое использование git"
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

Получение навыков продвинутой работы с репозиториями git.


# Выполнение лабораторной работы

## Установка программного обеспечения

### Установка git-flow

Установим git-flow

Установка из коллекции репозиториев Copr  
(https://copr.fedorainfracloud.org/coprs/elegos/gitflow/):

![Рис 1.1.1: установка copr](image/Screenshot_1.png)

Теперь сам git-glow

![Рис 1.1.2: установка git-flow](image/Screenshot_2.png)

### Установка Node.js

Установим Node.js

На Node.js базируется программное обеспечение для семантического версионирования и общепринятых коммитов.

![Рис 1.2.1: установка nodejs](image/Screenshot_3.png)

Так как у нас выводится ошибка при установке pnpm (невозможно найти пакет), то перейдем к ручной установке.

![Рис 1.2.2: ошибка](image/Screenshot_4.png)

Перейдем на https://pnpm.io/installation и ввдем следующую команду: *wget -qO- https://get.pnpm.io/install.sh | sh -*

![Рис 1.2.3: установка через сайт](image/Screenshot_5.png)

### Настройка Node.js

Перейдем к настройке Node.js

Сначала перелгонимися: *source ~/.bashrc*  
После запустим pnpm

![Рис 1.3.1: проверка работы pnpm](image/Screenshot_6.png)


## Общепринятые коммиты

### commitizen

Данная программа используется для помощи в форматировании коммитов: *pnpm add -g commitizen*

![Рис 2.1.1: добавление/установка программы](image/Screenshot_7.png)

При этом устанавливается скрипт git-cz, который мы и будем использовать для коммитов.

### standard-changelog

Данная программа используется для помощи в создании логов: *pnpm add -g standard-changelog*

![Рис 2.2.1: добавление/установка программы](image/Screenshot_8.png)

### Практический сценарий использования git

1. Создание репозитория git
  - Подключение репозитория к github
 Создадим репозиторий на GitHub. Для примера назовём его git-extended.

 ![Рис 2.3.1: сайт для скачивания iso образа Fedora](image/Screenshot_9.png)

 Далее скачаем/клонируем репозиторий

 ![Рис 2.3.2: сайт для скачивания iso образа Fedora](image/Screenshot_10.png)

 Делаем первый коммит и выкладываем на github:  
 git add .  
 git commit -m "first commit"  
 git remote add origin git@github.com:<username>/git-extended.git  
 git push -u origin master
 
 ![Рис 2.3.3: сайт для скачивания iso образа Fedora](image/Screenshot_12.png)

  - Конфигурация общепринятых коммитов  
 Конфигурация для пакетов Node.js  
 *pnpm init*
 
 ![Рис 2.3.4: сайт для скачивания iso образа Fedora](image/Screenshot_13.png)
 
 Необходимо заполнить несколько параметров пакета.
 
 Название пакета.  
 Лицензия пакета. Список лицензий для npm: https://spdx.org/licenses/. Предлагается выбирать лицензию CC-BY-4.0.  
 Сконфигурируем формат коммитов. Для этого добавим в файл package.json команду для формирования коммитов:  
 
 "config": {  
     "commitizen": {  
         "path": "cz-conventional-changelog"   
     }  
 }
 
 
 Таким образом, файл package.json приобретает вид:

 ![Рис 2.3.5: сайт для скачивания iso образа Fedora](image/Screenshot_14.png)
 
 Добавим новые файлы, выполним коммит, отправим на github:  
 git add .  
 git cz  
 git push  
 
 ![Рис 2.3.6: сайт для скачивания iso образа Fedora](image/Screenshot_15.png)

  - Конфигурация git-flow

 Инициализируем git-flow: *git flow init*
 
 ![Рис 2.3.7: сайт для скачивания iso образа Fedora](image/Screenshot_16.png)

 Префикс для ярлыков установим в v.

 Проверим, что мы на ветке develop: *git branch*
 
 ![Рис 2.3.8: сайт для скачивания iso образа Fedora](image/Screenshot_17.png)

 Загрузим весь репозиторий в хранилище: *git push --all*
 
 ![Рис 2.3.9: сайт для скачивания iso образа Fedora](image/Screenshot_18.png)

 Установим внешнюю ветку как вышестоящую для этой ветки: *git branch --set-upstream-to=origin/develop develop*
 
 ![Рис 2.3.10: сайт для скачивания iso образа Fedora](image/Screenshot_19.png)

 Создадим релиз с версией 1.0.0: *git flow release start 1.0.0*

 ![Рис 2.3.11: сайт для скачивания iso образа Fedora](image/Screenshot_20.png)

 Создадим журнал изменений: *standard-changelog --first-release*

 ![Рис 2.3.12: сайт для скачивания iso образа Fedora](image/Screenshot_21.png)

 Добавим журнал изменений в индекс  
 
 git add CHANGELOG.md  
 git commit -am 'chore(site): add changelog'
 
 ![Рис 2.3.13: сайт для скачивания iso образа Fedora](image/Screenshot_22.png)

 Зальём релизную ветку в основную ветку: *git flow release finish 1.0.0*
 
 ![Рис 2.3.14: сайт для скачивания iso образа Fedora](image/Screenshot_23.png)

 
 Отправим данные на github  

 git push --all  
 git push --tags
 
 
 ![Рис 2.3.15: сайт для скачивания iso образа Fedora](image/Screenshot_24.png)


 Создадим релиз на github. Для этого будем использовать утилиты работы с github:  
 *gh release create v1.0.0 -F CHANGELOG.md*
 
 ![Рис 2.3.16: сайт для скачивания iso образа Fedora](image/Screenshot_25.png)

2. Работа с репозиторием git
  - Разработка новой функциональности
 Создадим ветку для новой функциональности: *git flow feature start feature_branch*
 
 ![Рис 2.3.17: сайт для скачивания iso образа Fedora](image/Screenshot_26.png)

 
 Далее, продолжаем работу c git как обычно.
 По окончании разработки новой функциональности следующим шагом следует объединить ветку feature_branch c develop:  
 *git flow feature finish feature_branch*
 
 ![Рис 2.3.18: сайт для скачивания iso образа Fedora](image/Screenshot_27.png)

 
  - Создание релиза git-flow
 Создадим релиз с версией 1.2.3: *git flow release start 1.2.3*

 ![Рис 2.3.19: сайт для скачивания iso образа Fedora](image/Screenshot_28.png)

 Обновим номер версии в файле package.json.
 
 ![Рис 2.3.20: сайт для скачивания iso образа Fedora](image/Screenshot_29.png)

 Создадим журнал изменений и добавим его в индекс:  
 
 standard-changelog  
 git add CHANGELOG.md  
 git commit -am 'chore(site): update changelog'
 
 
 ![Рис 2.3.21: сайт для скачивания iso образа Fedora](image/Screenshot_30.png)

 Зальём релизную ветку в основную ветку: *git flow release finish 1.2.3*

 ![Рис 2.3.22: сайт для скачивания iso образа Fedora](image/Screenshot_31.png)

 Отправим данные на github и создадим релиз на github с комментарием из журнала изменений:  
 
 git push --all  
 git push --tags  
 gh release create v1.2.3 -F CHANGELOG.md
 
 
 ![Рис 2.3.23: сайт для скачивания iso образа Fedora](image/Screenshot_32.png)

# Выводы

Я получил навыки продвинутой работы с репозиториями git.


# Список литературы{.unnumbered}

::: {#refs}
:::
