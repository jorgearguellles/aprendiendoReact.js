[ReactJS Fundamental — Props & State Simplified](https://medium.com/@infinitypaul/reactjs-fundamental-props-state-simplified-bb2cd73803d5)

# 1. Las Props

- Las *Props* le permiten pasar datos de un **componente principal (envoltorio o padre)** a un **componente secundario (incrustado o hijo)**. 
- Las *Props* son como un argumento para una función.
- Las *Props* son utiles al momento de mostrar una parte de informació sin usar código complejo

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

***El Estado***  es una propiedad de la clase del componente, debe llamarlo **state** (el nombre no es opcional).
Luego puede acceder a él a través del `this.state código JSX` de su clase (que devuelve en el render()método requerido ).
