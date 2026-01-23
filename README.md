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








