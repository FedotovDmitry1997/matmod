---
# Front matter
lang: ru-RU
title: "Лабораторная работа №4"
subtitle: "Модель гармонических колебаний"
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

	Цель четвертой лабораторной работы - рассмотреть модель линейного 
	гармонического осциллятора.

# Задание

1. Построить решение уравнения гармонического осциллятора без затухания 

2. Записать уравнение свободных колебаний гармонического осциллятора с затуханием, построить его решение. Построить фазовый портрет гармонических колебаний с затуханием.

3. Записать уравнение колебаний гармонического осциллятора, если на систему действует внешняя сила, построить его решение. Построить фазовый портрет колебаний с действием внешней силы.

# Выполнение лабораторной работы

## Теоретическое введение
	Движение грузика на пружинке, маятника, заряда в электрическом контуре,
 а также эволюция во времени многих систем в физике, химии, биологии и других
 науках при определенных предположениях можно описать одним и тем же
 дифференциальным уравнением, которое в теории колебаний выступает в качестве
 основной модели. Эта модель называется линейным гармоническим осциллятором.

   Уравнение свободных колебаний гармонического осциллятора имеет следующий вид:

$$ \ddot {x} + 2 \gamma \dot {x} + w_0^2x = f(t) $$

$x$ — переменная, описывающая состояние системы 

$\gamma$ — параметр, характеризующий потери энергии

$w$ — собственная частота колебаний

$t$ — время

Обозначения: $$ \ddot{x} = \frac{\partial^2 x}{\partial t^2}, \dot{x} = \frac{\partial x}{\partial t}$$

	Уравнение

$$ \ddot {x} + 2 \gamma \dot {x} + w_0^2x = f(t) $$ 

есть линейное однородное дифференциальное уравнение второго порядка и оно является
примером линейной динамической системы
	При отсутствии потерь в системе $$ \gamma = 0 $$ получаем уравнение
 консервативного осциллятора, энергия колебания которого сохраняется во времени.

$$ \ddot {x} + w_0^2x = 0 $$


   Для однозначной разрешимости уравнения второго порядка необходимо задать два начальных условия вида:

$$ \begin{cases} x(t_0) = x_0 \\ \dot{x}(t_0) = y_0 \end{cases} $$

   Уравнение второго порядка можно представить в виде системы двух уравнений первого порядка:

$$ \begin{cases} \dot{x} = y \\ \dot{y} = -w_0^2x \end{cases} $$

   Начальные условия для системы примут вид:

$$ \begin{cases} x(t_0) = x_0 \\ y(t_0) = y_0 \end{cases} $$

   Независимые переменные x, y определяют пространство, в котором «движется» решение. Это фазовое пространство системы, поскольку оно двумерно будем называть его фазовой плоскостью.
   
   Значение фазовых координат x, y в любой момент времени полностью определяет состояние системы. Решению уравнения движения как функции времени отвечает гладкая кривая в фазовой плоскости. Она называется фазовой траекторией. Если множество различных решений (соответствующих различным начальным условиям) изобразить на одной фазовой плоскости, возникает общая картина поведения системы. Такую картину, образованную набором фазовых траекторий, называют фазовым портретом.

## Вариант выполненой работы 

1. Колебания гармонического осциллятора без затуханий и без действий внешней силы $\ddot {x} + 8.8x = 0$

2. Колебания гармонического осциллятора c затуханием и без действий внешней силы $\ddot {x} + 8 \dot {x} + 8x = 0$

3. Колебания гармонического осциллятора c затуханием и под действием внешней силы $\ddot {x} + 8 \dot {x} + 8x = 0.8sin(8t)$

На интервале $t \in [0; 88]$(шаг 0.05) с начальными условиями $x_0 = 1.8, y_0 = 0.8$

## Код на Python


```
import math
import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plt

w = math.sqrt(8.8);
g = 0.00;
w2 = math.sqrt(8);
g2 = 4;
w3 = math.sqrt(8);
g3 = 4;

#Правая часть уравнения

#Первый случай

def f(t):
    f = 0
    return f


#Второй случай

def f2(t_2):
    f2 = 0
    return f2


#Третий случай

def f3(t_3):
    f3 = 0.8*np.sin(8*t_3)
    return f3


# Вектор-функция f(t, x) для решения системы дифференциальных
 уравнений x' = y(t, x)

#Первый случай

def y(x, t):
    dx1 = x[1]
    dx2 = - w*w*x[0] - 2*g*x[1] - f(t)
    return dx1, dx2

#Второй случай

def y22(x_2, t_2):
    dx_21 = x_2[1]
    dx_22 = - w2*w2*x_2[0] - 2*g2*x_2[1] - f2(t_2)
    return dx_21, dx_22

#Третий случай 

def y33(x_3, t_3):
    dx_31 = x_3[1]
    dx_32 = - w3*w3*x_3[0] - 2*g3*x_3[1] - f3(t_3)
    return dx_31, dx_32


# Вектор начальных условий x(t0) = x0

x0 = np.array([1.8, 0.8])

x_20 = np.array([1.8, 0.8])

x_30 = np.array([1.8, 0.8])


# Интервал, на котором будет решаться задача

t = np.arange(0, 88, 0.05)

t_2 = np.arange(0, 88, 0.05)

t_3 = np.arange(0, 88, 0.05)


# Решаем дифференциальные уравнения с начальным условием 
x(t0) = x0 на интервале t с правой частью, заданной y и записываем решение 
в матрицу x

x = odeint(y, x0, t)

x_2 = odeint(y22, x_20, t_2)

x_3 = odeint(y33, x_30, t_3)

y1 = x[:,0]

y2 = x[:,1]

y_22 = x_2[:,1]

y_22 = x_2[:,1]

y_31 = x_3[:,0]

y_32 = x_3[:,1]


# Строим фазовый портрет

#Первый случай

plt.plot(y1,y2, 'o')
plt.grid(axis='both')    

#Второй случай

plt.plot(y_21,y_22)
plt.grid(axis='both')

#Третий случай

plt.plot(y_31,y_32)
plt.grid(axis='both')
```

## Графики

График первого случая. Колебания гармонического осциллятора без затуханий и без действий внешней силы $\ddot {x} + 8.8x = 0$ (рис. -@fig:001)

![Первый случай](images/1.png){ #fig:001 width=70% }

График второго случая. Колебания гармонического осциллятора c затуханием и без действий внешней силы $\ddot {x} + 8 \dot {x} + 8x = 0$ (рис. -@fig:002)

![Второй случай](images/2.png){ #fig:002 width=70% }

График третьего случая. Колебания гармонического осциллятора c затуханием и под действием внешней силы $\ddot {x} + 8 \dot {x} + 8x = 0.8sin(8t)$ (рис. -@fig:003)

![Третий случай](images/3.png){ #fig:003 width=70% }

## Ответы на вопросы

1. Простейшая модель гармонических колебаний $x = x_m cos (ωt + φ0)$. 
    
2. Осциллятор — система, совершающая колебания, то есть показатели которой периодически повторяются во времени.

3. Уравнение динамики принимает вид: $$\frac{d^2 \alpha}{d t^2} + \frac{g}{L} sin{\alpha} = 0$$ В случае малых колебаний полагают $sin{\alpha} ≈ \alpha$. В результате возникает линейное дифференциальное уравнение $$\frac{d^2 \alpha}{d t^2} + \frac{g}{L} \alpha = 0$$ или $$\frac{d^2 \alpha}{d t^2} + \omega^2 \alpha = 0$$

4. В дифференциальное уравнение 2-го порядка $$ \ddot {x} + w_0^2x = f(t) $$ сделаем замену $$ y = \dot{x} $$.

Получим систему уравнений:
	 $$ \begin{cases} y = \dot{x} \\ \dot{y} = - w_0^2x \end{cases}$$

5. Фазовая траектория — это гладкая кривая на фазовой плоскосте, описывающаа движение с помощью функции времени.

Фазовый портрет — это картина, которая возникает при изображении множества решений на фазовой плоскости.

# Выводы
В ходе выполнения работы я научился:

1. Строить решение уравнения гармонического осциллятора без затухания 

2. Строить решение уравнения и фазовый портрет свободных колебаний гармонического осциллятора с затуханием.

3. Строить решение уравнения и фазовый портрет свободных колебаний гармонического осциллятора с затуханием, с действием внешней силы.