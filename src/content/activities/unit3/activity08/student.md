#### Capturas
| Momento | pStack  | pHeap  |
| ------------- | :---: | :---: |
| **Antes**     | <img width="300" alt="image" src="https://github.com/user-attachments/assets/f5f0fd5e-6a90-4d72-8f55-9282d3e7c48b" />| <img width="300" alt="image" src="https://github.com/user-attachments/assets/093e5e66-0b51-491a-92a9-9d72db6316ec" />|
| **Después**   | <img width="300" alt="image" src="https://github.com/user-attachments/assets/47d72307-401c-4ae4-8a2b-e4a1c2f5b85f" />| <img width="300" alt="image" src="https://github.com/user-attachments/assets/558d7595-05d1-4beb-b025-8f1e8e40ad29" />|
| **Antes**     |<img width="300" alt="image" src="https://github.com/user-attachments/assets/6c9bf681-f76e-4a11-a5f4-6a095815e11a" />|<img width="300" alt="image" src="https://github.com/user-attachments/assets/4ff9bbc3-18e9-4643-b0ca-f7253796006e" />|
| **Después**   |<img width="300" alt="image" src="https://github.com/user-attachments/assets/ee39343e-62ab-402d-a20a-1cedac0ea1be" />|<img width="300" alt="image" src="https://github.com/user-attachments/assets/e25a54d2-3427-4ab8-99c8-572a9ddea454" />|

#### Explicación de la diferencia entre objetos creados en el stack y en el heap.
Los objetos creados en el Stack cobran vida solo cuando se llama a la función o bloque en la que están, cuando la función termina este objeto que está en el Stack "puf" se muere, se libera de la memoria automáticamente. 

Mientras que los objetos creados en el Heap cobran vida ahí cuando uno escribe "new" y los puede usar desde diferentes tramos del código. Lo que pasa es que al terminar la función ya no hay nada referenciandome ese objeto del Heap, entonces ya sea el GC (C#) o uno manualmente (C++) debe ir a borrar ese objeto que quedó como "flotando" en la nada del Heap, por eso hay que guardar su dirección.

<p align="center">
<img width="500" alt="image" src="https://github.com/user-attachments/assets/cd84dbe2-0b3e-4b6c-9e81-d8be4fbf37b8" />
</p>

------------------------------------------------------------------------------------------------------------------------------
#### a. pStack ¿Es un objeto o una referencia a un objeto?
Es un objeto. Por que?

Porque pStack es una variable de tipo "punto", y recordemos que "punto" es un objeto, eso hace que pStack sea un objeto inicializado con (30,40).
#### b. pHeap ¿Es un objeto o una referencia a un objeto? Si es una referencia, ¿A qué objeto hace referencia?
Es una referencia. Por que?

Porque pHeap es una variable que guarda la * (dirección) de un dato tipo "punto". Esa varible pHeap en realidad almacena la dirección del Heap de ese "new punto" que se está creando, además se inicializa en (50, 60).

#### c. Memory and Locals de Heap ¿Qué observas? ¿Qué significa esto?
1. Antes de que se corra esa línea esa variable pHeap no ha cobrado vida ni se ha inicializado.
<img width="500" alt="image" src="https://github.com/user-attachments/assets/6a2c0706-ce24-47aa-9767-0dcca7f6bd29" />

2. Cuando se corre esa línea de una podemos ver como el contendido de "valor" es una dirección y además (50,60)
<img width="500" alt="image" src="https://github.com/user-attachments/assets/9ae9ec07-3723-48ae-82c3-d25037b54625" />

3. Al buscar en la Memory "&pHeap", es decir la dirección de esa variable pHeap, podemos ir a donde está almacenada y ver su contenido. Al hacer esto pude verificar que el contenido es en realidad la dirección de punto.
<img width="500" alt="image" src="https://github.com/user-attachments/assets/827f90e3-ca5b-4993-a8d0-04baa5ba392c" />

4. Acá verifiqué que la dirección que tenía almacena pHeap es la misma del paso #2, osea que se comprobó que pHeap en efecto almacena la misma direción de Punto.
<img width="500" alt="image" src="https://github.com/user-attachments/assets/8992884a-a0fd-4a28-bf7f-cd1f76f8a0ea" />

5. Por último el Heap se debe "deleteciar" entonces así se vió la Memory una vez se llamó al destructor y se borró todo lo correspondiente a ese objeto.
<img width="500" alt="image" src="https://github.com/user-attachments/assets/82b1d61d-8558-4a22-8b6a-64d95a0c9b99" />
