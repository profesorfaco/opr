### Optativo de Profundización: [Desarrollo Web y Diseño Visual de Información](https://github.com/profesorfaco/opr/?tab=readme-ov-file#readme) → Clase 06 → 10/04/2026

# Formatos ligeros de intercambios de datos (clase 2 de 2)

### Teoría (para la casa)

JSON (JavaScript Object Notation): Formato ligero de intercambio de datos, fácil de leer y escribir para los humanos y fácil de analizar y generar para las máquinas. Su bloque constructivo básico es el par "clave": valor, organizado dentro de llaves `{...}` para objetos o corchetes `[...]` para arreglos.

Para profundizar: [Trabajando con JSON en MDN](https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/JSON).

Desde tal referencia para profundizar, podemos obtener este ejemplo:

```
[
  {
    "name": "Molecule Man",
    "age": 29,
    "secretIdentity": "Dan Jukes",
    "powers": ["Radiation resistance", "Turning tiny", "Radiation blast"]
  },
  {
    "name": "Madame Uppercut",
    "age": 39,
    "secretIdentity": "Jane Wilson",
    "powers": ["Million tonne punch","Damage resistance","Superhuman reflexes"]
  }
]
```

En el ejemplo tenemos un arreglo, que en su primera `[0]` y segunda posición `[1]` nos ofrece objetos `{…}`, y dentro de cada objeto podemos encontrar claves que contienen cadenas de caracteres entre comillas, números (sin comillas) y arreglos.

Y aprovechando [la misma referencia de MDN](https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/JSON), podemos agregar: 

- JSON es sólo un formato de datos — contiene sólo propiedades, no métodos.

- JSON requiere usar comillas dobles para las cadenas y los nombres de propiedades. Las comillas simples no son válidas.

- Una coma o dos puntos mal ubicados pueden producir que un archivo JSON no funcione. Se debe ser cuidadoso para validar cualquier dato que se quiera utilizar (aunque los JSON generados por computador tienen menos probabilidades de tener errores, mientras el programa generador trabaje adecuadamente). Es posible validar JSON utilizando una aplicación como [JSONLint](https://jsonlint.com/).

- JSON puede tomar la forma de cualquier tipo de datos que sea válido para ser incluido en un JSON, no sólo arreglos u objetos. Así, por ejemplo, una cadena o un número único podrían ser objetos JSON válidos.

- A diferencia del código JavaScript en que las propiedades del objeto pueden no estar entre comillas, en JSON, sólo las cadenas entre comillas pueden ser utilizadas como propiedades.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Para partir, vamos a utilizar:

- https://github.com/profesorfaco/opr/blob/main/clase-06/registros.csv

- https://csvjson.com/csv2json

Lo que nos dará por resultado:

```
[
  {
    "id": 1,
    "nombre": "María Jesús Alegría Cotoras",
    "cuenta": "https://github.com/mjcotoras",
    "uno": "https://mjcotoras.github.io/dno002-01/",
    "dos": "https://mjcotoras.github.io/dn002-02/",
    "tres": "https://mjcotoras.github.io/dno002-03/",
    "cuatro": ""
  },
  {
    "id": 2,
    "nombre": "Florencia Catalina Benavente Mena",
    "cuenta": "",
    "uno": "",
    "dos": "",
    "tres": "",
    "cuatro": ""
  },
  {
    "id": 3,
    "nombre": "Rosario Sofia Fuentes Carrizo",
    "cuenta": "https://github.com/rosi2701",
    "uno": "https://rosi2701.github.io/webclase1/",
    "dos": "https://rosi2701.github.io/webclase2/",
    "tres": "https://rosi2701.github.io/webclase3/",
    "cuatro": "https://rosi2701.github.io/webclase4/"
  },
  {
    "id": 4,
    "nombre": "Florencia Asunción García Pardo",
    "cuenta": "https://github.com/FloAGarciaP",
    "uno": "",
    "dos": "https://floagarciap.github.io/DNO002-01/",
    "tres": "https://floagarciap.github.io/DNO002-3/",
    "cuatro": "https://floagarciap.github.io/DNO002-4/"
  },
  {
    "id": 5,
    "nombre": "Paz Ignacia Lienlaf Vargas",
    "cuenta": "https://github.com/jjugodemango",
    "uno": "https://jjugodemango.github.io/DNO-WEB-clase1/",
    "dos": "https://jjugodemango.github.io/DNO-WEB-clase2/",
    "tres": "https://jjugodemango.github.io/DNO-WEB-clase3/",
    "cuatro": "https://jjugodemango.github.io/DNO-WEB-clase4/"
  },
  {
    "id": 6,
    "nombre": "Pedro Montes Silveira",
    "cuenta": "https://github.com/PedroMS7002",
    "uno": "https://pedroms7002.github.io/clase01-web/",
    "dos": "",
    "tres": "",
    "cuatro": ""
  },
  {
    "id": 7,
    "nombre": "Matias Pablo Reyes Sánchez",
    "cuenta": "https://github.com/MrMathew18",
    "uno": "",
    "dos": "https://mrmathew18.github.io/viz-clase2/",
    "tres": "https://mrmathew18.github.io/viz-clase3/",
    "cuatro": "https://mrmathew18.github.io/opr4/"
  },
  {
    "id": 8,
    "nombre": "Antonia Belen Rojas Farias",
    "cuenta": "https://github.com/AntoRojasf",
    "uno": "https://antorojasf.github.io/Desarrollo-web-2026/index.html",
    "dos": "https://antorojasf.github.io/Clase2/",
    "tres": "https://antorojasf.github.io/clase-3/",
    "cuatro": "https://antorojasf.github.io/clase-4-/"
  },
  {
    "id": 9,
    "nombre": "Valentina Luz Sarrat Tornero",
    "cuenta": "https://github.com/valentinasarrat",
    "uno": "",
    "dos": "https://valentinasarrat.github.io/opr02/",
    "tres": "https://valentinasarrat.github.io/opr03/",
    "cuatro": "https://valentinasarrat.github.io/opr04/"
  },
  {
    "id": 10,
    "nombre": "Florencia Maria Verdier Fernández",
    "cuenta": "https://github.com/florenciaverdier",
    "uno": "",
    "dos": "https://florenciaverdier.github.io/Clase-2/",
    "tres": "https://florenciaverdier.github.io/Clase-3/",
    "cuatro": "https://florenciaverdier.github.io/Clase-4/"
  }
]
```

Esto lo podemos a publicar en [myjson](https://myjson.online/)

Y si queda bien publicado, luego podemos trabajar con: 

```
<!doctype html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Un fetch</title>
    </head>
    <body>
        <h1>Hola mundo</h1>

        <script>
            // 1. Definimos la URL de la API que queremos consultar
            const URL = "https://api.myjson.online/v1/records/a5902166-9172-4f15-a4cc-c404b1372dc7";

            // 2. Usamos fetch() — es una función nativa del navegador
            //    que realiza peticiones HTTP de forma asíncrona
            fetch(URL)
                // 3. fetch() devuelve una "promesa"
                //    .then() se ejecuta cuando la respuesta llega
                .then((respuesta) => {
                    // 4. Verificamos que el servidor respondió con éxito (código 200-299)
                    if (!respuesta.ok) {
                        throw new Error("Error HTTP: " + respuesta.status);
                    }

                    // 5. Convertimos el cuerpo de la respuesta de texto JSON
                    //    a un objeto JavaScript. Esto también es asíncrono.
                    return respuesta.json();
                })

                // 6. Ahora "datos" es el objeto JavaScript listo para usar
                .then((datos) => {
                    console.log("Datos recibidos:", datos);
                })

                // 7. Si algo falló (red caída, error del servidor, etc.)
                //    este bloque lo captura
                .catch((error) => {
                    console.error("Algo salió mal:", error);
                });
        </script>
    </body>
</html>
```




- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-04) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-07)
