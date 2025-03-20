Entrega: captura de pantalla con el resultado de la ejecución del programa. Ahora trata de armar tu mismo el mapa de memoria del programa. Para ello, identifica las direcciones de memoria de las variables y constantes globales, locales, estáticas y de la memoria dinámica. Así como las direcciones de las funciones y el mensaje de solo lectura. Ten presente que los números están en hexadecimal. Cuando hagas el mapa de memoria, ubica las direcciones mayores en la parte superior y las menores en la parte inferior. Compara tu mapa de memoria con el que te mostré al inicio de la actividad.

### <p align=center> Ejecución del programa </p>
<img width="580" alt="image" src="https://github.com/user-attachments/assets/ff8fbeed-8768-4a7a-8856-1fdd920b8951" />

<img width="580" alt="image" src="https://github.com/user-attachments/assets/8b87b56d-d9a5-487b-b4f6-4098d6d0f6fa" />

### <p align=center> Mapa de memoria </p>
```
+----------------------------------------------------------------+
|    Las intrucciones en lenguaje maquina,                       | <--- Segmento de código (instrucciones, funciones)
|    previamente compiladas a ensamblador                        |
+----------------------------------------------------------------+
| int global_inicializada = 42;                                  | <--- Variables globales y estáticas
| int global_no_inicializada;                                    |
| const char* const mensaje_ro = "Hola, memoria de solo lectura";|
| static int var_estatica = 100;                                 |
+----------------------------------------------------------------+
|           Heap                                                 | <--- Heap: Asignación dinámica (new/malloc)
|                                                                |
|                                                                |
|                                                                |
|                                                                |
+----------------------------------------------------------------+
|           Stack                                                | <--- Stack: Variables locales
|           Stack                                                |
|           Stack                                                |
|           Stack                                                |
|           Stack                                                |
|           Stack                                                |
|           Stack                                                |
+----------------------------------------------------------------+
```
