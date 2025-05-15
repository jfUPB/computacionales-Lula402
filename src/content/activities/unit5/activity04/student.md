#### 1. ¿En la actividad anterior donde estás aplicando el concepto de encapsulamiento? ¿Por qué? Muestra en qué parte del código.

En realidad se usa en varias partes del código, pero esa es una de ellas. Se usa porque se quiere mantener protegidas las varibales, osea que risingParticle quiere poner bajo llave sus cositas, pero solo algunos tienen la llave, que vendrian siendo ella misma y si tiene hijas.

```cpp
class RisingParticle : public Particle {
protected:
    glm::vec2 position;
    glm::vec2 velocity;
    ofColor color;
    float lifetime; // tiempo máximo antes de explotar
    float age;
    bool exploded;
public:
    RisingParticle(const glm::vec2& pos, const glm::vec2& vel, const ofColor& col, float life)
        : position(pos), velocity(vel), color(col), lifetime(life), age(0), exploded(false) {
    }

    void update(float dt) override {
        position += velocity * dt;
        age += dt;
        // Aumenta la desaceleración para dar sensación de recorrido largo
        velocity.y += 9.8f * dt * 8;
        // Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
        float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
        if (position.y <= explosionThreshold || age >= lifetime) {
            exploded = true;
        }
    }

    void draw() override {
        ofSetColor(color);
        // Partícula más grande
        ofDrawCircle(position, 10);
    }

    bool isDead() const override { return exploded; }
    bool shouldExplode() const override { return exploded; }
    glm::vec2 getPosition() const override { return position; }
    ofColor getColor() const override { return color; }
};
```

#### 2. ¿En la actividad anterior donde estás aplicando el concepto de herencia? ¿Por qué? Muestra en qué parte del código.
Se usa literal en todos los objetos, este es un ejemplo. Se usa porque necesitaba que NuevaParticle usara la estructura de particle, en especial los metodos virtuales, para poder simplificar y usar el mismo nombre pero diferente comportamiento.

```cpp
class NuevaParticle : public Particle
```

#### 3. ¿En la actividad anterior donde estás aplicando el concepto de polimorfismo? ¿Por qué? Muestra en qué parte del código. Te pediré que digas dónde implementas el polimorfismo y en qué parte del código lo estás usando, es decir, en qué parte estás haciendo llamados a métodos polimórficos.

Este es el update dentro de NuevaParticula:

```cpp
 void update(float dt) override {
     position += velocity * dt;
     age += dt;
     // Aumenta la desaceleración para dar sensación de recorrido largo
     velocity.y += 9.8f * dt * 8;
     // Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
     float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
     if (position.y <= explosionThreshold || age >= lifetime) {
         exploded = true;
     }
 }
```

Acá se llama a ese polimorfismo, porque ese update se ejecuta diferente al saber que es el de Nueva y no el de particle normal. (tambien esta en mas partes):

```cpp
void ofApp::update() {
    float dt = ofGetLastFrameTime();

    // Actualiza todas las partículas
    for (int i = 0; i < particles.size(); i++) {
        particles[i]->update(dt);             // ACAAAAAAAAA
    }
```

#### 4. Luego de esta experiencia de aprendizaje define con tus propias palabras ¿Qué es un objeto? ¿Qué es una clase?
Una clase es el humano original y los objetos son los hijos, que salen con la misma genética, pero son diferentes en algo.

#### 5. ¿Cómo se ve en memoria un objeto de una clase que hereda de otra clase?
Primero está lo del humano original y luego está lo que el hijo tiene de dirente.
