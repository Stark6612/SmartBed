# Smart Bed V2 — Itemized Budget (Verified)

**Project:** AI-Powered Multimodal Contactless Patient Monitoring & Clinical Decision Support System  
**Document:** Smart Bed V2 Research Prototype — Verified Itemized Budget  
**Location:** Coimbatore, Tamil Nadu, India  
**Funding Limit:** ₹1,00,000  
**Prepared / Verified:** August 2026  
**Updated Total:** ₹63,740  

> All prices are **verified / corrected** as per the Budget Verification Report (BudgetVerification.md).  
> Items marked ⚠️ require a supplier quotation before final procurement.  
> Items marked 🏛️ should be accessed through institutional resources, not purchased.

---

## Section A — Core Hardware

| # | Item | Required Specification | Recommended Model | Purpose / Why It Is Used / Where It Is Used | Unit Price (₹) | Qty | Total Price (₹) |
|---|---|---|---|---|---:|---:|---:|
| 1 | mmWave Radar Module | 60 GHz FMCW, respiratory rate + heart rate micro-motion extraction, UART output, 3.3 V/5 V compatible, 0.4–1.5 m effective vital-sign range | **HLK-LD6002** (Hi-Link, 60 GHz vital sign FMCW radar) — replaces originally specified HLK-LD2450 which cannot extract respiratory rate from a stationary patient | Primary non-contact physiological sensor. Extracts sub-mm chest-wall displacement caused by breathing to estimate **respiratory rate** and attempt heartbeat-related measurements. Mounted at the headboard directed toward the patient's chest (~0.5–0.9 m distance). Used in published hospital-bed vital-sign monitoring research. | 2,200 | 1 | 2,200 |
| 2 | Velostat Pressure Sensor Sheet | Piezoresistive conductive (Velostat / Linqstat) sheet, minimum 280×280 mm per sheet | Velostat / Linqstat standard 11″×11″ piezoresistive sheet | Four sheets tile the mattress surface (~60 cm × 60 cm covering torso + lower body) to form a **DIY pressure sensor matrix**. Provides spatial pressure distribution maps for body position estimation, bed occupancy detection, visitor / second-occupant detection, and body movement tracking. Low-cost research-standard approach vs. ₹50,000+ commercial pressure mats. | 600 | 4 | 2,400 |
| 3 | Conductive Electrode Tape (Matrix Material) | 5 mm width conductive fabric / copper tape, 10 m roll | Conductive copper fabric adhesive tape / adhesive copper foil tape | Row-column electrode grid material applied to Velostat sheets to construct the pressure matrix. Required for the matrix to function — creates the scannable row and column conductors that allow individual cell pressure values to be read. | 450 | 2 | 900 |
| 4 | Load Cell 50 kg | Half-bridge aluminium body load cell, 50 kg capacity | Generic 50 kg half-bridge aluminium load cell | One per bed leg (4 total). Two full-bridge pairs formed from four half-bridge cells. Measures **total patient weight**, enables bed occupancy detection, visitor / second-occupant detection (weight delta), and bed-exit monitoring. Explicitly specified in the project document as a core sensing modality. | 100 | 4 | 400 |
| 5 | Thermal Camera — Spatial Array | MLX90640 IR thermal array, 32×24 pixels, 55° FOV, I2C interface, 3.3 V / 5 V compatible | **MLX90640** IR thermal camera breakout (7Semi or Waveshare variant) | Overhead sensor for **spatial thermal mapping** of the patient across the mattress surface. Provides body-position estimation, occupancy detection via thermal footprint, and temperature zone monitoring over time. 32×24 px gives sufficient spatial data for a hospital bed footprint. Mounted on overhead arm above patient upper body. Note: ±1.5°C accuracy — supplemented by MLX90614 (Item 5B) for accurate point readings. | 5,000 | 1 | 5,000 |
| 5B | Point Temperature Sensor | Melexis MLX90614, single-pixel IR thermometer, ±0.2°C accuracy, I2C, 3.3 V compatible; BCC variant (90° FOV) or DCH variant (35° FOV) | **Melexis MLX90614ESF-BCC** (or DCH variant) | Supplementary **high-accuracy point temperature sensor** for clinical-grade skin temperature readings (±0.2°C vs ±1.5°C for MLX90640). Aimed at patient forehead/chest from headboard. Provides the accurate, publishable temperature measurement; complements the MLX90640 spatial heatmap. Also used to validate the MLX90640's readings during calibration. The MLX90640 alone cannot reliably report a clinical temperature figure. | 700 | 1 | 700 |
| 6 | Raspberry Pi 5 (8 GB) | RPi 5, 8 GB LPDDR4X RAM, BCM2712 quad-core, full GPIO header | **Raspberry Pi 5 — 8 GB** (official board) | Primary **edge computing and AI inference platform**. Runs Python sensor fusion engine, AI inference (PyTorch / Scikit-learn), FastAPI backend, MQTT broker, and SQLite database simultaneously. 8 GB RAM is required for real-time AI inference alongside continuous multi-sensor data acquisition. Explicitly specified in the project document. | 20,000 | 1 | 20,000 |
| 7 | Raspberry Pi 5 Active Cooler | Official RPi 5 active cooler (fan + heatsink clip-on) | **Official Raspberry Pi 5 Active Cooler** | Required for sustained AI inference workloads without thermal throttling on the Pi 5. Clips directly onto BCM2712 and memory; official cooler is mechanically compatible with the RPi 5 acrylic case. | 520 | 1 | 520 |
| 8 | MicroSD Card 64 GB A2 | 64 GB, A2 Class 10 rating, microSD | **SanDisk Extreme 64 GB** | Primary OS and operating software storage for Raspberry Pi 5. A2 Application Performance Class rating required for the random I/O performance demanded by simultaneous live database writes during multi-sensor data collection sessions. | 2,800 | 1 | 2,800 |
| 9 | Raspberry Pi 5 Official Power Supply | Official Raspberry Pi 27 W USB-C PD supply, India plug, 5.1 V / 5 A | **Official Raspberry Pi 27 W USB-C Power Supply** (India plug) | Official 5.1 V / 5 A PD supply required for stable Raspberry Pi 5 operation with multiple USB peripherals and GPIO sensors active simultaneously. Unofficial supplies cause undervoltage throttling during continuous sensor collection. | 1,200 | 1 | 1,200 |
| 10 | ESP32 Development Board | ESP32-WROOM-32, 38-pin, CP2102 USB-to-UART, Wi-Fi + BLE | **ESP32-WROOM-32 38-pin dev board** (CP2102 variant) | Microcontroller handling HX711 load-cell ADC reading and CD74HC4067 pressure matrix multiplexer scanning. Publishes sensor data to Raspberry Pi via MQTT over Wi-Fi. Reduced from 2× (original budget) to 1× — a single ESP32 is sufficient for the prototype stage; LD6002 radar UART connects directly to the Raspberry Pi serial port. | 450 | 1 | 450 |
| 11 | HX711 Load Cell ADC Module | HX711 24-bit ADC breakout for load cells | **HX711 Load Cell Amplifier Module** breakout | Converts analogue half-bridge load cell signals to digital readings for the ESP32. Two modules: one per full-bridge pair (two pairs from four half-bridge cells). Industry-standard, reliable, low-cost load cell ADC interface. | 70 | 2 | 140 |
| 12 | CD74HC4067 16-Channel Analog Multiplexer | 16-channel analogue/digital mux, 2.54 mm headers, 3.3 V/5 V compatible | **CD74HC4067 16-channel mux breakout** | Scans the pressure matrix row-column grid without exceeding the ESP32's limited analogue pin count. Three modules allow scanning a ~12×12 pressure matrix grid. Standard research approach for DIY Velostat matrix scanning. | 60 | 3 | 180 |
| 13 | ADS1115 16-bit ADC Module | 4-channel 16-bit I2C ADC breakout | **ADS1115 16-bit I2C ADC breakout module** | High-resolution (16-bit) ADC for pressure matrix analogue readings where the ESP32's built-in 12-bit ADC is insufficient to detect fine pressure gradients between occupied / unoccupied cells. | 150 | 2 | 300 |
| 14 | Breadboards & Jumper Wires | Full-size solderless breadboard ×2 + 120-piece jumper wire assortment (M-M / M-F / F-F) | Standard solderless breadboard set + jumper wire assortment | Initial prototyping and system integration wiring before final soldered permanent connections. Essential for rapid iteration, debugging, and sensor-interface testing during the development phase. | 400 | 1 set | 400 |
| 15 | Passive Components Assortment | 600-piece resistor assortment + 200-piece ceramic capacitor assortment | Standard mixed-value resistor + capacitor assortment pack | Voltage divider networks for pressure matrix column signals, decoupling capacitors for ADC supply lines, and pull-up / pull-down resistors for I2C and UART lines. Required supporting electronics for signal conditioning throughout the system. | 350 | 1 set | 350 |
| 16 | Logic Level Converter Module | 4-channel bi-directional I2C / SPI logic level shifter (3.3 V ↔ 5 V) | **Bi-directional 4-channel Logic Level Converter module** | Safe voltage-level translation between 5 V ESP32 GPIO and 3.3 V sensors (MLX90640 I2C lines, ADS1115 I2C lines). Prevents component damage from voltage mismatch at signal interfaces. | 40 | 2 | 80 |
| 17 | 12 V 5 A Regulated DC Power Supply | Regulated 12 V DC, 5 A output, terminal block connection | Generic regulated 12 V / 5 A DC bench supply with terminal block — local Coimbatore electronics market | Centralised power source for ESP32 boards, CD74HC4067 multiplexers, and ADS1115 ADC modules, stepped down via LM2596 buck converters. Reduces wiring complexity and supply noise vs. individual USB power cables per module. | 500 | 1 | 500 |
| 18 | LM2596 Adjustable Buck Converter | Adjustable step-down DC-DC buck converter, input 4.5–40 V, 1.5 A output | **LM2596 DC-DC adjustable step-down buck module** | Steps the 12 V centralised supply down to 5 V / 3.3 V for individual sensor sub-circuits. Three modules provide independently regulated rails for ESP32, mux modules, and ADC modules, reducing supply noise. | 50 | 3 | 150 |
| 19 | ~~External SSD~~ — **REMOVED** | — | — | **Not purchased.** A laptop will be present at every experiment session for monitoring. Session data is streamed and stored directly on the laptop (via SSH / shared folder / USB). The 64 GB A2 microSD (Item 8) handles per-session buffer storage. The 32 GB USB flash drive (V7) covers supervisor backup. Cloud backup (institutional OneDrive / Google Drive) provides redundancy. **Saving: ₹15,000.** | — | — | 0 |
| 20 | CH340 USB-to-UART Debug Cable | CH340-based USB-to-UART TTL serial cable | **CH340 USB-to-UART TTL serial debug cable** | ESP32 serial debugging and firmware flashing during development. Separate from the CP2102 module (Item NEW-2) which is used exclusively for LD6002 radar configuration. | 175 | 1 | 175 |
| NEW-1 | Raspberry Pi 5 Protective Case | GPIO-accessible acrylic or polycarbonate enclosure for Raspberry Pi 5, compatible with active cooler | **Waveshare Clear Acrylic Case for Raspberry Pi 5** (removable GPIO cover) | Physical protection for the Raspberry Pi 5 board on a dynamic prototype platform subject to vibration, dust, and accidental contact during experiment setup and repositioning. Not included in original budget — identified as a missing component during verification. | 1,000 | 1 | 1,000 |
| NEW-2 | CP2102 USB-to-UART Module (LD6002 config) | USB-to-UART TTL module, CP2102 chip, micro-USB or USB-C | **CP2102 USB-to-UART TTL breakout module** | Dedicated UART adapter for configuring the HLK-LD6002 radar during initial setup (output format selection, sensitivity tuning) directly from a laptop, without routing through the Raspberry Pi. Separate from the CH340 debug cable (Item 20) which is used for ESP32 flashing only. Not included in original budget — identified as a missing component during verification. | 120 | 1 | 120 |

**Hardware Subtotal: ₹39,965**

---

## Section B — Prototype Fabrication

| # | Item | Required Specification | Recommended Model | Purpose / Why It Is Used / Where It Is Used | Unit Price (₹) | Qty | Total Price (₹) |
|---|---|---|---|---|---:|---:|---:|
| F1 | Hospital Bed / Metal Cot | Standard single-person metal cot or iron hospital bed frame | Standard hospital-grade or commercial single-person metal cot | Mechanical mounting platform for all sensors. The sensing value lies entirely in the integrated sensor hardware. A secondhand or departmental cot is preferred; if unavailable, purchase from local market. | 5,000 | 1 | 5,000 |
| F2 | Foam Mattress | Standard 75×36 inch foam mattress, 4 inch thick | Standard foam mattress | Required to simulate real bed conditions for pressure matrix deformation and radar target positioning. | 2,000 | 1 | 2,000 |
| F3 | Headboard Radar Mount Bracket | MS (mild steel) flat bar, drilled + welded, adjustable mounting for radar module at headboard | Custom fabrication — college mechanical workshop | Holds the HLK-LD6002 radar module at the correct headboard position directed toward the patient's chest at ~0.5–0.9 m distance. Angle-adjustable for optimal vital-sign sensing range. | 500 | 1 | 500 |
| F4 | Overhead Thermal Camera Arm | Aluminium extrusion arm + L-bracket + M5 bolts, adjustable height | Custom aluminium extrusion arm — college workshop / purchase | Positions the thermal camera directly above the patient's upper body as specified in the project document. Height-adjustable to set correct field-of-view coverage. | 500 | 1 | 500 |
| F5 | Load Cell Mounting Footpad Plates | 4× aluminium sandwich footpad plates, M6 threaded rods + nuts, 3 mm aluminium sheet | Custom fabrication — college mechanical workshop (4 units) | Each bed leg rests on a load-cell sandwich plate. Transfers the full bed weight evenly onto each load cell's active sensing area without mechanical eccentricity errors. Required for accurate weight measurement. | 700 | 1 set (4 units) | 700 |
| F6 | Cable Conduit & Management | Spiral cable wrap 10 m + adhesive cable clips + cable tie packs | Standard spiral wrap + adhesive cable clips + zip tie assortment | Organises all sensor wiring across the bed frame and to the electronics enclosure. Prevents cable damage, tangling, and accidental disconnection during prototype operation and repositioning. | 250 | 1 | 250 |
| F7 | Project Enclosure Box | ABS plastic enclosure, 200×120×75 mm | Standard ABS project enclosure | Protects the ESP32 board, HX711 modules, and LM2596 power electronics from mechanical damage, dust, and accidental contact during prototype operation. Two enclosures separate MCU subsystem from power subsystem. | 180 | 2 | 360 |
| F8 | Fasteners & Standoff Assortment | M4/M5 bolts, nuts, washers + nylon PCB standoffs assortment | Standard M4/M5 fastener + nylon standoff assortment pack | General assembly hardware for sensor mounting, PCB standoff spacing inside enclosures, and mechanical assembly of load cell sandwich plates and camera arm brackets. | 200 | 1 set | 200 |
| F9 | Wire & JST Connectors | 20 m flexible 22 AWG copper wire (assorted colours) + 20× JST-PH 2-pin connectors | 22 AWG flexible hookup wire + JST-PH 2-pin connector set | Sensor wiring harness for all connections between sensors, ADC modules, and electronics enclosure. JST connectors provide detachable, maintenance-friendly connections for transport or reconfiguration without cutting wire. | 350 | 1 | 350 |
| F10 | Soldering Consumables | 60/40 solder wire 50 g + flux pen + solder wick | Standard 60/40 solder + flux pen + solder wick set | Final assembly soldering for HX711 load cell connections, pressure matrix electrode routing, connector pin crimping, and permanent PCB connections. Required for mechanically robust final assembly. | 300 | 1 | 300 |

**Fabrication Subtotal: ₹10,160**

---

## Section C — Data & Experimentation

| # | Item | Required Specification | Recommended Model | Purpose / Why It Is Used / Where It Is Used | Unit Price (₹) | Qty | Total Price (₹) |
|---|---|---|---|---|---:|---:|---:|
| D1 | Calibration Weights Set | 5 kg cast-iron calibration weight set (1 kg × 5) | Standard 5 kg cast-iron calibration weight set | Load cell tare and calibration — known weights are applied to validate load cell readings and characterise linearity. Also used for mapping the pressure sensor response to known applied forces. Produces the calibration curve required for trustworthy, publishable weight measurements. | 700 | 1 set | 700 |
| D2 | Anti-Static / EVA Foam Backing Sheet | 5 mm EVA foam sheet, 60×120 cm | 5 mm EVA foam sheet (anti-static or standard) | Controlled-stiffness backing layer placed beneath the Velostat pressure matrix. Ensures reproducible deformation behaviour (consistent baseline compliance) during pressure calibration and across volunteer sessions, making results comparable between sessions. | 150 | 2 | 300 |
| D3 | Thermal Reference Target | Copper plate + adhesive NTC thermistor + small heater, assembled for known-temperature thermal camera calibration | Custom assembly (copper plate + NTC thermistor + heater) ⚠️ | Validates MLX90640 thermal camera temperature readings against a known-temperature reference surface before volunteer trials. Characterises the camera's absolute temperature accuracy and allows corrections to be applied. | 400 ⚠️ | 1 | 400 |
| D4 | Reference Digital Thermometer | Medical-grade digital infrared forehead thermometer | Institutional access preferred (college biomedical / nursing lab) 🏛️ | Provides per-session reference surface temperature for thermal camera validation. Used alongside the MLX90640 to record reference temperature readings for each volunteer at session start and end. **Institutional access recommended; budget reserved if unavailable.** | 700 🏛️ | 1 | 700 |
| D5 | USB Desk Fan | Standard 5 V USB desk fan | Standard USB desk fan | Environmental interference testing for thermal camera and radar subsystems. Fan creates air movement and thermal variation to test system robustness — directly addresses the "environmental interference" technical challenge listed in the project document. | 350 | 1 | 350 |
| D6 | Experimental Documentation & Printing | A4 data collection forms, session log templates, printed circuit diagrams, data sheets | Printed forms + circuit diagram printouts (local print shop) | Research documentation for each experimental session. Session logs capture volunteer ID, session timing, reference measurements, and system-state notes. Required for experimental reproducibility and ethical audit trail. | 400 | 1 | 400 |
| D7 | Volunteer Session Consumables | Disposable mattress protector covers (pack of 10), gloves (box of 50), hand sanitiser | Disposable mattress protectors + exam gloves + hand sanitiser | Hygiene consumables for non-invasive human volunteer experimental sessions. Disposable covers are placed on the mattress between sessions. Required for ethical conduct of human-participant experiments and volunteer welfare. | 500 | 1 | 500 |

**Data & Experimentation Subtotal: ₹3,350**

---

## Section D — Validation

| # | Item | Required Specification | Recommended Model | Purpose / Why It Is Used / Where It Is Used | Unit Price (₹) | Qty | Total Price (₹) |
|---|---|---|---|---|---:|---:|---:|
| V1 | Reference Breath Counter (Stopwatch) | Digital stopwatch with split-lap function | Standard digital sports stopwatch | Gold-standard reference for respiratory rate validation. A trained observer manually counts breaths over 60-second windows simultaneously with the radar system. Simple, inexpensive, and scientifically rigorous reference for respiratory rate comparison and radar accuracy assessment. | 200 | 1 | 200 |
| V2 | Reference Platform Weighing Scale | Digital body weight scale, ≥150 kg capacity, 0.1 kg resolution | **Dr. Trust / HealthSense digital weighing scale** 🏛️ | Validates load-cell total weight readings against a calibrated reference. **Prefer institutional access (college biomedical / physiotherapy / hospital calibrated scale) — purchase only if unavailable.** Budget reserved as a fallback. Source: Amazon India / Flipkart, verified ₹1,000–₹1,500 range. | 1,200 🏛️ | 1 | 1,200 |
| V3 | Reference Spirometer / Peak Flow Meter | Manual peak flow meter or incentive spirometer (3-ball type) | **Manual peak flow meter (Rossmax / LungChek)** or standard incentive spirometer 🏛️ | Comparative respiratory data alongside the radar respiration signal for correlation analysis. Records reference respiratory effort values during volunteer sessions. **Prefer institutional access (college biomedical lab / hospital) — purchase only if unavailable.** Source: Amazon India / 1mg, verified ₹500–₹900 range. | 600 🏛️ | 1 | 600 |
| V4 | Reference Pulse Oximeter (SpO₂ + HR) | Fingertip SpO₂ + heart rate monitor, OLED display | **Contec CMS50D fingertip pulse oximeter** 🏛️ | Reference heart rate recording during radar-HR correlation experiments. Not claimed as a system replacement — used only to assess quality of radar-derived heartbeat signals alongside SpO₂ readings. **Prefer institutional access (college nursing lab / hospital) — purchase only if unavailable.** Source: Amazon India / Flipkart, verified ₹850–₹1,300 range. | 1,000 🏛️ | 1 | 1,000 |
| V5 | Volunteer Honoraria | Nominal cash honoraria for healthy volunteer participants (non-invasive sessions) | Cash honoraria — ₹200 per session × ~10 sessions | Ethical recognition for volunteer participants. Required for ethical experimental conduct and volunteer recruitment. Institutional ethics clearance (IRB) must be obtained before any volunteer sessions begin. | 200 | 10 sessions | 2,000 |
| V6 | Ethics Documentation Printing | Informed consent forms, ethics application, data privacy forms — printed sets | Printed forms — local print shop | Institutional ethics (IRB) clearance documentation. Mandatory before any human-participant data collection begins. Covers informed consent forms, data handling policy, and ethics committee submission package. | 500 | 1 | 500 |
| V7 | Validation Backup Storage (USB Flash Drive) | 32 GB USB flash drive, USB 3.0 | Standard 32 GB USB 3.0 flash drive | Backup of the complete validation dataset for supervisor review, result verification, and research paper preparation. Separate from the external SSD (Item 19) which is the primary data store on the prototype. | 250 | 1 | 250 |

**Validation Subtotal: ₹5,750**  
> 🏛️ *Items V2, V3, V4 are priced as a fallback — institutional access is strongly preferred. If all three are sourced through college labs, validation cost reduces by ₹2,800 to ₹2,950.*

---

## Budget Summary

| Category | Amount (₹) |
|---|---:|
| Core Hardware — Section A (Items 1–20 + 5B + NEW-1, NEW-2; SSD removed) | 39,965 |
| Prototype Fabrication — Section B (F1–F10) | 10,160 |
| Data & Experimentation — Section C (D1–D7) | 3,350 |
| Validation — Section D (V1–V7, incl. conditional V2/V3/V4) | 5,750 |
| **Procurement Subtotal** | **59,225** |
| Contingency (~8% of procurement subtotal) | **4,515** |
| **TOTAL** | **₹63,740** |
| **Surplus vs. ₹1,00,000 cap** | **₹36,260 uncommitted** |
| *If V2/V3/V4 sourced institutionally (best case)* | *₹60,940 total* |

---

> **⚠️ Critical Note — Radar Module Replacement:** The originally specified HLK-LD2450 (24 GHz, ₹650) has been **replaced** by the **HLK-LD6002** (60 GHz vital-sign FMCW radar, ₹2,200). The LD2450 is a motion-tracking sensor and **cannot extract respiratory rate from a stationary patient** — which is a primary research objective. This replacement is **mandatory** before funding submission.

> **📌 Thermal Sensor Update:** MLX90614 (Item 5B, ₹700) added as a supplementary point temperature sensor. The MLX90640 alone has ±1.5°C accuracy which is insufficient for clinical temperature reporting. The MLX90614 (±0.2°C) provides the accurate single-point forehead/chest temperature needed for publishable fever-detection results, while the MLX90640 continues to provide spatial thermal mapping and occupancy detection.

> **💾 SSD Removed:** External SSD (Item 19) removed from the budget. A laptop present at every session provides all necessary local storage. Net saving: ₹15,000. Budget impact of all changes: −₹14,300 total reduction from previous version.

---

*Document prepared: August 2026*  
*Smart Bed V2 — Verified Itemized Budget | Coimbatore, Tamil Nadu*  
*Source documents: Budget.md + BudgetVerification.md + Smart Bed V2.pdf*
