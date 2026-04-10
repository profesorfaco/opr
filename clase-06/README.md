### Optativo de Profundización: [Desarrollo Web y Diseño Visual de Información](https://github.com/profesorfaco/opr/?tab=readme-ov-file#readme) → Clase 06 → 10/04/2026

# Formatos ligeros de intercambios de datos (clase 2 de 2)

### Teoría (para la casa)

JSON (JavaScript Object Notation): Formato ligero de intercambio de datos, fácil de leer y escribir para los humanos y fácil de analizar y generar para las máquinas. Su bloque constructivo básico es el par "clave": valor, organizado dentro de llaves `{...}` para objetos o corchetes `[...]` para arreglos.

Para profundizar: [Trabajando con JSON en MDN](https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/JSON).

Desde tal recomendación de profundización, podemos obtener este ejemplo:

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

En este intercambio de datos tenemos un arreglo, que en su primera `[0]` y segunda posición `[1]` nos ofrece objetos `{…}`, y dentro de cada objeto podemos encontrar claves que contienen cadenas de caracteres entre comillas, números (sin comillas) y arreglos.

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Pendiente (corresponde ajustarlo según su avance).

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-04) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-07)
