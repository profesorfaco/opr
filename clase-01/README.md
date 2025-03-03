### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 01 → 05/03/2025

# Datos e información

### Teoría (para la casa)

El título dice, entre paréntesis, “para la casa”. La razón de lo dicho está en la apuesta por el aprendizaje invertido. La explicación de la apuesta la encuentran en esta página del [Centro de Desarrollo Docente UC](https://desarrollodocente.uc.cl/servicios/asesorias-personalizadas/metodologias-innovadoras/aprendizaje-invertido/). Pero, en su apuesta, este optativo hace un ajuste: No se basa en videos de contenido, sino en hipertexto que, en algunas clases, podría vincular a videos.

--------

En este optativo es necesario que, en su partida, cada estudiante pueda leer-comprender lo que sigue: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Primer ejemplo</title>
        <!-- Usando CSS Grid Generator - https://cssgridgenerator.io/ -->
        <style>
            .parent {
                display: grid;
                grid-template-columns: repeat(2, 1fr);
                grid-template-rows: repeat(1, 1fr);
                gap: 0px;
            }
        </style>
    </head>
    <body>
        <div class="parent">
            <div class="div1">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
                    <g id="primera"></g>
                </svg>
            </div>
            <div class="div2">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
                    <g id="segunda"></g>
                </svg>
            </div>
        </div>
        <script>
            const data = [50, 10];
            let cero = document.querySelector("#primera");
            cero.innerHTML = `<circle cx="50" cy="50" r="${data[0]}" />`;
            let uno = document.querySelector("#segunda");
            uno.innerHTML = `<circle cx="50" cy="50" r="${data[1]}" />`;
        </script>
    </body>
</html>
```
Si se lo comprende, podremos dar el primer paso concentrándonos en la variable-constante `data`, a la que se le asigna un arreglo con **dos números enteros que, de momento, no tienen sentido**: No tenemos su origen ni su destino, pero los tenemos a la vista siendo el primero, convencionalmente, cinco veces el segundo.

Examinemos lo del párrafo anterior, partiendo por las primeras acepciones de *data*, en inglés:

- [plural in form but singular or plural in construction] *factual information (such as measurements or statistics) used as a basis for reasoning, discussion, or calculation* —Merrian-Webster Dictionary.

- [uncountable, plural] *facts or information, especially when examined and used to find out things or to make decisions* —Oxford dictionary.

50 y 10 no nos permiten razonamiento, discusión, cálculo, descubrimiento ni toma de decisión más allá de la convencional multiplicación. Convencional porque nos exige adoptar convenios o pactos sobre símbolos como números y operaciones matemáticas. No es un hecho (*fact*) que 50 sea 5 veces 10. Si es un convenio o pacto adoptado (ver convenional en [RAE](https://dle.rae.es/convencional)).

Falta conectar a 50 y 10 con un *fact* para tener *data*. Esa conexión exige un camino, y el camino debería tener un sentido tal como en el tránsito; hay un sentido en el estar dirigido para poder recortar “algo” que siempre está en el medio de algo más, que forma parte de un “campo” (Merleau-Ponty, 2010).

Pero no es tan conveniente profundizar ahora en cuestiones "fenomenológicas". Sí es conveniente revisar la idea del DIKW (Data → Information → Knowledge → Wisdom) en cualquiera de los siguientes artículos:

- Frické, M. H. (2018). Data-information-knowledge-wisdom (DIKW) pyramid, framework, continuum. Encyclopedia of big data, 1-4 → https://link.springer.com/referenceworkentry/10.1007/978-3-319-32001-4_331-1
  
- Peters, M. A., Jandrić, P., & Green, B. J. (2024). *The DIKW model in the age of artificial intelligence*. Postdigital science and education, 1-10 → https://www.researchgate.net/publication/378527476_The_DIKW_Model_in_the_Age_of_Artificial_Intelligence

- Weinberger, D. (2010). *The Problem with the Data-Information-Knowledge-Wisdom Hierarchy*. Harvard
Business Review → https://hbr.org/2010/02/data-is-to-info-as-info-is-not

La lectura de cualquiera de tales artículo le servirá a cada estudiante para comenzar a trabajar un concepto propio de información, que es lo que luego diseñará teniendo a la base lenguajes como las que ya se muestran en el código de más arriba.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Generemos 4 Gráficos de Dónut en una página web, donde se comparen la distribución del un 100% entre dos grupos. 

Tomemos números del INE (Instituto Nacional de Estadísticas). Podríamos aprovechar sus [Estadísticas > Demografía y vitales > Estadísticas vitales](https://www.ine.gob.cl/estadisticas/sociales/demografia-y-vitales/nacimientos-matrimonios-y-defunciones) > Cuadros estadísticos > 2024 > Estadísticas vitales cifras coyunturales diciembre 2024.

De allí se pueden tomar 4 pares de datos, donde ambos sumen 100, para luego aprovechar el siguiente código:

```
<svg width="100%" height="100%" viewBox="0 0 42 42" class="donut">
  <circle class="donut-hole" cx="21" cy="21" r="15.91549430918954" fill="#fff"></circle>
  <circle class="donut-ring" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#d2d3d4" stroke-width="3"></circle>
  <circle class="donut-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#ce4b99" stroke-width="3" stroke-dasharray="85 15" stroke-dashoffset="0"></circle>
</svg>
```

Tal código se encuentra en el *post*: [Scratch-made SVG Donut & Pie Charts in HTML5](https://heyoka.medium.com/scratch-made-svg-donut-pie-charts-in-html5-2c587e935d72).

A tal referencia, conviene sumar: 

- https://datavizcatalogue.com/ES/metodos/grafico_de_donut.html

- https://cssgridgenerator.io/

- https://mozilladevelopers.github.io/playground/css-grid/04-fr-unit/

Los resultados deben publicarse en un repositorio de GitHub, activando GitHub Pages y luego ingresando la URL de su página web operativa en un foro de canvas por crearse.

- - - - - - - 

###### [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-02)
