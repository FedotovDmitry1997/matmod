---
# Front matter
lang: ru-RU
title: "Лабораторная работа 7"
subtitle: "Математическое моделирование"
author: "Федотов Дмитрий Константинович"
teacher: "Кулябов Дмитрий Сергеевич"

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

	Цель седьмой лабораторной работы - рассмотреть модель 
эффективности рекламы.

# Задание

1. Построить график распространения рекламы о салоне красоты в разных случаях.

2. Сравнить эффективность рекламной кампании в разных случаях.

3. Определить в какой момент времени эффективность рекламы будет иметь максимально быстрый рост.

4. Построить решение, если учитывать вклад только платной рекламы.

5. Построить решение, если предположить, что информация о товаре распространятся только путем  сарафанного радио, сравнить оба решения.

# Выполнение лабораторной работы

## Теоретическое введение

Организуется рекламная кампания нового товара или услуги. Необходимо, чтобы прибыль будущих продаж с избытком покрывала издержки на рекламу. Вначале расходы могут превышать прибыль, поскольку лишь малая часть потенциальных покупателей будет информирована о новинке. Затем, при увеличении числа продаж, возрастает и прибыль, и, наконец, наступит момент, когда рынок насытится, и рекламировать товар станет бесполезным.

Предположим, что торговыми учреждениями реализуется некоторая продукция, о которой в момент времени t из числа потенциальных покупателей N знает лишь n покупателей. Для ускорения сбыта продукции запускается реклама по радио, телевидению и других средств массовой информации. После запуска рекламной кампании информация о продукции начнет распространяться среди потенциальных покупателей путем общения друг с другом. Таким образом, после запуска рекламных объявлений скорость изменения числа знающих о продукции людей пропорциональна как числу знающих о товаре покупателей, так и числу покупателей о нем не знающих.

Модель рекламной кампании описывается следующими величинами. Считаем, что $\frac{\partial n}{\partial t}$ — скорость изменения со временем числа потребителей, узнавших о товаре и готовых его купить, t — время, прошедшее с начала рекламной кампании, n(t) — число уже информированных клиентов. Эта величина пропорциональна числу покупателей, еще не знающих о нем.

 Это описывается следующим образом:

$$ \alpha_1(t)(N-n(t)) $$

N — общее число потенциальных платежеспособных покупателей

$\alpha_1(t)>0$ — характеризует интенсивность рекламной кампании (зависит от затрат на рекламу в данный момент времени).

Помимо этого, узнавшие о товаре потребители также распространяют полученную информацию среди потенциальных покупателей, не знающих о нем (в этом случае работает т.н. сарафанное радио). Этот вклад в рекламу описывается величиной

$$ \alpha_2(t)n(t)(N-n(t)) $$ эта величина увеличивается с увеличением потребителей узнавших о товаре. 

Математическая модель распространения рекламы описывается уравнением:

$$ \frac{\partial n}{\partial t} = (\alpha_1(t) + \alpha_2(t)n(t))(N - n(t))$$

При $\alpha_{1}(t)\gg \alpha_{2}(t)$ получается модель типа модели Мальтуса, решение которой имеет вид (рис. -@fig:001):

![График решения уравнения модели Мальтуса](images\1.png){ #fig:001 width=70% }

В обратном случае, при $\alpha_{1}(t)\ll \alpha_{2}(t)$ получаем уравнение логистической кривой (рис. -@fig:002):

![График логистической кривой](images\2.png){ #fig:002 width=70% }

## Вариант выполненой работы 

Постройте график распространения рекламы, математическая модель которой описывается следующим уравнением:

- $\frac{\partial n}{\partial t} = (0.605 + 0.000015n(t))(N - n(t))$

- $\frac{\partial n}{\partial t} = (0.000025 + 0.205n(t))(N - n(t))$

- $\frac{\partial n}{\partial t} = (0.05sin(t) + 0.31cos(t)n(t))(N - n(t))$

При этом объем аудитории $N$ = 1515, в начальный момент о товаре знает 12 человек.

Для случая 2 определите в какой момент времени скорость распространения рекламы будет иметь максимальное значение.

## Выполнение работы на языке Python

1. Зададим начальные условия (рис. -@fig:003).

![Начальные условия](images\3.png){ #fig:003 width=70% }

2. Составим функции, отвечающие за платную рекламу и сарафанное радио для пяти случаев (рис. -@fig:004). 

![Функции, отвечающие за платную рекламу и сарафанное радио](images\4.png){ #fig:004 width=70% } 

3. Составим уравнения,описывающие распростронение рекламы для пяти случаев (рис. -@fig:005). 

![Уравнения описывающие распространение рекламы](images\5.png){ #fig:005 width=70% } 

4. Составим решение  ОДУ для пяти случаев (рис. -@fig:006). 

![Решение ОДУ](images\6.png){ #fig:006 width=70% } 

5. Построим график распространения рекламы для $\frac{\partial n}{\partial t} = (0.605 + 0.000015n(t))(N - n(t))$ (рис. -@fig:007).

![Первый случай](images\7.png){ #fig:007 width=70% } 

6. Построим график распространения рекламы для $\frac{\partial n}{\partial t} = (0.000025 + 0.205n(t))(N - n(t))$ (рис. -@fig:008).

![Второй случай](images\8.png){ #fig:008 width=70% } 

7. Найдем в какой момент времени скорость распространения рекламы будет иметь максимальное значение (рис. -@fig:009).

![Момент времени с максимальной скоростью](images\9.png){ #fig:009 width=70% }

8. Построим график распространения рекламы для $\frac{\partial n}{\partial t} = (0.05sin(t) + 0.31cos(t)n(t))(N - n(t))$ (рис. -@fig:010).

![Третий случай](images\10.png){ #fig:010 width=70% } 

9. Построим график распространения рекламы для трех случаев (рис. -@fig:011).

![Три случая](images\11.png){ #fig:011 width=70% } 

10. Построим графики распространения рекламы для случаев, когда есть только сарафанное радио и только платная реклама (рис. -@fig:012).

![Только сарафанное радио и только платная реклама](images\12.png){ #fig:012 width=70% } 

## Ответы на вопросы 

1. Записать модель Мальтуса (дать пояснение, где используется данная модель)

$\frac{\partial N}{\partial t} = rN$

- N-исходная численность населения 

- r-коэффициент прироста числености населения

- t-время.

-  Используется в популяционной экологии как первый принцип популяционной динамики

2. Записать уравнение логистической кривой (дать пояснение, что описывает данное уравнение)

$$ \frac{\partial P}{\partial t} = rP(1 - \frac{P}{K}) $$

- P-численность популяции

- t-время

- r-скорость размножения

- K-поддерживающая ёмкость среды

Исходя из названия коэффициентов, в экологии часто различают две стратегии поведения видов: r-стратегия предполагает бурное размножение и короткую продолжительность жизни особей,K-стратегия — низкий темп размножения и долгую жизнь.

3. На что влияет коэффициент $\alpha_1(t)$ и $\alpha_2(t)$ в модели распространения рекламы.

$\alpha_1(t)$ — интенсивность рекламной кампании, зависящая от затрат, $\alpha_2(t)$ — интенсивность рекламной кампании, зависящая от сарафанного радио.

4. Как ведет себя рассматриваемая модель при $\alpha_1(t) \gg \alpha_2(t)$

При $\alpha_{1}(t)\gg \alpha_{2}(t)$ получается модель типа модели Мальтуса, решение которой имеет вид (рис. -@fig:013):

![График решения уравнения модели Мальтуса](images\13.png){ #fig:013 width=70% }

5. Как ведет себя рассматриваемая модель при $\alpha_1(t) \ll \alpha_2(t)$

При $\alpha_1(t) \ll \alpha_2(t)$ получаем уравнение логистической кривой (рис. -@fig:014):

![График логистической кривой](images\14.png){ #fig:014 width=70% }

## Выводы

1. Построил график распространения рекламы о салоне красоты.

2. Сравнил эффективность рекламной кампании при $\alpha_1(t) > \alpha_2(t)$ и $\alpha_1(t) < \alpha_2(t)$.

3. Определил в какой момент времени эффективность рекламы будет иметь максимально быстрый рост.

4. Построил решение, если учитывать вклад только платной рекламы.

5. Построил решение, если предположить, что информация о товаре распространятся только путем «сарафанного радио», сравнить оба решения.



