# Presentation Notes Final — Smart Bed V2

> **Source File:** [AI-Powered Multimodal Contactless Patient Monitoring System.pptx](file:///d:/Smart%20Bed/Presentation%20Content/AI-Powered%20Multimodal%20Contactless%20Patient%20Monitoring%20System.pptx)  
> **Total Slides:** 19 Slides  
> **Usage:** Contains exact slide text, visual references, and presentation delivery notes for each of the 19 slides in your PowerPoint deck.

---

## Master Slide Index

| Slide # | Slide Title | Type / Format |
|---:|---|---|
| **1** | Project Title | Hero Title Slide |
| **2** | The Monitoring Gap in Indian Hospital Wards | Clinical Problem Table & Quote |
| **3** | Why Contact-Based Monitoring Has Limits | Pain Points Bulleted List |
| **4** | Contactless Systems Already Work — in Labs and Hospitals | 2025–2026 Clinical Evidence Table |
| **5** | Why Existing Contactless Systems Are Not the Answer | 3-Way Approach Comparison Table |
| **6** | The Silent Failure Problem | Disturbance vs Output Table & Quotes |
| **7** | Our Approach: The Hospital Bed as a Sensing Platform | Sensor Placement Table & Retrofit Bullets |
| **8** | Five Sensors — Three Independent Measurement Pathways | Pathway Architecture & Sensors |
| **9** | Hardware Architecture | System Hardware Stack Diagram |
| **10** | Components and Their Roles | Component Reference Table |
| **11** | Software Architecture | System Data Flow Diagram |
| **12** | Data Flow | 6-Stage Software Pipeline Table |
| **13** | The Confidence-Aware Fusion Engine | 6-Step Validity State Machine Table |
| **14** | From One Bed to a Ward | Phase 2 Software Ward Simulation & SHAP |
| **15** | What the Dashboard Tells Nurses — Single-Bed View | Single-Bed UI Elements Table |
| **16** | What the Dashboard Tells Nurses — Ward Priority View | Ward Priority Queue Table |
| **17** | Evidence, Research Novelty, & Expected Contribution | Peer-Reviewed Evidence, Research Gap & Deliverables |
| **18** | Budget | Section-Wise Budget Table (₹64,280 Total) |
| **19** | Thank You | Closing Vision & Contact Details |

---

---

## Slide-by-Slide Content & Presentation Notes

### 📍 Slide 1 — Title Slide

**Display Content on Slide:**
> # AI-Powered Multimodal Contactless Patient Monitoring System
> *Using the Hospital Bed as an Unobtrusive Sensing Platform*
>
> Department of Biomedical Engineering / Computer Science  
> Coimbatore, Tamil Nadu, India | August 2026

**How to Present / Talking Points:**
- Speak one clean opening statement: *"We propose retrofitting conventional hospital cots into intelligent, non-contact patient monitoring platforms — zero wires, zero patient attachments, and zero bed replacements."*
- Let the title breathe. Establish the core premise immediately: affordable, unobtrusive, confidence-aware.

---

### 📍 Slide 2 — The Monitoring Gap in Indian Hospital Wards

**Display Content on Slide:**

| Reality | Impact |
|---|---|
| 15–40 patients per nurse in general wards | Vital signs checked only every 4–8 hours |
| Heavy documentation workload | Nurses spend less time at the bedside |
| ICU monitors unavailable in general wards | Long unmonitored windows between rounds |
| Patient deterioration can be gradual and silent | Early signs missed until acute crisis |

> *"A patient can deteriorate and recover — or not — between two manual rounds."*

**How to Present / Talking Points:**
- *"In general wards across India, nurses manage 15 to 40 patients per shift. Vital signs are recorded manually every 4 to 8 hours."*
- Highlight the core vulnerability: between 10 AM and 4 PM, a patient's breathing rate can spike or drop unnoticed.
- End on the bottom quote: *"A patient can deteriorate and recover — or not — between two manual rounds."*

---

### 📍 Slide 3 — Why Contact-Based Monitoring Has Limits

**Display Content on Slide:**

**The problem with wires and patches:**
- **Sensor Displacement:** ECG leads and oximeter clips detach during sleep or movement, triggering false alarms.
- **Skin Discomfort:** Adhesive electrodes cause irritation and skin tears in elderly and pediatric patients.
- **Alarm Fatigue:** Frequent false disconnection alarms cause nursing staff to ignore monitor alerts.
- **Maintenance Overhead:** Cables require constant cleaning, untangling, and replacement.
- **Incomplete Records:** Detached sensors create gaps in continuous monitoring data.

**How to Present / Talking Points:**
- *"Why can't we just clip wired sensors onto every ward patient?"*
- Walk through the five points: leads fall off during sleep, adhesives tear delicate skin, constant beeping causes alarm fatigue, and cables require endless sanitisation.
- Transition: *"To solve this, we must remove the sensor from the patient entirely."*

---

### 📍 Slide 4 — Contactless Systems Already Work — in Labs and Hospitals

**Display Content on Slide:**

| Study | Technology | Key Result | Patients |
|---|---|---|---|
| Padaki et al., Jan 2026 | Camera rPPG (smartphone/webcam) | HR RMSE 1.62 bpm · RR RMSE 1.71 bpm | 111 ED patients |
| Shaya, Levy et al., Jun 2026 | 24 GHz Doppler Radar (TAMAR) | RR LOA ±1.6 bpm confirmed in real EDs | 315 ED patients, 3 hospitals |
| Pitafi et al., Feb 2026 | Geophone under mattress + Raspberry Pi | HR/RR MAE < 2 bpm on edge hardware | Synthetic + 75 human references |
| Chen et al., 2024 | mmWave FMCW Radar (76–81 GHz) | Contactless chest displacement feasibility confirmed | Controlled lab |
| Lee, Kim & Jeong, Aug 2025 | Load cells on bed frame | 96.26% fall/bed-exit detection accuracy | Healthy adults |

**How to Present / Talking Points:**
- *"Non-contact vitals monitoring is not science fiction. It is proven in recent 2025 and 2026 literature."*
- Point to **Padaki et al.** (111 real ER patients) and **Shaya et al.** (315 real ER patients across 3 hospitals).
- Emphasise: *"The individual sensing technologies are medically validated — the gap lies in integration and accessibility."*

---

### 📍 Slide 5 — Why Existing Contactless Systems Are Not the Answer

**Display Content on Slide:**

| Requirement | Commercial Smart Beds | Single-Sensor Radar/Camera | Our Approach |
|---|---|---|---|
| Cost per bed | ₹10–50 lakh | ₹5–15 lakh (full setup) | **₹64,280** |
| Works on existing beds | ❌ Replace entire bed | ❌ Requires fixed installation | ✅ Retrofit any cot |
| Multiple sensing modalities | Some | ❌ One sensor only | ✅ Five sensors |
| Handles movement/visitors/blankets | ❌ No | ❌ No — silently fails | ✅ Explicitly detects and flags |
| Accessible to resource-constrained wards | ❌ No | ❌ No | ✅ Yes |

**How to Present / Talking Points:**
- Compare the three columns: Commercial smart beds cost ₹10 to ₹50 lakh and require throwing away existing cots.
- Single-sensor radar/camera setups fail when a blanket is placed or a visitor sits on the bed.
- Highlight Our Approach: ₹64,280 retrofit on any existing bed with 5 complementary sensors.

---

### 📍 Slide 6 — The Silent Failure Problem

**Display Content on Slide:**

**What happens when a single sensor is disturbed:**

| Disturbance | What the Sensor Sees | What It Reports |
|---|---|---|
| Patient turns over | Radar phase noise spike | Reports erratic RR — may look like tachypnea |
| Visitor sits on the bed | Radar detects visitor's breathing | Reports visitor's RR as patient's RR |
| Thick blanket covers patient | Thermal camera reads blanket surface | Reports ambient temperature as body temperature |

> **This is the silent failure problem:**  
> The sensor produces a plausible-looking but clinically wrong number — with no warning.

> *"A sensor that fails loudly is safe. A sensor that fails silently is dangerous."*  
> — TAMAR 315-patient trial (Shaya et al., Jun 2026): 30% of measurements were invalid under real conditions.

**How to Present / Talking Points:**
- Spend extra time here — this is your core research motivation.
- *"If a single-sensor radar sees a visitor sitting on the bed, it measures the visitor's chest and reports it as the patient's respiratory rate."*
- Quote the TAMAR trial finding: *"30% of real-world radar measurements failed due to movement and positioning. A system must know when its data cannot be trusted."*

---

### 📍 Slide 7 — Our Approach: The Hospital Bed as a Sensing Platform

**Display Content on Slide:**

**The Retrofit Concept:**
- No new beds required — sensors attach to any existing single-person metal cot
- Zero leads or patches on the patient
- Zero change to nursing workflow
- Five sensors, each placed unobtrusively:

| Sensor | Where |
|---|---|
| 60 GHz mmWave Radar | Headboard, facing patient chest |
| Geophone (BCG vibration sensor) | Under the mattress, beneath upper torso |
| Pressure Matrix (12×12 grid) | On the mattress surface, under a thin sheet |
| 4× Load Cells | Under each bed leg, inside footpad plates |
| Thermal Camera + Point IR | Overhead arm (1.2 m) + headboard |

> *"The bed becomes the sensor. The patient simply lies down."*

**How to Present / Talking Points:**
- *"We convert the bed into the sensor. The patient lies down, and monitoring happens automatically."*
- Briefly highlight the 5 physical zones: headboard radar, under-mattress geophone, surface pressure matrix, leg load cells, overhead thermal arm.

---

### 📍 Slide 8 — Five Sensors — Three Independent Measurement Pathways

**Display Content on Slide:**

**Three independent ways to measure breathing and heartbeat:**
- **Pathway 1 (Through Air):** 60 GHz Radar (HLK-LD6002) — measures sub-mm chest wall displacement via Doppler phase shift.
- **Pathway 2 (Through Structure):** SM-24 Geophone — detects structural Ballistocardiography (BCG) micro-vibrations through mattress and frame.
- **Pathway 3 (Through Contact):** Velostat Pressure Matrix — captures surface pressure micro-vibration and posture centroid.
- **Validation Channels:** Load Cells ×4 (weight, occupancy, visitor, bed-exit) + Dual Thermal (MLX90640 + MLX90614, surface temp trend & blanket index).

**How to Present / Talking Points:**
- *"Why three pathways? If radar is blocked by a blanket, the under-mattress geophone still detects heartbeat and breathing micro-vibrations through the bed structure."*
- Cross-validating three distinct physical principles guarantees high-confidence readings.

---

### 📍 Slide 9 — Hardware Architecture

**Display Content on Slide:**
- **Diagram Reference:** High-level Hardware System Architecture Diagram (Sensors → ESP32/ADCs → Raspberry Pi 5 Edge → Power Subsystem → Nurse Dashboard).
- **See:** [Slide 9 Diagram.md](file:///d:/Smart%20Bed/Presentation%20Content/Slide%209%20Diagram.md) for full visual rendering.

**How to Present / Talking Points:**
- *"The hardware architecture is split into two compute tiers:"*
  1. An **ESP32 microcontroller** handling load cell ADCs and multiplexed pressure grid scanning.
  2. A **Raspberry Pi 5 (8 GB)** edge server handling high-speed radar UART, thermal I2C, signal processing, and the AI fusion engine.

---

### 📍 Slide 10 — Components and Their Roles

**Display Content on Slide:**

| Component | Role |
|---|---|
| Raspberry Pi 5 (8 GB) | Edge compute: signal processing, fusion engine, FastAPI server |
| ESP32 WROOM-32 | MCU: multiplexes pressure matrix (12×12), reads load cells, publishes via MQTT |
| ADS1115 ×2 | 16-bit ADC for geophone and pressure matrix analog signals |
| CD74HC4067 Mux ×3 | Scans 12×12 pressure matrix grid (144 cells) |
| HX711 ×2 | 24-bit ADC for 4 load cells (2 full-bridge pairs) |
| 12 V 5 A Supply + LM2596 ×3 | Regulated 5 V and 3.3 V rails for MCU and sensor subsystems |

**How to Present / Talking Points:**
- Walk through the table briefly.
- Emphasise that off-the-shelf, low-cost breakout components keep the entire electronics hardware cost under ₹28,000, anchored by the Raspberry Pi 5.

---

### 📍 Slide 11 — Software Architecture

**Display Content on Slide:**
- **Diagram Reference:** End-to-End Software Architecture & Data Pipeline Diagram (Ingestion → Signal Processing → Fusion State Machine → SQLite → FastAPI → Dashboard).
- **See:** [Slide 10 Diagram.md](file:///d:/Smart%20Bed/Presentation%20Content/Slide%2010%20Diagram.md) for full visual rendering.

**How to Present / Talking Points:**
- *"Our software pipeline operates as a clean, unidirectional flow: raw sensor streams enter, pass through SciPy digital filtering, get gated by the confidence engine, and stream live via WebSockets."*

---

### 📍 Slide 12 — Data Flow

**Display Content on Slide:**

| Stage | What Happens |
|---|---|
| Ingestion | ESP32 MQTT + Radar UART + Thermal I2C + Geophone ADC → raw data collected |
| Signal Processing | FFT (radar RR), dual bandpass (geophone RR + HR), centroid calculation (pressure) |
| Fusion Engine | Confidence state machine — occupancy, visitor, motion, blanket, 3-way agreement |
| Storage | SQLite database, flushed every 30 s |
| API | FastAPI WebSocket streams live data to dashboard |
| Dashboard | Nurse-facing single-bed view + Phase 2 ward queue |

**How to Present / Talking Points:**
- Explain the 6 pipeline stages in order.
- Emphasise Stage 3 (Fusion Engine): *"No reading reaches the database or nurse interface without passing the validity check."*

---

### 📍 Slide 13 — The Confidence-Aware Fusion Engine

**Display Content on Slide:**

| Step | Rule / Check | Trigger Condition | Resulting System State & Action |
|---:|---|---|---|
| **1** | Occupancy Check | Load cells $\le$ Tare weight baseline | 🔴 **Bed Unoccupied** — Suppress all physiological outputs |
| **2** | Visitor Gate | Weight delta > 30 kg **OR** 2nd centroid | 🟠 **Visitor Detected** — Suppress vitals, raise alert |
| **3** | Motion Gate | Pressure grid temporal change > threshold | 🟡 **Patient Moving** — Pause radar & geophone RR (30 s) |
| **4** | Blanket Gate | Thermal contrast index < 0.3 | 🟡 **Body Obscured** — Suspend temperature reading only |
| **5** | 3-Way Agreement | Radar RR & Geophone RR agree within $\pm2$ bpm | 🟢 **High Confidence** — Publish all validated vitals |
| **6** | Pathway Disagreement | Radar RR & Geophone RR disagree $>2$ bpm | 🟡 **Low Confidence** — Publish vitals with warning flag |

**How to Present / Talking Points:**
- *"This slide represents our core technical novelty."*
- Walk through the decision hierarchy:
  1. *Unoccupied bed?* Suppress vitals.
  2. *Visitor sitting on bed?* Flag visitor & pause vitals.
  3. *Patient moving?* Pause physiological extraction for 30 s.
  4. *Blanket covering patient?* Flag body obscured & pause thermal.
  5. *Radar and geophone agree?* Publish **High Confidence**.

---

### 📍 Slide 14 — From One Bed to a Ward

**Display Content on Slide:**

**Phase 2: Software Ward Simulation (₹0 extra hardware)**
- The single-bed prototype collects labelled scenario recordings:

| Scenario Label | What the prototype recorded |
|---|---|
| `quiet_rest` | Still patient, stable RR, normal temperature |
| `elevated_rr` | RR elevated >20% above personal baseline |
| `sustained_pressure` | Same body region under load > 2 hours |
| `bed_exit_attempt` | Load cell weight dropping, centroid at edge |
| `visitor_present` | Weight delta +30 kg, second pressure centroid |

- Composed into multi-bed synthetic ward snapshots.
- **XGBoost Classifier** ranks patient priority.
- **SHAP (SHapley Additive exPlanations)** outputs readable explanations:
  > *"Bed 3 — HIGH PRIORITY: Elevated RR +35% above baseline (High Confidence) → +0.42 · Sustained sacral pressure 2.2 h → +0.31 · Surface temp +0.7°C → +0.18"*

**How to Present / Talking Points:**
- *"Phase 1 builds and validates the physical single-bed prototype. Phase 2 extends the data into a simulated ward at zero additional hardware cost."*
- Read the SHAP output string — explain that nurses receive actionable explanations, not black-box predictions.

---

### 📍 Slide 15 — What the Dashboard Tells Nurses — Single-Bed View

**Display Content on Slide:**

| Display Element | What It Shows |
|---|---|
| Occupancy Status | Occupied / Unoccupied (green / grey) |
| Body Position | Supine / Left Lateral / Right Lateral / Seated |
| Respiratory Rate | e.g. 16 bpm 🟢 High Confidence |
| Surface Temperature Trend | e.g. +0.4°C over last 60 min |
| Movement Level | Low / Medium / High |
| Active Alerts | e.g. "Patient stationary 3 hours — check pressure risk" |

**How to Present / Talking Points:**
- *"In Single-Bed Mode, the nurse sees six clear parameters, including live posture and explicit confidence flags."*

---

### 📍 Slide 16 — What the Dashboard Tells Nurses — Ward Priority View

**Display Content on Slide:**

| Bed | Status | Priority | Reason |
|---|---|---|---|
| Bed 3 | Occupied, Supine | 🔴 HIGH | Elevated RR + sustained pressure |
| Bed 7 | Occupied, Moving | 🟡 MEDIUM | Patient restless — readings paused |
| Bed 1 | Occupied, Supine | 🟢 LOW | Stable, all sensors agree |

> **No diagnostic claims.** All outputs are *observational alerts*, not medical judgements.

**How to Present / Talking Points:**
- *"In Ward Mode, beds are sorted by priority rank."*
- Reiterate regulatory safety: *"We make zero diagnostic claims. The system provides continuous observation and alerts — clinical judgement remains with the nursing staff."*

---

### 📍 Slide 17 — Evidence, Research Novelty, & Expected Contribution

**Display Content on Slide:**

**Built on recent peer-reviewed evidence:**

| Paper | Key Support |
|---|---|
| Lee et al. (Aug 2025) | Load cells: 96.26% bed-exit detection |
| Pitafi et al. (Feb 2026) | Geophone BCG on Raspberry Pi: MAE < 2 bpm |
| Shaya et al. (Jun 2026) | 315-patient radar trial — 30% silent failure justifies our fusion approach |
| Reyes et al. (2026) | Multi-patient radar unsolved — justifies our simulation approach |

> *"No study has demonstrated a system under ₹65,000 combining three independent physiological pathways with explicit confidence-aware interference detection and simulation-based explainable ward prioritisation."*

**Expected outputs:**
- Validated single-bed prototype with documented sensor accuracy
- Labelled scenario dataset from 10 volunteer sessions
- SHAP-explainable multi-patient simulation model
- Conference / journal paper

**How to Present / Talking Points:**
- Read the research gap quote clearly.
- State the 4 concrete academic deliverables: prototype, dataset, XAI simulation model, and peer-reviewed paper.

---

### 📍 Slide 18 — Budget

**Display Content on Slide:**

| Section | Amount (₹) | Key Components Included |
|---|---:|---|
| **Section A — Core Hardware** | 40,465 | RPi 5 8GB (₹20k), Radar, Geophone, Velostat matrix, Load cells, MLX90640, MLX90614, ESP32, ADCs, Muxes |
| **Section B — Prototype Fabrication** | 10,160 | Cot frame, foam mattress, headboard radar mount, overhead camera arm, footpads, enclosures, wiring |
| **Section C — Data & Experimentation** | 3,350 | Calibration weights (5 kg), EVA foam, thermal target, ref thermometer, USB fan, forms & hygiene |
| **Section D — Validation** | 5,750 | Reference stopwatch, volunteer honoraria, ethics printing, backup drive + conditional ref instruments |
| **Contingency (~8%)** | 4,555 | Component failures, price variation & shipping buffer |
| | | |
| **Total (Worst Case)** | **₹64,280** | **Full 5-sensor AI research prototype expenditure** |
| **Surplus for Phase 2** | **₹35,720** | **Uncommitted surplus remaining under ₹1,00,000 grant cap** |

**How to Present / Talking Points:**
- *"The total budget required to build, fabricate, and clinically validate the prototype is ₹64,280."*
- Point out that this leaves **₹35,720 uncommitted** under the ₹1,00,000 institutional grant cap, reserved for Phase 2 clinical-site testing.

---

### 📍 Slide 19 — Thank You

**Display Content on Slide:**

> # Thank You
>
> *"Affordable, Unobtrusive, Confidence-Aware Patient Monitoring for Resource-Constrained Healthcare."*
>
> **Project:** AI-Powered Multimodal Contactless Patient Monitoring System  
> **Department:** Department of Biomedical Engineering / Computer Science  
> **Location:** Coimbatore, Tamil Nadu, India  
> **GitHub:** github.com/Stark6612/SmartBed  

**How to Present / Talking Points:**
- Say the final vision statement: *"Affordable, unobtrusive, confidence-aware patient monitoring."*
- Thank the committee and invite questions.

---

*Presentation Notes Final — 100% Aligned with AI-Powered Multimodal Contactless Patient Monitoring System.pptx | August 2026*