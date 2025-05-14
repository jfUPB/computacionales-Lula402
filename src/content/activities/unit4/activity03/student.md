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

