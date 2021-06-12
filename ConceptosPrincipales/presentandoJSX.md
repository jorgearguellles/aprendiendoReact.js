
# Presentando JSX

Estos son los apuntes en mi proceso de aprender React.js

## ¿Qué es JSX?

Es una extensión de la sintaxis de JavaScript que visualmente se ve como la mezcla de una String y una etiqueta HTML, sin ser ninguna de las dos. En React es recomendable usar JSX para indicar cómo debería ser la interfaz del usuario porque JSX produce **Elementos**

## ¿Porqué usar JSX?

React acepta el hecho de que la lógica de renderizado está intrínsecamente unida a la lógica de la interfaz de usuario: 

- Cómo se manejan los eventos
- Cómo cambia el estado con el tiempo
- Cómo se preparan los datos para su visualización

React trabaja de manera acoplada la lógica y el maquetado en unidades llamadas **Componentes**. React no requiere usar JSX, pero la mayoría de la gente lo encuentra útil como ayuda visual cuando trabajan con interfaz de usuario dentro del código Javascript. Esto también permite que React muestre mensajes de error o advertencia más útiles.

## ¿Cuáles son las principales características de JSX?

### 1. En JSX puedes insertar expresiones de JavaScript

Puedes poner cualquier expresión de JavaScript dentro de llaves en JSX  **{ Expresiones de JS }**.
```js
Ejemplo ...
```

### 2. JSX también es una expresión de JavaScript

Después de compilarse, las expresiones JSX se convierten en llamadas a funciones JavaScript regulares y se evalúan en objetos JavaScript, es decir que también puedes usar JSX dentro de declaraciones if y bucles for, asignarlo a variables, aceptarlo como argumento, y retornarlo desde dentro de funciones: 
```js
...ejemplo...
```

### 3. En JSX puedes especificar atributos

Puedes utilizar comillas para especificar strings literales como atributos:
```js
const element = <div tabIndex="0"></div>;
```
También puedes usar llaves para insertar una expresión JavaScript en un atributo:
```js
const element = <img src={user.avatarUrl}></img>;
```

No pongas comillas rodeando llaves cuando insertes una expresión JavaScript en un atributo. Debes utilizar comillas (para los valores de los strings) o llaves (para las expresiones), pero no ambas en el mismo atributo.

### 4. En JSX puedes especificar hijos
Si una etiqueta está vacía, puedes cerrarla inmediatamente con />, como en XML:
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

### 5. JSX representa Objetos

Babel compila JSX a llamadas de React.createElement().
Estos dos ejemplos son idénticos:

```js
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
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


  