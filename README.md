# 🚀 Bootcamp de Análisis Matemático: Preparación para Finales

Esta guía está estructurada de manera secuencial. Cada tema incluye la teoría estrictamente necesaria, la metodología algorítmica de resolución y el desarrollo paso a paso de modelos de examen.

---

## 📘 FASE I: EDOs de Primer Orden

### 1. Variables Separables
*   **Definición:** Ecuaciones que se pueden factorizar en la forma $\frac{dy}{dx} = g(x)h(y)$.
*   **Método:** Agrupar las variables $x$ con $dx$ y las $y$ con $dy$, luego integrar ambos lados de la igualdad: $\int \frac{1}{h(y)} dy = \int g(x) dx$.

**Ejercicio de Examen:**
$$ (y^3 - y)dx + (x y^2 + x - y^2 - 1)dy = 0 $$

**Paso 1: Factorización.**
Agrupamos por factor común en cada diferencial.
$$ y(y^2 - 1)dx + (x - 1)(y^2 + 1)dy = 0 $$

**Paso 2: Separación de Variables.**
Dividimos toda la ecuación para separar las variables.
$$ \frac{1}{x - 1}dx + \frac{y^2 + 1}{y(y^2 - 1)}dy = 0 $$

**Paso 3: Integración por Fracciones Parciales.**
La primera integral es directa. Para la segunda, separamos en fracciones parciales.
$$ \int \left( -\frac{1}{y} + \frac{1}{y-1} + \frac{1}{y+1} \right) dy = -\ln|y| + \ln|y-1| + \ln|y+1| = \ln\left| \frac{y^2 - 1}{y} \right| $$

**Paso 4: Solución General.**
Sumamos las integrales y aplicamos la propiedad exponencial para despejar.
$$ \ln|x - 1| + \ln\left| \frac{y^2 - 1}{y} \right| = C_0 \implies (x - 1)(y^2 - 1) = K y $$

### 2. Ecuaciones Homogéneas
*   **Definición:** Una EDO $M(x,y)dx + N(x,y)dy = 0$ es homogénea si $M$ y $N$ son funciones del mismo grado. Es decir, $M(tx, ty) = t^n M(x,y)$.
*   **Método:** Se aplica la sustitución paramétrica $y = zx$, sabiendo que la diferencial será $dy = z dx + x dz$. Esto siempre transforma la ecuación en una de variables separables.

**Ejercicio de Examen:**
$$ 2x^3y \, dx + (x^4 + y^4) \, dy = 0 $$

**Paso 1: Sustitución ($y=zx$).**
$$ 2x^3(zx)dx + (x^4 + z^4x^4)(zdx + xdz) = 0 $$
$$ 2x^4z \, dx + x^4(1 + z^4)(zdx + xdz) = 0 $$

**Paso 2: Simplificación.**
Dividimos por $x^4$ y agrupamos los diferenciales.
$$ (3z + z^5)dx + x(1 + z^4)dz = 0 $$

**Paso 3: Separación e Integración.**
$$ \frac{1}{x}dx + \frac{1 + z^4}{z(3 + z^4)}dz = 0 $$
Integrando por partes o descomposición obtenemos:
$$ \ln|x| + \frac{1}{3}\ln|z| + \frac{1}{6}\ln|3+z^4| = C_0 $$

**Paso 4: Retorno a variables originales.**
Multiplicando y aplicando exponenciales, reemplazamos $z = y/x$.
$$ x^6 \left(\frac{y}{x}\right)^2 \left[ 3 + \left(\frac{y}{x}\right)^4 \right] = C \implies y^2(3x^4 + y^4) = C $$

---

## 📗 FASE II: EDOs Lineales de Segundo Orden

### 1. Variación de Parámetros
*   **Definición:** Método analítico para resolver $y'' + P(x)y' + Q(x)y = f(x)$ cuando los coeficientes no son constantes o $f(x)$ no es una función fácilmente anulable.
*   **Método:**
    1. Hallar la solución de la homogénea: $y_h = C_1 y_1 + C_2 y_2$.
    2. Calcular el Wronskiano del sistema: $W = y_1 y_2' - y_2 y_1'$.
    3. Construir la solución particular $y_p = u_1 y_1 + u_2 y_2$, donde:
       $$ u_1 = \int \frac{-y_2 f(x)}{W} dx, \quad u_2 = \int \frac{y_1 f(x)}{W} dx $$

**Ejercicio de Examen:**
$$ y'' + 2y' + 2y = e^{-x} \sec x $$

**Paso 1: Solución Homogénea.** 
Calculamos las raíces del polinomio $r^2 + 2r + 2 = 0 \implies r = -1 \pm i$.
$$ y_h = e^{-x}(C_1 \cos x + C_2 \sin x) \implies y_1 = e^{-x}\cos x, \quad y_2 = e^{-x}\sin x $$

**Paso 2: Wronskiano.**
$$ W = (e^{-x}\cos x)(e^{-x}(\cos x - \sin x)) - (e^{-x}\sin x)(-e^{-x}(\cos x + \sin x)) = e^{-2x} $$

**Paso 3: Parámetros variables ($u_1, u_2$).**
$$ u_1 = \int \frac{-(e^{-x}\sin x)(e^{-x}\sec x)}{e^{-2x}} dx = \int -\tan x dx = \ln|\cos x| $$
$$ u_2 = \int \frac{(e^{-x}\cos x)(e^{-x}\sec x)}{e^{-2x}} dx = \int 1 dx = x $$

**Paso 4: Solución General ($y = y_h + y_p$).**
$$ y = e^{-x}(C_1 \cos x + C_2 \sin x) + e^{-x}(\cos x \ln|\cos x| + x \sin x) $$

---

## 📙 FASE III: Transformada de Laplace

### 1. Transformada Directa e Inversa
*   **Definición:** Operador integral lineal que convierte ecuaciones diferenciales temporales en ecuaciones algebraicas complejas: $\mathcal{L}\{f(t)\} = \int_{0}^{\infty} e^{-st} f(t) dt$.
*   **Propiedades Clave:**
    * $\mathcal{L}\{y'\} = sY(s) - y(0)$
    * $\mathcal{L}\{y''\} = s^2Y(s) - s y(0) - y'(0)$

**Ejercicio de Examen (Demostración de Identidad):**
$$ \mathcal{L}\{\cos^3 t\} = \frac{s(s^2+7)}{(s^2+9)(s^2+1)} $$

**Paso 1: Identidad Trigonométrica.**
$$ \cos^3 t = \frac{1}{4}\cos(3t) + \frac{3}{4}\cos t $$

**Paso 2: Aplicación del Operador Laplace.** 
Usando la propiedad de tabla $\mathcal{L}\{\cos(at)\} = \frac{s}{s^2+a^2}$:
$$ \mathcal{L}\{\cos^3 t\} = \frac{1}{4}\left( \frac{s}{s^2+9} \right) + \frac{3}{4}\left( \frac{s}{s^2+1} \right) $$

**Paso 3: Unificación Algebraica.**
$$ = \frac{s(s^2+1) + 3s(s^2+9)}{4(s^2+9)(s^2+1)} = \frac{4s^3 + 28s}{4(s^2+9)(s^2+1)} = \frac{s(s^2+7)}{(s^2+9)(s^2+1)} $$

**Ejercicio de Examen (PVI con Laplace):**
$$ y'' + 2y' + 2y = e^{2t}, \quad y(0)=1, \, y'(0)=2 $$

**Paso 1: Transformar la Ecuación.**
Aplicamos Laplace y sustituimos las condiciones iniciales:
$$ (s^2 Y(s) - s - 2) + 2(s Y(s) - 1) + 2Y(s) = \frac{1}{s-2} $$

**Paso 2: Despejar $Y(s)$ algebraicamente.**
$$ (s^2 + 2s + 2)Y(s) = \frac{1}{s-2} + s + 4 = \frac{s^2 + 2s - 7}{s-2} $$
$$ Y(s) = \frac{s^2 + 2s - 7}{(s-2)(s^2 + 2s + 2)} $$

**Paso 3: Fracciones Parciales e Inversa.**
$$ Y(s) = \frac{1/10}{s-2} + \frac{9/10(s+1) + 27/10}{(s+1)^2 + 1} $$
Aplicamos el Primer Teorema de Traslación para retornar al dominio temporal:
$$ y(t) = \frac{1}{10}e^{2t} + \frac{9}{10}e^{-t}\cos t + \frac{27}{10}e^{-t}\sin t $$

---

## 📕 FASE IV: Series de Fourier

### 1. Desarrollo en Serie Trigonométrica
*   **Definición:** Principio de análisis armónico que dictamina que toda función periódica $f(x)$ de período $2L$ se puede expresar como:
    $$ f(x) = a_0 + \sum_{n=1}^{\infty} \left[ a_n \cos\left(\frac{n\pi x}{L}\right) + b_n \sin\left(\frac{n\pi x}{L}\right) \right] $$

**Ejercicio de Examen:**
Demostrar que para $0 < x < L$:
$$ \frac{1}{2}L - x = \frac{L}{\pi} \sum_{n=1}^{\infty} \frac{1}{n} \sin\left(\frac{2n\pi x}{L}\right) $$

**Paso 1: Período y coeficientes nulos.** 
El período fundamental del argumento es $L$. La función es impar respecto al centro, por lo que las proyecciones pares son nulas: $a_0 = 0$ y $a_n = 0$.

**Paso 2: Planteamiento del coeficiente impar ($b_n$).**
$$ b_n = \frac{2}{L} \int_{0}^{L} \left(\frac{1}{2}L - x\right) \sin\left(\frac{2n\pi x}{L}\right) dx $$

**Paso 3: Integración por partes.**
$$ b_n = \frac{2}{L} \left[ \left(\frac{1}{2}L - x\right)\left(-\frac{L}{2n\pi}\cos\left(\frac{2n\pi x}{L}\right)\right) \right]_0^L $$
Evaluando en los límites superior e inferior:
$$ = \frac{2}{L} \left[ \frac{L^2}{4n\pi} - \left(-\frac{L^2}{4n\pi}\right) \right] = \frac{L}{n\pi} $$

**Paso 4: Ensamblaje de la Serie Final.**
Extraemos las constantes fuera de la sumatoria.
$$ f(x) = \sum_{n=1}^{\infty} \frac{L}{n\pi} \sin\left(\frac{2n\pi x}{L}\right) = \frac{L}{\pi} \sum_{n=1}^{\infty} \frac{1}{n} \sin\left(\frac{2n\pi x}{L}\right) $$
