### Introducción al desarrollo web desde el diseño → Clase 13 → 07/11/2025

# Diseño y desarrollo de su primer sitio web profesional o prototipo avanzado de aplicación web

Para mejorar el código en el README.md de la clase 10, una primera alternativa: 

```
const portfolio = document.querySelector("#porotito");

// Función para escapar HTML y prevenir XSS
function escapeHTML(str) {
    const div = document.createElement('div');
    div.textContent = str;
    return div.innerHTML;
}

async function datos(raw) {
    try {
        let consulta = await fetch(raw);
        if (consulta.status === 429) {
            await new Promise(resolve => setTimeout(resolve, 2000));
            consulta = await fetch(raw);
        }
        let trabajos = await consulta.json();
        console.log(trabajos);
        trabajos.forEach((trabajo) => {
            portfolio.innerHTML += `
                <div class="col">
                    <div class="card shadow-sm">
                        <img src="${escapeHTML(trabajo.imagen)}" class="card-img-top">
                        <div class="card-body">
                            <p class="card-text">${escapeHTML(trabajo.titulo)}</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <div class="btn-group">
                                    <button type="button" class="btn btn-sm btn-outline-secondary">${escapeHTML(trabajo.categoria)}</button>
                                </div>
                                <small class="text-body-secondary">Reciente</small>
                            </div>
                        </div>
                    </div>
                </div>`;
        });
    } catch (error) {
        console.error("Error al cargar los datos:", error);
    }
}

// Esperar a que el DOM esté listo antes de ejecutar
if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', () => {
        datos("https://raw.githubusercontent.com/profesorfaco/clase-10/refs/heads/main/datos.json");
    });
} else {
    datos("https://raw.githubusercontent.com/profesorfaco/clase-10/refs/heads/main/datos.json");
}
```

Cambios Implementados por Claude, en palabras de Claude: 

**1. Protección contra XSS (Cross-Site Scripting)**: Agregué la función escapeHTML() que convierte caracteres especiales a entidades HTML. Escapo todos los datos que vienen del JSON: imagen, titulo y categoria. Esto previene que código malicioso en los datos se ejecute en el navegador.

**2. DOM Ready**: Agregué verificación de `document.readyState`. Si el documento aún está cargando, espera al evento DOMContentLoaded. Si ya está listo, ejecuta inmediatamente

**3. En caso de error 429**: Agregué un manejo simple del error 429 (Too Many Requests). Si detecta un error 429, espera 2 segundos automáticamente. Luego reintenta la solicitud una vez más. Esto soluciona el problema más común de rate limiting sin complicar demasiado el código.

**La mejora descrita responde a los mínimos necesarios. Si se necesita una mejora mayor, para un trabajo completamente seguro podemos volver a pedirle ayuda a Claude, que/quien identifica los siguientes problemas de seguridad:**

1. **XSS en atributo src**: Aunque escapas el HTML, al usar escapeHTML() en el atributo src de una imagen, no estás previniendo inyección de JavaScript a través de URLs maliciosas como javascript:alert(1)

2. **innerHTML con contenido dinámico**: Usar innerHTML += con datos externos es peligroso, incluso con escape básico

3. **Falta de validación de URL**: No verificas que la URL de la imagen sea legítima

4. **Falta de Content Security Policy**: No hay protección contra carga de recursos externos

5. **Error handling insuficiente**: Los errores se logean en consola exponiendo información

Después de identificar tales problemas, la misma Inteligencia Artificial propone: 

```
const portfolio = document.querySelector("#porotito");

// Lista blanca de dominios permitidos para imágenes
const ALLOWED_IMAGE_DOMAINS = [
    'raw.githubusercontent.com',
    'github.com',
    'i.imgur.com',
    'images.unsplash.com'
];

// Función mejorada para validar y sanitizar URLs
function sanitizeImageURL(url) {
    try {
        const urlObj = new URL(url);
        
        // Solo permitir protocolos seguros
        if (!['http:', 'https:'].includes(urlObj.protocol)) {
            return null;
        }
        
        // Verificar dominio contra lista blanca
        const isAllowed = ALLOWED_IMAGE_DOMAINS.some(domain => 
            urlObj.hostname === domain || urlObj.hostname.endsWith('.' + domain)
        );
        
        if (!isAllowed) {
            console.warn('Dominio no permitido:', urlObj.hostname);
            return null;
        }
        
        return urlObj.href;
    } catch (e) {
        console.warn('URL inválida:', url);
        return null;
    }
}

// Función para escapar HTML y prevenir XSS
function escapeHTML(str) {
    if (typeof str !== 'string') return '';
    const div = document.createElement('div');
    div.textContent = str;
    return div.innerHTML;
}

// Función para crear elemento de forma segura usando DOM API
function createWorkCard(trabajo) {
    const col = document.createElement('div');
    col.className = 'col';
    
    const card = document.createElement('div');
    card.className = 'card shadow-sm';
    
    // Validar y sanitizar URL de imagen
    const sanitizedImageURL = sanitizeImageURL(trabajo.imagen);
    if (sanitizedImageURL) {
        const img = document.createElement('img');
        img.className = 'card-img-top';
        img.src = sanitizedImageURL;
        img.alt = escapeHTML(trabajo.titulo || 'Imagen del proyecto');
        // Prevenir que la imagen cargue scripts
        img.referrerPolicy = 'no-referrer';
        card.appendChild(img);
    }
    
    const cardBody = document.createElement('div');
    cardBody.className = 'card-body';
    
    const cardText = document.createElement('p');
    cardText.className = 'card-text';
    cardText.textContent = trabajo.titulo || 'Sin título';
    cardBody.appendChild(cardText);
    
    const flexDiv = document.createElement('div');
    flexDiv.className = 'd-flex justify-content-between align-items-center';
    
    const btnGroup = document.createElement('div');
    btnGroup.className = 'btn-group';
    
    const button = document.createElement('button');
    button.type = 'button';
    button.className = 'btn btn-sm btn-outline-secondary';
    button.textContent = trabajo.categoria || 'General';
    btnGroup.appendChild(button);
    
    const small = document.createElement('small');
    small.className = 'text-body-secondary';
    small.textContent = 'Reciente';
    
    flexDiv.appendChild(btnGroup);
    flexDiv.appendChild(small);
    cardBody.appendChild(flexDiv);
    card.appendChild(cardBody);
    col.appendChild(card);
    
    return col;
}

async function datos(raw) {
    try {
        // Validar URL de la API
        const apiURL = new URL(raw);
        if (!['http:', 'https:'].includes(apiURL.protocol)) {
            throw new Error('Protocolo no seguro');
        }
        
        let consulta = await fetch(raw, {
            method: 'GET',
            headers: {
                'Accept': 'application/json'
            },
            // Evitar enviar credenciales
            credentials: 'omit'
        });
        
        if (consulta.status === 429) {
            await new Promise(resolve => setTimeout(resolve, 2000));
            consulta = await fetch(raw, {
                method: 'GET',
                headers: {
                    'Accept': 'application/json'
                },
                credentials: 'omit'
            });
        }
        
        if (!consulta.ok) {
            throw new Error(`HTTP error! status: ${consulta.status}`);
        }
        
        const trabajos = await consulta.json();
        
        // Validar que sea un array
        if (!Array.isArray(trabajos)) {
            throw new Error('Formato de datos inválido');
        }
        
        // Limitar cantidad de elementos para prevenir DoS
        const MAX_ITEMS = 100;
        const trabajosLimitados = trabajos.slice(0, MAX_ITEMS);
        
        // Usar DocumentFragment para mejor rendimiento
        const fragment = document.createDocumentFragment();
        
        trabajosLimitados.forEach((trabajo) => {
            // Validar estructura básica del objeto
            if (trabajo && typeof trabajo === 'object') {
                const card = createWorkCard(trabajo);
                fragment.appendChild(card);
            }
        });
        
        portfolio.appendChild(fragment);
        
    } catch (error) {
        // No exponer detalles técnicos al usuario
        console.error("Error al cargar los datos");
        
        // Mostrar mensaje genérico al usuario
        const errorDiv = document.createElement('div');
        errorDiv.className = 'alert alert-warning';
        errorDiv.textContent = 'No se pudieron cargar los proyectos en este momento.';
        portfolio.appendChild(errorDiv);
    }
}

// Esperar a que el DOM esté listo antes de ejecutar
if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', () => {
        datos("https://raw.githubusercontent.com/profesorfaco/clase-10/refs/heads/main/datos.json");
    });
} else {
    datos("https://raw.githubusercontent.com/profesorfaco/clase-10/refs/heads/main/datos.json");
}
```
Como les adelanté: 

1. No estábamos usando las alterantivas más seguras. 

2. No las estábamos usando para evitar mayores complejidades y complicaciones.

**Pero al momento de comenzar a desarrollar, de manera autónoma, su primer sitio web profesional o prototipo avanzado de aplicación web, es necesario conocerlas y usarlas. Con esto pueden evitar problemas a mediano o largo plazo en lo que puedan desarrollar**. 

- - - - - - - 

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/opr/tree/main/clase-11) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-14)
