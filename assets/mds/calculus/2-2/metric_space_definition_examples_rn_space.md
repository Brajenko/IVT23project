Здесь мы будто обратно возращаемся в алгем, вопросы чуть ли не повторяются.

*Метрическое пространство*, строго говоря - это множество $X$, на котором задана *метрика* (метрическая функция, функция расстояния) $d$, которая любым двум элементам этого множества ставит действительное число, удовлетворяющие условиям:
- $d(x,y) = 0 \Leftrightarrow x = y$ (аксиома тождества)
- $d(x,y) \geq 0$ (аксиома положительности)
- $d(x,y) = d(y,x)$ (аксиома симметричности)
- $d(x,z) \leq d(x,y) + d(y,z)$ (аксиома треугольника или неравенство треугольника)

Аксиома положительности является избыточной, ведь следует из остальных аксиом:
$$0 = d(x,x) \leq d(x,y) + d(y,x) = 2 \cdot d(x,y) \Rightarrow d(x,y) \geq 0$$
## Примеры
Множества $\mathbb R$ и $\mathbb C$ является метрическими пространствами с метрикой
$$d(x,y) = |x - y|$$
Обозначим за $C[a,b]$ множество непрерывных на $[a,b]$ действительных функций. Тогда его можно обратить в метрическое пространство, введя метрику
$$d(f,g) \underset{x\in [a,b]}= \max |f(x) - f(y)|$$

Множество $\mathbb R^n$ - множество из $n$ упорядоченных действительных чисел:
$$\mathbb R^n = \set{(x_1, \ldots , x_n) \ | \ x_i \in \mathbb R, i \in \overline{1, n}}$$
Например, двухмерная плоскость точек (пара координат) - это множество $\mathbb R^2$. Множество $\mathbb R^3$ будет уже трехмерным пространством. Такие множества обычно дополняют до метрических пространств, вводя евклидову метрику - более известную как теорема Пифагора для случая $\mathbb R^2$:
$$d(x,y) = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}$$
Первые три свойства очевидно выполняются, докажем неравенство треугольника. В доказательстве нам потребуется [неравенство Коши-Буняковского][[[0,1,34]]], поэтому сделаем детур на его доказательство:
$$\array{\forall \lambda \in \mathbb R : d(x,\lambda y) \geq 0 \\ d^2(x, \lambda y) = \sum\limits_{i=1}^n(x_i-y_i)^2 = \sum\limits_{i=1}^n (x_i^2 - 2x_iy_i +y_i^2) = \\ = \lambda^2\sum\limits_{i=1}^n y_i^2 - 2\lambda \sum\limits_{i=1}^n x_iy_i + \sum\limits_{i=1}^n x_i^2 \geq 0}$$
Так как при любых значениях $\lambda$ этот многочлен не меньше нуля, дискриминант будет не больше нуля.
$$D = \left(2\sum\limits_{i=1}^nx_iy_i\right)^2 - 4\sum\limits_{i=1}^ny^2_i\sum\limits_{i=1}^nx^2_i \leq 0$$
$$\left(\sum\limits_{i=1}^nx_iy_i\right)^2 \leq \sum\limits_{i=1}^ny^2_i \cdot \sum\limits_{i=1}^nx^2_i $$
Неравенство Коши-Буняковского доказано. Теперь само неравенство треугольника:
$$\array{d^2(x,y) = \sum\limits_{i=1}^n(x_i-y_i)^2 = \sum\limits_{i=1}^n(x_i - z_i + z_i - y_i)^2 = \\ = \sum\limits_{i=1}^n\left((x_i - z_i) + (z_i - y_i)\right)^2 = \\ = \sum\limits_{i=1}^n\left((x_i - z_i)^2 + 2(x_i - z_i)(z_i - y_i)+(z_i - y_i)^2\right) = \\ = \sum\limits_{i=1}^n(x_i - z_i)^2 + \sum\limits_{i=1}^n(z_i - y_i)^2 + 2\sum\limits_{i=1}^n(x_i - z_i)(z_i - y_i) = \\ = d^2(x,z) + d^2(z,y) + 2\sum\limits_{i=1}^n(x_i - z_i)(z_i - y_i)}$$
Теперь по неравенству Коши-Буняковского можем сказать, что:
$$\sum\limits_{i=1}^n(x_i - z_i)(z_i - y_i) \leq \sqrt{\sum\limits_{i=1}^n(x_i - z_i)^2} \cdot \sqrt{\sum\limits_{i=1}^n(z_i - y_i)^2} = d(x,z) \cdot d(z,y)$$
Обращаю внимание на корни: в изначальном неравенстве Коши-Буняковского, сумма в левой части неравенства возведена в квадрат, а тут его нет - взамен на это мы накладываем корень на правую часть неравенства.
$$\leq d^2(x,z) + d^2(z,y) + 2d(x,z) \cdot d(z,y) = (d(x,z) + d(z,y))^2$$
Собирая всю цепочку равенств и неравенств вместе:
$$d^2(x,y) \leq (d(x,z) + d(z,y))^2 \Rightarrow d(x,y) \leq d(x,z) + d(z,y)$$
Неравенство треугольника доказано.