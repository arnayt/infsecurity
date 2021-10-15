---
# Front matter
lang: ru-RU
title: "Лабораторная работа №3"
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

Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей.

# Задание

## Создать второго нового пользователя (гостя)
## Научиться работать с атрибутами файлов и директорий группы

# Выполнение лабораторной работы

## Создание нового пользователя

Учетная запись guest в моей операционной системе уже существует. Она была создана при выполнении прошлой лабораторной работы. (рис. -@fig:001)

![Доказательство существования учётной записи](image/1.png){ #fig:001 width=70% }

Пароль для данной учетной записи также был установлен в прошлый раз. (рис. -@fig:002)

![Доказательство существования пароля](image/2.png){ #fig:002 width=70% }

Создам второго пользователя guest2. Для этого в консоли пропишем:

``` useradd guest ```

После этого зададим пароль с помощью команды:

``` passwd guest ``` (рис. -@fig:003)

![Создание учётной записи](image/3.png){ #fig:003 width=70% }

Добавлю пользователя guest2 в группу guest. (рис. -@fig:004)

![Добавление в группу](image/4.png){ #fig:004 width=70% }

Осуществлю вход в систему от двух пользователей на двух разных консолях: guest на первой консоли и guest2 на второй консоли. (рис. -@fig:005)

![Вход на двух консолях](image/5.png){ #fig:005 width=70% }


Для обоих пользователей командой ```pwd``` определю директорию, в которой нахожусь. Ели сравнить директорию с приглашениями командной, то они совпадают. (рис. -@fig:006)

![Команда pwd](image/6.png){ #fig:006 width=70% }

Уточню имя каждого пользователя (команда ```whoami```), его группу (команды ```groups guest``` и ```groups guest2```), кто входит в неё и к каким группам принадлежит он сам. (рис. -@fig:007)

![Имя пользователя и группы](image/7.png){ #fig:007 width=70% }

Сравню вывод команды groups с выводом команд ```id -Gn``` и ```id -G```. Первая команда выводит на экран группы пользователя, но без уточнения к какому пользователю относятся группы, т.к. команды работаю только для пользователя, через которого открыта консоль. Вторая команда выводи код группы пользователя. (рис. -@fig:008)

![Выводы команд](image/8.png){ #fig:008 width=70% }

Сравню полученную информацию с содержимым файла /etc/group. Просмотрю файл командой ```cat /etc/group```.  (рис. -@fig:009 — -@fig:010)

![/etc/group 1](image/9.png){ #fig:009 width=70% }

![/etc/group 2](image/10.png){ #fig:010 width=70% }

## Работа с атрибутами файлов и директорий

От имени пользователя guest2 выполню регистрацию пользователя guest2 в группе guest командой newgrp guest. (рис. -@fig:011)

![Регистрация](image/11.png){ #fig:011 width=70% }

1От имени пользователя guest изменю права директории /home/guest, разрешив все действия для пользователей группы:

```chmod g+rwx /home/guest``` (рис. -@fig:012)

![Права директории](image/12.png){ #fig:012 width=70% }

От имени пользователя guest сниму с директории /home/guest/dir1 все атрибуты командой ```chmod 000 dir1``` и проверю правильность снятия атрибутов. (рис. -@fig:013)

![Атрибуты](image/13.png){ #fig:013 width=70% }

Меняя атрибуты у директории dir1 и файла file1 от имени пользователя guest и делая проверку от пользователя guest2, заполню таблицу «Установленные права и разрешённые действия», определяя опытным путём, какие операции разрешены, а какие нет. (рис. -@fig:014 — -@fig:019)

![Таблица УПиРД ч.1](image/15.png){ #fig:014 width=95% }

![Таблица УПиРД ч.2](image/16.png){ #fig:015 width=95% }

![Таблица УПиРД ч.3](image/17.png){ #fig:016 width=95% }

![Таблица УПиРД ч.4](image/18.png){ #fig:017 width=95% }

![Таблица УПиРД ч.5](image/19.png){ #fig:018 width=95% }

![Таблица УПиРД ч.6](image/20.png){ #fig:019 width=95% }

Заполним таблицу «Минимальные права для совершения операций». (рис. -@fig:020)

![Таблица МПдСО](image/21.png){ #fig:020 width=95% }

# Выводы

Получил практические навыки работы в консоли с атрибутами файлов для групп пользователей.