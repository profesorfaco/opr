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
    </head>
    <body>
        <script>
            async function datos() {
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/opr/main/clase-05/datos.json");
                const data = await consulta.json();
                console.log(data);
                //armaré un arreglo
                var profes = [];
                data.forEach((x) => { profes.push(x.tutor); });
                console.log(profes);
                //armaré un objeto
                var cuenta = {};
                profes.forEach((y) => {cuenta[y] = (cuenta[y] || 0) + 1});
                document.write(JSON.stringify(cuenta));
            }
            datos().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-04) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-06)
