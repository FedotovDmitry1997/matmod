---
# Front matter
lang: ru-RU
title: "Лабораторная работа №6"
subtitle: "Задача об эпидемии"
author: "Федотов Дмитрий Константинович"

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

Построить графики изменения числа особей в каждой из трех групп:

- количество инфицированных особей в начальный момент времени.

- количество восприимчивых к болезни особей в начальный момент времени.

- количество здоровых особей с иммунитетом в начальный момент времени

Рассмотреть, как будет протекать эпидемия в разных случаях:
- $I(0) \leq I^*$ 

- $I(0) > I^*$

# Выполнение лабораторной работы

## Теоретическое введение

### Задача об эпидемии

Рассмотрим простейшую модель эпидемии. Предположим, что некая популяция, состоящая из N особей, (считаем, что популяция изолирована) подразделяется на три группы. Первая группа - это восприимчивые к болезни, но пока здоровые особи, обозначим их через S(t). Вторая группа – это числоинфицированных особей, которые также при этом являются распространителями инфекции, обозначим их I(t). А третья группа, обозначающаяся через R(t) – это здоровые особи с иммунитетом к болезни. 


До того, как число заболевших не превышает критического значения $I^*$ считаем, что все больные изолированы и не заражают здоровых. Когда $I(t)>I^*$, тогда инфицирование способны заражать восприимчивых к болезни особей.

Таким образом, скорость изменения числа S(t) меняется по следующему закону:

$$ \frac{\partial S}{\partial t} = \begin{cases} - \alpha S, если I(t)>I^* \\ 0, если I(t) \leq I^* \end{cases}$$

Поскольку каждая восприимчивая к болезни особь, которая, в конце концов, заболевает, сама становится инфекционной, то скорость изменения числа инфекционных особей представляет разность за единицу времени между заразившимися и теми, кто уже болеет и лечится, т.е.:

$$ \frac{\partial I}{\partial t} = \begin{cases} - \alpha S - \beta I, если I(t)>I^* \\ - \beta I, если I(t) \leq I^* \end{cases}$$

А скорость изменения выздоравливающих особей (при этом приобретающие иммунитет к болезни)

$$ \frac{\partial R}{\partial t} = \beta I$$

Постоянные пропорциональност $\alpha$ и $\beta$ коэффициент заболеваемости и выздоровления соответственно.

Для того, чтобы решения соответствующих уравнений определялось однозначно, необходимо задать начальные условия. Считаем, что на начало эпидемии в момент времени $t = 0$ нет особей с иммунитетом к болезни $R(0)=0$, а число инфицированных и восприимчивых к болезни особей $I(0)$ и $S(0)$ соответственно. Для анализа картины протекания эпидемии необходимо рассмотреть два случая: $I(0) \leq I^*$ и $I(0) > I^*$

## Условие моего варианта

Вариант 64:

- N = 14987
- I(0) = 187
- R(0) = 68
- S(0)=N - I(0) - R(0)
- a = 0.011
- b = 0.28

## Код на Python

1. Зададим начальные условия (рис. -@fig:001).

![Начальные условия](images\1.png){ #fig:001 width=70% }

2. Начальные значения в момент времени 0 (рис. -@fig:002).

![Начальные значения](images\2.png){ #fig:002 width=70% }

3. Задаем интервал и шаг (рис. -@fig:003).

![Интервал и шаг](images\3.png){ #fig:003 width=70% }

4. Напишем функцию для решения системы дифференциальных уравнений для первого случая (рис. -@fig:004).

![Функция для решения уравнений для $I(0) \leq I^{*}$](images\4.png){ #fig:004 width=70% }

5. Напишем функцию для решения системы дифференциальных уравнений для второго случая (рис. -@fig:005).

![Функция для решения уравнений для $I(0) \leq I^{*}$](images\5.png){ #fig:005 width=70% }

6. Построим график изменения для случая $I(0) \leq I^{*}$] (рис. -@fig:006).

![$I(0) \leq I^{*}$](images\6.png){ #fig:006 width=70% }

7. Построим график изменения для случая $I(0) \leq I^{*}$] (рис. -@fig:007).

![$I(0) > I^{*}$](images\7.png){ #fig:007 width=70% }

## Графики

Графики изменения числа особей в каждой из трех групп при  $I(0) \leq I^{*}$] (рис. -@fig:008).

![$I(0) \leq I^{*}$](images/8.png){ #fig:008 width=70% }

Графики изменения числа особей в каждой из трех групп при  $I(0) > I^{*}$] (рис. -@fig:008).

![$I(0) > I^{*}$](images/9.png){ #fig:009 width=70% }

# Выводы

Построил графики изменения числа особей в каждой из трех групп:

- количество инфицированных особей в начальный момент времени.

- количество восприимчивых к болезни особей в начальный момент времени.

- количество здоровых особей с иммунитетом в начальный момент времени

Рассмотрел, как будет протекать эпидемия в разных случаях:
- $I(0) \leq I^*$ 

- $I(0) > I^*$