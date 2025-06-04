### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 13 → 04/06/2025

# ~~Gráficas y datos en diseño web responsive SVG, HTML, CSS y JavaScript (segunda parte)~~ Diseño y programación: Desarrollo de la propuesta

Cada estudiante debería tener, al final de la clase, al menos: 

- una consulta resuelta a un csv o json con los datos que ya pudo preparar
  
- una página html con un relato y algunos bocetos de visualizaciones

- un README.md con antecedentes y referentes. Cada uno con imagen, descripción (qué es), dirección (fuente), aspectos positivos y aspectos negativos.
 

Ejemplo de págin html:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Trabajo final</title>
        <style>

            [data-theme="light"] { --color-bg: #eceff1; --color-fg: #263238; }

            [data-theme="dark"] { --color-bg: #263238; --color-fg: #eceff1; }

            * { margin: 0; padding: 0; }

            body { 
                font-family: monospace; 
                color: var(--color-fg); 
                background: var(--color-bg); 
                text-align: center;
            }

            header, main, footer { 
                padding: 1% 10%; 
                width: min(70%, 700px); 
                margin: 0 auto; 
                text-align: left; 
                background: pink;
            }  


            figure{
                margin:1% -10%;
            }

            figure img{
                width:100%;
            }

            figure figcaption{
                margin:1% 8%;
            }

            header{
                margin-top:2rem;
            }          

            footer{
                margin-bottom:2rem;
            }  

            h1{
                text-align: center;
            }

            h2{
                text-align: center;
            }
            h5{
                text-align: center;
            }

            h3{
                margin-top:3rem;
            }
        </style>
    </head>
    <body>
        <header>
            <h1>Un título que puede ser "clickbaitero"</h1>
            <h2>Un subtítulo que sea más serio</h2>
            <h5>Por nombre apellido</h5>
            <p>Una bajada tipo abstract. Maecenas eleifend luctus diam, sed fermentum arcu interdum nec. Fusce eu efficitur libero. Nullam vitae sagittis nunc. Sed justo erat eleifend.</p>
        </header>
        <main>
            <article>
                <h3>Primer asunto</h3>
                <figure>
                    <img src="https://images.ctfassets.net/pdf29us7flmy/7k1Pxm3wUryWsPiNiE8BrC/ae306b7a493537ba1199148cfce562f1/GOLD-6487-CareerGuide-Batch04-Images-GraphCharts-13-Bullet.png?w=720&q=100&fm=avif">
                    <figcaption>Pequeño texto</figcaption>
                </figure>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas eleifend luctus diam, sed fermentum arcu interdum nec. Fusce eu efficitur libero. Nullam vitae sagittis nunc. Sed justo erat eleifend.</p>
            </article>
            <article>
                <h3>Segundo asunto</h3>
                <figure>
                    <img src="https://images.ctfassets.net/pdf29us7flmy/63wBLDfuNpESMQ5lFPGWrU/8b76d1862870b1312b32cd2ae4438c46/GOLD-6487-CareerGuide-Batch04-Images-GraphCharts-08-Pie.png?w=720&q=100&fm=avif">
                    <figcaption>Pequeño texto</figcaption>
                </figure>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas eleifend luctus diam, sed fermentum arcu interdum nec. Fusce eu efficitur libero. Nullam vitae sagittis nunc. Sed justo erat eleifend.</p>
            </article>
            <article>
                <h3>Tercer asunto</h3>
                <figure>
                    <img src="https://images.ctfassets.net/pdf29us7flmy/51sHTHQeWaWNAZ5IlyRTs8/b916596b1c94e2fbbf1df2db07e85aa9/GOLD-6487-CareerGuide-Batch04-Images-GraphCharts-07-Flowchart.png?w=720&q=100&fm=avif">
                    <figcaption>Pequeño texto</figcaption>
                </figure>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas eleifend luctus diam, sed fermentum arcu interdum nec. Fusce eu efficitur libero. Nullam vitae sagittis nunc. Sed justo erat eleifend.</p>
            </article>            
            <article>
                <h3>Cuarto y último asunto</h3>
                <figure>
                    <img src="https://images.ctfassets.net/pdf29us7flmy/3qy7LasC628YTk0rb7hcAY/5a35687a67bbb3a709f852dbb8c62351/GOLD-6487-CareerGuide-Batch04-Images-GraphCharts-06-ScatterPlot.png?w=720&q=100&fm=avif">
                    <figcaption>Pequeño texto</figcaption>
                </figure>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas eleifend luctus diam, sed fermentum arcu interdum nec. Fusce eu efficitur libero. Nullam vitae sagittis nunc. Sed justo erat eleifend.</p>
            </article>
            <article>
                <p>Esta es la conclusión con un lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas eleifend luctus diam, sed fermentum arcu interdum nec. Fusce eu efficitur libero. Nullam vitae sagittis nunc. Sed justo erat eleifend.</p>
            </article>
        </main>
        <footer>
            tres
        </footer>

    <script>
            async function datos() {
                const consulta = await fetch("…");
                const data = await consulta.json();
                console.log(data);
            }
            datos().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-12) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-14)
