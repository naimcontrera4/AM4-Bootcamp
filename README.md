# Bootcamp de Análisis Matemático Avanzado: Ecuaciones Diferenciales, Transformadas de Laplace y Series de Fourier

Este documento constituye una guía analítica y un programa de estudio intensivo de **34 días** diseñado para dominar los fundamentos teóricos y prácticos de las ecuaciones diferenciales ordinarias (EDO) de primer y segundo orden, la transformada de Laplace y el análisis armónico mediante series de Fourier. La estructura conceptual se fundamenta rigurosamente en los enfoques de **George F. Simmons** (*Ecuaciones Diferenciales con Aplicaciones y Notas Históricas*) y **Erwin Kreyszig** (*Matemáticas Avanzadas para Ingeniería*).

---

## 🏛️ Cronograma de Planificación Estructural (34 Días)

| Fase | Temática Central | Intervalo Temporal | Alcance Operativo |
| :--- | :--- | :--- | :--- |
| **I** | **EDOs de Primer Orden** | Días 1 - 7 | Separación de variables, transformaciones homogéneas, análisis de linealidad y teoría de exactitud. |
| **II** | **EDOs Lineales de Segundo Orden** | Días 8 - 14 | Espacios de soluciones homogéneas, polinomios característicos y método de Variación de Parámetros. |
| **III** | **Transformada de Laplace** | Días 15 - 24 | Mapeo integral impropio, teoremas de traslación, derivadas de transformadas y resolución de PVI. |
| **IV** | **Series de Fourier** | Días 25 - 29 | Ortogonalidad funcional, coeficientes de Euler-Fourier y convergencia en intervalos finitos. |
| **V** | **Consolidación y Simulación** | Días 30 - 34 | Resolución analítica avanzada de modelos de exámenes finales de nivel de ingeniería. |

---

## 📘 Fase I: Ecuaciones Diferenciales Ordinarias de Primer Orden

### 1. Fundamentos Teóricos
Una ecuación diferencial ordinaria de primer orden relaciona una variable independiente $x$, una función dependiente $y(x)$ y su primera derivada $y'$. Su forma implícita general es $F(x, y, y') = 0$. 

* **Teorema de Existencia y Unicidad (Picard-Lindelöf):** Sea $y' = f(x,y)$. Si $f(x,y)$ y $rac{\partial f}{\partial y}$ son continuas en un rectángulo cerrado $R$ del plano $xy$ que contiene al punto $(x_0, y_0)$, entonces existe un intervalo abierto que contiene a $x_0$ en el cual el problema de valor inicial posee una única solución $y = \phi(x)$.
* **Variables Separables:** Ocurre si $f(x,y) = g(x)h(y)$. La integración se efectúa de forma directa mediante:
    $$\int rac{1}{h(y)} \, dy = \int g(x) \, dx + C$$
* **Ecuaciones Homogéneas:** Una ecuación $M(x,y)dx + N(x,y)dy = 0$ es homogénea de grado $n$ si $M(tx, ty) = t^n M(x,y)$ y $N(tx, ty) = t^n N(x,y)$. La sustitución canónica $y = zx$ (donde $dy = zdx + xdz$) reduce la ecuación a una forma separable en variables $x$ y $z$.
* **Ecuaciones Exactas (Criterio Teórico):** Una expresión $M(x,y)dx + N(x,y)dy = 0$ es una diferencial total si cumple con la condición de simetría de derivadas parciales mixtas (Teorema de Clairaut-Schwarz):
    $$rac{\partial M}{\partial y} = rac{\partial N}{\partial x}$$
    Su solución general está dada implícitamente por $U(x,y) = C$, tal que $rac{\partial U}{\partial x} = M$ y $rac{\partial U}{\partial y} = N$.

---

### 2. Resolución de Modelos de Examen (Fase I)

#### Ejercicio 1.1: Ecuación por Variables Separables Complejas
**Enunciado:** Resolver la ecuación diferencial:
$$(y^3 - y)dx + (x y^2 + x - y^2 - 1)dy = 0$$

**Desarrollo Analítico:**
1.  **Análisis por Factorización Algebraica:** Intentamos agrupar los términos de cada diferencial por factor común.
    * Para el término $M(x,y)$: 
        $$y^3 - y = y(y^2 - 1)$$
    * Para el término $N(x,y)$: Agrupamos por parejas asociadas a la variable $x$:
        $$x y^2 + x - y^2 - 1 = x(y^2 + 1) - 1(y^2 + 1) = (x - 1)(y^2 + 1)$$
2.  **Reescritura de la EDO:**
        $$y(y^2 - 1)dx + (x - 1)(y^2 + 1)dy = 0$$
3.  **Separación de Variables:** Dividimos toda la expresión por $(x - 1)y(y^2 - 1)$, asumiendo que estos términos son no nulos:
        $$rac{1}{x - 1}dx + rac{y^2 + 1}{y(y^2 - 1)}dy = 0$$
4.  **Integración por Fracciones Parciales:** La integral respecto a $x$ es directa: $\int rac{1}{x-1} dx = \ln|x-1|$. Para el término en $y$, descomponemos la función racional:
        $$rac{y^2 + 1}{y(y-1)(y+1)} = rac{A}{y} + rac{B}{y-1} + rac{C}{y+1}$$
    Multiplicando por el denominador común obtenemos la identidad:
        $$y^2 + 1 = A(y^2 - 1) + By(y + 1) + Cy(y - 1)$$
    Evaluamos en los polos del sistema para hallar los coeficientes residenciales:
    * Si $y = 0 \implies 1 = A(-1) \implies A = -1$.
    * Si $y = 1 \implies 2 = B(1)(2) \implies B = 1$.
    * Si $y = -1 \implies 2 = C(-1)(-2) \implies C = 1$.
    
    Por lo tanto, la integral con respecto a $y$ es:
        $$\int \left( -rac{1}{y} + rac{1}{y-1} + rac{1}{y+1} 
ight) dy = -\ln|y| + \ln|y-1| + \ln|y+1| = \ln\left| rac{y^2 - 1}{y} 
ight|$$
5.  **Composición de la Solución General:**
        $$\ln|x - 1| + \ln\left| rac{y^2 - 1}{y} 
ight| = C_0$$
    Aplicando la función exponencial en ambos miembros:
        $$|x - 1| \cdot \left| rac{y^2 - 1}{y} 
ight| = e^{C_0} \implies (x - 1)(y^2 - 1) = K y$$
    Donde $K$ representa la constante matemática arbitraria de integración del sistema.

#### Ejercicio 1.2: Ecuación Diferencial Homogénea de Grado Superior
**Enunciado:** Resolver la ecuación diferencial:
$$2x^3y \, dx + (x^4 + y^4) \, dy = 0$$

**Desarrollo Analítico:**
1.  **Verificación de Homogeneidad:**
    * $M(tx, ty) = 2(tx)^3(ty) = t^4 (2x^3y) = t^4 M(x,y)$ $
ightarrow$ Homogénea de grado 4.
    * $N(tx, ty) = (tx)^4 + (ty)^4 = t^4 (x^4 + y^4) = t^4 N(x,y)$ $
ightarrow$ Homogénea de grado 4.
2.  **Sustitución Estándar:** Definimos $y = zx$, por lo tanto, la diferencial diferencial asociada es $dy = zdx + xdz$.
3.  **Sustitución en la EDO Original:**
        $$2x^3(zx)dx + (x^4 + (zx)^4)(zdx + xdz) = 0$$
        $$2x^4z \, dx + x^4(1 + z^4)(zdx + xdz) = 0$$
    Dividimos toda la ecuación por $x^4$ ($x 
eq 0$):
        $$2z \, dx + (1 + z^4)z \, dx + (1 + z^4)x \, dz = 0$$
    Agrupamos los términos dependientes de la diferencial de la variable independiente $dx$:
        $$(2z + z + z^5)dx + x(1 + z^4)dz = 0 \implies (3z + z^5)dx + x(1 + z^4)dz = 0$$
4.  **Separación e Integración de Variables Auxiliares:**
        $$rac{1}{x}dx + rac{1 + z^4}{z(3 + z^4)}dz = 0$$
    Para integrar el segundo término, realizamos una sustitución de variable de orden superior: $u = z^4 \implies du = 4z^3 dz$. Sin embargo, resulta algebraicamente más elegante notar que el numerador es proporcional a la derivada del denominador si reorganizamos la expresión, o bien usar fracciones parciales directas. Multiplicamos y dividimos por $z^3$:
        $$\int rac{(1+z^4)z^3}{z^4(3+z^4)} dz = \int rac{1+u}{u(3+u)} rac{du}{4}$$
    Descomponiendo $rac{1+u}{u(3+u)} = rac{1/3}{u} + rac{2/3}{3+u}$, la integral resulta en:
        $$rac{1}{4} \left[ rac{1}{3}\ln|u| + rac{2}{3}\ln|3+u| 
ight] = rac{1}{12}\ln|z^4| + rac{1}{6}\ln|3+z^4| = rac{1}{3}\ln|z| + rac{1}{6}\ln|3+z^4|$$
    Sumando la integral de $x$:
        $$\ln|x| + \ln|z^{1/3}| + \ln|(3+z^4)^{1/6}| = C_0 \implies x \cdot z^{1/3} \cdot (3+z^4)^{1/6} = K$$
    Elevando a la sexta potencia para eliminar fracciones en los exponentes:
        $$x^6 z^2 (3 + z^4) = K^6$$
5.  **Retorno a las Variables Originales ($z = y/x$):**
        $$x^6 \left(rac{y}{x}
ight)^2 \left[ 3 + \left(rac{y}{x}
ight)^4 
ight] = C \implies x^4 y^2 \left[ rac{3x^4 + y^4}{x^4} 
ight] = C$$
    Simplificando términos idénticos de potencia de base $x$:
        $$y^2(3x^4 + y^4) = C$$

---

## 📐 Fase II: Ecuaciones Diferenciales Lineales de Segundo Orden

### 1. Estructura Teórica del Espacio de Soluciones
La forma estándar de una ecuación diferencial lineal de segundo orden no homogénea es:
$$y'' + P(x)y' + Q(x)y = f(x)$$

* **Principio de Superposición:** Si $y_1$ y $y_2$ son soluciones linealmente independientes de la ecuación homogénea asociada ($f(x)=0$), entonces la combinación lineal $y_h = C_1 y_1 + C_2 y_2$ es la solución general de la homogénea.
* **Dependencia Lineal y el Wronskiano:** Dos funciones son linealmente independientes en un intervalo si y solo si su determinante Wronskiano es distinto de cero en dicho intervalo:
    $$W(y_1, y_2) =  egin{vmatrix} y_1 & y_2 \ y_1' & y_2' \end{vmatrix} = y_1 y_2' - y_2 y_1' 
eq 0$$
* **Método de Variación de Parámetros:** Es un método general fundamentado por Lagrange para hallar una solución particular $y_p(x) = u_1(x)y_1(x) + u_2(x)y_2(x)$, donde las funciones variables de los parámetros se deducen a partir de las siguientes integrales de derivadas directas:
    $$u_1(x) = \int rac{-y_2(x)f(x)}{W(y_1, y_2)} \, dx, \quad u_2(x) = \int rac{y_1(x)f(x)}{W(y_1, y_2)} \, dx$$

---

### 2. Resolución de Modelos de Examen (Fase II)

#### Ejercicio 2.1: EDO de Coeficientes Constantes con Variación de Parámetros
**Enunciado:** Resolver la ecuación diferencial ordinaria de segundo orden:
$$y'' + 2y' + 2y = e^{-x} \sec x$$

**Desarrollo Analítico:**
1.  **Resolución de la Ecuación Homogénea Asociada:**
        $$y'' + 2y' + 2y = 0$$
    Planteamos el polinomio característico mediante una solución de tipo exponencial $y = e^{rx}$:
        $$r^2 + 2r + 2 = 0$$
    Aplicando la fórmula cuadrática para hallar las raíces complejas conjugadas:
        $$r = rac{-2 \pm \sqrt{4 - 4(1)(2)}}{2} = rac{-2 \pm \sqrt{-4}}{2} = -1 \pm i$$
    La parte real es $ lpha = -1$ y la parte imaginaria es $ eta = 1$. Por lo tanto, el espacio del conjunto fundamental de soluciones homogéneas está definido por:
        $$y_h(x) = e^{-x}(C_1 \cos x + C_2 \sin x)$$
    Identificamos de forma unívoca: $y_1(x) = e^{-x}\cos x$ y $y_2(x) = e^{-x}\sin x$.

2.  **Cálculo Riguroso del Determinante Wronskiano:**
    Calculamos las derivadas primeras de nuestro conjunto fundamental:
    * $y_1'(x) = -e^{-x}\cos x - e^{-x}\sin x = -e^{-x}(\cos x + \sin x)$
    * $y_2'(x) = -e^{-x}\sin x + e^{-x}\cos x = e^{-x}(\cos x - \sin x)$
    
    Evaluamos el determinante:
        $$W = (e^{-x}\cos x)(e^{-x}(\cos x - \sin x)) - (e^{-x}\sin x)(-e^{-x}(\cos x + \sin x))$$
        $$W = e^{-2x}[\cos^2 x - \cos x \sin x + \sin x \cos x + \sin^2 x]$$
    Por identidad pitagórica fundamental ($\cos^2 x + \sin^2 x = 1$):
        $$W(y_1, y_2) = e^{-2x}$$

3.  **Determinación de los Parámetros Variable ($u_1, u_2$):**
    Sabiendo que el término no homogéneo es $f(x) = e^{-x}\sec x$:
    * **Para $u_1(x)$:**
        $$u_1 = \int rac{-(e^{-x}\sin x)(e^{-x}\sec x)}{e^{-2x}} \, dx = \int -\sin x \cdot rac{1}{\cos x} \, dx = \int -	an x \, dx = \ln|\cos x|$$
    * **Para $u_2(x)$:**
        $$u_2 = \int rac{(e^{-x}\cos x)(e^{-x}\sec x)}{e^{-2x}} \, dx = \int \cos x \cdot rac{1}{\cos x} \, dx = \int 1 \, dx = x$$

4.  **Construcción de la Solución Particular e Integral General:**
    La solución particular $y_p$ queda formulada estructuralmente como:
        $$y_p(x) = (\ln|\cos x|)e^{-x}\cos x + (x)e^{-x}\sin x$$
    Sumando la componente homogénea obtenemos la solución general completa del sistema analítico:
        $$y(x) = e^{-x}(C_1 \cos x + C_2 \sin x) + e^{-x}(\cos x \ln|\cos x| + x \sin x)$$

---

## ⚡ Fase III: Transformada de Laplace

### 1. Marco Teórico e Integrales Impropia
La transformada de Laplace es un operador lineal integral que mapea una función $f(t)$ definida en el dominio del tiempo ($t \ge 0$) a una función $F(s)$ en el dominio de la variable compleja $s$. Se define mediante la siguiente integral impropia:
$$\mathcal{L}\{f(t)\} = F(s) = \int_{0}^{\infty} e^{-st} f(t) \, dt$$

* **Condición de Existencia:** La integral converge si $f(t)$ es continua por tramos en $[0, \infty)$ y de **orden exponencial**, es decir, existen constantes $M > 0$ y $c$ tales que $|f(t)| \le M e^{ct}$ para todo $t > T$.
* **Teorema de la Transformada de la Derivada:** Permite transformar ecuaciones diferenciales en operadores algebraicos puros:
    $$\mathcal{L}\{y'(t)\} = sY(s) - y(0)$$
    $$\mathcal{L}\{y''(t)\} = s^2Y(s) - s y(0) - y'(0)$$
* **Derivada de una Transformada (Multiplicación por $t$):**
    $$\mathcal{L}\{t \cdot f(t)\} = -rac{d}{ds}F(s)$$

---

### 2. Demostraciones y Problemas de Valor Inicial (PVI)

#### Ejercicio 3.1: Demostración Analítica de Identidades Trigonométricas
**Enunciado:** Demostrar analíticamente mediante propiedades de la transformada que:
$$\mathcal{L}\{\cos^3 t\} = rac{s(s^2+7)}{(s^2+9)(s^2+1)}$$

**Demostración Rigurosa:**
1.  **Descomposición de la Potencia Trigonométrica:** Utilizamos la identidad del producto o del ángulo triple para el coseno:
        $$\cos(3t) = 4\cos^3 t - 3\cos t \implies \cos^3 t = rac{1}{4}\cos(3t) + rac{3}{4}\cos t$$
2.  **Aplicación del Operador Lineal de Laplace:** Por linealidad integral del operador:
        $$\mathcal{L}\{\cos^3 t\} = rac{1}{4}\mathcal{L}\{\cos(3t)\} + rac{3}{4}\mathcal{L}\{\cos t\}$$
    Sabiendo por tabla fundamental demostrada que $\mathcal{L}\{\cos(at)\} = rac{s}{s^2+a^2}$:
        $$\mathcal{L}\{\cos^3 t\} = rac{1}{4}\left( rac{s}{s^2+9} 
ight) + rac{3}{4}\left( rac{s}{s^2+1} 
ight)$$
3.  **Unificación Algebraica de Fracciones:**
        $$\mathcal{L}\{\cos^3 t\} = rac{s(s^2+1) + 3s(s^2+9)}{4(s^2+9)(s^2+1)} = rac{s^3 + s + 3s^3 + 27s}{4(s^2+9)(s^2+1)}$$
        $$\mathcal{L}\{\cos^3 t\} = rac{4s^3 + 28s}{4(s^2+9)(s^2+1)} = rac{4s(s^2+7)}{4(s^2+9)(s^2+1)}$$
    Simplificando el escalar ponderado en el numerador y denominador se obtiene la expresión exacta:
        $$\mathcal{L}\{\cos^3 t\} = rac{s(s^2+7)}{(s^2+9)(s^2+1)}$$
    **Q.E.D. (Queda Demostrado).**

#### Ejercicio 3.2: Resolución de un PVI mediante Laplace
**Enunciado:** Resolver analíticamente el problema de valor inicial:
$$y'' + 2y' + 2y = e^{2t}, \quad 	ext{con } y(0)=1, \, y'(0)=2$$

**Desarrollo Analítico:**
1.  **Aplicación del Operador de Laplace a la EDO:**
        $$\mathcal{L}\{y''\} + 2\mathcal{L}\{y'\} + 2\mathcal{L}\{y\} = \mathcal{L}\{e^{2t}\}$$
2.  **Sustitución de las Condiciones Iniciales del Sistema:**
        $$[s^2 Y(s) - s y(0) - y'(0)] + 2[s Y(s) - y(0)] + 2Y(s) = rac{1}{s-2}$$
    Introduciendo los valores $y(0)=1$ e $y'(0)=2$:
        $$s^2 Y(s) - s - 2 + 2s Y(s) - 2 + 2Y(s) = rac{1}{s-2}$$
    Agrupamos la función incógnita $Y(s)$ en el miembro izquierdo:
        $$(s^2 + 2s + 2)Y(s) - s - 4 = rac{1}{s-2}$$
        $$(s^2 + 2s + 2)Y(s) = rac{1}{s-2} + s + 4$$
3.  **Resolución Algebraica en el Dominio $s$:**
        $$(s^2 + 2s + 2)Y(s) = rac{1 + (s+4)(s-2)}{s-2} = rac{1 + s^2 + 2s - 8}{s-2} = rac{s^2 + 2s - 7}{s-2}$$
        $$Y(s) = rac{s^2 + 2s - 7}{(s-2)(s^2 + 2s + 2)}$$
4.  **Descomposición en Fracciones Parciales Complejas:**
        $$rac{s^2 + 2s - 7}{(s-2)(s^2 + 2s + 2)} = rac{A}{s-2} + rac{Bs + C}{s^2 + 2s + 2}$$
        $$s^2 + 2s - 7 = A(s^2 + 2s + 2) + (Bs + C)(s-2)$$
    * Si $s = 2 \implies 4 + 4 - 7 = A(4 + 4 + 2) \implies 1 = 10A \implies A = rac{1}{10}$.
    * Igualando términos de igual potencia cuadrática ($s^2$): $1 = A + B \implies B = 1 - rac{1}{10} = rac{9}{10}$.
    * Igualando términos independientes ($s^0$): $-7 = 2A - 2C \implies -7 = rac{2}{10} - 2C \implies 2C = 7 + rac{1}{5} = rac{36}{5} \implies C = rac{18}{5} = rac{36}{10}$.
    
    Por lo tanto, la ecuación algebraica en variables de frecuencias se expresa como:
        $$Y(s) = rac{1}{10}\left(rac{1}{s-2}
ight) + rac{1}{10}\left(rac{9s + 36}{s^2 + 2s + 2}
ight)$$
5.  **Completación de Cuadrados y Transformación Inversa:**
    Analizamos el término con raíces complejas del denominador: $s^2 + 2s + 2 = (s+1)^2 + 1$. Ajustamos el numerador de manera equivalente:
        $$9s + 36 = 9(s+1) + 27$$
        $$Y(s) = rac{1}{10}\left(rac{1}{s-2}
ight) + rac{9}{10}\left(rac{s+1}{(s+1)^2+1}
ight) + rac{27}{10}\left(rac{1}{(s+1)^2+1}
ight)$$
    Aplicando la transformada inversa de Laplace ($\mathcal{L}^{-1}$) junto con el Primer Teorema de Traslación ($\mathcal{L}^{-1}\{F(s-a)\} = e^{at}f(t)$):
        $$y(t) = rac{1}{10}e^{2t} + rac{9}{10}e^{-t}\cos t + rac{27}{10}e^{-t}\operatorname{sen} t$$

---

## 🎹 Fase IV: Series de Fourier y Análisis Armónico

### 1. Geometría Funcional y Coeficientes de Euler
Las series de Fourier permiten representar una función periódica de período $T = 2L$ como una suma infinita de funciones armónicas ortogonales (senos y cosenos). La serie trigonométrica general es de la forma:
$$f(x) = a_0 + \sum_{n=1}^{\infty} \left[ a_n \cos\left(rac{n\pi x}{L}
ight) + b_n \operatorname{sen}\left(rac{n\pi x}{L}
ight) 
ight]$$

Los coeficientes del desarrollo espectral se determinan mediante las proyecciones integrales de Euler-Fourier basadas en las propiedades de ortogonalidad del espacio funcional:
$$a_0 = rac{1}{2L} \int_{-L}^{L} f(x) \, dx$$
$$a_n = rac{1}{L} \int_{-L}^{L} f(x) \cos\left(rac{n\pi x}{L}
ight) \, dx$$
$$b_n = rac{1}{L} \int_{-L}^{L} f(x) \operatorname{sen}\left(rac{n\pi x}{L}
ight) \, dx$$

---

### 2. Resolución de Modelos de Examen (Fase IV)

#### Ejercicio 4.1: Demostración del Desarrollo de una Onda Lineal Asimétrica
**Enunciado:** Demostrar que para una función lineal definida en el dominio acotado $0 < x < L$, se cumple el siguiente desarrollo en serie periódica de Fourier:
$$rac{1}{2}L - x = rac{L}{\pi} \sum_{n=1}^{\infty} rac{1}{n} \operatorname{sen}\left(rac{2n\pi x}{L}
ight)$$

**Demostración Rigurosa:**
1.  **Análisis del Período Fundamental:** Observando el argumento de la función seno del enunciado, $rac{2n\pi x}{L}$, deducimos que el período de la serie de Fourier de este examen está definido formalmente por $T = L$. Por lo tanto, el semiperíodo de integración es $L_{	ext{efectivo}} = L/2$. Los coeficientes espectrales generales para un desarrollo completo en el intervalo $(0, L)$ con período $T=L$ se formulan como:
        $$a_0 = rac{2}{L} \int_{0}^{L} \left(rac{1}{2}L - x
ight) dx$$
        $$a_n = rac{2}{L} \int_{0}^{L} \left(rac{1}{2}L - x
ight) \cos\left(rac{2n\pi x}{L}
ight) dx$$
        $$b_n = rac{2}{L} \int_{0}^{L} \left(rac{1}{2}L - x
ight) \operatorname{sen}\left(rac{2n\pi x}{L}
ight) dx$$
2.  **Evaluación de los Coeficientes de Coseno ($a_0, a_n$):**
    * **Para $a_0$:**
        $$a_0 = rac{2}{L} \left[ rac{1}{2}Lx - rac{1}{2}x^2 
ight]_0^L = rac{2}{L} \left( rac{1}{2}L^2 - rac{1}{2}L^2 
ight) = 0$$
    * **Para $a_n$:** Aplicamos el método de integración por partes definiendo $u = rac{1}{2}L - x \implies du = -dx$, y $dv = \cos\left(rac{2n\pi x}{L}
ight)dx \implies v = rac{L}{2n\pi}\operatorname{sen}\left(rac{2n\pi x}{L}
ight)$.
        $$a_n = rac{2}{L} \left[ \left(rac{1}{2}L - x
ight)rac{L}{2n\pi}\operatorname{sen}\left(rac{2n\pi x}{L}
ight) 
ight]_0^L - rac{2}{L} \int_{0}^{L} -rac{L}{2n\pi}\operatorname{sen}\left(rac{2n\pi x}{L}
ight) dx$$
    Dado que $\operatorname{sen}(2n\pi) = 0$ y $\operatorname{sen}(0) = 0$, el término de frontera se anula por completo. La integral remanente del seno evaluada en un período completo también es idénticamente cero. Por tanto:
        $$a_n = 0$$
3.  **Evaluación de los Coeficientes de Seno ($b_n$):**
    Aplicamos integración por partes con los mismos términos diferenciales para $u$ y $du$, pero variando el término armónico: $dv = \operatorname{sen}\left(rac{2n\pi x}{L}
ight)dx \implies v = -rac{L}{2n\pi}\cos\left(rac{2n\pi x}{L}
ight)$.
        $$b_n = rac{2}{L} \left[ \left(rac{1}{2}L - x
ight)\left(-rac{L}{2n\pi}\cos\left(rac{2n\pi x}{L}
ight)
ight) 
ight]_0^L - rac{2}{L} \int_{0}^{L} \left(-rac{L}{2n\pi}\cos\left(rac{2n\pi x}{L}
ight)
ight)(-dx)$$
    * Evaluamos el término de límites integrales (superior menos inferior):
        $$	ext{Límite Superior } (x=L): \left(rac{1}{2}L - L
ight)\left(-rac{L}{2n\pi}\cos(2n\pi)
ight) = \left(-rac{1}{2}L
ight)\left(-rac{L}{2n\pi}
ight) = rac{L^2}{4n\pi}$$
        $$	ext{Límite Inferior } (x=0): \left(rac{1}{2}L - 0
ight)\left(-rac{L}{2n\pi}\cos(0)
ight) = \left(rac{1}{2}L
ight)\left(-rac{L}{2n\pi}
ight) = -rac{L^2}{4n\pi}$$
        $$	ext{Resta de Fronteras:} \left( rac{L^2}{4n\pi} 
ight) - \left( -rac{L^2}{4n\pi} 
ight) = rac{L^2}{2n\pi}$$
    * La integral del término armónico remanente es:
        $$-rac{2}{L}\cdotrac{L}{2n\pi} \int_{0}^{L} \cos\left(rac{2n\pi x}{L}
ight) dx = -rac{1}{n\pi} \left[ rac{L}{2n\pi}\operatorname{sen}\left(rac{2n\pi x}{L}
ight) 
ight]_0^L = 0$$
    * Multiplicando el valor neto obtenido por el factor exterior $rac{2}{L}$:
        $$b_n = rac{2}{L} \cdot \left( rac{L^2}{2n\pi} 
ight) = rac{L}{n\pi} = rac{L}{\pi} rac{1}{n}$$
4.  **Ensamblaje Espectral Final:**
    Sustituyendo los coeficientes calculados dentro de la serie trigonométrica:
        $$f(x) = \sum_{n=1}^{\infty} b_n \operatorname{sen}\left(rac{2n\pi x}{L}
ight) = \sum_{n=1}^{\infty} rac{L}{\pi}rac{1}{n} \operatorname{sen}\left(rac{2n\pi x}{L}
ight)$$
    Factorizando la constante espacial fuera de la sumatoria convergente:
        $$rac{1}{2}L - x = rac{L}{\pi} \sum_{n=1}^{\infty} rac{1}{n} \operatorname{sen}\left(rac{2n\pi x}{L}
ight)$$
    **Q.E.D. (Queda Demostrado).**
