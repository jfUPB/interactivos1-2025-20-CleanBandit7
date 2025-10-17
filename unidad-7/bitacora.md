
# Evidencias de la unidad 7

**Nota Antes De Empezar:** YO PUEDO PASAR LA MATERIA =)

# ACTIVIDAD 01

**1. Prepara el proyecto:**
  - Descarga o clona el código del caso de estudio en tu computador. El código está en este repositorio.
  - Abre una terminal en la carpeta raíz del proyecto.
  - Ejecuta npm install para instalar las dependencias (express, socket.io). Haz esto solo la primera vez.

**2. Inicia el servidor local:**
  - Abre la carpeta del proyecto en VS Code.
  - Abre una terminal integrada en VS Code (View > Terminal).
  - En la terminal, ejecuta npm start.
  - Deberías ver el mensaje: Server is listening on http://localhost:3000. ¡Pero aún no accedas a esa URL!

**3. Expón el servidor con Dev Tunnels:**
  - Selecciona PORTS. Click en Forward a Port (Dev Tunnels).
  - En el número de puerto, selecciona 3000 (¿Por qué este?)
  - En la columna Visibility, selecciona Public. Esto permitirá que el túnel sea accesible desde cualquier lugar.
  - Copia la URL que aparece en la columna Forwarded Address. Esta URL es la que usarás para acceder al servidor desde tu celular.
  - Envía esta URL a tu celular. Se verá algo como https://TU-TENDRAS-UNA-DIFERNTE.use2.devtunnels.ms/.

**4. Accede a las aplicaciones:**
  - En tu Computador: abre un navegador web y ve a la URL: http://localhost:3000/desktop/. Deberías ver el canvas de p5.js con un círculo rojo.
  - En tu Celular: abre un navegador web y ve a la URL que enviaste pero añadiendo /mobile/ al final. Algo así como esto: https://TU-TENDRAS-UNA-DIFERNTE.use2.devtunnels.ms//mobile/ (Asegúrate de añadir /mobile/ al final). Deberías ver el canvas de p5.js con el texto “Touch to move the circle”.

**5. Prueba la interacción:**
  - Toca y mueve el dedo sobre la pantalla de tu celular.
  - Observa el navegador de tu computador. El círculo rojo debería moverse siguiendo tu dedo.
  - Observa la terminal donde corre server.js. Deberías ver mensajes “New client connected”, “Received message => …”, y “Client disconnected” cuando cierras las pestañas.

**6. Cierra el Port:** una vez termines de hacer las pruebas NO OLVIDES CERRAR el puerto.

**7. ¿Si cerraste el puerto?**

**REPORTE DE BITÁCORA DE LA ACTIVIDAD 01:**

A. Por qué en el número de puerto se tiene que seleccionar 3000?

RTA: Para comprender esto, primero se tiene que recalcar que en este caso el puerto es un tipo de "canal" que permite que el dispositivo local reciba datos de internet, por ejemplo cuando se utiliza http, el número de puerto sería 80, cuando se usa https es el puerto 443. Como en este caso, en el archivo server.js se define que el puerto a utilizar es el 3000 ya que este es el número de puerto de Node.js, al seleccionarlo, cuando se abre el link de Dev Tunnels en internet, tanto en el pc como en el teléfono, lo que se está haciendo es "decirle" a VS code que cree un túnel o una vía desde internet hasta mi puerto 3000 local que hace que cuando en el teléfono se abra el link se reenvíe directamente al localhost:3000 del pc  los datos de la pantalla touch del mismo y estos se vean reflejados en la pantalla del pc.

En esta sección del código de server.js se ve donde se determina que el puerto de conexión para recibir una rta por parte del pc será el 3000:

```js
server.listen(3000, () => {
  console.log("Server is listening on http://localhost:3000");
});
```


B. ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?

RTA: 

- La URL que obtuve con Dev Tunnels fue https://wkszwzmd-3000.use2.devtunnels.ms/

- El uso de una URL generada por herramientas como Dev Tunnels es necesario porque localhost es una dirección interna que solo existe dentro del propio computador. Cuando se escribe "http://localhost:3000", el sistema operativo entiende que la conexión debe hacerse al puerto 3000 del mismo dispositivo, no desde otro equipo.

Por esta razón, si intento acceder desde mi celular usando esa dirección, el navegador del celular buscará el puerto 3000 en el mismo teléfono, donde no hay ningún servidor corriendo, lo que hace imposible la conexión.

La URL del túnel (https://wkszwzmd-3000.use2.devtunnels.ms/) actúa como un puente entre Internet y mi servidor local. Es decir, crea una dirección pública temporal que redirige el tráfico hacia el puerto 3000 de mi computador, permitiendo que otros dispositivos, como el teléfono, se conecten y envíen datos al servidor.

Aunque teóricamente podría usarse la IP local del computador (por ejemplo, http://192.168.1.5:3000), esto solo funcionaría si ambos dispositivos están en la misma red Wi-Fi y si el firewall permite ese tipo de conexiones, lo cual no siempre es seguro ni confiable. Por eso, el túnel se convierte en la opción más práctica y estable para realizar pruebas entre el servidor local y dispositivos externos.


C.  Describe brevemente qué hace npm install y npm start.

RTA:

- **npm install:** Se encarga de descargar e instalar todas las dependencias que un proyecto necesita para funcionar. Estas dependencias están listadas en el archivo package.json y pueden ser librerías, frameworks o herramientas que el proyecto requiere. Por ejemplo, si el proyecto usa Express para crear un servidor web o Socket.io para comunicación en tiempo real, npm install descargará esas librerías y las guardará dentro de la carpeta "node_modules".

- **npm start:** Se utiliza para ejecutar la aplicación, lo que hace realmente es correr el script definido en la sección "start" del archivo package.json. En muchos proyectos de Node.js, este script lanza el servidor principal, o para resumir, npm pone en marcha la aplicación para que se pueda usar y probar.


D. ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?

RTA: En este caso, cuando se conecta la señal de DevTunnels tanto en el pc como en el telédono, apareció el mismo mensaje de "new client connected" y cuando se toca la pantaalla en el celular, aparece "recieved message" junto a las coordenadas registradas en el mismo.

<img width="426" height="108" alt="Captura de pantalla 2025-10-14 105356" src="https://github.com/user-attachments/assets/d0e126df-8fa8-4bb3-93e8-aa3085e0b6eb" />


<img width="716" height="445" alt="Captura de pantalla 2025-10-14 105324" src="https://github.com/user-attachments/assets/03ed8fe7-48dc-488e-a139-fdcfa3638fc5" />

E. Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?

RTA: Tras realizar el vínculo de DevTunnels de manera adecuada, se logró establecer la conexión y en este caso, se pudo interactuar con el círculo rojo que aparecía en pantalla en el pc desde el tacto del teléfono, sin embargo, pude identificar que si tocaba ligeramente la pantalla en ubicaciones al asar, el círculo no se desplazaría directamente, sino que tocaba mantener oprimido el dedo sobre la pantalla durante algunos segundos. Además, pude notar que aunque el círculo se desplazaba cuando movía el dedo por la pantalla, este tenía un pequeño retraso de algunos milisegundos, no obstante, la interacción funcionó de manera adecuada.


**SEEK: INVESTIGACIÓN**

  Para desglozar el sistema base utilizado anteriormente necesitamos comprender los siguientes conceptos clave:

  - **Socket.io:** es la librería virtual que permite la conección en dos direcciones entre el pc y el teléfono en tiempo real, permitiendo que ambos dispositivos puedan enviar y recibir "mensajes" o datos de manera instantánea sin necesidad de recargar la página una vez se establezca la conexión.

  - **Dev Tunnels:** Es el canal que permite establecer la conexión entre el pc y otros dispositivos externos usando la red wifi mediante una URL pública. Gracias a esto, el celular puede acceder al servidor Node.js que está corriendo en nuestro computador, incluso si no están en la misma red.

  - **Eventos Táctiles (Touch del móvil):** Gracias a funciones en el código de la aplicación en p5.js como 'touchMoved()', se detectan las coordenadas en las que tiene contacto el táctil del teléfono con el dedo del usuario, enviando los datos al pc y permitiendo ver el movimiento del táctil en la pantalla del pc.

  Una vez entendido estos tres conceptos como un conjunto que forman el puente se puede proceder a explicar cada uno de sus elementos claves para su funcionamiento:

  1. **El servidor Node.js: el puente de comunicación**

    El archivo server.js cumple la función de intermediario.
    
    - Recibe los mensajes que provienen del celular (coordenadas x, y del toque).
    
    - Luego, reenvía esa información al cliente de escritorio usando Socket.IO. De esta manera, el servidor no procesa los datos, solo los distribuye: es como un mensajero que recibe un paquete y lo entrega al destinatario correcto.
    
    - Además, el servidor usa express.static('public') para compartir los archivos de las carpetas desktop y mobile, que contienen los sketches de p5.js. Así, ambos clientes pueden acceder a sus interfaces desde el navegador.

  2. **El cliente móvil: captura y envío de datos táctiles**

    Como se mencionó antes, en el archivo "mobile/sketch.js", el código usa la función "touchMoved()" de p5.js para obtener las coordenadas del dedo (x, y) mientras el usuario toca la pantalla.
    Cada vez que el dedo se mueve más allá de un pequeño umbral (threshold), el cliente envía esas coordenadas al servidor mediante un socket.
    Esto evita enviar demasiados datos por cada movimiento mínimo, reduciendo el consumo de red y mejorando el rendimiento.
    En resumen, el celular actúa como un sensor de entrada, convirtiendo el movimiento del dedo en datos numéricos.

  3. **Cliente de escritorio: visualización en tiempo real**

    El archivo desktop/sketch.js es el encargado de recibir los datos que el servidor retransmite.
    Cada vez que el servidor envía un mensaje con las coordenadas del toque, el cliente de escritorio actualiza la posición del círculo rojo en el canvas.
    Así, se genera una visualización interactiva que responde directamente al movimiento del dedo en el celular.

  Como conclusión, se puede decir que este sistema combina diferentes tecnologías teniendo el táctil del teléfono como un controlador físico, el servidor com un intermediario lógico y el computador como una pantalla visualizadora o medio de recepción.



# ACTIVIDAD 02


1. **El problema de la conexión directa:**

- Cuando ejecutas npm start, el servidor escucha en localhost:3000. localhost (o 127.0.0.1) es una dirección especial que siempre se refiere a tu propia máquina.
- Si intentaras acceder a http://localhost:3000 desde tu celular, este buscaría un servidor en el propio celular, no en tu computador.
- Podrías usar la IP local de tu computador (ej. 192.168.1.X), pero esto solo funciona si ambos dispositivos están en la misma red Wi-Fi y no hay firewalls bloqueando. No funcionaría si tu celular usa datos móviles o está en otra red.
- Necesitamos una dirección pública y accesible desde cualquier lugar.


2. **La solución: VS Code Dev Tunnels (Port Forwarding):**

- Dev Tunnels actúa como un intermediario seguro. Crea un túnel desde una URL pública en Internet (la que obtuviste, como https://TU-TENDRAS-UNA-DIFERNTE.use2.devtunnels.ms/) hasta el puerto 3000 de tu localhost.
- Cuando tu celular (o cualquier cliente en Internet) se conecta a la URL pública de Dev Tunnels, el servicio de Dev Tunnels reenvía esa conexión de forma segura a través del túnel hasta tu servidor Node.js local.
- Del mismo modo, las respuestas de tu servidor local viajan de vuelta por el túnel hasta el servicio Dev Tunnels, que las entrega al cliente (celular/escritorio).
- Analogía: Es como tener un número de teléfono público (la URL de Dev Tunnels) que redirige las llamadas a tu teléfono privado en casa (localhost:3000), sin exponer directamente tu número privado.


3. **Capturando la entrada: eventos táctiles en p5.js (mobile/sketch.js):**

- p5.js ofrece funciones específicas que se ejecutan automáticamente cuando ocurren eventos táctiles en un dispositivo móvil (o simulación en escritorio).
- touchMoved(): es la función clave aquí. Se llama continuamente mientras el usuario mantiene un dedo presionado y lo mueve sobre el canvas. Dentro de esta función, mouseX y mouseY contienen las coordenadas actuales del toque.
- Optimización (threshold): el código no envía un mensaje en cada pequeño movimiento detectado por touchMoved(). Comprueba si el movimiento desde la última vez que se envió (lastTouchX, lastTouchY) supera un umbral (threshold). Esto evita inundar la red con mensajes si el dedo tiembla o se mueve mínimamente, enviando solo cambios significativos.
- Otras funciones útiles (no usadas en este caso base, pero relevantes):
  - touchStarted(): se llama una vez cuando el usuario toca la pantalla por primera vez.
  - touchEnded(): se llama una vez cuando el usuario levanta el dedo de la pantalla.

**REPORTE DE BITÁCORA EN LA ACTIVIDAD 02:**

A. Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?

RTA: Dev Tunnels es necesario ya que este es el que permite que el computador se pueda conectar a una red pública vía internet a la cuál pueden acceder dispositivos externos sin necesidad de estar conectados a la misma red, de manera que cuando desde el dispositivo externo, en este caso el teléfono, haya una interacción de tacto (un toque o desliz con el dedo) las coordenadas del mismo sean reportadas al Node.js del pc y esto haga que se represente gráficamente en la pantalla del pc. Básicamente DevTunnels funciona conceptualmente como un "puente" o "tunel" que da paso a la conexión entre el pc (dispositivo local) y el teléfono (dispositivo externo).

B. Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.

RTA: La función touchMoved() es la que permite registrar las coordenadas en X y Y del toque realizado sobre la pantalla táctil del teléfono, lo que permite enviar después esos datos al pc y así registrar el movimiento del mismo en la versión visual de la aplicación. En este caso, la variable treshold ayuda a que cuando haya una interacción muy leve cuando se realice el toque, es decir que medio se roce la pantalla o se toque levemente, no se registre el movimiento de manera inmediata para así, tener menos "descontrol" sobre el envío de corrdenadas que se va a realizar hacia el pc.

C. Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?

RTA: Usar la IP local permite conectar dispositivos que están dentro de la misma red Wi-Fi, sin necesidad de Internet, lo que suele hacer la comunicación un poco más rápida y directa. Sin embargo, esta opción solo funciona si el celular y el computador están en la misma red y no hay bloqueos del router o firewalls. En cambio, Dev Tunnels no necesita que ambos dispositivos compartan la misma red: crea un túnel seguro a través de una URL pública que cualquiera con Internet puede usar para conectarse al servidor local. Su principal ventaja es la accesibilidad y la seguridad, aunque depende de la conexión a Internet y puede generar un poco más de latencia al enviar los datos.

D. Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).

RTA: Aquí está el video del funcionamiento del sistema y algunas capturas de la terminal:

[Demostración del Uso de la Aplicación](https://youtu.be/d-XlG-U2DxQ)

<img width="718" height="405" alt="Captura de pantalla 2025-10-17 000729" src="https://github.com/user-attachments/assets/7f6709ca-3d2e-45e2-909f-ad364de6a0e4" />


# ACTIVIDAD 03

Enunciado

Vamos a analizar el código server.js. Este script actúa como un repetidor simple pero esencial, recibiendo mensajes del cliente móvil y retransmitiéndolos al cliente de escritorio.


**REPORTE DE BITÁCORA ACTIVIDAD 03:**

A. ¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?

RTA: La función principal de express.static('public') es permitir que el servidor entregue directamente los archivos que están dentro de la carpeta “public” sin tener que crear rutas manualmente. Es decir, si dentro de esa carpeta hay un archivo HTML, JS o CSS, el servidor lo puede enviar automáticamente al navegador cuando se le pide.
En cambio, en la Unidad 6 usábamos app.get('/ruta', …) para definir de forma manual qué debía responder el servidor cuando alguien accedía a una dirección específica. Esa forma es más controlada, pero también más tediosa cuando tienes muchos archivos.
En conclusión, express.static hace el trabajo más simple y eficiente, sobre todo cuando queremos servir una aplicación web completa (como la del desktop o el mobile) sin tener que escribir una ruta para cada archivo.

B. Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?

RTA: Todo empieza en el cliente móvil, cuando el usuario toca o mueve el dedo sobre la pantalla. En ese momento se activa el evento touchMoved() en el código de p5.js, que toma las coordenadas del toque (mouseX, mouseY) y las envía al servidor usando socket.emit('message', data).
El servidor, que está "escuchando" esos mensajes, los recibe con socket.on('message', (data) => {...}). En ese punto, el servidor no los guarda ni los procesa mucho: simplemente los retransmite a los demás clientes conectados, pero sin incluir al que los envió.
Para eso se usa socket.broadcast.emit('message', data), porque socket.emit solo respondería al cliente que mandó el mensaje, y io.emit lo enviaría a todos, incluyendo al emisor. En este caso queremos que los datos del toque solo se reflejen en el computador (desktop) y no en el celular, por eso broadcast es la opción ideal.
Finalmente, el cliente de escritorio recibe esos datos con su propio socket.on('message', …) y los usa para mover el círculo o actualizar la visualización en tiempo real.

C. Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?

RTA: En ese caso, ambos computadores de escritorio recibirían el mensaje, pero el celular no. Esto pasa porque el servidor usa socket.broadcast.emit, lo que significa que reenvía los datos del toque a todos los clientes conectados excepto al que los envió (el celular).
Entonces, los dos escritorios verían moverse el círculo al mismo tiempo, ya que los dos están escuchando los mensajes del servidor. Es una forma de sincronizar varias visualizaciones sin duplicar la información en el cliente que origina los datos.

D. ¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?

RTA: Los mensajes console.log me resultaron muy útiles porque permiten ver en tiempo real lo que está pasando en el servidor. Muestran cuándo un cliente se conecta o se desconecta, y también los datos que llegan desde el celular cuando se hace un toque o movimiento. Esto ayuda mucho a entender el flujo completo de comunicación y a detectar si todo está funcionando bien.
En general, me pareció interesante porque es como tener una “ventana” al interior del servidor: se puede ver cómo se comunican los dispositivos y confirmar que los mensajes viajan correctamente. Además, facilita muchísimo el proceso de depuración cuando algo no sale como se espera.


# ACTIVIDAD 04

Enunciado:

Ahora analizaremos el código que corre en los navegadores: el cliente móvil que captura el toque (mobile/sketch.js) y el cliente de escritorio que recibe la información y dibuja (desktop/sketch.js). Veremos cómo usan Socket.IO para comunicarse con el servidor.

**REPORTE DE BITÁCORA ACTIVIDAD 04:**

Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema.

RTA:

<img width="1000" height="535" alt="Captura de pantalla 2025-10-17 022211" src="https://github.com/user-attachments/assets/14e5ec44-e6e6-43d2-b55b-c79dc9b6e5a3" />


# ACTIVIDAD 05 (APPLY)

1. Diseña una aplicación interactiva que use el touch del móvil para controlar una visuales de tema musical de tu elección. Las visuales correrán en una aplicación de escritorio (desktop). Recuerda que ambas aplicaciones las construirás usando p5.js y utilizando el servidor Node.js como puente.

**IDEA DE DISEÑO:**

- Parte automatizada (del desktop): Quiero que la visual de la aplicación sean unas partículas de color rojo que van a tener de fondo la canción de scorpions "Rock You Like A Hurricane" y que, cuando el volumen de la canción suba, las partículas aumenten su velocidad y que cuando el volumen de la canción baje, estas la disminuyan.

- Parte Interactiva (del mobile): Por otro lado, quiero que la interacción que haya cuando se toca el táctil del teléfono sea que cuando se toque cierta parte de la pantalla, las coordenadas las partículas se acumulen donde se registraron las mismas y que cuando se deje de tocar la pantalla, que las partículas se dispersen para seguir con su comportamiento nuevamente.

3. Implementa tu diseño. Puedes usar IA generativa para ayudarte a escribir el código, pero primero debes hacer el diseño de lo que quieres.
   
4. Incluye todos los códigos (servidor y clientes) en tu bitácora.

Sketch Server:

```js
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');

const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3000;

app.use(express.static('public'));

io.on('connection', (socket) => {
    console.log('New client connected');
    socket.on('message', (message) => {
        console.log('Received message =>', message);
        socket.broadcast.emit('message', message);
    });

    socket.on('disconnect', () => {
        console.log('Client disconnected');
    });
});

server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
});
```


Sketch Desktop:

```js
// sketch.js (Visualización Desktop)

let socket;
let song; 
let amplitude; 
let particles = [];
const numParticles = 150; 
const particleSize = 8;   
const maxBaseSpeed = 0.5; 

// --- NUEVAS VARIABLES DE CONTROL ---
// Modos: 'AUDIO' (normal), 'CONCENTRATE', 'DISPERSE'
let visualMode = 'AUDIO'; 
let targetX = 0; // Posición X objetivo (normalizada)
let targetY = 0; // Posición Y objetivo (normalizada)

// Clase para definir una sola estrella/partícula
class Star {
    constructor() {
        this.x = random(width);
        this.y = random(height);
        this.vx = random(-1, 1);
        this.vy = random(-1, 1);
    }

    // Método para calcular el movimiento
    update(ampLevel) {
        if (visualMode === 'AUDIO') {
            // Modo Normal: Movimiento basado en el volumen de la música
            let speedMultiplier = map(ampLevel, 0, 1, 1, 15); 
            this.x += this.vx * maxBaseSpeed * speedMultiplier;
            this.y += this.vy * maxBaseSpeed * speedMultiplier;
        } else if (visualMode === 'CONCENTRATE') {
            // Modo Concentración: Se mueve hacia el punto objetivo (targetX, targetY)
            let tx = targetX * width;
            let ty = targetY * height;
            
            // Vector de movimiento hacia el objetivo
            let dirX = tx - this.x;
            let dirY = ty - this.y;
            
            // Mueve el 10% de la distancia restante en cada frame (hace un movimiento suave)
            this.x += dirX * 0.1; 
            this.y += dirY * 0.1;
            
        } else if (visualMode === 'DISPERSE') {
            // Modo Dispersión: Dispara la partícula con un vector de velocidad aleatorio
            // La velocidad se reasigna una sola vez al entrar en este modo
            this.x += this.vx * 15; // Velocidad de dispersión alta
            this.y += this.vy * 15;
            
            // Transición a AUDIO después de la dispersión (reestablece la velocidad normal)
            if (this.x < 0 || this.x > width || this.y < 0 || this.y > height) {
                // Si sale de la pantalla, se reubica aleatoriamente y vuelve a modo AUDIO
                this.x = random(width);
                this.y = random(height);
                visualMode = 'AUDIO'; // Vuelve al modo normal si una partícula sale
            }
        }

        // Si la estrella sale de la pantalla en modo AUDIO, la reposicionamos
        if (visualMode === 'AUDIO') {
            if (this.x < 0) this.x = width;
            if (this.x > width) this.x = 0;
            if (this.y < 0) this.y = height;
            if (this.y > height) this.y = 0;
        }
    }

    // Método para dibujar la estrella
    display(ampLevel) {
        noStroke();
        
        let redValue = map(ampLevel, 0, 1, 150, 255); 
        let alphaValue = map(ampLevel, 0, 1, 150, 255);
        
        fill(redValue, 0, 0, alphaValue); 
        
        ellipse(this.x, this.y, particleSize, particleSize);
    }
}

function preload() {
    song = loadSound("/assets/rock_you_like_a_hurricane.mp3");
}

function setup() {
    createCanvas(windowWidth, windowHeight);
    background(0);
    
    amplitude = new p5.Amplitude(); 

    // Inicializar partículas/estrellas
    for (let i = 0; i < numParticles; i++) {
        particles.push(new Star());
    }

    // Configuración de Socket.io
    socket = io(); 
    socket.on('connect', () => { console.log('Connected to server'); });
    
    // --- MANEJO DE MENSAJES DEL CELULAR ---
    socket.on('message', (data) => {
        console.log(`Received message:`, data);
        if (data.type === 'start') {
            // Tocar: Cambia a modo CONCENTRATE y guarda la posición
            visualMode = 'CONCENTRATE';
            targetX = data.x; // Coordenadas normalizadas 0-1
            targetY = data.y;
        } else if (data.type === 'end') {
            // Soltar: Cambia a modo DISPERSE y reasigna vectores de velocidad
            visualMode = 'DISPERSE';
            particles.forEach(p => {
                // Le da una velocidad aleatoria muy alta para la dispersión
                p.vx = random(-1, 1); 
                p.vy = random(-1, 1);
            });
        }
    });    
    
    socket.on('disconnect', () => { console.log('Disconnected from server'); });
    socket.on('connect_error', (error) => { console.error('Socket.IO error:', error); });
}

function draw() {
    background(0, 30); 

    let level = amplitude.getLevel();

    for (let i = 0; i < particles.length; i++) {
        particles[i].update(level);     
        particles[i].display(level);    
    }
}

function mousePressed() {
    // Lógica para iniciar el audio (requerida por navegadores)
    let startMessage = document.getElementById('start-message');
    if (startMessage) {
        startMessage.style.display = 'none';
    }
    
    if (song && !song.isPlaying()) {
        song.loop(); 
        amplitude.setInput(song); 
    }
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```


Sketch Mobile:

```js
// sketch.js (Celular)

let socket;
// Ya no necesitamos lastTouchX/Y ni threshold si solo enviamos Start/End
const port = 3000;

function setup() {
    // Canvas que ocupa toda la pantalla del celular
    createCanvas(windowWidth, windowHeight); 
    background(0); // Fondo negro para el controlador
    socket = io(); 

    socket.on('connect', () => {
        console.log('Connected to server');
    });

    socket.on('disconnect', () => {
        console.log('Disconnected from server');
    });

    socket.on('connect_error', (error) => {
        console.error('Socket.IO error:', error);
    });
}

function draw() {
    background(0);
    fill(255, 255, 255);
    textAlign(CENTER, CENTER);
    textSize(24);
    text('Toca para concentrar estrellas', width / 2, height / 2);

    // Feedback visual al tocar
    if (touches.length > 0) {
        fill(255, 0, 0, 150);
        noStroke();
        ellipse(touches[0].x, touches[0].y, 60, 60);
    }
}

function touchStarted() {
    if (socket && socket.connected && touches.length > 0) {
        // Enviar coordenadas normalizadas (0 a 1) y tipo 'start'
        let touchData = {
            type: 'start',
            x: touches[0].x / width, // Normalizado
            y: touches[0].y / height // Normalizado
        };
        socket.emit('message', touchData);
        console.log('Touch Start Sent:', touchData);
    }
    return false; // Previene el desplazamiento de la página
}

function touchEnded() {
    if (socket && socket.connected) {
        // Enviar tipo 'end' para dispersar las partículas
        let touchData = {
            type: 'end'
        };
        socket.emit('message', touchData);
        console.log('Touch End Sent');
    }
    return false; // Previene el desplazamiento de la página
}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}
```


Index Desktop:

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Visuales de Amsterdam (Desktop)</title>

    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/addons/p5.sound.min.js"></script>
    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    <script src="sketch.js"></script>

    <style>
        /* Estilos básicos para eliminar márgenes del navegador */
        body {
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #000; /* Fondo oscuro, ideal para visuales */
            overflow: hidden; /* Evita barras de desplazamiento */
            color: white; /* Para el mensaje de clic */
            font-family: Arial, sans-serif;
            flex-direction: column;
        }

        /* Estilo para el mensaje de inicio */
        #start-message {
            position: absolute; /* Para que quede encima del canvas si ya se ha creado */
            z-index: 100;
            padding: 10px;
            background-color: rgba(0, 0, 0, 0.7);
            border-radius: 5px;
            cursor: pointer;
            text-align: center;
            /* Esto asegura que el mensaje esté visible y centrado */
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    </style>
</head>
<body>
    <div id="start-message">
        ¡Haz clic o toca en cualquier lugar para empezar la música y la visual! 🎶
    </div>

    <script>
        // **Código para quitar el texto al hacer clic**
        document.getElementById('start-message').addEventListener('click', function() {
            // Establece el estilo 'display' en 'none' para ocultar completamente el elemento
            this.style.display = 'none';
        });

        // Asegurarse de que al hacer clic en el canvas también funcione si el usuario no hace clic en el div exacto
        function mousePressed() {
            let startMessage = document.getElementById('start-message');
            if (startMessage) {
                // Si el mensaje sigue visible y se hace clic en el canvas, lo oculta
                startMessage.style.display = 'none';
            }
            
            // Lógica original de p5.js para iniciar la canción
            if (song && !song.isPlaying()) {
                song.loop();
                console.log("Canción iniciada por interacción del usuario.");
            }
        }
    </script>
</body>
</html>
```


Index Mobile

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    <script src="sketch.js"></script>
    <title>Mobile p5.js Application</title>
</head>
<body></body>
</html>
```

[Video Demostrando La App](https://youtu.be/7jlIcNDjCjQ)


# AUTOEVALUACIÓN:

Siento que mi nota en esta unidad debería ser un 5.0, no solo por el hecho de que completé todas las actividades (desde las de investigación y comprensión de conceptos hasta las de diseño y creación) sino porque siento que aprendí bastante sobre el uso de los Dev Tunnels y cómo su sistema de funcionamiento puede permitir realizar tantas acciones de interacción entre dos o más dispositivos sin la necesidad de estar conectados manualmente, solo con la necesidad de abrir un canal via código y copiar un link en los dispositivos que se deseen conectar. Siento que aunque en unidades anteriores he tenido algunos altibajos, en esta unidad quedé muy satisfecho por mi trabajo de profundización y comprensión, lo cual me ayudó a disfrutarla y entender como funcionan muchas de las tecnologías interactivas que existen hoy en día.


Actividad 01: Completada la apertura del canal de DevTunnels que permitió conectar los dispositivos posteriormente.

ACTIVIDAD 02: Comprensión de los conceptos escenciales para entender el funcionamiento y para qué sirve cada uno. (

ACTIVIDAD 03: Se comprendió por qué el método usado en esta unidad es más eficiente y menos tedioso que el que se usó en la unidad anterior, permitiendo conectar dispositivos sin tenerlos conectados a la misma red de wifi y sin usar la IP.

ACTIVIDAD 04: Diagrama completado y grafica correctamente el proceso que realiza Dev Tunnels para enviar los datos desde el teléfono al pc.

ACTIVIDAD 05 (APPLY): Actividad Final Funcional

Nota Final Propuesta: 5.0
