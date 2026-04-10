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

Pendiente (corresponde ajustarlo según su avance).

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-04) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-07)
