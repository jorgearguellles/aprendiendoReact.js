# Indice de contenido

1. [¿Qué es un Componente?](#componente)
    1. [Caracteristicas de un Componente](#caracteristicasCompoennte)
2. [Tipos de Componentes](# )
3. []()
4. []()
5. []()
6. []()



<a name="componente"/>

# 1. ¿Qué es un Componente?

Un componente **es una función de JavaScript** que recibe atributos, que en React.js se les llamamos *Props* y devuelve un **elemento de react.js** que describe lo que debe aparecer en la pantalla.

> Recordemos: Los **elementos** son los bloques más pequeños de las aplicaciones de React.js Los **elementos** son los que constituyen los **componentes** y los **componentes** constituyen las **interfaces de usuario**.

<a name="caracteristicasCompoennte"/>

## 1.1. Caracteristicas de un Componente
- Permiten separar la interfaz de usuario en **piezas independientes**
- Permiten separar la interfaz de usuario en **piezas reutilizables**
- Permiten pensar en **cada pieza de forma aislada**.


<a name="tiposDeComponente"/>

# 2. Tipos de Componentes

<a name="componenteFuncional"/>

## 2.1. Componentes funcionales

La forma más sencilla de definir un componente es escribir **una función de JavaScript** y por eso mismo se les llama **Componentes funcionales**.

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
<a name="componenteClase"/>

## 2.2. Componentes de clase
El ejemlo anterior también se puede expresar por medio de una [clase de ES6](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Classes) para definir un componente:

```js
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

<a name="renderizadoComponente"/>

# 3. Renderizando un componente

Un componente puede renderizar **etiquetas del DOM** y **componentes definidos por el desarrollador**. 
> Siempre comienza los nombres de componentes definidos con una letra mayúscula. React trata los componentes que empiezan con letras minúsculas como etiquetas del DOM.

Por ejemplo:

```js
const element = <div />; //Representa una etiqueta div HTML
```

```js
const element = <Welcome name="Jorge" />; //Representa un componente y requiere que Welcome esté definido.
```

Cuando React ve un elemento representando un componente definido por el usuario, pasa atributos JSX e hijos a este componente como un solo objeto. Llamamos a este objeto “props”. Por ejemplo:


```js
function Welcome(props) { //Aquí defino el componente e indico que recibe props 
  return <h1>Hello, {props.name}</h1>; //El props se llama name y más adelante le van a indicar
}

const element = <Welcome name="Jorge" />; //Aquí llamo el componente y le indico el dato que pasra como props, lo guardo en una constante llamada elemento

ReactDOM.render(
  element,
  document.getElementById('root')
);
```
<a name="composiciónComponente"/>

# 4. Composición de componentes

Composición de componentes quiere decir que los componentes pueden referirse a otros componentes en su salida, esto nos permite tener la misma abstracción de componente para cualquier nivel de detalle.

Por ejemplo, podemos crear un **componente App** que renderiza el **componente Welcome** muchas veces:

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Jorge" />
      <Welcome name="Carolina" />
      <Welcome name="Carlos" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```
<a name="extracciónComponente"/>

# 5. Extracción de componentes

Extracción de componentes nos invita a siempre dividir los componentes en otros más pequeños. (Buena práctica)

Por ejemplo, considera este componente **Comment** que describe un comentario en una web de redes sociales y acepta las siguientes **Props**:
- author (un objeto)
- text (un string)
- date (una fecha)

```js
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img className="Avatar"
          src={props.author.avatarUrl}
          alt={props.author.name}
        />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```

Este componente puede ser difícil de cambiar debido a todo el anidamiento, y también es difícil reutilizar partes individuales de él. Vamos a extraer algunos componentes del mismo.

1. Primero, vamos a extraer **Avatar** que no necesita saber que está siendo renderizado dentro de un **Comment** porque le dimos a su propiedad un nombre más genérico: user en vez de author.

```js
function Avatar(props) {
  return (
    <img className="Avatar"
      src={props.user.avatarUrl}
      alt={props.user.name}
    />
  );
}
```
> Recomendamos nombrar las Props desde el punto de vista del componente, en vez de la del contexto en el que se va a utilizar.

El **componenete Comment** va quedando así:

```js
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <Avatar user={props.author} />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}



function Avatar(props) {
  return (
    <img className="Avatar"
      src={props.user.avatarUrl}
      alt={props.user.name}
    />
  );
}
```

A continuación, vamos a extraer un **componente UserInfo** que renderiza un **Avatar** al lado del nombre del usuario:

```js
function UserInfo(props) {
  return (
    <div className="UserInfo">
      <Avatar user={props.user} />
      <div className="UserInfo-name">
        {props.user.name}
      </div>
    </div>
  );
}
```

Finalmente el **componente Commet** queda así:

```js
function Comment(props) {
  return (
    <div className="Comment">
      <UserInfo user={props.author} />
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}


function UserInfo(props) {
  return (
    <div className="UserInfo">
      <Avatar user={props.user} />
      <div className="UserInfo-name">
        {props.user.name}
      </div>
    </div>
  );
}


function Avatar(props) {
  return (
    <img className="Avatar"
      src={props.user.avatarUrl}
      alt={props.user.name}
    />
  );
}
```
<a name="propsLectura"/>

# 6. Las Props son de solo lectura

> **Todos los componentes de React deben actuar como funciones puras con respecto a sus props.**

Para entender la idea de que los Props son de solo lectura, es necesario entender qué es una función pura y que es una función Inpura.

<a name="funcionPura"/>

## 6.1 ¿Qué es una función pura?

Una función pura es la que siempre devuelven el mismo resultado para las mismas entradas. Por ejemplo:

```js
function sum(a, b) {
  return a + b;
}
```
<a name="funcionInpura"/>

## 6.2 ¿Qué es una función inpura?

Una función Inpura es la que cambia su entrada y así mismo la salida. Por ejemplo:

```js
function withdraw(account, amount) {
  account.total -= amount;
}
```

Por supuesto, las interfaces de usuario de las aplicaciones son dinámicas y cambian con el tiempo. Más adelante veremos un nuevo concepto de “estado”. El estado le permite a los componentes de React cambiar su salida a lo largo del tiempo en respuesta a acciones del usuario, respuestas de red y cualquier otra cosa, sin violar esta regla.
