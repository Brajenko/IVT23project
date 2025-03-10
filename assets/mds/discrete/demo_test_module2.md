# Задание 1 - производящие функции
Задание на производящие функции - определимся, что это. Производящая функция - функция вида
$$A(x) = \sum_{n=0}^\infty a_nx^n$$
То есть такой бесконечный многочлен с коэффициентами $a_n$. Производящая функция либо сразу пишется как $A(x)$, либо задается через последовательность $a_n$.

Полезными операциями для производящих функций - смещение начала.
Допустим, есть у нас функция $A(x)$, и мы хотим построить новую функцию $B(x)$, для которой коэффициенты $b_i$ смещены на $k$ элементов вправо от $a_i$. При этом, чтобы сохранить нумерацию, первые $k$ элементов будут занулены. Можно записать $b_n$ следующим образом:
$$b_n = \cases{a_{n-k}, & $n \geq k$ \\ 0, & $0\leq n<k$}$$
Тогда, функцию $B(x)$ можно выразить через $A(x)$ следующим образом:
$$B(x) = x^kA(x)$$
И ведь действительно, первые элементы суммы зануляются, и степень $x^k$ можно вынести из под суммы по дистрибутивности:
$$\array{B(x) = \sum\limits_{n=0}^\infty b_nx^n = b_0 + b_1x + \ldots + b_{k-1}x^{k-1}+\sum\limits_{n=k}^\infty b_{n}x^n = \\ = 0 + \sum\limits_{n=0}^\infty b_{n+k}x^{n+k} = \sum\limits_{n=0}^\infty a_nx^{n+k} = x^{k}\sum\limits_{n=0}^\infty a_nx^n = x^kA(x)}$$

Альтернативно можно построить $B(x)$, для которой коэффициенты $b_i$ смещены на $k$ элементов *влево* от $a_i$, хоть выглядит и немного страшнее:
$$b_{n} = a_{n+k} \Rightarrow B(x) = \frac{1}{x^k} \left(A(x) - \sum_{n=0}^{k-1}a_nx^n\right)$$
К счастью, она только выглядит страшно - в скобках мы из первоначальной функции вычитаем первые $k$ элементов - получится, будто первые $k$ элементов равны нулю, прямо как в примере до этого, когда мы смещали вправо - и в скобках получается $x^k B(x)$. Чтобы получить просто $B(x)$, соответственно нужно поделить на этот $x^k$, и получаем формулу выше.

С некоторыми производящими функциями вы уже встречались - в частности, ряд Маклорена - это производящая функция
$$a_n = 1 \Rightarrow A(x) = \sum\limits_{n=0}^\infty x^n = \frac{1}{1-x}, \ \ \ \ |x|<1$$
$$a_n = n \Rightarrow A(x) = \sum_{n=0}^\infty nx^n = \frac{x}{(1-x)^2}, \ \ \ \ \ |x|<1$$
$$a_n = \frac1{n!} \Rightarrow A(x) = \sum\limits_{n=0}^\infty \frac{x^n}{n!} = e^x$$
и т.д.

А теперь попробуем посмотреть на задачки:
## Пример 1
Дана производящая функция числовой последовательности $a_n$:
$$A(x) = \frac{1}{1-x}$$
Найти числовую последовательность.

Решение: вообще мы умные и сразу знаем, что числовая последовательность $a_n = 1$, ведь это сумма бесконечной геометрической прогрессии. Но формальное решение, наверное, выглядит как-то так: умножим обе стороны на $1-x$:
$$(1-x)A(x)=1 \Leftrightarrow A(x) - xA(x) = 1$$
Расписываем как суммы:
$$\sum\limits_{n=0}^\infty a_nx^n - x\sum\limits_{n=0}^\infty a_nx^n = 1$$
$$\sum\limits_{n=0}^\infty a_nx^n = 1 + \sum\limits_{n=0}^\infty a_nx^{n+1}$$
Смещаем индекс суммы справа:
$$\sum\limits_{n=0}^\infty a_nx^n = 1 + \sum\limits_{n=1}^\infty a_{n-1}x^{n}$$
Левые и правые части равны - сравним коэффициенты при $x^n$ слева и справа:
- Для $a_0x^0$ слева соответствует $1$ справа.
- Для $a_nx^n$ слева соответствует $a_{n-1}x^n$ справа.

$$a_0x^0 + a_1 x^1 + a_2x^2 + a_3x^3 + \ldots = 1 + a_0x^1 + a_1x^2 + a_2x^3 + \ldots$$
Из этого делаем вывод, что $a_0 = 1$, и $a_n = a_{n-1}$, а значит $a_n = 1$ для всех $n \geq 0$.

Ответ: $a_n = 1, \ \ \ \ n \geq 0$.

## Пример 2
Дана числовая последовательность $a_n = 1^n$, $n = 0,1,2,3,\ldots$.
Производящая функция $A(x)$ числовой последовательности $a_n$ дифференциируема. Найти числовую последовательность $b_n$, для которой $A'(x)$ является производящей функцией, где $A'(x)$ - производная $A(x)$.

Решение: записываем функцию, дифференциируем сумматор, смещаем сумму так, чтобы внутри суммы находился $x^n$, и выделяем $b_n$.
$$\array{A(x) = \sum\limits_{n=0}^\infty a_nx^n \\ A'(x) = \left(\sum\limits_{n=0}^\infty a_nx^n  \right)' = \sum\limits_{n=0}^\infty (a_nx^n)' = \sum\limits_{n=0}^\infty na_nx^{n-1}}$$
Т.к. первый член равен нулю, можем его убрать и сместить индекс с нуля до единицы:
$$A'(x) = \sum\limits_{n=1}^\infty na_nx^{n-1}$$
Теперь смещаем индекс в сумме с единицы до нуля - а внутри суммы заменяем все $n$ на $n+1$:
$$A'(x) = \sum\limits_{n=0}^\infty (n+1)a_{n+1}x^n$$
И теперь мы можем выразить отсюда $b_n$:
$$\array{b_n = (n+1)a_{n+1}, \ \ \ n\geq 0 \\ B(x) = \sum\limits_{n=0}^\infty b_nx^n = \sum\limits_{n=0}^\infty (n+1)a_{n+1}x^n}$$
Учитывая условие $a_n = 1^n = 1$, то из ответа попросту пропадает $a_{n+1}$.

Ответ: $b_n = (n+1)a_{n+1}, \ \ \ n\geq 0$, или же $b_n = n+1, \ \ \ \ n \geq 0$.

## Пример 3
Дана числовая последовательность $a_n = 1^n$, $n = 0,1,2,3,\ldots$.
Производящая функция $A(x)$ числовой последовательности $a_n$ интегрируема. Найти числовую последовательность $b_n$, для которой $B(x)$ является производящей функцией, где $B(x)$ - первообразная $A(x)$.

Решение: тут план такой же, просто интегрируем вместо дифференциирования.
$$A(x) = \sum\limits_{n=0}^\infty a_nx^n$$
$$B(x) = \int \left(\sum\limits_{n=0}^\infty a_nx^n  \right)\dd x = \sum\limits_{n=0}^\infty \int a_nx^n\dd x = \sum\limits_{n=0}^\infty \frac{a_n}{n+1}x^{n+1} + C_{n+1}$$
$C_n$ - константа интегрирования для $n$-ного члена. Смещаем индекс суммы с нуля до единицы, заодно заменяем все $n+1$ на $n$:
$$B(x) = \sum\limits_{n=1}^\infty \frac{a_{n-1}}{n}x^{n} + C_{n}$$
Вот отсюда мы и можем взять $b_n$:
$$b_n = \frac{a_{n-1}}n, \ \ \ \ n \geq 1$$
Все константы интегрирования $C_n$ в сумме дают $b_0$ - но так как $b_0$ состоит из констант интегрирования, то он может принимать любое значение.
$$b_0 \in \mathbb R$$
В любом случае, при дифференциировании производящей функции от последовательности $b_n$, коэффициент $b_0$ просто уйдет.

Учитывая условие $a_n = 1^n = 1$, то из ответа попросту пропадает $a_{n-1}$.

Ответ: $b_n = \frac{a_{n-1}}n, \ \ n\geq 1$, или же $b_n = \frac1n, \ \ n\geq 1$, (и если есть желание выпендриться,) $b_0 \in \mathbb R$.

# Задание 2 - линейные (не)однородные рекуррентные соотношения
По своей структуре, очень напоминают дифференциальные уравнения, можете сами проводить параллели по ходу чтения. Есть два способа решения - через формулу (производящую функцию) и через характеристический многочлен.

Тут я предлагаю сразу решать и рассказывать по ходу.
## Пример 1
Найти явное решение линейного рекуррентного соотношения с помощью производящей функции:
$$a_{n+2} = a_{n+1}+2a_n, \ \ \ \ a_0=1, a_1=2$$
Решение: все как будто в диффурах, где слева находится однородное ДУ, справа - задача Коши.

В общем виде, ЛНРС выглядит так:
$$a_{n+k} = C_1a_{n+k-1} + C_2a_{n+k-2} + \ldots + C_ka_{n} + d_n$$
- $a_0, \ldots, a_{k-1}$ - начальные условия.
- $C_1, \ldots, C_k$ - коэффициенты ЛНРСа.
- $d_n$ - последовательность от $n$, и имеет производящую функцию $D(x)$.

Общим решением называется выражение для $a_n$ в закрытой форме (без других $a_{n+k}$). Явным решением - общее решение, с подставленными начальными условиями $a_0, \ldots, a_{k-1}$.

Так вот явное решение через производящую функцию выглядит так:
$$A(x) = \frac{P_{k-1}(x) - x^kD(x)}{1-C_1x-C_2x^2-\ldots-C_kx^k}$$
где
$$P_{k-1}(x) = \sum\limits_{i=0}^{k-1}a_ix^i - C_1x\sum\limits_{i=0}^{k-2}a_ix^i - \ldots -C_{k-1}x^{k-1}a_0$$
или же эквивалентно
$$P_{k-1}(x) = a_0 + x(a_1-C_1x_0) + \ldots + x^{k-1}(a_{k-1}-C_1a_{k-2}-\ldots-C_{k-1}a_0)$$
- У нас $d_n \equiv 0$ (однородное линейное соотношение, все уравнение состоит лишь из слагаемых $C\cdot a_{n+i}$), поэтому $D(x)$ тоже равно нулю.
- $k$ - это степень соотношения, то самое $k$ в общем виде ЛНРС. У нас максимальный член $a_{n+2}$, поэтому $k=2$.
- $C_1 = 1, C_2 = 2$ - их мы берем из данного уравнения (смотрим общий вид ЛНРС).
- $a_0 = 1, a_1 = 2$, это дано по условию в правой части.

Составим наше $P_{k-1}(x)$, подставляя начальные условия.:
$$\array{P_{k-1}(x) = P_1(x) =a_0 + x(a_1 - C_1a_0) = a_0 + xa_1 - xC_1a_0 \\ P_1(x) = 1 + 2x - C_1x = 1 + x(2-C_1) = 1+x}$$
Подставляем и получаем $A(x)$:
$$A(x) = \frac{1+x}{1-C_1x-C_2x^2} = \frac{1+x}{1-x-2x^2}$$
Но мы получили производящую функцию, а хочется вычленить отсюда $a_n$. Для этого методом неопределенных коэффициентов разобьем дробь на сумму и представим их как геометрические ряды. Да простит бог за то, что я хочу сейчас сделать:
$$\frac{1+x}{1-x-2x^2} = -\frac{1+x}{2x^2+x-1}$$
Вам не показалось - ***я вынес минус***. Представим $2x^2+x-1$ как произведение - не забываем про то, что произведение корней надо умножать на коэффициент $a$:
$$ax^2+bx+c = a(x-x_0)(x-x_1)$$
$$2x^2+x-1 = 2(x+1)(x-\frac12)$$
$$A(x) = -\frac{1+x}{2x^2+x-1} = -\frac12 \frac{1+x}{(x+1)(x-\frac12)}$$
По-хорошему тут надо было использовать неопределенные коэффициенты, но здесь и так $x+1$ сокращается и остается просто
$$-\frac{1}{2}\frac1{x-\frac12} = \frac{1}{1-2x}$$
Такую дробь мы можем представить как бесконечно убывающую геометрическую прогрессию:
$$A(x) = \frac{1}{1-2x} = \sum\limits_{n=0}^\infty (2x)^n = \sum\limits_{n=0}^\infty 2^nx^n$$
И уже здесь четко видно, что $a_n = 2^n$.

Ответ: $a_n = 2^n$.

Бонусный пример: пусть будет дробь
$$\frac{8-5x}{(3-2x)(2-x)}$$
Неопределенными коэффициентами бы мы ее привели к
$$\frac{2}{2-x} + \frac{1}{3-2x}$$
Каждую дробь нужно привести к виду $\frac1{1-qx}$, чтобы затем превратить ее в геометрический ряд. Для этого, при необходимости, нужно выносить за скобки минус и вычитаемые значения:
$$\frac{2}{2-x} = \frac 22 \cdot \frac{1}{1-\frac x2} = \sum_{n=0}^\infty \left(\frac x2\right)^n = \sum_{n=0}^\infty \left(\frac 12\right)^nx^n$$
$$\frac{1}{3-2x} = \frac{1}{3} \cdot \frac{1}{1-\frac{2x}3} = \frac13\sum_{n=0}^\infty \left(\frac {2x}3\right)^n = \frac13\sum_{n=0}^\infty \left(\frac 23\right)^nx^n$$
Итого
$$\frac{2}{2-x} + \frac{1}{3-2x} = \sum_{n=0}^\infty \left(\frac 12\right)^nx^n + \frac13\sum_{n=0}^\infty \left(\frac 23\right)^nx^n$$
Заносим ряды справа под один сумматор и получаем выражение для $a_n$:
$$\sum_{n=0}^\infty \left(\frac 12\right)^nx^n + \frac13\sum_{n=0}^\infty \left(\frac 23\right)^nx^n = \sum_{n=0}^\infty \left(\left(\frac 12\right)^n +\frac13\left(\frac 23\right)^n\right)x^n$$
$$a_n = \left(\frac 12\right)^n +\frac13\left(\frac 23\right)^n$$
## Пример 2
Найти явное решение линейного рекуррентного соотношения с помощью характеристического многочлена:
$$a_{n+2} = a_{n+1}+2a_n, \ \ \ \ a_0=1, a_1=2$$
Решение: если вы не почувствовали диффуры в прошлом примере, то здесь чувство будет еще сильнее. Первым делом перенесем все однородные кусочки в левую часть уравнения, чтобы справа остался ноль:
$$a_{n+2}-a_{n+1}-2a_n = 0$$
Теперь составляем характеристический многочлен (и характеристическое уравнение). Для общей формы ЛОРС
$$C_{n+k}a_{n+k} + C_{n+k-1}a_{n+k-1} + \ldots + C_{n}a_n = 0$$
характеристическое уравнение выглядит как
$$C_{n+k}x^k+C_{n+k-1}x^{k-1} + \ldots + C_n = 0$$
то есть все $a_{n+i}$ превращаются в $x^i$, очень схоже с тем, как составляется характеристический многочлен для ДУ.

Составим и для нашего ЛОРС характеристическое уравнение:
$$x^2 - x - 2=0 \Leftrightarrow (x+1)(x-2)=0$$
Записываем для уравнения как его корни $\alpha$, так и их кратность $r$.
$$\array{\alpha_1 = -1&:& r=1 \\ \alpha_2 = 2 &:& r=1}$$
И - о шок - общее решение ЛОРС составляется точно так же, как и для ОДУ, если есть $m$ различных корней:
$$a_{n_{\text{O-общ}}} = P_1(n)\alpha_1^{n} + P_2(n)\alpha_2^{n} + \ldots +P_m(n)\alpha_m^{n}$$
где $P_i(n)$ - многочлен ($r_i-1$)-той степени с неопределенными коэффициентами:
$$P_i(n) = p_{0,i} + p_{1,i}n + \ldots + p_{r-1, i}n^{r-1}$$
Соответственно, когда все корни различны, общее решение будет выглядеть просто:
$$a_{n_{\text{O-общ}}} = p_1\alpha_1^n + p_2\alpha_2^n + \ldots + p_m\alpha_m^n$$
Составим и для нашего ЛОРС общее решение:
$$a_{n_{\text{O-общ}}} = p_1 (-1)^n + p_22^n$$
Превратим *общее* решение в *явное*, подставив начальные условия:
$$\cases{a_0 = p_1(-1)^0 + p_22^0 \\ a_1 = p_1(-1)^1 + p_22^1} \Rightarrow \cases{1 = p_1 + p_2 \\ 2 = -p_1 + 2p_2} \Rightarrow \cases{p_2 = 1 \\ p_1 = 0}$$
Получаем
$$a_{n_{\text{явн}}} = 2^n$$
Ответ: $a_n = 2^n$.

## Пример 3
Найти общее решение линейного рекуррентного соотношения с помощью характеристического многочлена:
$$a_{n+2} = 2a_{n+1}+3a_n+2^n$$
Решение: все решения все равно начинаются с решения ЛОРС, даже если видна неоднородность в виде $2^n$. Оставим однородную часть слева, неоднородную - справа:
$$a_{n+2}-2a_{n+1}-3a_n = 2^n$$
Составляем характеристическое уравнение, находим корни, все стандартно:
$$x^2 -2x - 3 = 0 \Leftrightarrow (x+1)(x-3)=0$$
$$\array{\alpha_1 = -1 &:& r=1 \\ a_2=3 &:& r=1}$$
Составляем общее решение ЛОРС:
$$a_{n_{\text{O-общ}}} = p_1 (-1)^n + p_23^n$$
Теперь для каждого слагаемого в неоднородной части (прямо как для ДУ) мы составляем свой частный кусок решения. Если неоднородность находится в форме
$$(d_0 + d_1n + \ldots + d_mn^m)\alpha^n$$
то частное решение для него будет в форме
$$n^r (p_0 + p_1n + \ldots + p_mn^m)\alpha^n$$
Степень многочлена $m$ сохраняется равной степени многочлена в неоднородности. Иногда множителя $\alpha^n$ нет в явном виде (например, неоднородность это только многочлен). Тогда принимаем, что $\alpha = 1$, ибо тогда $1^n = 1$ и он не влияет на результат. $r$ - кратность корня $\alpha$ среди всех корней характеристического многочлена. Если $\alpha$ не является корнем характеристического многочлена, то $r=0$. $p_0, \ldots, p_m$ - неопределенные коэффициенты.

Составим частное решение для неоднородности $2^n$. Степень многочлена при нем равна нулю (многочлена нет), $\alpha=2$, но корнем характеристического многочлена не является: $r=0$. Тогда:
$$a_{{n}_{\text{частн}_1}} = p_0 2^n$$
И снова по аналогии с ДУ, теперь мы подставляем это частное решение в текущее ЛНРС и находим все неопределенные коэффициенты.
$$\array{p_02^{n+2} -2p_02^{n+1}-3p_02^n=2^n \ \ \ |:2^n \\ p_02^2 - 2p_02 - 3p_0 = 1 \\ -3p_0 = 1 \Rightarrow p_0 = -1/3}$$
Получаем частное решение с найденным коэффициентом:
$$a_{{n}_{\text{частн}_1}} = -\frac{2^n}3$$
И по традиции: общее решение ЛНРС - это сумма общего решения ЛОРС и частного решения ЛНРС:
$$a_{n_{\text{общ}}} = p_1 (-1)^n + p_23^n - \frac{2^n}3$$
Ответ: $a_n = p_1 (-1)^n + p_23^n - \frac{2^n}3$.

Бонусом напоминаю, что если бы было, например, такое уравнение:
$$a_{n+2} = 2a_{n+1}+3a_n+2^n + (3+x)4^n$$
мы бы находили частное решение по отдельности для каждых из двух уравнений:
$$\left[\array{a_{n+2}-2a_{n+1}-3a_{n} = 2^n \\ a_{n+2}-2a_{n+1}-3a_{n} = (3+x)4^n}\right.$$
и затем складывали все вместе.

# Задание 3 - матрицы графов
## Пример 1
Дан орграф $G$:
![[discrete-2-2-1.svg]]
Составить матрицу смежности для орграфа.

Решение: орграф значит ***ор***иентированный ***граф*** - то есть со стрелочками.

Матрица смежности - квадратная матрица, в которой по строчкам и столбцам стоят вершины графа (точки). На пересечении $i$-той строки и $j$-того столбика стоит количество ребер, которые выходят из $i$-той вершины и входят в $j$-тую вершину. Так как обычно две вершины соединены не более чем одним путем, матрица состоит лишь из нулей и единиц - хотя если вдруг будет несколько ребер выходящих из $i$ и входящих в $j$, там уже будет больше единицы.

Если граф неориентированный, то матрица получится симметричной. Если же ориентированный - то всегда смотрим именно на дуги (ориентированные ребра), которые выходят из вершины ***в строке***, и входят в вершину ***в столбике***. Для этого орграфа матрица смежности выглядит как
$$\array{
    & [1] & [2] & [3] & [4] \\
[1] & 0 & 0 & 1 & 0 \\
[2] & 1 & 0 & 1 & 0 \\
[3] & 0 & 1 & 0 & 1 \\
[4] & 1 & 1 & 0 & 0}$$
## Пример 2
Дан орграф $G$:
![[discrete-2-2-2.svg]]
Составить матрицу инцидентности для орграфа.

Решение: матрица инцидентности - прямоугольная (в общем случае) матрица, где строчки соответствуют вершинам матрицы, а столбики - ребрам. В случае ориентированного графа, если из вершины выходит дуга, то в строке этой вершины ставится $1$. Если же дуга входит в вершину, то в строке этой вершины ставится $-1$. В противном случае ставится $0$. Если же граф неориентирован, ставится $1$ в обоих случаях.

Для данного орграфа матрица инцидентности выглядит так:
$$\array{
    & [1'] & [2'] & [3'] & [4'] & [5'] & [6'] & [7']\\
[1] & -1 & 0 & 0 & 0 & 1 & -1 & 0 \\
[2] & 1 & -1 & 1 & -1 & 0 & 0 & 0 \\
[3] & 0 & 1 & -1 & 0 & -1 & 0 & 1 \\
[4] & 0 & 0 & 0 & 1 & 0 & 1 & -1}$$

## Пример 3
Дан нагруженный орграф $G$:
![[discrete-2-2-3.svg]]
Составить весовую матрицу для орграфа.

Решение: не сильно отличается от матрицы смежности. Единственное, что мы теперь не пишем нули и единички, а записываем веса ребер между двумя вершинами. В клетках на диагонали остаются нули* (ничего не стоит перейти из клетки $i$ в клетку $i$), а в клетках между вершинами, не соединенных ребрами, ***ставится знак бесконечности.***

В орграфе вес ставится в клетке, в строке где находится начало дуги, и в столбике где находится конец дуги. В неориентированном графе вес ставится в клетки симметрично.

\*начинают возникать вопросы, когда только у некоторых вершин стоят ребра-петли с весом - это стоит уточнять.
$$\array{
    & [1] & [2] & [3] & [4] \\
[1] & 0 & \infty & 6 & \infty \\
[2] & 2 & 0 & 4 & \infty \\
[3] & \infty & 5 & 0 & 1 \\
[4] & 2 & 3 & \infty & 0}$$
# Задание 4 - жадные алгоритмы минимального остова
## Пример 1
Дан нагруженный граф $G$:
![[discrete-2-2-4.svg]]

Построить минимальное остовное дерево нагруженного графа, применяя алгоритм Прима, и найти его вес.

Решение: разбираемся с терминами.
- Дерево - граф без циклов
- Остовное дерево графа - дерево, которое содержит в себе все вершины этого графа. Обычно остовное дерево графа далеко не одно.
- Нагруженный граф - граф, снабженный весами (числами) на ребрах
- Вес остовного дерева - сумма всех весов ребер этого дерева.

Теперь опишем [алгоритм Прима](https://ru.wikipedia.org/wiki/Алгоритм_Прима). Первым шагом - выбираем случайную вершину, и начинаем строить дерево из нее. 

Затем выполняем шаг: Для каждой вершины текущего дерева выбираем все ребра из оригинального графа такие, что одна вершина этого ребра уже есть в нашем дереве, а другой - нет. Затем, среди всех этих ребер выбираем ребро с минимальным весом - и добавляем его в наше дерево. Если таких ребер несколько, мы имеем право выбрать любое. Повторяем этот шаг, пока все вершины графа не окажутся в дереве.

Применим этот алгоритм на данном графе. Выберем за стартовую вершину $[1]$.
![[discrete-2-2-4-1.svg]]
Шаг 1:
Кандидаты на новые ребра:
$$\pmatrix{[1] \to [2] =2\\ [1] \to [3] = 6 \\ [1] \to [4] = 2}$$
Здесь есть два кандидата с минимальным весом, поэтому мы можем выбрать добавить как ребро $[1] \to [2]$, так и $[1] \to [4]$. Я выберу $[1] \to [2]$:
![[discrete-2-2-4-2.svg]]

Шаг 2:
Кандидаты на новые ребра:
$$\pmatrix{[1] \to [3] = 6 \\ [1] \to [4] = 2 \\ [2] \to [3] = 5 \\ [2] \to [4] = 3 \\ [2] \to [5] = 6}$$
Заметьте, как мы не рассматриваем ребро $[2] \to [1]$ - обе вершины уже принадлежат дереву. Среди этих ребер выигрывает очевидно $[1] \to [4]$, так что добавляем ее:
![[discrete-2-2-4-3.svg]]

Шаг 3:
Кандидаты на новые ребра:
$$\pmatrix{[1] \to [3] = 6 \\ [2] \to [3] = 5 \\ [2] \to [5] = 6 \\ [4] \to [3] = 1 \\ [4] \to [5] = 1}$$
Снова обращаю внимания, что теперь мы не рассматриваем ребро $[2] \to [4]$ - обе вершины принадлежат дереву, и если мы добавим это ребро, получится зацикливание в графе, и дерево перестанет быть деревом. Снова непонятки кого выбирать, я выберу $[4] \to [3]$:
![[discrete-2-2-4-4.svg]]

Шаг 4:
Кандидаты на последнее ребро:
$$\pmatrix{[2] \to [5] = 6 \\ [3] \to [5] = 3 \\ [4] \to [5] = 1}$$
Среди них выигрывает $[4] \to [5]$, поэтому это ребро и добавляем:
![[discrete-2-2-4-5.svg]]

Все вершины добавлены, поэтому алгоритм закончен, остовное дерево построено. Теперь посчитаем его вес, просто сложив все веса ребер вместе.
$$1+1+2+2=6$$
Ответ: $6$.

## Пример 2
Дан нагруженный граф $G$:
![[discrete-2-2-4.svg]]

Построить минимальное остовное дерево нагруженного графа, применяя алгоритм Краскала, и найти его вес.

Решение: для алгоритма Краскала нужно отсортировать все ребра по их весу, и добавлять ребра, начиная с минимального веса, в дерево. Если добавление ребра приведет к появлению цикла в графе, это ребро пропускается. Алгоритм заканчивается, когда больше нельзя добавить ни одно ребро - полное дерево построено.

Мы же будем сортировать не сами ребра, а *веса* этих ребер, и добавлять сразу по несколько ребер в дерево за шаг.
Отсортированное множество весов:
$$W = \set{1,2,3,5,6}$$
Проще оставлять вершины на их исходных местах и просто не добавлять ребра в начале алгоритма:
![[discrete-2-2-5-1.svg]]

Шаг 1:
С весом $1$ есть ребра $[4] \to [5]$ и $[4] \to [3]$, их всех можно добавить в дерево без появления циклов:
![[discrete-2-2-5-2.svg]]

Шаг 2:
С весом $2$ есть ребра $[1] \to [4]$ и $[1] \to [2]$, и их тоже можно добавить в дерево без появления циклов:
![[discrete-2-2-5-3.svg]]

И вот, все вершины уже соединены в дерево, поэтому больше никаких ребер добавить не получится - алгоритм завершен.

Снова посчитаем вес остовного дерева:
$$1+1+2+2=6$$
Ответ: $6$.

# Задание 5 - Дейкстра
Дан нагруженный орграф $G$:
![[discrete-2-2-6.svg]]
Найти кратчайший путь из вершины $1$ в вершину $5$, применяя алгоритм Дейкстры.

Решение: для начала алгоритма, снабдим каждую вершину графа меткой - минимальным известным расстоянием до нее от начальной вершины. Инициализируем все метки как бесконечность, кроме начальной - ее метка будет нулевая. Будем выполнять *шаг*, пока не останется непосещенных вершин.

Шаг: выбираем непосещенную вершину с минимальной меткой (на первом шаге это начальная вершина). Для каждого соседа вершины (такой вершины, которая соединена дугой (направленным ребром) с рассматриваемой вершиной) обновляем метку, если сумма метки выбранной вершины и веса дуги, соединяющего эти выбранную вершину и соседа, меньше текущего значения метки соседа. Помечаем вершину как посещенную и повторяем шаг.

После всех шагов, метка каждой вершины будет равна минимальному расстоянию от начальной вершины до этой вершины.

Давайте выполним алгоритм Дейкстры для данного орграфа - инициализириуем первую вершину:
![[discrete-2-2-6-1.svg]]

Шаг 1:
Так как у вершины $[1]$ наименьшая метка (0), начинаем с нее. Из нее только одна дуга $[1] \to [3]$, поэтому обновляем метку вершины $[3]$. Так как сумма текущей метки и веса дуги $0+6 < \infty$, метка вершины $[3]$ становится равна $0+6=6$. Отмечаем вершину как посещенную.
![[discrete-2-2-6-2.svg]]

Шаг 2:
Выбираем вершину с минимальной меткой среди непосещенных - это конечно же вершина $[3]$. Из нее выходят дуги $[3] \to [2]$ и $[3] \to [4]$. Какая бы сумма не получилась, она будет меньше бесконечности, так что присваиваем вершинам $[2]$ и $[4]$ метки $6+5=11$ и $6+1=7$ соответственно. Отмечаем вершину как посещенную.
![[discrete-2-2-6-3.svg]]

Шаг 3:
Вот теперь уже есть две непосещенные вершины с небесконечным весом - $[2]$ и $[4]$. Из них метка меньше у $[4]$, поэтому начинаем шаг для нее. Из нее выходят три дуги: $[4] \to [1]$, $[4] \to [2]$, и $[4] \to [5]$.

Для первой дуги сумма получается $7+2=9$, а это больше уже имеющейся метки у вершины $[1]$ ($0$), поэтому метку мы не меняем. Для дуги $[4] \to [2]$ сумма будет $7+3=10$, что меньше имеющейся у вершины $[2]$ метки равной $11$, поэтому мы меняем ее на $10$. Для последней дуги $[4] \to [5]$ сумма будет $7+1 = 8$, и мы меняем у вершины $[5]$ метку (ведь сейчас она $\infty$). Не забываем отметить вершину как посещенную.
![[discrete-2-2-6-4.svg]]

Шаг 4:
Между оставшимися вершинами $[4]$ и $[5]$ меньшая метка у вершины $[5]$, поэтому работаем с ней. Из нее выходят дуги $[5] \to [2]$ и $[5] \to [3]$, хотя ни та, ни другая сумма не будет меньше уже имеющихся меток: $8+6>10$ и $8+3>6$. Поэтому ничего не меняем и просто помечаем вершину $[5]$ как посещенную.
![[discrete-2-2-6-5.svg]]

Шаг 5:
Последняя вершина $[2]$, из которой выходят лишь дуга $[2] \to [1]$, но она ничего не меняет, ибо $10+2>0$, поэтому просто отмечаем последнюю вершину как посещенную, и заканчиваем алгоритм.
![[discrete-2-2-6-6.svg]]

После всего алгоритма смотрим на метку желаемой вершины - вершины $[5]$. Ее метка равна $8$, и это будет минимальное расстояние от вершины $[1]$ до вершины $[5]$. 

Кратчайший путь здесь уже можно и глазками найти, но алгоритмически можно это сделать двумя способами:
1. Каждый раз, когда мы обновляем метку вершины, будем также сохранять номер вершины, из которой мы обновили метку. Таким образом, после завершения алгоритма можно пройти из финальной вершины в обратном порядке по сохраненным вершинам. 
2. После завершения алгоритма, из конечной вершины начинаем идти по обратным дугам, причем только если в сумма метки соседа и веса дуги равна текущей вершине.
	1. Из вершины $[5]$ мы идем по обратной дуге $[4] \to [5]$, ведь сумма метки соседа и веса дуги $7+1$ равна метке текущей вершины $8$, поэтому переходим к вершине $[4]$.
	2. Из вершины $[4]$ идем по обратной дуге $[3] \to [4]$, ведь сумма $6+1$ равна метке текущей вершины $7$, и приходим к вершине $[3]$.
	3. Из вершины $[3]$ есть две обратные дуги: $[5] \to [3]$ и $[1] \to [3]$. $[5] \to [3]$ неподходит, ведь $8+3 \neq 6$, а вот $[1] \to [3]$ подходит, ведь $0+6=6$. Переходим к $[1]$, и это наша начальная вершина. Получаем путь $[1] \to [3] \to [4] \to [5]$.

Ответ: путь $[1] \to [3] \to [4] \to [5]$ с расстоянием $8$.