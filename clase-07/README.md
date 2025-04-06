### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 07 → 16/04/2025

# Gráficas y datos en diseño web responsive: SVG

### Teoría (para la casa)

Ya hemos avanzado bastante en datos, convendría volver sobre SVG y algunas posibilidades de hacerlo responsive, además de interactivo. 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Séptima clase</title>
        <style>
            * { margin: 0; padding: 0; }

            body { font-family: monospace; }

            article { padding: 1rem; width: min(90%, 500px); margin: 2rem auto; text-align: center; }

            article:nth-child(3){ width: min(90%, 800px); }

            h2 { font-size: 1.5rem; margin: 1.5rem auto; line-height: 1; }

            p { margin:.75rem auto; line-height: 1.5; }

            @keyframes pedrope {
                0% { transform: rotate(0); }
                100% { transform: rotate(360deg); }
            }

            img { display: block; width: 50%; margin: 2rem auto; }

            img.animate { animation: pedrope 2s linear infinite; }
        </style>
    </head>
    <body>
        <article>
            <h2>Del innerHTML al setAttribute</h2>
            <!--usando input type="radio"-->
            <p><input type="radio" name="stroke" value="0.25" onchange="primera(this.value)" /> LIGHT <input type="radio" name="stroke" value="1" checked onchange="primera(this.value)" /> NORMAL
            <input type="radio" name="stroke" value="1.75" onchange="primera(this.value)" /> BOLD</p>
            <!--un svg que tomo de https://feathericons.com/-->
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke-linecap="round" stroke-linejoin="round">
                <rect x="0" y="0" width="24" height="24"></rect>
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
            <img src="https://raw.githubusercontent.com/profesorfaco/opr/refs/heads/main/clase-07/img/mapache.png" />
        </article>
        <article>
            <h2>Y cerremos con un "SVG responsive"</h2> 
            <div></div>           
        </article>
        <script>
            //Partamos por el cierre
            const planetas = document.querySelectorAll("div")[0];

            function cero() {
                var ancho = window.innerWidth;
                var alto = window.innerHeight;
                if (ancho < alto) {
                    planetas.innerHTML = `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 30 150" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke="black">
                        <g id="planetas" stroke-width=".2">
                            <circle cx="15" cy="${10-0.38}" r=".38"></circle>
                            <circle cx="15" cy="${20-0.95}" r=".95"></circle>
                            <circle cx="15" cy="${30-1}" r="1" fill="#1976D2"></circle>
                            <circle cx="15" cy="${40-0.53}" r=".53"></circle>
                            <circle cx="15" cy="${70-11.21}" r="11.21"></circle>
                            <circle cx="15" cy="${100-9.45}" r="9.45"></circle>
                            <circle cx="15" cy="${120-4.01}" r="4.01"></circle>
                            <circle cx="15" cy="${140-3.88}" r="3.88"></circle>
                        </g>
                        <rect x="0" y="0" width="30" height="150" stroke-width="1"></rect>
                    </svg>`;
                } else {
                    planetas.innerHTML = `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 150 30" fill="none" stroke="black">
                        <g id="planetas" stroke-width=".6">
                            <circle cx="${10-0.38}" cy="15" r=".38"></circle>
                            <circle cx="${20-0.95}" cy="15" r=".95"></circle>
                            <circle cx="${30-1}" cy="15" r="1" fill="#1976D2"></circle>
                            <circle cx="${40-0.53}" cy="15" r=".53"></circle>
                            <circle cx="${70-11.21}" cy="15" r="11.21"></circle>
                            <circle cx="${100-9.45}" cy="15" r="9.45"></circle>
                            <circle cx="${120-4.01}" cy="15" r="4.01"></circle>
                            <circle cx="${140-3.88}" cy="15" r="3.88"></circle>
                        </g>
                        <rect x="0" y="0" width="150" height="30" stroke-width="2"></rect>
                    </svg>`;
                }
            }

            cero();
            window.addEventListener("resize", cero);
            
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
                }
            }

        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-06) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-08)
