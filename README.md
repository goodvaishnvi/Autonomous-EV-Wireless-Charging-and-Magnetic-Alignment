# ⚡ Autonomous EV Wireless Charging and Magnetic Alignment

## 📌 Project Overview

Autonomous EV Wireless Charging and Magnetic Alignment is an embedded system designed to improve the efficiency of Wireless Power Transfer (WPT) in Electric Vehicles (EVs).

Wireless charging efficiency decreases when the transmitter and receiver coils are not properly aligned. This project uses a **TMAG5273 3D Hall-Effect Magnetic Sensor** to detect magnetic-field variations and an **SG90 Servo Motor** to automatically adjust the coil alignment.

The MSPM0H3216 microcontroller processes the magnetic sensor readings, calculates alignment error, and controls the servo motor. An INA219 sensor is included to monitor electrical parameters such as voltage, current, and power. An OLED display provides real-time system information.

## 🎯 Objectives

- Develop an automatic magnetic alignment system for EV wireless charging.
- Detect magnetic-field variations using a 3D Hall-Effect sensor.
- Measure magnetic-field components along X, Y, and Z axes.
- Automatically correct coil misalignment using a servo motor.
- Monitor voltage, current, and power during charging.
- Display sensor readings and alignment status on an OLED display.

## 🛠️ Components Required

| Component | Purpose |
|---|---|
| MSPM0H3216 LaunchPad | Main microcontroller |
| TMAG5273 | 3D magnetic-field detection |
| SG90 Servo Motor | Automatic mechanical alignment |
| INA219 | Voltage, current and power monitoring |
| OLED Display | Display sensor readings and system status |
| Magnetic Pilot Beacon | Generates the magnetic reference field |

## ⚙️ Technologies Used

- Embedded C
- Texas Instruments MSPM0 SDK
- I²C Communication
- PWM (Pulse Width Modulation)
- Hall-Effect Magnetic Sensing
- Closed-Loop Alignment Control

## 🔄 Working Principle

1. **Magnetic Field Detection:** A magnetic pilot beacon is placed near the charging pad. The TMAG5273 detects its magnetic field.
2. **Data Acquisition:** The sensor measures magnetic-field components along the X, Y, and Z axes.
3. **Data Processing:** The MSPM0H3216 receives sensor readings through I²C communication and processes the measurements.
4. **Calibration:** The system initially sets the servo motor to 90° and takes 64 X-axis readings to calculate the target magnetic value.
5. **Error Calculation:** The filtered X-axis measurement is compared with the calibrated target value to determine alignment error.
6. **Automatic Alignment:** The controller calculates small servo movements to correct the misalignment.
7. **Performance Monitoring:** The INA219 monitors electrical parameters, while the OLED displays magnetic readings, servo angle, and alignment status.

**Note:** Converting magnetic-field readings into actual coil displacement requires calibration and a known magnetic-field arrangement.

## 🧠 System Algorithm

1. Initialize the microcontroller and peripherals.
2. Configure I²C communication, OLED, TMAG5273 and servo.
3. Set the servo motor to the center position (90°).
4. Calibrate the target magnetic position using 64 sensor readings.
5. Continuously read X, Y and Z magnetic-field values.
6. Apply a 16-sample moving average filter.
7. Calculate alignment error by comparing filtered X with target X.
8. If the error is within the alignment limit, mark the system as aligned.
9. Otherwise, calculate a servo correction step and adjust its position.
10. Display sensor readings, servo angle and alignment status.

## 📐 Main Control Parameters

| Parameter | Value |
|---|---:|
| Servo center angle | 90° |
| Minimum servo angle | 10° |
| Maximum servo angle | 170° |
| Alignment limit | 80 |
| Maximum servo step | 3 |
| Filter samples | 16 |
| Calibration readings | 64 |
| OLED I²C address | 0x3C |
| TMAG5273 I²C address | 0x35 |
| INA219 I²C address | 0x40 |

## 🏗️ Applications

- Electric Vehicle Wireless Charging
- Automatic Parking for Charging
- Electric Wheelchairs and Mobility Vehicles
- Smart Parking Systems
- Robotic Wireless Charging
- Fleet and Public EV Charging

## 🚀 Advantages

- Automatic magnetic alignment.
- Reduced manual coil positioning.
- Real-time magnetic-field detection.
- Microcontroller-based control.
- Electrical parameter monitoring.
- Improved positioning accuracy through calibration and feedback.

## 🔮 Future Scope

- Implement two-dimensional or three-dimensional coil positioning.
- Improve alignment accuracy through advanced calibration.
- Integrate a complete wireless power transfer transmitter and receiver.
- Develop a larger mechanical alignment platform.
- Implement data logging and wireless monitoring.
- Evaluate charging efficiency at different coil positions.

## 📂 Project Structure

```text
Autonomous-EV-Wireless-Charging/
│
├── README.md
│
├── Code/
│   └── main.c
│
├── Circuit_Diagram/
│   └── circuit_diagram.png
│
├── Images/
│   ├── hardware_setup.jpg
│   ├── project_output.jpg
│   └── system_architecture.png
│
└── Documentation/
    └── project_presentation.pptx
```

## 👨‍💻 Development Platform

**Microcontroller:** MSPM0H3216 LaunchPad

**Programming Language:** Embedded C

**Communication:** I²C

**Motor Control:** PWM

**Development Environment:** Code Composer Studio / TI MSPM0 SDK

## 📌 Project Status

Embedded system development and magnetic alignment prototype.




---

