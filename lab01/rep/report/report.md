---
# Front matter
lang: ru-RU
title: "Лабораторная работа №1"
subtitle: "Информационная безопасность"
author: "Давтян Артур Арменович"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Задание

## Создать виртуальную машину
## Поставить на неё CentOS
## Настроить ОС
## Создать ещё одну машину на основе первой

# Выполнение лабораторной работы

## Настройка виртуальной машины 

Создаём новую виртуальную машину. Для этого в VirtualBox выбрать "Машина" -> "Создать". (рис. -@fig:001)

![Нажатие на кнопку "Создать"](image/1.png){ #fig:001 width=70% }

Укажем имя виртуальной машины — Base, тип операционной системы — Linux, RedHat. (рис. -@fig:002)

![Имя ВМ и тип ОС](image/2.png){ #fig:002 width=70% }

Укажем размер основной памяти виртуальной
машины — 4096 МБ. (рис. -@fig:003)

![Имя ВМ и тип ОС](image/3.png){ #fig:003 width=70% }

Зададим конфигурацию жёсткого диска — загрузочный, VDI (VirtualBox Disk Image), динамический виртуальный диск. (рис. -@fig:004 — -@fig:005)

![Тип жёсткого диска](image/4.png){ #fig:004 width=70% }

![Формат хранения](image/5.png){ #fig:005 width=70% }

Зададим размер диска — 40 ГБ — и его расположение. (рис. -@fig:006)

![Размер и расположение диска](image/6.png){ #fig:006 width=70% }

Запустим виртуальную машину Base, выберем образ для установки системы. (рис. -@fig:007)

![Запуск и выбор образа](image/7.png){ #fig:007 width=70% }

Установим русский язык. (рис. -@fig:008)

![Установка русского языка](image/8.png){ #fig:008 width=70% }

Установим дату и время. (рис. -@fig:009)

![Установка даты и времени](image/9.png){ #fig:009 width=70% }

Выберем нужный жёсткий диск. (рис. -@fig:010)

![Выбор жёсткого диска](image/10.png){ #fig:010 width=70% }

Выберем вариант установки "Рабочая станция". (рис. -@fig:011)

![Выбор варианта установки](image/11.png){ #fig:011 width=70% }

Зададим имя узла. (рис. -@fig:012)

![Имя узла](image/12.png){ #fig:012 width=70% }

Зададим пароль для root. (рис. -@fig:013)

![Пароль root](image/13.png){ #fig:013 width=70% }

Зададим имя пользователя и пароль, сделаем пользователя администратором. (рис. -@fig:014)

![Новый пользователь](image/14.png){ #fig:014 width=70% }

## Настройка ОС CentOS

Зайдём в терминал, выдадим права root с помощью команды su и обновим программы с помощью команды yum update. (рис. -@fig:015)

![Новый пользователь](image/15.png){ #fig:015 width=70% }

Установим файловый менеджер Midnight Commander с помощью команды yum install mc. (рис. -@fig:016)

![Установка Midnight Commander](image/16.png){ #fig:016 width=70% }

## Создание второй виртуальной машины на основе первой

Поменяем тип жёсткого диска с "Обычный" на "С множественным подключением" для того, чтобы другие виртуальные машины могли использовать машину Base и её конфигурацию как базовую. (рис. -@fig:017)

![Смена типа жёсткого диска](image/17.png){ #fig:017 width=70% }

Создадим новую виртуальную машину под названием Host2 и используем для нее существующий виртуальный диск Base. (рис. -@fig:018)

![Новая ВМ](image/18.png){ #fig:018 width=70% }

# Выводы

Приобрел практические навыки установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.