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

El parecido entre lo que es, originalmente, *JavaScript Object Notation* y el formato JSON, nos permite prescindir de alguna biblioteca de Javascript que simplifican el *fetch* y *parsing* (como hicimos [la clase recién pasada](https://github.com/profesorfaco/opr/tree/main/clase-04), con PapaParse); es **suficiente [esperar](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/await) el resultado de un [fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch) que debe intepretarse como [json](https://developer.mozilla.org/en-US/docs/Web/API/Response/json)**: 

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
        <style>
            * { margin: 0; padding: 0; }
            body { font-family: monospace; text-align: center; }
            table { margin: 5vh auto; text-align: left; }
            table tr td { padding: 0.3rem; }
            table tr td:nth-child(1) { color: #aaa; text-align: right; padding-right: 1rem; }
            table tr td:nth-child(2) { font-weight: bolder; }
        </style>
    </head>
    <body>
        <table></table>
    <script>
            const visualizacion = document.querySelector("table");
            function plecas(numero){
                var visual = "";
                for(let x = 0; x < numero; x++){
                    visual = visual+"|";
                }
                return visual;
            }
            async function datos() {
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/opr/main/clase-05/datos.json");
                const data = await consulta.json();
                // ya tengo los datos de proyectos con nota 7
                console.log(data);
                // ahora armo un arreglo que tengan sólo nombres de Profes'
                var profes = [];
                data.forEach((x) => {profes.push(x.tutor)});
                console.log(profes);
                // https://gist.github.com/ralphcrisostomo/3141412?permalink_comment_id=2315571#gistcomment-2315571 
                // puedo contar las veces que se repiten los nombres de cada Profe'
                var conteo = profes.reduce((a,b)=>((a[a.findIndex(d=>d.profesor===b)]||a[a.push({profesor:b,veces:0})-1]).veces++,a),[]);
                console.log(conteo);
                // creo otra variable, a la que empujaré nombres de Profes' con una condición
                var nombres = [];
                conteo.forEach((x) => {
                    visualizacion.innerHTML+=`<tr><td>${x.profesor}</td><td>${plecas(x.veces)}</td></tr>`;
                    if (x.veces > 3) { nombres.push(x.profesor) }
                });
                // revisemos el siguiente dato en la consola para avanzar
                console.log("HAN GUIADO A MÁS DE TRES NOTAS SIETE: " + nombres);
            }
            datos().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-04) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-06)
