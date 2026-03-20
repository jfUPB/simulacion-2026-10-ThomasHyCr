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

### Actividad 02

#### Comparación con Example 4.2:

- ¿Qué responsabilidades que antes estaban en draw() ahora están dentro de la clase Emitter?  
El checkeo constante del tiempo de vida de las particulas

- ¿Cuál es la ventaja de encapsular la lógica de emisión en una clase separada?  
Que permite una mejor organización, comprensión, y adición de más emisores.

- En este ejemplo hay un array de emitters. ¿Quién crea los emitters? ¿Quién crea las partículas dentro de cada emitter?  
Cada vez que se da click se hace push de un nuevo emiter, en el emitter, el "addParticle", pushea nuevas particulas, al script particles.

- Dibuja un diagrama que muestre la jerarquía: sketch → [emitters] → [partículas]. ¿Cuántos niveles de “colección” hay?  
<img width="712" height="467" alt="image" src="https://github.com/user-attachments/assets/04bec3d0-678b-45d2-ad95-7dcb0b604ba7" />



### Actividad 03

- ¿Qué tienen en común las subclases de partículas? ¿Qué tienen de diferente?  
En común tienen todos los comportamientos y caracteristicas que no hayan sido sobre-escritos. De diferente, todo lo sobre-escrito.

- ¿Por qué es importante que el Emitter no necesite saber qué tipo específico de partícula está gestionando? Explica esto con tus propias palabras.  
Porque esto favorece el añadir nuevos tipos de particulas, sin necesidad de hacerle modificaciones al Emitter, Ergo el principio Open & Close de POO.

 - Si mañana quisieras agregar un tercer tipo de partícula, ¿Qué tendrías que crear y qué NO tendrías que modificar?  
Idealmente (no para eficiencia computacional, pero si para eficiencia colaborativa), crear un nuevo tipo de particula, y pasarsela al emitter, de forma que este no tenga que llamarla directamente, sino, simplemente recibir la instancia.
 
 - Compara con Example 4.2: ¿Cambió la lógica del Emitter? ¿Cambió la lógica de muerte? ¿Qué capa del sistema se modificó y cuáles permanecieron intactas?  
La lógica del emitter, solo se le añadió el llamado a crear la nueva particula. La lógica de muerte continúa igual, y simplemente se añadió un nuevo tipo de particula que hereda de particle, y tiene un override en el show().

#### Transferencia conceptual:

- Describe este ejemplo usando palabras que NO mencionen p5.js, JavaScript, ni ninguna herramienta específica. Usa solo términos como: entidad, estado, colección, emisor, ciclo de vida, fuerza.  
Este ejemplo permite crear emisores de entidades, las cuales comienzan con una fuerza inicial, y se ven sujetas a la gravedad. además cuentan con un tiempo de vida, y lentamente se desvanecen según este avanza.


## Bitácora de aplicación 


## Bitácora de reflexión
