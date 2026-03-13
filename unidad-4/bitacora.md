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

### Actividad 11
- Describe el concepto de tu obra generativa. Recuerda que desde la unidad anterior añadimos la idea de narrativa a la obra generativa, para guiar algunas de las decisiones en la definición de reglas del sistema generativo. PERO OJO, no estamos contando una historia, estamos usando la narrativa como herramienta de diseño para la definición de reglas.  
Quise usar como narrativa esta vez, un pendulo que fuese un reloj de bolsillo, y que este represente el inevitable paso del tiempo, reforzandolo con un sonido y textos tetricos.


- El código de la aplicación.
Pendulum:
```js


class Pendulum {
  constructor(x, y, r) {
    // Fill all variables
    this.pivot = createVector(x, y);
    this.bob = createVector();
    this.r = r;
    this.angle = PI / 4;

    this.angleVelocity = 0.0;
    this.angleAcceleration = 0.0;
    this.damping = 0.998; // Arbitrary damping
    this.ballr = 24.0; // Arbitrary ball radius
    
    this.prevAngleVelocity = 0;
    
  }

  // Function to update position
update() {
  if (!this.dragging) {
    let gravity = 0.4;

    this.angleAcceleration = ((-1 * gravity) / this.r) * sin(this.angle);
    this.angleVelocity += this.angleAcceleration;
    this.angle += this.angleVelocity;

    this.angleVelocity *= this.damping;

    // Detectar cambio de dirección
    if (this.prevAngleVelocity * this.angleVelocity < 0) {
      this.onAngularStop();
    }

    this.prevAngleVelocity = this.angleVelocity;
  }
}

  show() {

    // calcular posición del reloj
    this.bob.set(this.r * sin(this.angle), this.r * cos(this.angle));
    this.bob.add(this.pivot);

    // cadena
    stroke(120);
    strokeWeight(2);
    line(this.pivot.x, this.pivot.y, this.bob.x, this.bob.y);

    // pivote
    fill(150);
    circle(this.pivot.x, this.pivot.y, 8);

    push();
    translate(this.bob.x, this.bob.y);

    // caja del reloj
    stroke(80);
    strokeWeight(3);
    fill(212,175,55);
    circle(0, 0, this.ballr * 2.8);

    // carátula
    fill(245);
    strokeWeight(1);
    circle(0, 0, this.ballr * 2.2);

    // marcas de horas
    stroke(0);
    for (let i = 0; i < 12; i++) {
      let a = TWO_PI * i / 12;

      let r1 = this.ballr * 0.8;
      let r2 = this.ballr * 0.95;

      let x1 = r1 * sin(a);
      let y1 = -r1 * cos(a);

      let x2 = r2 * sin(a);
      let y2 = -r2 * cos(a);

      line(x1, y1, x2, y2);
    }

    // manecilla minutos
    strokeWeight(2);
    let minuteAngle = frameCount * 0.02;

    line(
      0,
      0,
      sin(minuteAngle) * this.ballr * 0.8,
      -cos(minuteAngle) * this.ballr * 0.8
    );

    // manecilla horas
    strokeWeight(3);
    let hourAngle = frameCount * 0.005;

    line(
      0,
      0,
      sin(hourAngle) * this.ballr * 0.5,
      -cos(hourAngle) * this.ballr * 0.5
    );

    // centro
    fill(0);
    circle(0, 0, 4);

    pop();
  }

  // The methods below are for mouse interaction

  // This checks to see if we clicked on the pendulum ball
  clicked(mx, my) {
    let d = dist(mx, my, this.bob.x, this.bob.y);
    if (d < this.ballr) {
      this.dragging = true;
    }
  }

  // This tells us we are not longer clicking on the ball
  stopDragging() {
    this.angleVelocity = 0; // No velocity once you let go
    this.dragging = false;
  }

  drag() {
    // If we are draging the ball, we calculate the angle between the
    // pendulum origin and mouse position
    // we assign that angle to the pendulum
    if (this.dragging) {
      let diff = p5.Vector.sub(this.pivot, createVector(mouseX, mouseY)); // Difference between 2 points
      this.angle = atan2(-1 * diff.y, diff.x) - radians(90); // Angle relative to vertical axis
    }
    
    
    
  }
  
  
  
  onAngularStop() {
    


    
    let r = random(0, 255); // r is a random number between 0 - 255
    let g = random(0,255); // g is a random number betwen 100 - 200
    let b = random(0, 255); // b is a random number between 0 - 100
    let c = color(r,g,b,255);
    background(c);
    bells.play();
    
    let choiceTxt = random(txt);
    
    fill(255);
    noStroke();
    textSize(50);
    text(choiceTxt, random(height), random(width));
  }
}


```


sketch:
```js

let pendulum;
let bells;
let txt= ['tick','tack','you cant escape time'];
function setup() {
  createCanvas(900, 800);
  // Make a new Pendulum with an origin position and armlength
  pendulum = new Pendulum(width / 2, 0, 500);
  bells = loadSound('mm_clocktower_bell.mp3');
}

function draw() {
  background(0, 5);
  pendulum.update();
  pendulum.show();

  pendulum.drag(); // for user interaction
}

function mousePressed() {
  pendulum.clicked(mouseX, mouseY);
}

function mouseReleased() {
  pendulum.stopDragging();
}


```

- Un enlace al proyecto en el editor de p5.js.
https://editor.p5js.org/ThomasHyCr/sketches/MiOfTFzKC


- Selecciona capturas de pantalla representativas de tu pieza de arte generativa.
<img width="884" height="737" alt="image" src="https://github.com/user-attachments/assets/8fe72b0c-df21-43a0-a614-9403082fa874" />

<img width="807" height="616" alt="image" src="https://github.com/user-attachments/assets/23afce0e-b20f-4819-85e9-cdb485fc2cf6" />


## Bitácora de reflexión

- Realiza un diagrama conceptual (puedes usar excalidraw si quieres) donde incluyas todos los conceptos que has aprendido en las unidades 1 a 4. Relaciona los conceptos entre ellos. Si no sabes por donde comenzar ve al sitio web del libro guía y mira la tabla de contenidos de cada unidad, esto te puede servir de guía.  

[Véase figura 1, en los archivos montados]  

  
Muchos de estos conceptos se ven relacionados entre si, principalmente porque muchos de ellos al combinarse con otros conceptos se forman, por ejemplo en el marco de Motion 101, se combinan los conceptos de movimiento, vectores, e incluso fuerzas, los cuales después, y a su vez, son los que se usan para los pendulos, etc.


- Con todo lo que has aprendido hasta ahora, te voy a pedir que pienses cómo lo podrías aplicar a tu perfil profesional. ¿En dónde ves oportunidades?  
Personalmente, creo que prácticamente todo esto puede ser aplicado, ya que mi perfil profesional es el diseño, y los videojuegos, por lo tanto debido a su naturaleza tan versatil, todo, mientras pueda imaginarlo, se puede aplicar.






