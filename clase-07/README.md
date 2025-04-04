### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 07 → 16/04/2025


# Gráficas y datos en diseño web responsive: SVG

### Teoría (para la casa)

Ya hemos avanzado bastante en datos, convendría volver sobre SVG y posibilidades de hacerlo interactivo.

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
            h2 {font-size: 1.5rem; margin: 5vh 0}
            p { font-size: 1.25rem; }
            p:nth-child(2n + 1){ margin-top:1rem; }
            @keyframes pedrope{
                0%{transform:rotate(0)}
                100%{transform:rotate(360deg)}
            }
            img{ display:block;  width:50%;  margin:0 auto 2rem auto;}
            img.animate { animation: pedrope 2s linear infinite; }
        </style>
    </head>
    <body>
        <div>
            <h2>Del innerHTML al setAttribute</h2>
            <!--usando input type="radio"-->
            <input type="radio" name="stroke" value="0.25" onchange="primera(this.value)" />
            <label for="light">LIGHT</label>
            <input type="radio" name="stroke" value="1" checked onchange="primera(this.value)" />
            <label for="normal">NORMAL</label>
            <input type="radio" name="stroke" value="1.75" onchange="primera(this.value)" />
            <label for="bold">BOLD</label>
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
            <h2>Y del setAttribute al addClass</h2>
            <img src="img/mapache.png">
            <!--usando input type="checkbox"-->
            <input type="checkbox" name="animado" onchange="cuarta()"> <label>ANÍMATE, PEDRO</label>
        </div>
        <script>
            // Hay muchos tipos de inputs: https://www.w3schools.com/html/html_form_input_types.asp
            // Acá usaremos cuatro, radio, range, [3] color y [4] checkbox
            function primera(valor) {
                document.querySelector("svg").setAttribute("stroke-width", valor);
            }
            function segunda(valor) {
                document.querySelector("svg").setAttribute("stroke", "hsl(" + valor + ",100%,50%)");
                document.querySelector("span").innerHTML = valor;
            }
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
            primera(1);
            segunda(0);
            //No necesito ejecutar tercera ni cuarta.
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-06) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-08)
