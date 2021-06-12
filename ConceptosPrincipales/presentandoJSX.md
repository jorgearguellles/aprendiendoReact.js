# ¿Qué es JSX?

Es una extensión de la sintaxis de JavaScript que visualmente es una mezcla entre una **String** y una **etiqueta HTML**, sin ser ninguna de las dos.
Es recomendable usar JSX para indicar cómo debería ser la interfaz del usuario porque JSX produce **Elementos**

# ¿Porqué usar JSX?

React.js acepta que **la lógica de renderizado** está intrínsecamente unida a **la lógica de la interfaz de usuario**: 

- Cómo se manejan los eventos
- Cómo cambia el estado con el tiempo
- Cómo se preparan los datos para su visualización

React.js trabaja la lógica y el maquetado de manera acoplada en unidades llamadas **Componentes**. 
Para programar en React.js no se requiere usar JSX, pero es muy útil como ayuda visual al momento de trabajar con interfaces de usuario dentro del código Javascript.
Esto también permite que React muestre mensajes de error o advertencia más útiles.

# ¿Cuáles son las principales características de JSX?

## 1. En JSX puedes insertar expresiones de JavaScript

Puedes poner cualquier expresión de JavaScript dentro de llaves en JSX  **{ Expresiones de JS }**.
Ejemplo1:
```js
const name = 'Jorge Arias Argüelles';
const element = <h1>Hello, {name}</h1>;
```
Ejemplo2:
```js
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Jorge',
  lastName: 'Arias'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);
```

## 2. JSX también es una expresión de JavaScript

Después de compilarse, las expresiones JSX se convierten en llamadas a funciones JavaScript regulares y se evalúan en objetos JavaScript, es decir que también puedes usar JSX dentro de declaraciones:
- if
- bucles for y while
- asignarlo a variables
- aceptarlo como argumento
- Retornarlo desde dentro de funciones
Por ejemplo: 

```js
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

## 3. En JSX puedes especificar atributos

- Puedes utilizar comillas para especificar strings literales como atributos:
```js
const element = <div tabIndex="0"></div>;
```
- También puedes usar llaves para insertar una expresión JavaScript en un atributo:
```js
const element = <img src={user.avatarUrl}></img>;
```

**No pongas comillas rodeando llaves cuando insertes una expresión JavaScript en un atributo.** - Debes utilizar comillas para los valores de los strings
- Y llaves para las expresiones de JavaScript

## 4. En JSX puedes especificar hijos
Si una etiqueta está vacía, puedes cerrarla inmediatamente con />, como en XML.
Ejemplo:
```js
const element = <img src={user.avatarUrl} />;
```

Las etiquetas de Javascript pueden contener hijos:

```js
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

## 5. JSX representa Objetos

Babel compila JSX a llamadas de **React.createElement()**.
Estos dos ejemplos son idénticos:

```js
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

```js
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

**React.createElement()** realiza algunas comprobaciones para ayudarte a escribir código libre de errores, pero, en esencia crea un objeto como este:

```js
// Nota: Esta estructura está simplificada
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```

Estos objetos son llamados **Elementos de React**. Puedes pensar en ellos como descripciones de lo que quieres ver en pantalla. React lee estos objetos y los usa para construir el DOM y mantenerlo actualizado.


## Documentation

[Documentación de React.js](https://es.reactjs.org)

  
## Authors

- Jorge Arias Argüelles en [@LinkedIn](https://www.linkedin.com/in/jorgeariasarguelles/) y en [@GitHub](https://github.com/jorgearguellles)

  
## Feedback

Si tienes recomendaciones para mejorar, por favor escribeme [@jorgeariasarg](https://www.linkedin.com/in/jorgeariasarguelles/)


  