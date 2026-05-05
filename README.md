# Navigator Band — Wearable Assistive System

![3D PCB](images/pcb_3d.png)

A compact, wrist-worn assistive device designed to provide real-time obstacle awareness through haptic and audio feedback — without relying on a smartphone or internet.

---

## 🧠 Overview

Navigator Band is a fully self-contained wearable built around the ESP32-S3. It continuously monitors the environment using multiple sensors and translates spatial information into intuitive vibration patterns and audio cues.

---

## ⚙️ System Architecture

![Block Diagram](images/system_block.png)

The design is divided into four major blocks:

### 🔌 Power Block

* USB-C input (5V)
* MCP73831 LiPo charger
* 400mAh LiPo battery
* XC6206 LDO → 3.3V rail

### 🧠 MCU Block

* ESP32-S3 (BLE + I2C + I2S)

### 📡 Sensor Block

* VL53L1X — ToF
* ICM-42688 — IMU
* VEML7700 — Light
* MAX30205 — Temperature

### 🔊 Feedback Block

* DRV2605L — Haptic driver
* Dual motors
* MAX98357 — Audio amplifier

---

## 🧾 Schematic

![Schematic](images/schematic.png)

Complete system-level schematic showing power, MCU, sensors, and feedback integration.

---

## 🧩 PCB Layout

![PCB Placement](images/pcb_top.png)

* 2-layer PCB (40mm × 36mm)
* Optimized placement for compact wearable design
* Functional block separation (power, MCU, sensors, feedback)

---

## 🎯 3D View

![3D Front](images/pcb_3d.png)

Visual representation of the assembled PCB showing real-world layout and component positioning.

---

## ⚡ Power Design

* Battery: **3.0V – 4.2V (LiPo)**
* Regulated to **3.3V via XC6206**
* Designed for low power wearable operation

---

## 🔁 Working Principle

1. Device boots and checks skin contact
2. ToF sensor measures distance (~50 Hz)
3. IMU validates orientation
4. Distance mapped to feedback
5. Output:

   * Haptic vibration
   * Audio cues

---

## 📦 Repository Contents

* `hardware/` — KiCad files
* `images/` — PCB renders and diagrams
* `docs/` — project documentation
* `bom/` — bill of materials

---

## 🚧 Future Improvements

* Replace LDO with buck-boost converter
* Add enclosure design
* Improve power efficiency
* Add BLE firmware support

---

## 👨‍💻 Author

Swayam Kotecha
Electronics & Communication Engineering

---

## 📌 Note

This project demonstrates PCB-level system integration, power management, and embedded hardware design.
