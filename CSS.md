# CSS

## ¿Qué es CSS? 🤔


CSS, que significa "Cascading Style Sheets" en inglés, es un lenguaje de hojas de estilo utilizado en el desarrollo web. Se utiliza para definir y controlar la presentación y el formato de documentos HTML (Hypertext Markup Language), lo que incluye aspectos como el diseño, el color, la tipografía y el espaciado de los elementos en una página web.

CSS permite separar el contenido de una página web de su presentación visual, lo que hace que el código HTML sea más limpio y estructurado. En lugar de incluir estilos directamente en las etiquetas HTML, como se hacía en los primeros días de la web, CSS permite definir estilos en un archivo separado, lo que facilita la gestión y la consistencia del diseño en todo un sitio web.

Los estilos CSS se aplican a elementos HTML mediante selectores, y se pueden utilizar propiedades y valores para controlar cómo se muestran estos elementos en un navegador web. CSS es una herramienta esencial para los diseñadores web y desarrolladores, ya que les permite crear páginas web atractivas y con un diseño coherente en diferentes dispositivos y tamaños de pantalla.

> "CSS es el lenguaje que da vida a la estética y el diseño de las páginas web."

## Requerimientos para empezar con CSS

- Navegador
- Editor de código (VS Code)
- Visualizador de nuestra página (Live Server)

# Fundamentos de CSS

## Sintaxis
```css
h1 {
    color: red;
    font-size: 20px;
}
```
Las reglas de sintaxsis de CSS consisten de un *selector* y un *bloque de declaracion*
- ***h1*** Es el selector que apunta hacia el elemento html.
- ***color y font-size*** Son las propiedades del elemento dentro del bloque de declaración y constan de un nombre de propiedad ("color") y su valor ("rojo"). Si hay más de una propiedad dentro de un bloque de declaración, deben separarse con un punto y coma (;).

<img align="center" width="100%" height="100%" src="https://www.w3schools.com/css/img_selector.gif">



---

## Selectores CSS

Un selector CSS como su nombre lo indica selecciona el o los elementos HTML que quieras estilar.

Podemos dividir los selectores css en en 5 cantegorias:
- Selectores simples (seleccionan elementos basados en el nombre del elemento, id o clase)
- Selectores combinados (seleccionan elementos basados en una relacion esepecificada entre ellos)
- Selectores de pseudo-clase (seleccionan elementos basados en cierto estado)
- Selectores de pseudo-elemento (seleccionan una parte de un elemento)
- Selectores de atributo (Selecionan elementos basados en un atributo o valor de un atributo)

### Selector de elemento
En este ejemplo cambiaremos el color de todos los elementos `<p>` para que su texto sea color rojo y este centrado.

```css
p {
    color: red;
    text-align: center;
}
```

### Selector id
El selector id usa el atributo id de un elemento para seleccionar el elemento especifico. El id de un elemento deberia ser *unico* en una pagina web, por lo tanto el selector de id es usado para seleccion un solo elemento. Para seleccionar un elemento especifico utilizando el selector id deberemos escribir el simbolo (*#*) seguido por el (*id*) del elemento.
```css
#titulo1 {
    color: blue;
}
```

### Selector de clase
El selector de clase selecciona elementos HTML con un atributo de clase especifico. Para seleccionar elementos con una clase especifica escribimos un punto (.), seguido del nombre de la clase.
 ```css
 .center {
    text-align: center;
 }
 ```

 ### Selector Universal
 Este selector afectara a todos los elementos HTML de nuestra pagina.
 ```css
 *{
    color: green;
 }
 ```
 
### Resumen
 ![Alt text](image.png)

---

## Añadir CSS a HTML
Cuando un navegador lee una hoja de estilos, le dara formato al documento HTML de acuerdo a la informacion que tiene la hoja de estilos.

Existen 3 formas de insertar CSS:
- CSS Externo
- CSS Interno
- CSS En linea

### CSS Externo
Con una hoja de estilos css externa, puedes modificar el estilo de un pagina web completa solo modificando un archivo

Las hojas de estilo externas se definen con la etiqueta `<link>` dentro de la seccion `<head>` del archivo HTML.

```html
<!DOCTYPE html>
<html>
<head>
<link rel="stylesheet" href="mystyle.css">
</head>
<body>

<h1>Esto es un titulo</h1>
<p>Esto es un parrafo</p>

</body>
</html>
```
Una hoja de estilo externa debe ser un archivo con la extension ***.css***, por ejemplo ***mystyle.css***

Para el ejemplo anterior el archivo ***mystyle.css*** se veria de esta forma:
```css
body {
    background-color: cyan;
}

h1 {
    color: yellow;
}
```

---
### CSS Interno
Una hoja de estilos interna debe ser usada si una sola pagina HTML tiene un unico estilo. Los estilos internos se definen con la etiqueta `<style>` dentro de la seccion `<head>` en el archivo HTML.

```html
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background-color: linen;
}

h1 {
  color: maroon;
  margin-left: 40px;
}
</style>
</head>
<body>

<h1>Esto es un titulo</h1>
<p>Esto es un parrafo</p>

</body>
</html>
```
---

### CSS En linea (inline css).
Los estilos en linea se definen dentro del atributo style del elemento al que queremos darle estilos.

```html
<!DOCTYPE html>
<html>
<body>

<h1 style="color:blue;text-align:center;">Esto es un titulo</h1>
<p style="color:red;">Esto es un parrafo</p>

</body>
</html>
```
---

### Multiples Hojas de Estilo.
Si algunas propiedades han sido definidas por el mismo selector en diferentes hojas de estilo, se asignara el valor de la ultima hoja de estilos leida.

Supongamos que una *hoja de estilos externa* tiene los siguientes estilos:
```css
h1 {
    color: green;
}
```
Y tambien tenemos una *hoja de estilos interna* con los siguientes estilos:
```css
h1 {
    color: blue;
}
```

Si la *hoja de estilos interna* es definida despues de haber vinculado la *hoja de estilos externa*, el elemento `<h1>` sera de color azul.

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
<style>
h1 {
  color: orange;
}
</style>
</head>
```


Ahora, si la *hoja de estilos interna* es definida antes que la *hoja de estilos externa*, el elemento `<h1>` sera naranja.



Que estilo se utlizara cuando hay mas de un estilo espedificado para un elemento HTML?

Para esto existen 2 formas de determinar que estilo tendra un elemento HTML cuando hay mas 1 selector apuntando a el.

## Especificidad
La especificidad en CSS es un grupo de reglas aplicadas a los selectores CSS para determinar qué estilo se aplica a un elemento. Cuanto más específico sea un selector, mayor será su valor en ***puntos*** y más probable será que esté presente en el estilo del elemento.

El navegador evalúa la especificidad en dos partes:

1. Los estilos aplicados en linea (inline styles).
2. Los estilos aplicados mediante un selector (especificidad del selector).

### Jerarquía de la especificidad
Podemos pensar en la especificidad como un puntaje o score que determina cuales declaraciones de estilo se aplican finalmente a un elemento.

Cada tipo de de selector recibe puntos que indican su especificidad, y se suman los puntos de todos los selectores utilizados para calcular la especificidad total del selector.

Cada selector tiene su lugar en la jerarquía de especificidad. Hay cuatro categorias que definen el nivel de especificidad de un selector.















<!-- ### Cascada


Todos los estilos de una pagina caeran en forma de una "cascada" dentro de una nueva hoja de estilos "virual" siguiendo las siguientes reglas, donde el numero 1 tiene la prioridad mas alta:

1. Estilos en linea (dentro de un elemento HTML)
2. Hojas de estilo internas y externas (en la seccion `<head>`)
3. Estilos por defecto del navegador

De forma que los estilos en linea tienen la prioridad mas alta y sobreescribiran las hojas de etilo internas, externas y del navegador.

> *EL ULTIMO ESTILO DECLARADO SERA EL QUE SE TOME* -->

