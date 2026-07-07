# Battery Management System (BMS) using Arduino/ESP32

An embedded Battery Management System (BMS) prototype designed for a 12V lead-acid battery pack. The system performs real-time battery voltage monitoring, State-of-Charge (SoC) estimation, and intelligent charging control using Arduino/ESP32.

The project integrates voltage sensing, IoT-based monitoring using MQTT, LCD visualization, and Bluetooth-enabled manual control to improve battery safety and reliability.

---

## Features

### Battery Monitoring
- Measures battery voltage using a voltage divider-based sensing circuit.
- Processes analog sensor readings through the microcontroller ADC.
- Estimates battery State-of-Charge (SoC) using voltage-based calculation.

### Automated Charging Control
- Implemented finite state-machine based charging logic.
- Automatically disables charging when battery voltage reaches full capacity (~14.4V).
- Re-enables charging when battery percentage drops below the safe threshold.
- Prevents overcharging and enhances battery lifespan.

### LCD Display Interface
- Displays real-time battery parameters:
  - Battery Voltage
  - Battery Percentage (SoC)
  - Charging Status

### IoT Monitoring using MQTT
- Publishes battery voltage and SoC data to an MQTT broker.
- Enables remote battery monitoring.
- Supports wireless command-based charging control.

### Bluetooth Manual Control
Supports manual operation using Bluetooth commands:

| Command | Function |
|---------|----------|
| 1 | Enable Charging |
| 0 | Disable Charging |
| 3 | Switch to Automatic Mode |

### Connectivity Indicators
- LED indication for:
  - Wi-Fi connection status
  - MQTT connection status

---

## System Workflow

1. Battery voltage is measured using the voltage divider circuit.
2. ESP32/Arduino reads voltage through ADC.
3. Battery State-of-Charge (SoC) is calculated.
4. Data is displayed on the LCD interface.
5. Battery parameters are transmitted using MQTT.
6. Charging is controlled automatically or manually.

---

## Hardware Components

- ESP32 / Arduino Microcontroller
- 12V Lead-Acid Battery
- Voltage Divider Circuit
- Relay Based Charging Control Circuit
- I2C LCD Display
- Bluetooth Module (HC-05)
- Status Indicator LEDs

---

## Software Requirements

### Development Environment
- Arduino IDE

### Libraries Used
- Wire.h
- LiquidCrystal_I2C.h
- WiFi.h
- PubSubClient.h

---

## Charging Control Logic

### Automatic Mode

Charging is disabled when:

Battery Voltage >= 14.4V

The battery is detected as fully charged and charging is stopped.

Charging resumes when:

Battery Percentage <= 15%

This ensures safe battery operation and prevents deep discharge conditions.

---

## Circuit Implementation

### Voltage Sensing

- Battery voltage is reduced using a resistor-based voltage divider circuit.
- The reduced voltage is supplied to the microcontroller ADC pin.
- Actual battery voltage is calculated using the voltage divider ratio.

### Communication

- MQTT protocol enables IoT-based remote monitoring.
- Bluetooth communication provides manual charging control.

---

## Applications

- Electric Vehicle Battery Monitoring
- Renewable Energy Storage Systems
- UPS Battery Management
- Embedded Power Monitoring Systems

---

## Future Improvements

- Integration of current sensing for Coulomb counting based SoC estimation.
- State-of-Health (SoH) monitoring.
- Active/passive cell balancing implementation.
- CAN communication support for EV applications.

---

## Safety Considerations

- Use suitable resistor values for voltage divider design.
- Ensure ADC input voltage stays within microcontroller limits.
- Adjust charging thresholds according to battery specifications.
