#### ¿Qué valor en decimal obtienes? 
DEC= 160

#### Escribe 14 ¿Qué valor en decimal obtienes? ¿Qué observas?
DEC= 20

#### ¿Cómo quedarían almacenados los bytes en la memoria de p?
Los bytes quedan almacenados con little-endian, es decir del menor Byte al mayor. P tiene (10,20) como valores para (x,y) y como 10 es un int de 32 bytes aparece primero que el 20, ya que es menor.
32 Bytes de 10 = 0a 00 00 00 
32 Bytes de 20 = 14 00 00 00

#### ¿Cuál es la diferencia entre un constructor y un destructor en C++?
La diferencia es que el constructor básicamente inicializa el objeto y un destructor lo que hace es que destruye lo que está en el stack. Basicamente el destructor cumple la función del Garbage Collector de C#, porque en C++ no hay eso.

#### ¿Cuál es la diferencia entre un objeto y una clase en C++?
Una clase es un molde, donde basicamente creamos un nuevo tipo de dato con ciertas características y ademán de una vez le metemos ahí como es que se va porder manipular ese dato y las cosas que se le puede hacer (funciones). 
Mientras que un objeto es una instancia de ese molde, es decir es un hijito (objeto) que tiene todo lo que tiene ese molde, porque fue hecho con eso.

#### ¿Qué diferencia notas entre el objeto Punto en C++ y C#?
El objeto Punto en C++ está creado en el Stack, entonces cuando 

#### ¿Qué es p en C++ y qué es p en C#? (en uno de ellos p es un objeto y en el otro es una referencia a un objeto).
p en C++ es un objeto, porque lo crea directamente en el stack y simplemente está diciendo que p es un objeto tipo punto.
p en C# es una referencia al objeto, porque lo crea en el Heap al decir "new" y basicamente el "punto p" está guardando la dirección del "nuevo punto".

#### ¿En qué parte de memoria se almacena p en C++ y en C#?
En C++, p se almacen a en el Stack, es decir que cuando salga del main este se va a destruir. En C#, p está creado en el Heap, entonces lo puedo usar en otros lados del código y la ventaja es que es GC y el CLR están pendientes de si sigue referenciado o no para limpiarlo.

#### Captura de pantalla del depurador mostrando la variable p y su dirección de memoria.

| Antes de crear p  | Despues de crear p |
| ------------- | ------------- |
| <img width="350" alt="image" src="https://github.com/user-attachments/assets/bba8237b-e40d-419d-a7be-69e5f3fce63b" /> | <img width="350" alt="image" src="https://github.com/user-attachments/assets/785e612b-037a-417b-8b8f-78185e7a26a4" /> | 
| <img width="350" alt="image" src="https://github.com/user-attachments/assets/9788f4ca-6a89-4189-80be-7038a2622fa2" /> | <img width="350" alt="image" src="https://github.com/user-attachments/assets/bfc90576-4162-47c1-9b8b-483354b1ef7e" /> |
| <img width="350" alt="image" src="https://github.com/user-attachments/assets/c16d6ae3-609d-4df8-a198-99d5d4756590" /> | <img width="350" alt="image" src="https://github.com/user-attachments/assets/1cf1d4b7-4a9d-4072-85c7-c3f750fde1a4" /> |

#### ¿Qué observaste con el depurador acerca de p? Según lo que observaste ¿Qué es un objeto en C++?
Antes de que p tipo punto se ejecute, el depurador de C++ sabe que ahí va una (x,y) entonces de una vez los pone ahí y ya cuando el objeto si se crea en el stack, entonces pone (10,20).
Un objeto en C++ es una instancia de la clase con sus valores especfíficos.
