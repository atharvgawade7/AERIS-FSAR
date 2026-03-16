# Firmware Logic Explanation

The firmware controls the behavior of the **AERIS-FSAR robot** using the ESP32.  
It reads sensor data, decides the robot state, and controls movement and fire suppression.

---

# 1. Pin Configuration

The initial section defines all hardware connections.

- **Motor Driver Pins**
  - ENA, ENB control motor speed using PWM.
  - IN1–IN4 control motor direction (forward, backward, turning).

- **IR Sensors**
  - IR1–IR4 detect the black boundary of the arena.
  - Used to prevent the robot from leaving the field.

- **Flame Sensor Pins**
  - Five analog sensors detect flame direction.
  - Positioned as: Left, Left-Middle, Center, Right-Middle, Right.

- **Relay Pin**
  - Controls the fire suppression fan.
  - Relay ON activates the fan to extinguish fire.

---

# 2. System Settings

Important control parameters are defined.

- `THRESHOLD`
  - Minimum flame sensor value required to consider fire detected.

- `SPEED_FORWARD`
  - Motor speed used for normal movement.

- `SPEED_TURN`
  - Motor speed used when turning toward fire.

- **PWM Setup**
  - ESP32 PWM channels control motor speed.

---

# 3. Robot States

The robot operates using a simple **state machine**.

- `ROAMING`
  - Robot moves around the arena searching for fire.

- `FIRE_TRACKING`
  - Activated when a flame is detected.
  - Robot aligns itself toward the fire.

---

# 4. Motor Control Functions

Reusable functions control robot movement.

- `forward()`
  - Moves the robot straight ahead.

- `backward()`
  - Moves the robot backward.

- `turnLeft()` / `turnRight()`
  - Rotates the robot to align with fire direction.

- `stopMotors()`
  - Stops both motors immediately.

- `setSpeed()`
  - Controls motor speed using PWM signals.

---

# 5. Setup Function

The `setup()` function initializes the system.

- Starts serial communication for debugging.
- Sets motor driver pins as output.
- Configures IR sensors as input.
- Initializes the relay module.
- Configures PWM channels for motor speed control.

---

# 6. Sensor Reading

During every loop cycle the robot reads:

- IR sensor values for boundary detection.
- Flame sensor values to determine fire location.
- A logical check determines if **any flame sensor crosses the threshold**.

If any sensor detects fire → `flameDetected = true`.

---

# 7. Mode Switching

If the robot is roaming and detects a flame:

- The robot switches from **ROAMING → FIRE_TRACKING mode**.

---

# 8. Roaming Mode (Normal Navigation)

In roaming mode the robot:

- Moves forward while scanning the environment.
- If a boundary is detected using IR sensors:
  - Moves backward briefly.
  - Turns right to stay inside the arena.

This behavior allows **continuous autonomous exploration**.

---

# 9. Fire Tracking Mode

When fire is detected:

- The robot compares the flame sensor values.
- It determines where the strongest flame signal is located.

Movement decision:
- Center strongest → move forward.
- Left stronger → turn left.
- Right stronger → turn right.

This aligns the robot toward the fire.

---

# 10. Fire Suppression Condition

The robot considers that it **reached the fire** when:

- The center flame sensor has the strongest signal.
- A boundary is detected near the fire source.

When this condition occurs:

- Motors stop.
- Fire suppression sequence begins.

---

# 11. Fire Suppression Loop

The robot repeatedly performs:

1. Turn fan **ON for 5 seconds**.
2. Turn fan **OFF for 2 seconds**.
3. Check if the flame still exists.

If flame disappears:

- Fan is turned OFF.
- Robot moves backward.
- Turns right to exit the fire area.
- Returns to **ROAMING mode**.

---

# 12. Continuous Operation

After extinguishing the fire:

- The robot resumes roaming.
- Searches for another possible fire source in the arena.
