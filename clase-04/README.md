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
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>TITANIC v/s ICEBERG</title>
        <style>
            @import url('https://fonts.googleapis.com/css2?family=Roboto+Condensed:ital,wght@0,100..900;1,100..900&display=swap');

            body{ font-family: "Roboto Condensed", sans-serif; font-weight:300; color:#333; background:#fcfeff; }
            
            div{ width:min(95%,700px); margin:0 auto;}
            
            a{color:#000;}

            a:hover{color:#333;}
            
            header{text-align: center; }

            header svg{ width: 75%; margin: 0 auto;}

            @keyframes flota {
                0% {transform: translateY(0);}
                100% {transform: translateY(10px);}
            }

            polygon#iceberg { animation: flota 3s ease infinite alternate; }

            line#mar { animation: flota 2s ease infinite alternate; }

            h1 { font-size: calc(1rem + 3vw); line-height: 1; font-weight: 200;}

            h1 > span {font-size: 90%; color: #111; font-weight: 200; display: inline-block; margin:0 0.5rem}

            p {margin:0.9rem 0.3rem;}

            footer{ border-top:1px solid #eee; margin-top:3rem; padding-bottom:3rem; }
            
            footer > p{ display:flex; justify-content: space-between; }
        </style>
    </head>
    <body>
        <div>
            <header>
                
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400" id="cabecera" fill="none" stroke="#111" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <polygon points="200,20 250,100 300,150 250,350 200,380 125,275 90,200 100,125 180,25" id="iceberg" />
                    <line x1="10" y1="100" x2="390" y2="100" id="mar" />
                </svg> 
                
                <h1>TITANIC <span><sup>v</sup>/<small>s</small></span> ICEBERG</h1>
            
            </header>
            <main>
                
                <p>Usaremos datos disponibles en línea, en <a href="https://github.com/datasciencedojo/datasets/blob/master/titanic.csv" target="_blank">esta tabla</a>. Con tales datos podremos visualizar el destino de las <span id="dato"></span> personas que iban a bordo del Titanic, divididas en tres clases:</p>

                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 892 150">
                    <g id="segmentos"></g>
                </svg>
                
                <p>Aprovechando la ficción y algunas condiciones lógicas: Calculemos el número de personas como <a href="https://es.wikipedia.org/wiki/Rose_DeWitt_Bukater" target="_blank">Rose DeWitt Bukater</a> y <a href="https://es.wikipedia.org/wiki/Jack_Dawson" target="_blank">Jack Dawson</a>.</p>

            </main>
            <footer>
                
                <p><a href="https://github.com/profesorfaco/opr/tree/main/clase-04">DNO097</a> <a href="#">Nombre Apellido</a></p>
                
            </footer>
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

                    clases.innerHTML = `<rect x="0" y="0" width="${primera}" height="100" fill="#333"></rect>
                    <text x="${primera/2}" y="60" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#fff">${primera}</text>
                    <text x="${primera/2}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#333">PRIMERA CLASE</text>`

                    clases.innerHTML += `<rect x="${primera}" y="0" width="${segunda}" height="100" fill="#666"></rect>
                    <text x="${primera+(segunda/2)}" y="60" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#fff">${segunda}</text>
                    <text x="${primera+(segunda/2)}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#333">SEGUNDA CLASE</text>`

                   clases.innerHTML += `<rect x="${primera+segunda}" y="0" width="${tercera}" height="100" fill="#999"></rect>
                    <text x="${primera+segunda+(tercera/2)}" y="60" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#fff">${tercera}</text>
                    <text x="${primera+segunda+(tercera/2)}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#333">TERCERA CLASE</text>`

                } // cierra lo abierto después de complete: function…

            }); // cierra lo abierto después de Papa.parse("https…

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

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-03) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-05)
