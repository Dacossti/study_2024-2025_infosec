---
## Front matter
title: "Лабораторная работа № 3."
subtitle: "Дискреционное разграничение прав в Linux. Два пользователя"
author: "ОЗЬЯС Стев Икнэль Дани"

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

Цель данной работы --- получение практических навыков работы в консоли с атрибутами файлов для групп пользователей.


# Теоретическое введение

В Linux, как и в любой многопользовательской системе, абсолютно естественным образом возникает задача разграничения доступа субъектов — пользователей к объектам — файлам дерева каталогов.

Один из подходов к разграничению доступа — так называемый дискреционный (от англ, discretion — чье-либо усмотрение) — предполагает назначение владельцев объектов, которые по собственному усмотрению определяют права доступа субъектов (других пользователей) к объектам (файлам), которыми владеют.

Дискреционные механизмы разграничения доступа используются для разграничения прав доступа процессов как обычных пользователей, так и для ограничения прав системных программ в (например, служб операционной системы), которые работают от лица псевдопользовательских учетных записей.


# Выполнение лабораторной работы

1.  В установленной операционной системе создал учётную запись пользователя guest (использую учётную запись администратора): useradd guest (рис. [-@fig:001])

![Создание учётной записи пользователя guest](image/1.png){ #fig:001 width=70% }

2. Задал пароль для пользователя guest (использую учётную запись администратора): passwd guest (рис. [-@fig:002])

![Задание пароля для пользователя guest](image/2.png){ #fig:002 width=70% }

3. Аналогично создал второго пользователя guest. (рис. [-@fig:003])

![Создание второго пользователя guest](image/3.png){ #fig:003 width=70% }

4. Добавил пользователя guest2 в группу guest: gpasswd -a guest2 guest (рис. [-@fig:004])

![Добавление пользователя guest2 в группу guest](image/4.png){ #fig:004 width=70% }

5. Осуществил вход в систему от двух пользователей на двух разных консолях: guest на первой консоли и guest2 на второй консоли.(рис. [-@fig:005]

![Вход в систему от двух пользователей на двух разных консолях](image/5.png){ #fig:005 width=70% }

6. Для обоих пользователей командой pwd определил директорию, в которой нахожусь. Сравнил её с приглашениями командной строки (рис. [-@fig:006]

![Определение текущей директории](image/6.png){ #fig:006 width=70% }

7. Уточнил имя вашего пользователя, его группу, кто входит в неё и к каким группам принадлежит он сам.Определил командами groups guest и groups guest2, в какие группы входят пользователи guest и guest2. Сравнил вывод команды groups с выводом команд id -Gn и id -G. (рис. [-@fig:007])

![Запрос информации о пользователе](image/7.png){ #fig:007 width=70% }

8. Сравнил полученную информацию с содержимым файла /etc/group. Просмотрел файл командой cat /etc/group (рис. [-@fig:008])

![Сравнение полученной информации с содержимым файла](image/8.png){ #fig:008 width=70% }

9. От имени пользователя guest2 выполнил регистрацию пользователя guest2 в группе guest командой
newgrp guest (рис. [-@fig:009])

![Регистрация пользователя guest2 в группе guest](image/9.png){ #fig:009 width=70% }

10. От имени пользователя guest изменил права директории /home/guest, разрешив все действия для пользователей группы: chmod g+rwx /home/guest (рис. [-@fig:010])

![Изменение права директории /home/guest](image/10.png){ #fig:010 width=70% }

11. От имени пользователя guest снял с директории /home/guest/dir1 все атрибуты командой
chmod 000 dirl (рис. [-@fig:011])

![Снятие с директории /home/guest/dir1 всех атрибутов](image/11.png){ #fig:011 width=70% }

12. И проверил правильность снятия атрибутов.

Меняя атрибуты у директории dir1 и файла file1 от имени пользователя guest и делая проверку от пользователя guest2, заполнил первую таблицу, определив опытным путём, какие операции разрешены, а какие нет. Если операция разрешена, занес в таблицу знак «+», если не разрешена, знак «-».(рис. [-@fig:012])

![Заполнение первой таблицы](image/12.png){ #fig:012 width=70% }

13. Сравнил таблицу из лабораторной работы № 2 и полученную таблицу. На основании заполненной таблицы определил те или иные минимально необходимые права для выполнения пользователем guest2 операций внутри директории dir1 и заполнил вторую таблицу.(рис. [-@fig:013])

![СЗаполнение второй таблицы](image/13.png){ #fig:013 width=70% }


# Выводы

Я получил практические навыки работы в консоли с атрибутами файлов для групп пользователей.
   
# Список литературы{.unnumbered}

::: {#refs}
:::
