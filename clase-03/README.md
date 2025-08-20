### Introducción al desarrollo web desde el diseño → Clase 03 → 22/08/2025

# Conociendo dos lenguajes y una biblioteca: HTML5, CSS3 y p5.js

Conviene partir insistiendo en preguntas y respuestas, para simplificar la partida: 

- **¿Qué es lo que contiene la página? Se responde con HTML (HyperText Markup Language)**. Lenguaje estándar que describe la estructura de las páginas web. HTML5 es la versión más reciente de este lenguaje. El bloque constructivo más básico del HTML es el elemento. Cada elemento de HTML se escribe, generalmente, entre etiquetas: `<etiqueta>contenido</etiqueta>` → Podemos complementar esta breve introducción a HTML con una revisión de la página: https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/HTML_basics

- **¿Cómo se muestra lo que contiene la página? Se responde con CSS (Cascading Style Sheets)**. Lenguaje estándar que describe la presentación de las páginas web. CSS3 es la versión más reciente de este lenguaje. Su unidad más básica es la regla. Cada regla se inicia con un selector, seguido de paréntesis de llave `{…}`. Tal paréntesis contiene un bloque de declaraciones. En tal bloque, cada declaración se separa de otra mediante punto y coma `;`. Una declaración se compone del par `propiedad: valor`. Con todo lo dicho, una regla se escribirá, generalmente, de la siguiente manera: `selector{ propiedad: valor; }`  →  Podemos complementar esta breve introducción a CSS con una revisión de la página: https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/CSS_basics (no es necesario realizar el ejercicio que allí se propone).

- **¿Qué hace la página? Se responde con JS (JavaScript)**. Lenguaje de programación que controla el comportamiento de las páginas web. Con JS se pueden escribir secuencias de instrucciones con las que una computadora realizará una tarea determinada. Su estructura puede variar dependiendo de la lógica de cada instrucción, la [versión](https://www.w3schools.com/js/js_versions.asp) en uso, la *library* en la que nos apoyemos para resolver algo específico, o el *framework* de programación con el que se levanta todo el trabajo → Podemos complementar esta breve introducción a JS con una revisión de la página: https://developer.mozilla.org/es/docs/Learn/JavaScript/First_steps/What_is_JavaScript

Para comenzar a profundizar en un lenguaje de programación aprovechamos [p5.js](https://p5js.org/es/):

> p5.js es una herramienta amigable para aprender a programar y hacer arte. Es una biblioteca de JavaScript libre y de código abierto construida por una comunidad inclusiva y solidaria. ¡p5.js da la bienvenida a artistas, diseñadores, principiantes, educadores y cualquier otra persona!

Esta biblioteca fue creada por [Lauren McCarthy](http://lauren-mccarthy.com/), como una reinterpretación de [Processing](https://processing.org/) para la web. Consideremos que cuando se trabaja en Processing cada *sketch* tiene su `void setup()` y `void draw()`. Hay un `setup` que se ejecuta una única vez, en la partida. Hay un `draw` que por defecto se ejecuta una y otra vez. Ahora, cambiemos el `void` de [Java](https://es.wikipedia.org/wiki/Java_(lenguaje_de_programaci%C3%B3n)) por el `function` de [JavaScript](https://es.wikipedia.org/wiki/JavaScript), y tenemos:

```
function setup(){
  //colocas acá lo que se ejecuta una única vez
}

function draw(){
  //colocas acá lo que necesitas dibujar una y otra vez
}
```

Tal como Processing, [p5.js](https://p5js.org/es/) ofrece un conjunto completo de funcionalidades que *hace que dibujar con código sea tan intuitivo como dibujar en un cuaderno dibujar*. Pero puedes salir de los márgenes del [`<canvas></canvas>`](https://developer.mozilla.org/es/docs/Web/HTML/Reference/Elements/canvas) para tomar toda la página del navegador como tu cuaderno. Y puedes tomarla por el [Modelo de Objeto de Documento (DOM)](https://developer.mozilla.org/es/docs/Glossary/DOM): **A través del DOM, los programas escritos en JavaScript pueden acceder y modificar el contenido, estructura y estilo a la vista**.

Con el DOM podemos manipular una página así como cuando *photoshopeamos* una imagen. Si capturaste una imagen con 3 elementos y agregas un cuarto *photoshopénadolo*, en ningún caso modificas el fenómeno capturado, pero todos podrán ver una imagen con 4 elementos. 

Por la manipulación del DOM **podríamos encontrar inconcruencias entre** dos vista: la del **código fuente de la página** y la de los **elementos de la página**. Estirando la analogía: En el código fuente de la página ves el fenómeno tal como fue capturado, mientras que en la vista de elementos de la misma página está lo *photoshopeado* (lo que tenemos a la vista en toda la página del navegador).

Para que esta diferencia quede muy clara, aprovechen [este ejemplo](https://profesorfaco.github.io/dno037-2023-2/clase-02/ejemplo.html), donde pueden revisar las diferencias entre la vista del **código fuente de la página** y la de los **elementos de la página**. Noten que en el código fuente faltan contenidos que sí están en la visualización que ofrece el navegador y en los elementos de la página.


- - - - - - - 

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/opr/tree/main/clase-01) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-04)

