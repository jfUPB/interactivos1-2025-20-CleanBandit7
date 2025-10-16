
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

[Demostración del Uso de la Aplicación](https://youtu.be/d-XlG-U2DxQ)

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


