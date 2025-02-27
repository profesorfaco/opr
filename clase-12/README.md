### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 12 → 21/05/2025

# Gráficas y datos en diseño web responsive SVG, HTML, CSS y JavaScript (primera parte)

### Teoría (para la casa)

CSS es mi amigo.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Para ordenar lo que llevamos:

```<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Clase 12</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous" />
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/chartist/0.11.4/chartist.min.css" integrity="sha512-V0+DPzYyLzIiMiWCg3nNdY+NyIiK9bED/T1xNBj08CaIUyK3sXRpB26OUCIzujMevxY9TRJFHQIxTwgzb0jVLg==" crossorigin="anonymous" referrerpolicy="no-referrer"/>

        <link rel="preconnect" href="https://fonts.googleapis.com" />
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
        <link href="https://fonts.googleapis.com/css2?family=Jacquard+12&family=Reddit+Sans&display=swap" rel="stylesheet" />
        <style>
            :root {
                --bs-font-sans-serif: "Reddit Sans", sans-serif;
                --bs-light-rgb: 200, 230, 250;
            }

            .ct-series-a .ct-bar,
            .ct-series-a .ct-line,
            .ct-series-a .ct-point,
            .ct-series-a .ct-slice-donut {
                stroke: rgb(158, 1, 66);
            }
            .ct-series-a .ct-area,
            .ct-series-a .ct-slice-donut-solid,
            .ct-series-a .ct-slice-pie {
                fill: rgb(158, 1, 66);
            }
            .ct-series-b .ct-bar,
            .ct-series-b .ct-line,
            .ct-series-b .ct-point,
            .ct-series-b .ct-slice-donut {
                stroke: rgb(219, 73, 74);
            }
            .ct-series-b .ct-area,
            .ct-series-b .ct-slice-donut-solid,
            .ct-series-b .ct-slice-pie {
                fill: rgb(219, 73, 74);
            }
            .ct-series-c .ct-bar,
            .ct-series-c .ct-line,
            .ct-series-c .ct-point,
            .ct-series-c .ct-slice-donut {
                stroke: rgb(248, 142, 83);
            }
            .ct-series-c .ct-area,
            .ct-series-c .ct-slice-donut-solid,
            .ct-series-c .ct-slice-pie {
                fill: rgb(248, 142, 83);
            }
            .ct-series-d .ct-bar,
            .ct-series-d .ct-line,
            .ct-series-d .ct-point,
            .ct-series-d .ct-slice-donut {
                stroke: rgb(254, 210, 129);
            }
            .ct-series-d .ct-area,
            .ct-series-d .ct-slice-donut-solid,
            .ct-series-d .ct-slice-pie {
                fill: rgb(254, 210, 129);
            }

            .ct-series-e .ct-bar,
            .ct-series-e .ct-line,
            .ct-series-e .ct-point,
            .ct-series-e .ct-slice-donut {
                stroke: rgb(251, 248, 176);
            }
            .ct-series-e .ct-area,
            .ct-series-e .ct-slice-donut-solid,
            .ct-series-e .ct-slice-pie {
                fill: rgb(251, 248, 176);
            }
            .ct-series-f .ct-bar,
            .ct-series-f .ct-line,
            .ct-series-f .ct-point,
            .ct-series-f .ct-slice-donut {
                stroke: rgb(213, 238, 159);
            }
            .ct-series-f .ct-area,
            .ct-series-f .ct-slice-donut-solid,
            .ct-series-f .ct-slice-pie {
                fill: rgb(213, 238, 159);
            }
            .ct-series-g .ct-bar,
            .ct-series-g .ct-line,
            .ct-series-g .ct-point,
            .ct-series-g .ct-slice-donut {
                stroke: rgb(137, 207, 165);
            }
            .ct-series-g .ct-area,
            .ct-series-g .ct-slice-donut-solid,
            .ct-series-g .ct-slice-pie {
                fill: rgb(137, 207, 165);
            }
            .ct-series-h .ct-bar,
            .ct-series-h .ct-line,
            .ct-series-h .ct-point,
            .ct-series-h .ct-slice-donut {
                stroke: rgb(70, 150, 179);
            }
            .ct-series-h .ct-area,
            .ct-series-h .ct-slice-donut-solid,
            .ct-series-h .ct-slice-pie {
                fill: rgb(70, 150, 179);
            }
            .ct-series-i .ct-bar,
            .ct-series-i .ct-line,
            .ct-series-i .ct-point,
            .ct-series-i .ct-slice-donut {
                stroke: rgb(94, 79, 162);
            }
            .ct-series-i .ct-area,
            .ct-series-i .ct-slice-donut-solid,
            .ct-series-i .ct-slice-pie {
                fill: rgb(94, 79, 162);
            }
        </style>
        <script
            src="https://cdnjs.cloudflare.com/ajax/libs/chartist/0.11.4/chartist.min.js"
            integrity="sha512-9rxMbTkN9JcgG5euudGbdIbhFZ7KGyAuVomdQDI9qXfPply9BJh0iqA7E/moLCatH2JD4xBGHwV6ezBkCpnjRQ=="
            crossorigin="anonymous"
            referrerpolicy="no-referrer"
        ></script>
    </head>
    <body>
        <header class="bg-light fixed-top shadow-sm">
            <div class="container py-3">
                <div class="row">
                    <div class="col-10 mx-auto text-center fw-lighter">
                        <p class="my-0 d-flex justify-content-between align-items-center"><span>Cambie su nombre</span> <span class="d-sm-none">|</span> <span>Diseño UC</span></p>
                    </div>
                </div>
            </div>
        </header>
        <main class="mt-5 py-5">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-lg-8 pe-5">
                        <h2 class="text-center">Highest grossing movies in history</h2>
                        <object data="viz.svg" type="image/svg+xml" class="w-100">
                            <img src="alt.png" />
                        </object>
                    </div>
                    <div class="col-lg-4">
                        <div class="row ps-lg-5">
                            <div class="col-12 col-sm-6 col-lg-12 py-3">
                                <h2 class="text-center fs-5">ROI</h2>
                                <div class="ct-chart1 ct-minor-second"></div>
                            </div>
                            <div class="col-12 col-sm-6 col-lg-12 py-3">
                                <h2 class="text-center fs-5">BOX OFFICE</h2>
                                <div class="ct-chart2 ct-minor-second"></div>
                            </div>
                        </div>
                    </div>
                    <div class="col-12 pt-5">
                        <h2 class="text-center">Comparación promedios</h2>
                        <div class="ct-chart3 ct-major-twelfth"></div>
                    </div>
                </div>
            </div>
        </main>

        <script>
            //los datos
            var roi = {
                labels: ["Acción", "Aventura", "Animación", "Biografía", "Crimen", "Drama", "Familia", "Horror", "Musical"],
                series: [13.53, 63.46, 64.05, 34.9, 42.8, 56.95, 75.5, 51.5, 66.2],
            };
            var box = {
                labels: ["Acción", "Aventura", "Animación", "Biografía", "Crimen", "Drama", "Familia", "Horror", "Musical"],
                series: [1268.59, 694.75, 751.45, 286, 246, 957.5, 793, 441, 397],
            };
            var options = {
                showLabel: true,
                donut: true,
                donutWidth: 60,
            };
            //la creación
            new Chartist.Pie(".ct-chart1", roi, options);
            new Chartist.Pie(".ct-chart2", box, options);
        </script>

        <script>
            new Chartist.Bar(
                ".ct-chart3",
                {
                    labels: ["Acción", "Aventura", "Animación", "Biogrfía", "Crimen", "Drama", "Familia", "Horror", "Musical"],
                    series: [
                        [13.681, 147.625, 81.77, 34.9, 42.8, 37.525, 75.5, 36.8, 66.2],
                        [1284.43, 754.125, 834.27, 286, 246, 879.75, 793, 441, 397],
                    ],
                },
                {
                    axisX: {
                        // On the x-axis start means top and end means bottom
                        position: "start",
                    },
                    axisY: {
                        // On the y-axis start means left and end means right
                        position: "end",
                    },
                }
            );
        </script>
    </body>
</html>
```
- - - - - - - 

Partiendo de lo recién presentado, como en cada clase, corresponde dejar constancia, durante el día, de su resultado ya publicado en GitHub mediante una entrada en este foro de discusión: https://cursos.canvas.uc.cl/courses/73175/discussion_topics/793009

Con lo ingresado en el foro se rellena la siguiente tabla:

| N° | Nombre | URL |
|:---------:|:------------------------------|:---------------------------|
| 1 | ISIDORA ARRIAGADA | https://isidjan.github.io/dnoweb097_12/ |
| 2 | TRINIDAD FORSTER | https://trinidad-forster.github.io/C12_15-05/ |
| 3 | TAHIS FUENTES | — |
| 4 | SARA GOLDZVEIG | https://saragoldzveig.github.io/Clase012/ |
| 5 | JOSEFINA IMSCHENETZKY | https://jimschenetzky.github.io/DNOWEB_12/ |
| 6 | PAULA MIRANDA | — |
| 7 | JAVIERA MOLIN | https://javimolin-uc.github.io/C12/ |
| 8 | ISIDORA MUÑOZ | https://isidoramunoz.github.io/dnoweb-12/ |
| 9 | VALENTINA NAVARRETE | https://valenavarrete.github.io/Clase-12/ |
| 10 | TRINIDAD RODRÍGUEZ | https://trinirodriguez.github.io/dno-12/ |
| 11 | CATALINA SEGUEL | https://cataseguel.github.io/Clase-12/ |
| 12 | FRANCISCA SOTO | https://fsoti.github.io/Clase-12/ |
| 13 | CAMILA VALLEJO | https://camivallejo.github.io/clase_12_Web/ |

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-11) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-13)
