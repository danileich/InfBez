---
## Front matter
title: "Лабораторная работа № 2"
subtitle: "Дисциплина: Информационная безопасность"
author: "Новосельцев Данила Сергеевич"

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
lot: false
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

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Выполнение лабораторной работы

1. Создал учетную запись пользователя guest и задал пароль(@fig:001).

![Создание и настройка пароля учетной записи](./image/img1.png){#fig:001}


2. Вошёл в систему от имени пользователя guest и определил директорию, в которой нахожусь, после чего перешел в домашнюю папку пользователя guest(@fig:002).

![Вход в новосозданную учетную запись и переход в домашнюю папку](./image/img2.png){#fig:002}

3. Уточнил имя пользователя, его группу, а также группы, куда входит пользователи. Просмотрел файл /etc/passwd и проверил, какие расширенные атрибуты установлены на поддиректориях текущего пользователя, находящихся в директории /home(@fig:003).

![Характеристика пользователя guest](./image/img3.png){#fig:003}

4. Создал в домашней директории поддиректорию dir1 и вывел права доступа и расширенные атрибуты(@fig:004).

![Создание поддиректории и проверка прав доступа и атрибутов](./image/img4.png){#fig:004}

5. Снял с директории dir1 все атрибуты, попытался создать в поддиректории dir1 файл file1(@fig:005).

![Попытка создания файла после снятия вех атрибутов с директории](./image/img5.png){#fig:005}

Поскольку я не обладаю правами, я не могу создать файл, вследствие чего получил ошибку Permission Denied.

12. Заполнил таблицу установленных прав и разрешённых действий(@fig:006).

![Таблица «Установленные права и разрешённые действия»](./image/img6.png){#fig:006}

13. Заполнил таблицу минимальных прав для совершения операций(@fig:007).

![Таблица «Минимальные права для совершения операций»](./image/img7.png){#fig:007}

# Выводы

Получены практические навыки работы в консоли с атрибутами файлов, а также были закреплены теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Список литературы{.unnumbered}

[1] https://esystem.rudn.ru/pluginfile.php/2090273/mod_resource/content/6/002-lab_discret_attr.pdf