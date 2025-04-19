### <p align=center> EXPERIMENTO 3 </p>
#### ¿Qué ocurre? 
La variable global inicializada pasa de ser = 42 a ser = 69. La variable global no inicializada pasa de estar no inicializada (=0) a ser = 666.

#### ¿Por qué?
Porque ambas están en la parte de la memoria donde se almacenan las variables globales y estáticas. A esta parte de la memoria se puede acceder y se puede hacer escritura, por lo que si me dejó cambiar el contenido de estas dos variables sin ningún problema.

### <p align=center> EXPERIMENTO 4 </p>
#### ¿Qué ocurre? 
Me arroja un error de compilación, porque el Main no conoce la variable llamada: var_estatica, así que simplemente no la puede modificar a =42.

#### ¿Por qué?
Porque cuando pongo Static a una variable dentro de una función, esto me permite que sea global pero aún asi debo acceder a ella por medio de la función en la que está metida. Es decir, yo hice que var_estatica, fuera static, entonces se vuelve global, pero para que el main pueda modificarla, debe llamar a la función y modificar su valor.
Por que simplemente no crear un global? Porque el static me permite crear variables globales pero dentro de una función, evitando que esta sea local y no la pueda acceder o modificar por fuera de esta función.
Entonces la ventaja es que la función lleve consigo su paquetico de cosas, incluida su global y que no tenga como las tripitas regadas por todo el código.
