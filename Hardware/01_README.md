# AERIS FSAR Hardware

This section documents the hardware architecture of **AERIS FSAR (Fire Suppression and Response Robot)**.

The robot is built using a modular hardware structure consisting of:

• Sensing System  
• Motion System  
• Fire Suppression System  
• Power System  

These subsystems work together to enable autonomous fire detection, navigation, and suppression.

---


# Hardware Components

## ESP32 Development Board
- Acts as the main controller, processing sensor inputs and executing control logic.
- Sends control signals to the motor driver, relay module, and other actuators.

## Flame Sensor (5-Channel)
- Detects infrared radiation emitted by flames within a wide sensing range.
- Helps the robot identify and align toward the fire source.

## IR Sensors (Boundary Detection) (4)
- Detect black boundary lines using infrared reflection.
- Allow the robot to stay inside the arena and avoid crossing boundaries.

## Motor Driver Module
- Interfaces the ESP32 with DC motors and supplies required current.
- Enables PWM-based speed and direction control of the robot.

## DC Gear Motors (2)
- Provide mechanical movement for the robot.
- Drive the wheels to enable forward motion and turning.

## Wheels (2)
- Convert motor rotation into robot movement and traction.
- Wheel diameter (~65–70 mm) provides stable motion and smooth navigation.

## Caster Wheel
- Supports the robot chassis while allowing free rotation for balance.
- Helps maintain smooth turning and stability.

## Relay Module
- Acts as an electronic switch controlled by the ESP32.
- Used to turn the fire suppression fan ON and OFF.

## Fire Suppression Fan (DC Motor)
- Generates airflow to cut off oxygen supply to the flame.
- Activated when the robot enters fire suppression mode.

## Lithium-Ion Battery (12V)
- Provides portable power to the robot system.
- Supplies energy for motors, sensors, ESP32, and fan.

## Battery Charging Module
- Allows direct charging of the lithium battery pack.
- Ensures safe and convenient power management.

## Switch
- Used to manually turn the robot ON or OFF.
- Controls the main power flow to the system.

---

# Wiring Logic

The AERIS-FSAR robot uses the ESP32 as the central controller. Sensors provide input signals to the ESP32, and based on these inputs the ESP32 controls actuators like motors and the fire suppression fan.

---

## Sensor Connections

| Component | Connected To | Purpose |
|-----------|--------------|---------|
| Flame Sensor (5-Channel) | ESP32 Analog/Digital GPIO Pins | Detects the direction and presence of fire |
| IR Sensors | ESP32 GPIO Pins | Detect black arena boundaries |

---

## Motion Control Connections

| Component | Connected To | Purpose |
|-----------|--------------|---------|
| Motor Driver | ESP32 PWM / GPIO Pins | Controls speed and direction of motors |
| DC Gear Motors | Motor Driver Output | Drives the robot wheels |

---

## Fire Suppression Connections

| Component | Connected To | Purpose |
|-----------|--------------|---------|
| Relay Module | ESP32 GPIO Pin | Switches the suppression fan ON/OFF |
| DC Fan Motor | Relay Module Output | Generates airflow to extinguish flame |

---

## Power Connections

| Component | Connected To | Purpose |
|-----------|--------------|---------|
| 12V Lithium Battery | Motor Driver & Relay | Provides power to motors and fan |
| ESP32 | Regulated Power Supply | Powers the control system |
| Charging Module | Battery Pack | Enables direct battery charging |

---

# Circuit Diagram

![Circuit Diagram](02_Fritzing_circuit_.png)
