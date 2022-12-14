# Flow-4
En este repositorio se muestra la actividad 4 con Node Red, el cual consiste en observar en una gráfica, los datos que se mandan a través de MQTT.

## Material necesario
Para poder realizar necesario es necesario tener instalado:
- [Node.js](https://github.com/nodesource/distributions/blob/master/README.md) Usar la versión LTS v16x e instalar los build tools.
- [Node-Red](https://nodered.org/docs/getting-started/local)
- [Ubuntu 20.04](https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64)

## Material de referencia
Para hacer las instalaciones requeridas para este ejercicio se siguieron los pasos de los cursos siguientes:
- [Instalación de Ubuntu 20.04 en VirtualBox Windows](https://edu.codigoiot.com/course/view.php?id=812)
- [Instalación de NodeRed en Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=817)
- [Introducción a NodeRed](https://edu.codigoiot.com/course/view.php?id=278)

## Instrucciones
1. Abrir la terminal y escribir el siguiente comando: **node-red**.
>Nota: Es importante escribir este comando en la terminal ya que si no se hace no se podrá trabajar con Node Red.
2. En el navegador escribir: **localhost:1880**, se abrirá Node Red.
3. Agregar el bloque **mqtt in** y editar el server colocando *local host*. Escribir el nombre del tema el cual es: codigoIoT/Mor/mqtt/flow4.
4. Agregar un bloque **json** y en la sección de *Action* colocar la opción *Always convert to JavaScript Object*.
5. Agregar dos bloques **function** y unirlos a las salida del bloque **json**. El primer bloque se llamará temperatura y contendrá el siguiente código:
>msg.payload = msg.payload.temp;

>msg.topic = "Temperatura";

>return msg;

El segundo bloque se llamará humedad y contendrá el siguiente código:
>msg.payload = msg.payload.hum;

>msg.topic = "Humedad";

>return msg;
6. A la salida de cada uno de los bloques, insertar dos bloques de dashboard de tipo **gauge**. Para configurar cada uno de los bloques **gauge** se debe crear un grupo para casa variable, en este caso, un grupo para temperatura y otro para la humedad. Configurar las unidades y rangos de valores que tendrá el gauge.
7. Para hacer un Histórico que grafique ambos valores en una sola gráfica, se debe insertar un bloque **gauge** y crear un grupo para este gráfico.
8. Abrir la terminal y ejecutar el siguiente comando:
>mosquitto_pub -h localhost -t codigoIoT/Mor/mqtt/flow4 -m '{"ID":"NOMBRE","temp":TEMPERATURA,"hum":HUMEDAD}'
TEMPERATURA y HUMEDAD son valores numéricos.
9. Finalmente, dar click en el botón **Deploy** para que se actualicen los cambios. 

## Resultados
Una vez completados los pasos anteriores se deberá ver abrir el dashboard, como se muestra a continuación:

![Captura de pantalla](Captura_gauge.png)

El flow en Node Red debe verse como el mostrado a continuación:

![Captura de pantalla](Captura_NodeRed.png)

## Evidencias
[Evidencia Flow 4](https://youtu.be/up2s5yH4JKM)

## Créditos
Este ejercicio fue basado en los ejercicios que se encuentran en el repositorio [flow4-NodeRed](https://github.com/hugoescalpelo/flow4-NodeRed-MQTT)

Documentación realizada por [Karen Rosas](https://github.com/KarenRosas49)