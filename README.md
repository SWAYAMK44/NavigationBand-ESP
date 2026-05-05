# NavigationBand-ESP# Navigator Band — Wearable Assistive System for the Visually Impaired

A compact, wrist-worn assistive device designed to provide real-time obstacle awareness through haptic and audio feedback — without relying on a smartphone, internet, or external infrastructure.

Developed as part of an Electronic Systems Packaging project, this system integrates sensing, processing, power management, and feedback on a single 2-layer PCB.

---

## 🧠 Overview

Navigator Band is a fully self-contained wearable built around the ESP32-S3. It continuously monitors the environment using multiple sensors and translates spatial information into intuitive vibration patterns and audio cues.

The system is designed to be:

* **Discreet** — wristband form factor
* **Low-power** — optimized for battery operation
* **Real-time** — no cloud or phone dependency
* **Accessible** — no visual interface required

---

## ⚙️ System Architecture

The design is divided into four major blocks:

### 🔌 Power Block

* USB-C input (5V)
* MCP73831 LiPo charging IC
* 400mAh LiPo battery
* XC6206 LDO regulator → stable 3.3V rail

### 🧠 MCU Block

* ESP32-S3
* BLE 5.0 capability
* I2C for sensors
* I2S for digital audio output

### 📡 Sensor Block

All sensors share a common I2C bus:

* VL53L1X — Time-of-Flight distance sensing
* ICM-42688 — IMU for orientation correction
* VEML7700 — Ambient light sensing
* MAX30205 — Skin temperature sensing

### 🔊 Feedback Block

* DRV2605L — haptic driver for LRA motors
* Dual vibration motors (directional feedback)
* MAX98357 — I2S audio amplifier
* Speaker for voice cues

---

## 🔁 Working Principle

1. Device boots and checks skin contact using temperature sensor
2. ToF sensor continuously measures distance (~50 Hz)
3. IMU filters readings based on wrist orientation
4. Obstacle distance is mapped to feedback intensity
5. Output:

   * Haptic patterns (proximity-based)
   * Audio cues ("Turn Left", "Stop", etc.)

If the device is removed (temperature drop), the system enters deep sleep to conserve power.

---

## ⚡ Power Design

* Battery voltage varies from **3.0V to 4.2V**
* Regulated to a stable **3.3V rail using an LDO**
* Designed for low quiescent current operation

---

## 🧩 PCB Design Highlights

* 2-layer PCB (40mm × 36mm)
* Full ground plane on bottom layer
* Compact component placement optimized for wearable form factor
* All decoupling capacitors placed close to IC supply pins
* Clean routing with dedicated power and signal paths
* ERC & DRC verified (zero errors)

---

## 📦 Repository Contents

* KiCad schematic files
* PCB layout files
* 3D board render
* Gerber files (manufacturing-ready)
* Bill of Materials (BOM)
* Project presentation

---

## 🎯 Design Goals

* Minimize system size while maintaining functionality
* Ensure low power consumption for wearable use
* Maintain signal integrity on a 2-layer PCB
* Provide intuitive, non-visual feedback for navigation

---

## 🚧 Future Improvements

* Replace LDO with buck-boost converter for full battery utilization
* Add enclosure design for wearable ergonomics
* Integrate wireless firmware updates via BLE
* Improve motor driver isolation for reduced noise

---

## 👨‍💻 Author

Swayam Kotecha
Electronics & Communication Engineering
Project: Electronic Systems Packaging

---

## 📌 Note

This project is a design-focused implementation demonstrating PCB-level system integration, power management, and embedded hardware architecture.
