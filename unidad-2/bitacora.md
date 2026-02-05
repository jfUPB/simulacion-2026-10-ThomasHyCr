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
- ¿Qué resultado obtuviste?
- Recuerda los conceptos de paso por valor y paso por referencia en programación.
- ¿Qué tipo de paso se está realizando en el código?
- ¿Qué aprendiste?

### Actividad #5: Explora posibilidades
- ¿Para qué sirve el método mag()? Nota que hay otro método llamado magSq(). ¿Cuál es la diferencia entre ambos? ¿Cuál es más eficiente?
- ¿Para qué sirve el método normalize()?
- Te encuentras con un periodista en la calle y te pregunta ¿Para qué sirve el método dot()? ¿Qué le responderías en un frase?
- El método dot() tiene una versión estática y una de instancia. ¿Cuál es la diferencia entre ambas?
- Ahora el mismo periodista curioso de antes te pregunta si le puedes dar una intuición geométrica acerca del producto cruz. Entonces te pregunta ¿Cuál es la interpretación geométrica del producto cruz de dos vectores? Tu respuesta debe incluir qué pasa con la orientación y la magnitud del vector resultante.
- ¿Para que te puede servir el método dist()?
- ¿Para qué sirven los métodos normalize() y limit()?

### Actividad #6: Interpolamos?
- El código que genera el resultado que te pedí.
- ¿Cómo funciona lerp() y lerpColor().
- ¿Cómo se dibuja una flecha usando drawArrow()?

### Actividad #7: Motion 101

### Actividad #8: Experimentando con la aceleración



## Bitácora de aplicación 

### Actividad #9: Creación de obra generativa

## Bitácora de reflexión

### Actividad #10: 




