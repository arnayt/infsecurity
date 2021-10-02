---
# Front matter
lang: ru-RU
title: "Лабораторная работа №2"
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

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Задание

## Создать нового пользователя (гостя)
## Научиться работать с атрибутами файлов и директорий

# Выполнение лабораторной работы

## Создание нового пользователя

Создаём новую учётную запись. Для этого в консоли пропишем:

``` useradd guest ```

После этого зададим пароль с помощью команды:

``` passwd guest ``` (рис. -@fig:001)

![Создание учётной записи](image/1.png){ #fig:001 width=70% }

Войдём в систему от имени гостя (только что созданной учётной записи). (рис. -@fig:002)

![Вход в систему](image/2.png){ #fig:002 width=70% }

С помощью команды ``` pwd ``` определим директорию, в которой находимся. Сравнивая с приглашением командной строки, обнаруживаем, что всё верно. Также определяем, что находимся в домашней директории пользователя guest. (рис. -@fig:003)

![Команда pwd](image/3.png){ #fig:003 width=70% }

Уточним имя пользователя с помощью команды ``` whoami ```. (рис. -@fig:004 — -@fig:005)

![Хто я?](image/4.png){ #fig:004 width=70% }

Уточним имя пользователя, его группу, а также группы, куда входит пользователь, командой ```id```.

Сравнивая вывод id с выводом команды groups, обнаружим, что группы, в которые входит пользователь, действительно одинаковые. Также, сравнивая вывод id c приглашением командной строки, обнаружим, что имя пользователя повторяется. (рис. -@fig:006)

![Команда id](image/5.png){ #fig:005 width=70% }

Откроем файл ```/etc/passwd``` с помощью команды ```cat /etc/passwd```. Найдём в нём свою учётную запись. Определим uid пользователя. Определите gid пользователя. Сравнивая найденные значения с полученными в предыдущих пунктах, видим, что они сходятся.

![Файл /etc/passwd](image/6.png){ #fig:006 width=70% }

## Работа с атрибутами файлов и директорий

Определим существующие в системе директории командой ```ls -l /home/```. Нам удалось получить список поддиректорий. У каждой из них установлены права на чтение, запись и выполнение только для самого пользователя.(рис. -@fig:007)

![Существующие директории](image/7.png){ #fig:007 width=70% }

Проверьте, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории ```/home```, командой:

```lsattr /home```

Нам удалось увидеть расширенные атрибуты директории, но не удалось увидеть расширенные атрибуты директорий других
пользователей. (рис. -@fig:008)

![Расширенные атрибуты](image/8.png){ #fig:008 width=70% }

Создадим в домашней директории поддиректорию ```dir1``` командой

```mkdir dir1```

Определим командами ```ls -l``` и ```lsattr```, какие права доступа и расширенные атрибуты были выставлены на директорию ```dir1```. (рис. -@fig:009)

![Создание новой директории](image/9.png){ #fig:009 width=70% }

Снимем с директории ```dir1``` все атрибуты командой

```chmod 000 dir1```

и проверим с её помощью правильность выполнения команды
```ls -l```. (рис. -@fig:010)

![Снятие атрибутов с директории](image/10.png){ #fig:010 width=70% }

Попытаемся создать в директории dir1 файл file1 командой

```echo "test" > /home/guest/dir1/file1```

Мы получим отказ от выполнения, так как шагом ранее сняли все атрибуты с директории. Проверим, действительно ли файл не создался, с помощью команды

```ls -l /home/guest/dir1```. (рис. -@fig:011)

![Попытка создания файла](image/11.png){ #fig:011 width=70% }

Заполним таблицу «Установленные права и разрешённые действия». (рис. -@fig:012 — -@fig:014)

![Таблица УПиРД ч.1](image/12.png){ #fig:012 width=95% }

![Таблица УПиРД ч.2](image/13.png){ #fig:013 width=95% }

![Таблица УПиРД ч.3](image/14.png){ #fig:014 width=95% }

Заполним таблицу «Минимальные права для совершения операций». (рис. -@fig:015)

![Таблица МПдСО](image/15.png){ #fig:015 width=95% }

# Выводы

Получил практические навыки работы в консоли с атрибутами файлов, закрепил теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.