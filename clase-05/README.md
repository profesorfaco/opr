### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 05 → 02/04/2025

# Formatos ligeros de intercambios de datos en la creación de gráficas: JSON (primera parte)

### Teoría (para la casa)

JSON es sigla de JavaScript Object Notation (notación de objetos en JavaScript), sigla que refiere a su origen, pero no a su actual uso como formato de intercambio de datos. Es que el formato no es idéntico a la notación de Javascript y muchos otros lenguajes de programación pueden aprovecharlo.

Por ejemplo, puedo tener una variable en JavaScript como la que sigue:

```
const ejemplo = [
    {
        student: "AGUIRRE ULLOA MANUELA",
        title: "Design For Dignity",
        tutor: "GONZÁLEZ, A.",
        what: "safety blanket…",
        what_for: "s.i.",
        year: 2012,
    },
    {
        student: "ARAOS ANDUEZA TRINIDAD",
        title: "EL NOGAL, ROPA ORGÁNICA PARA BEBÉS",
        tutor: "MORENO, P.",
        what: "Vestuario sustentable para babés…",
        what_for: "Crear vestimenta para bebés…",
        year: 2015,
    },
]
```

Si los mismos datos fueran intercambiados mediante un `ejemplo.json`, sería:

```
[
	{
		"student": "AGUIRRE ULLOA MANUELA",
		"title": "Design For Dignity",
		"tutor": "GONZÁLEZ, A.",
		"what": "safety blanket…",
		"what_for": "s.i.",
		"year": 2012
	},
	{
		"student": "ARAOS ANDUEZA TRINIDAD",
		"title": "EL NOGAL, ROPA ORGÁNICA PARA BEBÉS",
		"tutor": "MORENO, P.",
		"what": "Vestuario sustentable para babés…",
		"what_for": "Crear vestimenta para bebés…",
		"year": 2015
	}
]
```

Pueden copiar el código del ejemplo y revisarlo con servios tales como https://webformatter.com/json, https://jsonlint.com/ o https://jsonformatter.curiousconcept.com/

El parecido entre lo que es, originalmente, una *JavaScript Object Notation* y el formato JSON, nos permite prescindir de alguna biblioteca de Javascript para simplificar simplicar *fetch* y *parsing*. Nos basta con: 

```
<script>
async function datos() {
  const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/opr/main/clase-05/datos.json");
  const data = await consulta.json();
  console.log(data);
}
datos().catch((error) => console.error(error));
</script>
```

Si es la primera vez que se enfrentan a un código como el que se muestra arriba, covendría dedicar 16 minutos y 21 segundos a ver https://www.youtube.com/watch?v=uxf0--uiX0I

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Partamos con el código que sigue, pegándolo en un index.html y revisando el resultado en la consola de JavaScript:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Partiendo la quinta clase</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous" />
        <style>
            image {
                filter: grayscale(1);
                opacity: 0.3;
            }
        </style>
    </head>
    <body>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
            <defs>
                <clipPath id="clipping">
                    <circle class="donut-hole" cx="20" cy="20" r="15.91549430918954" fill="#fff"></circle>
                </clipPath>
            </defs>
        </svg>
        <div class="container">
            <div class="row">
                <div class="col py-5"><h1 class="fs-6 text-center">PROFESORES BUENOS PARA LOS SIETES</h1></div>
            </div>
            <div class="row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 g-3" id="tartas"></div>
        </div>
        <script>
            //copiando de antes
            const graficaTarta = document.querySelector("#tartas");
            //esto es nuevo
            const fotos = [
                "https://diseno.uc.cl/wp-content/uploads/2014/11/allard_jose.jpg",
                "https://diseno.uc.cl/wp-content/uploads/2014/11/alvarez-pedro.jpg",
                "https://diseno.uc.cl/wp-content/uploads/2014/11/caro_ivan.jpg",
                "https://diseno.uc.cl/wp-content/uploads/2014/11/duran_alejandro.jpg",
                "https://diseno.uc.cl/wp-content/uploads/2019/06/gonzalez_alberto.jpg",
                "https://diseno.uc.cl/wp-content/uploads/2014/11/FOTO-PATRICIA-MANNS.png",
                "https://diseno.uc.cl/wp-content/uploads/2025/07/image-1.png",
                "https://diseno.uc.cl/wp-content/uploads/2019/06/moreno_paola.jpg",
                "https://diseno.uc.cl/wp-content/uploads/2014/11/rramirez.jpg",
                "https://diseno.uc.cl/wp-content/uploads/2014/11/ximena_ulibarri.png",
            ];
            //esto es para lo nuevo
            var f = 0;

            async function datos() {
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/opr/main/clase-05/datos.json");
                const data = await consulta.json();
                console.log(data);
                data.forEach((d) => {
                    if (d.sietes.length > 3) {
                        //lo que ya teníamos
                        console.log(d.tutor + " - Lleva " + d.sietes.length + ", o un " + Math.round((100 * d.sietes.length) / 13) + " de 100");
                        //lo del clase 2
                        graficaTarta.innerHTML += `<div class="col h-100 d-flex align-items-center justify-content-center"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 40 40"><circle class="donut-hole" cx="20" cy="20" r="15.91549430918954" fill="#fff"></circle><image x="5" y="5" width="30" height="30" xlink:href="${
                            fotos[f]
                        }"  clip-path="url(#clipping)"></image><circle class="donut-ring" cx="20" cy="20" r="15.91549430918954" fill="transparent" stroke="#eee" stroke-width="3"></circle><circle class="donut-segment" cx="20" cy="20" r="15.91549430918954" fill="transparent" stroke="#0ad" stroke-width="3" stroke-dasharray="${Math.round(
                            (100 * d.sietes.length) / 13
                        )} ${100 - Math.round((100 * d.sietes.length) / 13)}" stroke-dashoffset="25"></circle><text x="20" y="28" font-size="2" text-anchor="middle" fill="#09c">${d.tutor}</text></svg></div>`;
                        f++;
                    }
                });
            }
            datos().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

En la partida usamos un [`String.length`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/length) para contar número de elementos de arreglos con el índice `sietes`. Y lo usamos dos veces, primero en una condición [`if…else`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/if...else) y después en la construcción del [mensaje del `console.log()`](https://developer.mozilla.org/es/docs/Web/API/console/log_static)

Ojo que en la construcción del mensaje también interviene un [`Math.round()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/round).

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-04) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-06)
