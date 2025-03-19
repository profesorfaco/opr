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
        <title>Datos e información en gráficas</title>
        <style>
            body {
                font-family: Helvetica, Arial, sans-serif;
                text-align: center;
            }
            div {
                margin: 2vh 25vw 5vh 25vw;
            }

            @media (orientation: portrait) {
                div {
                    margin: 2vh 2vw 3vh 2vw;
                }
            }

            div > svg {
                margin: 1rem;
            }

            div > p {
                margin: 1rem;
            }
        </style>
    </head>
    <body>
        <div>
            <svg viewBox="0 0 100 100">
                <defs>
                    <clipPath id="clipping">
                        <path
                            d="M94.53,5.54V94.46H73.74l-1.85-6.15H88.38V11.69H49.75V29.4c-10.94,0-16.6,5-19.55,16.6l-1.73,6.64c-1.1,4.43,1.36,8.25,6.15,8.25H37l-1.47,6H30.44c-4.06,0-6.39,1.36-7.62,5l-3,8.85H46.31l3.44-3.32v17H5.47V5.54ZM66.36,88.31l1.84,6.15H59.35l-1.72-6.15L50,62.61H48.52L46.31,74.17l-3.44,3H25.28l1.23-3.81A3.87,3.87,0,0,1,30.2,70.6h8.11l7-29.76c-2.83.73-4.31,2.83-5.29,7l-1.73,7A3.26,3.26,0,0,1,35,57.69a3.1,3.1,0,0,1-2.83-4.06l1.73-6.77c2.58-10.08,7.25-13.77,17.22-13.77,7.75,0,11.81,3.32,10.08,11.19L57.75,59.9Zm-2.09-67.4c0,2.95,0,7.63-.86,9-.37.61-1.85,1.6-4.55,1.6-2.46,0-4.06-1-4.43-1.6-.86-1.48-1.11-6.27-1.11-9.23a3.11,3.11,0,0,1,.74-2.46,6.57,6.57,0,0,1,4.8-1.84,7.32,7.32,0,0,1,4.79,1.84C64.27,18.7,64.27,19.56,64.27,20.91Zm6.89,39a9.47,9.47,0,0,1-2.59-.49l-6.89-2L63,50.92l8.61,2.34a3.37,3.37,0,0,1-.49,6.64Z"
                        />
                    </clipPath>
                </defs>
                <image height="100%" width="100%" preserveAspectRatio="xMinYMin slice" xlink:href="https://www.guemil.info/wp-content/themes/guemil_fondart/img/bg-1.png" clip-path="url(#clipping)" />
            </svg>

            <p>
                Usando <a href="https://www.guemil.info/" target="_blank">Guemil</a> para una doble representación; el <a href="https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths" target="_blank">path</a> que recorta es una
                representación y la <a href="https://developer.mozilla.org/en-US/docs/Web/SVG/Element/image" target="_blank">image</a> recortada es otra.
            </p>

            <svg viewBox="0 0 42 42">
                <circle cx="21" cy="21" r="15.91549430918954" fill="#fff"></circle>
                <circle cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#ddd" stroke-width="2"></circle>
                <circle class="donut-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#FE4300" stroke-width="2" stroke-dasharray="79 21" stroke-dashoffset="25"></circle>
                <text x="50%" y="29" dominant-baseline="middle" text-anchor="middle" font-size="6" fill="#FE4300">79%</text>
                <image x="15" y="10" width="12" height="12" xlink:href="https://raw.githubusercontent.com/Guemil/Guemil_Icons_v15_2020/main/svg/09_Emergency_exit_v15.svg"></image>
            </svg>

            <p>
                Entre las personas consultadas, un 79% refiere a la semejanza de lo visto con una salida de emergencia ya vista (lo que se está representando). El dato de éxito de la referencia también se podría presentar, si se aproxima a
                8 en 10, como sigue:
            </p>

            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 160 16" id="personas"></svg>

            <p>En la presentación gráfica del dato de 8 en 10 se utilizó un <a href="https://datavizcatalogue.com/ES/metodos/grafico_de_pictogramas.html" target="_blank">Gráfico de pictogramas</a></p>
        </div>
        <script>
            for (let x = 0; x < 10; x++) {
                if (x < 8) {
                    document.querySelector("#personas").innerHTML += `<path d="M3 14s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1zm5-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6" fill="#FE4300" transform ="translate(${x * 16} 0)"/>`;
                } else {
                    document.querySelector("#personas").innerHTML += `<path d="M3 14s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1zm5-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6" fill="#ddd" transform ="translate(${x * 16} 0)"/>`;
                }
            }
        </script>
    </body>
</html>
```


- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-02) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-04)
