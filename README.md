# Low-Cost-DAQ-System-for-Rocket-Testing

### STM32F373-Based Dual-PCB Acquisition System

Hardware project for a modular data acquisition system (DAQ) designed for static fire tests of small rocket engines.  
Built around a precision STM32F373 microcontroller with integrated Sigma-Delta ADCs and analog signal conditioning for both load cell and pressure sensor measurements.

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
* Header for stacked pressure board  
* Debug and power connectors

### Pressure Board

* Current-to-voltage conversion (4–20 mA)  
* TSV911 buffer for ADC interfacing  
* Overvoltage protection  
* Simple analog interface to main board

---

## **Applications**

* Thrust and chamber pressure measurement in hybrid and solid rocket motor tests  
* Real-time data acquisition with graphical interface (LabVIEW)  
* Educational laboratory experiments involving signal conditioning  
* Fault-tolerant analog data logging with overvoltage resilience

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

## **Author**

Nathan Netzel  
Electrical Engineering Student — Londrina State University
