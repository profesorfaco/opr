### Optativo de Profundización: [Desarrollo Web y Diseño Visual de Información](https://github.com/profesorfaco/opr/?tab=readme-ov-file#readme) → Clase 10 → 08/05/2026

# Gráficas y datos en diseño web responsive: SVG, HTML y JavaScript (clase 1 de 2)

### Teoría (para la casa)

Trabajemos con aves chilenas, aprovechando el trabajo de los [Ninjas.cl](https://github.com/NinjasCL/chileanbirds-dataset), pero tomándolo desde otro lado: 

https://api.myjson.online/v1/records/b4cc6491-a885-4cf0-8760-c06ccd90e3ce

- - - - - - - 

### Práctica (para la clase)

Busquemos qué consultar, aprovechando lo ya trabajado en clases previas y sumando algunas cositas.

Una alternativa podría ser llegar a desarrollar algo como: https://aves.ninjas.cl/


```
<!doctype html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Un fetch</title>
        <style>
            *,
            *::before,
            *::after {
                box-sizing: border-box;
                margin: 0;
                padding: 0;
            }

            :root {
                --texto: #000;
                --fondo: #eee;
                --blanco: #fff;
                --fuente: Helvetica, Arial, sans-serif;
            }

            body {
                font-family: var(--fuente);
                background: var(--fondo);
            }
            svg#escondido {
                display: none;
            }

            div#contenedor {
                width: 90%;
                max-width: 480px;
                margin: 1rem auto;
                box-shadow: 0 0 3px rgba(200, 200, 200, 0.5);
                padding: 1rem;
                background: var(--blanco);
            }

            h1 {
                text-align: left;
                font-size: calc(1rem + 2vw + 2vh);
                margin: 2vw auto;
                padding-left:calc(2rem + 2vw + 2vh);
                background:url('data:image/svg+xml,<%3Fxml version="1.0" encoding="utf-8"%3F><!-- Generator: Adobe Illustrator 27.5.0, SVG Export Plug-In . SVG Version: 6.00 Build 0) --><svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 1024 1024" style="enable-background:new 0 0 1024 1024;" xml:space="preserve"><g><path style="fill:%23252523;" d="M176.723,119.24c47.725-14.592,100.919-9.15,145.035,14.018c39.42,20.218,70.449,53.681,93.717,90.91c14.275,23.34,38.331,37.486,61.957,49.758c97.482,54.784,181.004,130.101,263.051,205.173c48.397,36.343,100.876,66.855,151.809,99.431c-30.083-4.267-60.77-2.233-90.238,4.983c70.463,47.452,141.155,94.59,211.304,142.515c5.47,3.724,15.593,12.73,7.804,18.786c-19.475,2.978-33.777-14.461-50.159-22.05c4.855,10.267,13.374,17.956,20.505,26.547c3.293,3.277,2.435,10.352-3.008,10.467c-13.143,1.073-24.527-7.002-36.641-10.739c9.808,9.307,23.584,14.72,30.986,26.317c2.219,9.25-10.182,7.632-15.736,6.744c-22.022-4.252-44.304-9.794-64.35-20.074c-58.448-36.785-116.325-74.515-173.673-112.99c-28.381,24.37-59.968,44.946-94.089,60.368c-7.89,2.721-11.256,10.768-15.88,16.997c-27.722,41.58-54.813,83.607-81.961,125.575c-2.549,4.224-6.3,11.025-1.088,14.805c13.718,8.006,30.657,8.649,45.606,3.896c11.354-3.766,23.697,3.378,27.362,14.475c26.805,2.292,55.399,3.451,79.212,17.327c-53.424,4.394-107.664,1.317-159.598-12.501c-20.505-6.802-39.721,6-59.223,10.354c-38.933,9.277-79.283,11.44-119.161,12.515c14.978-9.796,31.931-16.081,48.655-22.181c-19.402-2.562-38.775-15.651-58.363-7.474c-55.571,18.069-114.709,24.384-172.871,19.129c23.154-12.601,50.216-14.19,75.833-17.798c2.075-12.601,15.221-22.137,27.792-17.985c14.605,4.653,30.485,7.962,45.448,2.693c25.517-8.392,45.391-27.564,63.691-46.437c29.783-29.654,58.391-60.439,88.304-89.966c-134.869-9.449-256.607-105.515-303.344-231.363c-12.845-33.376-19.216-68.845-22.638-104.325c-1.761-22.095-3.794-45.392-16.209-64.449c-11.984-16.009-22.795-34.38-21.649-55.171C69.804,271.005,34.694,264.332,0,255.841c27.506-20.705,57.991-37.186,89.75-50.358C96.509,161.709,136.586,131.425,176.723,119.24z"/><path style="fill:%23FCD439;" d="M173.258,142.966c45.52-17.111,98.299-12.257,141.04,10.467c35.611,18.887,62.845,49.858,83.965,83.622c13.789,20.533,33.307,36.642,55.07,48.154c59.895,32.261,115.124,72.524,166.828,116.584c12.372,10.925,25.259,21.463,35.94,34.106c-46.148-21.935-91.61-45.591-139.45-63.747c-56.244-21.75-122.971-30.828-178.227-1.546c34.38-4.826,69.675-5.67,103.797,1.503c65.05,13.876,123.929,47.096,179.616,82.305c-58.852-3.18-117.601-12.257-176.666-8.577c22.854,9.709,47.567,13.932,72.081,16.811c-22.852,8.349-47.539,8.061-71.522,7.633c9.693,3.478,19.902,5.153,29.755,8.132c-33.679,8.978-68.974,3.165-102.18-4.997c13.445,9.966,28.651,17.183,44.489,22.423c-32.805,3.466-65.353-3.55-96.753-12.428c11.039,10.51,24.442,18.155,38.603,23.61c-28.208-0.457-56.116-10.781-77.794-28.852c-24.599-20.347-37.529-52.135-38.489-83.637c-12.744,31.502-3.523,68.258,19.617,92.414c32.561,36.686,86.199,51.147,133.379,39.462c12.157-4.151,27.164-4.996,36.513,5.442c17.642,20.132,39.335,36.383,63.06,48.669c85.412,43.931,189.252,44.675,278.486,11.755c3.408-1.946,6.058,1.462,8.678,3.123c56.803,39.118,114.078,77.564,170.136,117.728c6.386,5.843,15.95,10.567,17.526,19.76c-14.463,0.201-25.874-10.065-37.901-16.639c-56.616-32.417-110.784-69.618-169.836-97.467c7.861,11.941,19.946,20.017,31.043,28.651c40.896,30.069,83.294,58.02,124.874,87.115c5.727,4.253,11.742,8.663,15.035,15.221c-14.634,0.888-26.403-9.307-38.175-16.423c-55.456-35.611-110.498-71.867-165.925-107.52c-14.72-9.179-32.032-1.576-46.178,4.825c-36.4,16.28-77.007,21.593-116.527,17.54c35.267,18.672,77.607,17.498,115.352,7.66c-98.485,73.972-240.985,74.529-346.201,14.005c-82.792-47.253-144.82-130.187-164.308-223.746c-11.04-44.245-2.95-95.191-32.947-133.079c-8.42-11.784-20.147-32.189-5.47-43.544c13.589-11.855,27.106-23.768,40.637-35.668c-11.04-1.732-22.352-0.572-33.305-2.691c-12.873-5.026-27.765-15.407-28.967-30.198C121.051,172.979,146.639,153.305,173.258,142.966z"/><path style="fill:%23252523;" d="M198.644,187.067c17.069-5.398,36.671,7.747,38.775,25.345c1.705,15.923-11.841,31.315-27.792,31.974c-15.165,1.876-30.457-9.751-32.762-24.814C174.675,205.281,185.013,190.963,198.644,187.067z"/><path style="fill:%23FEFEFE;" d="M205.948,202.977c7.717-2.563,11.111,9.894,3.579,12.171C201.537,218.283,197.227,204.007,205.948,202.977z"/><path style="fill:%23252523;" d="M249.391,213.501c26.69-12.415,58.65,1.13,75.617,23.425c-14.934-7.116-31.057-14.104-48.01-12.042c-14.635,1.217-26.962,9.809-40.237,15.135C240.957,231.327,241.272,219.629,249.391,213.501z"/><path style="fill:%23FEFEFE;" d="M33.807,248.267c21.149-9.822,43.4-17.298,65.479-24.857c7.546,7.804,17.126,12.973,27.163,16.853C95.606,243.298,64.721,246.047,33.807,248.267z"/><path style="fill:%23FEFEFE;" d="M72.969,255.784c18.199-1.776,36.542-0.244,54.798-0.96C112.045,267.783,91.097,254.337,72.969,255.784z"/><path style="fill:%23FCD439;" d="M586.713,475.276c28.638,3.064,60.011,4.868,85.885-10.066c29.768,15.85,60.654,30.671,88.434,49.657c-14.734,4.725-30.471-0.702-45.348-2.479C671.896,503.427,627.508,493.934,586.713,475.276z"/><path style="fill:%23FCD439;" d="M546.935,483.796c69.561,33.793,147.325,44.79,223.99,45.591c18.213-0.042,35.609,8.334,50.172,18.587c-6.014,7.317-19.545,4.467-28.666,5.527c-72.282-2.464-145.322-15.881-211.03-46.98C569.444,499.877,556.013,494.335,546.935,483.796z"/><path style="fill:%23FCD439;" d="M507.916,505.503c-5.728-3.852-14.647-15.836-3.121-18.113c15.923,2.335,26.604,16.467,40.164,24.027c48.799,32.689,106.776,46.837,164.065,55.614C637.889,573.504,562.643,552.141,507.916,505.503z"/><path style="fill:%23FCD439;" d="M465.118,503.686c16.925,0.228,26.261,17.053,39.362,25.343c56.129,45.22,130.187,60.298,200.821,59.195c-9.565,3.966-19.975,5.025-30.155,6.271c-77.18,7.46-158.538-18.729-212.964-74.831C456.784,515.198,456.497,504.157,465.118,503.686z"/><path style="fill:%23FEFEFE;" d="M517.424,734.132c21.68-0.53,43.029-4.481,64.393-7.761c1.217,5.957-3.351,10.61-5.842,15.535c-18.027,31.846-36.57,63.404-55.872,94.504c-10.782,18.1-28.295,31.589-47.839,39.076c-4.927-11.455-18.543-16.853-30.127-12.543c-19.002,5.355-45.219,7.876-58.879-9.15c37.328-39.305,76.49-76.906,115.08-115.009C502.806,732.656,510.938,735.048,517.424,734.132z"/></g></svg>');
                background-repeat: no-repeat;
                background-size:calc(1.5rem + 2vw + 2vh);

            }

            h2{
                margin:3rem 0 1rem 0;
            }

            ol,
            ul {
                list-style-position: inside;
                list-style: none;
                width: 100%;
                margin: 1rem 0;
                border-top: 1px solid silver;
            }

            ol li {
                border-bottom: 1px solid silver;
                padding: 0.5rem 0;
            }

            ol li:last-child {
                border-bottom: 3px solid silver;
            }

            li {
                display: flex;
                flex-direction: row;
                align-items: center;
            }

            .tiny {
                width: 2rem;
                height: auto;
                border-radius: 50% 50%;
                margin-right: 0.5rem;
            }
        </style>
    </head>
    <body>
        <div id="contenedor">
            <h1>Orden</h1>
            <p>La clase Aves se divide en aproximadamente 40 órdenes según la clasificación de Clements (2023), siendo Passeriformes (pájaros cantores) el más numeroso, abarcando más de la mitad de las especies conocidas en el mundo. Para conocer alguno de los órdenes de aves chilenas, puedes ver lo que siguen:</p>
            
            <h2>Strigiformes</h2>
            <p>Los estrigiformes son las aves rapaces nocturnas, que incluye búhos, chunchos, lechuzas.
            
            <ol id="uno"></ol>
            
            <h2>Charadriiformes</h2>
            <p>Los Charadriiformes son aves de agua dulce o salada, tales como las gaviotas, gaviotines y sus primas de patas largas y pico agudo.</p>
            
            <ol id="dos"></ol>

            <h2>Passeriformes</h2>

            <p>Los paseriformes se conocen comúnmente como pájaros y a veces aves cantoras o pájaros cantores</p>
            
            <ol id="tres"></ol>
        </div>
        <script>
            fetch("https://api.myjson.online/v1/records/b4cc6491-a885-4cf0-8760-c06ccd90e3ce")
                .then((respuesta) => {
                    if (!respuesta.ok) {
                        throw new Error("Error HTTP: " + respuesta.status);
                    }
                    return respuesta.json();
                })
                .then((datos) => {
                    var pajaretes = datos.data;
                    console.log("Datos recibidos:", pajaretes);
                    const primero = document.getElementById("uno");
                    const segundo = document.getElementById("dos");
                    const tercero = document.getElementById("tres");

                    //Passeriformes
                    //Charadriiformes
                    //Strigiformes

                    pajaretes.forEach((x) => {
                        if (x.info.order.value.includes("Strigiformes")) {
                            primero.innerHTML += `<li><img src="${x.image.url}" class="tiny"/>${x.names.spanish}</li>`;
                        }
                        if (x.info.order.value.includes("Charadriiformes")) {
                            segundo.innerHTML += `<li><img src="${x.image.url}" class="tiny"/>${x.names.spanish}</li>`;
                        }
                        if (x.info.order.value.includes("Passeriformes")) {
                            tercero.innerHTML += `<li><img src="${x.image.url}" class="tiny"/>${x.names.spanish}</li>`;
                        }

                    });
                })
                .catch((error) => {
                    console.error("Algo salió mal:", error);
                });
        </script>
    </body>
</html>
```

Lo del SVG como imagen de fondo (siendo código SVG) se logra con https://www.svgbackgrounds.com/tools/svg-to-css/



- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-08) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-11)
