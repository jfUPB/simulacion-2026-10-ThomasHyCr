# Unidad 5
<img width="1000" height="628" alt="image" src="https://github.com/user-attachments/assets/a45b41ec-95cf-45c8-9d98-139deab89c64" />

## Bitácora de proceso de aprendizaje
### Actividad 01

#### Capa de comportamiento:

- **¿Qué propiedades tiene cada partícula? Clasifícalas: ¿Cuáles definen su estado físico? ¿Cuáles su estado vital?**  
Aparte de las propiedades del motion 101, y las de la apariencia, estas particulas cuentan una propiedad que es el tiempo de vida, este es como un contador, que va reduciendose con el tiempo.

- **¿Qué condición determina que una partícula “muere”? ¿Es una muerte instantánea o gradual?**  
Un contador que se va reduciendo con el tiempo, visualmente se ve como gradual, debido a que la opacidad de la particula se ve dictada por su tiempo restante de vida.

- **¿Cómo se actualiza la partícula en cada frame? Identifica el patrón motion 101 dentro de la partícula.**  
El componente de la velocidad, y la posición se calculan normalmente, además tiene el mañadido del tiempo de vida, y la aceleración se reinicia luego de estos calculos.

  
#### Capa de estructura:

- **¿Quién crea las partículas? ¿En qué momento?** 
El script "particles", en el draw se crean, cada vez que se hace push de una nueva particula.

- **¿Quién decide cuándo eliminar una partícula del array?**  
El tiempo de vida, el cual en el draw se está chequeando constantemente.

- **¿Por qué se recorre el array en orden inverso para eliminar? ¿Qué pasaría si no se hiciera así?**  
Para evitar fallos, y fugas de memoria, debido al funcionamiento del splice. Porque este luego de eliminar un elemento del array "jala" a los siguientes elementos, lo que causa que el que sería el siguiente elemento a checkear, sea saltado.

- **Si no eliminaras nunca las partículas, ¿Qué pasaría con la memoria y el rendimiento? Haz el experimento: comenta la línea que elimina y observa el frame rate.**  
La particulas permanecerían vivas, y se acumularian, lo que destruiria el rendimiento de la aplicación

  
#### Capa de visualización:

- **¿Qué elementos visuales usa para representar una partícula?**
- **¿Cómo se conecta el “tiempo de vida” con la apariencia visual?**
- **Si quisieras cambiar la representación visual (por ejemplo, usar líneas en vez de círculos), ¿Qué cambiarías y qué NO cambiarías?**

### Actividad 02

#### Comparación con Example 4.2:

- **¿Qué responsabilidades que antes estaban en draw() ahora están dentro de la clase Emitter?**  
El checkeo constante del tiempo de vida de las particulas

- **¿Cuál es la ventaja de encapsular la lógica de emisión en una clase separada?**  
Que permite una mejor organización, comprensión, y adición de más emisores.

- **En este ejemplo hay un array de emitters. ¿Quién crea los emitters? ¿Quién crea las partículas dentro de cada emitter?**  
Cada vez que se da click se hace push de un nuevo emiter, en el emitter, el "addParticle", pushea nuevas particulas, al script particles.

- **Dibuja un diagrama que muestre la jerarquía: sketch → [emitters] → [partículas]. ¿Cuántos niveles de “colección” hay?**  
<img width="712" height="467" alt="image" src="https://github.com/user-attachments/assets/04bec3d0-678b-45d2-ad95-7dcb0b604ba7" />



### Actividad 03

- **¿Qué tienen en común las subclases de partículas? ¿Qué tienen de diferente?**  
En común tienen todos los comportamientos y caracteristicas que no hayan sido sobre-escritos. De diferente, todo lo sobre-escrito.

- **¿Por qué es importante que el Emitter no necesite saber qué tipo específico de partícula está gestionando? Explica esto con tus propias palabras.**  
Porque esto favorece el añadir nuevos tipos de particulas, sin necesidad de hacerle modificaciones al Emitter, Ergo el principio Open & Close de POO.

 - **Si mañana quisieras agregar un tercer tipo de partícula, ¿Qué tendrías que crear y qué NO tendrías que modificar?**  
Idealmente (no para eficiencia computacional, pero si para eficiencia colaborativa), crear un nuevo tipo de particula, y pasarsela al emitter, de forma que este no tenga que llamarla directamente, sino, simplemente recibir la instancia.
 
 - **Compara con Example 4.2: ¿Cambió la lógica del Emitter? ¿Cambió la lógica de muerte? ¿Qué capa del sistema se modificó y cuáles permanecieron intactas?**  
La lógica del emitter, solo se le añadió el llamado a crear la nueva particula. La lógica de muerte continúa igual, y simplemente se añadió un nuevo tipo de particula que hereda de particle, y tiene un override en el show().

#### Transferencia conceptual:

- **Describe este ejemplo usando palabras que NO mencionen p5.js, JavaScript, ni ninguna herramienta específica. Usa solo términos como: entidad, estado, colección, emisor, ciclo de vida, fuerza.**  
Este ejemplo permite crear emisores de entidades, las cuales comienzan con una fuerza inicial, y se ven sujetas a la gravedad. además cuentan con un tiempo de vida, y lentamente se desvanecen según este avanza.


## Bitácora de aplicación 
### Concepto
- **Concepto: 2-3 frases sobre qué ciclo de vida representarás y qué emoción o idea quieres comunicar.**
Quiero hacer un cerezo con flores, y que al hacerle click a las flores, estas se desprendan del arbol, y lentamente caigan al suelo, cambiando de estado lentamente, hasta volverse polvo. La belleza de lo efimero.

- **Bocetos: al menos 2 bocetos (pueden ser a mano) que muestren cómo imaginas la pieza antes de programarla.**  
<img width="1236" height="692" alt="image" src="https://github.com/user-attachments/assets/7cbb82b6-ab83-4ee0-aae0-9b18d167ce0a" />
<img width="578" height="360" alt="image" src="https://github.com/user-attachments/assets/c9bb8615-14b5-4c64-8c0c-45c2282f2116" />


- **Mapa de decisiones: para cada elemento del sistema, explica la decisión de diseño: ¿Por qué esa emisión, esas fuerzas, esa condición de muerte, esa visualización, qué significa la interacción del usuario dentro del concepto?**  
**Elementos:**  
**Viento suave** - Para de esta forma, tranquilamente ver como las flores atraviezan su ciclo de vida.  
**Condición de muerte** - Tiempo, hecho aasí para representar que al arrancar la flor, esta comienza su proceso de "muerte".  
**Petalos** - Al momento de arrancarlo con click, estos caen lentamente y comienzan a degradarse.  
**Estados** - Flor, Petalo, Polvo...  

La interacción del usario representa el arrancar la flor, del arbol, lo cual inicia su proceso de degradación.

- **Implementación: enlace al código en el editor de p5.js + código fuente en la bitácora.**

[Enlace](https://editor.p5js.org/ThomasHyCr/sketches/vmX1aGI9o)
  
``` js
let flowers = [];     // flores en la rama
let particles = [];   // sistema de partículas
let treeLayer;        // buffer del árbol

function setup() {
  createCanvas(800, 800);

  // 🌿 buffer del árbol
  treeLayer = createGraphics(800, 800);
  treeLayer.background(245, 240, 230);

  let startX = -50;
  let startY = height * 0.7;

  // dibujar árbol UNA sola vez en el buffer
  growBranch(startX, startY, 250, -PI / 6, 25, 0, treeLayer);
}

function draw() {
  background(245, 240, 230);

  // 🌿 dibujar árbol persistente
  image(treeLayer, 0, 0);

  // 🌸 flores quietas
  for (let f of flowers) {
    f.draw();
  }

  // 🌬️ partículas
  for (let i = particles.length - 1; i >= 0; i--) {
    let p = particles[i];

    p.update();
    p.display();

    // 🌸 flor → pétalos
    if (p instanceof FallingFlower && p.timer > 120) {
      p.explode();
      particles.splice(i, 1);
    } 
    // 🌸 pétalos → polvo
    else if (p instanceof Petal && p.life < 100) {
      p.explode();
      particles.splice(i, 1);
    } 
    // 🌫️ eliminar
    else if (p.isDead()) {
      particles.splice(i, 1);
    }
  }
}

// 🖱️ interacción: desprender flor
function mousePressed() {
  for (let i = flowers.length - 1; i >= 0; i--) {
    let f = flowers[i];
    let d = dist(mouseX, mouseY, f.x, f.y);

    if (d < 20) {
      particles.push(new FallingFlower(f.x, f.y, f.petalData));
      flowers.splice(i, 1);
    }
  }
}

// 🌿 ramas (dibujadas en buffer)
function growBranch(x, y, len, angle, thickness, depth, g) {
  if (len < 10 || thickness < 1) return;

  let steps = int(len / 2);
  let px = x;
  let py = y;

  for (let i = 0; i < steps; i++) {
    let t = i / steps;

    let a = angle + map(noise(i * 0.1 + depth), 0, 1, -0.2, 0.2) + random(-0.05, 0.05);

    let nx = px + cos(a) * 3;
    let ny = py + sin(a) * 3;

    g.stroke(60, 40, 20, 150);
    g.strokeWeight(thickness * (1 - t) * random(0.9, 1.1));
    g.line(px, py, nx, ny);

    // ramificación
    if (i > steps * 0.3 && i < steps * 0.8 && random() < 0.08) {
      let subAngle = angle + random(-PI/3, PI/3);
      growBranch(px, py, len * random(0.3, 0.5), subAngle, thickness * 0.5, depth + 1, g);
    }

    px = nx;
    py = ny;
  }

  // flores en puntas
  if (len < 80 && random() < 0.7) {
    flowers.push(new Flower(px, py));
  }

  growBranch(px, py, len * random(0.6, 0.8), angle + random(-0.1, 0.1), thickness * 0.7, depth + 1, g);
}

// 🌸 flor estática
class Flower {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.petals = int(random(4, 6));
    this.baseSize = random(12, 18);
    this.petalData = [];

    for (let i = 0; i < this.petals; i++) {
      let angle = TWO_PI / this.petals * i + random(-0.3, 0.3);
      let px = this.x + cos(angle) * this.baseSize * random(0.8, 1.2);
      let py = this.y + sin(angle) * this.baseSize * random(0.8, 1.2);
      this.petalData.push({x: px, y: py});
    }
  }

  draw() {
    noStroke(); // 🔥 quitar bordes

    for (let p of this.petalData) {
      fill(255, 180, 200, 120);
      ellipse(p.x, p.y, 8);
    }

    fill(180, 80, 100);
    ellipse(this.x, this.y, 4);
  }
}

// ================= PARTICLES =================

// 🧩 base
class Particle {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.vel = createVector(random(-0.5, 0.5), random(-0.5, 0));
    this.acc = createVector(0, 0);
    this.life = 500;
  }

  applyForce(f) {
    this.acc.add(f);
  }

  update() {
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    this.acc.mult(0);
    this.life -= 2;
  }

  isDead() {
    return this.life <= 0;
  }
}

// 🌺 flor cayendo
class FallingFlower extends Particle {
  constructor(x, y, petalData) {
    super(x, y);
    this.petalData = petalData;
    this.timer = 0;
  }

  update() {
    super.update();
    this.timer++;

    this.applyForce(createVector(0, 0.02));

    let wind = map(noise(frameCount * 0.01), 0, 1, -0.01, 0.01);
    this.applyForce(createVector(wind, 0));
  }

  display() {
    push();
    translate(this.pos.x, this.pos.y);

    for (let p of this.petalData) {
      fill(255, 180, 200, this.life);
      ellipse(p.x - this.pos.x, p.y - this.pos.y, 4);
    }

    pop();
  }

  explode() {
    for (let p of this.petalData) {
      particles.push(new Petal(p.x, p.y));
    }
  }
}

// 🌸 pétalos
class Petal extends Particle {
  constructor(x, y) {
    super(x, y);
    this.vel = createVector(random(-1, 1), random(-1, 0));
  }

  update() {
    super.update();

    this.applyForce(createVector(0, 0.015));

    let wind = map(noise(frameCount * 0.02), 0, 1, -0.02, 0.02);
    this.applyForce(createVector(wind, 0));
  }

  display() {
    fill(255, 170, 200, this.life);
    ellipse(this.pos.x, this.pos.y, 3);
  }

  explode() {
    for (let i = 0; i < 3; i++) {
      particles.push(new Dust(this.pos.x, this.pos.y));
    }
  }
}

// 🌫️ polvo
class Dust extends Particle {
  constructor(x, y) {
    super(x, y);
    this.vel = p5.Vector.random2D().mult(0.5);
  }

  update() {
    super.update();
    this.applyForce(createVector(0, 0.005));
  }

  display() {
    fill(200, 200, 200, this.life);
    ellipse(this.pos.x, this.pos.y, 2);
  }
}
```

- **Capturas: al menos 3 capturas de momentos diferentes del ciclo de vida.**
<img width="635" height="636" alt="image" src="https://github.com/user-attachments/assets/1d4dc9fc-433b-47a8-a8ae-04776dba6b59" />
<img width="236" height="184" alt="image" src="https://github.com/user-attachments/assets/118411eb-041a-4c35-b0e1-907acd36697c" />
<img width="328" height="215" alt="image" src="https://github.com/user-attachments/assets/c2f135bf-5f96-4215-b6c5-4c4744c2a2be" />





## Bitácora de reflexión
