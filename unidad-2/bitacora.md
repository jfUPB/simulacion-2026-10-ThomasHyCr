# Unidad 2
<img width="1000" height="462" alt="image" src="https://github.com/user-attachments/assets/71de743e-46be-4982-a073-ac658baf841a" />

## Bitácora de proceso de aprendizaje

### Actividad #2: Introducción a los vectores
- ¿Cómo funciona la suma dos vectores en p5.js?
Se deben sumar sus componentes individualmente, lo que da un nuevo vector como resultado.

- ¿Por qué esta línea position = position + velocity; no funciona?
Porque se está intentando sumar los vectores explicitamente, en lugar de implicitamente, mediante la suma de sus componentes.

### Actividad #3: Repasa
- ¿Qué tuviste que hacer para hacer la conversión propuesta?
Cambiar el constructor, para que creara el vector, y en point(), ponerle que reciba el vector, y finalmente en el random walker, que le sumara o restara al componente correspondiente.

- Escribe el código que utilizaste para resolver el ejercicio.
```js

// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(0);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.vector = createVector(width/2,height/2);
  }

  show() {
    stroke(255);
    point(this.vector);
  }

  step() {
    const choice = floor(random(4));
    if (choice == 0) {
      this.vector.x++;
    } else if (choice == 1) {
      this.vector.x--;
    } else if (choice == 2) {
      this.vector.y++;
    } else {
      this.vector.y--;
    }
  }
}


```

### Actividad #4: Experimenta
- ¿Qué resultado esperas obtener en el programa anterior?
Que se imprima en el log el vector 2 veces, primero el original, y segundo el cambiado

- ¿Qué resultado obtuviste?
El esperado

- Recuerda los conceptos de paso por valor y paso por referencia en programación.
Paso por valor es pasando una copia del valor, y el por referencia, pasa una referencia del valor almacenado, por lo que si se puede cambiar el original.

- ¿Qué tipo de paso se está realizando en el código?
referencia, porque se modifica el original

- ¿Qué aprendiste?
diferencia de los pasos, y cómo se podrian usar.

### Actividad #5: Explora posibilidades
- ¿Para qué sirve el método mag()? Nota que hay otro método llamado magSq(). ¿Cuál es la diferencia entre ambos? ¿Cuál es más eficiente?
Para sacar la magnitud de un vector, y para la magnitud al cuadrado. Dependiendo de lo que se requiera cualquiera podría ser el más eficiente, ya que ahorra el uso de una operación.

- ¿Para qué sirve el método normalize()?
Para normalizar un vector, para obtener su dirección.

- Te encuentras con un periodista en la calle y te pregunta ¿Para qué sirve el método dot()? ¿Qué le responderías en un frase?
Para hallar el producto punto entre dos vectores

- El método dot() tiene una versión estática y una de instancia. ¿Cuál es la diferencia entre ambas?
La forma en que se llama al método.

- Ahora el mismo periodista curioso de antes te pregunta si le puedes dar una intuición geométrica acerca del producto cruz. Entonces te pregunta ¿Cuál es la interpretación geométrica del producto cruz de dos vectores? Tu respuesta debe incluir qué pasa con la orientación y la magnitud del vector resultante.
La orientación es perpendicular al plano que forman los dos vectores, y su magnitud es el area de la forma que generan.

- ¿Para que te puede servir el método dist()?
Para hallar la distancia entre dos puntos.

- ¿Para qué sirven los métodos normalize() y limit()?
Para normalizar y para limitar.


### Actividad #6: Interpolamos?
- El código que genera el resultado que te pedí.
```js
let off= 0.0;
let forward;

function setup() {
    createCanvas(500, 500);
}

function draw() {
    background(0);

    let v0 = createVector(50, 50);
    let v1 = createVector(400, 0);
    let v2 = createVector(0, 400);
    let v3 = p5.Vector.lerp(v1, v2, off);
    let endV1 = v0.copy().add(v1);
    let endV2 = v0.copy().add(v2);
    let v4 = p5.Vector.sub(endV2,endV1);
    drawArrow(v0, v1, 'red');
    drawArrow(v0, v2, 'blue');
    drawArrow(v0, v3, 'purple');
    drawArrow(endV1, v4, 'green');
  if (forward){
    off=off+0.05;
  }
  else{
    off=off-0.05;
  }
  if(off>=1.0){
    forward=false;
  }
  else if(off<=0.0){
    forward=true;
  }
    
}

function drawArrow(base, vec, myColor) {
    push();
    stroke(myColor);
    strokeWeight(3);
    fill(myColor);
    translate(base.x, base.y);
    line(0, 0, vec.x, vec.y);
    rotate(vec.heading());
    let arrowSize = 7;
    translate(vec.mag() - arrowSize, 0);
    triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
    pop();
}
```
- ¿Cómo funciona lerp() y lerpColor().

Funciona para hallar el valor de la sección especificada entre 2 puntos. Y el lerp color realiza lo mismo, pero para el color, de forma que haya un color entre los dos colores especificados.

- ¿Cómo se dibuja una flecha usando drawArrow()?

Primero especifica las caracteristicas de grosor y color de la linea, luego traslada el sistema de coordenadas al parametro de base que le fué dado, luego dibuja la linea, desde la base, hasta el vector que le fué dado, después rota el sistema de coordenadas en la dirección a la que apunta el vector de la flecha que se está dibujando, define el tamaño de la punta de la flecha, nuevamente traslada el sistema de coordenadas al final de la linea, dibuja la punta de la flecha, y reestablece el sistema de coordenadas a la normalidad,

### Actividad #7: Motion 101
- Cuál es el concepto del marco motion 101 y cómo se interpreta geométricamente.

Son los conceptos básicos del movimiento de fisica mecanica, pero simplificados para aplicarlos fácilmente a las aplicaciones. Geometricamente sería como bajo que reglas se rige el movimiento de las figuras que tenemos en las aplicaciones.

- ¿Cómo se aplica motion 101 en el ejemplo?

Se simula una caida, dandole a la figura una aceleración constante hacia abajo, actuando como la gravedad. Y además también se le pone una velocidad limite, de forma que no continua aumentando su velocidad indefinidamente.

### Actividad #8: Experimentando con la aceleración
- ¿Qué observaste cuando usas cada una de las aceleraciones propuestas?

Con aceleración constante, en el caso del ejemplo 1.8, funciona como una simulación sencilla de la gravedad. En la de aceleración aleatoria tiene un comportamiento bastante erratico, pero en cierta forma como natural. Y finalmente con la aceleración hacia el mouse, funciona como una especia de "seguidor", que intenta estar siempre en la posición del mouse, pero que debido a las aceleraciones, le cuesta estar quieto en un solo sitio.



## Bitácora de aplicación 

### Actividad #9: Creación de obra generativa

## Bitácora de reflexión

### Actividad #10: 










