### Introducción al desarrollo web desde el diseño → Clase 06 → 12/09/2025

# Conociendo y comprendiendo dos lenguajes y otras biblioteca de JavaScript

Partamos un código, que pueden probarlo en su computador, con la cámara: 

https://editor.p5js.org/codingtrain/sketches/LCEHJm6PA

Una vez empiece a mostrarles lo que captura la cámara de su computador: Hagan este gesto con una mano 👌 y muévanla.

El código está usando p5.js y [ml5.js](https://ml5js.org/)

Detalles del HandPose que nos ofrece ml5.js se encuentran en: https://docs.ml5js.org/#/reference/handpose

**Para seguir jugando: https://thecodingtrain.com/tracks/ml5js-beginners-guide/ml5/facemesh**

Ahora veamos otra biblioteca, usando el siguiente código fuente: 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Chart.js</title>
    </head>
    <body>
        <canvas id="aqui"></canvas>
        <p style="text-align:center; margin-top:2rem">Más información en <a href="https://www.chartjs.org/docs/latest/getting-started/" target="_blank">Chart.js</a></p>
        <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
        <script>
            new Chart("aqui", {
                type: "scatter",
                data: {
                    datasets: [
                        {
                            pointRadius: 5,
                            pointBackgroundColor: "rgb(255,0,255)",
                            pointBorderWidth: 0,
                            data: [
                                { x: 50, y: 7 },
                                { x: 60, y: 8 },
                                { x: 70, y: 8 },
                                { x: 80, y: 9 },
                                { x: 90, y: 9 },
                                { x: 100, y: 9 },
                                { x: 110, y: 10 },
                                { x: 120, y: 11 },
                                { x: 130, y: 14 },
                                { x: 140, y: 14 },
                                { x: 150, y: 15 },
                            ],
                        },
                    ],
                },
                options: {
                    plugins: {
                        legend: {
                            display: false,
                        },
                    },
                },
            });
        </script>
    </body>
</html>
```


- - - - - - - -

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/opr/tree/main/clase-05) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-07)
