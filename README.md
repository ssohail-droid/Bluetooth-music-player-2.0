## 📌 Project Overview
This project builds a **Bluetooth Classic A2DP audio player** using an **ESP32** and **ESP-IDF**, with a strong focus on **correct system architecture**, **power behavior**, and **real RF limitations**.

The project intentionally avoids “magic software fixes” and instead documents what **is and is not possible** with ESP32 Bluetooth, providing a solid foundation for a future hardware revision.

---

## 🎯 Project Objectives
- Build a **stable A2DP Source** using ESP-IDF
- Understand **Bluetooth power and RF limits**
- Avoid unnecessary complexity and unstable hacks
- Measure what matters: **architecture over myths**
- Create a clean base for **future hardware upgrades**

---

## 🧱 Hardware
- ESP32 Dev Board (WROOM-class)
- USB power (development & testing)
- Bluetooth headphones (A2DP sink)
- PLA enclosure (RF-transparent)

---

## 🧠 Design Philosophy
This project is structured in **phases**.  
Each phase is validated before moving on to avoid compounding bugs or false assumptions.

**Key rule:**  
> If the system is not stable, do not add features.

---

## 🗺️ Project Roadmap

### ✅ Phase 0 — Environment Sanity
**Goal:**  
Verify ESP-IDF, flash configuration, and board stability.

**Deliverables:**
- Reliable boot (no reset loops)
- Serial logs visible after bootloader
- Correct flash size/mode configuration

---

### ✅ Phase 1 — Bluetooth Baseline
**Goal:**  
Initialize Classic Bluetooth and A2DP Source with **no audio yet**.

**Deliverables:**
- Device advertises over Bluetooth
- Headphones can discover and connect
- Bluetooth stack remains stable

---

### ⏭ Phase 2 — Audio Test Tone
**Goal:**  
Verify actual A2DP audio streaming.

**Deliverables:**
- Continuous sine wave playback
- No dropouts or resets
- Stable long-duration connection

---

### ⏭ Phase 3 — Power Behavior Analysis
**Goal:**  
Understand power usage in different states.

**Deliverables:**
- Idle (Bluetooth on, no audio)
- Active streaming
- “Soft-off” (audio gated, CPU reduced)

---

### ⏭ Phase 4 — SD Card WAV Playback
**Goal:**  
Replace test tone with real audio.

**Deliverables:**
- FATFS + SPI SD card
- WAV header parsing
- Ring buffer feeding A2DP

---

### ⏭ Phase 5 — UI & Controls
**Goal:**  
Human interaction without breaking stability.

**Deliverables:**
- Buttons (play/pause/next)
- Minimal display updates
- No Bluetooth instability from UI logic

---

### ⏭ Phase 6 — Hardware v2 Decision
**Goal:**  
Decide whether ESP32 is sufficient long-term.

**Deliverables:**
- External-antenna ESP32 option  
  **or**
- Migration to dedicated Bluetooth audio SoC

---

## 🔧 Software Stack
- ESP-IDF v5.5.x
- Classic Bluetooth (Bluedroid host)
- A2DP Source profile
- No Arduino framework
- Minimal, explicit configuration via `menuconfig`

---

## 📁 Project Structure
bt_audio_player/
├── CMakeLists.txt
├── sdkconfig
└── main/
├── CMakeLists.txt
└── main.c


