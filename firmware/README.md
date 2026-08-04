# Firmware - Hardware Integration

This directory contains the embedded C++ codebase for our hardware endpoints, running on the ESP32-S3 architecture. This firmware manages all physical interactions, including sensor polling, camera triggers, motor driver logic, and state management (e.g., the bottle-recycling currency system).

## Hardware & Tech Stack

- **Microcontroller:** ESP32-S3 (Config: `4d_systems_esp32s3_gen4_r8n16`)
- **Environment:** PlatformIO
- **Key Peripherals:** ESP32-S3 Cam, servos, LiDAR, environmental sensors, LED indicators, and audio buzzers.

---

## Directory Structure

- `src/`: Main application source code and core state machine logic.
- `lib/`: Custom, reusable internal hardware libraries (e.g., LED management, buzzer control, sensor parsing).
- `include/`: Header files, global configurations, and unified GPIO pin mappings.
- `test/`: Unit tests for hardware logic.

---

## Developer Setup

Because our 5-person team develops across different operating systems (Windows and Linux), we rely entirely on **PlatformIO** to isolate the C++ toolchain and prevent local compiler conflicts.

1. Install the **PlatformIO IDE** extension in VS Code.
2. Open the `firmware/Software_Engineering` folder. (PlatformIO requires its folder to be the root of the workspace to initialize properly).
3. Allow PlatformIO a few minutes to automatically read the `platformio.ini` file and download the correct ESP32 toolchains and libraries.
4. Click the PlatformIO **Build** button (the checkmark icon in the bottom status bar) to verify your local environment compiles successfully.

---

## ⚠️ Strict Development Rules

Hardware debugging is difficult. To maintain a stable and traceable codebase, the following rule is absolute and non-negotiable:

- **RULE: NO DELETING LOGS OR COMMENTS, EVERYTHING MUST LOG ITSELF.**
  Every state change, sensor reading, API transmission, and camera trigger must output to the serial monitor. Do not remove existing debug lines, comments, or logging statements when refactoring code.

---

## Flashing the Device

1. Connect the ESP32-S3 to your machine via USB.
2. Ensure you have the proper USB-to-UART bridge drivers installed for your OS.
3. Click the PlatformIO **Upload** button (the right-arrow icon in the bottom status bar).
4. Click the **Serial Monitor** button (the plug icon) to view the live logs.
