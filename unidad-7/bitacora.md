# Unidad 7
<img width="1779" height="877" alt="Mindscape_Ukinami_Yuzuha_Partial" src="https://github.com/user-attachments/assets/197d66c7-2b07-46eb-99b7-3c7e17efadf1" />


## Bitácora de proceso de aprendizaje
### Actividad 01:
- **Analiza 3 o 4 ejemplos de Ji Lee.**
- **Explica cómo la manipulación tipográfica refuerza el significado.**
En estos casos, esta manipulaión, le da vida al significado de estas palabras, ya que lo representan gráficamente.  
- **Propón 2 o 3 palabras propias y esboza cómo podrían representarse visualmente.**
Dragón, Nieve (Snow), Obliteración.   
- **Indica cuál de esas palabras te interesa más y por qué.**
Nieve (Snow), porque es un concepto que siempre me ha maravillado, y creo que tengo una buena idea para poder representarlo.

### Actividad 02:
- **Explica con tus palabras qué hace cada uno de esos conceptos:**
Engine: Base, o set de herramientas pre-hechas, se usa para crear "productos" más complejos.  
World: El "canvas", sobre el que se encontrará ensamblado todo.  
Bodies: Los objetos que interactuan en la simulación.  
Constraint: Limitadores, ya sea de posición, rotación, u otros parámetros.  
MouseConstraint: Limitador del mouse, podría ser de una zona en la que se contiene el movimiento del mouse.  
- **Replica al menos dos experimentos básicos integrando Matter.js con p5.js.**
- **Incluye código y capturas o enlaces.**
<img width="494" height="339" alt="image" src="https://github.com/user-attachments/assets/fa4f3f28-49bd-464e-a5a4-380ebde751d1" />

```js

// Importar módulos de Matter.js
let Engine = Matter.Engine;
let World = Matter.World;
let Bodies = Matter.Bodies;

let engine, world;
let ball;
let ground;

function setup() {
  createCanvas(600, 400);

  // Crear motor de física
  engine = Engine.create();
  world = engine.world;

  // Crear un círculo (pelota)
  ball = Bodies.circle(300, 50, 20, {
    restitution: 0.8 // rebote
  });

  // Crear suelo
  ground = Bodies.rectangle(300, 380, 600, 40, {
    isStatic: true
  });

  // Añadir al mundo
  World.add(world, [ball, ground]);
}

function draw() {
  background(220);

  // Actualizar física
  Engine.update(engine);

  // Dibujar pelota
  fill(100, 150, 255);
  ellipse(ball.position.x, ball.position.y, 40);

  // Dibujar suelo
  fill(100);
  rectMode(CENTER);
  rect(ground.position.x, ground.position.y, 600, 40);
}
```

<img width="486" height="327" alt="image" src="https://github.com/user-attachments/assets/b6942a05-03c3-4628-a1a0-0e85449639f3" />
```js

// Importar Matter.js
let Engine = Matter.Engine;
let World = Matter.World;
let Bodies = Matter.Bodies;
let Mouse = Matter.Mouse;
let MouseConstraint = Matter.MouseConstraint;

let engine, world;
let balls = [];
let ground;
let mConstraint;

function setup() {
  createCanvas(600, 400);

  engine = Engine.create();
  world = engine.world;

  // Suelo
  ground = Bodies.rectangle(300, 380, 600, 40, {
    isStatic: true
  });

  World.add(world, ground);

  // Mouse
  let canvasMouse = Mouse.create(canvas.elt);
  canvasMouse.pixelRatio = pixelDensity();

  mConstraint = MouseConstraint.create(engine, {
    mouse: canvasMouse
  });

  World.add(world, mConstraint);
}

function draw() {
  background(30);

  Engine.update(engine);

  // Dibujar pelotas
  fill(100, 200, 255);
  noStroke();
  for (let ball of balls) {
    ellipse(ball.position.x, ball.position.y, 40);
  }

  // Dibujar suelo
  fill(200);
  rectMode(CENTER);
  rect(ground.position.x, ground.position.y, 600, 40);
}

// Crear nuevas pelotas al hacer click
function mousePressed() {
  let ball = Bodies.circle(mouseX, mouseY, 20, {
    restitution: 0.7
  });

  balls.push(ball);
  World.add(world, ball);
}
```

- **Describe qué tipo de comportamiento físico te interesa explorar en tu palabra.**
Particulas cayendo y acoplandose.

### Actividad 03:
- **Realiza al menos dos experimentos simples de audio-reactividad.**
https://editor.p5js.org/ThomasHyCr/sketches/nPy1U0ebR
https://editor.p5js.org/ThomasHyCr/sketches/5a33dLRuk
- **Explica qué dato estás leyendo del audio.**
En ambos casos leo las frequencias y el nivel de "energia".
- **Explica qué comportamiento visual o físico activa ese dato.**
En el primero, activa las barras y el color para "ver cada frecuencia con su nivel". En el segundo crea una deformación en la figura de tipo ojo.
- **Describe qué tipo de respuesta sonora te serviría más para tu palabra y por qué.**
La exploración del color, ya que la cancion al ser muy tranquila daría unas variaciones muy tranquilas

### Actividad 04:
- **Muestra una prueba inicial.**  
<img width="713" height="475" alt="image" src="https://github.com/user-attachments/assets/9768832c-286d-44d0-9a7b-1c9ad12a122e" />
Aqui no tenia ni reactividad, ni sonidos en general  
- **Explica qué parte de la palabra construiste.**  
La caida de la nieve y la tranquilidad que produce  
- **Explica qué propiedad física manipulaste.**  
La caida de las particulas  
- **Explica qué aspecto del audio afecta qué comportamiento.**  
El audio afecta a los colores del fondo, los cuales toman las tonalidades de una aurora boreal  
- **Evalúa qué funcionó y qué no para el significado que quieres construir.**  
Al principio hubo que hacer muchos cambios, pero el iba bien encaminado, especialmente por la forma en que se forma la palabra.  
## Bitácora de aplicación   


- Palabra elegida.  
Snow
- Justificación conceptual.  
La nieve cae pacificamente, y forma la palabra, además se puede apartar la nieve con el mouse.
- Análisis de su significado visual y comportamental.  
la idea es representar un invierno o nieve pacificos, con la iluminacion de las auroras boreales de fondo
- Moodboard o referencias.  
<img width="259" height="194" alt="image" src="https://github.com/user-attachments/assets/a9fefe56-6da7-4a04-a2fc-3823f52c90b7" />
<img width="626" height="376" alt="image" src="https://github.com/user-attachments/assets/eef530dc-aaa6-48af-8bf5-5e264551c8ca" />
 
- Bocetos.  
<img width="479" height="356" alt="image" src="https://github.com/user-attachments/assets/2f76b811-b241-4eaa-9507-2875061b747d" />

- Mapa de decisiones.  
Nieve cae automaticamente
Al acercarse a cierta zona -> se acopla para formar palabra
Música -> Color fondo

- Mapa de interpretación.  
El mouse repele la nieve -> Apartar la nieve con la "mano"

- Explicación de la relación entre audio y comportamiento.  
El color de las auroras boreales no es constante, estas varian, e incluso pueden producir sonido, por lo tanto el sonido controla el color en este proyecto.

- Evidencia del uso de IA.  
<img width="955" height="603" alt="image" src="https://github.com/user-attachments/assets/c23498cb-565a-43cc-9ff8-8bc6cf55b9d4" />

- Código fuente.
```js
// Sketch p5.js adaptado a pantalla completa y escalado correcto

const BASE_W = 900;
const BASE_H = 560;

const LOG_W = BASE_W;
const LOG_H = BASE_H;
const SNOW_R = 3;
const GRID_STEP = 7;
const REPEL_R = 90;

let engine, world;
let flakes = [];
let settled = [];
let slotMap = new Map();
let letterMask;
let totalSlots = 0;
let spawnRate = 0;

let music;
let clickSounds = [];

// 🔊 audio reactivo
let amp;
let smoothLevel = 0;

// 🔊 sistema de audio
let clickPool = [];
let maxSimultaneousClicks = 8;
let clicksThisFrame = 0;

function preload() {
  music = loadSound("Secunda - Jeremy Soule.mp3");

  clickSounds[0] = loadSound("Clicks-001.wav");
  clickSounds[1] = loadSound("Clicks-002.wav");
  clickSounds[2] = loadSound("Clicks-003.wav");
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  pixelDensity(1);
  frameRate(60);

  engine = Matter.Engine.create({ gravity: { x: 0, y: 0 } });
  world = engine.world;

  buildLetterMask();

  userStartAudio();
  getAudioContext().resume();

  if (music && music.isLoaded()) {
    music.setLoop(true);
    music.setVolume(0.6);
    music.play();
  }

  // 🔊 amplitud
  amp = new p5.Amplitude();
  amp.setInput(music);

  for (let i = 0; i < maxSimultaneousClicks; i++) {
    let base = random(clickSounds);
    clickPool.push(base);
  }
}

// 🌌 colores aurora
function getAuroraColor(t) {
  let c1 = color(15, 30, 50);
  let c2 = color(30, 100, 90);
  let c3 = color(90, 40, 110);

  if (t < 0.5) {
    return lerpColor(c1, c2, t * 2);
  } else {
    return lerpColor(c2, c3, (t - 0.5) * 2);
  }
}

function playClick() {
  if (clicksThisFrame > 4) return;

  for (let s of clickPool) {
    if (s && !s.isPlaying()) {
      s.setVolume(0.25);
      s.rate(random(0.9, 1.1));
      s.play();
      clicksThisFrame++;
      return;
    }
  }
}

function buildLetterMask() {
  slotMap.clear();
  letterMask = null;
  totalSlots = 0;

  let pg = createGraphics(BASE_W, BASE_H);
  pg.pixelDensity(1);
  pg.background(0);
  pg.fill(255);
  pg.noStroke();
  pg.textAlign(CENTER, CENTER);
  pg.textSize(180);
  pg.textStyle(BOLD);
  pg.text("Snow", BASE_W / 2, BASE_H * 0.525);
  pg.loadPixels();

  letterMask = new Uint8Array(BASE_W * BASE_H);
  for (let i = 0; i < BASE_W * BASE_H; i++) {
    letterMask[i] = pg.pixels[i * 4] > 128 ? 1 : 0;
  }

  for (let x = GRID_STEP; x < BASE_W - GRID_STEP; x += GRID_STEP) {
    for (let y = GRID_STEP; y < BASE_H - GRID_STEP; y += GRID_STEP) {
      let ix = Math.round(x), iy = Math.round(y);
      if (ix < BASE_W && iy < BASE_H && letterMask[iy * BASE_W + ix]) {
        let gx = Math.round(x / GRID_STEP);
        let gy = Math.round(y / GRID_STEP);
        slotMap.set(`${gx},${gy}`, { x, y, filled: false });
      }
    }
  }

  totalSlots = slotMap.size;
}

function spawnFlake() {
  flakes.push({
    x: random(0, LOG_W),
    y: -SNOW_R,
    vx: random(-0.3, 0.3),
    vy: random(0.7, 1.4),
    phase: random(TWO_PI),
    drag: random(0.012, 0.022),
    life: 0
  });
}

function findSlot(px, py) {
  let gx = Math.round(px / GRID_STEP);
  let gy = Math.round(py / GRID_STEP);
  let best = null, bestD = GRID_STEP * 4;

  for (let dx = -3; dx <= 3; dx++) {
    for (let dy = -3; dy <= 3; dy++) {
      let s = slotMap.get(`${gx + dx},${gy + dy}`);
      if (s && !s.filled) {
        let d = dist(px, py, s.x, s.y);
        if (d < bestD) {
          bestD = d;
          best = s;
        }
      }
    }
  }
  return best;
}

function draw() {

  // 🔊 fondo reactivo (único cambio real)
  let level = amp.getLevel();
  smoothLevel = lerp(smoothLevel, level, 0.08);

  let timeShift = sin(frameCount * 0.01) * 0.1;
  let t = map(smoothLevel, 0, 0.3, 0, 1) + timeShift;
  t = constrain(t, 0, 1);

  let aurora = getAuroraColor(t);
  background(red(aurora), green(aurora), blue(aurora));

  clicksThisFrame = 0;

  let s = min(width / BASE_W, height / BASE_H);
  let tx = (width - BASE_W * s) / 2;
  let ty = (height - BASE_H * s) / 2;

  let mx = (mouseX - tx) / s;
  let my = (mouseY - ty) / s;

  if (mouseX < tx || mouseX > tx + BASE_W * s || mouseY < ty || mouseY > ty + BASE_H * s) {
    mx = -9999;
    my = -9999;
  }

  spawnRate = min(spawnRate + 0.0015, 1.0);
  let wordDone = settled.length >= totalSlots * 0.999;

  if (!wordDone && random() < spawnRate * 0.5 && flakes.length < 220) {
    spawnFlake();
  }

  // 🔁 repulsión (esto es lo que se rompía antes)
  let toUnsettle = [];
  for (let i = 0; i < settled.length; i++) {
    if (dist(settled[i].x, settled[i].y, mx, my) < REPEL_R * 0.85) {
      toUnsettle.push(i);
    }
  }

  for (let i = toUnsettle.length - 1; i >= 0; i--) {
    let sObj = settled[toUnsettle[i]];
    if (sObj.slot) sObj.slot.filled = false;

    let angle = atan2(sObj.y - my, sObj.x - mx);
    let d = dist(sObj.x, sObj.y, mx, my);
    let str = 1 - d / (REPEL_R * 0.85);
    let spd = 1.5 + str * 4;

    flakes.push({
      x: sObj.x,
      y: sObj.y,
      vx: cos(angle) * spd,
      vy: sin(angle) * spd,
      phase: random(TWO_PI),
      drag: 0.018,
      life: 0
    });

    settled.splice(toUnsettle[i], 1);
  }

  push();
  translate(tx, ty);
  scale(s);

  let toRemove = [];

  for (let i = 0; i < flakes.length; i++) {
    let f = flakes[i];

    f.life++;
    f.vy += 0.028;
    f.vx += sin(frameCount * 0.018 + f.phase) * 0.012;

    f.vx *= (1 - f.drag);
    f.vy *= (1 - f.drag * 0.4);

    f.vx = constrain(f.vx, -0.9, 0.9);

    f.x += f.vx;
    f.y += f.vy;

    let dx = f.x - mx, dy = f.y - my;
    let d = dist(f.x, f.y, mx, my);

    if (d < REPEL_R && d > 0.5) {
      let force = (1 - d / REPEL_R) * 0.8;
      f.vx += (dx / d) * force;
      f.vy += (dy / d) * force;
    }

    if (f.y > LOG_H + 40 || f.x < -60 || f.x > LOG_W + 60) {
      toRemove.push(i);
      continue;
    }

    let ix = round(f.x), iy = round(f.y);
    if (
      f.life > 20 &&
      ix >= 0 && ix < LOG_W &&
      iy >= 0 && iy < LOG_H &&
      letterMask[iy * LOG_W + ix]
    ) {
      let slot = findSlot(f.x, f.y);
      if (slot) {
        f.vx *= 0.5;
        f.vy *= 0.5;

        if (mag(f.vx, f.vy) < 1.5) {
          slot.filled = true;
          settled.push({ x: slot.x, y: slot.y, slot });

          playClick();

          toRemove.push(i);
          continue;
        }
      }
    }

    noStroke();
    fill(155, 200, 255, 16);
    circle(f.x, f.y, SNOW_R * 5.5);
    fill(255, 255, 255, 210);
    circle(f.x, f.y, SNOW_R * 2);
  }

  for (let i = toRemove.length - 1; i >= 0; i--) {
    flakes.splice(toRemove[i], 1);
  }

  for (let sObj of settled) {
    noStroke();
    fill(120, 185, 255, 28);
    circle(sObj.x, sObj.y, SNOW_R * 6);
    fill(205, 228, 255, 115);
    circle(sObj.x, sObj.y, SNOW_R * 3);
    fill(255);
    circle(sObj.x, sObj.y, SNOW_R * 1.9);
  }

  noFill();
  stroke(190, 225, 255, 8);
  strokeWeight(1);
  circle(mx, my, REPEL_R * 2);
  noStroke();

  pop();
}

function mousePressed() {
  fullscreen(!fullscreen());

  userStartAudio();
  let ac = getAudioContext();
  if (ac && ac.state !== 'running') ac.resume();

  resizeCanvas(windowWidth, windowHeight);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```
- Enlace al sketch.  
https://editor.p5js.org/ThomasHyCr/sketches/t48dHMMW5
- Capturas o registros de la pieza.  
<img width="1884" height="1065" alt="image" src="https://github.com/user-attachments/assets/c3a49665-adb0-4c9c-97dd-06baabb21cc9" />
<img width="1361" height="918" alt="image" src="https://github.com/user-attachments/assets/d6199586-7188-40cc-a43c-0e890076a46c" />

## Bitácora de reflexión
