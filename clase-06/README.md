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
        <title>Partiendo la sexta clase</title>
        <style>
            *{ padding:0; margin:0; }
            body{ text-align: center; }
            main{ margin:5vh auto;}
        </style>
    </head>
    <body>
        <main>
        </main>
        <script>
            var ambitos = [];
            async function datos() {
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/opr/main/clase-06/data.json");
                const data = await consulta.json();
                console.log(data);
                data.forEach((d)=>{ambitos.push(d.ambito)});
                console.log(ambitos);
                const ambitosOK = [...new Set(ambitos)];
                ambitosOK.sort();
                console.log(ambitosOK);
            }
            datos().catch((error) => console.error(error));
        </script>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-05) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-07)
