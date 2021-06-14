En esta ocación veremos dos temas:
1. Renderizado de elementos en el DOM
    1. ¿Qué es un elemento de React.js?
    2. ¿Qué es un nodo raíz del DOM?
2. Actualización del elemento renderizado

# 1. Renderizado de elementos en el DOM

Para renderizar un **elemento de React** en un **nodo raíz del DOM**, pasa ambos a **ReactDOM.render()**, para entender lo anetior primero entedamos **¿Qué es un elemento de React.js?** y **¿Qué es un nodo raíz del DOM?**

## 1.1. ¿Qué es un elemento de React.js?

Es importante tener claro que los **elementos** son los bloques más pequeños de las aplicaciones de React.
Los **elementos** son los que constituyen los **componentes** y los **componentes** constituyen las **interfaces de usuario**.
En las notas ateriores vimos que un **Elemento de react** describe lo que quieres ver en la pantalla y lo generamos usando JSX, por ejemplo:

```js 
const element = <h1>Hello, world</h1>;
```
## 1.2. ¿Qué es un nodo raíz del DOM?

Para responder esta pregunta recordemos que [DOM](https://medium.com/jspoint/understanding-basics-of-dom-265b73d958d1) es la abreviatura de *Document Object Model*. Es una representación estructurada en forma de árbol de elementos HTML. 

Entonces un nodo raíz del DOM es una etiqueta contenendota (Qué abra y cierre) que este al interior de la etiqueta <body></body> del archivos HTML. Ese nodo lo llamaremos Nodo Raíz del DOM porque su id ="root" y porque todo lo que esté dentro de él será manejado por **React DOM**.
Veamolo en un archivo báscio de HTML:

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

También es importante tener claro que **ReactDOM.render()** recibe dos parametros, el primero es el **qué** y el segundo es el **dónde**. Por ejemplo:

```js
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

# 2. Actualización del elemento renderizado





Para concluir repasemos los conceptosvistos en esta ocación:
1. [X] Renderizado de elementos en el DOM
    1. [X] ¿Qué es un elemento de React.js?
    2. [X] ¿Qué es un nodo raíz del DOM?
2. [X] Actualización del elemento renderizado
