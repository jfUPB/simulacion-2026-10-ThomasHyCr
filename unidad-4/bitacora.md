# Unidad 4
<img width="1000" height="563" alt="image" src="https://github.com/user-attachments/assets/ec5778e5-a51a-42e0-b472-341ad541ecf6" />

## Bitácora de proceso de aprendizaje
### Actividad 01
- Documenta en tu bitácora de aprendizaje los aspectos que más te llamaron la atención de la obra de Memo.
El uso de sonidos, complementado por los demás elementos de las obras

### Actividad 02
- ¿Qué hace la función heading()?
Da el angulo que forma con el eje x, del vector

- ¿Qué hace la función push() y pop()? Realiza algunos experimentos para entender su funcionamiento.
Almacena los cambios hechos sobre las transformaciones de los dibujos realizados entre ambas funciones, y una vez terminadas, se restablecen a como se encontraban antes de ingresar a ellas.

- ¿Qué hace rectMode(CENTER)? Realiza algunos experimentos para entender su funcionamiento.
Cambia el pivote de las figuras a dibujar

- ¿Cuál es la relación entre el ángulo de rotación y el vector de velocidad? Trata de dibujar en un papel el vector de velocidad y cómo se relaciona con el ángulo de rotación y la operación de traslación y rotación.
El cambio en el angulo de rotación, modifica el angulo del vector de velocidad.

### Actividad 03
- Documenta en tu bitácora de aprendizaje tu proceso de creación de la simulación.
Empecé a partir del código anterior, con el pequeño detalle de que además le sumaba fuerzas perpendiculares al movimiento, con las teclas de las flechas, para que así pudiese girar hacia los lados.

### Actividad 04
- Identifica motion 101. ¿Qué modificación hay que hacer al motion 101 cuando se quiere agregar fuerzas acumulativas? Trata de recordar por qué es necesario hacer esta modificación.
Se limita la distancia para evitar resultados extremos, al reducirse mucho las distancias.

- Identifica dónde está el Attractor en la simulación. Cambia el color de este.
Está en la clase attractor, pero este ya cuenta con una función que le cambia el color.
  
- Observa que el Attractor tiene dos atributos this.dragging y this.rollover. Estos atributos no se modifican en el código, pero permitirían mover el attractor con el mouse y cambiar su color cuando el mouse está sobre él. ¿Cómo podrías modificar el código para que esto funcione? considera las funciones que ofrece p5.js para interactuar con el mouse.
Le añado las funciones de interacción con el mouse al sketch, y en el attractor, le añadi las funciones, para que que se pueda mover con el mouse, y esto activa los 2 atributos con los que ya contaba anteriormente. 


### Actividad 05
- Observa de nuevo esta parte del código ¿Cuál es la relación entre r y theta con las posiciones x y y? Puedes repasar entonces la definición de coordenadas polares y cómo se convierten a coordenadas cartesianas.
r y theta son los parametros, bajo los cuales funciona el sistema de coordenadas polares, de modo que en el código se hace una traducción de estos, para que en este funcione con x y y. 

  
- Modifica la función draw(): ¿Qué ocurre? ¿Por qué?
El programa no corre, ya que al definir el vector, no sé esta definiendo r como una "parte del vector", ni se hace una traducción de las componentes de esta, y se intenta usar bajo x y y.


- Ahora realiza esta modificación: ¿Qué ocurre aquí? ¿Por qué?
Ahora el programa funciona como con el original, excepto que en este no se cambia el radio del circulo en función de la altura y el seno de theta, sino que está constante.

### Actividad 06
- Documenta tus reflexiones sobre la función sinusoide en tu bitácora de aprendizaje.
Es una función muy util para generar ciclos, movimientos ciclicos, dado a su recorrido tan particular y "perfecto".

### Actividad 07
- Documenta en tu bitácora de aprendizaje el proceso de modificación de la simulación.
Cambié todo el marco bajo el que funcionaba todo el proyecto, y finalmente puse que el color bajo el que funciona el "show", fuese cada vez que se llama de un color aleatorio usando random()

### Actividad 08
- Documenta en tu bitácora de aprendizaje el proceso de modificación de la simulación.
Comencé pasando toda la sección que dibuja la onda, a la función draw, y ahí le modifiqué los parametros para que se dibuje como una ola constantemente-

### Actividad 09
- Documenta en tu bitácora de aprendizaje el proceso de modificación de la simulación.
Similar a como fué con ejemplo anterior, modifiqué este código para que el color y el tamaño de la circunferencia se modifique según su coordenada polar.

### Actividad 10
- Documenta en tu bitácora de aprendizaje el proceso de modificación de la simulación.
Nuevamente jugué con las coordenadas polares para el tamaño del pendulo, pero además, según el angulo al que se encuentra el pendulo dicta su color.

## Bitácora de aplicación 



## Bitácora de reflexión



