### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 02 → 12/03/2025

# Datos e información en gráficas (primera parte)

### Teoría (para la casa)

**Retomemos las ideas compartidas la clase recién pasada, mediante tres citas**.

Partamos por *The DIKW model in the age of artificial intelligence*, de Peters, Jandrić & Green:

> Recognizing the limitations of the DIKW model […] encourages humility in our pursuit of understanding, acknowledging that the path to wisdom is nuanced and multifaceted.

Agreguemos cita a la *Ética para Celia*, de Ana de Miguel (2021, p.117): 

> Una vez más, diremos, sin resentimiento pero cargadas de razones y con Adrienne Rich, que «objetividad» es el nombre que se da a la «subjetividad masculina». 

Y cerremos con una tercera cita, que  tomamos de [*Feminismo de Datos*](https://data-feminism.mitpress.mit.edu/pub/tzq8d54o/release/1?readingCollection=b371d820), de Catherine D’Ignazio y Lauren F. Klein (2020):

> «Lo que se cuenta, cuenta», ha afirmado la geógrafa feminista Joni Seager […] Lo que se cuenta –como ser varón o mujer– suele ser la base de la elaboración de políticas y la asignación de recursos. Por el contrario, lo que no se cuenta –como ser no binario– se vuelve invisible.

**Tales citas invitan a sospechar de la "captura de realidad" ofrecida por cada dato objetivo o dato duro**.

A propósito de realidad conviene sumar una cuarta cita, que tomamos de *La Objetividad, una argumentos para obligar*, de Humberto Maturana (2007,p.40):

> [L]a realidad surge como una proposición explicativa de nuestra experiencia de las coherencias operacionales en nuestra vida diaria y técnica, como las vivimos en nuestra vida técnica y diaria.

La sospecha debe ser incluida en la base de la pirámide DIKW (Data → Information → Knowledge → Wisdom), pirámide con la que ya pudieron –y aún pueden– relacionarse, por vía de los artículos:

- Baskarada, S. & Koronios, A. (2013). Data, Information, Knowledge, Wisdom (DIKW): A Semiotic Theoretical and Empirical Exploration of the Hierarchy and its Quality Dimension → https://doi.org/10.3127/ajis.v18i1.748

- Peters, M. A., Jandrić, P., & Green, B. J. (2024). *The DIKW model in the age of artificial intelligence*. Postdigital science and education, 1-10. https://www.researchgate.net/publication/378527476_The_DIKW_Model_in_the_Age_of_Artificial_Intelligence

- van Meter, H. J. (2020). *Revising the DIKW pyramid and the real relationship between data, information, knowledge, and wisdom*. Law, Technology and Humans, 2(2), 69–80. https://search.informit.org/doi/10.3316/agispt.20210112042035

**Hecha la vinculación con la clase previa, sobre [Datos e información](https://github.com/profesorfaco/opr/tree/main/clase-01#readme), conviene avanzar a las gráficas**.

Y nos referiremos, primero, a las gráficas que se describen en las palabras de Gottfried Boehm, que tomamos de su *¿Más allá del lenguaje? Apuntes sobre la lógica de las imágenes*, según son traducidas por Antonio de la Cruz Valles y Ana Garcia Varas, para el libro Filosofía de la Imagen (García Varas, 2011):

> Surgió, bien entrada la segunda mitad del siglo XVIII, la forma de imagen cognitiva de mayor éxito y que hoy todavía es omnipresente: **la gráfica**. La gráfica es a menudo, y pese a su fuerte connotación cognitiva, una verdadera imagen, porque permite visualizar grandes magnitudes abstractas de un modo casi inimaginable. Traslada lo abstracto (por ejemplo, los datos sobre el volumen de intercambio, de tonelaje, de bienes, de frecuencias en relación con un intervalo temporal, etc.) a una configuración visual que *muestra* lo que nunca podría verse sin más en columnas de números. Con la gráfica la representación estadística se transformó radicalmente, al convertir la cantidad estadística en una cualidad visible. La condición de esto es que el campo de la imagen no se ha de considerar solo como una superficie estructurada, sino como una función de coordenadas *x* e *y*, la abscisa y la ordenada, cuya relación matemática se muestra mediante la «solución» sobre el plano.

La palabra que en el español es *gráfica*, en su original alemán es *Diagramm*: 

> Jahrhunderts die erfolgreichste und bis heute omnipräsente kognitive Bildform, nämlich **das Diagramm**. Diagramme sind oftmals starke, wenn auch betont kognitive Bilder, weil sie eine ganz unglaubliche Veranschaulichung abstrakter Zahlengrössen zustande bringen können. Sie versetzen das Abstrakteste, zum Beispiel Angaben über Handelsvolumen, Tonnage, Güter, Frequenzen in Bezug auf Zeitspannen etc. in eine visuelle Konfiguration, die *zeigt*, was man aus blassen Zahlenkolonnen niemals lesen könnte. Mit dem Diagramm verändert sich die Darstellung von Statistiken grundlegend. Das statistische Quantum springt um in ein anschauliches Quale. Voraussetzung war, dass das Bildfeld nicht nur als gegliederte Fläche, sondern als Funktion der Koordinaten x und y, also von Abszisse und Ordinate, betrachtet wurde, deren jeweilige mathematische Beziehung sich als »Lösung« auf der Fläche verbildlicht

Tanto en la traducción como en el original, se acompaña a las palabras con una gráfica/Diagramm producida por [William Playfair](https://es.wikipedia.org/wiki/William_Playfair) en la década de 1780, muy similar a la que se encuentra en [Wikicommons](https://commons.wikimedia.org/wiki/File:Playfair_TimeSeries-2.png), donde este ejemplo de gráfica/Diagramm se etiqueta con la palabra *chart*, misma palabra que Playfair utiliza en algunos títulos de láminas en *The Commercial and Politica Atlas* (1786) y *Statical Breviary* (1801), publicaciones que contienen los primeros usos de 

- [gráficas de barras](https://datavizcatalogue.com/ES/metodos/graficos_de_barras.html) y

- [línea](https://datavizcatalogue.com/ES/metodos/grafica_de_linea.html).

gráficas donde el sistema de coordenadas cartesianas, usado habitualmente en los mapas, se adapta para *visualizar* lo cuantitativo.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Intentemos generar los tres tipos de gráficos referidos arriba, partiendo con el siguiente código en un `index.html`:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Sigamos usando Bootstrap</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    </head>
    <body>
        <div class="container-fluid m-0 p-0">
            <div class="row">
                <div class="col-12 p-5 pb-1 text-center">
                    <h5>Comparación de áreas urbanas y rurales en distintas regiones</h5>
                    <p>Con tres gráficas de tarta, para un promedio y dos extremos en la relación de población por área urbana-rural</p>
                </div>
            </div>
            <div class="row g-0 bg-light" style="height: 75vh;" id="tartas"><!--aquí dentro va crean unas divisiones, cada división contiene un svg--></div>
            <div class="row">
                <div class="col-12 p-5 pb-1 text-center">
                    <h5>Evolución en el tiempo de la población en la Región Metrolitana Chilena</h5>
                    <p>Con una gráfica de líneas</p>
                </div>
                <div class="col-12 p-5 text-center bg-light">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 570 210">
                        <g transform="translate(0,195) scale(1,-1)" id="lineas"><!--aquí dentro va la polyline--></g>
                        <g id="years"><!--aquí dentro van los textos con los años--></g>
                    </svg>
                </div>
                <div class="col-12 p-5 pb-1 text-center">
                    <h5>Población en las distintas regiones de Chile</h5>
                    <p>Con una gráfica de barras</p>
                </div>
                <div class="col-12 p-5 text-center bg-light">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 55" id="barras"><!--aquí dentro van los grupos con rectangulo y textos--></svg>
                </div> 
            </div>
        </div>
        <script>
            // PRIMERA GRÁFICA
            // Datos en tarta fueron tomados de la síntesis de resultados censo 2017
            // Noten que cambie categorías y valores, para acercarme a algo más "perceptible"

            const tarta = [
                {region: "País", urbano: 83.3, rural: 16.7},
                { region: "Metropolitana", urbano: 96.3, rural: 3.7 },
                { region: "Ñuble", urbano: 69.4, rural: 30.6 },
            ];

            const graficaTarta = document.querySelector("#tartas");

            tarta.forEach((d) => {
                graficaTarta.innerHTML += `<div class="col h-100 d-flex align-items-center justify-content-center"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 40 40"><circle class="donut-hole" cx="20" cy="20" r="15.91549430918954" fill="#fff"></circle><circle class="donut-ring" cx="20" cy="20" r="15.91549430918954" fill="transparent" stroke="silver" stroke-width="3"></circle><circle class="donut-segment" cx="20" cy="20" r="15.91549430918954" fill="transparent" stroke="#777" stroke-width="3" stroke-dasharray="${d.rural} ${100 - d.rural}" stroke-dashoffset="25"></circle><text x="20" y="20" font-size="2" text-anchor="middle">${d.region}</text></svg></div>`;
            });

            //SEGUNDA GRÁFICA

            // Datos en lineal fueron tomados de https://es.wikipedia.org/wiki/Anexo:Crecimiento_poblacional_de_Santiago_de_Chile

            const lineal = {
                censos: [1820, 1854, 1865, 1888, 1920, 1940, 1952, 1960, 1982, 1992, 2002, 2012],
                censados: [46000, 69018, 115337, 256000, 507296, 952075, 1350409, 1907378, 3899619, 4729118, 5428590, 7057491],
            };

            const graficaLineas = document.querySelector("#lineas");

            let coordenadas = "";

            let momentos = ""

            // la manera de despliegue de las coordenadas del Eje Y nos exige un ajuste, que copiamos de https://stackoverflow.com/questions/39560206/change-0-0-from-svg

            lineal.censados.forEach((d, i) => {
                coordenadas += ((i*50)+7) + "," + Math.round(d*0.000025) + " ";
                momentos += `<text x="${i*50}" y="205" font-size="5">${lineal.censos[i]}</text> `;
    
            })

            console.log(coordenadas);

            console.log(momentos);

            graficaLineas.innerHTML += `<polyline points="${coordenadas}" fill="none" stroke="black" stroke-width="0.5"/>`;

            document.querySelector("#years").innerHTML += momentos;


            // TERCERA GRÁFICA 

            // Datos para las barras fueron tomados de https://es.wikipedia.org/wiki/Anexo:Regiones_de_Chile_por_poblaci%C3%B3n

            const barras = [
                    {region:"Metropolitana", numero:8420729},
                    {region:"Valparaíso", numero:2010849},
                    {region:"Biobío", numero:1681225},
                    {region:"Demás regiones", numero:7848086}
                ]

            const graficaBarras = document.querySelector("#barras");

            barras.forEach((d, i) => {
                graficaBarras.innerHTML += `<g transform="translate(0,${i*15})">
                    <rect x="0" y="0" width="${d.numero/20000}" height="10" />
                    <text x="3" y="7" fill="white" font-size="4">${d.region}</text>
                    <text x="${(d.numero/20000)+3}" y="7" font-size="4">${new Intl.NumberFormat("es-ES").format(d.numero)} habitantes</text>
                </g>`
            });
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-01) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-03)
