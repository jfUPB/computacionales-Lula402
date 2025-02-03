### Profundizando en las instrucciones del lenguaje ensamblador
#### A-instructions
##### ¿Cuál es su función?
Sirven para poner un valor numérico en el registro A. Puede ser un número o una dirección de memoria (RAM o ROM).
##### ¿Cómo se representa en binario?
Se representan con 16 bits, que son 16 caracteres binarios.
El primer bit siempre es 0, seguido de 15 bits para el valor.
```
*0 v v v v v v v v v v v v v v v*
```
**V:** es el valor en binario que se almacena en el registro A.

##### Ejemplos
*#1* @5 → En binario: **0**000000000000101

*#2* @100 → En binario: **0**000000001100100

*#3* @200 → En binario: **0**0000000011001000

#### C-instructions
##### ¿Cuál es su función?
Ejecutan operaciones con la ALU, guardan el resultado en registros A/D o RAM y permiten saltos condicionales en la ejecución del programa.
##### ¿Cómo se representa en binario?
El primer bit siempre es 1, seguido de códigos que indican la operación (comp), el destino (dest) y el tipo de salto (jump).
```
1 1 1 a c1 c2 c3 c4 c5 c6 d1 d2 d3 j1 j2 j3  
```
comp: Código que indica la operación a realizar. Ya existen operaciones estandares escritas en binario.
dest: Indica si almacenar el resultado en registro D, A o memoria M. Ya existen ubicaciones de memoria estándares.
jump: Especifica si la instrucción debe hacer un salto condicional. Los diferentes tipos de salto ya están especificados.

##### Ejemplos
*#1* D=M+1 → En binario: 1111110111100000
Suma 1 al valor almacenado en M|A| y lo guarda en D.

*#2* MD=D-1 → En binario: 1110001110101000
Resta 1 al valor de D y guarda el resultado en D y en M.

*#3* D;JGT → En binario: 1110001100000001
Si D > 0, saltar a la dirección almacenada en A; sino, continuar con la siguiente instrucción.



