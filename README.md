## System Overview
The **TF24 Acquisition & Launch Robot** is a mobile robotics platform designed for ball acquisition and active flywheel launching, controlled remotely via a custom smartphone interface. 

This repository contains the full engineering audit, baseline hardware designs, schematics, PCB layouts, system block diagrams, and post-mortem configuration drift analysis evaluating the deltas between initial multi-rail power design blueprints and physical operational constraints.

---

## 📄 Key Asset & Post-Mortem Analysis
* **Primary Post-Mortem Document:** [📄 Click Here to Read PM_Analysis_Zalix_Razera.pdf](./docs/PM_Analysis_Zalix%20Razera.pdf)
* **Scope:** Configuration drift analysis mapping hardware architecture changes, multi-rail power distribution constraints, and operational lessons learned during physical deployment.

---

## 📐 System Architecture

### Hardware & Power Distribution
- **Main Microcontroller:** ESP32 (Wi-Fi/Bluetooth telemetry & real-time control interface)
- **Power Architecture:** Multi-rail regulation system supplying high-current motor drivers and logic stages
- **Custom PCB Design:** Carrier motherboard designed in KiCad for modular power delivery and signal routing

```mermaid
graph TD
    App[Kodular Control App] -->|Wireless Telemetry| ESP32[ESP32 Controller]
    ESP32 -->|PWM / Gate Control| Launch[Flywheel Launcher Stage]
    ESP32 -->|Motor Control| Drive[Drivetrain Actuators]
    Power[Multi-Rail Power System] -->|V_Logic| ESP32
    Power -->|V_Motor| Launch
    Power -->|V_Motor| Drive
