### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 03 → 19/03/2025

# Datos e información en gráficas (segunda parte)

### Teoría (para la casa)

La [clase recién pasada](https://github.com/profesorfaco/opr/tree/main/clase-02) hablamos de *gráficas* de manera acotada: como traducción del inglés *chart* o el alemán *diagramm*, palabras que tienen un relación con números y las convenciones que posibilitan ver algo que, en principio, no pueda darse a la (misma) vista.

Así, por ejemplo, cuando conocemos las convenciones de una [gráfica de línea](https://datavizcatalogue.com/ES/metodos/grafica_de_linea.html) podemos ver cómo cambian los números de “algo” en un intervalo de tiempo determinado. 

Lo convencional de la gráfica que visualiza (*chart* o *diagramm*) puede funcionar como lo convencional de juntar **Á → R → B → O → L** para referir a una *planta de tallo leñoso y elevado, que se ramifica a cierta altura del suelo*; cuando ignoramos la convención, podemos incluso omitir la intención de referir por medio de **Á → R → B → O → L** a tal o cualquiera *planta de tallo leñoso…*. 

Conviene, entonces, aprender convenciones y conocer las aprendidas: *Yo nunca he usado [la gráfica de bala](https://datavizcatalogue.com/ES/metodos/grafico_de_bala.html), pero revisando sus artículos noto que ustedes y sus lectores lo usan siempre. Tendré que aprender a usarla.*

Ese *uso* en la anécdota implica aprender la convención para poder escribir y leer tales gráficas que visualizan. Y para aprender las convenciones de varias gráficas es muy recomendable consultar a:

- https://datavizcatalogue.com/ES/buscar.html
- https://datavizproject.com/

Conviene notar que el segundo vínculo en la lista nos ofrece una búsqueda por *FAMILY*, donde no solo está la opción de *Chart*, también está la de *Diagram* (en inglés y con una *m*; no son dos como en alemán). Nótese que dentro de la familia *Diagram* es posible encontrar, por ejemplo, este *Exploded View Drawing*:

![zapato](https://github.com/user-attachments/assets/ff7770bc-d412-4461-ae17-a9d09d44982f)


Aunque lo que tenemos a la vista no es, en rigor, un *drawing* y mejor sería llamarle *picture*, convengamos que consiste en la representación de algo que antes pudo estar AHÍ ADELANTE. En este caso, lo que está a la vista refiere a lo que le es semejante (en su aparecer conocido). Veo, por semejanza, una bota como las botas que ya pude haber visto AHÍ ADELANTE (este AHÍ ADELANTE, en mayúscula, se toma de Edmund Husserl escribiendo, en *Ideas I*, sobre un mundo extendido que cada uno encuentra ante sí inmediata e intuitivamente, mediante el ver, el tocar, el oir, etc., en los diversos modos de percepción sensible). 

En el *Exploded View Drawing* no habría un visualizar, sino un visibilizar. Lo que ofrece a la vista ya tenía forma visible. Y visibilizar implica representar o volver a presentar algo que ya pudo presentarse a la vista.

Mientras la gráfica que visualiza nos exige trabajar con convenciones bien conocidas para presentar en gráfica algo por primera vez, la gráfica que visibiliza nos exige mayor atención a las experiencias de quien las tendrá a la vista por segunda vez (en su representación).

Considérese, esta gráfica de [Guemil](https://www.guemil.info/):

![guemil](https://github.com/user-attachments/assets/d22ee002-252a-42ef-85ed-815e937da1cb)

Desde Japón se le comentó a Rodrigo Ramirez, el creador de Guemil, que era necesario agregar a su primera representación, llamada *drop and cover*, un *hold*, porque allá se enseña a sujetar (*to hold*) una pata de la mesa, para evitar que el mismo movimiento telúrico la desplace y deje de cubrir.

Luego, cuanto ya respresentaba el *drop, hold and cover*, tal como ahora está a la vista de ustedes, desde EE.UU. se pensó que la gráfica refería, por su semejanza, a un *school shooting*.

Pero incluso la semejanza a lo visto AHÍ ADELANTE, en la propia experiencia, puede ser afectada por el dominio de una convención. Tal es el caso que presenta Jorge Frascara en *El diseño de comunicación visual* (2006, p.75), citando a [Uger Mijksenaar](https://www.theicod.org/storage/app/media/resources/Publications/Icographic/ICO_Publications_Icographic_07_full.pdf)

<img width="500" alt="mina" src="https://github.com/user-attachments/assets/1cbf839d-3aa5-4ac2-aed9-9a999d41698d" />

> Dado que muchos mineros sudafricanos no sabían leer, esta historieta fue concebida para persuadirlos de dejar los rieles libres de material caído. Sin embargo, no funcionó: un creciente número de rocas se encontró en los rieles. La causa descubierta, fue que los mineros tendían a leer el mensaje de derecha a izquierda, y obedientemente sacaban rocas de las vagonetas. 

Sobre visualización y visibilización, convención y semejanza, presentación y representación, opera el diseño de información que es un término que, según escribe Isabel Meirelles en Design for Information (2013, p.11):

> is broadly used to describe communication design practices in which the main purpose is to inform, in contrast to persuasive approaches more commonly used in practices such as advertising. Infographics is one of the possible outputs within the large information design discipline.

Y cuando aparecer el término de *infographics*, corresponde recordar, también con Isabel Meirelles, que: 

> In a nutshell, infographics stand for visual displays in which graphics (illustrations, symbols, maps, diagrams, etc) together with verbal language communicate information that would not be possible otherwise

Corresponde notar que la definición de infografía citada está apuntado a gráficas que visibilizan o representan, tales como ilustraciones y mapas, pero no necesariamente se restringe a ellas.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Partamos con el siguiente código en un `index.html`:

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

            h1 { font-size: calc(1rem + 4vw); line-height: 1; font-weight: 200;}

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
                    <text x="${primera/2}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#012d4f">PRIMERA CLASE</text>`

                    clases.innerHTML += `<rect x="${primera}" y="0" width="${segunda}" height="100" fill="#666"></rect>
                    <text x="${primera+(segunda/2)}" y="60" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#fff">${segunda}</text>
                    <text x="${primera+(segunda/2)}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#012d4f">SEGUNDA CLASE</text>`

                   clases.innerHTML += `<rect x="${primera+segunda}" y="0" width="${tercera}" height="100" fill="#999"></rect>
                    <text x="${primera+segunda+(tercera/2)}" y="60" font-size="48" dominant-baseline="middle" text-anchor="middle" fill="#fff">${tercera}</text>
                    <text x="${primera+segunda+(tercera/2)}" y="125" font-size="18" dominant-baseline="middle" text-anchor="middle" fill="#012d4f">TERCERA CLASE</text>`

                } // cierra lo abierto después de complete: function…

            }); // cierra lo abierto después de Papa.parse("https…

        </script>
    </body>
</html>
```


- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-02) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-04)
