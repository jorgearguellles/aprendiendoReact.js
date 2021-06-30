
# 1. Props & Local State
Es importante entender que los componentes pueden renderizar datos que no cambian con el tiempo y datos que si cambian con el tiempo.
- Los datos qué no cambian con el tiempo se les puede pasar al componente de varias maneras:
    - Escribiendo los datos directamente en el componente
    - Pasando los datos por medio de las ***props*** que vienen desde el **componente padre**. 
- Los datos que si cambian con el tiempo se les pasa por medio del estado o ***State***. El estado es privado y es totalmente controlado por el componente donde esta ubicado.
    - El estado comienza con un valor predeterminado cuando un componente se monta y muta a traves del tiempo, dichas mutaciones son generadas a partir de eventos realizados por el usuario. 
    - Cuando el estado de un componente se actualiza, normalmente el componente hace rerender de si mismo.

# 2. Estado local en Componente de Clase (ES6)

Antes del **ES6** el estado local solo se manejaba en componentes de estado. Entonces transformemos un componente de función a un componente de clase, con los siguientes 5 pasos.

1. Crear una clase ES6 con el mismo nombre que herede de **React.Component**.
2. Agregar un único método vacío llamado **render()**.
3. Mover el cuerpo de la función al método **render()**.
4. Reemplazar ***props*** con ***this.props*** en el cuerpo de **render()**.
5. Borrar el resto de la declaración de la función ya vacía.

### Componente de función -> Componente de Clase

```js
function Clock(props) {
  return (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {props.date.toLocaleTimeString()}.</h2>
    </div>
  );
}

ReactDOM.render(
    <Clock date={new Date()} />,
    document.getElementById('root')
  );
```

```js
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
    <Clock date={new Date()} />,
    document.getElementById('root')
  );

```
**Clock** ahora se define como una clase en lugar de una función.

El método render se invocará cada vez que ocurre una actualización; pero, siempre y cuando rendericemos `<Clock />` en el mismo nodo del DOM, se usará solo una única instancia de la clase Clock. 

Esto nos permite utilizar características adicionales como el estado local y los métodos de ciclo de vida. Agregamos el estado local a un componentes de clase con tres pasos:

1. Reemplazar ***this.props.date*** con ***this.state.date*** en el método **render()**:

```js
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        /* <h2>It is {this.props.date.toLocaleTimeString()}.</h2> */
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
    <Clock date={new Date()} />,
    document.getElementById('root')
  );
```
2. Añadir un **constructor de clase** que asigne el ***this.state inicial***:

```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
    <Clock date={new Date()} />,
    document.getElementById('root')
  );
```
Las ***props*** que eliminamos en el paso uno las ubicamos en el **contructor de clase**. 
> Los componentes de clase siempre deben invocar al constructor base con props.

3. Eliminar la ***prop date*** del elemento `<Clock />`:

```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
```

# 3. ¿Cuáles son las diferentes fases del ciclo de vida de los componentes?

El ciclo de vida del componente tiene tres fases distintas del ciclo de vida:

1. **Mounting - Montaje:** el componente está listo para ser montado en el DOM del navegador. Esta fase cubre la inicialización de los métodos de ciclo de vida:
    - `constructor()`
    - `getDerivedStateFromProps()`
    - `render()`
    - `componentDidMount()`

2. **Updating - Actualización:** en esta fase, el componente se actualiza de dos maneras, enviando las nuevos *props* y actualizando el estado desde el método `setState()` o `forceUpdate()`. Esta fase cubre los métodos del ciclo de vida:
    - `getDerivedStateFromProps()`
    - `shouldComponentUpdate()`
    - `render()`
    - `getSnapshotBeforeUpdate()`
    - `componentDidUpdate()`

3. **Unmounting - Desmontaje:** En esta última fase, el componente no es necesario y se desmonta del DOM del navegador. Esta fase incluye el método de ciclo de vida: 
    - `componentWillUnmount()``


Vale la pena mencionar que React internamente tiene un concepto de fases al aplicar cambios al DOM. Están separados de la siguiente manera:
  - **Render - Renderizar:** El componente se renderizará sin efectos secundarios. Esto se aplica a los **componentes puros** y en esta fase, React puede pausar, cancelar o reiniciar el renderizado. 
  - **Pre-commit - Compromiso previo:** Antes de que el componente aplique los cambios al DOM, hay un momento que permite a React leer del DOM a través de `getSnapshotBeforeUpdate()`
  - **Commit - Compromiso:** React funciona con DOM y ejecuta los ciclos de vida finales respectivamente, `componentDidMount()` para el montaje, `componentDidUpdate()` para actualizar y `componentWillUnmount()` para desmontar.


# 4. 