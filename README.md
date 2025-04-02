# Apuntes-Sexta semana
Apuntes control de movimiento - Segundo Corte-Sexta Semana

# Diseño de Eslabones en Simulink
El diseño de eslabones en Simulink con Simscape Multibody permite modelar sistemas mecánicos compuestos por cuerpos rígidos conectados mediante articulaciones. Un eslabón es una pieza mecánica que transmite movimiento o fuerza dentro de un mecanismo, como en un brazo robótico, una biela-manivela o una suspensión automotriz.

## 1. Definición movimiento de perfil
El movimiento de un perfil está determinado como el movimiento dentro de una trayectoría para cumplir el recorrido de un punto A a un punto B. Existen diferentes casos dentro del movimiento de perfil que está dado por la cantidad de ejes que se quieran mover al tiempo.

>🔑 *Caso 1:* Es el caso más simple en el cual se mueve un solo eje por lo que el movimiento se observará como una línea recta.
>
>🔑 *Caso 2:* Para el manejo de diferentes ejes se requiere una combinación de diferentes perfiles para lograr una tarea específica; para entender el movimiento de cada eje se debe tener en cuenta la posición, velocidad y aceleración de cada etapa.
>

## Conceptos básicos de la Cinemática de Movimiento
### Cálculos de Perfil de Movimiento:
* Posición (X(t)):  Determina la ubicación del sistema o efector final en función del tiempo.
* Velocidad  $v(\tau): \frac{d\chi }{d\tau}$ : Evalúa la tasa de cambio de posición y permite definir un movimiento suave y eficiente. La anterior ecuación se puede reescribir en cuestión de integrales de la siguiente manera: $s=\int v(\tau )d\tau$.
* Aceleración $a(\tau): \frac{dv}{d\tau}$ : Controla la aceleración máxima para evitar esfuerzos mecánicos excesivos. La anterior ecuación se puede reescribir en cuestión de integrales de la siguiente manera: $s=\int a(\tau )d\tau$.

La siguiente imagen refleja el comportamiento gráfico de la posición, velocidad y aceleración. 

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Sexta-Semana/blob/0a3b3c05c17711da2cf50962724627c729bb02ea/perfil%20de%20movimiento.png)


## 2. Reglas Geométricas
Para el desarrollo y movimiento de perfiles se deben tener en cuenta diferentes conceptos frente a la dinámica de cada uno de los ejes del perfil. A continuación realizaremos una breve explicación de los puntos a tener en cuenta.
* Cualquier punto de la posición del movimiento del sistema está dado por el área bajo la curva de velocidad hasta el instante de tiempo a analizar.
* La aceleración se puede denotar como la pendiente de la curva de velocidad.
* Este análisis está dado por las siguientes ecuaciones:
  $v= v_{0} + a(t-t_{0})$

  $s=s_{0}+\frac{1}{2}(t-t_{0})(v_{0}+a(t-t_{0}))$

En las anteriores ecuaciones el parámetro $t_{0}$ es el tiempo inicial del movimiento del intervalo donde se calculará, $v_{0}$ es la velocidad inicial del sistema del intervalo donde se calculará y $s_{0}$ la posición inicial en la que se encontrará el sistema.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Sexta-Semana/blob/0d7817a8221d6b92206eb80cb93a1d519e691503/area%20bajo%20la%20curva.png)

## 3. Tipos de Perfiles

En sistemas mecánicos y de control, el movimiento se describe mediante cambios en la posición de un objeto a lo largo del tiempo. Dependiendo de cómo varíen la velocidad y la aceleración, se pueden clasificar en distintos tipos, cada uno con aplicaciones específicas en robótica, automatización y maquinaria industrial.

Los perfiles de movimiento más comunes incluyen:

**Perfil Trapezoidal**:  Es uno de los más utilizados en control de movimiento porque proporciona un equilibrio entre rapidez y suavidad. Se llama así porque la forma de la gráfica de velocidad en función del tiempo tiene un aspecto de trapezoide.

El movimiento se divide en tres fases principales:

*Aceleración constante*

* El sistema inicia desde el reposo y aumenta su velocidad de manera uniforme hasta alcanzar una velocidad máxima.

* La aceleración es constante en esta etapa.

*Velocidad constante*

* El sistema se mueve a velocidad máxima sin cambios.

* No hay aceleración ni desaceleración en esta fase.

*Desaceleración constante*

* El sistema reduce su velocidad de manera uniforme hasta detenerse o alcanzar el nuevo punto de destino.

* La desaceleración es constante y de la misma magnitud que la aceleración.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Sexta-Semana/blob/7049ff48ecd31d96b365c153e34da52d09cd3c59/perfil%20trapezoidal.png)

**Curva en S**: Es una evolución del perfil trapezoidal que suaviza los cambios bruscos en aceleración y desaceleración. Se llama así porque su gráfica de posición en función del tiempo tiene una forma similar a una letra "S".

Este tipo de movimiento es ideal cuando se busca minimizar vibraciones, reducir el impacto mecánico y mejorar la estabilidad en sistemas de control de movimiento.

El movimiento se divide en cinco fases principales:

*Aceleración progresiva*

* En lugar de iniciar con una aceleración constante, esta aumenta gradualmente, lo que suaviza el arranque.

*Aceleración constante*

* El sistema mantiene una aceleración estable hasta alcanzar la velocidad máxima.

*Velocidad constante*

* El sistema se desplaza sin cambios en la velocidad.

*Desaceleración constante*

* Se inicia la fase de frenado, reduciendo la velocidad de manera controlada.

*Desaceleración progresiva*

* En vez de frenar bruscamente, la desaceleración disminuye de manera gradual hasta el reposo.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Sexta-Semana/blob/77a85765182e09a1f234fc1bdefb7dcf80b80b5d/curva%20s.png)

*Modelo Matemático Curva en S*

* Según la cantidad de segmentos curvos que presente la velocidad, esta está dada por un modelo de polinomio de segundo orden.

$$v(t)=C_{1}t^{2} + C_{2}t + C{3}$$

  En la fórmula anterior $C_{1}$, $C_{2}$ y $C_{3}$ son coeficientes que están determinadas por las condiciones de frontera.

## 4. Movimiento Multi-eje
Se refiere a la coordinación de varios ejes de movimiento (X, Y, Z, rotación, etc.) para lograr trayectorias complejas y precisas en sistemas mecánicos y robóticos. Es fundamental en aplicaciones donde un solo eje no es suficiente para realizar una tarea, como en robots industriales, máquinas CNC y brazos manipuladores.

A continuación explicaremos 3 tipos de movimiento multi-eje:

*Movimiento Secuencial*

* Cada eje se mueve por separado, uno tras otro.

* Es simple de programar pero más lento.

*Movimiento Coordinado*

* Los ejes se mueven simultáneamente siguiendo una trayectoria planificada.

* Evita movimientos bruscos y reduce el tiempo de operación.

*Interpolación Multieje*

* Lineal: Mueve varios ejes a velocidad constante en línea recta.

* Circular: Crea trayectorias circulares coordinando dos ejes.

* Helicoidal: Combina movimiento circular con desplazamiento en otro eje.

* Spline: Usa curvas suaves para trayectorias precisas.


## 5. Ejercicios

## 6. Conclusiones

* El diseño adecuado de perfiles de movimiento en entornos virtuales como Simscape permite optimizar la eficiencia y precisión de los sistemas mecánicos, facilitando la simulación de trayectorias y desplazamientos controlados.

* El análisis de posición, velocidad y aceleración es fundamental para garantizar movimientos suaves y eficientes, evitando esfuerzos mecánicos excesivos y optimizando el rendimiento del sistema.

*Ventajas de los Perfiles de Movimiento Comunes*

* Perfil trapezoidal: Proporciona un equilibrio entre rapidez y suavidad, siendo ideal para aplicaciones que requieren eficiencia sin excesiva complejidad.

* Perfil en S: Reduce vibraciones y esfuerzos mecánicos al suavizar los cambios de aceleración y desaceleración, mejorando la estabilidad del sistema.

* La coordinación de múltiples ejes permite lograr trayectorias complejas en robótica, CNC y sistemas automatizados. Diferentes estrategias, como el movimiento secuencial, coordinado e interpolación multieje, permiten adaptar el sistema según los requisitos de la aplicación.

## 7. Referencias
