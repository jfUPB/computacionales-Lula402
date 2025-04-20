<p align=center> Dibujo de cómo se vería la lista enlazada si tuviera 3 nodos</p>

![3Nodos](https://github.com/user-attachments/assets/f51addf9-52f8-4434-b56e-f813685a1dcd)


<p align=center> Dibujo de cómo se vería la lista enlazada si tuviera 4 nodos</p>

![4Nodos](https://github.com/user-attachments/assets/442600da-3201-4f39-94c2-3c72b505f18e)

<p align=center> Dibuja un objeto de la clase LinkedList </p>

![Imagen de WhatsApp 2025-04-19 a las 19 44 50_d99a6f36](https://github.com/user-attachments/assets/8c0f8aed-debe-43f2-97fa-f34461ff949b)


#### <p align=center>¿Qué pasaría si el objeto de la clase LinkedList no tuviera el puntero a head?</p>
Si no tengo el puntero a Head no sabría donde encontrar el objeto en el Heap.


#### <p align=center>¿Podrías recorrer la lista? </p>
No podría recorrer la lista de nodos, porque no se ni siquiera donde ir a buscarlo para recorrerlo.


#### <p align=center>¿Qué pasaría si no tuviera el puntero a tail?</p>
Si no tuviera un puntero a tail, sería mucha vuelta para poder saber cual es el ultimo de la lista y asi poder crear uno nuevo o simplemente saber hasta donde recorro.


#### <p align=center>¿Podrías agregar un nuevo nodo al final de la lista? </p>
Creerría que si, pero sería muy complicado. Se me ocurre que podría ser que con el puntero de head voy y busco donde inicia el objeto, de ahí cuento el size de la lista y miro en que posición está el último nodo, la idea sería poner el nuevo nodo despues de ese. Se supone que ese ultimo nodo que encontré debería tener un "next" que al inicio es null, pero que luego va a guardar la dirección de ese nuevo nodo que yo cree a lo ultimo de la lista.


#### <p align=center>¿Qué pasaría si no tuviera el entero size? ¿Podrías saber cuántos nodos hay en la lista?</p>
Si no tuviera size no sabría a simple vista cuantos nodos tiene la lista.

Creo que si podría saber cuantos nodos hay, pero definitivamente se simplifica al tener esta variable size. Podría ir a la dirección a la que apunta Head y de ahí decifrar la memoria y mirar que tan grande está el objeto para saber cuantos nodos van en la lista.

#### <p align=center> ¿Por qué se necesario liberar la memoria que ocupa el objeto y además liberar la memoria de los nodos de la lista? ¿Qué pasaría si no lo hicieras?</p>

Es necesario liberarla, porque los punteros que nos ayudan a trackear donde está hubicado el objeto viven en el Stack. Cuando la lista se destruye, estos punteros también mueren, entonces ya no sabemos donde está el objeto. 

Si no libero la memoria entonces el objeto y sus nodos se van a quedar por ahí perdidos en el Heap y ya nadie lo puede vover a referenciar, basicamente, se vuelve un memory leak (basura).

#### <p align=center>el objeto de la clase LinkedList qué datos tiene? y ¿Cuál es la relación con los nodos de la lista? En este punto te pediré que uses el depurador para ver la memoria y poder analizar las preguntas.</p>

**Tiene 3 datos:** Node* head; Node* tail; int size;

La relacion con los nodos es que la clase LinkedList no guarda los nodos directamente, solo guarda el inicio y el final de la lista. Los nodos están conectados entre sí por punteros. Size está relacionado con los nodos porque es quien va marcando cuantos nodos hay.

#### <p align=center> cuando programas en C# no tenías que liberar la memoria de los objetos. ¿Por qué crees que en C++ es necesario liberar la memoria de los objetos?</p>

En C# está el GC y el CLR, entonces el CLR se encarga de revisar si hay cosas que ya nadie está referenciando y manda al GC a que las limpie.
En cambio, en C++ no hay GC, entonces uno mismo tiene que estar bien pendiente de limpiar todo y de rastrear dónde están las cosas en la memoria.

<p align=center> Dibujo añadiendo a LinkedList </p>

![Imagen de WhatsApp 2025-04-19 a las 20 33 17_53c402eb](https://github.com/user-attachments/assets/95745c11-cca1-4c70-b50c-978b591f1dd7)

<p align=center> Dibujo eliminando de LinkedList </p>

#### Size = 0

<img width="400" alt="image" src="https://github.com/user-attachments/assets/cc81c17c-7740-4607-97b0-6c402baa9a66" />

#### Size = 1

![Imagen de WhatsApp 2025-04-19 a las 20 41 11_32803180](https://github.com/user-attachments/assets/c91b4938-a87e-414b-ab3e-d3d0a31a348e)

#### Size = 2

![Imagen de WhatsApp 2025-04-19 a las 20 41 11_35fc8279](https://github.com/user-attachments/assets/28d736c3-c398-44d7-a866-2be7321e7a8a)

<p align=center> Dibujo clear de LinkedList </p>

![Imagen de WhatsApp 2025-04-19 a las 20 54 02_5b24b49a](https://github.com/user-attachments/assets/15423884-4e94-44e5-bc24-67ac7c07fe5d)

<p align=center> ¿Qué hace el método setup? </p>

Recorre la lista de los nodos, para poder llenarla.

<p align=center> ¿Qué hace el método update? </p>

Hace que dependiendo del movimiento del mouse, la cabeza de la snake siga el mouse y que luego cada nodo siga o se intente acercar a la posición del nodo anterior. 

<p align=center> ¿Qué hace el método draw? </p>

Dibuja todo lo que queremos ver en pantalla. El fondo asi en gradiente, la snake con en forma de lineas y los circulitos que tiene cada nodo al alrededor.

<p align=center> ¿Qué hace el método keyPressed?</p>

Dependiendo si se presiona ***c, a, r, s*** se hace una acción. C limpia toda la serpiente, a añade un nodo, r elimina el último nodo, s toma un screenshot del canvas.

