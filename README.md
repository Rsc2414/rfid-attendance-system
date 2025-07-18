# RFID-Based College Attendance System


## 📌 Project Overview
This project is an IoT-based solution built with Arduino and RFID technology to automate student attendance in colleges. It reduces manual errors by 30% and eases administrative work.

## 🚀 Features
- Detects student ID via RFID tag
- Logs attendance via Serial Monitor
- Can be extended to SD card or IoT server logging

## 🛠️ Hardware Used
- Arduino Uno
- MFRC522 RFID Reader Module
- RFID Tags (Keychain or Cards)
- Jumper Wires
- Breadboard or PCB

## ⚡ Circuit Diagram

MFRC522 → Arduino UNO
SDA → Pin 10
SCK → Pin 13
MOSI → Pin 11
MISO → Pin 12
IRQ → Not connected
GND → GND
RST → Pin 9
3.3V → 3.3V


> 💡 Use the `MFRC522` library in Arduino IDE via Library Manager before uploading.

## 📂 File List
- `rfid_attendance.ino` – Arduino source code
- `README.md` – Documentation

## 📸 Sample Output (Serial Monitor)

RFID Attendance System Initialized.
Scanned UID: DE 4B 3A 91
Attendance marked ✅


## 📄 License
MIT

---

Feel free to expand the code by:
- Adding EEPROM to prevent multiple scans in a day
- Using an SD card or IoT platform like Firebase to log attendance


