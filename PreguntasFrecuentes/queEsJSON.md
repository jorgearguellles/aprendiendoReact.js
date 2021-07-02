[¿Qué es JSON?](https://medium.com/@julianam.tyler/what-is-json-91df906ed27b)

# 1. ¿Qué significa JSON?

JSON significa JavaScript Object Notation

# 2. ¿Qué es un JSON?

JSON es un formato basado en texto que representa datos estructurados en la sintaxis de objetos JavaScript.

# 3. ¿En qué casos se usa JSON?

Se utiliza en casos como cuando un servidor necesita enviar algunos datos al cliente y se puede mostrar en la página web y viceversa. 

# 4. ¿Cuales son las reglas que aplican al trabajar con JSON?

1. Los datos están en pares de `"nombre" -> ""valor"`: `"Ciudad": "Cali"`
2. Los datos estan separados por comas: `"Ciudad": "Cali", "Pais":"Colombia"`
3. Los datos estan al interior de llaves tipo Objeto de JavaScript: `{"Ciudad": "Cali", "Pais":"Colombia"}`
4. Los Objetos están contenido en un Array de Objetos: 
```js
  "Ciudades": [
          {"Ciudad": "Cali"},
          {"Ciudad":"Bógota"},
          {"Ciudad":"Bóyaca"},
          {"Ciudad":"Popayan"}
  ];
```

# 5. ¿Cómo enviar y recibir datos?

Para intercambiar datos entre el navegador y el servidor, solo se puede usar texto para enviar y recibir datos. 

Por eso se utiliza la función **JSON.parse()** incorporada en JavaScript para convertir de **objeto JSON** a **cadena de caracteres**.

Podemos convertir cualquier objeto JavaScript en un JSON, y luego enviarlo al servidor y hacer lo mismo para pasar de JSON a JavaScript.