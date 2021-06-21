
Es importante entender que los componentes pueden renderizar datos que no cambian con el tiempo y datos que si cambian con el tiempo.
- Los datos qué no cambian con el tiempo, el componente recibe 
 *Props* son datos establecidas directaente o por el componente padre y son fijas durante toda la vida útil de un componente.
- El estado o *State* son datos que cambian a lo largo del ciclo de vida de un componente.
    - El estado comienza con un valor predeterminado cuando un componente se monta y muta a traves del tiempo, dichas mutaciones son generadas a partir de eventos realizados por el usuario. 
    - Cuando el estado de un componente se actusliza, normalmente el componente hace rerender de si mismo.


Para empezar a entender el estado, es necesario aclarar que existen dos tipos de componentes en relación al estado:
- Componentes con estado (*stateful componenet*)
- Componentes sin estado (*stateless component*)

