#### 5 nodos
![5Nodos](https://github.com/user-attachments/assets/bdef6d6b-bf57-421b-84a5-dea0a12f029c)

#### Inserta un nodo
![NuevoNodo](https://github.com/user-attachments/assets/90788f55-4a81-4461-bf18-1fb1e8e6f0a0)

#### elimina un nodo
![EliminarNodo](https://github.com/user-attachments/assets/fc74da39-a676-4243-a405-dda9ead1745b)

#### limpia la lista
![0Nodos](https://github.com/user-attachments/assets/9304bead-1d9a-494a-902d-5a0fed6b0229)

<p align=center> ¿Cómo se crea la lista enlazada? </p>
En ofApp.h. Se crea una lista de vectores.

```cpp
std::list<glm::vec2> snake;
```

<p align=center> ¿Cómo se añaden los primero nodos a la lista? </p>
En el .cpp está el método setup(), ahí está el siguiente ciclo que debe ser para recorrer la lista de vectores e irla llenando.

```cpp
void ofApp::setup() {
    backgroundHue = 0;

    // Inicializa la serpiente con varios nodos en el centro
    for (int i = 0; i < 20; i++) {
        snake.emplace_back(ofGetWidth() / 2, ofGetHeight() / 2);
    }
}
```

<p align=center> ¿Cómo se añaden nodos adicionales a la lista? </p>

En el .cpp está el método keyPressed(), que al parecer lo que hace es que al presionar "a" a la lista ***snake*** le añade otro nodo en el back, osea al final.

```cpp
else if (key == 'a') {
    snake.emplace_back(ofRandomWidth(), ofRandomHeight());
}
```
<p align=center> ¿Cómo se eliminan nodos de la lista? </p>
En el .cpp está el método keyPressed(), que al parecer lo que hace es que si se presionar "r" y si la lista es diferente a vacía, osea que si hay serpiente ya con nodos, entonces como que la lista de la snake la compacta.

```cpp
   else if (key == 'r') {
       if (!snake.empty()) {
           snake.pop_back();
       }
```

<p align=center> ¿Cómo se limpia la lista? </p>

En el .cpp está el método keyPressed(), que al parecer lo que hace es que si se presionar "c" borra todos los nodos. clear() deja la lsita vacía.

```cpp
   if (key == 'c') {
    snake.clear();
}
```

<p align=center> ¿Cómo se verifica si la lista está vacía? </p>

Al poner ***!snake.empty*** se está queriendo decir que si la lista es diferente de vacía, osea si la snake si tiene cosas, entonces que entre al if.

```cpp
if (!snake.empty()) {
    
}
```
