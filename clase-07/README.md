### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 07 → 16/04/2025

# Gráficas y datos en diseño web responsive: SVG

### Teoría (para la casa)

Ya hemos avanzado bastante en datos, convendría volver sobre el SVG y algunas posibilidades de hacerlo responsive, además de interactivo. 

```
<!DOCTYPE html>
<html lang="es" data-theme="light">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Séptima clase</title>
        <style>
            [data-theme="light"] {
              --color-bg: #fefefe;
              --color-fg: #111;
            }

            [data-theme="dark"] {
              --color-bg: #263238;
              --color-fg: #fff;
            }

            * { margin: 0; padding: 0; }

            body { font-family: monospace; color:var(--color-fg); background:var(--color-bg)}

            article { padding: 1rem; width: min(90%, 500px); margin: 2rem auto; text-align: center; }

            article:nth-child(3) { width: min(90%, 1000px); }

            h2 { font-size: 1.5rem; margin: 1.5rem auto; line-height: 1; }

            p { margin: 0.75rem auto; line-height: 1.5; }

            @keyframes pedrope {
                0% { transform: rotate(0); }
                100% { transform: rotate(360deg); }
            }

            figure{width: 50%; margin: 2rem auto; background: #fff}

            img { width:100% }

            img.animate { animation: pedrope 2s linear infinite; }

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
            <div class="portrait">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 30 140" fill="none">
                    <rect x="0" y="0" width="30" height="140" fill="black"></rect>
                    <g stroke-width=".2" stroke="white">
                    </g>
                </svg>
            </div>
            <div class="landscape">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 270 40" fill="none">
                    <rect x="0" y="0" width="300" height="40" fill="black"></rect>
                    <g stroke-width=".5" stroke="white"></g>
                </svg>
            </div>
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
                const svgMobile = document.querySelectorAll("g")[0];
                const svgOther = document.querySelectorAll("g")[1];
                data.forEach((v, i) => {
                    if (i < 4) {
                        svgMobile.innerHTML += `<circle cx="15" cy="${(i + 1) * 10}" r="${v.comparado}"></circle>`;
                        svgOther.innerHTML += `<circle cx="${(i + 1) * 25}" cy="20" r="${v.comparado}"></circle>`;
                        if (v.comparado == 1) {
                            svgMobile.innerHTML += `<circle cx="15" cy="${(i + 1) * 10}" r="${v.comparado}" fill="white"></circle>`;
                            svgOther.innerHTML += `<circle cx="${(i + 1) * 25}" cy="20" r="${v.comparado}" fill="white"></circle>`;
                        }
                    } else if (i == 4) {
                        svgMobile.innerHTML += `<circle cx="15" cy="${(i + 1) * 12}" r="${v.comparado}"></circle>`;
                        svgOther.innerHTML += `<circle cx="${(i + 1) * 27}" cy="20" r="${v.comparado}"></circle>`;
                    } else if (i == 5) {
                        svgMobile.innerHTML += `<circle cx="15" cy="${(i + 1) * 15}" r="${v.comparado}"></circle>`;
                        svgOther.innerHTML += `<circle cx="${(i + 1) * 29.5}" cy="20" r="${v.comparado}"></circle>`;
                    } else  {
                        svgMobile.innerHTML += `<circle cx="15" cy="${(i + 1) * 16}" r="${v.comparado}"></circle>`;
                        svgOther.innerHTML += `<circle cx="${(i + 1) * 30}" cy="20" r="${v.comparado}"></circle>`;
                    }
                });
            }
            quinta().catch((error) => console.error(error));

            function sexta(){
                var ancho = window.innerWidth;
                var alto = window.innerHeight;
                if(ancho < alto){
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
