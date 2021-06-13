Es importante tener claro que los **elementos** son los bloques más pequeños de las aplicaciones de React. Los **elementos** son los que constituyen los **componentes** y los **componentes** constituyen las **interfaces de usuario**.

# Renderizado elementos en el DOM

Para renderizar un elemento de React en un nodo raíz del DOM, pasa ambos a **ReactDOM.render()**:

Ya sabemos que un **Elemento de react**  lo generamos usando JSX, pero **¿Qué es, dónde está y cómo creamos un Nodo Raíz del DOM?**. 

Para responder estas preguntas recordemos que el DOM nace del documento HTML + documento CSS, entonces necesitamos una etiqueta (Que abra y cierre) en el archivos HTML que sea nuestro nodo donde renderizamos el elemento de React
Ese nodo lo llamaremos Nodo Raíz del DOM porque su id ="root", lo normal es usar una etiqueta div: 
```js
<div id="root"></div>
```


# Actualización del elemento renderizado