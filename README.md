# 🥛 SmartMILK — Low-Cost Solar-Powered PCM-Assisted Portable Milk Chilling Can

> **Cool Milk | Better Quality | Stronger Farmers**

SmartMILK is an IoT-enabled, solar-powered milk chilling can that keeps raw milk cool without relying on grid electricity — built for small-scale and rural dairy farmers. A Phase Change Material (PCM) layer stores cooling energy to cut continuous power draw, while an ESP32 control unit monitors temperature, drives the cooling relay, and displays live status on an LCD.

🔗 **Live Dashboard:** https://smart-milk-keeper.lovable.app 

---

## 📌 Problem Statement

| Field | Details |
|---|---|
| Problem Statement ID | 26110 |
| Problem Statement Title | Development of a Low-Cost Light-weight Milk Chilling Can for Small-Scale Dairy Farmers |
| Theme | Agriculture, Food Tech and Rural Development |
| PS Category | Hardware |
| Team Name | CHILLFORGE |

---

## 🔧 Current Prototype Status

The working prototype (ESP32 + sensor + relay + LCD) is built and running. It:
- Reads live temperature via a **DHT11** sensor
- Drives a **relay module** to switch the cooling unit ON above a **4°C** threshold
- Displays live status (`SmartMILK COOL/IDLE` + temperature) on a **16x2 I2C LCD**
- Logs readings over Serial for debugging

The physical unit uses a food-grade stainless steel can with the electronics (ESP32, relay, LCD, sensor) wired externally on a test board for prototyping.

*(Solar charging, PCM thermal storage, and cloud/IoT sync are part of the full design — see Tech Stack below — and are being integrated into the next hardware revision.)*

---

## ✨ Key Features

- ✅ Rapid cooling of raw milk to 4°C
- ✅ Solar-powered — no dependency on grid electricity
- ✅ PCM-assisted thermal storage to reduce continuous cooling load
- ✅ Real-time temperature monitoring with automatic relay-controlled cooling
- ✅ Local LCD status display
- ✅ Remote IoT monitoring dashboard for farmers
- ✅ Low-cost, lightweight, and portable

---

## 🧩 System Architecture

![SmartMILK Block Diagram](docs/block-diagram.png)

### How it works
1. The solar panel charges the battery through a charge controller.
2. The ESP32 reads live temperature from the DHT11 sensor.
3. When temperature rises above 4°C, the ESP32 energizes the relay to turn cooling ON.
4. The PCM layer absorbs excess heat, reducing the continuous cooling load.
5. The insulated, food-grade stainless steel can keeps the temperature stable during transport.
6. Live status is shown on the onboard LCD and sent to the cloud/mobile dashboard.
7. Farmers get alerts if temperature rises abnormally or battery runs low.

---

## 🛠️ Tech Stack

**Hardware (built)**
- ESP32 (control unit)
- DHT11 — temperature sensor
- Relay module (active-LOW) — switches the cooling unit
- 16x2 I2C LCD (`LiquidCrystal_I2C`) — local status display

**Hardware (full design)**
- Peltier/TEC cooling module + heat sink & fan
- Phase Change Material (PCM) thermal storage
- Solar panel, charge controller, battery
- GSM/4G module (optional, for remote areas)

**Firmware**
- Arduino (C++) on ESP32
- Libraries: `Wire`, `LiquidCrystal_I2C`, `DHT`

**Software / Dashboard**
- Live web dashboard built with [Lovable](https://lovable.dev) (React + TypeScript + Vite + Tailwind CSS + shadcn/ui)
- Cloud platform: ThingSpeak / Blynk / Firebase (device-to-cloud telemetry)

---

## 🚀 Getting Started

### Dashboard
```bash
git clone https://github.com/<your-username>/smart-milk-keeper.git
cd smart-milk-keeper
npm install
npm run dev        # local dev server
npm run build       # production build
```
> Requires [Node.js](https://nodejs.org/) (v18+) and npm.

### Firmware
1. Open `firmware/smartmilk_control.ino` in Arduino IDE.
2. Install libraries: `LiquidCrystal_I2C`, `DHT sensor library` (via Library Manager).
3. Select board: **ESP32 Dev Module**.
4. Set `DHTPIN` (default 4) and `RELAY_PIN` (default 18) to match your wiring.
5. Upload, then open Serial Monitor at `115200` baud to confirm readings and relay state.

---

## 📂 Project Structure
smart-milk-keeper/
├── docs/
│ └── block-diagram.png # System architecture diagram
├── firmware/
│ └── smartmilk_control.ino # ESP32 sensor + relay + LCD control
├── src/ # Dashboard source code
├── public/
├── package.json
└── README.md

---

## 🌍 Impact

- Reduces milk spoilage during transportation
- Helps maintain milk quality
- Reduces losses for small-scale farmers

| Category | Benefit |
|---|---|
| Social | Supports farmer with better milk handling |
| Environmental | Uses renewable solar energy |
| Economic | Reduces milk wastage & income loss |


## 👥 Team CHILLFORGE

Smart India Hackathon 2026 — Problem Statement ID 26110

---

*Innovative Technology | Sustainable Agriculture | Empowering Farmers*
