---
# Front matter
lang: ru-RU
title: "Лабораторная работа №4"
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

Получение практических навыков работы в консоли с расширенными атрибутами файлов.


# Выполнение лабораторной работы

## Установка расширенного атрибута a

От имени пользователя `guest` опредяем расширенные атрибуты файла `/home/guest/dir1/file1` командой `lsattr /home/guest/dir1/file1` и в нашем случае получаем отсутствие прав для всех групп пользователей. (рис. -@fig:001)

![Определение расширенного атрибута](image/1.png){ #fig:001 width=70% }

Устанавливаем командой `chmod 600 dir1/file1` на файл `file1` права, разрешающие чтение и запись для владельца файла. (рис. -@fig:002)

![Установка прав](image/2.png){ #fig:002 width=70% }

Попробуем установить на файл `/home/guest/dir1/file1` расширенный атрибут `a` от имени пользователя `guest`: `chattr +a /home/guest/dir1/file1`. В ответ получаем отказ от выполнения операции. (рис. -@fig:003)

![Расширенный атрибут от имени гостя](image/3.png){ #fig:003 width=70% }


Тогда, зайдя на вторую консоль с правами администратора, попробуем установить расширенный атрибут `a` на файл `/home/guest/dir1/file1` от имени суперпользователя: `chattr +a /home/guest/dir1/file1`. В ответ ошибку не получаем - значит всё установилось успешно. (рис. -@fig:004)

![Расширенный атрибут от имени администратора](image/4.png){ #fig:004 width=70% }

От пользователя `guest` убеждаемся в правильности установления атрибута: `lsattr /home/guest/dir1/file1`. (рис. -@fig:005)

![Проверка от имени гостя](image/5.png){ #fig:005 width=70% }

## Работа с файлом с расширенным атрибутом a

Выполняем дозапись в файл `file1` слова «test» командой `echo "test" >> /home/guest/dir1/file1`. После этого выполняем чтение файла `file1` командой `cat /home/guest/dir1/file1`. В выводе получаем текст, записанный до выполнения предыдущей команды, а также наше слово `test` в конце файла. (рис. -@fig:006)

![Дозапись](image/6.png){ #fig:006 width=70% }

Пробуем стереть имеющуюся в файле `file1` информацию командой `echo "abcd" > /home/guest/dirl/file1`. Но получаем ошибку - операция не разрешена. Пробуем переименовать файл командой `mv dir1/file1 dir1/file2`. Также получаем сообщение об ошибке. (рис. -@fig:007)

![Удаление и переименование](image/7.png){ #fig:007 width=70% }

Пробуем с помощью команды `chmod 000 file1` установить на файл `file1` права, например, запрещающие чтение и запись для владельца файла. И вновь получаем сообщение об ошибке. (рис. -@fig:008)

![Расширенный атрибут от имени гостя](image/8.png){ #fig:008 width=70% }

## Работа с файлом без расширенного атрибута a

Снимаем расширенный атрибут `a` с файла `/home/guest/dirl/file1` от имени суперпользователя командой `chattr -a /home/guest/dir1/file1`. (рис. -@fig:009)

![Расширенный атрибут от имени гостя](image/9,1.png){ #fig:009 width=70% }

Повторяем операции, которые ранее нам не удалось выполнить. Теперь же все операции прошли успешно: мы смогли перезаписать информацию в файле, переименовать `file1` в `file2`, а также снять все атрибуты. (рис. -@fig:010)

![Расширенный атрибут от имени гостя](image/9,2.png){ #fig:010 width=70% }

## Работа с файлом с расширенным атрибутом i

Установливаем расширенный атрибут `i` на файл `/home/guest/dir1/file1` от имени суперпользователя: `chattr +i /home/guest/dir1/file1`.

Теперь повторяем все предыдущие операции над файлом `file1`.

Убеждаемся в правильности установления атрибута: `lsattr /home/guest/dir1/file1`. Выполняем дозапись в файл `file1` слова «test» командой `echo "test" >> /home/guest/dir1/file1`. Получем сообщение об ошибке - отказано в доступе. После этого выполняем чтение файла `file1` командой `cat /home/guest/dir1/file1`. В выводе получаем текст, записанный до выполнения предыдущей команды, но слова `test` в конце файла нет - операция не прошла.

Также пробуем стереть имеющуюся в файле `file1` информацию командой `echo "abcd" > /home/guest/dirl/file1`. Но получаем ошибку - операция не разрешена.
Пробуем переименовать файл командой `mv dir1/file1 dir1/file2`. Также получаем сообщение об ошибке. (рис. -@fig:011)

![Повторение операций с атрибутом i](image/10.png){ #fig:011 width=70% }


# Выводы

В ходе выполнения лабораторной работы получили практические навыки работы в консоли с расширенными атрибутами файлов «а» и «i».