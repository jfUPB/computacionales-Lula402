### El ciclo de Fetch-Decode-Execute paso a paso
#### ¿Qué valor tiene el PC al inicio del ciclo?
PC= 0
#### ¿Qué instrucción se busca en la memoria?
No se busca ninguna instrucción en la memoria, en este caso solo se almacena en la posición 6 de la RAM el valor de D=69
#### ¿Cómo se decodifica la instrucción?
El PC lee la instrucción de esa posición, luego la unidad de control la decodifica.

| Instrucción  | Fetch | Decode | Execute |
| ------------- | ------------- | ------------- | ------------- |
| @60 | El Pc indica traer la instrucción 0 | @Value=A=60 | El registro de A se hace =60, PC=1 |
| D=A  | El Pc indica traer la instrucción 1 | D=A | El registro de D se hace = al valor del registro A, PC=2|
| @9  | El Pc indica traer la instrucción 2 | @Value=A=9 | El registro de A se cambia a =9, PC=3|
| D=D+A  | El Pc indica traer la instrucción 3 | D=D+A | El registro de D se hace = al valor del registro actual de D + el valor del registro A, PC=4|
| @6 | El Pc indica traer la instrucción 4 |  @Value=A=6 | El registro de A se cambia a =6, PC=5|
| M=D | El Pc indica traer la instrucción 5 |  M=D | En la posición 6 de la RAM se guarda el valor del registro D, PC=6 |
| @0 | El Pc indica traer la instrucción 6 | @Value=A=0 | El registro de A se cambia a =0, PC=7 |
| 0;JMP | El Pc indica traer la instrucción 7 | 0;JMP | Se hace un salto incondicional a la posición que tenga A que es =0, PC=0 |






