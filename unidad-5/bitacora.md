# Unidad 5
<img width="1000" height="628" alt="image" src="https://github.com/user-attachments/assets/a45b41ec-95cf-45c8-9d98-139deab89c64" />

## Bitácora de proceso de aprendizaje
### Actividad 01

#### Capa de comportamiento:

- ¿Qué propiedades tiene cada partícula? Clasifícalas: ¿Cuáles definen su estado físico? ¿Cuáles su estado vital?  
Aparte de las propiedades del motion 101, y las de la apariencia, estas particulas cuentan una propiedad que es el tiempo de vida, este es como un contador, que va reduciendose con el tiempo.

- ¿Qué condición determina que una partícula “muere”? ¿Es una muerte instantánea o gradual?  
Un contador que se va reduciendo con el tiempo, visualmente se ve como gradual, debido a que la opacidad de la particula se ve dictada por su tiempo restante de vida.

- ¿Cómo se actualiza la partícula en cada frame? Identifica el patrón motion 101 dentro de la partícula.  
El componente de la velocidad, y la posición se calculan normalmente, además tiene el mañadido del tiempo de vida, y la aceleración se reinicia luego de estos calculos.

  
#### Capa de estructura:

- ¿Quién crea las partículas? ¿En qué momento? 
El script "particles", en el draw se crean, cada vez que se hace push de una nueva particula.

- ¿Quién decide cuándo eliminar una partícula del array?  
El tiempo de vida, el cual en el draw se está chequeando constantemente.

- ¿Por qué se recorre el array en orden inverso para eliminar? ¿Qué pasaría si no se hiciera así?  
Para evitar fallos, y fugas de memoria, debido al funcionamiento del splice. Porque este luego de eliminar un elemento del array "jala" a los siguientes elementos, lo que causa que el que sería el siguiente elemento a checkear, sea saltado.

- Si no eliminaras nunca las partículas, ¿Qué pasaría con la memoria y el rendimiento? Haz el experimento: comenta la línea que elimina y observa el frame rate.  
La particulas permanecerían vivas, y se acumularian, lo que destruiria el rendimiento de la aplicación

  
#### Capa de visualización:

- ¿Qué elementos visuales usa para representar una partícula?
- ¿Cómo se conecta el “tiempo de vida” con la apariencia visual?
- Si quisieras cambiar la representación visual (por ejemplo, usar líneas en vez de círculos), ¿Qué cambiarías y qué NO cambiarías?



## Bitácora de aplicación 


## Bitácora de reflexión
