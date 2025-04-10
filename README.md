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

### Ejemplo Biela Manivela

En principio realizamos el montaje dentro del espacio de trabajo Simscape Multibody; en primera instancia se coloca la transformación de ejes con el rigid transform para manejar el eje que deseemos dentro del modelo de movimiento, seguidamente se conectará un prismático el cual ejercerá el movimiento de las piezas dentro del diseño, esta salida se visualizará mediante un scope.

Además, se realizó la conexión de un revolution joint el cual genera el movimiento en el efector final del sistema para darle accionamiento al actuador, se realizó la conexión a nuestros perfiles de movimiento y se repite el proceso 2 instancias más para darle movimiento a cada uno de los perfiles de movimiento; por último se realiza un reajuste de ejes para poder mover cada una de las piezas sobre el mismo eje coordinado.


![](Manivela.jpg)


![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_sexta_semana/blob/e5fc03c8607472c62c4ebbcd9183101668ee143d/Manivela2.jpg)

### Ejemplo Prismático

Para el desarrollo de este ejemplo utilizamos el diseño de un perfil de movimiento el cual realizará la acción desiganda en el sistema mediante el bloque prismático. Para este proceso, en primera medida se realiza el reajuste de ejes para poder realizar el movimiento del sistema en el mismo eje coordinado. Una vez realizado la conexión de los sistemas se conectará directo al efector al cual se le aplicará movimiento y la nueva dirección de funcinamiento destinada por los planos de referencia con el que cuenta el sistema. 

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_sexta_semana/blob/b95e4ac4a06fc853ab1a897a0adaa2e2cc8fc5cd/primastico.jpg)


![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_sexta_semana/blob/f07a8938c5f45b0ebb052263f02411fdec653240/README.md)

### Ejemplo Revolute Join

Para este sistema se utilizará el cuadro de revolute joinel cual irá conectado a cada uno de nuestros perfiles de movimiento conectados y asignados mediante el sistema de coordenadas que se repite periodicamente 2 secciones más. La conexión de este sistema nos permite poder ajustar el movimiento de los 3 perfiles al tiempo sin generar ningún
bloquedo frente al movimiento de los demás

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_sexta_semana/blob/6d3108f30bae0e863b266a62ae9ac5f851186f45/movimiento%20triple.jpg)

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_sexta_semana/blob/c88fc8a30b33635756d34a00cbed491971fa9908/movimiento%20triple%202.jpg)

## 5. Conclusiones

* El diseño de eslabones en Simulink con Simscape Multibody permite modelar con alta fidelidad mecanismos mecánicos reales. Gracias al uso de bloques como Solid, Revolute Joint y Prismatic Joint, se puede representar el comportamiento dinámico de sistemas con movimiento rotacional o traslacional.

* Al combinar diferentes tipos de juntas y eslabones, es posible simular desde mecanismos simples como una biela-manivela, hasta estructuras más complejas como robots articulados o sistemas de suspensión.

* El uso del bloque PS Converter permite integrar señales matemáticas de Simulink, como una onda senoidal, dentro del entorno físico de Simscape. Esto abre la posibilidad de aplicar entradas dinámicas, controlar movimientos o analizar respuestas en función de señales programadas.

* Simscape Multibody permite no solo visualizar el movimiento de los eslabones, sino también analizar fuerzas, velocidades angulares, desplazamientos y torques, lo que lo convierte en una herramienta potente para validación y prototipado virtual.

* Al entender los conceptos fundamentales de los eslabones y su modelado en Simulink, se sienta la base para implementar sistemas de control, optimización de mecanismos, o incluso inteligencia artificial aplicada a sistemas mecánicos.

## 7. Referencias
