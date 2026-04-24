### Optativo de Profundización: [Desarrollo Web y Diseño Visual de Información](https://github.com/profesorfaco/opr/?tab=readme-ov-file#readme) → Clase 08 → 24/04/2026

# Gráficas y datos en diseño web responsive: SVG y HTML

### Teoría (para la casa)


En HTML puedo tener dos versiones de la misma gráfica, una angosta y otra ancha.

```
<figure id="first">
  <object data="angosta.svg" type="image/svg+xml">
    <img src="angosta.svg">
  </object>
  <figcaption>Mobile</figcaption>
</figure>

<figure id="second">
  <object data="ancha.svg" type="image/svg+xml">
    <img src="ancha.svg">
  </object>
  <figcaption>Desktop</figcaption>
</figure>
```

Luego, mediante `CSS` muestro o escondo otra. 

```
/* Móvil: se muestra #first, se oculta #second */
#first {
  display: block;
}

#second {
  display: none;
}

/* Pantallas desde 600px: se oculta #first, se muestra #second */
@media screen and (min-width: 600px) {
  #first {
    display: none;
  }

  #second {
    display: block;
  }
}
```

- - - - - - - - - - - - - - 

### Práctica (para la clase)

Pendiente (corresponde ajustarlo según su avance).

- - - - - - - 

###### [← CLASE PREVIA](https://github.com/profesorfaco/opr/tree/main/clase-07) • [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-10)
