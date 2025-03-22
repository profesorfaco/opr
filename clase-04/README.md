### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 04 → 26/03/2025

# Formatos ligeros de intercambios de datos en la creación de gráficas: CSV

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

Por legibilidad, conviene aprovecharnos de una manera en que GitHub muestra los CSV dentro de los repositorios:

https://github.com/datasciencedojo/datasets/blob/master/titanic.csv

Podríamos buscar en tales datos por el total de pasajeros por clase, cuántos sobrevivieron en total, la distribución sexogenérica, etc. 

¡Pero no los busquemos a mano! Hagámoslo con JavaScript, y mostremos el resultado con SVG.

Primero necesitamos hacer un *fetch* y un *parser* de los datos en [titanic.csv](https://raw.githubusercontent.com/datasciencedojo/datasets/refs/heads/master/titanic.csv). Para hacer lo que necesitamos muy rápido y [sin dolores de cabeza](https://youtu.be/RfMkdvN-23o?feature=shared), podríamos usar un atajo: [Papa Parse –The powerful, in-browser CSV parser for big boys and girls](https://www.papaparse.com/).

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

Con ello ya tenemos datos con los que comenzar a trabajar, desde el examen de la Consola de JavaScript (donde se podrían ver los `results` del *script*).

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Estamos partiendo con esto: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>¡Clase 4!</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous" />
    </head>
    <body>
        <div class="container">
            <div div="row">
                <div div="col">
                    <h1 class="mt-5 mb-4">Sietes por años:</h1>

                    <h2>Total por año</h2>

                    <table class="table table-striped">
                        <tr>
                            <td>2010</td>
                            <td id="diez"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2011</td>
                            <td id="once"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2012</td>
                            <td id="doce"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2013</td>
                            <td id="trece"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2014</td>
                            <td id="catorce"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2015</td>
                            <td id="quince"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2016</td>
                            <td id="dieciseis"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2017</td>
                            <td id="diecisiete"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2018</td>
                            <td id="dieciocho"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2019</td>
                            <td id="diecinueve"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2020</td>
                            <td id="veinte"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2021</td>
                            <td id="veintiuno"></td>
                            <td></td>
                        </tr>

                        <tr>
                            <td>2022</td>
                            <td id="veintidos"></td>
                            <td></td>
                        </tr>
                    </table>

                    <h2 class="my-5">Total por Profes</h2>

                    <address></address>
                </div>
            </div>
        </div>

        <script
            src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js"
            integrity="sha512-dfX5uYVXzyU8+KHqj8bjo7UkOdg18PaOtpa48djpNbZHwExddghZ+ZmzWT06R5v6NSk3ZUfsH6FNEDepLx9hPQ=="
            crossorigin="anonymous"
            referrerpolicy="no-referrer"
        ></script>
        <script>
            // todas las celdas
            const diez = document.querySelector("#diez");
            const once = document.querySelector("#once");
            const doce = document.querySelector("#doce");
            const trece = document.querySelector("#trece");
            const catorce = document.querySelector("#catorce");
            const quince = document.querySelector("#quince");
            const dieciseis = document.querySelector("#dieciseis");
            const diecisiete = document.querySelector("#diecisiete");
            const dieciocho = document.querySelector("#dieciocho");
            const diecinueve = document.querySelector("#diecinueve");
            const veinte = document.querySelector("#veinte");
            const veintiuno = document.querySelector("#veintiuno");
            const veintidos = document.querySelector("#veintidos");

            // marca
            const picto = "◾";

            // los raw data
            var datos;

            //esto es nuevo, no se asusten:
            var profes = [];
            var profesOK = [];
            const olimpo = document.querySelector("address");

            Papa.parse("https://raw.githubusercontent.com/profesorfaco/opr/main/clase-04/sietes.csv", {
                download: true,
                header: true,
                dynamicTyping: true,
                complete: function (results) {
                    console.log(results);
                    datos = results.data;
                    console.log(datos);
                    datos.forEach((x) => {
                        if (x.year == 2010) {
                            diez.innerHTML += picto;
                        } else if (x.year == 2011) {
                            once.innerHTML += picto;
                        } else if (x.year == 2012) {
                            doce.innerHTML += picto;
                        } else if (x.year == 2013) {
                            trece.innerHTML += picto;
                        } else if (x.year == 2014) {
                            catorce.innerHTML += picto;
                        } else if (x.year == 2015) {
                            quince.innerHTML += picto;
                        } else if (x.year == 2016) {
                            dieciseis.innerHTML += picto;
                        } else if (x.year == 2017) {
                            diecisiete.innerHTML += picto;
                        } else if (x.year == 2018) {
                            dieciocho.innerHTML += picto;
                        } else if (x.year == 2019) {
                            diecinueve.innerHTML += picto;
                        } else if (x.year == 2020) {
                            veinte.innerHTML += picto;
                        } else if (x.year == 2021) {
                            veintiuno.innerHTML += picto;
                        } else {
                            veintidos.innerHTML += picto;
                        }

                        //puedo aprovecharme del mismo ciclo

                        profes.push(x.tutor);
                    });

                    //y agrego algunas cosas

                    console.log(profes);

                    profesOK = [...new Set(profes)];

                    profesOK.sort();

                    console.log(profesOK);

                    olimpo.innerHTML = "Acá irían los profes… ";
                },
            });
        </script>
    </body>
</html>
```


- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-03) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-05)
