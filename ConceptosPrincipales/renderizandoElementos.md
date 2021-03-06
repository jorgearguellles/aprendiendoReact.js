# Indice de contenidos

1. [Renderizado de elementos en el DOM](#dom)
    1. [¿Qué es un elemento de React.js?](#elemento)
    2. [¿Qué es un nodo raíz del DOM?](#nodoraiz)
2. [Actualización del elemento renderizado](#actualizacion)

<a name="dom"/>

# 1. Renderizado de elementos en el DOM

Para renderizar un **elemento de React** en un **nodo raíz del DOM**, pasa ambos al interior de **ReactDOM.render()**, para entender lo anterior, primero entendamos **¿Qué es un elemento de React.js?** y **¿Qué es un nodo raíz del DOM?**

<a name="elemento"/>

## 1.1. ¿Qué es un elemento de React.js?

Es importante tener claro que los **elementos** son los bloques más pequeños de las aplicaciones de React.
Los **elementos** son los que constituyen los **componentes** y los **componentes** constituyen las **interfaces de usuario**.
En las notas ateriores vimos que un **Elemento de react** describe lo que quieres ver en la pantalla y lo generamos usando JSX, por ejemplo:

```js 
const element = <h1>Hello, world</h1>;
```

<a name="nodoraiz"/>

## 1.2. ¿Qué es un nodo raíz del DOM?

Para responder esta pregunta comencemos recordando que:
- El [DOM](https://medium.com/jspoint/understanding-basics-of-dom-265b73d958d1) significa *Document Object Model*.
- El [DOM](https://levelup.gitconnected.com/what-is-the-dom-6522bf1d312b) es una representación estructurada en forma de árbol **basada en objetos** del documento HTML de origen.
- El DOM es la primera etapa del [*Critial Rendering Path*](https://dev.to/codesensei/critical-rendering-path-39m).

Entonces un nodo raíz del DOM es una etiqueta contenedora (Qué abra y cierre) que este al interior de la etiqueta <body></body> del archivos HTML. Ese nodo lo llamaremos Nodo Raíz del DOM porque su id ="root" y porque todo lo que esté dentro de él será manejado por **React DOM**.
Veamoslo en un archivo básico de HTML:

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

También es importante tener claro que **ReactDOM.render(par1, par2)** recibe dos parametros, el primero es el **qué** y el segundo es el **dónde**. Por ejemplo:

```js
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

<a name="actualizacion"/>

# 2. Actualización del elemento renderizado

Los elementos de React son **inmutables** Es decir, una vez creas un elemento, no puedes cambiar sus hijos o atributos. Con nuestro conocimiento hasta este punto, la única manera de actualizar la interfaz de usuario es creando un nuevo elemento, y pasarlo a **ReactDOM.render()**.

Por ejemplo un reloj en marcha:
```js
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);
```
Este función llama a **ReactDOM.render()** cada segundo desde un callback del **setInterval()**.
React DOM compara el elemento y sus hijos con el elemento anterior, y solo aplica las actualizaciones del DOM que son necesarias para que el DOM esté en el estado deseado.

> En la práctica, la mayoría de las aplicaciones de React solo llaman a ReactDOM.render() una   vez. En las siguientes secciones aprenderemos cómo el código se puede encapsular en componentes con estado.

<details>
           <summary>Notas sobre ReactDom.render()</summary>
           <ul>
           <li>ReactDOM.render() controla el contenido del nodo contenedor que suministras. Cualquiera de los elementos DOM dentro de este son reemplazados cuando se llama por primera vez. Las llamadas posteriores utilizan el algoritmo de diferenciado de React DOM para actualizaciones eficientes.</li>
           <li>ReactDOM.render() no modifica el nodo contenedor (solo modifica los hijos del contenedor). Puede ser posible insertar un componente en un nodo existente del DOM sin sobrescribir los hijos existentes.</li>
           <li>ReactDOM.render() actualmente retorna una referencia a la instancia ReactComponent raíz. Sin embargo, utilizar este valor retornado es una práctica vieja, y debe ser evitada debido a que en futuras versiones de React puede que los componentes se rendericen de manera asíncrona en algunos casos. Si deseas obtener una referencia a la instancia ReactComponent raíz, la solución preferida es agregar una referencia mediante callback al elemento raíz.</li>
           <li>El uso de ReactDOM.render() para hidratar un contenedor renderizado por servidor esta despreciado, y será eliminado en la versión 17 de React. Usa en su lugar hydrate().</li>
           </ul>
</details>

- - - -

# Temas vistos
1. [X] Renderizado de elementos en el DOM
    1. [X] ¿Qué es un elemento de React.js?
    2. [X] ¿Qué es un nodo raíz del DOM?
2. [X] Actualización del elemento renderizado
