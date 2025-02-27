### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 02 → 12/03/2025

# Datos e información en gráficas (primera parte)

### Teoría (para la casa)

**Retomemos las ideas compartidas la clase recién pasada, mediante tres citas**.

La primera la tomamos de *Ética para Celia*, de Ana de Miguel (2021, p.117): 

> Una vez más, diremos, sin resentimiento pero cargadas de razones y con Adrienne Rich, que «objetividad» es el nombre que se da a la «subjetividad masculina». 

La segunda cita la tomamos de *Después del método : Desorden en la investigación en ciencias sociales*, de John Law (2020,pp.21-22):

> Sin duda, las estructuras locales se pueden identificar, pero, o eso quiero argumentar, el mundo en general desafía cualquier intento de contabilización completa y ordenada. El mundo no debe ser entendido mediante la adopción de una versión metodológica de la auditoría. Las regularidades y las estandarizaciones son herramientas increíblemente poderosas, pero establecen límites. Esa es una parte de su poder (de doble filo).

La tercera y última la tomamos de [*Feminismo de Datos*](https://data-feminism.mitpress.mit.edu/pub/tzq8d54o/release/1?readingCollection=b371d820), de Catherine D’Ignazio y Lauren F. Klein (2020):

> «Lo que se cuenta, cuenta», ha afirmado la geógrafa feminista Joni Seager […] Lo que se cuenta –como ser varón o mujer– suele ser la base de la elaboración de políticas y la asignación de recursos. Por el contrario, lo que no se cuenta –como ser no binario– se vuelve invisible.

**Tales citas invitan a sospechar de lo que se presenta como dato objetivo, o dato duro, que captura la realidad**.

A propósito de realidad conviene sumar una cuarta cita, que tomamos de *La Objetividad, una argumentos para obligar*, de Humberto Maturana (2007,p.40):

> [L]a realidad surge como una proposición explicativa de nuestra experiencia de las coherencias operacionales en nuestra vida diaria y técnica, como las vivimos en nuestra vida técnica y diaria.

La sospecha debe ser incluida en la base de la pirámide DIKW (Data → Information → Knowledge → Wisdom), pirámide con la que ya pudieron –y aún pueden– relacionarse, por vía de los artículos:

- van Meter, H. J. (2020). Revising the DIKW pyramid and the real relationship between data, information, knowledge, and wisdom. Law, Technology and Humans, 2(2), 69–80. https://search.informit.org/doi/10.3316/agispt.20210112042035

- McDowell, K. (2021). Storytelling wisdom: Story, information, and DIKW. JASIST, Journal of the ASsociation for Information Science and Technology, 72 (10), 1223-1233. https://asistdl.onlinelibrary.wiley.com/doi/full/10.1002/asi.24466

**Hecha la vinculación con la clase previa, sobre [Datos e información](https://github.com/profesorfaco/opr/tree/main/clase-01#readme), conviene avanzar a las gráficas**.

Y nos referiremos, primero, a las gráficas que se describen en las palabras de Gottfried Boehm, que tomamos de su *¿Más allá del lenguaje? Apuntes sobre la lógica de las imágenes*, según son traducidas por Antonio de la Cruz Valles y Ana Garcia Varas, para el libro Filosofía de la Imagen (García Varas, 2011):

> Surgió, bien entrada la segunda mitad del siglo XVIII, la forma de imagen cognitiva de mayor éxito y que hoy todavía es omnipresente: **la gráfica**. La gráfica es a menudo, y pese a su fuerte connotación cognitiva, una verdadera imagen, porque permite visualizar grandes magnitudes abstractas de un modo casi inimaginable. Traslada lo abstracto (por ejemplo, los datos sobre el volumen de intercambio, de tonelaje, de bienes, de frecuencias en relación con un intervalo temporal, etc.) a una configuración visual que *muestra* lo que nunca podría verse sin más en columnas de números. Con la gráfica la representación estadística se transformó radicalmente, al convertir la cantidad estadística en una cualidad visible. La condición de esto es que el campo de la imagen no se ha de considerar solo como una superficie estructurada, sino como una función de coordenadas *x* e *y*, la abscisa y la ordenada, cuya relación matemática se muestra mediante la «solución» sobre el plano.

La palabra que en el español es *gráfica*, en su original alemán es *Diagramm*: 

> Jahrhunderts die erfolgreichste und bis heute omnipräsente kognitive Bildform, nämlich **das Diagramm**. Diagramme sind oftmals starke, wenn auch betont kognitive Bilder, weil sie eine ganz unglaubliche Veranschaulichung abstrakter Zahlengrössen zustande bringen können. Sie versetzen das Abstrakteste, zum Beispiel Angaben über Handelsvolumen, Tonnage, Güter, Frequenzen in Bezug auf Zeitspannen etc. in eine visuelle Konfiguration, die *zeigt*, was man aus blassen Zahlenkolonnen niemals lesen könnte. Mit dem Diagramm verändert sich die Darstellung von Statistiken grundlegend. Das statistische Quantum springt um in ein anschauliches Quale. Voraussetzung war, dass das Bildfeld nicht nur als gegliederte Fläche, sondern als Funktion der Koordinaten x und y, also von Abszisse und Ordinate, betrachtet wurde, deren jeweilige mathematische Beziehung sich als »Lösung« auf der Fläche verbildlicht

Tanto en la traducción como en el original, se acompaña a las palabras con una gráfica/Diagramm producida por [William Playfair](https://es.wikipedia.org/wiki/William_Playfair) en la década de 1780, muy similar a la que se encuentra en [Wikicommons](https://commons.wikimedia.org/wiki/File:Playfair_TimeSeries-2.png), donde este ejemplo de gráfica/Diagramm se etiqueta con la palabra *chart*, misma palabra que Playfair utiliza en algunos títulos de láminas en *The Commercial and Politica Atlas* (1786) y *Statical Breviary* (1801), publicaciones que contienen los primeros usos de [gráficas de barras](https://datavizcatalogue.com/ES/metodos/graficos_de_barras.html), [línea](https://datavizcatalogue.com/ES/metodos/grafica_de_linea.html) y [tarta](https://datavizcatalogue.com/ES/metodos/graficos_de_tarta.html), gráficas donde el sistema de coordenadas cartesianas, usado habitualmente en los mapas, se adapta para *visualizar* lo cuantitativo.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Intentemos generar los tres tipos de gráficos referidos arriba, partiendo con el siguiente código en un `index.html`:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Podríamos usar Bootstrap</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous" />
    </head>
    <body>
        <div class="container-fluid m-0 p-0">
            <div class="row">
                <div class="col-12 p-5 text-center">Título</div>
            </div>
            <div class="row g-0" style="height: 75vh;" id="tartas"></div>

            <div class="row">
                <div class="col-12 p-5 text-center">Título</div>
                <div class="col-12 p-5 text-center">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 500">
                        <g transform="translate(0,500) scale(1,-1)" id="lineas"></g>
                        <g id="years"></g>
                    </svg>
                </div>
                <div class="col-12 p-5 text-center">Título</div>
                <div class="col-12 p-5 text-center">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 200" id="barras"></svg>
                </div> 
            </div>
        </div>
        <script>
            // PRIMER GRÁFICO

            // Datos en tarta fueron tomados de la síntesis de resultados censo 2017

            const tarta = [
                {region: "País", mujer: 51.1, hombre: 48.9},
                { region: "Aysén", mujer: 52, hombre: 48 },
                { region: "Biobío", mujer: 48.3, hombre: 51.7 },
            ];

            const graficaTarta = document.querySelector("#tartas");

            tarta.forEach((d) => {
                graficaTarta.innerHTML += `<div class="col h-100 d-flex align-items-center justify-content-center"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 40 40"><circle class="donut-hole" cx="20" cy="20" r="15.91549430918954" fill="#fff"></circle><circle class="donut-ring" cx="20" cy="20" r="15.91549430918954" fill="transparent" stroke="blue" stroke-width="3"></circle><circle class="donut-segment" cx="20" cy="20" r="15.91549430918954" fill="transparent" stroke="red" stroke-width="3" stroke-dasharray="${d.mujer} ${100 - d.mujer}" stroke-dashoffset="25"></circle><text x="20" y="20" font-size="3" text-anchor="middle">${d.region}</text></svg></div>`;
            });

            //SEGUNDO GRÁFICO

            // datos en lineal fueron tomados de https://es.wikipedia.org/wiki/Anexo:Crecimiento_poblacional_de_Santiago_de_Chile

            const lineal = {
                censos: [1820, 1854, 1865, 1888, 1920, 1940, 1952, 1960, 1982, 1992, 2002, 2012],
                censados: [46000, 69018, 115337, 256000, 507296, 952075, 1350409, 1907378, 3899619, 4729118, 5428590, 7057491],
            };

            
            const graficaLineas = document.querySelector("#lineas");

            // con algo de complicaciones que se pueden resolver googleando https://stackoverflow.com/questions/39560206/change-0-0-from-svg

            let coordenadas = "";

            let momentos = ""

            lineal.censados.forEach((d, i) => {
                coordenadas += i*50 + "," + Math.round(d*0.0001) + " ";
                momentos += `<text x="${i*50}" y="480" font-size="5">${lineal.censos[i]}</text> `;
    
            })

            console.log(coordenadas);

            console.log(momentos);

            graficaLineas.innerHTML += `<polyline points="${coordenadas}" fill="none" stroke="black"/>`;

            document.querySelector("#years").innerHTML += momentos;

            // TERCER GRÁFICO 

            // datos en barras los ponen ustedes

            const barras = [
                    {region:"Metropolitana", numero:8420729},
                    {region:"Valparaíso", numero:2010849},
                    {region:"Biobío", numero:1681225},
                    {region:"otras", numero:7848086}
                ]

            const graficaBarras = document.querySelector("#barras");

            // AHORA ARMAREMOS LAS BARRAS

            barras.forEach((d, i) => {
            graficaBarras.innerHTML += `<g transform="translate(0,${i*50})">
                <rect x="10" y="10" width="${d.numero/500000}" height="10" />
                <text x="10" y="10" fill="white">${d.region}</text>
                <text x="10" y="${d.numero/500000}">${d.numero}</text>
            </g>`
            });
        </script>
    </body>
</html>
```

Después de las 13.30 hrs. seguí trabajando en el código desde el que ustedes pudieron partir, guardando como `index.html`

Hice varios ajustes de "legibilidad" que no alcancé a hacer en la (interrumpida) práctica de hoy. 

Lo ajustado lo pueden ver en: https://profesorfaco.github.io/opr/clase-02

No es necesario que su trabajo a publicar (o ya publicado) en GitHub se base en lo ajustado. 

Bien puede basarse en el mismo código de partida de unas líneas más arriba.

Lo importante es no olvidar dejar constancia, durante el día, de su publicación en GitHub mediante una entrada en este foro de discusión: https://cursos.canvas.uc.cl/courses/73175/discussion_topics/749338


- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-01) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-03)
