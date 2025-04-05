### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 07 → 16/04/2025


# Gráficas y datos en diseño web responsive: SVG

### Teoría (para la casa)

Ya hemos avanzado bastante en datos, convendría volver sobre SVG y algunas posibilidades de hacerlo interactivo.

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
            div { padding: 10px; width: min(90%, 500px); margin: 10px auto; text-align: center; }
            div svg { margin: 2rem; }
            h2 {font-size: 1.5rem; margin: 10vh 0 2vh 0;   }
            p { font-size: 1.25rem; }     
            @keyframes pedrope{ 0%{transform:rotate(0)} 100%{transform:rotate(360deg)}}  
            img{ display:block; width:50%; margin:2rem auto 4rem auto;}
            img.animate { animation: pedrope 2s linear infinite; }
            aside{background:#eee; border:3px solid black; margin:1rem 2rem; padding:1rem;}
            .escondido{opacity:0;}
        </style>
    </head>
    <body>
        <div>
            <h2>Del innerHTML al setAttribute</h2>
            <!--usando input type="radio"-->
            <input type="radio" name="stroke" value="0.25" onchange="primera(this.value)" /> LIGHT <input type="radio" name="stroke" value="1" checked onchange="primera(this.value)" /> NORMAL <input type="radio" name="stroke" value="1.75" onchange="primera(this.value)" /> BOLD 
            <!--un svg que tomo de https://feathericons.com/-->
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke-linecap="round" stroke-linejoin="round">
                <rect x="0" y="0" width="24" height="24"></rect>
                <circle cx="12" cy="12" r="10"></circle>
                <path d="M8 14s1.5 2 4 2 4-2 4-2"></path>
                <line x1="9" y1="9" x2="9.01" y2="9"></line>
                <line x1="15" y1="9" x2="15.01" y2="9"></line>
            </svg>
            <!--usando input type="range"-->
            <input type="range" min="0" max="359" step="1" value="0" onchange="segunda(this.value)" />
            <p>Stroke: HSL(<span>0</span>,100%,50%)</p>
            <!--usando input type="color"-->
            <p>Fill: <input type="color" value="#FFFFFF" onchange="tercera(this.value)" ></p>
            <h2>Del setAttribute al AddClass</h2>
            <!--usando input type="checkbox"-->
            <input type="checkbox" name="animado" onchange="cuarta()"> <label>ANÍMATE, PEDRO</label>
            <img src="https://raw.githubusercontent.com/profesorfaco/opr/refs/heads/main/clase-07/img/mapache.png">
            <aside>
                <!--usando select-->
                <select onchange="quinta(this.value)">
                    <option value="0">Tierra y Mercurio</option>
                    <option value="1">Tierra y Venus</option>
                    <option value="2">Tierra y Marte</option>
                    <option value="3">Tierra y Júpiter</option>
                    <option value="4">Tierra y Saturno</option>
                    <option value="5">Tierra y Urano</option>
                    <option value="6">Tierra y Neptuno</option>
                </select>
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 48 24" stroke-width=".25" stroke="black" fill="none">
                    <circle cx="12" cy="12" r="1"></circle>
                    <g id="planetas">
                        <circle cx="36" cy="12" r=".38" class="escondido"></circle>
                        <circle cx="36" cy="12" r=".95" class="escondido"></circle>
                        <circle cx="36" cy="12" r=".53" class="escondido"></circle>
                        <circle cx="36" cy="12" r="11.21" class="escondido"></circle>
                        <circle cx="36" cy="12" r="9.45" class="escondido"></circle>
                        <circle cx="36" cy="12" r="4.01" class="escondido"></circle>
                        <circle cx="36" cy="12" r="3.88" class="escondido"></circle>
                    </g>
                </svg>
            </aside>
        </div>
        <script>
            // Hay muchos tipos de inputs: https://www.w3schools.com/html/html_form_input_types.asp
            // Acá usaremos cuatro: radio, range, color y checkbox; también usaremos el select
            function primera(valor) {
                document.querySelectorAll("svg")[0].setAttribute("stroke-width", valor);
            }
            primera(1);

            function segunda(valor) {
                document.querySelectorAll("svg")[0].setAttribute("stroke", "hsl(" + valor + ",100%,50%)");
                document.querySelector("span").innerHTML = valor;
            }
            segunda(0);

            function tercera(valor){
                document.querySelector("rect").setAttribute("fill", valor);

            }

            function cuarta(){
                if(document.querySelector("input[type=checkbox]").checked == true){
                    document.querySelector("img").classList.add("animate");
                }else{
                    document.querySelector("img").removeAttribute("class");
                }
            }

            function quinta(valor){
                var circulos = document.querySelectorAll("#planetas > circle");
                for (let x = 0; x < 8; x++){
                    if (x == valor){
                        circulos[x].removeAttribute("class");
                    } else {
                        circulos[x].classList.add("escondido");
                    } 
                }
            }
            quinta(0);

        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-06) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-08)
