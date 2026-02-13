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
- Describe el concepto de tu obra generativa. Explica el concepto de tu obra generativa, qué regla aplicaste para la aceleración y por qué, si fue una decisión de diseño, o qué te evoca, si fue una exploración artística.
Quería hacer una simulación de una tormenta de lluvia en mitad del oceano, de modo que los conceptos de motion 101 que usé se aplicaron a la lluvia, y para las nubes y el oceano, usé un noise. Me evoca "contradictoriamente" una calma, en mitad de la tormenta.

- El código de la aplicación.
```js

let rain = [];

function setup() {
  createCanvas(900, 600);
  
  for (let i = 0; i < 150; i++) {
    rain.push({
      pos: createVector(random(width), random(height)),
      vel: createVector(0, 0)
    });
  }
}

function draw() {
  background(0, 50);
  stroke("rgb(221,255,251)");

  // Mapear mouseX a viento horizontal
  let windStrength = map(mouseX, 0, width, -0.2, 0.2);
  
  // Viento + gravedad
  let wind = createVector(windStrength, 0.1);

  for (let r of rain) {
    
    let prev = r.pos.copy();
    
    // Aplicar aceleración (viento)
    r.vel.add(wind);
    r.vel.limit(10,10);
    r.pos.add(r.vel);
    
    line(prev.x, prev.y, r.pos.x, r.pos.y);
    
    // Reiniciar cuando salen
    if (r.pos.y > height) {
      r.pos.y = 0;
      r.vel.y=5;
    }
    
    // Reaparecer lateralmente
    if (r.pos.x > width) r.pos.x = 0;
    if (r.pos.x < 0) r.pos.x = width;
  }
  
  clouds();
  sea();
  
  
}

function clouds(){
  
  // Set the noise level and scale.
  let noiseLevel = 100;
  let noiseScale = 0.003;

  // Iterate from left to right.
  for (let x = 0; x < width; x += 1) {
    // Scale the input coordinates.
    let nx = noiseScale * x;
    let nt = noiseScale * frameCount;

    // Compute the noise value.
    let y = noiseLevel * noise(nx, nt);
    
    // Draw the line.
    stroke("rgb(187,187,187)");
    line(x, 0, x, y);
  }
  
}

function sea(){
// Set the noise level and scale.
let noiseLevel = 200;
let noiseScale = 0.008;

for (let x = 0; x < width; x += 1) {
  let nx = noiseScale * x;
  let nt = noiseScale * frameCount;

  let y = noiseLevel * noise(nx, nt);

  stroke("rgb(23,60,104)");
  line(x, height, x, height - y);
}

  
}


```

- Un enlace al proyecto en el editor de p5.js.
https://editor.p5js.org/ThomasHyCr/sketches/reOL8vR9h

- Selecciona capturas de pantalla representativas de tu pieza de arte generativa.
<img width="851" height="584" alt="image" src="https://github.com/user-attachments/assets/6559ea45-7d53-48d5-bafe-654e079856be" />



## Bitácora de reflexión

### Actividad #10: 

- Describe el concepto de tu obra generativa. Explica el concepto de tu obra generativa.
####
Quería crear una especie de "creador de amebas", ya que luego de experimentar varias veces con el código de Jeffrey Ventrella, hubo una iteración en la que la forma en que se comportaban las particulas, era similar al movimiento de las amebas, de modo que intenté recrearlo ayudandome de chat GPT, para crear las reglas de las interacciónes, y le añadí interacción con el mouse y un poco de aleatoriedad.
  
- El código de la aplicación.
```js

let particlesA = [];
let particlesB = [];
let particlesC = [];

let minDistance = 60;
let separationStrength = 0.8;
let mouseAttractionStrength = 2;

// Colores globales por tipo
let colorA, colorB, colorC;

function setup() {
  createCanvas(windowWidth, windowHeight);

  // Generar colores aleatorios para cada tipo
  colorA = color(random(255), random(255), random(255));
  colorB = color(random(255), random(255), random(255));
  colorC = color(random(255), random(255), random(255));

  for (let i = 0; i < 30; i++) {
    particlesA.push(new ParticleTypeA(random(width), random(height)));
    particlesB.push(new ParticleTypeB(random(width), random(height)));
    particlesC.push(new ParticleTypeC(random(width), random(height)));
  }
}

function draw() {
  background(20);

  // =============================
  // A ACELERA HACIA EL MOUSE
  // =============================

  let mouse = createVector(mouseX, mouseY);

  for (let a of particlesA) {
    let forceToMouse = p5.Vector.sub(mouse, a.pos);
    let distance = forceToMouse.mag();

    distance = constrain(distance, 5, 200);
    forceToMouse.normalize();

    let strength = mouseAttractionStrength / (distance * 0.05);
    forceToMouse.mult(strength);

    a.applyForce(forceToMouse);
  }

  // =============================
  // INTERACCIONES ENTRE TIPOS
  // =============================

  // A atrae B
  for (let a of particlesA) {
    for (let b of particlesB) {
      b.applyForce(attractForce(a, b, 0.2));
    }
  }

  // B atrae C
  for (let b of particlesB) {
    for (let c of particlesC) {
      c.applyForce(attractForce(b, c, 0.15));
    }
  }

  // A y C se repelen
  for (let a of particlesA) {
    for (let c of particlesC) {
      let rep = attractForce(a, c, -0.25);
      a.applyForce(rep);
      c.applyForce(p5.Vector.mult(rep, -1));
    }
  }

  // C se repelen entre sí
  for (let i = 0; i < particlesC.length; i++) {
    for (let j = i + 1; j < particlesC.length; j++) {

      let c1 = particlesC[i];
      let c2 = particlesC[j];

      let rep = attractForce(c1, c2, -0.3);

      c1.applyForce(rep);
      c2.applyForce(p5.Vector.mult(rep, -1));
    }
  }

  // =============================
  // SEPARACIÓN GLOBAL
  // =============================

  let allParticles = [...particlesA, ...particlesB, ...particlesC];

  for (let i = 0; i < allParticles.length; i++) {
    for (let j = i + 1; j < allParticles.length; j++) {

      let p1 = allParticles[i];
      let p2 = allParticles[j];

      let force = separationForce(p1, p2);

      p1.applyForce(force);
      p2.applyForce(p5.Vector.mult(force, -1));
    }
  }

  // =============================
  // ACTUALIZAR Y MOSTRAR
  // =============================

  for (let p of particlesA) { p.update(); p.display(); }
  for (let p of particlesB) { p.update(); p.display(); }
  for (let p of particlesC) { p.update(); p.display(); }
}

/* =============================
   FUERZA TIPO GRAVITACIONAL
============================= */

function attractForce(source, target, strength) {
  let force = p5.Vector.sub(source.pos, target.pos);
  let distance = force.mag();

  distance = constrain(distance, 5, 120);
  force.normalize();

  let magnitude = strength / (distance * 0.05);
  force.mult(magnitude);

  return force;
}

/* =============================
   SEPARACIÓN GLOBAL
============================= */

function separationForce(p1, p2) {
  let force = p5.Vector.sub(p1.pos, p2.pos);
  let distance = force.mag();

  if (distance > 0 && distance < minDistance) {
    force.normalize();
    let strength = separationStrength * (1 - distance / minDistance);
    force.mult(strength);
    return force;
  }

  return createVector(0, 0);
}

/* =============================
   CLASE BASE
============================= */

class BaseParticle {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.vel = p5.Vector.random2D();
    this.acc = createVector(0, 0);
    this.maxSpeed = 3;
  }

  applyForce(force) {
    this.acc.add(force);
  }

  update() {
    this.vel.add(this.acc);
    this.vel.limit(this.maxSpeed);
    this.pos.add(this.vel);
    this.acc.mult(0);
    this.edges();
  }

  edges() {
    if (this.pos.x > width) this.pos.x = 0;
    if (this.pos.x < 0) this.pos.x = width;
    if (this.pos.y > height) this.pos.y = 0;
    if (this.pos.y < 0) this.pos.y = height;
  }
}

/* =============================
   TIPO A
============================= */

class ParticleTypeA extends BaseParticle {
  constructor(x, y) {
    super(x, y);
    this.size = 8;
  }

  display() {
    noStroke();
    fill(colorA);
    ellipse(this.pos.x, this.pos.y, this.size);
  }
}

/* =============================
   TIPO B
============================= */

class ParticleTypeB extends BaseParticle {
  constructor(x, y) {
    super(x, y);
    this.size = 12;
  }

  display() {
    noStroke();
    fill(colorB);
    rect(this.pos.x, this.pos.y, this.size, this.size);
  }
}

/* =============================
   TIPO C
============================= */

class ParticleTypeC extends BaseParticle {
  constructor(x, y) {
    super(x, y);
    this.size = 18;
  }

  display() {
    noFill();
    stroke(colorC);
    strokeWeight(2);
    ellipse(this.pos.x, this.pos.y, this.size);
  }
}


```
  
- Un enlace al proyecto en el editor de p5.js.
####
https://editor.p5js.org/ThomasHyCr/sketches/cp5th1pa-
  
- Selecciona capturas de pantalla representativas de tu pieza de arte generativa.
####
<img width="620" height="512" alt="image" src="https://github.com/user-attachments/assets/f3cf3faa-6eb0-4229-8234-85c62105283b" />
####
<img width="353" height="332" alt="image" src="https://github.com/user-attachments/assets/3eb75343-6910-49df-a4ac-08fb9e19688d" />















