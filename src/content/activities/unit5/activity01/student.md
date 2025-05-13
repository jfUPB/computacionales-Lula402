
<p align=center> Análisis del código .CPP </p>

### 1. 
``` cpp
void ofApp::setup() {
    ofSetFrameRate(60);
    ofBackground(0);
}
```
Este método se corre una sola vez al principio de programa. Configura que corra a 60 FPS y que el fondo sea negro

### 2. 
``` cpp
void ofApp::update() {
    float dt = ofGetLastFrameTime();

    // Actualiza todas las partículas
    for (int i = 0; i < particles.size(); i++) {
        particles[i]->update(dt);
    }

    // Procesa las partículas (iteración en reversa para facilitar eliminación)
    for (int i = particles.size() - 1; i >= 0; i--) {
        // Si la partícula debe explotar, generamos nuevas explosiones
        if (particles[i]->shouldExplode()) {
            int explosionType = (int)ofRandom(3); // 0: Circular, 1: Random, 2: Star
            int numParticles = (int)ofRandom(20, 30);
            for (int j = 0; j < numParticles; j++) {
                if (explosionType == 0) {
                    particles.push_back(new CircularExplosion(particles[i]->getPosition(), particles[i]->getColor()));
                }
                else if (explosionType == 1) {
                    particles.push_back(new RandomExplosion(particles[i]->getPosition(), particles[i]->getColor()));
                }
                else {
                    particles.push_back(new StarExplosion(particles[i]->getPosition(), particles[i]->getColor()));
                }
            }
            delete particles[i];
            particles.erase(particles.begin() + i);
        }
        else if (particles[i]->isDead()) {
            delete particles[i];
            particles.erase(particles.begin() + i);
        }
    }
}
```
Primero actualiza todas las partículas (las que están en pantalla), Después revisa si alguna partícula:

- Debe explotar, entonces crea nuevas partículas con forma de explosión.

- Ya murió (porque ya explotó o se acabó su tiempo de vida), entonces también la borra.

### 3. Draw
``` cpp
void ofApp::draw() {
    for (int i = 0; i < particles.size(); i++) {
        particles[i]->draw();
    }
}
```
Lo que hace es pintar lo que debería ir en pantalla cada frame. Es como en interactivos que el draw se encarga de que en cada iteración pinte.

### 4.
``` cpp
void ofApp::createRisingParticle() {
    // Genera una RisingParticle cerca del centro inferior (con variación horizontal)
    float minX = ofGetWidth() * 0.35;
    float maxX = ofGetWidth() * 0.65;
    float spawnX = ofRandom(minX, maxX);
    glm::vec2 pos(spawnX, ofGetHeight());
    // La partícula apunta hacia un objetivo en la parte superior central
    glm::vec2 target(ofGetWidth() / 2 + ofRandom(-300, 300), ofGetHeight() * 0.10 + ofRandom(-30, 30));
    glm::vec2 direction = glm::normalize(target - pos);
    // Velocidad ajustada para recorrer una mayor distancia
    glm::vec2 vel = direction * ofRandom(250, 350);
    ofColor col;
    col.setHsb(ofRandom(255), 220, 255);
    float lifetime = ofRandom(1.5, 3.5); // Tiempo de vida antes de explotar
    particles.push_back(new RisingParticle(pos, vel, col, lifetime));
}
```

Cuando presionamos el mouse o el espacio, crea una partícula que sube desde abajo hacia el centro arriba. Le asigna la dirección random para que no todas suban igual. Le da color, velocidad y cuánto tiempo debe vivir antes de explotar.

### 5.
``` cpp
void ofApp::mousePressed(int x, int y, int button) {
    createRisingParticle();
}

// --------------------------------------------------------------
void ofApp::keyPressed(int key) {
    if (key == ' ') {
        for (int i = 0; i < 1000; i++) {
            createRisingParticle();
        }
    }
    if (key == 's') {
        ofSaveScreen("screenshot_" + ofToString(ofGetFrameNum()) + ".png");
    }
}
```
Con espacio se crean 1000 particulas, con click se crea una particula, com s se guarda el screenshot.

### 6.
``` cpp
ofApp::~ofApp() {
    for (int i = 0; i < particles.size(); i++) {
        delete particles[i];
    }
    particles.clear();
}
```
Recorre el array de las particulas y las va borrando para que no queden flotando en la memoria.

<p align=center> Análisis del código .h </p>

### Clase Particle
Es el molde de las galletas para que las partículas que se creen hereden de esta.
Tiene los métodos: update(), draw(), isDead(), shouldExplode(), etc.

### RisingParticle
Es la que sube desde abajo. Sube por un tiempo o hasta cierta altura, entonces cuando llega a ese punto "máximo", explota.
Tiene color, posición, velocidad, tiempo de vida, etc.

### Explosiones 
Aparecen cuando la particula que subió explota.

#### CircularExplosion
Sale en todas direcciones como un círculo.
Partículas que se ven como bolitas.

#### RandomExplosion
Direcciones totalmente random.
Se dibujan como cuadraditos.

#### StarExplosion
Dibuja líneas que parecen los rayitos de una estrella.

<p align=center> Captura pantallas de la aplicación funcionando </p>

Un click:

<img width="300" alt="image" src="https://github.com/user-attachments/assets/a4f93506-7558-4454-904f-d9dac48c3d78" />

Varios clicks:

<img width="300" alt="image" src="https://github.com/user-attachments/assets/8f00c45a-0d85-41ce-bb5c-05c31171e235" />

Con la tecla espacio:

<img width="300" alt="image" src="https://github.com/user-attachments/assets/5513e0cb-eb9f-419a-bbdf-8fa8d2feca6e" />

<p align= center> ¿Cómo puedes interactuar con la aplicación? </p>

Puedo interactuar usando los clicks del mouse, tanto el derecho como el izquierdo. Con la tecla espacio se crean mil particulas y ahí es cuando el canvas se llena de las figuras. Con la tecla **S** se guarda el screenshot de lo que se esté viendo en el canvas.
