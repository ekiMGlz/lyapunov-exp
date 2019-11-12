# Mapeos Uni-dimensionales

## Definiciones generales para sistemas dinamicos discretos

DEF: Un **mapeo** (tambien conocido como ecuacion de diferencia, relacion de recursion o mapeo iterado) es sistema dinamico de tiempo discreto descrito por una condicion inicial $x_0$ y una ecuacion de estado:

$$
    x_n = f(x_{n-1})
$$

DEF: La **orbita** de un mapeo se define como la sucesion $x_0, f(x_0), f(f(x_0)), \dots$

DEF: $x^*$ es un **punto fijo** del mapeo $f$ si $f(x^*)=x^*$.

Para determinar la estabilidad de un punto fijo de una fuincion $f$ suave, consideramos la orbita cercana $x_n = x^* + \eta_n$. Utilizando Taylor:

$$
    x^*+\eta_{n+1} = x_{n+1} = f(x^*+\eta_n) = f(x^*) + f'(x^*)\eta_n + O(\eta_n^2)
$$

Luego:

$$
    \eta_{n+1} = f'(x^*)\eta_n + O(\eta_n^2)
$$

Si $O(\eta_n^2)$ es despreciable, entonces $\eta_{n+1}=\lambda \eta_n$, con $\lambda := f'(x^*)$. Con esto, si $|\lambda| < 1, \eta_n \to 0$, por lo que $x^*$ es linealmente estable. Si fuese mayor a 1, seria linealmente inestable. Si $|\lambda| = 1$, la aproximacion falla.

DEF: Un punto $x^*$ es superestable si $f'(x^*) = 0$

DEF: Una orbita es _p_-periodica si, para $n\geq n_0$, $x_n = x_{n+p}$

## Exponente de Lyapunov

Intuitivamente, se define el exponente de Lyapunov tomando $x_0$ y $x_0 + \delta_0$, con $\delta_0$ pequeño. Si $\delta_n$, la separacion despues de $n$ iteraciones, es tal que:

$$
    |\delta_n|\approx|\delta_0|e^{n\lambda}
$$

Entonces $\lambda$ es conocido como el exponente de Lyapunov. De manera mas precisa, vemos que cuando $\delta_0 \to 0$ como:

$$
\begin{aligned}
    \lambda &\approx \frac{1}{n}ln|\frac{\delta_n}{\delta_0}| \\
            &= \frac{1}{n}ln|\frac{f^n(x_0+\delta_0) - f^n(x_0)}{\delta_0}| \\
            &= \frac{1}{n}ln|(f^n)'(x_0)| \\
            &= \frac{1}{n}ln|\prod_{i=0}^{n-1}f'(x_i)| \\
            &= \frac{1}{n}\sum_{i=0}^{n-1}ln|f'(x_i)|
\end{aligned}
$$

Asi, definimos el exponente de Lyapunov como el limite de la expresion, es decir:
$$
    \lambda = \lim_{n\to\infty} \frac{1}{n}\sum_{i=0}^{n-1}ln|f'(x_i)|
$$
Podemos ver que $\lambda$ depende de nuestro $x_0$ inicial, pero para puntos cerca de un mismo atractor, debe de tener el mismo valor. Para puntos fijos estables y ciclos, $\lambda < 0$. Para atractores caoticos, $\lambda > 0$.

## Ejemplos

### Regresion Logistica

Considerar:

$$
    \begin{cases}
        x_0 \in [0,1] \\
        x_n = rx(1-x) \quad r \in [0,4]
    \end{cases}
$$

### Tienda de Campaña

$$
    \lambda = ln(r)
$$

### $f$ con orbita _p_ estable

$$
    \lambda < 0
$$
