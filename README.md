
# 🌡️ Automated Temperature Control Fan

This project is an **IoT-based smart fan** system that automatically adjusts its speed based on the surrounding temperature using sensors and microcontroller logic. It's designed to improve comfort and energy efficiency.

## 📌 Features

- 🌡️ Temperature sensing using **LM35 sensor**
- 🔁 Fan speed control using **PWM (Pulse Width Modulation)**
- ⚙️ Microcontroller-based logic (e.g., Arduino/ESP32)
- 💡 Energy-efficient & responsive
- 🧪 Real-time monitoring

## 🛠️ Components Used

| Component           | Description                         |
|--------------------|-------------------------------------|
| Microcontroller     | Arduino Uno / ESP32 / NodeMCU       |
| Temperature Sensor | LM35                                 |
| Motor Driver       | L293D / Relay module                 |
| Fan                | 5V/12V DC Fan                        |
| Power Supply       | 5V-12V (as per fan requirement)      |
| Jumper Wires       | For connections                      |
| Breadboard         | For prototyping                      |

## 🔌 Circuit Diagram

LM35 OUT ---> A0 (Arduino/ESP) Motor Driver IN1/IN2 ---> PWM pins (e.g., D9, D10) Fan + ---> Motor Driver OUT


## 📋 Working Principle

1. The LM35 sensor reads the ambient temperature.
2. The microcontroller processes the analog value and converts it into Celsius.
3. Based on temperature thresholds:
   - **Below 25°C**: Fan remains OFF or runs at low speed.
   - **25°C - 30°C**: Fan runs at medium speed.
   - **Above 30°C**: Fan runs at high speed.
4. PWM signal adjusts the fan speed accordingly.

## 🧠 Code Snippet (Arduino Example)

```cpp
const int tempPin = A0;
const int fanPin = 9;

void setup() {
  pinMode(fanPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int reading = analogRead(tempPin);
  float voltage = reading * 5.0 / 1024.0;
  float temperature = voltage * 100; // LM35 gives 10mV/°C

  Serial.print("Temperature: ");
  Serial.println(temperature);

  if (temperature < 25) {
    analogWrite(fanPin, 0);       // Fan OFF
  } else if (temperature < 30) {
    analogWrite(fanPin, 128);     // Medium speed
  } else {
    analogWrite(fanPin, 255);     // High speed
  }

  delay(1000);
}
📈 Future Improvements
Add Bluetooth/WiFi control via app

Connect to IoT platforms (like Blynk, Thingspeak)

Display temperature on an LCD or OLED

Add humidity sensors for dual-parameter control

🎓 Project Info
Project Title: Automated Temperature Control Fan

Domain: Embedded Systems / IoT

Language: C++ (Arduino)

Tools Used: Arduino IDE, Proteus (for simulation), Fritzing

🤝 Credits
Developed by Nageshwari, ECE Student
Internship Project | Miniox Tech Park | 2025

