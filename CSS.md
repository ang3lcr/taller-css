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


<img align="center" width="100%" height="100%" src="https://res.cloudinary.com/practicaldev/image/fetch/s--gR1j5EJy--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9wc5w6w10yriwydymc55.png">

---

# Propiedades
## Colors
Los colores se pueden especificar usando en nombres de colores predefinidos o valores RGB, HEX, HSL, RGBA o HSLA

### Nombre del color

```css
.box{
    color: red;
}
```

### Background Color
Puedes poner color a un fondo de un elemento HTML con el siguiente bloque de codigo:

```css
.body{
    background-color: purple;
}
```

### Colores RGB
Un color rgb representa las fuentes de luz (RED, GREEN y BLUE).

En CSS un color puede representarse como un valor RGB usando esta formula:


<center>
<code>rgb(red, green, blue)</code>
</center>

Cada parametro (red, green, blue) define la intensidad del color entre 0 y 255.

Por ejemplo, <code>rgb(255, 0, 0)</code> mostrara el color rojo, porque el rojo tiene el valor mas alto y los demas tienen 0. Para mostrar el color negro deberemos poner todos los colores en 0, <code>rgb(0, 0, 0)</code>


```css
p {
    background-color: rgb(255, 87, 51);
}
```

---

## Bordes
La propiedad <code>border</code> permite especificar el estilo, anchura, y color del borde del elemento.

<img align="center" width="100%" height="100%" src="https://img.uxcel.com/practices/the-border-style-property-1621321248336/a-1664877190163.jpg">

## Margenes
Los margenes son usados para crear espacio alrededor de los elementos. Con CSS tienes completo control sobre los margenes. Hay propiedades para colocar el margen por cada lado del elemento (top, bottom, right, left).

### Lados individuales
CSS tiene propiedades para especificar el margen por cada lado de un elemento:
- <code>margin-top</code>
- <code>margin-right</code>
- <code>margin-left</code>
- <code>margin-bottom</code>

Todas estas propiedades pueden estas seguidas de los siguientes valores:

- auto - El navegador calcula el margen.
- length - Especifica un margen en px, pt, cm, etc.
- % - Especifica un margen en porcentaje de la anchura del elemento contenedor.

Ejemplo:
```css
p {
  margin-top: 100px;
  margin-bottom: 100px;
  margin-right: 150px;
  margin-left: 80px;
}
```

El bloque anterior de codigo puede reducirse a este bloque de codigo

```css
p {
    margin: 100px 100px 150px 80px;
}
```

## Padding
Padding es usado para crear espacio alrededor del contenido del elemento, dentro de bordes definidos.
CSS tiene propiedades para especificar el padding por cada lado de un elemento:

- <code>padding-top</code>
- <code>padding-right</code>
- <code>padding-left</code>
- <code>padding-bottom</code>

Todas estas propiedades pueden estas seguidas de los siguientes valores:

- length - Especifica un padding en px, pt, cm, etc.
- % - Especifica un padding en porcentaje de la anchura del elemento contenedor.

Ejemplo:
```css
div {
  padding-top: 30px;
  padding-bottom: 30px;
  padding-right: 20px;
  padding-left: 50px;
}
```

El bloque anterior de codigo puede reducirse a este bloque de codigo

```css
div {
    padding: 30px 30px 20px 50px;
}
```

<img align="center" width="100%" height="100%" src="https://lh4.googleusercontent.com/R3-2VMPvVXQPC0hWujqUXeRc9L_eehOe0kzKwniE0W02f2O0ZJyYhXSWAEmF4gvBwkpRIQRmwB4z8NkG-xW5U6tdF2YDV1wzzaogrrVQA3op9SD13myk_4yRAnTu55LtQ0IaMxN7blHDU9oGTGMzt6J8a3d0sex8SjJEdIhKjHG9ECHcc7HBTOYPvhk2">

---



## Height, Width y Max-width
Las propiedades <code>height</code> y <code>width</code> son usadas para asignar la altura y anchura de un elemento HTML.

Las propiedades de altura y anchura no incluyen padding, bordes o margenes. Coloca la altura y anchura dentro del padding, borde y margen del elemento.

Las propiedades <code>width</code> y <code>height</code> estan seguidas por los siguientes valores:
- auto: El navegador calcula la altura y anchura.
- length: Define los valores en px, cm, etc
- %: Define el valor en un porcentaje del contenedor
- initial: Valor por defecto

Ejemplo
```css
div {
  height: 200px;
  width: 50%;
  background-color: blue;
}
```