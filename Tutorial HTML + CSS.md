# HTML + CSS

## Introducción

HTML y CSS son dos meta-lenguajes de programación para el front end de un sitio web.

HTML nos permite definir el contenido del sitio así como su estructura. Con HTML podríamos indicar cosas como:

* Acá va un título

* Acá va una imágen

* Acá va un link a otra página

Hasta ahí, si bien es muy útil, veríamos una página bastante aburrida...blanco y negro y links en azul.

Por esto aparece CSS que nos permite definir cuestiones de estilo y diseño del sitio. A través de CSS uno puede proponer cuestiones como:

* Determinado título quiero que tenga fondo azul y letra en negrita

* Todos los párrafos quiero que tengan fondo naranja y letra roja.

* Algunas imágenes tengan borde redondeado.

Con esta misma lógica se puede realizar un diseño responsive. Es decir, indicar algunas reglas de diseño que solamente aplicaran cuando la web se vea desde una tablet o un teléfono movil.

## Uso

HTML es un lenguaje de etiquetas. Una etiqueta podría decir

`<cartel>`

Esa etiqueta indica el comienzo de un cartel en HTML.

¿Donde termina el cartel? En la etiqueta de cierre la cual se escribe `</cartel>`

De esta forma, un elemento HTML podría ser:

```html
<cartel>
	Este es mi cartel!!!
</cartel>
```

Un navegador, como Chrome podrá leer este documento y mostrar en pantalla un cartel que diga "Este es mi cartel".

El chiste de esto esta en que Chrome no conoce la etiqueta `<cartel>` y habrá que aprender cuales etiquetas son válidas y como se combinan.

Si bien recomendamos el tutorial #ManosEnLaMasa pueden ver la referencia de sus etiquetas en [https://www.w3schools.com/html/default.asp](https://www.w3schools.com/html/default.asp)

Por otra parte CSS se escribe en un archivo aparte (el cual se vincula con el documento HTML) y se escriben "reglas" de CSS con el siguiente formato

```css
selector {

	propiedad: valor;

	propiedad: valor;

}
```

En este caso, **selector** indica cuales de las etiquetas HTML se modificaran. Por ejemplo "Todas las etiquetas de tipo `<p>`". La **propiedad** indica que cuestión del estilo queremos modificar, por ejemplo **color**. El **valor** indicará que valor le damos a la propiedad. En el caso del color un valor válido podría ser **#FF2312**

Un ejemplo real con la información propuesta arriba se vería

```css
p {

	color: red;

	font-size: 32px;

	background-color: #FF2312;

}
```

Una vez más, el chiste esta en aprender estas reglas, como se combinan y como escribir selectores.

Si bien recomendamos el Tutorial #ManosEnLaMasa, para ver una referencia completa pueden ingresar en [https://www.w3schools.com/css/](https://www.w3schools.com/css/)

## Tutorial #ManosEnLaMasa

Recomendamos tutoriales como:

* [https://www.codecademy.com/learn/learn-html](https://www.codecademy.com/learn/learn-html)

* [https://www.codecademy.com/learn/learn-css](https://www.codecademy.com/learn/learn-css)

* [https://www.codecademy.com/learn/make-a-website](https://www.codecademy.com/learn/make-a-website)

* [https://www.codecademy.com/learn/learn-responsive-design](https://www.codecademy.com/learn/learn-responsive-design)

* [https://devcode.la/cursos/html-css/](https://devcode.la/cursos/html-css/)

* [http://es.html.net/tutorials/html/](http://es.html.net/tutorials/html/)
