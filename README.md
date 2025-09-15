# Laboratorio 3 Programación Web

![alt text](image.png)

# Preguntas de Laboratorio

## ¿Por qué cambia el posicionamiento de las cajas internas al div principal?
`.box`

```css
.box {
    display: flex;
    background-color: var(--pink);
    flex-direction: column;
}

.box div {
    margin: 10px 5px;
    border-radius: 8px;
    padding: 5px;
    background-color: var(--blue);
}
```

El posicionamiento cambia porque el contenedor .box usa Flexbox (display: flex;).
Esto hace que todos los div internos se conviertan en elementos flexibles, y con flex-direction: column; se organizan de arriba hacia abajo en forma de columna, en lugar de seguir el flujo normal del HTML.

----------------

## ¿Qué pasa si me solicitan hacer un cambio en el orden de los elementos pero sin tocar los archivos html y js, será que puedo lograrlo a traves de CSS?

✅ Sí, se puede lograr con CSS, usando la propiedad order.
Cada hijo de un contenedor flex tiene por defecto order: 0.
Si se cambia ese valor, se puede alterar el orden visual de los elementos sin necesidad de tocar el HTML ni usar JavaScript.

`.box` :
``` css

.box div:first-child {
    order: 3; /* Se moverá al final */
}

.box div:nth-child(2) {
    order: 1; /* Será el primero */
}

.box div:nth-child(3) {
    order: 2; /* Será el segundo */
}
```
Esto mostrará los elementos en el orden:
Two → Three → One, aunque en el HTML se mantenga el orden original.

-----------------

`.box`: 

``` css

.box {
    display: flex;
    background-color: var(--pink);
    flex-direction: row;
    flex-wrap: wrap;
}

.box div {
    margin: 10px 5px;
    border-radius: 8px;
    padding: 5px;
    background-color: var(--blue);
    width: 33%;
}

.box div:first-child { 
    width: 64%;
}

```
## ¿Qué hacen estás propiedades?

- `display : flex;` → convierte al contenedor .box en un **flex container**, todos sus hijos div en elementos flexibles. Esto permite organizar los elementos de manera más controlada que con el flujo normal de HTML

- `background-color : var(--pink)` → pinta el fondo de contenedor de color rosa 

- `flex-direction: row` → organiza los hijos en fila (horizontalmente)

- `flex-wrap: wrap` → permite que los hijos se "rompan" y pasen a la siguiente fila si no caben en una sola. Sin esto, todos los elementos se quedaban en la misma fila y podìan desbordar el contenerdor.

- `margin: 10px 5px;` → espacio alrededor de cada div (10px arriba y abajo, 5px izquierda y derecha).

- `border-radius: 8px;` → esquinas redondeadas de 8px.

- `padding: 5px;` → espacio interno entre el contenido y el borde.

- `background-color: var(--blue);` → fondo azul para cada div.

- `width: 33%;` → cada div ocupa un tercio del ancho del contenedor..ç

- `width: 64%;` → hace que el primer div sea más ancho que los otros (ocupa el 64% del ancho del contenedor). Esto afecta cómo se distribuyen los demás elementos porque Flexbox redistribuye el espacio restante.

--------------

## ¿Puedo diseñar toda mi web usando GRID? ¿Por qué se dan estos cambios entre tan pocas líneas de diseño CSS?

Sí, se puede diseñar toda una web usando **CSS Grid**, ya que esta herramienta está pensada para organizar el **layout completo en dos dimensiones** (filas y columnas).  
Con Grid se puede estructurar fácilmente el *header*, el contenido principal, un *sidebar* y el *footer* sin necesidad de muchas reglas CSS adicionales.  

La razón por la que se dan estos cambios tan notorios con pocas líneas de código es porque **Grid es declarativo**: basta con definir las áreas y la distribución de columnas/filas en el contenedor, y el navegador automáticamente acomoda los elementos en esas posiciones.  

Por ejemplo, con solo unas líneas como:  

```css
grid-template-areas: 
  "Header Header Header Header"
  "Main Main . Sidebar"
  "Footer Footer Footer Footer";

```

ya logro que:

* El header abarque toda la primera fila.

* El main ocupe dos tercios y el sidebar un tercio de la segunda fila.

- El footer se coloque al final ocupando toda la tercera fila.

Esto antes requería muchas más reglas, pero con Grid se simplifica bastante.

👉 Aunque se puede usar Grid para todo, en la práctica lo mejor es combinarlo con Flexbox: Grid para el esqueleto principal y Flexbox para organizar el contenido interno de cada sección.