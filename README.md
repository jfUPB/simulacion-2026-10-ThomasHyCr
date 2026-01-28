# Bitácoras de aprendizaje 2026-10

# Unidad #1
<img width="1000" height="419" alt="image" src="https://github.com/user-attachments/assets/23bf9024-9b54-4ed6-991b-e0c4283bf231" />


## Actividad #1: La aleatoriedad en el arte generativo
Se observaron 4 videos, de distintos artistas, y se realizó una discusión de como la aleatoriedad juega un papel importante en el arte generativo.
La aleatoriedad es muy importante para el arte generativo ya que permite que cada obra, cada vez que se "ejecuta", sea distinta, y única.

## Actividad #2: Caminatas aleatorias
#### Modifica el código del ejemplo Example 0.1: A Traditional Random Walk.
``` js
  step() {
    const choice = floor(random(10));
    if (choice <= 2 ) {
      this.x++;
    } else if (choice <= 4) {
      this.x--;
    } else if (choice <= 6) {
      this.y++;
    } else {
      this.y--;
    }
  }
```
<img width="201" height="155" alt="image" src="https://github.com/user-attachments/assets/51b00547-f54f-4efb-b7e1-03b8c9857e6b" />

#### Qué espero que ocurra antes de ejecutar el código?:
Que se favorezca la dirección "y--", ya que esta cuenta con más probabilidades de ser elegida.
####
#### Resultado luego de ejecutar el código:
El rastro tiende a dirigirse hacía arriba.
####
#### Ocurrió lo que esperabas?, por qué crees que ocurrió?:
Si ocurrió lo que esperaba, ya que al analizar el código, el cual no tiene mucha complejidad, se puede evidenciar cómo las probabilidades favorecen la dirección "y-".

## Actividad #3: Distribuciones de probabilidad

#### En tus propias palabras cuál es la diferencia entre una distribución uniforme y una no uniforme de números aleatorios.
En una distribución uniforme, todos los posibles valores tienen la misma probabilidad de "salir". En cambio en una no uniforme, los posibles valores cuantan con probabilidades distintas.
####
#### Modifica el código de la caminata aleatoria para que utilice una distribución no uniforme, favoreciendo el movimiento hacia la derecha
``` js
  step() {
    const choice = floor(random(10));
    if (choice <= 4 ) {
      this.x++;
    } else if (choice <= 6) {
      this.x--;
    } else if (choice <= 8) {
      this.y++;
    } else {
      this.y--;
    }
  }
```
<img width="138" height="82" alt="image" src="https://github.com/user-attachments/assets/602de620-e8dd-46e3-b9de-221491e8826a" />

## Actividad #4: Distribución Normal
#### Crea un nuevo sketch en p5.js que represente una distribución normal.


#### Copia el código en tu bitácora.
``` js

let uniform


let value1=0;
let value2=0;
let value3=0;
let value4=0;
let value5=0;

function setup() {
  createCanvas(500, 500);
  uniform = new Uniform();
  background(200);
  uniform.txtUpdt();

}

function draw() {

  uniform.rngPicker();
  background(220);
  uniform.txtUpdt();
  uniform.lineDraw();
}


class Uniform{
    constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }
  
  rngPicker(){
    const resultado = floor(random(5));
    if(resultado == 0){
      value1++
    }
    else if(resultado ==1 ){
      value2++
    }
    else if(resultado ==2 ){
      value3++
    }
    else if(resultado ==3 ){
      value4++
    }
    else if(resultado ==4 ){
      value5++
    }
  
  }
  
  txtUpdt(){
    text(value1, 50, 150);
    text(value2, 50, 200);
    text(value3, 50, 250);
    text(value4, 50, 300);
    text(value5, 50, 350);
    
  }
  
  lineDraw(){
  line(80, 150, 80+value1, 150);
  line(80, 200, 80+value2, 200);
  line(80, 250, 80+value1, 250);
  line(80, 300, 80+value4, 300);
  line(80, 350, 80+value5, 350);
  }
    
}

```

#### Coloca en enlace a tu sketch en p5.js en tu bitácora.
[Enlace](https://editor.p5js.org/ThomasHyCr/sketches/xZyvPiP1g)

#### Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.
<img width="263" height="261" alt="image" src="https://github.com/user-attachments/assets/361d3680-0bf1-472f-889f-3ab67814109c" />


## Actividad #5: Distribución personalizada: Lévy flight
#### Crea un nuevo sketch en p5.js donde modifiques uno de los ejemplos anteriores y adiciones de Lévy flight.
#### Explica por qué usaste esta técnica y qué resultados esperabas obtener.
Quise usar esta tecnica para que sea bastante evidente cada vez que hay un salto, y que además sea bastante visible cúal salto se realizó mediante un codigo de colores.

#### Copia el código en tu bitácora.
``` js

let walker;
let c;
let s;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
  c = color(0);
  s = 5;
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(c);
    strokeWeight(s);
    point(this.x, this.y);
  }

  step() {
    const choice = floor(random(105));
    if (choice <= 100) {
      if (choice <= 25) {
        this.x++;
      } else if (choice <= 50) {
        this.x--;
      } else if (choice <= 75) {
        this.y++;
      } else if (choice <= 100) {
        this.y--;
      }
      c = color(0);
      s = 5;
      
    } 
    else if (choice <= 101) {
      this.x = this.x + 20;
      c = color('blue');
      s = 10;
    } 
    else if (choice <= 102) {
      this.x = this.x - 20;
      c = color('red');
      s = 10;
    } 
    else if (choice <= 103) {
      this.y = this.y + 20;
      c = color('yellow');
      s = 10;
    } 
    else {
      this.y = this.y - 20;
      c = color('green');
      s = 10;
    }
  }
}

```
#### Coloca en enlace a tu sketch en p5.js en tu bitácora.
[Enlace](https://editor.p5js.org/ThomasHyCr/sketches/lYHbZZRN7)
#### Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.
<img width="200" height="183" alt="image" src="https://github.com/user-attachments/assets/50f0e38f-6180-488a-bf12-a1e27cb47d2d" />

## Actividad #6: Ruido Perlin
#### Crea un nuevo sketch en p5.js donde los visualices.
#### Explica el concepto qué resultados esberabas obtener.
Espero poder representar el ruido, ya no como en una linea, sino en un circulo. Y que también el ruido afecte al color

#### Copia el código en tu bitácora.
``` js

let t = 0;
let sliderR;
let sliderS;
let sliderD;
let d;

function setup() {
  createCanvas(400, 400);
  
  sliderR = createSlider(60,200);
  sliderR.position(50,50);
  sliderR.size(80);
  sliderS = createSlider(0,100);
  sliderS.position(250,50);
  sliderS.size(80);
  sliderD = createSlider(20,100);
  sliderD.position(50,350);
  sliderD.size(80);

  colorMode(HSB, TWO_PI, 100, 100);
  
  
}

function draw() {
  background(255);
  stroke(0);
  strokeWeight(1);
  textSize(16);
  text('Radio',70,40);
  text('Longitud',260,40);
  text('Amplitud',60,340);
  
  
  translate(width / 2, height / 2);
  
  

  let radius = sliderR.value();
  let noiseScale = sliderS.value()*0.01;
  let d = sliderD.value();

  noFill();
  stroke(0);
  strokeWeight(3);

  beginShape();
  let noiseOffset = t;

  for (let angle = 0; angle < TWO_PI; angle += 0.02) {

    let r = radius + noise(noiseOffset) * d;

    let x = r * cos(angle);
    let y = r * sin(angle);

    stroke(noise(noiseOffset)*2, 80, 90);
    
    vertex(x, y);

    noiseOffset += noiseScale;
  }

  endShape(CLOSE);

  t += 0.01;
}


```

#### Coloca en enlace a tu sketch en p5.js en tu bitácora.
[Enlace](https://editor.p5js.org/ThomasHyCr/sketches/AGlDTe6Wt)


#### Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.
<img width="403" height="396" alt="image" src="https://github.com/user-attachments/assets/12a03e23-8db5-4d00-94cd-43705cc01bda" />

## Actividad #7: Creación de obra generativa
Vas a crear una obra generativa interactiva en tiempo real utilizando los conceptos de aleatoriedad que has aprendido en esta unidad.
Tu obra debe:

- Usar al menos tres conceptos estudiados en esta unidad COMBINADOS de manera creativa y coherente.
- Tu obra de ser interactiva y generativa en tiempo real. Puedes usar el mouse, el teclado o cualquier otro sensor de entrada para interactuar con la obra.

### Reporte
#### Un texto donde expliques el concepto de obra generativa.

#### Copia el código en tu bitácora.

#### Coloca en enlace a tu sketch en p5.js en tu bitácora.

#### Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.














Estas bitácoras de aprendizaje buscan evidenciar tu proceso y tus resultados de aprendizaje.

Cada bitácora tendrá las siguientes secciones:

``` markdown
# Unidad X

## Bitácora de proceso de aprendizaje


## Bitácora de aplicación 


## Bitácora de reflexión

```

En cada sección ingresa la información correspondiente. Utiliza para cada 
entrada que hagas el siguiente formato:

``` markdown
### título de la entrada
```














