### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 06 → 09/04/2025

# Formatos ligeros de intercambios de datos en la creación de gráficas: JSON (segunda parte)

### Teoría

Como es la segunda parte del JSON, en esta ocasión no tenemos teoría. Vamos directo a la práctica.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Partamos con un código, que se pega en un `index.html`:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Partiendo la séptima clase</title>
        <style>
            * { margin: 0; padding: 0;}
            :root{
                --base: #03122E;
                --detalle:#0D47A1;
                --ajuste:#1976D2;
                --borde:#E3F2FD;
                --claro:#FAFAFA;
            }
            body { color: var(--base); text-align: center; font-family: Helvetica, Arial, sans-serif; }
            
            em { font-style: normal; font-weight: bold; }
            
            a{ color:var(--detalle); text-decoration: none; transition:color .3s ease; }
            
            a:hover{ color:var(--ajuste); text-decoration: none; transition:color .3s ease; }
            
            div {margin: 3% auto; text-align: left; width: min(90%, 700px);}
            
            header { padding: 0.4rem;}
            
            h1 { font-weight: normal; font-size: calc(1.5em + 1vw); margin-left:-0.15rem;}
            
            h2 { font-weight: normal; font-size: 1.25rem; }
            
            h2 select { line-height: 1; font-size: 1.2rem; border: none; background: var(--claro); border-radius: 4px; box-shadow: inset 0 0 3px var(--borde); padding: 0.2rem; }
            
            h3 { padding: 0.5rem; border: 1px solid var(--borde); background: var(--claro); margin-top: 1rem; border-radius: 3px 3px 0 0; }
            
            article { padding: 0.5rem; border: 1px solid var(--borde); border-top:none; border-radius: 0 0 3px 3px; }
            
            table, th, td{ font-size:88%; border-bottom: 1px solid black; border-collapse: collapse; }
            
            table{ margin-bottom: 0.5rem; }
            
            th, td{ padding:0.2rem; }
            
            td:nth-child(1){ width:30%; }
            
            td:nth-child(3){ width:40%; }
            
            th:nth-child(5), td:nth-child(5){ text-align: center; }
            
            article p{ line-height: 1.5; margin-bottom:0.5rem; }
            
            p > span{ border:1px solid var(--detalle); padding-right:0.2rem; font-size:88%; color:var(--detalle); margin-right:0.2rem }
            
            span.badge{ background:var(--detalle); color:white; padding:0 0.2rem; font-weight: bold; }
            
            footer{ font-size: 78%; margin:1rem .4rem; color:#999;}
        </style>
    </head>
    <body>
        <svg xmlns="http://www.w3.org/2000/svg" style="display: none;">
            <symbol id="pdf" viewBox="0 0 16 16" fill="currentColor">
                <path fill-rule="evenodd" d="M14 4.5V14a2 2 0 0 1-2 2h-1v-1h1a1 1 0 0 0 1-1V4.5h-2A1.5 1.5 0 0 1 9.5 3V1H4a1 1 0 0 0-1 1v9H2V2a2 2 0 0 1 2-2h5.5zM1.6 11.85H0v3.999h.791v-1.342h.803q.43 0 .732-.173.305-.175.463-.474a1.4 1.4 0 0 0 .161-.677q0-.375-.158-.677a1.2 1.2 0 0 0-.46-.477q-.3-.18-.732-.179m.545 1.333a.8.8 0 0 1-.085.38.57.57 0 0 1-.238.241.8.8 0 0 1-.375.082H.788V12.48h.66q.327 0 .512.181.185.183.185.522m1.217-1.333v3.999h1.46q.602 0 .998-.237a1.45 1.45 0 0 0 .595-.689q.196-.45.196-1.084 0-.63-.196-1.075a1.43 1.43 0 0 0-.589-.68q-.396-.234-1.005-.234zm.791.645h.563q.371 0 .609.152a.9.9 0 0 1 .354.454q.118.302.118.753a2.3 2.3 0 0 1-.068.592 1.1 1.1 0 0 1-.196.422.8.8 0 0 1-.334.252 1.3 1.3 0 0 1-.483.082h-.563zm3.743 1.763v1.591h-.79V11.85h2.548v.653H7.896v1.117h1.606v.638z" />
            </symbol>
        </svg>
        <div>
            <header>
                <h1><strong>diseño</strong>uc</h1>
                <h2>Memorias en el ámbito de 
                    <select>
                        <option value="Alimentación">Alimentación y Gastronomía</option>
                        <option value="plicadas">Artesanía y Artes Aplicadas</option>
                        <option value="Bienestar">Bienestar</option>
                        <option value="Ciencia">Ciencia y Tecnología</option>
                        <option value="Ciudad">Ciudad, Ambiente y Equipamiento</option>
                        <option value="Comunicación">Comunicación</option>
                        <option value="Cultura">Cultura, Historia y Religión</option>
                        <option value="Deporte">Deporte</option>
                        <option value="Empresa">Economía y Empresa</option>
                        <option value="Educación">Educación</option>
                        <option value="Entretenimiento">Entretenimiento</option>
                        <option value="Género">Identidad, Género</option>
                        <option value="Inclusión">Inclusión, Migración y Discapacidad</option>
                        <option value="Moda">Moda</option>
                        <option value="Salud">Salud</option>
                        <option value="Silvo-agropecuario">Silvo-agropecuario</option>
                        <option value="Sustentabilidad">Sustentabilidad</option>
                        <option value="Transporte">Transporte</option>
                        <option value="Turismo">Turismo</option>
                    </select>
                </h2>
            </header>
            <main>
                <h3>Memorias mejor evaluadas en el ámbito</h3>
                <article>
                    <table>
                        <thead>
                            <tr>
                                <th>Autor(a)</th>
                                <th>Año</th>
                                <th>Título</th>
                                <th>Prof. Guía</th>
                                <th>Nota</th>
                            </tr>
                        </thead>
                        <tbody></tbody>
                    </table>
                </article>

                <h3>Palabras habituales en el ámbito</h3>
                <article>
                    <p>Se reúnen todos los "para qué" de los proyectos y se seleccionan las palabras repetidas tres o más veces (descartando artículos, adverbios, preposiciones y conjunciones).</p>
                    <p id="palabreo"></p>
                </article>

                <h3>Notas promedio por Prof. Guía en el ámbito</h3>
                <article>
                    <p>El promedio de las calificaciones de memorias en este ámbito es de <em id="corte"></em>. Los promedios de las memorias guiadas por distintos profesores es el que sigue:</p>
                    <svg id="aqui"></svg>
                </article>
            </main>
            <footer>Datos de memorias presentadas entre primer semestre de 2018 y segundo semestre de 2023. Se descartaron memorias con calificaciones bajo el 5.0. También se descartan memorias sobre tal calificación cuando no está disponible su PDF o falta algún dato en su descripción.</footer>
        </div>

        <script>
            const tabla = document.querySelector("tbody");
            const visualizacion = document.querySelector("#aqui");
            const palabreo = document.querySelector("#palabreo");

            async function datos(criterio) {
                var seleccion = [];
                var profes = [];
                var nombres = [];
                var barras = [];
                var ambitos = [];
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/opr/refs/heads/main/clase-06/data.json");
                const data = await consulta.json();
                console.log("Lo que sigue son todos los datos:");
                console.log(data);

                //Creo una selección, basándome en el selector
                data.forEach((d) => {
                    if (d.ambito.includes(criterio)) {
                        seleccion.push(d);
                    }
                });
                console.log("Lo que sigue es una selección de los datos:");
                console.log(seleccion);
                
                //Trabajando con la selección, creo una tabla
                seleccion.forEach((s, i) => {
                    tabla.innerHTML += `<tr><td>${s.nombre_completo}.</td><td>${s.year}</td><td><a href="https://diseno.uc.cl/memorias/pdf/${s.nombre_pdf}" class="link-dark">${s.nombre_proyecto} <svg width="1em" height="1em"><use href="#pdf"></use></svg></a></td><td>${s.nombre_guia}</td><td class="text-center">${s.nota_titulo.toFixed(1)}</td></tr>`;
                    let obj = {};
                    obj["prof"] = `${s.nombre_guia}`;
                    obj["nota"] = `${s.nota_titulo}`;
                    profes.push(obj);
                    nombres.push(s.nombre_guia);
                });
                console.log("Lo que sigue son sólo los nombres, sin repetir:");
                nombres = [...new Set(nombres)].sort();
                console.log(nombres);
                
                //Basándome en nombres, armo un objeto con profesores
                nombres.forEach((x) => {
                    //prof sin repetir
                    let unProf = profes.filter((p) => p.prof === x);
                    //promedio de notas de cada prof
                    let average = unProf.reduce((a, b) => a + Number(b.nota), 0) / unProf.length;
                    let obj = {};
                    obj["prof"] = x;
                    obj["promedio"] = Number(average);
                    barras.push(obj);
                });
                console.log("Lo que sigue son promedios para cada nombre:");
                console.log(barras);

                //Forma más "clásica" de sacar promedio
                var i = 0;
                var total = 0;
                barras.forEach((barra) => {
                    total += barra.promedio;
                    i++;
                });
                var corte = total / i;
                document.querySelector("#corte").innerHTML = corte.toFixed(2);
                var ajuste = 0;
                let mayor = 0;
                barras.forEach((x) => {
                    mayor = Math.max(mayor, x.promedio);
                        visualizacion.innerHTML += `<g transform="translate(0 ${ajuste * 3})"><rect x="0" y="0" height="2" width="70" fill="#eee"></rect><rect x="0" y="0" height="2" width="${x.promedio.toFixed(1) * 10}" fill="var(--detalle)"></rect><text fill="white" font-size="1.2" x="0.5" y="1.4" font-weight="bold">${x.prof}</text><text fill="white" font-size="1.2" x="${x.promedio.toFixed(1) * 10 - 2.5}" y="1.4">${x.promedio.toFixed(1)}</text></g>`;
                        ajuste++;
                });
                visualizacion.innerHTML += `<line x1="${mayor.toFixed(1) * 10}" y1="0" x2="${mayor.toFixed(1) * 10}" y2="${ajuste * 3}" stroke="white" stroke-width="0.1"/>`;
                var proporcion = "0 0 70 " + ajuste * 3;
                visualizacion.setAttribute("viewBox", proporcion);
                
                //Buscando las palabras frecuentes del "para qué" en su selección
                var words = "";
                seleccion.forEach((s) => (words = words + " " + s.para_que));
                var palabras = words.split(" ");
                palabras = palabras.sort();
                const nopalabras = ["","a","al","así","como","con","de","De","del","dentro","desde","e","el","El","en","entre","esta","este","esto","estos","fin","hacia","la","las","le","les","lo","los","más","mediante","no","o","para","por","que","qué","se","sin","sobre","son","su","sus","tanto","través","un","una","unas","unos","vez","y"];
                const sacaPalabras = (arreglo, sacar) => {
                    return arreglo.filter((palabra) => {
                        return !sacar.includes(palabra);
                    });
                };
                var palabrasAcotadas = sacaPalabras(palabras, nopalabras);
                const cuentaRepeticiones = (arreglo = []) => {
                    const resultado = [];
                    arreglo.forEach((el) => {
                        const index = resultado.findIndex((obj) => {
                            return obj["name"] === el;
                        });
                        if (index === -1) {
                            resultado.push({
                                name: el,
                                count: 1,
                            });
                        } else {
                            resultado[index]["count"]++;
                        }
                    });
                    return resultado;
                };
                var total = cuentaRepeticiones(palabrasAcotadas);
                total.forEach((x) => {
                    if (x.count >= 3) {
                        palabreo.innerHTML += `<span><span class="badge">${x.count}</span> ${x.name}</span> `;
                    }
                });
            }

            datos("Alimentación").catch((error) => console.error(error));

            document.querySelector("select").addEventListener("change", (event) => {
                tabla.innerHTML = " ";
                visualizacion.innerHTML = " ";
                palabreo.innerHTML = " ";
                console.clear();
                var seleccion = [];
                var profes = [];
                var nombres = [];
                var barras = [];
                var ambitos = [];
                datos(event.target.value).catch((error) => console.error(error));
            });
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-05) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-07)
