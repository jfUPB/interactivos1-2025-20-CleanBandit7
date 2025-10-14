
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

**SOLUCIÓN ACTIVIDAD 01:**

1. Por qué en el número de puerto se tiene que seleccionar 3000?

RTA: Para comprender esto, primero se tiene que recalcar que en este caso el puerto es un tipo de "canal" que permite que el dispositivo local reciba datos de internet, por ejemplo cuando se utiliza http, el número de puerto sería 80, cuando se usa https es el puerto 443. Como en este caso, en el archivo server.js se define que el puerto a utilizar es el 3000 ya que este es el número de puerto de Node.js, al seleccionarlo, cuando se abre el link de Dev Tunnels en internet, tanto en el pc como en el teléfono, lo que se está haciendo es "decirle" a VS code que cree un túnel o una vía desde internet hasta mi puerto 3000 local que hace que cuando en el teléfono se abra el link se reenvíe directamente al localhost:3000 del pc  los datos de la pantalla touch del mismo y estos se vean reflejados en la pantalla del pc.

En esta sección del código de server.js se ve donde se determina que el puerto de conexión para recibir una rta por parte del pc será el 3000:

```js
server.listen(3000, () => {
  console.log("Server is listening on http://localhost:3000");
});
```

2. ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?

RTA: 

- La URL que obtuve con Dev Tunnels fue https://wkszwzmd-3000.use2.devtunnels.ms/

- El uso de una URL generada por herramientas como Dev Tunnels es necesario porque localhost es una dirección interna que solo existe dentro del propio computador. Cuando se escribe "http://localhost:3000", el sistema operativo entiende que la conexión debe hacerse al puerto 3000 del mismo dispositivo, no desde otro equipo.

Por esta razón, si intento acceder desde mi celular usando esa dirección, el navegador del celular buscará el puerto 3000 en el mismo teléfono, donde no hay ningún servidor corriendo, lo que hace imposible la conexión.

La URL del túnel (https://wkszwzmd-3000.use2.devtunnels.ms/) actúa como un puente entre Internet y mi servidor local. Es decir, crea una dirección pública temporal que redirige el tráfico hacia el puerto 3000 de mi computador, permitiendo que otros dispositivos, como el teléfono, se conecten y envíen datos al servidor.

Aunque teóricamente podría usarse la IP local del computador (por ejemplo, http://192.168.1.5:3000), esto solo funcionaría si ambos dispositivos están en la misma red Wi-Fi y si el firewall permite ese tipo de conexiones, lo cual no siempre es seguro ni confiable. Por eso, el túnel se convierte en la opción más práctica y estable para realizar pruebas entre el servidor local y dispositivos externos.

3.  Vamos con toda
