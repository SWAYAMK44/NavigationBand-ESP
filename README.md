# Navigator Band — Wearable Assistive System

![PCB Front](images/Front-3d.png)
*Top view of the assembled PCB showing ESP32-S3 module and sensor placement*

A compact, wrist-worn assistive device designed to provide real-time obstacle awareness through haptic and audio feedback — without relying on a smartphone, internet, or external infrastructure.

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


The design is divided into four major functional blocks:

### 🔌 Power Block

* USB-C input (5V)
* MCP73831 LiPo charger
* 400mAh LiPo battery
* XC6206 LDO → stable 3.3V rail

### 🧠 MCU Block

* ESP32-S3
* BLE 5.0
* I2C (sensor interface)
* I2S (audio output)

### 📡 Sensor Block

* VL53L1X — Time-of-Flight distance sensor
* ICM-42688 — IMU (orientation + motion)
* VEML7700 — Ambient light sensor
* MAX30205 — Skin temperature sensor

### 🔊 Feedback Block

* DRV2605L — Haptic driver
* Dual LRA motors (directional feedback)
* MAX98357 — I2S audio amplifier
* Speaker output

---

## 🧾 Schematic

![Schematic](images/root-schematic.png)
*Complete system schematic showing power distribution, MCU, sensors, and feedback circuits*

---

## 🧩 PCB Layout

![PCB Placement](images/Placement.png)
*Component placement optimized for compact wearable design and logical block separation*

---

## 🎯 3D Views

### Front View

![3D Front](images/Front-3d.png)
*Front 3D render of the PCB*

### Back View

![3D Back](images/Back-3d.png)
*Back 3D render showing routing and ground plane*

---

## ⚡ Power Design

* Battery voltage range: **3.0V – 4.2V (LiPo)**
* Regulated to **3.3V using XC6206 LDO**
* Designed for low quiescent current operation

Power flow:

```
USB-C (5V) → MCP73831 → LiPo Battery → XC6206 → 3.3V rail
```

---

## 🔁 Working Principle

1. Device boots and checks skin contact using temperature sensor
2. ToF sensor measures distance continuously (~50 Hz)
3. IMU validates wrist orientation
4. Distance is mapped to feedback intensity
5. Output:

   * Haptic vibration patterns
   * Audio cues ("Turn Left", "Stop", etc.)

If the device is removed (temperature drop), the system enters deep sleep to conserve power.

---

## 🧠 Key Design Decisions

* Used **ESP32-S3** to integrate BLE, I2S, and processing in a single chip
* Selected **XC6206 LDO** for ultra-low quiescent current
* Implemented **shared I2C bus** to reduce routing complexity
* Maintained **antenna keepout region** for RF performance
* Chose **DRV2605L** for advanced haptic control without custom PWM

---

## ⚠️ Challenges

* Routing a dense **2-layer PCB within 40 × 36 mm constraints**
* Managing power stability with **battery voltage variation (3.0V–4.2V)**
* Ensuring signal integrity on a **shared I2C bus**
* Optimizing placement for **wearable ergonomics and compactness**

---

## 📐 Design Constraints

* PCB size: **40mm × 36mm**
* Layers: **2-layer design**
* Supply: **LiPo (3.0V – 4.2V)**
* Output: **3.3V regulated rail**

---

## 🧩 PCB Design Highlights

* Full ground plane on bottom layer
* Proper decoupling capacitor placement near ICs
* Clean routing with minimal vias
* Separation of power and signal paths
* ERC & DRC verified (**0 errors, 0 warnings**)

---

## 🛠️ How to Open

1. Install **KiCad (v7 or later)**
2. Clone this repository
3. Open the `.kicad_pro` file
4. Explore schematic and PCB layout

---

## 📦 Repository Contents

* `hardware/` — KiCad schematic & PCB files
* `images/` — renders and diagrams
* `docs/` — project documentation
* `bom/` — bill of materials
* `3D-model/` — 3D assets

---


## 📄 License

This project is licensed under the MIT License.
👉 [View License](LICENSE)

---

## 👨‍💻 Author

**Swayam Kotecha**
Electronics & Communication Engineering
Electronic Systems Packaging Project

---

## Acknowledement

I would like to express my sincere gratitude to my college, International Institute of Information Technology (IIIT-B), for providing the resources and support to complete this project.

I am especially grateful to my professor, Dr. Kurian Polachan, for their invaluable guidance, encouragement, and expertise throughout the development of this work.

---

## 📌 Note

This project demonstrates PCB-level system integration, power management, and embedded hardware design for wearable assistive technology.
