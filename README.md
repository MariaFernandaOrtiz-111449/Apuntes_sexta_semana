# Apuntes-Sexta semana
Apuntes control de movimiento - Segundo Corte-Sexta Semana

## 1. Diseño de Eslabones en Simulink
El diseño de eslabones en Simulink con Simscape Multibody permite modelar sistemas mecánicos compuestos por cuerpos rígidos conectados mediante articulaciones. Un eslabón es una pieza mecánica que transmite movimiento o fuerza dentro de un mecanismo, como en un brazo robótico, una biela-manivela o una suspensión automotriz.

En Simulink, cada eslabón se representa mediante un bloque Solid, donde se definen sus propiedades físicas como masa, forma y dimensiones. Los eslabones se conectan mediante juntas (como Revolute Joint o Prismatic Joint), que permiten definir los grados de libertad del sistema. Además, podemos aplicar fuerzas o torques para simular el comportamiento dinámico del mecanismo.

>🔑 *Revolute Joint:* es una articulación rotacional que permite que dos cuerpos giren uno respecto al otro en un solo eje. Es equivalente a una bisagra o a un eje de rotación en un sistema mecánico real, como el codo de un brazo robótico o la unión entre la biela y la manivela de un motor.

>🔑 *Primatic Joint:* es una articulación que permite el movimiento lineal (traslacional) entre dos cuerpos a lo largo de un solo eje, restringiendo todas las demás formas de movimiento. Es como una guía deslizante, un pistón, o el eje de un actuador lineal.

## 2. Bloque PS Converter en Simulink

El bloque PS Converter en Simulink se utiliza para convertir una señal del entorno de Simulink en una señal física (Physical Signal, PS). Esta conversión es esencial cuando se desea utilizar una señal matemática, como una onda senoidal, dentro de un modelo físico en Simscape.

Gracias a esta conversión, la señal puede ser conectada a bloques de Simscape que solo aceptan señales físicas, como por ejemplo:

* Fuentes de Simscape: para aplicar fuerzas, voltajes o torques.

* Joints con movimiento prescrito: para definir el desplazamiento o rotación de un cuerpo.

* Sensores físicos: para controlar o medir variables físicas dentro del modelo.

De esta manera, el PS Converter actúa como un puente entre el mundo matemático de Simulink y el mundo físico de Simscape, permitiendo la interacción y simulación conjunta de ambos entornos.

## 3. Conceptos claves

* Grados de Libertad (DOF): Un eslabón rotacional tiene un solo grado de libertad, lo que significa que puede rotar alrededor de un eje específico.

* Juntas Rotacionales: En Simulink, se usa el bloque "Revolute Joint" de Simscape Multibody para modelar una articulación rotacional.

* Par/Torque y Movimiento: Se pueden aplicar torques o definir movimientos preestablecidos a los eslabones.

* Sensores y Actuadores: Se pueden agregar sensores para medir ángulos y velocidades angulares, así como actuadores para controlar la rotación.

## 4. Ejercicios

## 5. Conclusiones

* El diseño de eslabones en Simulink con Simscape Multibody permite modelar con alta fidelidad mecanismos mecánicos reales. Gracias al uso de bloques como Solid, Revolute Joint y Prismatic Joint, se puede representar el comportamiento dinámico de sistemas con movimiento rotacional o traslacional.

* Al combinar diferentes tipos de juntas y eslabones, es posible simular desde mecanismos simples como una biela-manivela, hasta estructuras más complejas como robots articulados o sistemas de suspensión.

* El uso del bloque PS Converter permite integrar señales matemáticas de Simulink, como una onda senoidal, dentro del entorno físico de Simscape. Esto abre la posibilidad de aplicar entradas dinámicas, controlar movimientos o analizar respuestas en función de señales programadas.

* Simscape Multibody permite no solo visualizar el movimiento de los eslabones, sino también analizar fuerzas, velocidades angulares, desplazamientos y torques, lo que lo convierte en una herramienta potente para validación y prototipado virtual.

* Al entender los conceptos fundamentales de los eslabones y su modelado en Simulink, se sienta la base para implementar sistemas de control, optimización de mecanismos, o incluso inteligencia artificial aplicada a sistemas mecánicos.

## 7. Referencias
