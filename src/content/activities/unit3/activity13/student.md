```cpp
#include <iostream>
using namespace std;

class MensajeSecreto {
public:
    string contenido;
    double code;
    static int total;


    // Constructor
    MensajeSecreto(string _contenido, double _code) : contenido(_contenido), code(_code) {
        total++;
        cout << "Constructor: Mensaje(" << contenido << ", " << code << ") creado." << endl;
    }

    // Destructor
    ~MensajeSecreto() {
        total--;
        cout << "Destructor: Mensaje(" << contenido << ", " << code << ") destruido." << endl;
    }

    // Método para imprimirlo
    void RevelarMensaje() {
        cout << "Mensaje: (" << contenido << ", " << code << ")" << endl;
    }
};

class Agente {
public:
    void cambiarMensaje(MensajeSecreto& m, string nuevoContenido, double nuevoCode) {
        m.contenido = nuevoContenido;
        m.code = nuevoCode;
        cout << "Cambie el mensaje a: " << m.contenido << " , " << m.code << endl;
        std::cout << "\n";
    }

    void BorradorDeCambio(MensajeSecreto m, string nuevoContenido, double nuevoCode) {
        m.contenido = nuevoContenido;
        m.code = nuevoCode;
        cout << "Intentare cambiar el mensaje " << m.code << " a: " << m.contenido << endl;
        std::cout << "\n";
    }
};

int MensajeSecreto::total = 0;

int main()
{
    std::cout << "Abriendo linea secreta...\n";

    MensajeSecreto m1("Hallo", 01);
    m1.RevelarMensaje();
    std::cout << "\n";
    MensajeSecreto m2("Leute", 02);
    m2.RevelarMensaje();
    std::cout << "\n";
    MensajeSecreto* m3 = new MensajeSecreto("Ich bin", 03);
    m3->RevelarMensaje();
    std::cout << "\n";
    MensajeSecreto* m4 = new MensajeSecreto("Lula", 04);
    m4->RevelarMensaje();
    std::cout << "\n";

    cout << "MensajeSecreto::total = " << MensajeSecreto::total << endl;
    std::cout << "\n";

    Agente a1;
    a1.BorradorDeCambio(m2, "zusammen", 02);
    cout << "MensajeSecreto::total = " << MensajeSecreto::total << endl;
    std::cout << "\n";

    a1.cambiarMensaje(m2, "zusammen", 02.1);
    cout << "MensajeSecreto::total = " << MensajeSecreto::total << endl;
    std::cout << "\n";

    std::cout << "Eliminando conversacion secreta...\n";

    delete m3;
    delete m4;
}
```


<p align=center>Explicación</p>

1. Cree dos clases: ***MensajeSecreto*** y ***Agente***.
- MensajeSecreto tiene dos atributos que son contenido y código secreto. Como métodos tiene constructor, destructor y revelar mensaje.
- Agente no tiene atributos. Como métodos tiene que puede modificar los mensajes por referencia o por valor.

2. Cree 5 objetos tipo: ***MensajeSecreto*** y ***Agente***.
- 2 mensajes en el stack, que son m1 y m2.
- 2 mensajes en el Heap, que son MensajeSecreto (m3) y MensajeSecreto (m4).
- 1 agente llamado a1.

3. Cree 2 variables o mejor dicho punteros.
- 1 para poder guardar la dirección del mensaje 3 del Heap, se llama m3
- 1 para poder guardar la dirección del mensaje 4 del Heap, se llama m4

4. Cree una variable static
- static int total; todos la pueden acceder desde cualquier lado y es aproposito para mantener el conteo de cuantos mansajes hay en la linea de comunicación secreta.
  
-----------------------------------------------------------------------------------------------------------------------------

<p align=center>Análisis detallado de la memoria</p>

**string contenido; ->** segmento variables static y globales en la clase. Si el objeto esta en el stack esta variable tambien, si está en el Heap entonces esta variable tambien.

**double code; ->** segmento variables static y globales en la clase. Si el objeto esta en el stack esta variable tambien, si está en el Heap entonces esta variable tambien.

**static int total; ->**  segmento variables static y globales 

**string _contenido ->** segmento stack

**double _code ->**  segmento stack

**MensajeSecreto& m  ->**  segmento stack

**string nuevoContenido ->**  segmento stack

**double nuevoCode ->** segmento stack

**m1 ->**  segmento stack

**m2 ->**  segmento stack

**m3 ->**  segmento stack

**m4 ->**  segmento stack

**new MensajeSecreto("Ich bin", 03); ->** segmento Heap

**new MensajeSecreto("Lula", 04); ->** segmento Heap

**a1 ->** segmento stack
