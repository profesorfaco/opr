### Introducción al desarrollo web desde el diseño → Clase 04 → 29/08/2025

# Comprendiendo dos lenguajes y una biblioteca: HTML5, CSS3 y p5.js

Podríamos aprovechar lo trabajado por [Catalina Bustos](https://github.com/catita-b/web_clase02), que en su `index.html` describió que lo siguiente era lo que correspondía mostrar: 

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <!-- <script src="https://cdn.jsdelivr.net/npm/p5@1.11.8/lib/p5.js"></script> -->
    <link rel="stylesheet" type="text/css" href="style.css">
    <meta charset="utf-8" />
  </head>
  <body>
    <main id="bloque"> <!-- la identidad solo puede haber solo uno, para poder identificar eleemntos de una página-->
      <h1> Hola mundito! (˶ᵔᵕᵔ˶)</h1>
      <h2> Este es mi ejercicio 02</h2>
      <p> Clickea mi <a href="https://catita-b.github.io/web_clase01/" target="_blank">primer trabajito</a> para ver lo que hice en la primera clase de Intro a Web</p>
      <p> Les gustó mis ejercicio? <span class="pixel">  digan que si pipipi [;-;]</span> </p> <!-- la clase si se puede repetir entre otro elementos-->

    </main>
    <!-- <script src="sketch.js"></script> -->
  </body>
  <footer></footer>
</html>
```

Y lo recién descrito, debido a un vínculo con un `style.css` en relación de *stylesheet*, debía verse de la siguiente manera:

```
@import url('https://fonts.googleapis.com/css2?family=Pixelify+Sans:wght@400..700&display=swap');


html, body {
  margin: 0;
  padding: 0;
  background: #E4A1DF;
  color: #4C0529; 
  font-family: Helvetica, Arial, sans-serif;

}

a{ 
  color: white;
  font-weight: bold;
  text-decoration: none;
}

a:hover{
  color: blueviolet;
  text-decoration: underline;
  transition: all ease 2s;
}

a:hover:after{ 
  content:" -‧°𐐪♡𐑂°‧-";
}

#bloque{
  margin: 5rem;
  padding: 8rem;
  background: rgba(255, 255, 255, .2);
  border-radius: 1rem;
  box-shadow: 0 0 30px white;
}

h1,h2, span.pixel{
  font-family: "Pixelify Sans", sans-serif;
  font-style: normal;
}

span.pixel{
  color: #f00;
  font-size: 80%;
}

h1{ 
  font-size: calc(2rem + 5vw); 
}

h2{
  font-size: calc(1rem + 2vw);
}

```

Corresponde indicar que en el CSS recién desplegado se quitaron algunos `/*comentarios*/` dejados por Catalina.

Con lo recién visto tenemos un avance consistente en lo que respeta a descripción.

¡Aún no hemos programado!

La programación se hace con lenguajes de programación, tales como JavaScript. 

A tal lenguaje de programación nos acercaremos por la vía de **p5.js**, aprovechando sus [referencias](https://p5js.org/reference/), [tutoriales](https://p5js.org/tutorials/) y [ejemplos](https://p5js.org/examples/). 

- - - - - - - 

###### [← CLASE ANTERIOR](https://github.com/profesorfaco/opr/tree/main/clase-03) — [SIGUIENTE CLASE →](https://github.com/profesorfaco/opr/tree/main/clase-05)

