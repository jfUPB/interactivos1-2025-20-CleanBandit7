
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


