### <p align=center> 1. Código fuente completo </p>
#### BrushQueue.cpp (.h)

```cpp
#pragma once
#include "ofMain.h"

// Nodo de la cola
struct Node {
    float x, y;
    float radius;
    ofColor color;
    float opacity;
    Node* next;

    Node(float _x, float _y, float _radius, ofColor _color, float _opacity)
        : x(_x), y(_y), radius(_radius), color(_color), opacity(_opacity), next(nullptr) {
    }
};

// Implementación manual de una cola (FIFO)
class BrushQueue {
public:
    Node* front;
    Node* rear;
    int size;
    int maxSize;

    BrushQueue(int _maxSize);
    ~BrushQueue();

    void enqueue(float x, float y, float radius, ofColor color, float opacity); 
    void dequeue();
    void clear();
    bool isEmpty();
};


// Constructor
BrushQueue::BrushQueue(int _maxSize) : front(nullptr), rear(nullptr), size(0), maxSize(_maxSize) {}

// Destructor
BrushQueue::~BrushQueue() {
    clear();
}

// Implementa aquí `enqueue()`
void BrushQueue::enqueue(float x, float y, float radius, ofColor color, float opacity) {
    // TODO: crear un nuevo nodo y agregarlo al final de la cola.
    // Si la cola supera `maxSize`, eliminar el nodo más antiguo con `dequeue()`.

    if (size == maxSize) {
        dequeue();

        Node* newNode = new Node(x, y, radius, color, opacity);
        rear->next = newNode;
        rear = newNode;
    }
    else {
        Node* newNode = new Node(x, y, radius, color, opacity);
        if (front == nullptr) {
            front = rear = newNode;
        }
        else {
            rear->next = newNode;
            rear = newNode;
        }
        size++;
    }
}

// Implementa aquí `dequeue()`
void BrushQueue::dequeue() {
    // TODO: eliminar el nodo más antiguo si la cola no está vacía.
    if (front == nullptr) return;

    Node* temp = front->next;
    delete front;
    front = temp;
    size--;
}

// Implementa aquí `clear()`
void BrushQueue::clear() {
    // TODO: eliminar todos los nodos de la cola.
    Node* current = front;
    while (current != nullptr) {
        Node* nextNode = current->next;
        delete current;
        current = nextNode;
    }
    front = rear = nullptr;
    size = 0;
}

// Implementa aquí `isEmpty()`
bool BrushQueue::isEmpty() {
    // TODO: retornar si la cola está vacía.
    return size == 0;
}


class ofApp : public ofBaseApp {
public:
    BrushQueue strokes; // Cola de trazos
    float backgroundHue = 0;

    ofApp() : strokes(50) {} // Tamaño máximo de la cola

    void setup();
    void update();
    void draw();
    void keyPressed(int key);
};
```

#### ofApp.cpp (.cpp)

```cpp
#include "ofApp.h"
#include <iostream>
using namespace std;

int index = 0;

//--------------------------------------------------------------
void ofApp::setup() {
    ofBackground(0);
}

//--------------------------------------------------------------
void ofApp::update() {
    backgroundHue += 0.2;
    if (backgroundHue > 255) backgroundHue = 0;

    if (ofGetMousePressed()){
         float x = ofGetMouseX();
         float y = ofGetMouseY();
         ofColor color;
         color.setHsb(ofRandom(255), 255, 255); 
         float radius = ofRandom(5, 20);
         float opacity = ofMap(index, 0, strokes.size - 1, 50, 255);
         strokes.enqueue(x, y, radius, color, opacity);
         index++;
    }

    // TODO: agregar un nuevo trazo si el mouse está presionado.
    // Usa strokes.enqueue(x, y, radius, color, opacity);
}

//--------------------------------------------------------------
void ofApp::draw() {
    // Fondo con gradiente dinámico
    ofColor color1, color2;
    color1.setHsb(backgroundHue, 150, 240);
    color2.setHsb(fmod(backgroundHue + 128, 255), 150, 240);
    ofBackgroundGradient(color1, color2, OF_GRADIENT_LINEAR);

    // TODO: dibujar los trazos almacenados en la cola.
    // Recorre los nodos desde strokes.front hasta nullptr y usa ofDrawCircle().

    Node* current = strokes.front;
    int index = 0;

    while (current != nullptr) {
        Node* nextNode = current->next;
        float opacity = ofMap(index, 0, strokes.size - 1, 50, 255);
        ofSetColor(current->color, opacity);
        ofDrawCircle(current->x, current->y, current->radius);
        current = current->next;
        index++;
    }
}

//--------------------------------------------------------------




void ofApp::keyPressed(int key) {
    
    if (key == 'c') {
        strokes.clear();
        index = 0;
    }
    if (key == 'a') {
        if (strokes.maxSize == 50) {
            cout << "maxSize anterior: " << strokes.maxSize << endl;
            strokes.maxSize = 100;
        } 
        else {
            cout << "maxSize anterior: " << strokes.maxSize << endl;
            strokes.maxSize = 50;
        }
        // TODO: alternar entre 50 y 100 trazos.

        while (strokes.size > strokes.maxSize) {
            strokes.dequeue();
        }
        cout << "max Size cambiado: " << strokes.maxSize << "\n" << endl;
    }
    else if (key == 's') {
        ofSaveFrame();
        // TODO: guardar el frame actual.
    }
}
```

### <p align=center> 2. Capturas de pantalla </p>
Todo es mejor en video: 

https://youtu.be/v1l4IByJJcI

Ahi se puede ver como se generan los strokes cuando doy click y muevo. Se evidencia que los trazos más antiguos, osea el primero que se haya puesto, se van borrando gradualmente cuando se alcanza el max size.
Para hacer la prueba de que con a si cambiara el max size, imprimi por consola el mx size anterior y el cambiado, de todas manera se nota porque la cola se borra más lento cuando max size es = 100.

### <p align=center> 3. Uso del depurador en Visual Studio </p>
<img width="800" alt="image" src="https://github.com/user-attachments/assets/565151ae-e70a-4483-97e6-64198cb5b000" />

Usé el depurador de Visual Studio, agregué unos strokes en el canvas y luego al darle ***c*** (clear) observé que si se habían eliminado con exito todos los nodos y sin dejar fugas de memoria. El front y el rear se hicierojn null y ademas la variable key almacenó un 99, que es el código ASCII para la tecla c. 


### <p align=center> 4. Lista de pruebas realizadas </p>

### Prueba 1
#### Qué intentaste probar: 
Intenté probar si ya tenía full bien enqueue, dequeue. En el update por el momento solo me encargaba de la posición (x,y) y del radio que era random entre 5 y 20, aun no estaba trabajando con color y opacidad.
#### Qué resultado esperabas obtener: 
Esperaba que cuando la cola alcanzara el maxSize si se empezaran a borrar los primero trazos que había hecho.
#### Qué resultado obtuviste:
La cola con todos los strokes se veia blanca y si variaba el radio entre cada una. Al alcanzar maxsize si se empezaban a borrar los first in.
#### Si el resultado fue correcto o si tuviste que corregir algo:
Fue correcto.

-----------------------------------------------------------------------------------------------------------------------------

### Prueba 2
#### Qué intentaste probar:
Intenté probar que la opacidad si disminuyera gradualmente, para que el primero que pinté tuviera menos opacidad y el último que habia pintado tuviera full la opacidad.
#### Qué resultado esperabas obtener: 
Esperaba un gusanito (cola con strokes) asi como el de la referencia, bien gradual ese cambio en la opacidad.
#### Qué resultado obtuviste:
Todo aparecía con la misma opacidad full.
#### Si el resultado fue correcto o si tuviste que corregir algo:
Me acordé que tenia que recorrer la cola, entonces puse un while en el update, porque yo queria determinar todo en el update y solo pintar en el draw.

#### Qué resultado obtuviste:
Se ponia la opacidad gradualmente pero solo al hacer el primer trazo, a partir de ahí ya todos tenian otra vez la opacidad full.
#### Si el resultado fue correcto o si tuviste que corregir algo:
Me tocó poner el while con el que recorría la cola dentro del draw en vez de tenerlo en el update. A la final eso si tenia más lógica, porque en el update determinaba que la opacidad iba a aumentar segun el index (orden) en el que estaban, y ya en el draw si recorria la cola para pintar cada uno.

#### Qué resultado obtuviste:
Me volvía a equivocar, otra vez solo se veia gradual en el primer trazo.
#### Si el resultado fue correcto o si tuviste que corregir algo:
La solución fue calcular un opacity inicial en el update, para poder entregarle ese valor que esperaba el parametro en el enqueue. Luego también poner dentro del while en el que pintaba los strokes otra calculada del opacity, entonces segun el index se le asignaba una opacity gradual y dentro de ese mismo while se pintaba con esa opacity.

#### Qué resultado obtuviste:
Me volvía a equivocar, otra vez solo se veia gradual en el primer trazo.
#### Si el resultado fue correcto o si tuviste que corregir algo:
Resulta que estaba usando current->opacity y pues si hacia eso, estaba agarrando el opacity calculado en el update. La solución fue solo poner ***opacity** poque ahi si estaba tomando el valor de lo que estaba calculando dentro del draw.

-----------------------------------------------------------------------------------------------------------------------------

### Prueba 3
#### Qué intentaste probar: 
Que a cambiara el maxsize como debía
#### Qué resultado esperabas obtener:
Que cambiara el maxsize como debía
#### Qué resultado obtuviste:
Empieza en 50, luego lo cambiaba a 100 y cuando lo volvía a cambiar a 50 se bloqueaba la cola y ya nunca borra los strokes.
#### Si el resultado fue correcto o si tuviste que corregir algo:
Tuve que corregir que si al pasar de maxsize= 100 a  maxsize= 50 la cantidad de trazos era mayor a 50, pues entonces borrar esos excedentes para que no se bloqueara. Asi el programa podia decir "tenemos 100 y solo ponemos tener 50, entonces voy a borrar los que sobran", luego, "listo borré los que sobran, quedamos con 50, si nos pasamos por 1 empezamos a borrar"
