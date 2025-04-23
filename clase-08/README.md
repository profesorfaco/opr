### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 08 → 23/04/2025

# Gráficas y datos en diseño web responsive: SVG y HTML

### Teoría (para la casa)

Repasaremos lo tratado en clases previas con los siguientes datos reales:

**Tengo sus notas en *Google Spreadsheets***.

Por defecto, *Google* pone a España en la Configuración de cada Archivo creado. 

Por eso tengo que ir a `Archivo → Configuración → Configuración regional`. 

Cambio a `España` por `Estados Unidos` (o cualquier otro país de habla inglesa) para que los números se escriban al modo que lo entienda [JavaScript](https://www.w3schools.com/js/js_numbers.asp)

Teniendo mis número en inglés (con los decimales separados por puntos, nunca comas), puedo aprovecharme de otra herramienta: https://csvjson.com/csv2json

Y con tal herramienta pude generar: https://raw.githubusercontent.com/profesorfaco/opr/refs/heads/main/clase-08/notas.json

Para trabajar con lo generado, podemos usar [fetch](https://www.w3schools.com/js/js_api_fetch.asp): 

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Las notas</title>
    </head>
    <body>
        <h1>Hola mundo!</h1>
        <script>
            async function notas(raw) {
                let consulta = await fetch(raw);
                let data = await consulta.json();
                console.log(data);
            }
            notas("https://raw.githubusercontent.com/profesorfaco/opr/refs/heads/main/clase-08/notas.json").catch((error) => console.error(error));
        </script>
    </body>
</html>
```

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Repasaremos lo tratado en clases previas.

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-07) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-10)
