### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 07 → 16/04/2025

# Gráficas y datos en diseño web responsive: SVG

### Teoría (para la casa)

Ya hemos avanzado bastante en datos, convendría volver sobre el SVG y algunas posibilidades de hacerlo [responsive](https://es.wikipedia.org/wiki/Dise%C3%B1o_web_adaptable), además de interactivo. 

Para lo interactivo, conviene prepararse con:

El subtítulo de **Llamar funciones** en el artículo sobre funciones en MDN: https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Functions#llamar_funciones

La respuesta a la pregunta **¿Qué es un evento?** en el mismo MDN: https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/Events#%C2%BFqu%C3%A9_es_un_evento

La recomendación en el mismo documento ya referido respecto de **Manejadores de eventos en línea**: https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/Events#manejadores_de_eventos_en_l%C3%ADnea_no_los_utilices

- - - - - - - - - - - - - - 

### Práctica (para la clase)

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Séptima clase</title>
        <style>
            [data-theme="light"] { --color-bg: #eceff1; --color-fg: #263238; }

            [data-theme="dark"] { --color-bg: #263238; --color-fg: #eceff1; }

            * { margin: 0; padding: 0; }

            body { font-family: monospace; color: var(--color-fg); background: var(--color-bg); }

            article { padding: 1rem; width: min(90%, 500px); margin: 2rem auto; text-align: center; }

            article:nth-child(3) { width: min(90%, 1000px); margin-bottom: 5rem; }

            h2 { font-size: 1.5rem; margin: 1.5rem auto; line-height: 1; }

            p { margin: 0.75rem auto; line-height: 1.5; }

            input[type="radio"] { accent-color: #232323; }

            @keyframes pedrope {
                0% { transform: rotate(0); }
                100% { transform: rotate(360deg); }
            }

            figure { width: 50%; margin: 2rem auto; background: #fff; }

            img { width: 100%; }

            img.animate { animation: pedrope 2s linear infinite; }

            div.portrait > svg { font-size: 7.5%; stroke-width: 0; fill: white; alignment-baseline: middle; text-anchor: start; display: block; margin:3rem; }

            div.landscape { display: inline-block; }

            div.landscape > svg { width: 10%; font-size: 25%; stroke-width: 0; fill: black; alignment-baseline: middle; text-anchor: middle; }

            div.landscape > svg:nth-child(5) { margin-left:3%; margin-right:4%; }

            div.landscape > svg:nth-child(7) { margin-left:2%; }

            @media (orientation: portrait) {
                div.landscape { display: none; }
            }

            @media (orientation: landscape) {
                div.portrait { display: none; }
            }
        </style>
    </head>
    <body>
        <article>
            <h2>Del innerHTML al setAttribute</h2>
            <!--usando input type="radio"-->
            <p>
                <input type="radio" name="stroke" value="0.25" onchange="primera(this.value)" /> LIGHT <input type="radio" name="stroke" value="1" checked onchange="primera(this.value)" /> NORMAL
                <input type="radio" name="stroke" value="1.75" onchange="primera(this.value)" /> BOLD
            </p>
            <!--un svg que tomo de https://feathericons.com/-->
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke-linecap="round" stroke-linejoin="round">
                <rect x="0.9" y="0.9" width="22.2" height="22.2"></rect>
                <circle cx="12" cy="12" r="10"></circle>
                <path d="M8 14s1.5 2 4 2 4-2 4-2"></path>
                <line x1="9" y1="9" x2="9.01" y2="9"></line>
                <line x1="15" y1="9" x2="15.01" y2="9"></line>
            </svg>
            <!--usando input type="range"-->
            <p><input type="range" min="0" max="359" step="1" value="0" onchange="segunda(this.value)" /></p>
            <p>Stroke: HSL(<span>0</span>,100%,50%)</p>
            <!--usando input type="color"-->
            <p>Fill: <input type="color" value="#FFFFFF" onchange="tercera(this.value)" /></p>
        </article>
        <article>
            <h2>Del setAttribute al AddClass</h2>
            <!--usando input type="checkbox"-->
            <input type="checkbox" name="animado" onchange="cuarta()" /> <label>ANÍMATE, PEDRO</label>
            <figure>
                <img src="https://raw.githubusercontent.com/profesorfaco/opr/refs/heads/main/clase-07/img/mapache.png" />
            </figure>
        </article>
        <article>
            <h2>Y cerremos con "un SVG responsive"</h2>
            <div class="portrait"></div>
            <div class="landscape"></div>
        </article>
        <script>
            // Hay muchos tipos de inputs: https://www.w3schools.com/html/html_form_input_types.asp
            // Acá usaremos cuatro: radio, range, color y checkbox

            function primera(valor) {
                document.querySelectorAll("svg")[0].setAttribute("stroke-width", valor);
            }
            primera(1);

            function segunda(valor) {
                document.querySelectorAll("svg")[0].setAttribute("stroke", "hsl(" + valor + ",100%,50%)");
                document.querySelector("span").innerHTML = valor;
            }
            segunda(0);

            function tercera(valor) {
                document.querySelector("rect").setAttribute("fill", valor);
            }

            function cuarta() {
                if (document.querySelector("input[type=checkbox]").checked == true) {
                    document.querySelector("img").classList.add("animate");
                } else {
                    document.querySelector("img").removeAttribute("class");
                    // también podría borrar la clase, dejando un class vacío
                    // document.querySelector("img").classList.remove("animate");
                }
            }

            async function quinta() {
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/opr/refs/heads/main/clase-07/planetas.json");
                const data = await consulta.json();
                console.log(data);
                const svgMobile = document.querySelectorAll("div.portrait")[0];
                const svgOther = document.querySelectorAll("div.landscape")[0];
                data.forEach((v, i) => {
                    svgMobile.innerHTML += `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 30 ${v.comparado*2}"><circle cx="12" cy="${v.comparado}" r="${v.comparado}" fill="white"></circle><text x="${v.comparado + 13}" y="${v.comparado+0.3}">${v.planeta}</text></svg>`;
                    svgOther.innerHTML += `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 33"><circle cx="12" cy="13" r="${v.comparado}" fill="black"></circle><text x="12" y="30">${v.planeta}</text></svg>`;
                });
            }
            quinta().catch((error) => console.error(error));

            function sexta() {
                var ancho = window.innerWidth;
                var alto = window.innerHeight;
                if (ancho < alto) {
                    document.querySelector("html").setAttribute("data-theme", "dark");
                } else {
                    document.querySelector("html").setAttribute("data-theme", "light");
                }
            }
            sexta();
            window.addEventListener("resize", sexta);
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-06) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-08)
