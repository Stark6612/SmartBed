# Budget

**Project:** AI-Powered Multimodal Contactless Patient Monitoring & Clinical Decision Support System  
**Document:** Smart Bed V2 Research Prototype Budget  
**Location:** Coimbatore, Tamil Nadu, India  
**Funding Limit:** ₹1,00,000  
**Prepared:** August 2026  

---

## 1. Budget Objective

This budget funds the construction of a **research prototype** of the AI-Powered Multimodal Contactless Patient Monitoring & Clinical Decision Support System described in *Smart Bed V2.pdf*.

The objective is **not** to build a production-ready or hospital-certified smart bed. The objective is to build a sufficiently functional prototype that:

- Integrates the four core sensor modalities described in the project document (mmWave radar, pressure sensor matrix, load cells, thermal camera) into a single hospital bed platform.
- Demonstrates real-time multimodal sensor fusion with AI interpretation.
- Generates measurable experimental data (respiratory rate estimates, pressure distribution maps, weight readings, surface temperature readings, bed occupancy and visitor detection).
- Is testable against reference measurements to enable initial clinical validation.
- Produces a published record of experimental evidence suitable for a proof-of-concept research paper.

The funding path is:

> **₹1,00,000 → Research Prototype → Experimental Data → Validation → Proof of Concept**

---

## 2. Prototype Scope

The funded prototype is expected to demonstrate the following capabilities to the extent technically feasible:

| Capability | Expected Outcome |
|---|---|
| Bed occupancy detection | Binary presence/absence detection via load cells + pressure matrix |
| Visitor / additional occupant detection | Weight-delta + pressure-distribution fusion detects second occupant |
| Body movement detection | Pressure matrix temporal change; radar motion flag |
| Body position estimation | Pressure centroid and distribution map from sensor matrix |
| Pressure distribution | Spatial pressure map across mattress surface |
| Patient weight estimation | Load cell sum with tare calibration |
| Respiratory rate estimation | mmWave Doppler chest-motion signal, validated against reference observer count |
| Heartbeat-related radar measurement | Attempted as research objective; feasibility documented |
| Surface temperature measurement | Thermal camera skin-surface reading, trended over time |
| Multimodal sensor fusion | Software fusion engine on Raspberry Pi 5 combining all four sensors |
| Measurement confidence assessment | AI validity gate: radar data accepted only when patient is still + single occupant confirmed |
| Basic clinical decision-support output | Priority score + reason + confidence percentage on dashboard |
| Experimental validation | Comparison with reference observer counts, spirometer readings, and reference weighing scale |

**Explicitly out of scope for this prototype:**  
The prototype does not claim to replace or replicate ECG, blood pressure monitoring, or pulse oximetry (SpO₂). These limitations are documented in the project document and remain acknowledged research limitations.

---

## 3. Detailed Item-Wise Budget

> **Notes on Source Types:**  
> - **Indian retailer (verified listing):** Price from named Indian electronics retailer, available at time of research.  
> - **Estimated / Quote Required:** No specific verified Indian listing found; price is a market estimate. Final procurement must verify.  
> - **Institutional Access Recommended:** Item should preferably be accessed through a college lab, hospital, or research collaborator rather than purchased.

| # | Category | Item | Specification / Model | Qty | Unit Cost (₹) | Total (₹) | Purchase / Access / Fabrication | Why This Cost? | Source |
|---|---|---|---|---:|---:|---:|---|---|---|
| 1 | Sensors | mmWave Radar Module | Hi-Link HLK-LD2450, 24 GHz, multi-target tracking, UART, 5 m range | 1 | 650 | 650 | Purchase | Low-cost 24 GHz FMCW radar sufficient for prototype respiration & occupancy detection. LD2450 supports multi-target tracking, enabling visitor detection. Full eval kits (TI IWR1443BOOST) cost ₹46,000+; LD2450 at ~₹650 delivers the core sensing capability for the research objective. | [Robu.in](https://robu.in) / [Rajguru Electronics](https://rajguruelectronics.com) — verified ₹430–₹800 range |
| 2 | Sensors | Pressure Sensor Matrix Material | Velostat / Linqstat piezoresistive conductive sheet, 30 cm × 30 cm minimum per sheet | 4 | 600 | 2,400 | Purchase | Four sheets tile a single-bed-zone sensing area (~60 cm × 60 cm covering torso + lower body). Velostat DIY matrix is the standard low-cost research approach for pressure mapping. Commercial pressure mat systems cost ₹50,000+. | [Thingbits Electronics](https://thingbits.in) / [MG Super Labs](https://mgsuperlabs.co.in) — verified ₹400–₹700 per sheet |
| 3 | Sensors | Matrix Electrode Material | Conductive fabric tape 5 mm width, 10 m roll | 2 | 350 | 700 | Purchase | Row-column electrode grid on Velostat for pressure matrix construction. Standard DIY matrix material; required for the matrix to function. | [Robu.in](https://robu.in) / local Coimbatore electronics market — Estimated |
| 4 | Sensors | Load Cells (50 kg) | Half-bridge 50 kg aluminium body load cell | 4 | 100 | 400 | Purchase | One per bed leg. Four cells in two full-bridge pairs provide total weight measurement for patient weight, occupancy, visitor detection, and bed exit monitoring. Explicitly identified as low-cost and reliable in project document. | [Robu.in](https://robu.in) / [Robocraze](https://robocraze.com) — verified ₹50–₹150 per cell |
| 5 | Sensors | Thermal Camera — Spatial Array | MLX90640 IR thermal array, 32×24 pixels, 55° FOV, I2C, 3.3 V/5 V | 1 | 5,000 | 5,000 | Purchase | Spatial thermal mapping of the supine patient: body-position estimation, presence detection, and temperature zone monitoring over time. 32×24 px is appropriate for a hospital bed footprint. Medical-grade thermal cameras cost ₹2,00,000+. MLX90640 is widely used in contactless temperature research prototypes. Note: ±1.5°C accuracy — supplemented by MLX90614 (Item 5B) for accurate point readings. | [Robocraze](https://robocraze.com) / [Robu.in](https://robu.in) — verified ₹4,589–₹5,200 range |
| 5B | Sensors | Point Temperature Sensor | Melexis MLX90614ESF-BCC (90° FOV) or DCH (35° FOV), ±0.2°C accuracy, I2C, 3.3 V | 1 | 700 | 700 | Purchase | High-accuracy single-pixel IR thermometer for clinical-grade skin temperature readings. Aimed at patient forehead/chest from headboard. Provides the accurate, peer-review-defensible temperature measurement (±0.2°C) that the MLX90640 cannot deliver (±1.5°C). Also used to cross-validate MLX90640 readings during calibration. | [Robu.in](https://robu.in) / local market — estimated ₹600–₹800 |
| 6 | Processing | Raspberry Pi 5 (8 GB) | Raspberry Pi 5, 8 GB LPDDR4X RAM, BCM2712 quad-core | 1 | 9,500 | 9,500 | Purchase | Primary edge-computing platform. Runs Python sensor fusion, AI inference (PyTorch/Scikit-learn), FastAPI backend, and MQTT broker simultaneously. 8 GB RAM required for real-time AI inference. Explicitly specified in project document. | [ThinkRobotics](https://thinkrobotics.com) / [Robu.in](https://robu.in) — verified ₹8,200–₹9,999 range |
| 7 | Processing | Raspberry Pi 5 Active Cooler | Official Raspberry Pi 5 active cooler (fan + heatsink clip-on) | 1 | 460 | 460 | Purchase | Required for sustained AI inference workloads without thermal throttling on the Pi 5. | [Robu.in](https://robu.in) — verified ₹430–₹490 range |
| 8 | Processing | MicroSD Card 64 GB A2 | SanDisk / Samsung 64 GB A2 Class 10 microSD | 1 | 900 | 900 | Purchase | Primary OS and software storage for Raspberry Pi 5. A2-rated for random I/O performance required for live database writes during data collection. | [Amazon India](https://amazon.in) / [Flipkart](https://flipkart.com) — verified ₹700–₹1,000 range |
| 9 | Processing | Raspberry Pi 5 Official Power Supply | Official Raspberry Pi 27 W USB-C PD power supply, India plug | 1 | 1,200 | 1,200 | Purchase | Official 5.1 V / 5 A supply required for stable Pi 5 operation with multiple USB and sensor peripherals. Unofficial supplies cause instability during continuous sensor collection. | [Robu.in](https://robu.in) / [Electropi.in](https://electropi.in) — verified ₹1,100–₹1,300 range |
| 10 | Microcontrollers | ESP32 Development Boards | ESP32 WROOM-32 38-pin dev board, CP2102 USB-to-UART, Wi-Fi + BLE | 2 | 450 | 900 | Purchase | Two ESP32 boards: one for HX711 load-cell ADC + pressure matrix multiplexer scanning; second for MQTT publishing to Raspberry Pi and system redundancy. Explicitly specified in project document. | [Robu.in](https://robu.in) / [Robocraze](https://robocraze.com) — verified ₹399–₹489 per board |
| 11 | Electronics | HX711 Load Cell Amplifier | HX711 24-bit ADC load cell amplifier breakout module | 2 | 80 | 160 | Purchase | Two modules read two full-bridge load-cell pairs (one per pair). Standard, reliable, low-cost load cell ADC interface. | [Robu.in](https://robu.in) / [Robocraze](https://robocraze.com) — verified ₹40–₹100 per module |
| 12 | Electronics | 16-Channel Analog Multiplexer | CD74HC4067 16-channel analog/digital mux breakout | 3 | 75 | 225 | Purchase | Scans the pressure matrix row-column grid without exceeding ESP32 analog pin count. Three modules allow scanning a ~12×12 grid. Standard research matrix scanning approach. | [ElectronicsComp](https://electronicscomp.com) / [Electropi.in](https://electropi.in) — verified ₹42–₹80 per module |
| 13 | Electronics | ADS1115 16-bit ADC Module | ADS1115 4-channel 16-bit I2C ADC breakout | 2 | 200 | 400 | Purchase | High-resolution ADC for pressure matrix analog readings where the ESP32's internal 12-bit ADC is insufficient for detecting fine pressure gradients. | [Robu.in](https://robu.in) / [FlyRobo](https://flyrobo.in) — verified ₹148–₹250 per module |
| 14 | Electronics | Breadboards & Jumper Wires | Full-size solderless breadboard ×2, 120-piece jumper wire assortment (M-M/M-F/F-F) | 1 set | 350 | 350 | Purchase | Initial prototyping and system integration wiring before final soldered connections. Essential for rapid iteration during development phase. | [Robu.in](https://robu.in) — standard market price |
| 15 | Electronics | Passive Components Assortment | 600-piece resistor assortment + 200-piece ceramic capacitor assortment | 1 set | 250 | 250 | Purchase | Voltage divider networks for pressure matrix column signals, decoupling capacitors, pull-up/pull-down resistors. Required supporting electronics for signal conditioning. | [Robu.in](https://robu.in) / local Coimbatore electronics market |
| 16 | Electronics | Logic Level Converters | Bi-directional 4-channel I2C/SPI logic level shifter module | 2 | 80 | 160 | Purchase | Safe interface between 5 V ESP32 I/O and 3.3 V sensors (MLX90640, ADS1115) without risking component damage. | [Robu.in](https://robu.in) |
| 17 | Power | 12 V DC Power Supply | 12 V 5 A regulated DC bench supply with terminal block | 1 | 700 | 700 | Purchase | Centralised power for ESP32 boards, multiplexers, and ADC modules. Reduces complexity of individual USB power cables during prototype operation. | [Robu.in](https://robu.in) / local Coimbatore electronics market — Estimated / Quote Required |
| 18 | Power | DC-DC Buck Converter Modules | LM2596 adjustable step-down buck converter module, 1.5 A output | 3 | 60 | 180 | Purchase | Steps 12 V supply down to 5 V for individual sensor sub-circuits, reducing wiring complexity and supply noise. | [Robu.in](https://robu.in) / [Robocraze](https://robocraze.com) |
| — | Storage | ~~External SSD~~ — **REMOVED** | — | — | — | 0 | **Not purchased** | A laptop will be present at all experimental sessions for monitoring. Data is stored directly on the laptop via SSH / shared folder. The 64 GB A2 microSD (Item 8) buffers per-session data; the V7 USB flash drive provides supervisor backup. Cloud (institutional OneDrive/Google Drive) gives additional redundancy. **Saving: ₹5,500.** | — |
| 20 | Communication | USB-to-UART Debug Cable | CH340-based USB-to-UART TTL serial cable | 1 | 120 | 120 | Purchase | ESP32 serial debugging and firmware flashing without occupying the onboard USB port during deployment. | [Robu.in](https://robu.in) |

---

## 4. Hardware Budget

| Sub-Category | Items | Amount (₹) |
|---|---|---:|
| Sensors | mmWave radar, Velostat sheets ×4, conductive electrode tape ×2, load cells ×4, MLX90640 spatial thermal camera, MLX90614 point temperature sensor | 9,850 |
| Processing | Raspberry Pi 5 (8 GB) + active cooler + 64 GB microSD + 27 W power supply | 12,060 |
| Microcontrollers | 2× ESP32 WROOM-32 38-pin boards | 900 |
| Electronics | HX711 ×2, CD74HC4067 mux ×3, ADS1115 ×2, breadboards + jumpers, resistors/capacitors, logic level converters ×2 | 1,385 |
| Power | 12 V/5 A DC supply + 3× LM2596 buck converters | 880 |
| Communication | CH340 debug cable (external SSD removed — laptop storage used) | 120 |
| **Hardware Total** | | **₹25,195** |

---

## 5. Prototype Fabrication Budget

| # | Item | Specification | Qty | Unit Cost (₹) | Total (₹) | Purchase / Fabrication | Notes |
|---|---|---|---|---:|---:|---|---|
| F1 | Hospital bed / metal cot | Standard single-person metal cot or iron hospital bed frame | 1 | 0 | 0 | **Institutional Access** | Coordinate with department / college engineering lab to use existing cot. Purchasing a new hospital bed not required for a prototype. |
| F2 | Foam mattress | Standard 75×36 inch foam mattress, 4 inch thick | 1 | 1,500 | 1,500 | Purchase (only if departmental cot unavailable) | Required to simulate real bed conditions for pressure matrix and radar testing. Existing lab mattress preferred. |
| F3 | Headboard radar mount bracket | MS flat bar bracket, drilled + welded, for headboard radar module | 1 | 400 | 400 | Fabrication (college workshop) | Holds radar module at correct headboard position directed toward patient chest. |
| F4 | Overhead thermal camera arm | Aluminium extrusion arm + L-bracket + M5 bolts, adjustable above-bed mounting | 1 | 600 | 600 | Fabrication / Purchase | Positions thermal camera above patient upper body as described in project document. |
| F5 | Load cell mounting plates | 4× aluminium sandwich footpad plates, M6 threaded rods + nuts | 1 set | 500 | 500 | Fabrication (college workshop) | Each bed leg rests on a load-cell sandwich. Fabricated from 3 mm aluminium sheet. |
| F6 | Cable conduit & management | Spiral cable wrap 10 m + adhesive cable clips + cable tie packs | 1 | 250 | 250 | Purchase | Organises sensor wiring; prevents cable damage during prototype operation. |
| F7 | Project enclosure boxes | ABS plastic enclosure 200×120×75 mm | 2 | 180 | 360 | Purchase | Protects ESP32 + HX711 + power electronics from mechanical damage. |
| F8 | Fasteners & standoff assortment | M4/M5 bolts, nuts, washers, nylon PCB standoffs assortment | 1 | 200 | 200 | Purchase | General assembly hardware for sensor mounting. |
| F9 | Wire & connectors | 20 m flexible 22 AWG copper wire (assorted colours) + 20× JST-PH 2-pin connectors | 1 | 350 | 350 | Purchase | Sensor wiring harness. JST connectors allow detachable, maintenance-friendly sensor connections. |
| F10 | Soldering consumables | 60/40 solder wire 50 g + flux + solder wick | 1 | 300 | 300 | Purchase | Final assembly of HX711 connections, matrix electrode routing, and connector crimping. |
| **Fabrication Total** | | | | | **₹4,460** | | |

> **Note on Bed:** The hospital bed is a mechanical platform only. The sensing value lies entirely in the sensor hardware integrated into it. A secondhand cot or existing departmental cot is fully suitable.

---

## 6. Data & Experimentation Budget

| # | Item | Specification | Qty | Unit Cost (₹) | Total (₹) | Purpose |
|---|---|---|---|---:|---:|---|
| D1 | Calibration weights | 5 kg cast-iron calibration weight set (1 kg × 5) | 1 set | 700 | 700 | Load cell tare and calibration — apply known weights to validate load cell readings and characterise linearity. Also used for pressure sensor response mapping. |
| D2 | Anti-static foam backing | 5 mm EVA foam sheet 60×120 cm | 2 | 150 | 300 | Controlled-stiffness backing layer beneath Velostat matrix, ensuring reproducible deformation behaviour during pressure calibration. |
| D3 | Thermal reference target | Copper plate + adhesive NTC thermistor + small heater (assembled) for known-temperature thermal camera calibration | 1 | 400 | 400 | Validates MLX90640 temperature readings against a known-temperature reference before volunteer trials. Estimated / Quote Required. |
| D4 | Reference digital thermometer | Medical-grade digital infrared forehead thermometer | 1 | 700 | 700 | **Institutional Access Recommended** — use college biomedical/nursing lab unit if available. If unavailable, budget reserved. Provides per-session reference temperature for thermal camera validation. |
| D5 | USB desk fan | Standard 5 V / USB desk fan | 1 | 350 | 350 | Environmental interference testing — directly addresses the "environmental interference" technical challenge listed in the project document. Fan creates air movement and thermal variation to test system robustness. |
| D6 | Experimental documentation | A4 data collection forms, session log templates, printed circuit diagrams, data sheets | 1 | 400 | 400 | Research documentation for each experimental session. Required for reproducibility and ethical audit. |
| D7 | Volunteer session consumables | Disposable mattress protector covers (pack of 10), gloves (box of 50), hand sanitiser | 1 | 500 | 500 | Hygiene consumables for human volunteer experimental sessions. Required for ethical conduct of non-invasive experiments. |
| **Data & Experimentation Total** | | | | | **₹3,350** | |

---

## 7. Validation Budget

| # | Item | Specification | Qty | Unit Cost (₹) | Total (₹) | Purchase / Access | Purpose |
|---|---|---|---|---:|---:|---|---|
| V1 | Reference breath counter | Digital stopwatch for manual respiratory rate counting by trained observer | 1 | 200 | 200 | Purchase | Gold-standard reference for respiratory rate validation: trained observer manually counts breaths over 60-second windows simultaneously with radar. Inexpensive but scientifically rigorous. |
| V2 | Reference platform weighing scale | Medical calibrated platform scale, ≥150 kg capacity | 1 | 0 | 0 | **Institutional Access.** Use college/hospital calibrated weighing scale. | Validates load-cell total weight readings against a calibrated reference. No purchase required. |
| V3 | Reference spirometer | Portable incentive spirometer or peak flow meter | 1 | 0 | 0 | **Institutional Access.** College biomedical lab or hospital collaborator. | Comparative respiratory data alongside radar respiration signal for correlation analysis. |
| V4 | Reference pulse oximeter (SpO₂) | Fingertip SpO₂ + HR monitor | 1 | 0 | 0 | **Institutional Access.** Departmental / hospital SpO₂ probe. | Used only for reference HR recording during radar-HR correlation experiments. Not claimed as a system replacement. |
| V5 | Volunteer honoraria | Nominal honoraria for healthy volunteer participants (non-invasive sessions) | 1 | 2,000 | 2,000 | Expense | Ethical recognition for ~10 volunteer sessions (₹200/session). Required for ethical experimental conduct and volunteer recruitment. |
| V6 | Ethics documentation printing | Informed consent forms, ethics application, data privacy forms | 1 | 500 | 500 | Purchase | Institutional ethics clearance documentation. Mandatory before any human-participant data collection. |
| V7 | Validation backup storage | 32 GB USB flash drive for data sharing and backup with research supervisor | 1 | 250 | 250 | Purchase | Backup of validation dataset for supervisor review, result verification, and research paper preparation. |
| **Validation Total** | | | | | **₹2,950** | | |

---

## 8. Contingency

**Amount:** ₹4,245  
**As percentage of hardware cost:** ~14%

The contingency is intended to cover:

1. **Component failure during development** — At-risk components: ESP32 boards (ESD damage during matrix assembly), Velostat sheets (electrode tearing during iterative assembly and calibration).
2. **Price variation at procurement time** — Prices for imported components (MLX90640 thermal camera, Raspberry Pi 5) fluctuate with currency exchange rates and stock availability.
3. **Unforeseen fabrication charges** — College mechanical workshop may charge nominal workshop fees for custom bracket fabrication (F3, F4, F5 items).
4. **Additional wiring and connectors** — Multi-sensor wiring frequently requires more cable, JST connectors, or cable management than initially estimated.
5. **Shipping costs** — Orders from multiple suppliers may incur shipping charges when individual order values fall below retailer free-shipping thresholds.
6. **Documentation and report preparation** — Final prototype documentation, circuit diagrams, and funding-committee progress reports.

> The contingency is kept conservative and is **not** a reserve for purchasing additional sensors or upgrading components. Any unspent contingency is returned to the institution or applied toward Phase 2 (clinical-site validation).

---

## 9. Category-Wise Summary

| Category | Amount (₹) |
|---|---:|
| Hardware (sensors + MLX90614, processing, MCU, electronics, power, communication) | 25,195 |
| Prototype Fabrication (mounting, wiring, enclosures, mechanical) | 4,460 |
| Data & Experimentation (calibration, test materials, consumables) | 3,350 |
| Validation (volunteer sessions, ethics documentation, reference items) | 2,950 |
| Contingency | 4,245 |
| **TOTAL** | **₹40,200** |

> **Surplus vs. ₹1,00,000 cap: ₹59,800 uncommitted.**  
> This surplus is intentional. It accurately reflects the project document's own estimate of ₹50,000–₹70,000. Artificially inflating the budget to consume the full ₹1 lakh would mislead the funding committee and waste institutional resources.  
>
> **Recommended use of surplus:** Retain in institutional account for Phase 2 — potential clinical-site testing, improved sensor hardware (higher-resolution radar or pressure mat for follow-up study), or conference paper submission and travel fees.

---

## 10. Purchase vs. Institutional Access

The following items should preferably be **accessed through institutional resources** rather than purchased:

| Item | Why Access Rather Than Purchase | Recommended Access Point |
|---|---|---|
| Hospital bed / metal cot | A bed frame serves only as a mechanical mounting platform for sensors. An existing departmental cot is fully sufficient. | College engineering lab / biomedical lab / nursing skills lab / hostel |
| Reference weighing platform scale | Calibrated platform scales are standard equipment in clinical, physiotherapy, and biomedical labs. | College biomedical engineering lab / attached hospital / physiotherapy department |
| Reference spirometer / peak flow meter | Incentive spirometers are routine teaching tools in nursing and biomedical programs. | College nursing skills lab / biomedical engineering lab |
| Reference pulse oximeter | Fingertip SpO₂ monitors are extremely common in clinical teaching departments. | College nursing lab / hospital teaching ward / research supervisor |
| Reference clinical thermometer | Digital infrared thermometers are available in virtually every biomedical or clinical teaching lab. | College biomedical lab / nursing lab |

**Why this matters:** Purchasing equipment the institution already owns reduces the research budget available for core sensors and wastes credibility in a funding proposal. A funding committee reviewing this budget can see that institutional resources are being used efficiently.

---

## 11. Budget Justification

### Hardware — ₹29,995 (66.7% of funded budget)

The hardware budget directly funds the four sensor modalities and the processing stack specified in the project document. Key justification decisions:

- **mmWave radar (₹650):** The Hi-Link HLK-LD2450 is chosen over TI evaluation modules (₹46,000+). For the prototype objective — demonstrating respiratory rate estimation and occupancy detection — the LD2450 provides 24 GHz FMCW sensing at the research scale. Research papers demonstrate respiratory detection using Hi-Link modules in comparable contexts. The cost saving is ₹45,350, which is redirected to more research-value activities.
- **Pressure sensor matrix (₹3,100 total materials):** The Velostat DIY approach is standard in pressure-mapping research. It produces a pressure distribution map sufficient for body position estimation, occupancy detection, and movement tracking — all stated research objectives. Commercial pressure-mat systems (₹50,000+) would consume the entire hardware budget for one component.
- **Thermal camera (₹5,000):** The MLX90640 is extensively validated in contactless temperature research prototypes. Its 32×24 pixel resolution is appropriate for skin-temperature trending across a hospital bed footprint.
- **Raspberry Pi 5 8 GB (₹9,500):** Explicitly specified in the project document. Required for simultaneous real-time AI inference, MQTT brokering, FastAPI backend, and database storage.

### Prototype Fabrication — ₹4,460 (9.9%)

Without mechanical integration, sensors cannot be positioned correctly and the multimodal system cannot be coherently evaluated. Fabrication costs are minimised by using the college mechanical workshop for custom brackets (items F3, F4, F5).

### Data & Experimentation — ₹3,350 (7.4%)

Calibration equipment (known weights, thermal reference) is essential for the prototype to produce trustworthy, publishable measurements. Environmental interference testing directly addresses a listed technical challenge. Without valid calibration data, the prototype produces only uncalibrated signals — not research evidence.

### Validation — ₹2,950 (6.6%)

Volunteer sessions with reference measurements produce the experimental evidence that transforms the prototype from a demonstration into a research contribution. Without comparison against reference measurements, the research question "Does it work?" cannot be answered for a peer-reviewed audience.

### Contingency — ₹4,245 (9.4%)

Provides a responsible operational buffer for component failures, price changes, and unforeseen assembly requirements. Kept at a level consistent with standard engineering project practice (~10–15% of main cost).

---

## 12. Important Procurement Notes

1. **Prices are market prices researched in August 2026.** All prices are subject to change due to currency fluctuations (for imported components), stock availability, import duties, and retailer promotions.

2. **Availability verification is mandatory before final procurement.** Items listed with specific retailers must be verified as in-stock and current-model at the time of purchase order. Do not use prices from out-of-stock, discontinued, or unverified listings as the basis for purchase orders.

3. **Avoid unverified marketplace listings.** For any component sourced from IndiaMART or similar B2B platforms, verify the seller's GST registration and exact product identity before ordering.

4. **GST considerations.** Prices above are estimated inclusive of 18% GST where applicable (electronics components attract 18% GST in India). Final invoice amounts must be verified against GST-inclusive pricing from the supplier at time of purchase.

5. **Shipping costs.** Most major Indian electronics retailers (Robu.in, Robocraze) offer free shipping above ₹499. Consolidating orders to reduce the number of shipments is strongly recommended.

6. **mmWave radar selection note.** The HLK-LD2450 is recommended for cost and availability reasons. However, its respiration-rate accuracy is likely lower than a TI IWR-class evaluation kit. The research team must explicitly document this as a limitation and report measured accuracy metrics in the prototype's research paper methodology section.

7. **Velostat matrix construction note.** Velostat-based pressure matrices require careful calibration and suffer from inter-cell crosstalk at the construction level. The team should allocate 2–3 days for matrix construction, characterisation, and calibration before clinical data collection begins.

8. **Ethical clearance must precede human-participant experiments.** Volunteer session expenses (V5) and consent documentation (V6) assume institutional IRB/ethics clearance is applied for promptly at the start of the project.

9. **Recommended procurement sequence:**
   1. Raspberry Pi 5 + accessories (leads the software development timeline)
   2. ESP32 boards + electronics modules
   3. Velostat sheets + conductive materials (matrix construction takes longest)
   4. MLX90640 thermal camera + MLX90614 point temperature sensor (Item 5B)
   5. Load cells + HX711 modules
   6. HLK-LD6002 vital sign radar module (replaces HLK-LD2450 — see BudgetVerification.md)
   7. Fabrication materials (after sensor placement is finalised)
   8. Calibration weights and experimental consumables (just before first test session)

10. **This budget is a research funding proposal estimate, not a final purchase order.** All prices must be independently verified at the time of procurement. GST invoices from registered suppliers must be obtained for all purchases. A funding committee should treat this document as a reasonable upper-bound estimate of prototype construction cost, not a guaranteed fixed-price quote.

---

*End of Budget Document*  
*Smart Bed V2 — Research Prototype Budget | Coimbatore, Tamil Nadu | August 2026*
