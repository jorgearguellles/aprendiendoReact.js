# 1. ¿Qué es un Componente?

Un componente **es una función de JavaScript** que recibe atributos (En React.js se les llamamos *Props*) y devuelve un **elemento de react.js** que describe lo que debe aparecer en la pantalla.

> Recordemos: Los **elementos** son los bloques más pequeños de las aplicaciones de React.js Los **elementos** son los que constituyen los **componentes** y los **componentes** constituyen las **interfaces de usuario**.

## 1.1. ¿Caracteristicas de un Componente?
- Permiten separar la interfaz de usuario en **piezas independientes**
- Permiten separar la interfaz de usuario en **piezas reutilizables**
- Permiten pensar en **cada pieza de forma aislada**.

# 2. Tipos de Componentes

## 2.1. Componentes funcionales

La forma más sencilla de definir un componente es escribir **una función de JavaScript** y por eso mismo se les llama **Componentes funcionales**.

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

## 2.2. Componentes de clase
El ejemlo anterior también se puede expresar por medio de una [clase de ES6](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Classes) para definir un componente:

```js
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

# Renderizando un componente

