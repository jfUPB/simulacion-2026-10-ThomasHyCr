# Unidad 6

<img width="1000" height="607" alt="image" src="https://github.com/user-attachments/assets/fcf6244d-bb92-4a16-8403-81288a399ffa" />


## Bitácora de proceso de aprendizaje

### Actividad 1:
- **Selecciona dos imágenes o piezas de Tyler Hobbs que te llamen la atención.**  
- **Describe qué decisiones visuales reconoces en ellas: composición, densidad, dirección del movimiento, color, ritmo, repetición y variación.**  
- **Explica por qué esas decisiones te parecen potentes.**  
- **Escribe una hipótesis: ¿Qué tipo de reglas o sistema crees que podrían estar detrás de esa pieza?**  



### Actividad 2: 
- **Explica con tus propias palabras qué es un agente autónomo.**  
- **Explica qué es una steering force.**  
- **Compara una steering force con una fuerza externa como la gravedad.**  
- **Describe por qué estas ideas son útiles para diseñar comportamiento visual y no solo para simular movimiento.**  


### Actividad 3: 
- **¿Cómo está construido el campo de flujo?**  
- **¿Qué representa cada celda o vector del campo?**  
- **¿Cómo usa un agente su posición para consultar el campo?**  
- **¿Cómo se convierte el vector consultado en una decisión de movimiento?**  
- **Identifica parámetros importantes del sistema, por ejemplo: resolución, maxspeed, maxforce, cantidad de agentes.**  
- **Realiza al menos una modificación y analiza el efecto visual que produce.**  
Además, responde:  

- **¿Qué tipo de movimiento produce este algoritmo?**  
- **¿Qué sensaciones visuales te sugiere?**  
- **¿En qué tipo de pieza musical imaginas que podría funcionar bien?**  

### Actividad 4:
- **Explica con tus palabras las tres reglas básicas: separación, alineación, cohesión.**  
- **Identifica qué parámetros controlan estas reglas.**  
- **Modifica uno o más pesos del sistema y describe el efecto visual y colectivo.**  
- **Describe el comportamiento emergente observado: compacto, disperso, estable, nervioso, caótico, fluido.**  
Además, responde:  

- **¿Qué atmósfera visual produce el flocking?**  
- **¿En qué tipo de relación con una canción podría funcionar mejor este algoritmo?**  


### Actividad 5:  
**Completa una comparación entre flow fields y flocking a partir de los siguientes aspectos:**  
- **Tipo de movimiento que producen**  
- **Nivel de control visual**  
- **Nivel de emergencia**  
- **Tipo de atmósfera o sensación**  
- **Relación posible con una pieza musical**  
- **Ventajas y limitaciones de cada uno**  
Cierra la actividad respondiendo:  

- **Si quisieras diseñar visuales para una canción contemplativa, agresiva, melancólica o eufórica, ¿Cuál algoritmo usarías en cada caso y por qué?**  

## Bitácora de aplicación 

### Actividad 6:
- **Concepto visual.**  
Quiero que en el proyecto, logre visualizar la canción de forma que se sienta la emoción desbordante que hay en esta, para expresar esto visualmente, quiero hacer que las frecuencias, y la intensidad de estas controlen varios parametros de lo visual, por ejemplo que el nivel, la energia, y la frequencia dicten el color de los agentes que se van a estar moviendo por el canvas. Además, las frecuencias en sí, son lo que van a dictar, hasta cierto punto, como se forma el flow field, y la energia, la velocidad máxima a la que se pueden mover.


- **Relación entre la visual y la canción.**  
La canción trata sobre la desesperación, y lo abrumador que resulta ser conciente de los sucesos, y sobre el mundo en el que nos encontramos, y como todo esto, genera ansiedad porque la perdición aparenta ser inminente, generando así un "Calor Anormal" (nombre traducido de la canción, "Netsu Ijou"). Teniendo todo esto en cuenta, quise representar como la ciudad, sin importar hacia dónde se mire, está toda en llamas (representada por las particulas de ascuas). y además hay cambios en los colores en base a la música, y también controlados por mí.

- **Moodboard o referencias.**
<img width="740" height="740" alt="image" src="https://github.com/user-attachments/assets/200f6ef1-e4c9-4f11-9c0a-358a811ff635" />
<img width="1322" height="730" alt="image" src="https://github.com/user-attachments/assets/c65155d5-1adb-467e-bc27-f46f256cdf04" />
<img width="850" height="510" alt="image" src="https://github.com/user-attachments/assets/d8b24212-dc89-4928-ab8b-35d209fc9c77" />
<img width="498" height="280" alt="image" src="https://github.com/user-attachments/assets/0a7e7f20-de0d-45ef-8318-ef77eb90065a" />



- **Dos o más bocetos.**  
<img width="803" height="600" alt="image" src="https://github.com/user-attachments/assets/7489e072-2ca4-4b67-ba69-7274a86d77bc" />
<img width="922" height="633" alt="image" src="https://github.com/user-attachments/assets/46006706-873a-496a-87de-bcae5be36d41" />



- **Mapa de decisiones.**  


- **Mapa de interpretación.**  



- **Justificación del algoritmo elegido.**  
Quise representar como una ciudad envuelta en llamas, y con muchas ascuas moviendose por el aire, y quise además que el movimiento fuese controlado por la musica.

- **Explicación de la relación audio-visual.**  
Muchas cosas son manejadas por la musica, como lo es la velocidad, el flowfield, los flashes, etc. Y hay otros aspectos como color, y blackflashes que controlo. Esto, mucho lo baso en el "video" músical, que aunque es MUY sencillo, me guió bastante, para todo lo visual.


- **Evidencia del uso de IA.**  
<img width="1470" height="551" alt="image" src="https://github.com/user-attachments/assets/09b5fc79-c13a-4625-b7d0-0bdf4797dcc8" />
<img width="921" height="473" alt="image" src="https://github.com/user-attachments/assets/758632c7-6fe1-4325-b071-de4ed291e90c" />
<img width="922" height="545" alt="image" src="https://github.com/user-attachments/assets/c9089c07-54ba-44e5-a158-2d9dd11b6c28" />



- **Código fuente.**  
Building.js
```js
let buildings = [];
const BUILDING_COLOR = [50, 46, 68];

class Building {
  constructor(x, w, h) {
    this.x = x;
    this.w = w;
    this.h = h;
  }

  update(speed) {
    this.x -= speed;
    if (this.x + this.w < 0) {
      this.x = width;
      this.h = random(height * 0.2, height * 0.85);
      this.w = random(80, 220);
    }
  }

  show(level, modeBlend) {
    let pulse = level * 30;
    let r = constrain(lerp(BUILDING_COLOR[0], 80, modeBlend) + pulse, 0, 255);
    let g = constrain(lerp(BUILDING_COLOR[1], 0,  modeBlend) + pulse * 0.5, 0, 255);
    let b = constrain(lerp(BUILDING_COLOR[2], 0,  modeBlend) + pulse, 0, 255);
    noStroke();
    fill(r, g, b);
    rect(this.x, height - this.h, this.w, this.h);
  }
}
```

flowfield.js
```js
class FlowField {
  constructor(r) {
    this.resolution = r;
    this.cols = floor(width / this.resolution);
    this.rows = floor(height / this.resolution);
    this.field = new Array(this.cols);
    for (let i = 0; i < this.cols; i++) {
      this.field[i] = new Array(this.rows);
      for (let j = 0; j < this.rows; j++) {
        this.field[i][j] = p5.Vector.fromAngle(0);
      }
    }
  }

  update(spectrum, energy) {
    let xoff = 0;
    for (let i = 0; i < this.cols; i++) {
      let yoff = 0;
      for (let j = 0; j < this.rows; j++) {
        let index = (i + j) % spectrum.length;
        let angle = map(spectrum[index], 0, 255, 0, TWO_PI);
        angle += noise(xoff, yoff) * energy * 5;
        // Mutar el vector existente en lugar de crear uno nuevo
        this.field[i][j].x = cos(angle);
        this.field[i][j].y = sin(angle);
        yoff += 0.1;
      }
      xoff += 0.1;
    }
  }

  show(modeBlend = 0) {
    // Colores fuera del loop
    let normalStroke = color(255, 40);
    let redStroke    = color(255, 0, 0, 40);
    let w = width / this.cols;
    let h = height / this.rows;

    for (let i = 0; i < this.cols; i++) {
      for (let j = 0; j < this.rows; j++) {
        let v = this.field[i][j].copy();
        v.setMag(w * 0.5);
        let x = i * w + w / 2;
        let y = j * h + h / 2;
        stroke(lerpColor(normalStroke, redStroke, modeBlend));
        strokeWeight(1);
        line(x, y, x + v.x, y + v.y);
      }
    }
  }

  lookup(position) {
    let column = constrain(floor(position.x / this.resolution), 0, this.cols - 1);
    let row    = constrain(floor(position.y / this.resolution), 0, this.rows - 1);
    return this.field[column][row].copy();
  }
}
```

vehicle.js
```js
class Vehicle {
  constructor(x, y, ms, mf) {
    this.position     = createVector(x, y);
    this.acceleration = createVector(0, 0);
    this.velocity     = createVector(0, 0);
    this.r            = 4;
    this.baseSpeed    = ms;
    this.maxspeed     = ms;
    this.maxforce     = mf;
  }

  run(flow, spectrum, level) {
    this.follow(flow);
    this.update(level);
    this.borders();
    this.show(spectrum, level);
  }

  follow(flow) {
    let desired = flow.lookup(this.position);
    desired.mult(this.maxspeed);
    let steer = p5.Vector.sub(desired, this.velocity);
    steer.limit(this.maxforce);
    this.applyForce(steer);
  }

  applyForce(force) {
    this.acceleration.add(force);
  }

  update(level) {
    this.maxspeed = this.baseSpeed + level * 20;
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.maxspeed);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  borders() {
    if (
      this.position.x < -this.r ||
      this.position.x > width + this.r ||
      this.position.y < -this.r ||
      this.position.y > height + this.r
    ) {
      this.position.x = random(width);
      this.position.y = random(height);
    }
  }

  show(spectrum, level) {
    let theta  = this.velocity.heading();
    let index  = constrain(floor(map(this.position.x, 0, width, 0, spectrum.length - 1)), 0, spectrum.length - 1);
    let freq   = spectrum[index];
    let energy = level;

    // frameSin precomputado en sketch.js una vez por frame
    let pulse = frameSin * 30;

    let nr, ng, nb;
    if (energy > 0.15) {
      nr = 200 + freq * 0.5;
      ng = freq;
      nb = 0;
    } else {
      nr = 70;
      ng = freq * 0.3;
      nb = 100 + freq * 0.3;
    }

    // modeBlend siempre existe, sin typeof
    let fr = constrain(lerp(nr, 80, modeBlend) + pulse, 0, 255);
    let fg = constrain(lerp(ng, 0, modeBlend) + pulse * (1 - modeBlend), 0, 255);
    let fb = constrain(lerp(nb, 0, modeBlend), 0, 255);

    push();
    translate(this.position.x, this.position.y);
    rotate(theta);

    // Halo solo si glow activo y hay suficiente energía
    if (glowEnabled && energy > 0.1) {
      noStroke();
      fill(fr, fg, fb, 40);
      ellipse(0, 0, this.r * 6 + energy * 40, this.r * 6 + energy * 40);
    }

    fill(fr, fg, fb, 200);
    stroke(0);
    strokeWeight(1);
    beginShape();
    vertex(this.r * 2, 0);
    vertex(-this.r * 2, -this.r);
    vertex(-this.r * 2, this.r);
    endShape(CLOSE);
    pop();
  }
}
```


sketch.js
```js
let music;
let amp, fft;
let radius = 10;
let debug = false;
let started = false;
let flowfield;
let vehicles = [];

let modeBlend = 1;
let modeBlendTarget = 0;
let modeBlendStartTime = 0;
let modeBlendStartValue = 1;
let modeBlendDuration = 50000;
let blackFlash = 0;

let chromaTimer;
let chromaFrames = 0;
const CHROMA_DURATION = 45;
let chromaBuffer = null;

let glowEnabled = false;

// Colores del radial precalculados (fuera de loops)
let cold1, cold2, hot1, hot2, redTarget;

// Sin precomputado por frame
let frameSin = 0;

function preload() {
  music = loadSound("miyyuu.m4a");
}

function setup() {
  pixelDensity(1);
  createCanvas(windowWidth, windowHeight);

  // Inicializar colores una sola vez
  cold1     = color(0, 80, 160);
  cold2     = color(0, 180, 120);
  hot1      = color(200, 30, 0);
  hot2      = color(255, 220, 0);
  redTarget = color(50, 0, 0);

  let baseArea    = 900 * 900;
  let currentArea = windowWidth * windowHeight;
  let ratio       = currentArea / baseArea;

  let vehicleCount = floor(200 * min(ratio, 1.5));
  let ffResolution = ratio > 1.5 ? 30 : 20;

  flowfield = new FlowField(ffResolution);
  vehicles  = [];
  for (let i = 0; i < vehicleCount; i++) {
    vehicles.push(new Vehicle(random(width), random(height), random(2, 5), random(0.1, 0.5)));
  }

  buildings = [];
  let bx = 0;
  while (bx < width + 300) {
    let bw = random(80, 220);
    let bh = random(height * 0.2, height * 0.85);
    buildings.push(new Building(bx, bw, bh));
    bx += bw;
  }

  angleMode(RADIANS);
  amp = new p5.Amplitude();
  fft = new p5.FFT(0.88, 128);

  chromaTimer  = floor(random(600, 900));
  chromaBuffer = createGraphics(floor(width * 0.5), floor(height * 0.5));
}

function draw() {
  if (!started) {
    background(0);
    fill(255);
    noStroke();
    textAlign(CENTER, CENTER);
    textSize(28);
    text("Click para comenzar", width / 2, height / 2);
    return;
  }

  // Transición de modeBlend
  if (modeBlend !== modeBlendTarget) {
    let elapsed = millis() - modeBlendStartTime;
    let t = modeBlendDuration > 0 ? constrain(elapsed / modeBlendDuration, 0, 1) : 1;
    modeBlend = lerp(modeBlendStartValue, modeBlendTarget, t);
    if (t >= 1) modeBlend = modeBlendTarget;
  }

  // Sin precomputado una vez por frame
  frameSin = sin(frameCount * 0.2);

  let spectrum = fft.analyze();
  let level    = amp.getLevel();
  let beat     = level > 0.35;

  let bgAlpha = beat ? 180 : constrain(map(level, 0, 0.3, 220, 120), 120, 255);
  background(0, bgAlpha);

  // Edificios
  let buildingSpeed = 1.2 + level * 15;
  for (let b of buildings) {
    b.update(buildingSpeed);
    b.show(level, modeBlend);
  }

  // Flowfield cada 2 frames
  if (frameCount % 2 === 0) {
    flowfield.update(spectrum, beat ? 1 : level);
  }
  if (debug) flowfield.show(modeBlend);

  // Vehículos
  for (let v of vehicles) {
    v.run(flowfield, spectrum, level);
  }

  // Radial
  push();
  translate(width / 2, height / 2);

  if (glowEnabled) {
    push();
    blendMode(ADD);
    for (let i = 20; i < spectrum.length - 45; i++) {
      let freq   = spectrum[i];
      let angle  = map(i, 20, spectrum.length - 45, 0, TWO_PI);
      let length = map(freq, 0, 256, 0, 300);

      let x1 = cos(angle) * radius;
      let y1 = sin(angle) * radius;
      let x2 = cos(angle) * (radius + length);
      let y2 = sin(angle) * (radius + length);

      let energy   = constrain(level * 5, 0, 1);
      let flicker  = sin(frameCount * 0.1 + i * 0.2) * 0.15;
      energy       = constrain(energy + flicker, 0, 1);

      let freqNorm = map(length, 0, 300, 0, 1);
      freqNorm    += sin(frameCount * 0.02 + i) * 0.05;
      freqNorm     = constrain(freqNorm, 0, 1);

      let c         = energy > 0.3 ? lerpColor(hot1, hot2, freqNorm) : lerpColor(cold1, cold2, freqNorm);
      let glowColor = lerpColor(c, redTarget, modeBlend);

      stroke(red(glowColor), green(glowColor), blue(glowColor), 40);
      strokeWeight(6 + level * 6);
      line(x1, y1, x2, y2);
    }
    pop();
  }

  // Pase normal del radial
  for (let i = 20; i < spectrum.length - 45; i++) {
    let freq   = spectrum[i];
    let angle  = map(i, 20, spectrum.length - 45, 0, TWO_PI);
    let length = map(freq, 0, 256, 0, 300);

    let x1 = cos(angle) * radius;
    let y1 = sin(angle) * radius;
    let x2 = cos(angle) * (radius + length);
    let y2 = sin(angle) * (radius + length);

    let energy  = constrain(level * 5, 0, 1);
    let flicker = sin(frameCount * 0.1 + i * 0.2) * 0.15;
    energy      = constrain(energy + flicker, 0, 1);

    let freqNorm = map(length, 0, 300, 0, 1);
    freqNorm    += sin(frameCount * 0.02 + i) * 0.05;
    freqNorm     = constrain(freqNorm, 0, 1);

    let c          = energy > 0.3 ? lerpColor(hot1, hot2, freqNorm) : lerpColor(cold1, cold2, freqNorm);
    let finalColor = lerpColor(c, redTarget, modeBlend);
    stroke(finalColor);
    strokeWeight(2 + level * 3);
    line(x1, y1, x2, y2);
  }

  pop();

  // Chromatic aberration
  if (chromaFrames > 0) {
    if (frameCount % 2 === 0) {
      let snap = get();
      chromaBuffer.clear();
      chromaBuffer.image(snap, 0, 0, chromaBuffer.width, chromaBuffer.height);
    }

    let progress = chromaFrames / CHROMA_DURATION;
    let offset   = floor(progress * 12);
    let jitter   = floor(random(-3, 3) * progress);

    background(0);
    blendMode(ADD);

    tint(255, 0, 0);
    image(chromaBuffer, offset + jitter, jitter, width, height);
    tint(0, 255, 0);
    image(chromaBuffer, 0, 0, width, height);
    tint(0, 0, 255);
    image(chromaBuffer, -offset + jitter, -jitter, width, height);

    noTint();
    blendMode(BLEND);
    chromaFrames--;
  } else {
    chromaTimer--;
    if (chromaTimer <= 0) {
      chromaFrames = CHROMA_DURATION;
      chromaTimer  = floor(random(600, 900));
    }
  }

  if (blackFlash > 0) {
    fill(0, 255);
    noStroke();
    rect(0, 0, width, height);
    blackFlash--;
  }
}

function keyPressed() {
  if (key === "1") {
    modeBlend          = 1.0;
    modeBlendTarget    = 0;
    modeBlendStartValue = modeBlend;
    modeBlendStartTime = millis();
    modeBlendDuration  = 50000;
  }
  if (key === "0") {
    modeBlend          = 0;
    modeBlendTarget    = 0;
    modeBlendStartValue = modeBlend;
    modeBlendStartTime = millis();
    blackFlash         = 30;
  }
  if (key === "2") {
    modeBlendTarget    = 1.0;
    modeBlendStartValue = modeBlend;
    modeBlendStartTime = millis();
    modeBlendDuration  = 20000;
  }
  if (key === "3") {
    glowEnabled = !glowEnabled;
  }
}

function mousePressed() {
  if (!started) {
    started = true;
    fullscreen(true);
    music.play();
    music.setVolume(1.0);
  }
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);

  let baseArea    = 900 * 900;
  let currentArea = windowWidth * windowHeight;
  let ratio       = currentArea / baseArea;

  chromaBuffer = createGraphics(floor(windowWidth * 0.5), floor(windowHeight * 0.5));

  let ffResolution = ratio > 1.5 ? 30 : 20;
  flowfield = new FlowField(ffResolution);

  buildings = [];
  let bx = 0;
  while (bx < width + 300) {
    let bw = random(80, 220);
    let bh = random(height * 0.2, height * 0.85);
    buildings.push(new Building(bx, bw, bh));
    bx += bw;
  }

  let vehicleCount = floor(200 * min(ratio, 1.5));
  vehicles = [];
  for (let i = 0; i < vehicleCount; i++) {
    vehicles.push(new Vehicle(random(width), random(height), random(2, 5), random(0.1, 0.5)));
  }
}
```


- **Enlace al sketch.**

https://editor.p5js.org/ThomasHyCr/sketches/mWE_jhrxb

- **Capturas o registros de momentos importantes de la pieza.**  


## Bitácora de reflexión
