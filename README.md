# Instalación y Configuración de Mosquitto MQTT en Raspberry Pi con Publisher ESP32

##  Descripción
Este proyecto demuestra la implementación de una arquitectura IoT utilizando el protocolo MQTT. Se configuró una Raspberry Pi como servidor central (Broker) y una ESP32 como dispositivo periférico (Publisher) para el envío de telemetría.

---

##  Requisitos e Infraestructura
| Componente | Detalle |
| :--- | :--- |
| **Broker** | Raspberry Pi (Debian Bullseye/Bookworm) |
| **Publisher** | ESP32 (NodeMCU) |
| **Protocolo** | MQTT v3.1.1 |
| **Hostname del Broker** | `eiot6cm3.local` |


---

##  Configuración del Sistema

### 1. Servidor (Raspberry Pi)
### 1. Instalación del Broker (Raspberry Pi)
Para preparar el servidor MQTT, se ejecutaron los siguientes comandos en la terminal de la Raspberry Pi:

* **Actualización del sistema:**
  `sudo apt update && sudo apt upgrade -y`
* **Instalación de Mosquitto y clientes:**
  `sudo apt install -y mosquitto mosquitto-clients`
* **Configuración de persistencia (inicio automático):**
  `sudo systemctl enable mosquitto`

### 2. Nodo Embebido (ESP32)
El código utiliza la librería `PubSubClient`. La lógica principal incluye:
- Conexión persistente a la red WiFi.
- Generación de un `ClientID` único para evitar colisiones.
- Publicación de datos en el tópico `escom/iot/equipo/datos` cada 5 segundos.

---

##  Evidencias de Funcionamiento

### Prueba de Mensajería Local
Prueba inicial utilizando comandos de consola en la Raspberry Pi para verificar que el broker acepta mensajes localmente.
![Prueba Local](evidencia/Publisher%20y%20Subscriber.png)

### Integración ESP32 -> Raspberry Pi
Monitorización de los mensajes recibidos en la Raspberry Pi enviados desde el microcontrolador ESP32 en tiempo real.
![Monitor Serie y Terminal](evidencia/image.png)

### Acceso Remoto
Conexión exitosa vía SSH al broker `eiot6cm3.local`.
![Acceso SSH](evidencia/Configuracion%20de%20Rasp%20en%20SSH.png)
---

##  Autor
* **Sanchez De Jesus Arlet (Arlet-S)** 