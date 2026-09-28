<h1 align="center">💧 PLC Automation – Multi-Station Coolant Filling & Hydrostatic Test System</h1>

<p align="center">
  <img src="https://img.shields.io/badge/PLC-Unitronics%20UniLogic-blue" alt="PLC"/>
  <img src="https://img.shields.io/badge/HMI-Integrated%20HMI-green" alt="HMI"/>
  <img src="https://img.shields.io/badge/Control-PID-orange" alt="PID"/>
  <img src="https://img.shields.io/badge/Application-Industrial%20Automation-red" alt="Automation"/>
</p>

<p align="center">
  <b>PLC/HMI-based automated coolant filling and hydrostatic pressure testing system developed using <i>Unitronics UniLogic</i> for multi-station industrial testing.</b>
</p>

---

## 📌 Project Overview

This project focuses on the design and development of an **automated coolant filling and hydrostatic pressure testing system** using a **Unitronics PLC and integrated HMI**.

The system is designed around a **central coolant supply and main pump** capable of supplying multiple independent test cells.

Each test station can perform operations such as:

- **Coolant Filling**
- **Hydrostatic Pressure Testing**

The PLC manages the complete process sequence while the HMI provides operators with real-time system monitoring, test configuration, pressure trending, alarm visualization, and individual cell control.

The project is designed to improve **test repeatability, operator safety, process monitoring, and overall testing efficiency**.

---

## ⚡ System Description

### 🔹 Central Coolant Supply

- Central coolant reservoir / tote
- Main coolant pump
- Common coolant supply to multiple test cells
- Pressure monitoring
- Pump control based on system demand
- Pressure regulation using PID control

### 🔹 Test Cells

The system is designed to support **multiple independent testing stations**.

Each test cell can be configured for:

- Coolant filling
- Hydrostatic pressure testing
- Target pressure setting
- Hold-time setting
- Test Start / Stop
- Pause / Resume
- Real-time pressure monitoring
- Test status indication
- Alarm and fault monitoring

### 🔹 Pressure Monitoring

Pressure transmitters provide continuous feedback to the PLC.

The pressure data can be used for:

- Real-time PSI display
- Pressure regulation
- High-pressure warnings
- Test validation
- Pressure trend visualization
- Alarm generation

---

## 🔄 Hydrostatic Test Process

A typical hydrostatic test sequence follows:

1. **Test Setup**  
   Operator selects the test cell and configures the required test parameters.

2. **Filling**  
   The system fills the connected test unit with coolant.

3. **Pressurization**  
   The main pump increases system pressure toward the configured target PSI.

4. **Pressure Regulation**  
   PID control can regulate pump operation to maintain the required pressure while minimizing overshoot.

5. **Pressure Hold**  
   The system maintains the target pressure for the configured hold duration.

6. **Monitoring**  
   The PLC continuously monitors pressure and system conditions throughout the test.

7. **Test Completion**  
   Once the hold time is completed successfully, the test status is updated.

8. **Pressure Release / Reset**  
   The system returns the test cell to a safe condition and prepares it for the next cycle.

---

## 🔄 Simplified Sequence

```text
IDLE
  ↓
FILLING
  ↓
PRESSURIZING
  ↓
PID PRESSURE CONTROL
  ↓
PRESSURE HOLD
  ↓
TEST COMPLETE
  ↓
RESET
```

If an abnormal condition occurs during the sequence:

```text
PROCESS
   ↓
FAULT DETECTED
   ↓
ALARM / SAFE STATE
```

---

## 🎛️ HMI Design

The project includes a custom operator interface developed in **Unitronics UniLogic HMI**.

### HMI Screens

- Splash / Startup Screen
- Main Menu
- System Overview
- Cell Control Screen
- Test Mode Selection
- Main Settings
- PID Settings
- Alarm Screen
- Pressure Trend Screen
- Test Status / Progress Display

---

## 🖥️ Main HMI Functions

Operators can use the HMI to:

- Select a test cell
- Select **Filling** or **Hydrostatic Test**
- Start and stop tests
- Pause and resume operations
- Set target pressure
- Configure hold time
- Monitor actual pressure
- Monitor test progress
- View system status
- View active alarms
- Acknowledge alarms
- Monitor pressure trends
- Configure system parameters

---

## 📈 Pressure Trending

A real-time trend graph can be used to visualize:

```text
Pressure (PSI)
      ↑
      │                 ───────── Target Pressure
      │              /
      │            /
      │          /
      │        /
      │_______/____________________________→ Time
```

The pressure trend allows operators to monitor:

- Pressure rise
- Target pressure achievement
- Pressure stability
- Pressure drop
- Hold-period performance
- Abnormal pressure behaviour

This can also support future automated **Pass / Fail analysis**.

---

## 🎯 PID Pressure Control

PID control is considered for regulating the main pump and maintaining stable test pressure.

The basic control principle is:

```text
Target Pressure
      │
      ▼
   PID Control
      │
      ▼
Pump / VFD Command
      │
      ▼
Hydraulic System
      │
      ▼
Pressure Sensor
      │
      └──────── Feedback ────────┘
```

PID control can help reduce:

- Pressure overshoot
- Pressure oscillation
- Pump cycling
- Unstable hold pressure

Typical PID parameters include:

- **P – Proportional Gain**
- **I – Integral Gain**
- **D – Derivative Gain**

Critical PID parameters can be protected from normal operator access and configured through an engineering or maintenance settings screen.

---

## 🚦 Cell Operating Modes

Each test station can support different operating modes.

### Filling Mode

```text
START
  ↓
OPEN CELL VALVE
  ↓
START COOLANT FLOW
  ↓
MONITOR PROCESS
  ↓
FILL COMPLETE
  ↓
STOP / CLOSE VALVE
```

### Hydrostatic Mode

```text
START
  ↓
FILL SYSTEM
  ↓
PRESSURIZE
  ↓
REACH TARGET PSI
  ↓
HOLD PRESSURE
  ↓
MONITOR PRESSURE
  ↓
COMPLETE TEST
```

---

## 🚨 Alarm Management

The system includes an alarm architecture for identifying abnormal process conditions.

Potential alarms include:

- High Pressure
- Low Pressure
- Pressure Not Reached
- Excessive Pressure Drop
- Pump Fault
- VFD Fault
- Pressure Sensor Fault
- Communication Fault
- Valve Fault
- Test Timeout
- Emergency Stop
- System Interlock Active

The HMI alarm screen can display:

- Alarm description
- Alarm status
- Active alarms
- Alarm acknowledgement
- Alarm history

---

## 🛡️ Safety & Interlocks

Safety and equipment protection are important parts of the control strategy.

Interlocks can prevent operation when unsafe conditions are detected.

Examples include:

- Pump operation disabled during critical faults
- High-pressure shutdown
- Pressure limits
- Emergency-stop monitoring
- Sensor validation
- Test-cell availability check
- Valve sequencing
- Pump / valve interlocking
- Fault-based automatic shutdown

---

## 🛠️ Implementation

### Unitronics UniLogic

**PLC Logic** is used for:

- Automatic process sequencing
- Test state management
- Pump control
- Valve control
- Pressure monitoring
- Timers
- Safety interlocks
- Alarm handling
- PID pressure regulation
- Test completion logic

### HMI

The integrated HMI is used for:

- Operator commands
- Process visualization
- Pressure monitoring
- Test configuration
- Test mode selection
- Alarm visualization
- Pressure trending
- System settings

---

## 📊 Control Logic Summary

### Inputs

- Pressure transmitters
- Temperature sensors
- Flow sensors
- Differential pressure sensors
- Pump feedback
- VFD feedback
- Valve feedback
- Emergency stop
- System status signals

### Outputs

- Main pump command
- VFD speed reference
- Cell valve commands
- Fill valve commands
- Pressure control outputs
- Alarm indicators
- Warning buzzer
- System status indicators

---

## ⚙️ Example Adjustable Parameters

```text
Target Pressure        : 60 PSI
Pressure Warning Limit : User Configurable
Hold Time              : User Configurable
Pump Speed             : Automatic / PID Controlled
Pressure Tolerance     : Configurable
Test Mode              : Filling / Hydrostatic
```

The values can be adjusted depending on the required test procedure.

---

## 🌐 Communication

The system architecture can support industrial communication protocols such as:

- Modbus TCP
- Modbus RTU
- Ethernet communication

Communication can be used for:

- PLC-to-PLC communication
- Sensor data acquisition
- VFD communication
- Remote monitoring
- Future PC-based supervisory control

---

## 🖧 System Architecture

```text
                    ┌─────────────────────┐
                    │   Unitronics PLC    │
                    │       + HMI         │
                    └──────────┬──────────┘
                               │
                ┌──────────────┼──────────────┐
                │              │              │
                ▼              ▼              ▼
         Pressure Sensors   Main Pump        VFD
                │              │
                │              ▼
                │       Coolant Supply
                │              │
                │     ┌────────┼────────┐
                │     │        │        │
                ▼     ▼        ▼        ▼
              Cell 1 Cell 2  Cell 3   ...
                │     │        │
                ▼     ▼        ▼
            Test Unit Test Unit Test Unit
```

---

## 📂 Repository Structure

```text
Multi-Station-Hydrostatic-Test-System/
│
├── README.md
│
├── PLC/
│   ├── UniLogic_Project/
│   └── PLC_Logic/
│
├── HMI/
│   ├── Main_Menu/
│   ├── Cell_Control/
│   ├── Settings/
│   ├── Alarms/
│   └── Trends/
│
├── Documentation/
│   ├── System_Architecture/
│   ├── Control_Sequence/
│   └── IO_List/
│
├── Images/
│   ├── HMI_Main_Menu.png
│   ├── HMI_Cell_Control.png
│   ├── HMI_Settings.png
│   └── HMI_Alarm_Page.png
│
└── Screenshots/
```

---

## 🚀 Future Enhancements

Planned future improvements include:

- Automatic Pass / Fail determination
- Automatic pressure test report generation
- Test data logging
- Pressure history storage
- Test result database
- Serial number / barcode tracking
- Operator login and user access levels
- Test recipe management
- Automatic PID tuning
- Production statistics
- Cycle-time monitoring
- Remote monitoring
- PC-based supervisory application
- Wireless or Ethernet-based PLC monitoring
- Historical trend visualization
- CSV test-data export
- Factory network / MES integration

---

## 🎯 Project Objectives

The main objectives of this project are to:

- Automate coolant filling and hydrostatic testing
- Improve test repeatability
- Maintain accurate pressure control
- Reduce manual operator intervention
- Improve operator safety
- Provide centralized process monitoring
- Improve fault detection
- Simplify troubleshooting
- Record and visualize test performance
- Create a scalable architecture for multiple test stations

---

## 🧰 Technologies & Skills

<p align="center">

`Unitronics UniLogic` • `PLC Programming` • `HMI Development` • `PID Control` • `Industrial Automation` • `Modbus` • `VFD Control` • `Instrumentation` • `Pressure Control` • `Alarm Management` • `Process Control` • `Industrial Networking`

</p>

---

## 👨‍💻 Author

**Md Mahadi Hasan Moon**

Electrical & Computer Engineering | EIT  
Industrial Automation | PLC | HMI | Control Systems

---

<p align="center">
  <i>“Automating pressure testing through intelligent control, monitoring, and industrial automation. ⚙️💧”</i>
</p>
