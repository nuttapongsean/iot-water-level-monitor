# 🌊 IoT Water Level Monitor with ESP8266 & NETPIE

![Project Overview](iot_water_level_monitor_diagram_1773634560264.png)

This project is an IoT-based system designed to monitor water levels in real-time. It uses an **ESP8266** microcontroller and an **HC-SR04 Ultrasonic Sensor** to measure the distance between the sensor and the water surface. The measured levels are then published to the **NETPIE** platform for remote monitoring.

---

## ✨ Features
- **Real-time Monitoring**: Measures water level Every 10 seconds.
- **NETPIE Integration**: Seamless connection to the NETPIE IoT platform.
- **Automatic Reconnection**: Intelligent logic to handle WiFi and NETPIE connection drops.
- **Level Categorization**: Automatically classifies water levels into 4 distinct states.

## 🛠️ Hardware Requirements
- **Microcontroller**: ESP8266 (NodeMCU or similar)
- **Sensor**: HC-SR04 Ultrasonic Sensor
- **Power**: USB Power Supply or Li-ion Battery
- **Connectivity**: WiFi (2.4GHz)

## 📌 Pin Mapping
| Component | ESP8266 Pin | Function |
| :--- | :--- | :--- |
| **HC-SR04 VCC** | 3.3V / 5V | Power |
| **HC-SR04 GND** | GND | Ground |
| **HC-SR04 TRIG** | D1 | Trigger Signal |
| **HC-SR04 ECHO** | D2 | Pulse Input |

---

## ⚙️ Logic & Calibration
The system calculates the distance and categorizes the water level based on the following logic (calibrated for a typical tank depth):

| Distance (cm) | Status Message | Meaning |
| :--- | :--- | :--- |
| < 15 cm | **High Level** | Water is near the sensor (Full) |
| 15 - 29 cm | **Medium Level** | Halfway point |
| 30 - 44 cm | **Low Level** | Water is Getting low |
| ≥ 45 cm | **Normal Level** | Tank is mostly empty / Safe baseline |

---

## 🚀 Getting Started

### 1. Prerequisites
Ensure you have the following libraries installed in your Arduino IDE:
- [ESP8266WiFi](https://github.com/esp8266/Arduino)
- [MicroGear](https://github.com/netpie/microgear-arduino)

### 2. Configuration
Open `main.ino` and update the following credentials:

```cpp
// WiFi Configuration
const char* ssid     = "YOUR_WIFI_SSID";
const char* password = "YOUR_WIFI_PASSWORD";

// NETPIE Configuration
#define APPID   "YOUR_APPID"
#define KEY     "YOUR_KEY"
#define SECRET  "YOUR_SECRET"
```

### 3. Upload
1. Connect your ESP8266 to your computer.
2. Select your board (e.g., NodeMCU 1.0) and COM port in the Arduino IDE.
3. Click **Upload**.
4. Open the Serial Monitor (115200 baud) to view the debug messages.

---

## 📱 Monitoring
You can monitor the status via the NETPIE Freeboard or any MQTT-compatible client by subscribing to the corresponding APPID and ALIAS.

---

## 📝 License
This project is open-source. Feel free to modify and adapt it for your own needs.
