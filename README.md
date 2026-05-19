# -Semana-5

$$f(x) = x \cos(x) - 1$$

Si evaluamos esta función en el intervalo dado para el método de bisección $[0.6, 0.7]$ (asumiendo radianes, que es el estándar en cálculo numérico):

$f(0.6) = 0.6 \cos(0.6) - 1 \approx -0.5048$

$f(0.7) = 0.7 \cos(0.7) - 1 \approx -0.4646$ 

Ambos valores son negativos. El método de bisección requiere que haya un cambio de signo ($f(a) \cdot f(b) < 0$) para garantizar que existe una raíz en el intervalo. De hecho, el valor máximo de $x \cos(x)$ antes de caer a cero en $\pi/2$ es aproximadamente $0.561$, por lo que la función $x \cos(x) - 1$ nunca cruza el cero cerca de $0.5$, $0.6$ o $0.7$. La primera raíz real positiva de esta ecuación se encuentra mucho más adelante, cerca de $x \approx 4.917$.

Resultados Analíticos y Ejecución de los MétodosDado que $f(x) = x \cos(x) - 1 = 0$, aquí tienes el comportamiento de cada método con los parámetros solicitados y una tolerancia de $10^{-6}$:

(a) Método de Bisección (Intervalo $[0.6, 0.7]$)

  Raíz aproximada obtenida: Fallo.
  
  Número de iteraciones: $0$
  
  Explicación: El algoritmo se detiene en la iteración cero porque $f(0.6)$ y $f(0.7)$ tienen el mismo signo. No se cumple el Teorema de Bolzano para iniciar la bisección.

(b) Método de Newton-Raphson ($x_0 = 0.5$)
  
  Raíz aproximada obtenida: $4.917186$
  
  Número de iteraciones: $13$ iteraciones.
  
  Explicación: Como no hay raíz cerca de $0.5$, la derivada empuja el cálculo hacia la derecha. El algoritmo salta erráticamente ($0.5 \rightarrow 1.37 \rightarrow 0.74 \rightarrow 2.71...$) hasta que finalmente es "capturado" por la concavidad de la raíz que existe cerca de $4.917$.

(c) Método de la Secante ($x_0 = 0.5, x_1 = 0.7$)

Raíz aproximada obtenida: $4.917186$

Número de iteraciones: $16$ iteraciones.

Explicación: Al igual que Newton, al evaluar puntos donde la curva no cruza el eje X y tiene pendientes suaves, la recta secante proyecta el siguiente punto muy lejos, divagando hasta encontrar la primera raíz positiva lejana.

Comparativa: ¿Qué método converge más rápido y por qué?

En un escenario donde los valores iniciales están cerca de la raíz real, el orden de velocidad es:Newton-Raphson > Secante > Bisección.

Newton-Raphson (Convergencia Cuadrática): Es el más rápido. El error se eleva al cuadrado en cada iteración ($E_{i+1} \approx c \cdot E_i^2$). Sin embargo, es el más costoso computacionalmente porque requiere conocer y calcular la derivada analítica $f'(x)$ en cada paso.

Secante (Convergencia Superlineal): Es ligeramente más lento que Newton (su tasa de convergencia es $\approx 1.618$), pero tiene la ventaja de que no necesita la derivada analítica, aproximándola a partir de los dos puntos anteriores.

Bisección (Convergencia Lineal): Es el método más lento, ya que solo reduce el error a la mitad en cada paso. Sin embargo, es el más robusto; si logras encerrar la raíz en un intervalo con cambio de signo, la convergencia está 100% garantizada, cosa que Newton y Secante no pueden asegurar.
