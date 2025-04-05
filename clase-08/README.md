### Optativo de Profundización: Desarrollo Web y Diseño Visual de Información → Clase 08 → 23/04/2025

# Gráficas y datos en diseño web responsive: SVG y HTML

### Teoría (para la casa)



- - - - - - - - - - - - - - 

### Práctica (para la clase)

Pero partamos por acá:

```
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>¿Qué sucede?</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous" />
    </head>
    <body>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" class="d-none d-md-block">
            <title>51_Avalanche_v15</title>
            <path d="M94.28,85.31a8.77,8.77,0,0,1-8.86,8.61H5.72V58.61l14.14-35.3,8.25-2.95h1.35l7.26,2.95L63.28,76.08c1.85,3.57,2.71,4.3,6,4.3h2.83L71,84.32H68.94c-4.79,0-6.76-.86-9.59-6.27L33.52,27.74l-4.8-2.09-5.53,2.09L13.1,52l8.36-3.56,8.61,5.65L39.54,52l16,31.37C57.87,87.89,60.82,90,67.71,90H85.42a4.68,4.68,0,1,0-4.67-4.67H76.81a8.67,8.67,0,0,1,8.61-8.74h.13a4.78,4.78,0,0,0-4.43-3.32,4.65,4.65,0,0,0-4.67,4.55H72.39a8.74,8.74,0,0,1,8.73-8.61c4.67,0,8.36,3.2,8.49,8.49A8.77,8.77,0,0,1,94.28,85.31ZM65.5,69.19,54.92,48h1.72l5.78,5.65,6.89,13.78a1.62,1.62,0,0,0,1.85,1.11h1.6l-1.23,3.93h-.62C67.84,72.51,67,72.14,65.5,69.19ZM59.35,31.43l12.3-6.76L59.35,17.9,61.56,14l12.06,7.38L73.25,7.2h4.67l-.37,14L89.48,14l2.34,3.94-12.3,6.77,12.3,6.76-2.34,3.94L77.55,28.11l.37,14H73.25L73.62,28,61.56,35.37Z"></path>
        </svg>

        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" class="d-md-none">
            <title>53_Alarm_v15</title>
            <path d="M22.82,34.26a3.72,3.72,0,0,1-5.29,0L9.9,26.63a3.84,3.84,0,0,1,0-5.29,3.57,3.57,0,0,1,5.17,0L22.82,29A3.72,3.72,0,0,1,22.82,34.26ZM73.74,58.49l1.11,16.73v6.64H50v-36H43.85c-4.55,0-9.23,2.33-10.09,13.41L32.53,75.46v6.4H25.15V75.22l1.23-16.73c.74-10.7,5.78-20.05,17.47-20.05H56.27C67.71,38.44,73,47.29,73.74,58.49ZM25.15,87.39h49.7v5.54H25.15Zm21.16-65.8V10.76A3.78,3.78,0,0,1,50,7.07a3.7,3.7,0,0,1,3.69,3.69V21.59A3.71,3.71,0,0,1,50,25.28,3.79,3.79,0,0,1,46.31,21.59ZM90.1,26.88,82.47,34.5a3.69,3.69,0,1,1-5.29-5.16l7.75-7.75a3.79,3.79,0,0,1,5.17,0A3.84,3.84,0,0,1,90.1,26.88Z"></path>
        </svg>
    </body>
</html>
```

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-07) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-10)
