# Capacitor_timer_reader-ESP32
# ESP32 Electronics Experiments  

This repository contains simple Arduino IDE codes for the *ESP32*, used to test and observe electronic components in lab experiments.  

## 📌 Projects Included
1. *Capacitor Timer Reader*  
2. *Back EMF Detector*  

---

## 1️⃣ Capacitor Timer Reader  

### 🔹 Description
This project reads the voltage across a capacitor connected to an ESP32 analog pin.  
It helps visualize the *charging and discharging behavior* of capacitors in real-time.

### 🔹 Circuit
- Capacitor connected in series with a resistor (RC circuit).  
- The capacitor’s voltage is read from *GPIO 32 (ADC pin)*.  
- Ensure voltage does not exceed *3.3V, otherwise use a **voltage divider*.  

### 🔹 Code
```cpp
// Capacitor Timer Reader on ESP32
const int capPin = 32; // ADC1_4 pin on ESP32

void setup() {
  Serial.begin(115200);
}

void loop() {
  int rawValue = analogRead(capPin);        // 0 - 4095
  float voltage = (rawValue / 4095.0) * 3.3; // Convert to volts (assuming 3.3V reference)

  Serial.print("Capacitor Voltage Reading (raw): ");
  Serial.print(rawValue);
  Serial.print(" | Voltage: ");
  Serial.print(voltage, 2); // print with 2 decimal places
  Serial.println(" V");

  delay(200);
}
