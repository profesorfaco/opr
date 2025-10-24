### Introducción al desarrollo web desde el diseño → Clase 11 → 24/10/2025

# Evaluación N°3

El 20% de la nota final se obtiene con: 

**1,0 punto base**.

**3,0 puntos** por:

- CLASE 09 - hasta el 16 de oct 23:59

- CLASE 10 - hasta 20 de octubre 23.59 

- CLASE 10 - Re-entrega - hasta 23 de octubre 23.59 (revisaré correcciones en el repositorio presentado en foro de discusión original, ya cerrado y comentado; quienes hayan recibido comentario positivo, sin indicación de ajuste, no necesitan comentar en este foro)

**3,0 puntos** por los siguientes 3 pasos: 

- Paso 1: Uso del JSON que se le indique para completar el portafolio de compañerx de curso.

- Paso 2: Uso del example Album en https://getbootstrap.com/docs/5.3/examples/

- Paso 3: Uso de la “lógica de programación” presentada en clases para el despliegue de las habilidades y el portafolio.


- - - - - - - 

En algunos casos podría mostrarse un error 429 en lugar del JSON.

En [Google, usando su modo IA](https://www.google.com/), podrían *buscar*: error 429 github pages json

Para evitarlo, sin complejizar, se recomienda usar https://myjson.online/

Al momento de publicar su JSON en tal plataforma, corresponde considerar que habrá un cambio en la estructura.

La estructura original quedará dentro de `data` 

```
{
"data”:[…],
"id": "serie de caracteres",
"version": número,
"displayName": "nombre"
}
```

Para ir por los datos dentro de `data`, habría que agregar una línea al `script.js`:

```
let consulta = await fetch(raw);
let resultado = await consulta.json();
let trabajos = resultado.data;
console.log(trabajos);
```

En la línea se agrega la variable `resultado`, para luego apuntar con la variable `trabajos` a una parte de la variable agregada.


- - - - - - - 

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/opr/tree/main/clase-10) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-13)
