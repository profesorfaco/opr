### Optativo de Profundización: [Desarrollo Web y Diseño Visual de Información](https://github.com/profesorfaco/opr/?tab=readme-ov-file#readme) → Clase 08 → 24/04/2026

# Gráficas y datos en diseño web responsive: SVG y HTML

### Teoría (para la casa)


En HTML puedo tener dos versiones de la misma gráfica, una angosta y otra ancha.

```
<figure id="first">
  <object data="angosta.svg" type="image/svg+xml">
    <img src="angosta.svg">
  </object>
  <figcaption>Mobile</figcaption>
</figure>

<figure id="second">
  <object data="ancha.svg" type="image/svg+xml">
    <img src="ancha.svg">
  </object>
  <figcaption>Desktop</figcaption>
</figure>
```

Luego, mediante `CSS` muestro o escondo otra. 

```
/* Móvil: se muestra #first, se oculta #second */
#first {
  display: block;
}

#second {
  display: none;
}

/* Pantallas desde 600px: se oculta #first, se muestra #second */
@media screen and (min-width: 600px) {
  #first {
    display: none;
  }

  #second {
    display: block;
  }
}
```

- - - - - - - - - - - - - - 

### Práctica (para la clase)

```
<!doctype html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-wivdth, initial-scale=1" />
        <title>Un fetch</title>
        <style>
            @import url("https://fonts.googleapis.com/css2?family=Inconsolata:wght@200..900&family=Roboto:ital,wght@0,100..900;1,100..900&display=swap");

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
                --fuente: "Inconsolata", monospace;
                --otrafuente: "Roboto", sans-serif;
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
                max-width: 780px;
                margin: 1rem auto;
                box-shadow: 0 0 3px rgba(200, 200, 200, 0.5);
                padding: 1rem;
                background: var(--blanco);
            }

            h1 {
                font-family: var(--otrafuente);
                text-align: center;
                font-size: calc(1rem + 2vw + 2vh);
                margin: 3vw auto;

                /*line-height: 2vw;*/
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

            ol li a {
                text-decoration: none;
                color: var(--texto);
                transition: all ease 0.5s;
            }

            ol li a:hover {
                letter-spacing: 0.1rem;
                transition: all ease 0.5s;
            }

            ol li a:nth-child(1) {
                display: inline-block;
                width: 50%;
            }

            ol li a[target="_blank"] {
                margin-left: 1rem;
            }

            figure {
                width: 80%;
                margin: 10% auto;
            }

            @keyframes nombre {
                0% {
                    fill: #00a;
                    transform: rotate(359deg);
                }
                100% {
                    fill: #a00;
                }
            }

            figure svg use[href="#bien"] {
                animation: nombre 2s infinite alternate;
                transform-origin: center 25%;
            }
            figure svg use[href="#mal"] {
                animation: nombre 4s infinite alternate;
                transform-origin: center 75%;
            }

            /* Móvil: se muestra #first, se oculta #second */
            #first {
                display: block;
            }

            #second {
                display: none;
            }

            /* Pantallas desde 600px: se oculta #first, se muestra #second */
            @media screen and (min-width: 600px) {
                #first {
                    display: none;
                }

                #second {
                    display: block;
                }

                figure svg use[href="#bien"] {
                    transform-origin: 25% center;
                }

                figure svg use[href="#mal"] {
                    transform-origin: 75% center;
                }
            }
        </style>
    </head>
    <body>
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16" id="escondido">
            <symbol id="bien" width="16" height="16" viewBox="0 0 16 16">
                <path d="M8 16A8 8 0 1 0 8 0a8 8 0 0 0 0 16M7 6.5C7 7.328 6.552 8 6 8s-1-.672-1-1.5S5.448 5 6 5s1 .672 1 1.5M4.285 9.567a.5.5 0 0 1 .683.183A3.5 3.5 0 0 0 8 11.5a3.5 3.5 0 0 0 3.032-1.75.5.5 0 1 1 .866.5A4.5 4.5 0 0 1 8 12.5a4.5 4.5 0 0 1-3.898-2.25.5.5 0 0 1 .183-.683M10 8c-.552 0-1-.672-1-1.5S9.448 5 10 5s1 .672 1 1.5S10.552 8 10 8" />
            </symbol>
            <symbol id="mal" width="16" height="16" viewBox="0 0 16 16">
                <path d="M8 16A8 8 0 1 0 8 0a8 8 0 0 0 0 16M7 6.5C7 7.328 6.552 8 6 8s-1-.672-1-1.5S5.448 5 6 5s1 .672 1 1.5m-2.715 5.933a.5.5 0 0 1-.183-.683A4.5 4.5 0 0 1 8 9.5a4.5 4.5 0 0 1 3.898 2.25.5.5 0 0 1-.866.5A3.5 3.5 0 0 0 8 10.5a3.5 3.5 0 0 0-3.032 1.75.5.5 0 0 1-.683.183M10 8c-.552 0-1-.672-1-1.5S9.448 5 10 5s1 .672 1 1.5S10.552 8 10 8" />
            </symbol>
        </svg>
        <div id="contenedor">
            <h1>Hola mundo</h1>
            <ol id="estudiantes"></ol>

            <figure id="first">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 32">
                    <use href="#bien" />
                    <use href="#mal" y="16" />
                </svg>
            </figure>

            <figure id="second">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 16">
                    <use href="#bien" />
                    <use href="#mal" x="16" />
                </svg>
            </figure>
        </div>
        <script>
            fetch("https://raw.githubusercontent.com/profesorfaco/opr/refs/heads/main/clase-07/registros.json")
                .then((respuesta) => {
                    if (!respuesta.ok) {
                        throw new Error("Error HTTP: " + respuesta.status);
                    }
                    return respuesta.json();
                })
                .then((datos) => {
                    var trabajo = datos;
                    console.log("Datos recibidos:", trabajo);
                    const donde = document.getElementById("estudiantes");
                    //repita
                    trabajo.forEach((x) => {
                        var cuantos = [];
                        if (x.uno != "") {
                            cuantos.push(x.uno);
                        }
                        if (x.dos != "") {
                            cuantos.push(x.dos);
                        }
                        if (x.tres != "") {
                            cuantos.push(x.tres);
                        }
                        if (x.cuatro != "") {
                            cuantos.push(x.cuatro);
                        }
                        if (x.seis != "") {
                            cuantos.push(x.seis);
                        }
                        if (x.siete != "") {
                            cuantos.push(x.siete);
                        }
                        donde.innerHTML += `<li><a href="${x.cuenta}">${x.nombre}</a> ${pelotitas(cuantos)}</li>`;
                    });
                    function pelotitas(n) {
                        var armado = "";
                        n.forEach((e) => {
                            if (e[1]) {
                                armado += `<a href="${e[0]}" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16"><use href="#bien" fill="#00a"/></svg></a>`;
                            } else {
                                armado += `<a href="${e[0]}" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16"><use href="#mal" fill="#a00"/></svg></a>`;
                            }
                        });
                        return armado;
                    }
                })
                .catch((error) => {
                    console.error("Algo salió mal:", error);
                });
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-07) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-10)
