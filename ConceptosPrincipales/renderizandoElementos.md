Es importante tener claro que los **elementos** son los bloques más pequeños de las aplicaciones de React. Los **elementos** son los que constituyen los **componentes** y los **componentes** constituyen las **interfaces de usuario**.


# Renderizado elementos en el DOM

Para renderizar un **elemento de React** en un **nodo raíz del DOM**, pasa ambos a **ReactDOM.render()**:

Ya sabemos que un **Elemento de react** describe lo que quieres ver en la pantalla y lo generamos usando JSX, por ejemplo:

```js 
const element = <h1>Hello, world</h1>;
```

Pero **¿Qué es, dónde está y cómo creamos un Nodo Raíz del DOM?**. Para responder estas preguntas recordemos que [DOM](https://medium.com/jspoint/understanding-basics-of-dom-265b73d958d1) es la abreviatura de *Document Object Model*. Es una representación estructurada en forma de árbol de elementos HTML. 

Entonces un nodo raíz del DOM es una etiqueta contenendota (Qué abra y cierre) que este al interior de la etiqueta <body></body> del archivos HTML. Ese nodo lo llamaremos Nodo Raíz del DOM porque su id ="root" y porque todo lo que esté dentro de él será manejado por **React DOM**.

```js
<html> 
    <head> 
        <meta charset = "UTF-8"> 
        <title> DOM </title>
    </head> 
    <body> 
        <div id="root"></div> // Este es el Nodo Raíz del DOM
    </body> 
</html>
```

**ReactDOM.render()** recibe dos parametros, el primero es el **qué** y el segundo es el **dónde**. Por ejemplo:

```js
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

# Actualización del elemento renderizado

