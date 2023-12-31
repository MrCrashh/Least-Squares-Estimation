<center>
  
# «Метод наименьших квадратов»  
## Описание модели
</center>

Модель полезного сигнала имеет вид:

$$\phi(x) = \theta_0 + \theta_1 x + \ldots + \theta_m x^m.(1)$$ 

Рассматривается модель наблюдений:
$$y_k = \theta_0 + \theta_1 x_k + \ldots + \theta_m x_k^m + \varepsilon_k, \quad k=\overline{1, n}, (2)$$
где $\varepsilon_1, \ldots, \varepsilon_n$  – независимые центрированные и одинаково распределённые случайные величины.
<center>

## Моделирование данных
Смоделировать два набора наблюдений на основе модели (2) для следующих случаев:

<table align="center">
    <tr>
        <th>Первый случай</th>
        <th>Второй случай</th>
    </tr>
    <tr>
        <td>$$m=3, \varepsilon_k \sim N(0, \sigma^2)$$</td>
        <td>$$m=2, \varepsilon_k \sim R(-3\sigma, 3\sigma) $$</td>
    </tr>
    <tr>
        <td>$$x_k=-4+k\frac{8}{n},$$</td>
        <td>$$\qquad k = \overline{1,n} , \qquad n=40$$</td>
    </tr>
</table> 

$$\theta_0 = -21, \theta_1 = -3, \theta_2 = -6, \theta_3 = 0.11, \sigma^2 = 3.0$$

## Задание
Для обоих случаев выполнить по очереди следующие задания.
1. Подобрать порядок многочлена $\hat{m}$ в модели (1), используя критерий Фишера на уровне значимости 0.05, и вычислить оценки неизвестных параметров $(\theta_0, \ldots, \theta_{\hat{m}})$ методом наименьших квадратов.
2. В предположении нормальности ошибок построить доверительные интервалы уровней
надёжности $\alpha_1 = 0.95$ и $\alpha_2 = 0.99$ для параметров $(\theta_0, \ldots, \theta_{\hat{m}})$.
3. В предположении нормальности ошибок построить доверительные интервалы уровней.
надёжности $\alpha_1 = 0.95$ и $\alpha_2 = 0.99$ для полезного сигнала (1).
4. Представить графически
> - истинный полезный сигнал,
> - набор наблюдений,
> - оценку полезного сигнала, полученную в шаге 1,
> - доверительные интервалы полезного сигнала, полученные в шаге 3.

5. По остаткам регрессии построить оценку плотности распределения случайной ошибки
наблюдения в виде гистограммы.
6. В предположении нормальности ошибок вычислить оценку максимального правдоподобия
дисперсии $\sigma^2$ случайной ошибки.
7. По остаткам регрессии с помощью &chi;² критерия Пирсона на уровне значимости 0.05 проверить
гипотезу о том, что закон распределения ошибки наблюдения является нормальным.

## Описание

Одной из важнейших деталей, отличающих оба случая, является вектор ошибок $\overline{ε}$, соответствующий следующим значениям с точностью до
третьего знака после запятой для первого случая:\
[ 2.118, -0.798, -0.689, -1.399,  1.128, -3.001,  2.275, -0.992,
        0.416, -0.325,  1.906, -2.686, -0.42 , -0.501,  1.478, -1.434,
       -0.225, -1.145,  0.055,  0.76 , -1.435,  1.493,  1.176,  0.655,
        1.175, -0.891, -0.16 , -1.22 , -0.349,  0.691, -0.902, -0.517,
       -0.896, -1.102, -0.875, -0.017, -1.457,  0.306,  2.164,  0.968]

### 1. Критерий Фишера

Критерий Фишера применяется на модели $Z_{n} = X_{n}\theta + E$, где $E ∼ N (0; σI_{n})$ и матрица $X_{n}$ имеет ранг $p$, для проверки гипотезы вида $H_{0}: A\theta = c$ с помощью реализации статистики

$$F(Z_{n})= \frac{(A\widehat{\theta_{n}}-c)^{T}[A(X_{n}^{T}X_{n})^{-1}A^{T}]^{-1}(A\widehat{\theta_{n}}-c)}{\frac{q}{n-p}(Z_{n}-X_{n}\widehat{\theta_{n}})^{T}(Z_{n}-X_{n}\widehat{\theta_{n}})}$$

В нашем случае гипотеза формулируется так: «При повышения порядка аппроксимации $\widehat{m}$ модели избыточно ли наличие коэф. $\theta_{\widehat{m}}$ при $x^{\widehat{m}}$ ?» или более формально $H_{0}: \theta_{\widehat{m}}=0$. Формулу можем упростить до $q=$ $1^{1}, p=\widehat{m}+1$ и перейти к скалярному виду, приняв за $k$-ый элемент главной диагонали матрицы $\left(X_{n}^{T} X_{n}\right)^{-1}$ символ $r_{k}$ и вектор остатков за $\widehat{E}=Z_{n}-X_{n} \widehat{\theta}_{n}=Y-X \widehat{\theta}$ :


$$F(Z_{n})=\frac{\widehat{\theta_{m}}^{2}}{r_{\widehat{m}}||\widehat{E}||^{2}}\cdot\frac{n-p}{1}$$


Далее, определив теоретические квантили для заданного уровня значимости $\alpha=0.05$ для распределений Фишера $F(q, n-p)$, проверим, попадает ли значение в критическую область $\left(f_{1-\alpha}(1, n-p) ; \infty\right)$.


### 2. Доверительные интервалы для параметров

Для уровней $\alpha_{1}=0.95$ и $\alpha_{2}=0.99$ для параметров распределения расчет опирается на следующее утверждение:

$$\frac{\widehat{\theta_{k}}-\theta_{k}}{\||\widehat{E}\|| \sqrt{r_{k}}} \sqrt{n-p} \sim t(n-p)$$

где $t(n-p)$ - распределение Стьюдента.

В итоге, доверительный интервал для уровня надежности 0.95 или 0.99 для $\alpha=0.05$ или $0.01$ :

$$\Delta_{k}=t_{1-\frac{\alpha}{2}}(n-p)\cdot\||\widehat{E}\||\sqrt{\frac{r_{k}}{n-p}}, \quad \widehat{\theta_{k}}-\Delta_{k}\leq \widehat{\theta_{k}}\leq\widehat{\theta_{k}}+\Delta_{k}$$

### 3. Доверительные интервалы для полезного сигнала 

По аналогии с оценкой параметров можем оценить доверительный интервал для полезного сигнала как:

$$\frac{\varphi\left(x,\widehat{\theta_{k}}\right)-\varphi\left(x, \theta_{k}\right)}{\||\widehat{E}\||\sqrt{r(x)}} \sqrt{n-p} \sim t(n-p)$$

где основное отличие в том, что $r(x)=\left(1, x, x^{2}, \ldots, x^{m}\right) \cdot\left(X^{T} X\right)^{-1} \cdot\left(1, x, x^{2}, \ldots, x^{m}\right)^{T}$.

Для уровней надежности $\alpha=0.95$ и $0.99$ с помощью символьных вычислений Sympу границы доверительного интервала будут описаны как 
$\left[\varphi\left(x, \\widehat{\theta_{k}}\right)-\Delta_{\alpha}(x) ; \varphi\left(x, \widehat{\theta_{k}}\right)+\Delta_{\alpha}(x)\right]$.

### 4. Графики

![newplot](https://github.com/MrCrashh/Least-Squares-Estimation/assets/80788354/37616270-1647-49d2-97cb-6bceac6f0f26)

![newplot (1)](https://github.com/MrCrashh/Least-Squares-Estimation/assets/80788354/8ae75628-710f-49cf-a5a7-f3b88ee80c1a)


### 5. Оценка плотности распределения остатков регрессии
Для оценки плотности распределения, построенного на какой-либо выборке данных, следует разбить эту выборку на $b=1+[\log_{2}n]=6$
 интервалов. Далее, подсчитав количество элементов выборки $O$, попадающих в заданные интервалы, можно построить кусочно-заданный график,
определеный на указанных $b$-интервалах со значением $O$.\
Нормализованная гистограмма формируется следующей кусочно-заданной функцией: \
$$\overline{h}(x)=\frac{O_{i}}{n\cdot\Delta_{b}},$$ 
где $O_{i}$ и $\Delta_{b}$ количество значений в $i$-ом интервале и ширина этого интервала соответственно.

### 6. МП-оценка дисперсии $σ{2}$ случайной ошибки
