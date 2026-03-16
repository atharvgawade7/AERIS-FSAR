# Development Notes

This section highlights some practical challenges faced during the development and testing of the **AERIS-FSAR (Autonomous Fire Suppression and Response Robot)** along with possible improvements for future versions.

---

## Challenges Faced

- **Sensor calibration** – Flame sensors required careful threshold tuning. Small changes in sensor position could cause false readings or missed detections.
- **Environmental interference** – The flame sensor could detect strong sunlight as fire. For reliable operation, testing was performed in darker environments or controlled lighting conditions.
- **Mechanical stability** – Wheels and chassis alignment had to be adjusted to reduce wobbling and ensure smooth movement.
- **Electrical reliability** – Connections had to be secured properly on the PCB to avoid loose wiring and unstable signals.
- **Power management** – The lithium battery required regular monitoring and charging during extended testing sessions.

---

## Precautions During Testing

- All sensors were firmly mounted to prevent displacement during robot movement.
- Connections were soldered on a PCB instead of using a breadboard to improve stability.
- The robot was tested with **small controlled flames (candles)** inside a defined arena.

---

## Future Improvements

- Integration of **ultrasonic sensors** for obstacle detection and safer navigation.
- **Remote monitoring and control** using ESP32 WiFi connectivity.
- Improving the robot’s ability to operate in **different environments and lighting conditions**.
- Upgrading the **air-based fire suppression system** for stronger and more efficient extinguishing.
