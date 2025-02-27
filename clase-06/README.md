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
        <title>Partiendo la quinta clase</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous" />
        <style>
            image {
                filter: grayscale(1);
                opacity: 0.3;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col">
                    <!--hagamos una tabla-->
                </div>
            </div>
        </div>
        <script>
            var seleccion = [];
            var ambitos = [];
            async function datos() {
                const consulta = await fetch("https://raw.githubusercontent.com/profesorfaco/opr/main/clase-06/data.json");
                const data = await consulta.json();
                console.log(data);

                //acortemos los datos con ámbito y pdf
                
                data.forEach(d => {
                    d.nota_titulo = parseFloat(d.nota_titulo.replace(",", "."));
                    d.nota_pga = parseFloat(d.nota_pga.replace(",", "."));
                    d.nota_seminario = parseFloat(d.nota_seminario.replace(",", "."));
                    d.year = Number(d.year);
                    d.pdf_ok = Number(d.pdf_ok);
                    ambitos.push(d.ambito);
                    if(d.ambito == "Educación" && d.pdf_ok == 1){
                        seleccion.push(d)
                    }
                });
                console.log(seleccion);

                //Veamos cuáles son los ámbitos no repetidos entre 1400
                
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

Pueden notar que que hay un `if()` que tiene un `&&` que significa "y", de esto y esto también.

Previamente pudieron notar el `parseFloat()` y el `Number()`, además del `replace(",", ".")`. Estos nos ayudan a preparar los datos para su tratamiento.

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-05) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-07)
