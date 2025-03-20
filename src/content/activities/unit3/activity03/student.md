### <p align=center> Ejecución del programa </p>
<img width="580" alt="image" src="https://github.com/user-attachments/assets/ff8fbeed-8768-4a7a-8856-1fdd920b8951" />

<img width="580" alt="image" src="https://github.com/user-attachments/assets/8b87b56d-d9a5-487b-b4f6-4098d6d0f6fa" />

### <p align=center> Mapa de memoria </p>
```bash
+-----------------------------------------------------------------------+
| Las intrucciones en lenguaje maquina,                                 | <--- Segmento de código (instrucciones, funciones)
| previamente compiladas a ensamblador                                  |
|                                                                       |
+-----------------------------------------------------------------------+
| int global_inicializada = 42;                                         | <--- Variables globales y estáticas
| int global_no_inicializada;                                           |
| const char* const mensaje_ro = "Hola, memoria de solo lectura";       |
| static int var_estatica = 100;                                        |
|                                                                       |
+-----------------------------------------------------------------------+
|//Con NEW se reserva memoria en el HEAP                                | <--- Heap: Asignación dinámica (new/malloc)
|int* arr = new int[tam];                                               |
|                                                                       |
|//tamArray es una variable que almacena ints y se inicializa en 10     |
|int tamArray = 10;                                                     |
|                                                                       |
|//arrayHeap es una variable que almacena la dirección de un int        |
|y la estoy inicializando con el resultado de la función crearArrayHeap,|
|que es la dirección del primer int de una array                        |
|int* arrayHeap = crearArrayHeap(tamArray);                             |
|                                                                       |
|//Liberamos la memoria HEAP, al ponerle delete. Lo cual es necesario   |
|porque esta se gestiona manualmente                                    |
|delete[] arrayHeap; // Liberamos la memoria dinámica                   |
|                                                                       |
+-----------------------------------------------------------------------+
|Son todas esas variables que estoy declarando dentro de una función    | <--- Stack: Variables locales
|pero que no las estoy definiciendo con "new",                          |
|es decir, no estoy asignando un espacio en el HEAP para ellas.         |
|Este espacio de memoria se gestiona automáticamente, osea que cuando   |
|el programa salga de la función estas variables ya se van a limpiar y  |
|ya no voy a poder acceder a ellas por fuera de la función, porque eran |
|momentaneas.                                                           |
|EJEMPLOS: int tam, static int var_estatica = 100;, int a, int b        |
+-----------------------------------------------------------------------+
```
