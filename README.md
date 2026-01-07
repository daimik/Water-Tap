# 💧 Smart Water Tap Controller

Automated water tap control system with ESPHome, featuring safety interlocks, statistics tracking, and audio feedback.

---

## 🛒 Shopping List

### Complete Bill of Materials

| Component | Supplier | Part Number | Link | Qty |
|-----------|----------|-------------|------|-----|
| **XIAO ESP32C6** | Kiwi Electronics | 20076 | [Link](https://www.kiwi-electronics.com/nl/seeed-studio-xiao-esp32c6-20076) | 1 |
| **2.4GHz WiFi Antenna** | Kiwi Electronics | 11062 | [Link](https://www.kiwi-electronics.com/nl/2-4ghz-mini-flexibele-wifi-antenne-met-ufl-connector-11062) | 1 |
| **HLK-PM03 Power Module** | Otronic | - | [Link](https://www.otronic.nl/nl/220vac-naar-33vdc-1a-converter-module-hlk-pm03.html) | 1 |
| **Green LED Button 12mm** | Otronic | - | [Link](https://www.otronic.nl/nl/drukknop-moment-puls-5v-led-groen-rvs-12mm.html) | 1 |
| **Red LED Button 12mm** | Otronic | - | [Link](https://www.otronic.nl/nl/drukknop-moment-puls-5v-led-rood-rvs-12mm.html) | 1 |
| **Blue LED Button 12mm** | Otronic | - | [Link](https://www.otronic.nl/nl/drukknop-moment-puls-5v-led-blauw-rvs-12mm.html) | 1 |
| **2-Channel Relay Module** | Otronic | - | [Link](https://www.otronic.nl/nl/relais-module-5v-low-2-kanaals.html) | 1 |
| **Passive Buzzer Module** | Otronic | - | [Link](https://www.otronic.nl/en/buzzer-module-passive-for-arduino.html) | 1 |
| **Motorized Ball Valve** | Tameson | BW2-012-AW1-230AC | [Link](https://tameson.nl/products/bw2-012-aw1-230ac-elektrische-kogelkraan-1-2inch-2-weg-230vac-3-punt) | 1 |

### Estimated Total Cost
- **Electronics**: ~€50-70
- **Valve**: ~€40-60
- **Total**: ~€90-130 (excluding enclosure and wiring)

### Additional Materials Needed
- Enclosure (IP65 rated recommended)
- Electrical wire (220V rated for valve, low voltage for electronics)
- Terminal blocks for 220V connections
- Cable glands and strain relief
- Mounting hardware (screws, standoffs)
- Heat shrink tubing
- USB-C cable (for programming)

---

## 📋 Table of Contents

- [Hardware Components](#-hardware-components)
- [Features](#-features)
- [Pin Configuration](#-pin-configuration)
- [Physical Controls](#️-physical-controls)
- [LED Indicators](#-led-indicators)
- [Sound Effects](#-sound-effects)
- [Safety Features](#️-safety-features)
- [Web Interface](#-web-interface)
- [Operation Guide](#-operation-guide)
- [Installation](#-installation)
- [Technical Specifications](#-technical-specifications)
- [Wiring Diagram](#-wiring-diagram)

---

## 🔧 Hardware Components

### Microcontroller
**Seeed Studio XIAO ESP32C6**
- **Processor**: Dual 32-bit RISC-V (160MHz + 20MHz)
- **Memory**: 512KB SRAM + 4MB Flash
- **Wireless**: WiFi 6 (2.4GHz), Bluetooth 5.3, Zigbee, Thread
- **Form Factor**: 21 x 17.8mm thumb-size board
- **Purchase**: [Kiwi Electronics - XIAO ESP32C6](https://www.kiwi-electronics.com/nl/seeed-studio-xiao-esp32c6-20076)
- **Documentation**: [XIAO ESP32C6 Getting Started Guide](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/)

### Motorized Ball Valve
**JP Fluid Control BW2 1/2" 2-Way 230V AC 3-Point**
- **Model**: BW2-012-AW1-230AC
- **Type**: Electric ball valve
- **Size**: 1/2 inch (DN15)
- **Voltage**: 230V AC
- **Control**: 3-point control (Open/Close/Stop)
- **Operation Time**: ~25 seconds
- **Product Link**: [Tameson - BW2-012-AW1-230AC](https://tameson.nl/products/bw2-012-aw1-230ac-elektrische-kogelkraan-1-2inch-2-weg-230vac-3-punt)

### Additional Components

#### Power Supply
- **AC-DC Converter Module** - HLK-PM03 (220V AC to 3.3V DC 1A)
  - [Otronic - HLK-PM03](https://www.otronic.nl/nl/220vac-naar-33vdc-1a-converter-module-hlk-pm03.html)
  - Input: 220V AC
  - Output: 3.3V DC @ 1A
  - Compact switching power supply module

#### Control Buttons (with integrated LEDs)
- **Red Push Button** - 12mm Stainless Steel Momentary with 5V LED
  - [Otronic - Red LED Button](https://www.otronic.nl/nl/drukknop-moment-puls-5v-led-rood-rvs-12mm.html)
  - Function: Close Water / Status indicator
  
- **Green Push Button** - 12mm Stainless Steel Momentary with 5V LED
  - [Otronic - Green LED Button](https://www.otronic.nl/nl/drukknop-moment-puls-5v-led-groen-rvs-12mm.html)
  - Function: Open Water / Status indicator
  
- **Blue Push Button** - 12mm Stainless Steel Momentary with 5V LED
  - [Otronic - Blue LED Button](https://www.otronic.nl/nl/drukknop-moment-puls-5v-led-blauw-rvs-12mm.html)
  - Function: Reboot / WiFi status indicator

#### Relay Module
- **2-Channel Relay Module** - 5V LOW trigger
  - [Otronic - 2-Channel Relay](https://www.otronic.nl/nl/relais-module-5v-low-2-kanaals.html)
  - Trigger: LOW level (active low)
  - Channels: 2 independent relays
  - Contact Rating: 10A @ 250V AC / 30V DC
  - Optocoupler isolated

#### Audio Feedback
- **Passive Buzzer Module** - Arduino compatible
  - [Otronic - Passive Buzzer](https://www.otronic.nl/en/buzzer-module-passive-for-arduino.html)
  - Type: Passive (PWM controlled)
  - Voltage: 5V
  - Frequency: Variable (PWM controlled)

#### Optional
- **External WiFi Antenna** - 2.4GHz Mini Flexible WiFi Antenna with U.FL connector
  - [Kiwi Electronics - 2.4GHz Antenna](https://www.kiwi-electronics.com/nl/2-4ghz-mini-flexibele-wifi-antenne-met-ufl-connector-11062)
  - Connector: U.FL (IPEX)
  - Frequency: 2.4GHz
  - Cable Length: Flexible mini antenna
  - Range Extension: Up to 80m
  - Auto-enabled on boot (GPIO3 + GPIO14 control)

---

## ✨ Features

### Core Functionality
- ✅ Remote water tap control via WiFi
- ✅ Physical button operation (Open/Close/Reboot)
- ✅ Automatic 25-second operation timing
- ✅ Real-time countdown timers
- ✅ Persistent statistics storage

### Safety Systems
- 🛡️ **Dual Relay Interlock** - Hardware prevention of simultaneous relay activation
- 🔒 **30-Second Safety Lockout** - Prevents rapid direction changes
- 🚫 **Operation Blocking** - No new operations during active operation
- ⚙️ **Relay Interlock Monitoring** - Real-time status display

### Monitoring & Statistics
- 📊 Total operations counter
- 🔓 Total opens counter
- 🔒 Total closes counter
- ⏱️ Total runtime tracking
- 🕐 Last operation timestamp
- 📡 WiFi signal strength
- ⏰ Device uptime

### User Feedback
- 💡 **LED Status Indicators** - Visual operation feedback
- 🔊 **Audio Alerts** - Thematic water sounds for events
- 🌐 **Web Interface** - Complete control dashboard
- 📱 **Home Assistant Integration** - Full API support

### Connectivity
- 📶 WiFi 6 (802.11ax) support
- 🔐 Encrypted API communication
- 🌐 Local web server (port 80)
- 📡 External antenna support (~80m range)
- 🔄 OTA firmware updates
- 🆘 Fallback access point mode

---

## 📍 Pin Configuration

### GPIO Pin Mapping

| Pin Label | GPIO | Function | Type | Component |
|-----------|------|----------|------|-----------|
| D0 | GPIO15 | Open Button | Input (Pull-up) | Physical push button |
| D1 | GPIO16 | Close Button | Input (Pull-up) | Physical push button |
| D2 | GPIO17 | Green LED | Output | Status indicator |
| D3 | GPIO18 | Red LED | Output | Status indicator |
| D4 | GPIO19 | Blue WiFi LED | Output | WiFi status indicator |
| D5 | GPIO20 | Open Relay | Output | Valve open control |
| D6 | GPIO21 | Close Relay | Output | Valve close control |
| D8 | GPIO23 | Reboot Button | Input (Pull-up) | Physical push button |
| D9 | GPIO8 | Passive Buzzer | PWM Output | Audio feedback |
| - | GPIO3 | RF Switch Control | Reserved | Antenna control |
| - | GPIO14 | Antenna Select | Reserved | External antenna |

### Available Pins
- **D10 (GPIO9)** - Free for expansion
- **GPIO0** - Free (Boot button, use with caution)

### Total Pin Usage
- **8 GPIO pins** - Active functions
- **2 GPIO pins** - Antenna control (reserved)
- **2 GPIO pins** - Available for expansion

---

## 🎛️ Physical Controls

### Button Functions

| Button | Location | Action | Response |
|--------|----------|--------|----------|
| **Open** | D0 (GPIO15) | Starts valve opening sequence | Rising bubble sound + Green LED pulse |
| **Close** | D1 (GPIO16) | Starts valve closing sequence | Descending flow sound + Red LED pulse |
| **Reboot** | D8 (GPIO23) | Restarts the device | System reboot |

### Button Behavior
- **Debounce**: 50ms delay filter
- **Pull-up**: Internal pull-up resistors enabled
- **Active**: Low (button press = GND connection)
- **Safety**: Lockout period enforced between operations

---

## 💡 LED Indicators

### LED Status Guide

#### 🟢 Green LED (D2 - GPIO17)
| State | Meaning | Duration |
|-------|---------|----------|
| **PULSING** (500ms on/off) | Water tap opening | 25 seconds |
| **SOLID ON** | Water tap is OPEN | Until closed |
| **OFF** | Water tap is CLOSED | Until opened |

#### 🔴 Red LED (D3 - GPIO18)
| State | Meaning | Duration |
|-------|---------|----------|
| **PULSING** (500ms on/off) | Water tap closing | 25 seconds |
| **SOLID ON** | Water tap is CLOSED | Until opened |
| **OFF** | Water tap is OPEN | Until closed |

#### 🔵 Blue WiFi LED (D4 - GPIO19)
| State | Meaning |
|-------|---------|
| **SOLID ON** | WiFi connected successfully |
| **OFF** | WiFi disconnected or connecting |

### LED Persistence
✅ LEDs restore to correct state after device reboot (state saved to flash)

---

## 🔊 Sound Effects

### Audio Feedback System
**Hardware**: Passive buzzer on D9 (GPIO8) with PWM control

### Sound Events

| Event | Sound Description | Frequency Pattern | When Played |
|-------|------------------|-------------------|-------------|
| **Water Opening** | 🎵 Rising bubbles | 400Hz → 600Hz → 800Hz | Start of open operation |
| **Water Closing** | 🎵 Descending flow | 800Hz → 600Hz → 400Hz | Start of close operation |
| **Operation Complete** | 🎶 Success jingle | C-E-G chord (523-659-784Hz) | After 25-second operation |
| **Safety Lockout** | ⚠️ Warning beep | 300Hz low tone | Attempt during lockout period |
| **Device Startup** | 🎵 Power-on chime | C-E-G-C ascending | System boot complete |
| **WiFi Connected** | 📶 Quick beep | 1000Hz | WiFi connection established |
| **Error Alert** | 🚨 Triple beep | 1000Hz rapid | System error condition |

### Sound Control
- ✅ Can be **enabled/disabled** via web interface
- ✅ **"Buzzer Enabled"** switch in web UI
- ✅ **"Test Buzzer Sounds"** button for testing
- ✅ Settings persist across reboots

---

## 🛡️ Safety Features

### 1. Relay Interlock System
- **Hardware Protection**: Both relays physically cannot be active simultaneously
- **Interlock Wait Time**: 500ms safety delay between relay switches
- **Real-time Monitoring**: Web interface shows relay status
- **Error Detection**: Alerts if both relays detected active (should never happen)

### 2. 30-Second Safety Lockout
- **Purpose**: Prevents mechanical stress on valve motor
- **Trigger**: Activates after each operation completes
- **Countdown**: Displayed in web interface (30→29→28...→0)
- **Direction-specific**: Only blocks opposite direction (Open→Close or Close→Open)
- **Audio Feedback**: Warning beep if operation attempted during lockout

### 3. Operation Blocking
- **Single Operation Mode**: Only one operation at a time
- **Queue Prevention**: New operations blocked during active operation
- **Status Display**: "Operation Blocked" indicator shows reason:
  - "YES - Operation in Progress"
  - "YES - Safety Lockout Active"
  - "NO - Ready"

### 4. State Persistence
- **Flash Storage**: Water state saved every 5 minutes
- **Reboot Recovery**: System restores last known state after power loss
- **LED Restoration**: LEDs show correct state immediately after boot

---

## 🌐 Web Interface

### Access
- **URL**: `http://[DEVICE_IP_ADDRESS]`
- **Port**: 80 (HTTP)
- **Fallback AP**: "Water-Tap Fallback Hotspot"
  - Password: `password`

### Interface Sections

#### 1️⃣ Action Buttons
- **▶️ Open Water** - Start opening sequence
- **⏹️ Close Water** - Start closing sequence
- **🔄 Reset Statistics** - Clear all operation counters
- **🔄 Restart Device** - Reboot system
- **🔊 Buzzer Enabled** - Toggle sound effects on/off
- **🎵 Test Buzzer Sounds** - Play test sound sequence

#### 2️⃣ Status Display
- **💧 Water Status**
  - Closed / Open / Operating
- **⏱️ Operation Countdown**
  - 25→0 seconds during operation
- **🔒 Safety Lockout Countdown**
  - 30→0 seconds after operation
- **🚫 Operation Blocked**
  - YES/NO with detailed reason
- **🛡️ Relay Interlock Status**
  - Real-time relay state monitoring
  - "Both Relays OFF" / "Open Relay Active" / "Close Relay Active"
  - "ERROR - Both Active!" (safety violation alert)
- **🕐 Last Operation Time**
  - Seconds/minutes/hours/days ago
- **🌐 IP Address**
  - Current network address

#### 3️⃣ Usage Statistics
- **📊 Total Operations** - Overall operation count
- **🔓 Total Opens** - Number of open operations
- **🔒 Total Closes** - Number of close operations
- **⏱️ Total Runtime** - Cumulative time in hours

#### 4️⃣ System Diagnostics
- **📡 WiFi Signal Strength** - dBm signal level
- **⏰ Device Uptime** - Time since last reboot
- **✅ Device Online** - Connection status

---

## 🚀 Operation Guide

### Opening Water Sequence

```
1. User Action: Press button or click "Open Water"
   ↓
2. System Check: Verify no operation in progress
   ↓
3. System Check: Verify not in safety lockout period
   ↓
4. Audio: 🎵 Rising bubble sound (400→600→800Hz)
   ↓
5. LED: 🟢 Green LED starts pulsing (500ms on/off)
   ↓
6. Relay: ⚙️ Open relay activates
   ↓
7. Timer: ⏱️ 25-second countdown starts (25→24→23...→0)
   ↓
8. Wait: Valve motor opens tap over 25 seconds
   ↓
9. Relay: ⚙️ Open relay deactivates
   ↓
10. Audio: 🎶 Success jingle (C-E-G)
    ↓
11. LED: 🟢 Green LED solid ON
    ↓
12. Lockout: 🔒 30-second safety period begins
    ↓
13. Status: Water tap is OPEN
```

### Closing Water Sequence

```
1. User Action: Press button or click "Close Water"
   ↓
2. System Check: Verify no operation in progress
   ↓
3. System Check: Verify not in safety lockout period
   ↓
4. Audio: 🎵 Descending flow sound (800→600→400Hz)
   ↓
5. LED: 🔴 Red LED starts pulsing (500ms on/off)
   ↓
6. Relay: ⚙️ Close relay activates
   ↓
7. Timer: ⏱️ 25-second countdown starts (25→24→23...→0)
   ↓
8. Wait: Valve motor closes tap over 25 seconds
   ↓
9. Relay: ⚙️ Close relay deactivates
   ↓
10. Audio: 🎶 Success jingle (C-E-G)
    ↓
11. LED: 🔴 Red LED solid ON
    ↓
12. Lockout: 🔒 30-second safety period begins
    ↓
13. Status: Water tap is CLOSED
```

### Error Conditions

#### Attempting Operation During Active Operation
```
User presses button → System blocks → No action taken
(Operation in progress indicator shows "YES")
```

#### Attempting Operation During Safety Lockout
```
User presses button → ⚠️ Warning beep plays → Operation blocked
Countdown shows remaining lockout time (e.g., "18 sec")
```

#### Both Relays Active (Safety Violation)
```
System detects both relays ON → 🚨 Error alert sound
Web interface shows: "ERROR - Both Active!"
(Should never occur due to hardware interlock)
```

---

## 📦 Installation

### Prerequisites
- ESPHome installed (Home Assistant add-on or standalone)
- YAML configuration file (provided)
- USB-C cable for programming
- WiFi network credentials

### Hardware Assembly

#### 1. Microcontroller Connections
```
XIAO ESP32C6 Pinout:
├── Power (from HLK-PM03)
│   ├── 3V3 → 3.3V DC from HLK-PM03
│   ├── GND → Common ground
│   └── 5V → Optional USB-C for programming
│
├── Button Switches (12mm Stainless Steel)
│   ├── D0 (GPIO15) → Green button switch → GND
│   ├── D1 (GPIO16) → Red button switch → GND
│   └── D8 (GPIO23) → Blue button switch → GND
│
├── Button LEDs (integrated in buttons, 5V)
│   ├── D2 (GPIO17) → Green button LED (+) → GND
│   ├── D3 (GPIO18) → Red button LED (+) → GND
│   └── D4 (GPIO19) → Blue button LED (+) → GND
│
├── Relays (2-channel 5V LOW trigger module)
│   ├── 5V → Relay VCC
│   ├── GND → Relay GND
│   ├── D5 (GPIO20) → Open relay IN1
│   └── D6 (GPIO21) → Close relay IN2
│
└── Audio
    ├── D9 (GPIO8) → Passive buzzer module (+)
    └── GND → Passive buzzer module (-)

HLK-PM03 Power Module:
├── AC Input
│   ├── 220V Live → From mains
│   └── 220V Neutral → From mains
└── DC Output
    ├── 3.3V → ESP32C6 3V3 pin
    └── GND → Common ground

Note: Use separate 5V power supply (USB or buck converter) 
      for relay module and button LEDs if needed.
```

#### 2. Valve Wiring (230V AC - DANGER!)
```
⚠️ WARNING: 230V AC CAN BE LETHAL! 
Use qualified electrician if not experienced.

Relay 1 (Open):
├── Common (COM) → 230V Live
├── Normally Open (NO) → Valve "Open" terminal
└── Normally Closed (NC) → Not connected

Relay 2 (Close):
├── Common (COM) → 230V Live
├── Normally Open (NO) → Valve "Close" terminal
└── Normally Closed (NC) → Not connected

Valve:
├── Common → 230V Neutral
├── Open terminal → Relay 1 NO
└── Close terminal → Relay 2 NO
```

### Software Installation

#### Step 1: Prepare XIAO ESP32C6
```bash
# Enter bootloader mode:
1. Press and hold BOOT button
2. Connect USB-C cable
3. Release BOOT button
```

#### Step 2: Configure ESPHome
```yaml
# Create secrets.yaml file
wifi_ssid: "YourWiFiName"
wifi_password: "YourWiFiPassword"
```

#### Step 3: Flash Firmware
```bash
# Via ESPHome dashboard or CLI:
esphome run water-tap.yaml

# Or compile and upload:
esphome compile water-tap.yaml
esphome upload water-tap.yaml
```

#### Step 4: Initial Setup
1. Device boots and plays startup sound
2. Connects to WiFi (blue LED turns on)
3. Check Home Assistant for new device
4. Access web interface at device IP

### Antenna Configuration
External antenna is **automatically enabled** on boot:
- GPIO3 set LOW (activates RF switch)
- GPIO14 set HIGH (selects external antenna)
- No manual configuration needed
- Range extended to ~80m

---

## 📊 Technical Specifications

### Microcontroller
| Specification | Value |
|--------------|-------|
| **Model** | Seeed Studio XIAO ESP32C6 |
| **CPU** | Dual RISC-V (160MHz + 20MHz) |
| **RAM** | 512KB SRAM |
| **Flash** | 4MB |
| **WiFi** | 802.11ax (WiFi 6), 2.4GHz |
| **Bluetooth** | BLE 5.3 |
| **Other Protocols** | Zigbee, Thread (802.15.4) |
| **Dimensions** | 21 x 17.8mm |
| **Operating Voltage** | 3.3V (5V tolerant on some pins) |
| **Power Consumption** | ~30mA active, ~15μA deep sleep |

### Motorized Valve
| Specification | Value |
|--------------|-------|
| **Model** | JP Fluid Control BW2-012-AW1-230AC |
| **Type** | 3-point electric ball valve |
| **Size** | 1/2 inch (DN15) |
| **Voltage** | 230V AC |
| **Control Method** | 3-wire (Open/Common/Close) |
| **Operation Time** | ~25 seconds (open or close) |
| **Protection** | IP65 rated |
| **Material** | Brass body, stainless steel ball |
| **Temperature Range** | -10°C to +90°C |
| **Pressure Rating** | PN16 (16 bar) |

### System Performance
| Parameter | Value |
|-----------|-------|
| **Operation Duration** | 25 seconds (fixed) |
| **Safety Lockout** | 30 seconds between direction changes |
| **Relay Interlock Delay** | 500ms |
| **Statistics Update** | Every 10 seconds |
| **Flash Write Interval** | Every 5 minutes |
| **WiFi Range** | Up to 80m (with external antenna) |
| **Web Server Port** | 80 (HTTP) |
| **API Encryption** | AES (Home Assistant) |

### Power Requirements
| Component | Voltage | Current |
|-----------|---------|---------|
| **HLK-PM03 Power Module** | 220V AC input | 3.3V DC @ 1A output |
| **ESP32C6** | 3.3V | ~30-100mA |
| **Relay Module** | 5V (from USB or separate supply) | ~70mA per relay |
| **LED Buttons (integrated)** | 5V | ~20mA each |
| **Buzzer** | 5V | ~30mA |
| **Valve Motor** | 230V AC | ~5W during operation |
| **Total System** | 220V AC | ~10W max (including valve) |

### Memory Usage
| Resource | Used | Available |
|----------|------|-----------|
| **Program Space** | ~85% | 4MB Flash |
| **Dynamic RAM** | ~40% | 512KB SRAM |
| **Persistent Storage** | ~1KB | 4MB Flash (NVS) |

---

## 🔌 Wiring Diagram

### Low Voltage Connections (5V/3.3V)
```
┌─────────────────────────────────────────┐
│      XIAO ESP32C6 (Top View)            │
│                                         │
│  [USB-C]                                │
│                                         │
│  5V  ●  D0/GPIO15 ──→ Green Button SW  │
│  GND ●  D1/GPIO16 ──→ Red Button SW    │
│  3V3 ●  D2/GPIO17 ──→ Green Button LED │
│      ●  D3/GPIO18 ──→ Red Button LED   │
│      ●  D4/GPIO19 ──→ Blue Button LED  │
│      ●  D5/GPIO20 ──→ Open Relay IN    │
│      ●  D6/GPIO21 ──→ Close Relay IN   │
│      ●  D8/GPIO23 ──→ Blue Button SW   │
│      ●  D9/GPIO8  ──→ Buzzer (+)       │
│      ●  D10/GPIO9     (Free)           │
│                                         │
│  [BOOT] [RESET]                         │
└─────────────────────────────────────────┘

Power Supply:
┌──────────────────────┐
│   HLK-PM03 Module    │
│  220V AC → 3.3V DC   │
├──────────────────────┤
│ AC IN: 220V L + N    │
│ DC OUT: 3.3V + GND   │
│ Max Current: 1A      │
└──────────────────────┘
      │
      └──→ ESP32C6 3V3 + GND
```

### Button Wiring (Integrated LED Buttons)
```
   12mm Stainless Steel Button with LED
   
          ESP32C6              Button         
             │                   │
    GPIO15 ──┼───────────────→ SW (NO)
             │                   │
       GND ──┼───────────────→ SW COM
             │                   │
    GPIO17 ──┼───────────────→ LED (+)
             │                   │
       GND ──┼───────────────→ LED (-)
             
   Note: Buttons have built-in LED
   Green Button = Open Water control
   Red Button = Close Water control  
   Blue Button = Reboot control
```

### LED Control (Integrated in Buttons)
```
The 12mm stainless steel buttons have integrated 5V LEDs:
- Green LED in Green Button (GPIO17)
- Red LED in Red Button (GPIO18)
- Blue LED in Blue Button (GPIO19)

Each LED is controlled independently from the button switch.
```

### Relay Module Wiring (2-Channel LOW Trigger)
```
    ESP32C6       2-Ch Relay Module       230V Valve
       │              │                      │
  GPIO20 ──→ IN1    VCC ────── 5V           │
  GPIO21 ──→ IN2    GND ────── GND          │
   5V   ──→ VCC                             │
   GND  ──→ GND    COM1 ───────────────── L (Live)
                   NO1  ───────────────── Valve Open
                   COM2 ───────────────── L (Live)
                   NO2  ───────────────── Valve Close
                                            │
                   Valve Common ────────── N (Neutral)

Note: This is a LOW trigger module
- HIGH (5V) = Relay OFF
- LOW (0V) = Relay ON
- Optocoupler isolated for safety
```

### High Voltage Warning
```
⚠️  DANGER - 230V AC  ⚠️

DO NOT attempt high voltage wiring without:
✓ Qualified electrician certification
✓ Proper isolation from low voltage circuits
✓ Circuit breaker protection
✓ Residual current device (RCD)
✓ Proper enclosure (IP-rated)

230V CAN KILL - Take extreme precaution!
```

---

## 📝 Configuration Files

### secrets.yaml
```yaml
wifi_ssid: "YourNetworkName"
wifi_password: "YourNetworkPassword"
```

### water-tap.yaml
Complete ESPHome configuration file is provided separately.
Key sections:
- WiFi configuration with fallback AP
- Antenna auto-selection on boot
- GPIO pin definitions
- Relay interlocks and safety timers
- LED control logic
- Sound effect scripts
- Web server interface
- Statistics tracking
- Home Assistant API integration

---

## 🏠 Home Assistant Integration

### Automatic Discovery
Device automatically appears in Home Assistant when API encryption key is configured.

### Available Entities
- **Buttons**: Open Water, Close Water, Reset Statistics
- **Switches**: Buzzer Enabled, Restart Device
- **Sensors**: All statistics and monitoring values
- **Text Sensors**: Status displays
- **Binary Sensors**: Device online status

### Example Automation
```yaml
automation:
  - alias: "Water Tap Scheduler"
    trigger:
      - platform: time
        at: "08:00:00"
    action:
      - service: button.press
        target:
          entity_id: button.water_tap_open_water
      - delay: "00:30:00"  # Wait 30 minutes
      - service: button.press
        target:
          entity_id: button.water_tap_close_water
```

---

## 🔍 Troubleshooting

### Device Won't Boot
1. Check USB-C power supply (5V, 500mA minimum)
2. Try pressing RESET button
3. Enter bootloader mode and reflash firmware

### WiFi Won't Connect
1. Check WiFi credentials in secrets.yaml
2. Ensure 2.4GHz network (5GHz not supported)
3. Connect to fallback AP: "Water-Tap Fallback Hotspot"
4. Check blue LED status

### Valve Doesn't Operate
1. Verify 230V AC power to valve
2. Check relay module LED indicators
3. Test relays manually (listen for click)
4. Verify valve wiring (3-wire: Common/Open/Close)
5. Check safety lockout countdown (must be 0)

### LEDs Don't Light Up
1. Check LED polarity (cathode to GND)
2. Verify current-limiting resistors (220Ω recommended)
3. Test GPIO outputs with multimeter
4. Check water state in web interface

### No Sound from Buzzer
1. Verify buzzer is passive type (not active)
2. Check "Buzzer Enabled" switch is ON
3. Use "Test Buzzer Sounds" button
4. Verify GPIO8 PWM output with oscilloscope

### Statistics Not Saving
1. Check flash write interval (default 5 minutes)
2. Verify device isn't rebooting frequently
3. Allow time for automatic save cycle

---

## 📚 Additional Resources

### Documentation
- **XIAO ESP32C6 Guide**: [Seeed Studio Wiki](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/)
- **Valve Datasheet**: [Tameson Product Page](https://tameson.nl/products/bw2-012-aw1-230ac-elektrische-kogelkraan-1-2inch-2-weg-230vac-3-punt)
- **ESPHome Docs**: https://esphome.io/
- **Home Assistant**: https://www.home-assistant.io/

### Support
- ESPHome Discord: https://discord.gg/KhAMKrd
- Home Assistant Forums: https://community.home-assistant.io/

---

## ⚖️ License

This project is provided as-is for educational and personal use.

### Disclaimer
```
⚠️  IMPORTANT SAFETY NOTICE  ⚠️

This project involves:
- High voltage (230V AC) electrical work
- Water control systems
- Automated mechanical devices

The creator assumes NO LIABILITY for:
❌ Electrical shock or electrocution
❌ Water damage or flooding
❌ Property damage
❌ Personal injury
❌ Device malfunction
❌ Any other damages or losses

By using this project, you agree:
✓ You have the necessary electrical qualifications
✓ You understand the risks involved
✓ You will follow all local electrical codes
✓ You will implement proper safety measures
✓ You take full responsibility for implementation

USE AT YOUR OWN RISK!
```

---

## 📊 Project Statistics

**Total Development Time**: ~8 hours  
**Code Lines**: ~800 lines (YAML + embedded C++)  
**Features Implemented**: 25+  
**Safety Features**: 4 independent systems  
**GPIO Pins Used**: 10 of 11 available  
**Sound Effects**: 7 unique audio patterns  
**Statistics Tracked**: 5 metrics with persistence

---

## 🎯 Quick Start Guide

1. **Hardware**: Connect XIAO ESP32C6 to relay module and valve
2. **Software**: Flash ESPHome configuration via USB
3. **Network**: Device connects to WiFi automatically
4. **Access**: Open web interface at device IP
5. **Test**: Use "Test Buzzer Sounds" and try manual operation
6. **Monitor**: Check all safety features are working
7. **Deploy**: Install in final location with proper enclosure

**🎉 Ready to use!** Press buttons or use web interface to control water tap.

---

**Version**: 1.0.0  
**Last Updated**: 2026-01-01  
**Firmware**: ESPHome 2024.x compatible  
**Hardware Revision**: XIAO ESP32C6 v1.0

**Made with ❤️ and ⚡ by the ESPHome Community**
