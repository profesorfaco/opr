### Optativo de Profundización: [Desarrollo Web y Diseño Visual de Información](https://github.com/profesorfaco/opr/?tab=readme-ov-file#readme) → Clase 04 → 27/03/2026

# Formatos ligeros de intercambios de datos (clase 1 de 2)

### Teoría (para la casa)

CSV es sigla de Comma Separated Values (Valores separados por comas en castellano), y resulta de exportar los datos de una Tabla, Hoja de Cálculo o Planilla de Excel.

En el ejemplo del artículo de Wikipedia para [Valores separados por comas](https://es.wikipedia.org/wiki/Valores_separados_por_comas), tenemos los siguientes datos:

| Año | Marca | Modelo | Descripción | Precio |
|:----|:-------|:-------|:------------|:-------|
| 1997	| Ford	| E350	| ac, ABS, moon	| 3000.00 |
| 1999	| Chevy	| Venture	| Extended Edition | 4900.00 |
| 1999 | Chevy | Venture | Extended Edition, Very Large	| 5000.00 |
| 1996 | Jeep | Grand Cherokee | MUST SELL! air, moon roof, loaded	| 4799.00 |

Los mismos datos en CSV:

```
Año,Marca,Modelo,Descripción,Precio
1997,Ford,E350,"ac, ABS, moon",3000.00
1999,Chevy,Venture,Extended Edition,4900.00
1999,Chevy,Venture,"Extended Edition, Very Large",5000.00
1996,Jeep,Grand Cherokee,"MUST SELL! air, moon roof, loaded",4799.00
```

Las filas siguen siendo filas. Las columnas son reemplazadas por la separación de las comas.

Si nos quedamos con la primera fila (de arriba hacia abajo) podemos notar su función de encabezado de columna: Le da sentido a lo que sigue abajo, sean años, marcas, modelos, descripciones o precios.

Así mismo podríamos leer un CSV con más datos: 

https://raw.githubusercontent.com/datasciencedojo/datasets/refs/heads/master/titanic.csv

Por legibilidad, conviene aprovecharnos de la manera en que GitHub muestra los CSV dentro de los repositorios:

https://github.com/datasciencedojo/datasets/blob/master/titanic.csv

Podríamos revisar en tales datos el total de pasajeros por clase, cuántos sobrevivieron, la distribución sexogenérica, etc. 

¡Pero no los busquemos a mano! Hagámoslo con JavaScript, y mostremos el resultado con SVG.

Para esto, primero necesitamos hacer un *fetch* y un *parser* de los datos en [titanic.csv](https://raw.githubusercontent.com/datasciencedojo/datasets/refs/heads/master/titanic.csv). Para hacer lo que necesitamos muy rápido y [sin dolores de cabeza](https://youtu.be/RfMkdvN-23o?feature=shared), podríamos usar un atajo: [Papa Parse –The powerful, in-browser CSV parser for big boys and girls](https://www.papaparse.com/).

Para usar el atajo, podríamos partir con algo como lo que sigue:

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js" integrity="sha512-dfX5uYVXzyU8+KHqj8bjo7UkOdg18PaOtpa48djpNbZHwExddghZ+ZmzWT06R5v6NSk3ZUfsH6FNEDepLx9hPQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script>
Papa.parse("https://raw.githubusercontent.com/datasciencedojo/datasets/refs/heads/master/titanic.csv", {
	download: true,
	header: true,
	dynamicTyping: true,
	complete: function(results) {
		console.log(results);
	}
});
</script>
```

Noten cómo vamos por un recurso en línea, y luego el *script* muestra una estructura bastante particular: Eso nos revela que este atajo es una bibliteca de JavaScript.

Y si leemos tal estructura contenida por `Papa.parse("…", {})`, notaremos que antes del `complete` que le da paso a una `function`, se le pide a la biblioteca que:

`download: true` → traiga los datos al computador

`header: true` → mantenga los encabezados del CSV

`dynamicTyping: true` → trate a los números como tales, sin transformarlos a "caracteres" ni "cadenas de caracteres". 

Con ello ya tenemos datos con los que comenzar a trabajar, datos que podríamos ver en la Consola de JavaScript.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Partamos copiando lo que sigue en un documento nuevo, para luego guardarlo como `index.html`: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <title>TITANIC v/s ICEBERG</title>
        <style>
            body {
                font-family: sans-serif;
                color: #333;
                background: #fcfeff;
            }

            div {
                width: min(95%, 700px);
                margin: 0 auto;
            }

            header {
                text-align: center;
            }

            header svg {
                width: 75%;
            }

            h1 {
                font-size: 2rem;
                font-weight: 200;
            }

            p {
                margin: 0.9rem 0.3rem;
            }

            footer {
                border-top: 1px solid #eee;
                margin-top: 3rem;
                padding-bottom: 3rem;
            }
        </style>
    </head>
    <body>
        <div>

            <header>
                <!-- Ícono SVG del iceberg -->
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400" fill="none" stroke="#111" stroke-width="2">
                    <polygon points="200,20 250,100 300,150 250,350 200,380 125,275 90,200 100,125 180,25" />
                    <line x1="10" y1="100" x2="390" y2="100" />
                </svg>

                <h1>TITANIC v/s ICEBERG</h1>
            </header>

            <main>
                <!-- El número de pasajeros se escribe aquí con JavaScript -->
                <p>Usaremos datos disponibles en línea. Con ellos visualizaremos el destino de las <span id="total"></span> personas a bordo del Titanic, divididas en tres clases:</p>

                <!-- El gráfico de barras se dibuja aquí con JavaScript -->
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 892 150">
                    <g id="grafico"></g>
                </svg>
            </main>

            <footer>
                <p>DNO097 — Nombre Apellido</p>
            </footer>

        </div>

        <!-- Librería para leer archivos CSV -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js"></script>

        <script>
            // Contadores para cada clase de pasajero
            var primera = 0;
            var segunda = 0;
            var tercera = 0;

            // Elementos del HTML donde escribiremos los resultados
            var spanTotal = document.querySelector("#total");
            var grafico   = document.querySelector("#grafico");

            // Leemos el archivo CSV desde internet
            Papa.parse("https://raw.githubusercontent.com/datasciencedojo/datasets/refs/heads/master/titanic.csv", {
                download: true,       // descarga el archivo
                header: true,         // la primera fila son los nombres de columnas
                dynamicTyping: true,  // convierte números automáticamente

                complete: function (results) {

                    // Mostramos el total de pasajeros en el HTML
                    spanTotal.innerHTML = results.data.length;

                    // Revisamos cada fila y contamos por clase
                    results.data.forEach(function(pasajero) {
                        if (pasajero.Pclass == 1) {
                            primera = primera + 1;
                        } else if (pasajero.Pclass == 2) {
                            segunda = segunda + 1;
                        } else {
                            tercera = tercera + 1;
                        }
                    });

                    // Dibujamos una barra por cada clase dentro del SVG
                    grafico.innerHTML =
                        // Primera clase (oscuro)
                        `<rect x="0" y="0" width="${primera}" height="100" fill="#333"></rect>
                        <text x="${primera / 2}" y="60" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#fff">${primera}</text>
                        <text x="${primera / 2}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#333">PRIMERA CLASE</text>` +

                        // Segunda clase (gris medio)
                        `<rect x="${primera}" y="0" width="${segunda}" height="100" fill="#666"></rect>
                        <text x="${primera + segunda / 2}" y="60" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#fff">${segunda}</text>
                        <text x="${primera + segunda / 2}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#333">SEGUNDA CLASE</text>` +

                        // Tercera clase (claro)
                        `<rect x="${primera + segunda}" y="0" width="${tercera}" height="100" fill="#999"></rect>
                        <text x="${primera + segunda + tercera / 2}" y="60" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#fff">${tercera}</text>
                        <text x="${primera + segunda + tercera / 2}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#333">TERCERA CLASE</text>`;

                } // fin de complete

            }); // fin de Papa.parse
        </script>
    </body>
</html>
```

Les dejo la base para los gráficos de dona: 

```
<svg width="100%" height="100%" viewBox="0 0 42 42" class="donut">
    <circle class="donut-ring" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#ddd" stroke-width="3"></circle>
    <circle class="donut-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#000" stroke-width="3" stroke-dasharray="37 63" stroke-dashoffset="0"></circle>
    <text x="21" y="19" font-size="9" dominant-baseline="middle" text-anchor="middle">37%</text>
    <text x="21" y="25" font-size="3" dominant-baseline="middle" text-anchor="middle">PRIMERA CLASE</text>
</svg>
```

Y la parte del cierre: 

```
<div id="cierre">
    <img src="https://www.gerdarntz.org/sites/gerdarntz.org/files/GMDH02_00290.gif" />
</div>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-03) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-06)
