# Low-Cost-DAQ-System-for-Rocket-Testing

### STM32F373-Based Dual-PCB Acquisition System

Hardware project for a modular data acquisition system (DAQ) designed for static fire tests of small rocket engines.  
Built around a precision STM32F373 microcontroller with integrated Sigma-Delta ADCs and analog signal conditioning for both load cell and pressure sensor measurements.

---

## 🔥 Highlights  
- Fully standalone operation (LCD, SD, user button — no PC required)  
- Integrated thrust & pressure acquisition (STM32F373, PGA308)  
- Safe igniter activation with isolated redundant channels  
- Modular design: DAQ, Igniter, and Power Boards  

---

## **Overview**

This system is composed of two stacked PCBs, integrated in a 3D-printed frame:

* **Main DAQ Board**: Handles microcontroller logic, load cell signal conditioning, and serial communication  
* **Pressure Acquisition Board**: Mounted above, adds pressure sensor interface and protection circuitry

Both PCBs work together to safely and accurately acquire thrust and chamber pressure data during motor tests.

---

## **Key Features**

* STM32F373VCT6 microcontroller (16-bit Sigma-Delta ADCs with programmable gain)  
* Load cell signal conditioning using PGA308 programmable gain amplifier  
* Pressure signal acquisition with current-to-voltage conversion and TSV911 buffer  
* RS-232 serial interface (optocoupled) for PC communication via LabVIEW  
* Overvoltage protection for sensor interfaces  
* Modular design for reusability and testing flexibility  
* 3D-printed support structure for mechanical integration

## **Applications**

* Thrust and chamber pressure measurement in hybrid and solid rocket motor tests  
* Real-time data acquisition with graphical interface (LabVIEW)  
* Educational laboratory experiments involving signal conditioning  
* Fault-tolerant analog data logging with overvoltage resilience

---

## 🧭 **Block Diagram (Main DAQ Board)**

![Block Diagram](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/Low_Cost_DAQ_Hardware_Diagram.png)  
*Figure 1: Functional architecture of the main DAQ board, highlighting signal conditioning, communication, and microcontroller connections. Also featured in the [3rd Brazilian Aerospace Congress].*

---

## 🖼️ **Hardware Photos**

| Main DAQ Board (Top View)                                                                      | Main + Pressure Boards Assembled                                                                | Main Board (Bottom View)                                                                             |
| ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| ![DAQ Top](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/Low_Cost_DAQ_Main_Board.png) | ![DAQ Stack](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/Low_Cost_DAQ_Pressure_Board.png) | ![DAQ Bottom](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/Low_Cost_DAQ_Bottom_Board.png)   |

> *Note: The blue pressure board is mounted on the green DAQ main board using a custom 3D-printed support*

---

## **System Architecture Summary**

### Main DAQ Board

* STM32F373VCT6 MCU with internal Sigma-Delta ADCs  
* PGA308 gain amplifier for load cell  
* RS-232 communication via optocoupler  
* Solder Pad for stacked pressure board  
* Debug and power connectors

### Pressure Board

* Current-to-voltage conversion (4–20 mA)  
* TSV911 buffer for ADC interfacing  
* Overvoltage protection  
* Simple analog interface to main board

---

# 🔄 Updated Version (2025)

### STM32F373-Based Integrated DAQ System with Ignition and Power Boards

An updated version of the low-cost data acquisition system has been developed.  
While maintaining the same core architecture (STM32F373, load cell conditioning, and modularity), the new design integrates **pressure acquisition into the main board** and adds multiple new features for usability, safety, and flexibility during rocket motor testing.  

The **main goal** of this updated version was to produce a **robust, fully standalone system**, capable of performing rocket motor tests **without requiring a PC or external serial interface**.  
Now, all critical tasks — data collection, igniter activation, and real-time monitoring — can be carried out directly through the **user button, LCD display, SD card logging, LEDs, and buzzer signals**, providing greater autonomy, safety, and reliability during operations.  

-
---

## **New Features (Main DAQ Board)**

* **Integrated pressure acquisition** (no separate pressure board required)  
* **Isolated USB interface** with Micro-USB connector using ADUM3166BRSZ  
* **SD Card reader** for standalone data logging  
* **2.4” 240x320 TFT LCD with touchscreen (ILI9341, SPI)** for real-time data visualization  
* **Protected serial interface** using SN74LVC2T45DCUT to safeguard SD operations  
* **User interaction & signaling**:  
  * 4 user-programmable external LEDs  
  * 3 dedicated power-status LEDs (+3.3V, +5V RS-232, +5V USB)  
  * User button  
  * Buzzer for audio feedback  
* **Load control connectors** for igniter activation (via secondary board)  
* **Expansion connector** with 14 GPIOs (ADC, DAC, Sigma-Delta, etc.)  
* **Power input protection** with rectifier bridge  
* **Improved PCB layout**: reorganized routing, more didactic silkscreen, and compact design  

---

## 🖼️ **Updated Hardware Photos**

| Main DAQ Board (Top View) | Main DAQ Board (Bottom View) | Assembled with LCD + SD |
|----------------------------|------------------------------|--------------------------|
| ![DAQ Updated Top](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/DAQ_Updated_Top.png) | ![DAQ Updated Bottom](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/DAQ_Updated_Bottom.png) | ![DAQ LCD](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/DAQ_LCD_SD.png) |

---

## ⚡ Igniter Activation Board

The **igniter board** ensures safe activation of rocket motor igniters.  
It operates from a **dedicated 30 V DC power supply** and uses **optical isolation** to decouple control logic from high-current ignition circuits.

**Key Points:**
* Two-channel igniter driver (redundant or independent use)  
* EL817 optocoupler for signal isolation  
* G5LE-14-DC24 relay per channel, driven by BC547 transistor  
* Flyback diodes for coil protection  
* Fail-safe design: both igniter terminals remain shorted to ground when relay is off  
* Output LEDs indicate when a channel is energized (⚠️ load must not be connected when LED is on)  

| Igniter Board (Top View) | Igniter Board (Bottom View) | Installed with DAQ |
|---------------------------|-----------------------------|--------------------|
| ![Igniter Top](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/Igniter_Top.png) | ![Igniter Bottom](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/Igniter_Bottom.png) | ![Igniter Assembled](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/Igniter_Assembled.png) |

---

## 🔌 Power Supply Board

A **dedicated power board** provides regulated DC supply to both the DAQ and Igniter modules.  
Each board is fed by its own transformer, ensuring electrical separation between subsystems.  

**Features:**
* AC input via transformer  
* Rectifier bridge with filtering capacitors  
* Individual modules used for DAQ and Igniter supply  

| Power Board (Top View) | Power Board (Bottom View) | Installed Setup |
|-------------------------|---------------------------|-----------------|
| ![PSU Top](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/PSU_Top.png) | ![PSU Bottom](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/PSU_Bottom.png) | ![PSU Assembled](https://github.com/NathanNetzel/Low-Cost-DAQ-System-for-Rocket-Testing/assets/PSU_Assembled.png) |

---

## **System Summary (Updated)**

* ✅ Main DAQ Board: STM32F373, load cell + pressure acquisition, USB isolation, SD, LCD  
* ✅ Igniter Board: isolated redundant channels, independent 30 V supply, fail-safe relays  
* ✅ Power Supply Board: independent rectified outputs for DAQ and ignition subsystems  

This upgraded system improves **safety**, **usability**, and **autonomy**, while keeping the modular architecture suited for rocket engine test benches.

---


## 📦 **Component Drivers**

All key embedded drivers used in this system are available on GitHub:

* [PGA308 STM32 HAL Driver](https://github.com/NathanNetzel/PGA308-STM32-HAL-Driver) 
* [STM32F373 Peripheral Setup (via STM32CubeMX)]()  

---

## ⚠️ Usage Notice

This repository is for demonstration and academic purposes only.  
No license is currently applied. Please contact the author for collaboration or reuse.

---

## 📚 Publications

- **A Versatile Low-Cost Data Acquisition System for Small Rocket Engine Test Bench**  
  *HardwareX, Elsevier, 2025*.  
  [Link to article (forthcoming, current issue)]()

- **DART – A Low-Cost Data Acquisition System for Small Rocket Motor Testing**  
  *III Brazilian Aerospace Congress (IIICAB)*, Brasília, Brazil, September 22–24, 2025.  
  [Conference Website](https://cab.unb.br/)

---

## **Author**

Nathan Netzel  
Electrical Engineering Student — Londrina State University
