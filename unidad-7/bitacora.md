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


## Bitácora de reflexión
