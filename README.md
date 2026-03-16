# AERIS-FSAR
AERIS- FSAR (Fire Suppression and Response Robot) is an autonomous firefighting robot designed to detect and extinguish fires in hazardous environments.  The system uses an ESP32-based control architecture, sensor-based fire detection, and a suppression mechanism to respond to fire incidents while minimizing human risk.


# <b>📌DESCRIPTION</b>

AERIS FSAR is an autonomous firefighting robot designed to detect and suppress small-scale fires in a controlled environment. The robot navigates inside a bounded arena, detects fire sources using flame sensors, aligns itself toward the fire, and extinguishes it using an air-based suppression mechanism.

The system integrates sensing, navigation, and suppression capabilities using an ESP32 microcontroller, enabling the robot to autonomously search for fire sources, suppress them, and continue scanning the environment.

---

# 📑 Table of Contents

1. Achievement
2. Project Overview
3. Problem Statement
4. Key Features
5. Components Used (BOM)
6. System Architecture
7. Working Principle
8. Repository Structure
9. Team
10. Future Improvements
11. License

---

# 🏆 Achievement

Winner — Defence Domain  
Kalpataru Robotics Competition

• Total teams in competition: 28  
• Teams in Defence Domain: 6  
• Result: **1st Place**

The challenge required teams to design an autonomous robot capable of detecting and extinguishing fire sources within a defined arena.

---

# 📌 Project Overview

The robot operates inside a square arena surrounded by black boundary lines. Multiple fire sources (candles) are placed within the arena.

The robot performs the following actions autonomously:

• Roams within the arena while avoiding boundaries  
• Continuously scans for fire using flame sensors  
• Navigates toward the detected fire source  
• Aligns itself so the central sensor faces the flame  
• Activates a fan-based suppression system to extinguish the fire  
• Returns to roaming mode to search for additional fire sources

This system demonstrates how autonomous robots can assist in fire response scenarios where human intervention may be dangerous.

---

# ❗ Problem Statement

Fire incidents in hazardous or inaccessible environments pose significant risks to human responders. Autonomous robotic systems can assist in detecting and suppressing fire sources while minimizing human exposure to danger.

The objective of this project was to design a robotic system capable of:

• Detecting fire sources autonomously  
• Navigating safely within a defined environment  
• Locating and approaching the fire source  
• Suppressing the fire using an onboard mechanism  
• Continuing operation to detect additional fire sources

---

# ⚙️ Key Features

• Autonomous fire detection  
• Multi-directional flame sensing (~120° detection arc)  
• Autonomous arena navigation  
• Boundary detection using IR sensors  
• Air-based fire suppression using a fan mechanism  
• ESP32-based control architecture  
• Lightweight and cost-effective robotic design

---

# 🧰 Components Used (BOM)

## Control System
• ESP32 Microcontroller

## Sensors
• 5-Channel Flame Sensor Module  
• 4 IR Sensors (Boundary Detection)

## Motion System
• 2 × DC Gear Motors  
• Motor Driver Module (PWM motor control)  
• 1 × Caster Wheel

## Fire Suppression System
• DC Fan Motor  
• Plastic 4-Blade Fan  
• Relay Module (Fan Control)

## Power System
• 12V Lithium-ion Battery  
• Battery Holder  
• Battery Charging Module

## Mechanical & Structural
• Plastic chassis panels  
• PCB Zero board (for secure wiring connections)  
• Power switch

---

# 🧠 System Architecture

The robot integrates sensing, control, navigation, and suppression systems.

Sensors → ESP32 Controller → Motor Driver → Robot Movement  
Flame Detection → ESP32 → Relay Module → Fire Suppression Fan

The ESP32 processes data from flame sensors and IR sensors to determine robot movement and suppression actions.

---

# ⚡ Working Principle

The robot operates using three operational modes.

---

## 1️⃣ Roaming Mode

In roaming mode, the robot moves around the arena searching for fire sources.

• IR sensors monitor the arena boundary  
• If a black boundary is detected:
  - Robot moves backward briefly
  - Turns right
  - Continues roaming

This ensures the robot remains inside the arena.

---

## 2️⃣ Fire Tracking Mode

When flame sensors detect a fire source:

• Sensor readings determine the direction of the fire  
• Robot adjusts its orientation  
• The robot aligns so the **central flame sensor points directly toward the fire**

This ensures accurate positioning of the suppression mechanism.

---

## 3️⃣ Fire Suppression Mode

When the robot reaches the fire source:

• Robot stops movement  
• Relay activates the fan motor  
• Fan blows air toward the flame

This airflow disrupts the oxygen supply, extinguishing the fire.

Suppression cycle:

• Fan ON for 5 seconds  
• Fan OFF  
• Sensors check if flame persists

If fire remains, the cycle repeats.

Once extinguished:

• Fan stops  
• Robot moves backward  
• Robot turns and resumes roaming mode

---

# 👥 Team

Team Name: **PARALYX**

• Atharv Gawade — Team Leader  
• Gitanshu Tule — Software & Hardware  
• Nishant Suryawanshi — Hardware  
• Vaibhav Chelekar — Hardware  
• Vishudhi Waykos — Presentation

---

# 🚀 Future Improvements

• Thermal camera integration  
• AI-based fire detection  
• SLAM-based navigation  
• Remote monitoring system  
• Advanced obstacle avoidance sensors  
• Deployment in real-world hazardous environments

---
# 📂 Repository Structure

```
aeris-fsar
│
├── README.md
│
├── hardware
│ ├── components_list.md
│ ├── circuit_diagram.png
│ ├── wiring_connections.md
│ └── README.md
│
├── firmware
│ ├── aeris_fsar.ino
│ └── code_explanation.md
│
├── design
│ └── fusion360_model.f3d
│
├── documentation
│ ├── architecture_diagram.png
│ ├── presentation_slides.pdf
│ ├── team_photos
│ ├── robot_photos
│ └── videos
```

---

# 📜 License

MIT License
