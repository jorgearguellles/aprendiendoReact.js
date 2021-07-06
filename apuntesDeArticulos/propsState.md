[ReactJS Fundamental — Props & State Simplified](https://medium.com/@infinitypaul/reactjs-fundamental-props-state-simplified-bb2cd73803d5)

# 1. Las Props

- Las *Props* le permiten pasar datos de un **componente principal (envoltorio o padre)** a un **componente secundario (incrustado o hijo)**. De la misma manerqa que cuando le pasamos argumentos a una función.
- Las *Props* son como un argumento para una función.
- Las *Props* son utiles al momento de mostrar una parte de informació sin usar código complejo

### Por ejemplo:

```js
//AllMenu Component - Parent
const AllMenu = () => {
    return (
        <div>
            <Menu item="Salad" />
        </div>
    );
}

//Menu Component - Child
const Menu = (props) => {
    return (
        <div>
            <h2>{props.item}</h2>
        </div>
    );
}

```

# 2. El Estado

Mientras que ***las Props*** permiten pasar datos por el árbol de componentes (y, por lo tanto, activar una actualización de la interfaz de usuario), **el estado** se usa para cambiar el componente desde dentro.

Los cambios de estado también desencadenan una actualización de la interfaz de usuario.

```js
class NewMenu extends Component { 
    state = { //A
        artículo: 1 
    };  
 
    render() { //B
        return ( 
            <div> {this.state.item} </div> 
        ); 
    } 
}


// A -> ¡solo se puede acceder al estado de esta forma en componentes basados ​​en clases! 
// B -> ¡Debe implementarse en componentes basados ​​en clases! ¡Necesita devolver algo de JSX! 
```

- ***El Estado***  es una propiedad de la clase del componente, debe llamarlo **state** (el nombre no es opcional). Luego puede acceder a él a través del `this.state código JSX` de su clase (que devuelve en el render() método requerido ).
- Siempre que **el estado** cambie, el componente volverá a representar(*render()*) esa sección de su aplicación y reflejará el nuevo estado.
- **El estado** es útil cuando necesita volver a renderizar o actualizar su aplicación en función de algunos cambios o algo que el usuario haya hecho, por lo que si desea cambiar algo en su aplicación, debe almacenarlos en el estado para que puedan volver a aparecer correctamente. render cuando hay cambios.
    - Si tiene varios elementos de formulario como el campo de entrada, la casilla de verificación y los me gusta que el usuario debe actualizar, State hace un buen trabajo al capturar qué valor está ingresando y qué valor se ha actualizado.
> La gran diferencia entre Props y State es que puede pasar Props a un componente, se maneja fuera de un componente y debe actualizarse fuera del componente, pero el Estado se maneja dentro del componente.

# Conclusiones

Uno de los principales desafíos que se enfrentan al elegir cuándo usar **State o Props** se debe al hecho de que no se piensa adecuadamente en qué datos va a ser manejado por el componente. 
- **Cuando usar el Estado:**
    - Si está manejando los datos dentro del componente solamente y en ningún lugar fuera de él.
- **Cuando usar las *Props*:**
    - Si está manejando los datos fuera del componente, entonces debe pasarlos a través de una *Prop* 
    - Si su información es estática y nunca va a cambiar, entonces necesita un *Props*, como dijimos anteriormente, los props son para cosas que se transmitirán desde el padre y no cambian dentro del componente.



