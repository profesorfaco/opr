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

- Paso 2: Uso del example Album en https://getbootstrap.com/docs/5.3/examples/ con adaptaciones ya indicadas.

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

|	Nombres		|	Entrega en foro	| Trabaja para… |
|:-------------|:---------|:-----------|
|	AGUSTÍN	AVENDAÑO	|	https://agustin070702.github.io/decimaClase/	| [Josefina Castro](https://github.com/josecastrod/) |
|	AYLEEN	BAHAMÓNDEZ	|	https://ayleenba23.github.io/Clase-10/	| [Bárbara Trabert](https://github.com/barbaratrabert/) |
|	SOFÍA	BASSALETTI	|	https://mbassaletti.github.io/clase10/	| [Rosario Fuentes](https://github.com/rosi2701/) |
|	CATALINA	BUSTOS	|	https://catita-b.github.io/web_clase10/	| [Pía Canales](https://github.com/piacanalesr/) |
|	PÍA	CANALES	|	https://piacanalesr.github.io/webo_10/	| [Catalina Bustos](https://github.com/catita-b/) |
|	JASMÍN	CASTILLO	|	https://jasmcastillo-dev.github.io/Clase-10/	| [Josefa Pérez](https://github.com/josefa020/) |
|	JOSEFINA	CASTRO	|	https://josecastrod.github.io/Clase-9/	| [Agustín Avendaño](https://github.com/agustin070702/) |
|	JUAN CARLOS	CONTRERAS	|	https://juancarlos2docontreras.github.io/NovenaClase/	| Javiera Baldebenito |
|	JAVIERA	DONOSO	|	https://javy3003.github.io/decima-clase/	| [Matilde Flores](https://github.com/matildeflvi/) |
|	CAMILA	FALCON	|	—	| — |
|	MATILDE	FLORES	|	https://matildeflvi.github.io/decima_clase/	|[ María Ignacia Orellana](https://github.com/marita03/) |
|	ROSARIO	FUENTES	|	https://rosi2701.github.io/decimaClase/	| [Pamela Jorquera](https://github.com/pameee73/) |
|	ANTONIA	GARCÉS	|	—	| [Bárbara Trabert](https://github.com/barbaratrabert/) |
|	FERNANDA	HUMERES	|	https://mikuby11.github.io/Clase_10/	| [Magdalena Rivas](https://github.com/magdarivas/) |
|	NOUR	JALILIE	|	https://nourjalilie.github.io/Clase10/	| [Ambar Martin](https://github.com/lavendas/) |
|	PAMELA	JORQUERA	|	https://pameee73.github.io/17-10new/	| [Rosario Fuentes](https://github.com/rosi2701/) |
|	LIVKA	KUTZ	|	https://l1vk4.github.io/10ma-clase/	| [Ayleen Bahamondez](https://github.com/ayleenba23/) |
|	ANTONIA	LABRA	|	https://ant-nia.github.io/c10/	| [Matilde Flores](https://github.com/matildeflvi/) |
|	AMBAR	MARTIN	|	https://lavendas.github.io/Clase10/	| [Nour Jalilie](https://github.com/nourjalilie/) |
|	MARÍA	IGNACIA ORELLANA	|	https://marita03.github.io/clase10.2/	| [Matilde Flores](https://github.com/matildeflvi/) |
|	JOSEFA	PÉREZ	|	https://josefa020.github.io/clase-10/	| [Jazmín Castillo](https://github.com/jasmcastillo-dev) |
|	MARÍA	PUELMA	|	https://isapuelma.github.io/Clase.10/	| [Javiera Valdebenito](https://github.com/javaaa000/) |
|	AMANCAY	RAMÍREZ	|	https://loubingui.github.io/Clase_10/	| [Magdalena Rivas](https://github.com/magdarivas/) |
|	MAGDALENA	RIVAS	|	https://magdarivas.github.io/clase10/	| [Javiera Valdebenito](https://github.com/javaaa000/) |
|	PALOMA	ROJAS	|	—	| [Amancay Ramirez](https://github.com/loubingui/) |
|	ANNA	SCHAEFERS	|	https://deleteandescape.github.io/clase-10/	| [Rosario Fuentes](https://github.com/rosi2701/) |
|	FLORENCIA	SEGRETTI	|	https://flosegretti.github.io/clase10/	| [María Ignacia Orellana](https://github.com/marita03/) |
|	ANAIS	SILVA	|	—	| — |
|	BÁRBARA	TRABERT	|	https://barbaratrabert.github.io/clase-10/	| [Livka Kutz](https://github.com/l1vk4/) |
|	JAVIERA	VALDEBENITO	|	https://javaaa000.github.io/decima_clase/	| [Magdalena Rivas](https://github.com/magdarivas/) |



- - - - - - - 

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/opr/tree/main/clase-10) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-13)
