#### ¿Qué es el direccionamiento directo?
Es cuando se expresa una dirección de memoria específica o se utilizar el símbolo de una dirección específica, para podeer leer o guardar datos.
#### ¿Cómo se usa en el lenguaje ensamblador Hack?
Se usa con una instrucción que sea @dirección (A-instruction) seguida de una C-instruction para acceder a la RAM, en la dirección almacenada en A.
#### ¿Qué significa M=D en lenguaje ensamblador Hack? ¿Y D=M?
M=D → Guarda el valor del registro D en la dirección de RAM apuntada por A.
D=M → Carga en el registro D el valor almacenado en la dirección de RAM apuntada por A.
#### Concepto "puntero"
Puntero hace referencia basicamente al registro A, porque este sirve como un puntero dentro de la RAM. En este caso A en vez e guardar un dato, guarda una posición en la memoria, actuando como un puntero.
#### Ejemplo
```
@100   // Guardo 100 en A (dirección de memoria)
D=A    // D tiene el valor 100
@200   // **Apunto con el puntero (A)** a la dirección 200, para acceder a la RAM en la posición 200
M=D    // Guardo el valor de D (100) en la dirección 200
```
