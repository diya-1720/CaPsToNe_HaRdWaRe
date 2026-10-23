# CaPsToNe_HaRdWaRe - ESP32 Smart Health Monitoring System

An IoT-based patient vital signs and health monitoring system built using the **ESP32 microcontroller**. It measures heart rate (BPM), blood oxygen saturation (SpO2), body temperature, and physical motion in real time, displays live metrics on an SSD1306 OLED screen, and triggers an alarm when health anomalies (such as resting tachycardia) are detected.

---

## 📌 Features

- **Heart Rate & Pulse Oximetry (SpO2)**: Measured via the **MAX30100** optical pulse oximeter sensor.
- **Body Temperature**: Continuous analog reading via the **LM35** temperature sensor.
- **Motion & Activity Tracking**: Real-time 3-axis acceleration tracking with **MPU6050** to distinguish resting states from active movement.
- **Intelligent Anomaly Detection**:
  - Detects resting tachycardia (High BPM > 105 when resting/not moving and valid SpO2 > 80%).
  - Sounds a buzzer alert to notify of potential abnormalities.
- **OLED Dashboard**: Live status display on a 128x64 I2C SSD1306 screen showing:
  - BPM Box & Pulse heart-beat indicator
  - SpO2 Level & Sensor lock indicator
  - Temperature (°C)
  - Motion / Acceleration magnitude (g)
  - System status (OK vs ALT)

---

## 🛠️ Hardware Requirements & Pinout

| Component | Pin / Interface | ESP32 Pin | Description |
| :--- | :--- | :--- | :--- |
| **I2C Bus (Shared)** | SDA | **GPIO 18** | Data line for MAX30100, MPU6050 & OLED |
| **I2C Bus (Shared)** | SCL | **GPIO 19** | Clock line for MAX30100, MPU6050 & OLED |
| **LM35 Temperature Sensor** | VOUT (Analog) | **GPIO 34** | ADC1 input (12-bit resolution) |
| **Buzzer** | Signal / Positive | **GPIO 25** | Digital output for alarm alert |
| **Power Supply** | VCC / GND | **3.3V / 5V & GND** | Standard power rails |

---

## 📦 Required Arduino Libraries

Ensure the following libraries are installed via Arduino IDE Library Manager:
1. **Adafruit SSD1306** (by Adafruit)
2. **Adafruit GFX Library** (by Adafruit)
3. **MAX30100lib** (by OXullo Intervent / PulseOximeter)
4. **Wire** (built-in ESP32 core)

---

## 🚀 Getting Started

1. Clone this repository:
   `ash
   git clone https://github.com/diya-1720/CaPsToNe_HaRdWaRe.git
   `
2. Open esp32_health_monitor/esp32_health_monitor.ino in Arduino IDE.
3. Select your ESP32 board (e.g., **ESP32 Dev Module**) from **Tools > Board**.
4. Set upload speed and select the corresponding COM port.
5. Compile and upload the sketch to your ESP32.
6. Open Serial Monitor at **115200 baud** to view real-time diagnostics.

---

## 📂 Project Structure

`	ext
CaPsToNe_HaRdWaRe/
├── README.md
├── .gitignore
└── esp32_health_monitor/
    └── esp32_health_monitor.ino
`
