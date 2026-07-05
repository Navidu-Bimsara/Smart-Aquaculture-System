# Smart-Aquaculture-System
IoT-based fault-tolerant aquarium management system with custom PCB isolation, Firebase telemetry, and automated mechanical water exchange.

# IoT-Based Water Quality Monitoring and Control System for Aquaculture

An automated, fault-tolerant smart aquarium management system driven by an ESP32 dual-core microcontroller. This project continuously monitors critical water parameters and autonomously performs corrective water exchange cycles without requiring human intervention.

## 🎥 Video Demonstration
*(Drag and drop your .mp4 video file here. This demonstration showcases the manual override from the mobile app, the immediate pump activation, and the programmed safety interlock delay before refilling.)*

## 🚀 System Architecture & Key Features
* **Custom Hardware Isolation & EMI Mitigation:** A custom-designed PCB (KiCad 9.0) physically separates 3.3V sensor logic traces from high-current 12V actuator lines. It utilizes an onboard buck converter and a 5V dual-channel opto-isolated relay to prevent electromagnetic interference and hardware failure.
* **Real-Time Telemetry & Signal Processing:** Integrates a waterproof DS18B20 temperature probe, an analog pH sensor, and an MD0591 turbidity sensor. Implements a 20x oversampling digital smoothing algorithm to ensure high signal accuracy and filter out false-positive hazard spikes caused by water turbulence.
* **Automated Mechanical Remediation:** A non-blocking finite state machine (FSM) evaluates water parameters. If safety thresholds are breached, the system autonomously executes a mechanically interlocked water exchange sequence utilizing a 12V brushless DC drain pump and a 12V refill solenoid valve.
* **Redundant Alert Architecture:** To prevent single-point network failure, the ESP32 independently executes secure HTTP requests to dispatch hazard warnings via the Telegram API and Gmail, ensuring delivery even if the mobile application is offline.
* **Live Dashboard & Remote Override:** A custom Thunkable mobile application synced with Google Firebase provides a low-latency telemetry dashboard and manual override capabilities for remote pump actuation.

## 🛠️ Hardware Bill of Materials (BOM)
| Component | Function | Estimated Cost (LKR) |
| :--- | :--- | :--- |
| **ESP32 Dual-Core** | Main Microcontroller | 1,800 |
| **DS18B20** | Digital Temperature Probe (Waterproof) | 800 |
| **Analog pH Sensor V1.1** | Water pH monitoring | 5,500 |
| **MD0591** | Turbidity Sensor | 2,500 |
| **5V Dual-Channel Relay** | Opto-isolated high-power switching | 600 |
| **12V AD20P Pump** | Brushless DC Drain Actuator | 1,200 |
| **12V Solenoid Valve** | Clean Water Refill Actuator | 1,800 |
| **Custom PCB** | Routing, Buck Converter & SMD Components | 3,500 |
| **Misc.** | 12V 2A Power Adapter, Enclosure, PVC, Netting | 2,200 |
| | **Total System Cost:** | **~19,900** |


## 💻 Software Stack
* **Firmware:** C++ (ESP32 / Arduino Framework)
* **Backend:** Google Firebase Realtime Database
* **Frontend:** Thunkable Cross-Platform Mobile App
* **PCB EDA:** KiCad 9.0

## 📁 Repository Structure
* `/Firmware` - Source code for the ESP32 microcontroller and dependency list.
* * `/Mobile-App` - Thunkable block logic screenshots and JavaScript implementation details.


## 📜 License
This project is licensed under the MIT License - see the `LICENSE` file for details.
