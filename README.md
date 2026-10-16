# Sistema de Monitoreo de Panel Solar
## Descripción general
El <a href="https://github.com/ranizouaoui/solar-panel-monitoring/">Sistema de Monitoreo de Panel Solar</a> está diseñado para proporcionar supervisión y análisis en tiempo real del rendimiento de los paneles solares. Este proyecto integra componentes tanto de hardware como de software. El hardware consta de un microcontrolador <a href="https://www.espressif.com/en/products/socs/esp32">ESP32</a> conectado a varios sensores que miden parámetros clave del panel solar, tales como voltaje, corriente, temperatura e intensidad de luz. Los datos recopilados se envían a un <a href="https://www.hivemq.com/">servidor MQTT (HiveMQ)</a>. En la parte de software, el servidor backend, desarrollado con <a href="https://expressjs.com/">Express.js</a>, recupera los datos del broker MQTT y los envía a la aplicación frontend desarrollada con <a href="https://vuejs.org/">Vue.js</a> para su visualización y monitoreo.

<div align="center"> 
<img src="https://github.com/ranizouaoui/solar-panel-monitoring/blob/main/pictures/home-interface.png" alt="" />
 </div>
 
## Mapa del proyecto
<div align="center"> 
<img src="https://github.com/ranizouaoui/solar-panel-monitoring/blob/main/pictures/pv-arch.gif" alt="" />
 </div>
<strong> Nota:</strong> La placa <a href="https://www.espressif.com/en/products/socs/esp32" >ESP32 </a>comienza a enviar datos si está bien configurada (desde la interfaz de configuración).

## Configuración manual
### Configuración de la placa ESP32
Sigue los siguientes pasos:

1- Descarga e instala <a href="https://www.arduino.cc/">Arduino</a>.<br/>
2- Instala el <a href="https://randomnerdtutorials.com/install-esp32-filesystem-uploader-arduino-ide/">cargador del sistema de archivos ESP32 en Arduino IDE</a>.<br/>
3- Edita el <a href="https://github.com/ranizouaoui/Solar-Panel-Monitoring-System/blob/main/iot/code_arduino_final/main_code/main_code.ino">código fuente</a> (actualiza el broker y la configuración de Firebase).<br/>
4- Instala las librerías utilizadas en el código de Arduino.<br/>
5- Sube la interfaz de configuración en SPIFFS a la placa ESP32 (ve a <strong> Herramientas > ESP32 Data Sketch Upload</strong> y espera a que se carguen los archivos).<br/>
6- Sube el <a href="https://github.com/ranizouaoui/Solar-Panel-Monitoring-System/blob/main/iot/code_arduino_final/main_code/main_code.ino">código fuente</a>. <br/>
 
<blockquote> <p dir="auto">Necesitarás crear una cuenta en Firebase y HiveMQ para poder modificar el código de Arduino.</p></blockquote>

7- Conéctate al punto de acceso <strong>SolPanelMonitor</strong>. <br/>
8- Configura la tarjeta electrónica desde la interfaz de configuración (http://192.168.4.1/). <br/>
 
 <blockquote> <p dir="auto">Si la tarjeta electrónica está bien configurada, serás redirigido a esta interfaz.</p></blockquote>
   <div align="center"> 
 <img src="https://github.com/ranizouaoui/ESP32-Based-IoT-Tracking-System/blob/main/pictures/configuration1.png" style="height: 400px;" alt="" />
 </div>
9- Realiza el cableado entre los sensores y el panel fotovoltaico (PV) como se muestra <a href="https://github.com/ranizouaoui/solar-panel-monitoring/blob/main/pictures/wiring.png">aquí</a>.

## Configuración de la aplicación web

<blockquote>
<p dir="auto">Asegúrate de que Docker esté instalado.</p>
</blockquote>

<blockquote> <p dir="auto">Debes actualizar el archivo de la API con tus configuraciones en <strong> web>frontend>src>api </strong> y <strong>web>backend>src>api</strong>.</p></blockquote>
<p dir="auto">Inicia los contenedores:</p>

```bash
docker-compose up -d --build
