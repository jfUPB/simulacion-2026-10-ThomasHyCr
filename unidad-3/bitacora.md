# Unidad 3

<img width="1000" height="490" alt="image" src="https://github.com/user-attachments/assets/a993962b-ae40-4768-9667-e894f52a0a48" />


## Bitácora de proceso de aprendizaje
### Actividad #1: 
Considero que es importante, sin importar que, hacer las cosas porque te gustan, y con el tema de las IA's es importante no depender de ellas, sino usarlas como una herramienta, o como un asistente.


### Actividad #2:
Es muy interesante cómo se traducen las formulas de fisica mecanica aquí, y cómo, en el caso de las fuerzas se aplican, para que tenga un correcto funcionamiento.


### Actividad #3:
En tu bitácora, vas a crear tres obras generativas para cada una de las siguientes fuerzas:

- Fricción:
https://editor.p5js.org/ThomasHyCr/sketches/9Y6vhtww1

- Resistencia al aire y fluidos:
https://editor.p5js.org/ThomasHyCr/sketches/oopP53vRN

- Atracción gravitacional:
https://editor.p5js.org/ThomasHyCr/sketches/d9Brw0W5I


## Bitácora de aplicación 

### Descripción

Describe el concepto de tu obra generativa. Explica la historia que quieres contar y cómo crees que esta influencierá las fuerzas que usarás para manipular la aceleración de los elementos visuales. En otras palabras, describe el vínculo entre tu narrativa y el sistema de reglas que dará vida a la composición visual.
Para el concepto, quise simular los distintos climas que pueden atravezar los aviones al volar, de forma que creé 4 modos: Estandar (con un buen lift), Nuboso (con un drag considerable), Ventoso (aumenta la velocidad y ligeramente el lift), y por ultimos Lluvioso (se aplica una fuerza vertical). En resumen se aplican distintas fuerzas en el sistema: Lift, Drag, Gravity, Thrust y Lluvia.

### El código de la aplicación.

- Plane.js:
```js
class Airplane {
  constructor(x, y, mass) {
    this.mass = mass;
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acceleration.add(f);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }
  
  checkEdges() {

  // Derecha → izquierda
  if (this.position.x > width) {
    this.position.x = 0;
  }

  // Izquierda → derecha
  if (this.position.x < 0) {
    this.position.x = width;
  }

  // Abajo → arriba
  if (this.position.y > height) {
    this.position.y = 0;
  }

  // Arriba → abajo
  if (this.position.y < 0) {
    this.position.y = height;
  }
}

  show() {
    push();
    translate(this.position.x, this.position.y);
    rotate(this.velocity.heading());

    fill(180);
    rect(-20, -5, 40, 10);

    fill(150);
    triangle(-10, 0, 0, -15, 10, 0);
    triangle(-20, -5, -30, -15, -20, 5);

    pop();
  }
}



```
- Rain.js:
```js
class Rain {
  constructor() {
    this.reset();
  }

  reset() {
    this.x = random(width);
    this.y = random(-800, 0);
    this.speed = random(4, 10);
  }

  update() {
    this.y += this.speed;
    if (this.y > height) {
      this.reset();
    }
  }

  show() {
    stroke(180, 180, 255);
    line(this.x, this.y, this.x, this.y + 10);
  }
}

function updateRain() {
  for (let drop of raindrops) {
    drop.update();
    drop.show();
  }
}

```

- Ambient:
```js
let airplanes = [];
let raindrops = [];
let mode = 1;
let windLines = [];

function setup() {
  createCanvas(1100, 800);

  for (let i = 0; i < 200; i++) {
    raindrops.push(new Rain());
  }
  
  for (let i = 0; i < 120; i++) {
  windLines.push(new WindLine());
}
}

function draw() {

  drawEnvironment();

  for (let plane of airplanes) {

    // GRAVEDAD
    let gravity = createVector(0, 0.1 * plane.mass);
    plane.applyForce(gravity);

    // THRUST BASE
    let thrust = createVector(0.2, 0);
    plane.applyForce(thrust);

    // DRAG BASE
    let speed = plane.velocity.mag();
    let baseDrag = plane.velocity.copy();
    baseDrag.mult(-1);
    baseDrag.setMag(0.02 * speed * speed);
    plane.applyForce(baseDrag);

    // LIFT BASE
    let lift = createVector(0, -plane.velocity.x * 0.05);

    // =========================
    // CAMBIO SEGÚN MODO
    // =========================

    // 1️⃣ ESTABLE
    if (mode === 1) {
      lift.mult(1.3);
    }

    // 2️⃣ NUBES (drag fuerte)
    if (mode === 2) {
      let cloudDrag = plane.velocity.copy();
      cloudDrag.mult(-1);
      cloudDrag.setMag(0.06 * speed * speed);
      plane.applyForce(cloudDrag);
    }

    // 3️⃣ VIENTO FUERTE
    if (mode === 3) {
      let wind = createVector(0.5, 0);
      plane.applyForce(wind);
    }

    // 4️⃣ LLUVIA
    if (mode === 4) {
      let rainForce = createVector(0, 0.15);
      plane.applyForce(rainForce);
    }

    plane.applyForce(lift);

    plane.update();
    plane.checkEdges();
    plane.show();
  }

  if (mode === 4) {
    updateRain();
  }
}

function mousePressed() {
  airplanes.push(new Airplane(mouseX, mouseY, random(1, 3)));
}

function drawEnvironment() {

  // 1️⃣ Estable
  if (mode === 1) {
    background(180, 220, 255);
  }

// 2️⃣ Nubes (fondo suave con noise)
if (mode === 2) {

  background(210, 210, 220);

  noStroke();

  let scale = 0.01;
  for (let x = 0; x < width; x += 10) {
    for (let y = 0; y < height; y += 10) {

      let n = noise(x * scale, y * scale, frameCount * 0.01);

      let c = map(n, 0, 1, 200, 255);
      fill(c, c, c, 150);
      rect(x, y, 10, 10);
    }
  }
}

// 3️⃣ Viento fuerte (líneas dinámicas)
if (mode === 3) {

  background(193,235,247);

  for (let w of windLines) {
    w.update();
    w.show();
  }
}

  // 4️⃣ Lluvia
  if (mode === 4) {
    background(100, 100, 150);
  }
}

class WindLine {
  constructor() {
    this.reset();
  }

  reset() {
    this.x = random(width);
    this.y = random(height);
    this.len = random(20, 120);
    this.speed = random(2, 8);
    this.thickness = random(1, 3);
  }

  update() {
    this.x += this.speed;

    if (this.x > width + this.len) {
      this.x = -this.len;
      this.y = random(height);
    }
  }

  show() {
    stroke(255);
    strokeWeight(this.thickness);
    line(this.x, this.y, this.x + this.len, this.y);
  }
}

function keyPressed() {
  if (key === '1') mode = 1;
  if (key === '2') mode = 2;
  if (key === '3') mode = 3;
  if (key === '4') mode = 4;
}

```

### Un enlace al proyecto en el editor de p5.js.
- Enlace: https://editor.p5js.org/ThomasHyCr/sketches/qDTYRA_Vt

### Selecciona capturas de pantalla representativas de tu pieza de arte generativa.
<img width="1086" height="705" alt="image" src="https://github.com/user-attachments/assets/b59caee7-6001-478f-8c16-9a8c42150b1c" />
<img width="1080" height="707" alt="image" src="https://github.com/user-attachments/assets/bb4e4cc3-0402-4283-bec5-7a08f1b07602" />
<img width="1071" height="701" alt="image" src="https://github.com/user-attachments/assets/b12594ab-1fc7-40d5-b98f-bf0941e8aa3e" />
<img width="1081" height="695" alt="image" src="https://github.com/user-attachments/assets/41c893f5-36a6-4c61-8277-396389b0d02a" />


## Bitácora de reflexión

### Explica detalladamente en tu bitácora ¿Qué es el marco de movimiento motion 101 y cómo se relacionan: fuerza, aceleración, velocidad y posición?
El marco de Motion 101, es un "sistema" de movimiento, basado en una versión simplificada de las formulas fisicas de movimiento, es decir, todo se basa en un cambio de posición y de velocidad, es decir velocidades, aceleraciones, posiciones, y fuerzas. Y sus relaciones, e interacciones entre si, de forma que primero se calculan todas las fuerzas y aceleraciones, y finalmente estos resultados se aplican a la velocidad, y posteriormente a la posición.

### Vas a analizar este video sobre el artista Alexander Calder. Selecciona una de sus obras y luego crea una obra generativa inspirada en la obra de Calder que seleccionaste y el marco de movimiento motion 101 con fuerzas que trabajamos en esta unidad.







