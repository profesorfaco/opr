### Introducción al desarrollo web desde el diseño → Clase 10 → 17/10/2025 

# Comprendiendo Bootstrap

```
const portfolio = document.querySelector("#porotito");

async function datos(raw) {
    try {
        let consulta = await fetch(raw);
        let trabajos = await consulta.json();
        console.log(trabajos);
        trabajos.forEach((trabajo) => {
            portfolio.innerHTML += `

                            <div class="col">
                                <div class="card shadow-sm">
                                <img src="${trabajo.imagen}" class="card-img-top">
                                <div class="card-body">
                                <p class="card-text">${trabajo.titulo}</p>
                                <div class="d-flex
                                justify-content-between
                                align-items-center">
                                <div class="btn-group">
                                <button type="button" class="btn btn-sm btn-outline-secondary">${trabajo.categoria}</button>
                                </div>
                                <small class="text-body-secondary">Reciente </small>
             </div>
             </div>
            </div>
            </div>`;
        });
    } catch (error) {
        console.error("Error al cargar los datos:", error);
    }
}

datos("https://raw.githubusercontent.com/profesorfaco/clase-10/refs/heads/main/datos.json");
```

- - - - - - - 

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/opr/tree/main/clase-09) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-11)
