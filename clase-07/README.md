### Introducción al desarrollo web desde el diseño → Clase 07 → 26/09/2025

# Avanzando en JavaScript sin bibliotecas

#### Primero las funciones

Recordarán, por el uso del https://editor.p5js.org/, que el sketch inicia, por defecto, con:

```
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}
```

Esa partida tiene 2 declaraciones de función. Cada una con su nombre, sin parámetros entre paréntesis redondo y sólo una declaración encerrada entre paréntesis de llave. 

Como se lee en [MDN](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Functions): 

> Las funciones son uno de los bloques de construcción fundamentales en JavaScript. Una función en JavaScript es similar a un procedimiento — un conjunto de instrucciones que realiza una tarea o calcula un valor, pero para que un procedimiento califique como función, debe tomar alguna entrada y devolver una salida donde hay alguna relación obvia entre la entrada y la salida. Para usar una función, debes definirla en algún lugar del ámbito desde el que deseas llamarla.

Ese par de funciones con las que parte p5.js sólo funcionan con la biblioteca tal como indica la referencia: 

- https://p5js.org/es/reference/p5/setup/

- https://p5js.org/es/reference/p5/draw/

Al trabajar sin p5.js ni otra biblioteca podremos crear funciones que no tendrán un “comportamiento predefinido". Podríamos crear, por ejemplo, una función que se llame setup y me calcule cuántas mesas necesito para un número determinado de personas: 

```
<html>
  <script>
  function setup(n){
    return Math.ceil(n / 5);
  }
  </script>
</html>
```

Tal código fuente lo pueden copiar y pegar en un nuevo documento HTML. Luego pueden abrir la consola de Javascript para escribir `setup(123)`. El resultado será el número de mesas para 5 personas que se necesitan conseguir para 123 personas. Y pueden probar cualquier otro número.

El `Math.ceil()`, que contiene a la división de número por 5, hace algo como el `Math.roud()` y el `Math.floor()`, que se explican junto a otros `Math` en https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math 

Queda así que `setup()` no implica algo más allá de la biblioteca de p5.js, pero `Math.ceil()` implica algo en cualquier uso de JavaScript, con o sin bibliotecas. 

#### Hazlo tantas veces sea necesario

Corresponde conocer el ciclo `for`: https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Loops_and_iteration#declaraci%C3%B3n_for

Diferenciarlo del método `forEach()`: https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach

#### Selecciona

Seguramente usaremos `document.querySelector()`: https://developer.mozilla.org/es/docs/Web/API/Document/querySelector

Alguna vez podría ser necesario usar el `document.querySelectorAll()` https://developer.mozilla.org/es/docs/Web/API/Document/querySelectorAll

#### Interacción

Para más adelante dejaremos el registro de eventos: https://developer.mozilla.org/es/docs/Web/API/EventTarget/addEventListener

#### Probemos

```
<!doctype html>
<html lang="es">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Ejemplo</title>
  </head>
  <body>
    <button onclick="muestra()">Click</button>
    <p></p>
    <p></p>
    <p></p>
    <p></p>
    <script>
      const valores = [6, 7, 9, 2];
      const parrafos = document.querySelectorAll("p");
      function muestra(){
        valores.forEach((v,i) => {
          parrafos[i].innerHTML = emojis(v);
        })
      }
      function emojis(n){
        var imprime = ""
        for(var x = 0; x < n; x++){
          imprime += "🤧 "
        }
        return imprime;
      }
    </script>
  </body>
</html>
```

- - - - - - - - - - - -

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/opr/tree/main/clase-06) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-08)
