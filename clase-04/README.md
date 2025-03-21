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
        <title>TITANIC v/s ICEBERG</title>
        <link rel="preconnect" href="https://fonts.googleapis.com" />
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
        <link href="https://fonts.googleapis.com/css2?family=Sofia+Sans+Extra+Condensed:ital,wght@0,1..1000;1,1..1000&display=swap" rel="stylesheet" />
        <style>
            body { font-family: "Sofia Sans Extra Condensed", sans-serif; text-align: center; }
            
            div { margin: 2vh 25vw 5vh 25vw; }
            
            @media (orientation: portrait) {
                div { margin: 2vh 2vw 3vh 2vw; }
            }
            
            svg#cabecera { width: 70%; margin: 0 auto;}

            @keyframes flota {
                0% {transform: translateY(0);}
                100% {transform: translateY(10px);}
            }

            polygon#iceberg { animation: flota 3s ease infinite alternate; }

            line#mar { animation: flota 2s ease infinite alternate; }

            h1 { font-size: calc(2rem + 2vw); letter-spacing: 0.1rem;}

            h1 > span { font-size: 80%; color: #0288d1; margin-left: 0.5rem; margin-right: 0.5rem; display: inline-block;}

            p {text-align: left; font-size:1.25rem;}
        </style>
    </head>
    <body>
        <div>
            
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400" id="cabecera" fill="none" stroke="#29B6F6" stroke-width="3" stroke-linecap="round" stroke-linejoin="round">
                <polygon points="200,20 250,100 300,150 250,350 200,380 125,275 90,200 100,125 180,25" id="iceberg" />
                <line x1="10" y1="150" x2="390" y2="150" id="mar" />
            </svg>
            
            <h1>TITANIC <span><sup>v</sup>/<small>s</small></span> ICEBERG</h1>
            
            <p>Usaremos datos disponibles en línea, en <a href="https://github.com/datasciencedojo/datasets/blob/master/titanic.csv" target="_blank">esta tabla</a>. Con tales datos podremos visualizar el destino de las <span id="dato"></span> personas que iban a bordo del Titanic, divididas en tres clases:</p>

            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 892 150">
                <g id="segmentos"></g>
            </svg>

            <p>Apelando a la ficción hollywoodense y algunas condiciones (lógicas): Partamos calculando el número de personas como <a href="https://es.wikipedia.org/wiki/Rose_DeWitt_Bukater" target="_blank">Rose DeWitt Bukater</a> y <a href="https://es.wikipedia.org/wiki/Jack_Dawson" target="_blank">Jack Dawson</a>.</p>

        </div>

        <script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js" integrity="sha512-dfX5uYVXzyU8+KHqj8bjo7UkOdg18PaOtpa48djpNbZHwExddghZ+ZmzWT06R5v6NSk3ZUfsH6FNEDepLx9hPQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        
        <script>
            var primera = 0;
            var segunda = 0;
            var tercera = 0;
            const total = document.querySelector("#dato");
            const clases = document.querySelector("#segmentos");

            Papa.parse("https://raw.githubusercontent.com/datasciencedojo/datasets/refs/heads/master/titanic.csv", {
                download: true,
                header: true,
                dynamicTyping: true,
                
                complete: function (results) {
                    console.log(results);
                    total.innerHTML = results.data.length;
                    
                    //reviso los datos

                    results.data.forEach(d => {
                        if(d.Pclass == 1){
                            primera = primera+1;
                        } else if(d.Pclass == 2){
                            segunda = segunda+1;
                        }else{
                            tercera = tercera+1;
                        }
                    })

                    //trabajo con el resultado de la revisión

                    clases.innerHTML = `<rect x="0" y="0" width="${primera}" height="100" fill="#B3E5FC"></rect>
                    <text x="${primera/2}" y="50" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#01579B">${primera}</text>
                    <text x="${primera/2}" y="120" font-size="24" dominant-baseline="middle" text-anchor="middle" fill="#01579B">PRIMERA CLASE</text>`

                    clases.innerHTML += `<rect x="${primera}" y="0" width="${segunda}" height="100" fill="#4FC3F7"></rect>
                    <text x="${primera+(segunda/2)}" y="50" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#01579B">${segunda}</text>
                    <text x="${primera+(segunda/2)}" y="120" font-size="24" dominant-baseline="middle" text-anchor="middle" fill="#01579B">SEGUNDA CLASE</text>`

                   clases.innerHTML += `<rect x="${primera+segunda}" y="0" width="${tercera}" height="100" fill="#03A9F4"></rect>
                    <text x="${primera+segunda+(tercera/2)}" y="50" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#01579B">${tercera}</text>
                    <text x="${primera+segunda+(tercera/2)}" y="120" font-size="24" dominant-baseline="middle" text-anchor="middle" fill="#01579B">TERCERA CLASE</text>`

                } // cierra lo abierto después de complete: function…

            }); // cierra lo abierto después de Papa.parse("https…

        </script>
    </body>
</html>
```


- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-03) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-05)
