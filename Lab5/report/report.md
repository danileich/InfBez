---
## Front matter
title: "Лабораторная работа № 5"
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

Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

# Выполнение лабораторной работы

## Создание программы

1. Вошёл в систему от имени пользователя guest и создал программу simpleid.c(@fig:001).

![Код программы в редакторе Emacs](./image/img1.png){#fig:001}

2. Скомпилировал и выполнил программу simpleid.(@fig:002).

![Успешная компиляция и запуск simpleid. Запуск системной программы id](./image/img2.png){#fig:002}


3. Усложнил программу, добавив вывод действительных идентификаторов(@fig:003).

![Код программы в редакторе Emacs](./image/img3.png){#fig:003}

4. Скомпилировал и запустил simpleid2.c(@fig:004).

![Успешная компиляция](./image/img4.png){#fig:004}

5. От имени суперпользователя выполнил команды:
```
chown root:guest /home/guest/simpleid2
chmod u+s /home/guest/simpleid2
```
Далее я выполнил проверку правильности установки новых атрибутов и смены владельца файла simpleid2, после чего запустил simpleid2 и id. И проделал то же самое относительно SetGID-бита(@fig:005).

![Успешная компиляция с новым владельцем файла](./image/img5.png){#fig:005}

6. Создал программу readfile.c и успешно скомпилировал её(@fig:006).

![Код программы в редакторе Emacs](./image/img6.png){#fig:006}

7. Сменил владельца у файла readfile.c и изменил права так, чтобы только суперпользователь (root) мог прочитать его, a guest не мог, после чего проверил, что пользователь guest не может прочитать файл readfile.c(@fig:007).

![Смена прав и владельца и проверка чтения файла](./image/img7.png){#fig:007}

8. Сменил у программы readfile владельца и установил SetU’D-бит, после чего проверил, может ли программа readfile прочитать файлы readfile.c и /etc/shadow(@fig:008 - @fig:009 - @fig:010).

![Смена прав и владельца](./image/img8.png){#fig:008}

![Проверка функционала файла](./image/img9.png){#fig:009}

![Чтение файла /etc/shadow](./image/img10.png){#fig:010}

## Исследование Sticky-бита

1. Выяснил, установлен ли атрибут Sticky на директории /tmp. От имени пользователя guest я создал файл file01.txt в директории /tmp со словом test, далее просмотрел атрибуты у только что созданного файла и разрешил чтение и запись для категории пользователей «все остальные»(@fig:011 - @fig:012).

![Смена прав и владельца](./image/img11.png){#fig:011}

![проверка атрибутов программы](./image/img12.png){#fig:012}

2. От пользователя guest2 я прочитал файл /tmp/file01.txt и дозаписал в файл слово test. Далее я записал в файл /tmp/file01.txt слово test3, стерев при этом всю имеющуюся в файле информацию и проверил содержимое файла командой. Я попробовал удалить файл file01.txt(@fig:013).

![Редактирование файла](./image/img13.png){#fig:013}

Однако в ответ я получил отказ от выполнения операции.

3. Повысил свои права до суперпользователя, затем снял атрибут t с директории /tmp, после чего покинул режим суперпользователя командой exit. От имени пользователя guest2 проверил, что атрибута t у директории /tmp
нет, после чего повторил те же действия. Теперь я могу удалить файл file01.txt. Повысил свои права до суперпользователя и вернул атрибут t на директорию /tmp(@fig:014).

![Редактирование файла в режиме суперпользователя](./image/img14.png){#fig:014}

# Вывод

Изучил механизмы изменения идентификаторов, применения SetUID- и Sticky-битов, получил практических навыков работы в консоли с дополнительными атрибутами, а также рассмотрел работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.