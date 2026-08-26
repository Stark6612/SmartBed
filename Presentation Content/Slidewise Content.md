# Slidewise Content — Smart Bed V2 Presentation

> **Purpose:** Exact display content and presentation notes for each of the 15 slides.  
> **Usage:** Each slide entry gives: Title, what to put on the slide, and how to present/deliver it.

---

## Slide 1 — Project Title

**Display on Slide:**

> # AI-Powered Multimodal Contactless Patient Monitoring System
> *Using the Hospital Bed as an Unobtrusive Sensing Platform*
>
> Department of Biomedical Engineering / Computer Science  
> Coimbatore, Tamil Nadu, India | August 2026

**How to Present:**
- One sentence spoken aloud: *"We propose converting ordinary hospital cots into intelligent, non-contact patient monitoring platforms — no wires, no attachments, no new beds required."*
- Let the title breathe. Don't read it word-for-word.

---

## Slide 2 — The Monitoring Gap in Indian Hospital Wards

**Display on Slide:**

| Reality | Impact |
|---|---|
| 15–40 patients per nurse in general wards | Vital signs checked only every 4–8 hours |
| Heavy documentation workload | Nurses spend less time at the bedside |
| ICU monitors unavailable in general wards | Long unmonitored windows between rounds |
| Patient deterioration can be gradual and silent | Early signs missed until acute crisis |

**Headline stat to feature prominently:**
> *"A patient can deteriorate and recover — or not — between two manual rounds."*

**How to Present:**
- Start with a question: *"How often does a nurse in a busy government ward actually record a patient's vital signs?"*
- Walk through the table row by row. Each row builds the case.
- End on the headline stat — let it land before moving on.

---

## Slide 3 — Why Contact-Based Monitoring Has Limits

**Display on Slide:**

**The problem with wires and patches:**

- **Sensor Displacement** — ECG leads and oximeter clips detach during sleep or movement, triggering false alarms
- **Skin Discomfort** — Adhesive electrodes cause irritation and skin tears in elderly and pediatric patients
- **Alarm Fatigue** — Frequent false disconnection alarms cause nursing staff to ignore monitor alerts
- **Maintenance Overhead** — Cables require constant cleaning, untangling, and replacement
- **Incomplete Records** — Detached sensors create gaps in continuous monitoring data

**How to Present:**
- *"Even when monitoring equipment exists, it creates its own problems."*
- Read through the five points quickly — the audience has seen these problems. Don't dwell.
- Transition: *"So what if we remove the sensor from the patient entirely?"*

---

## Slide 4 — Contactless Systems Already Work — in Labs and Hospitals

**Display on Slide:**

| Study | Technology | Patients | Key Result |
|---|---|---|---|
| Padaki et al., Jan 2026 | Camera rPPG (smartphone/webcam) | 111 ED patients | HR RMSE 1.62 bpm · RR RMSE 1.71 bpm |
| Shaya, Levy et al., Jun 2026 | 24 GHz Doppler Radar (TAMAR) | 315 ED patients, 3 hospitals | RR LOA ±1.6 bpm confirmed in real EDs |
| Pitafi et al., Feb 2026 | Geophone under mattress + Raspberry Pi | Synthetic + 75 human references | HR/RR MAE < 2 bpm on edge hardware |
| Chen et al., 2024 | mmWave FMCW Radar (76–81 GHz) | Controlled lab | Contactless chest displacement feasibility confirmed |
| Lee, Kim & Jeong, Aug 2025 | Load cells on bed frame | Healthy adults | 96.26% fall/bed-exit detection accuracy |

> *"The underlying sensing technologies are not experimental — they have been clinically validated."*

**How to Present:**
- *"We are not proposing speculative science. These results are from 2025 and 2026."*
- Point to the patient counts — 111 and 315 real hospital patients, not lab volunteers.
- This slide earns you credibility before you pitch your solution.

---

## Slide 5 — Why Existing Contactless Systems Are Not the Answer

**Display on Slide:**

| Requirement | Commercial Smart Beds | Single-Sensor Radar/Camera | Our Approach |
|---|---|---|---|
| Cost per bed | ₹10–50 lakh | ₹5–15 lakh (full setup) | **₹64,280** |
| Works on existing beds | ❌ Replace entire bed | ❌ Requires fixed installation | ✅ Retrofit any cot |
| Multiple sensing modalities | Some | ❌ One sensor only | ✅ Five sensors |
| Handles movement/visitors/blankets | ❌ No | ❌ No — silently fails | ✅ Explicitly detects and flags |
| Accessible to resource-constrained wards | ❌ No | ❌ No | ✅ Yes |

**How to Present:**
- *"Technology existing is not the same as technology being accessible."*
- Walk through the table column by column, not row by row — compare the three approaches.
- The last row is the killer: existing systems fail in real ward conditions without acknowledging it.
- Transition: *"Which brings us to the biggest problem."*

---

## Slide 6 — The Silent Failure Problem

**Display on Slide:**

**What happens when a single sensor is disturbed:**

| Disturbance | What the Sensor Sees | What It Reports |
|---|---|---|
| Patient turns over | Radar phase noise spike | Reports erratic RR — may look like tachypnea |
| Visitor sits on the bed | Radar detects visitor's breathing | Reports visitor's RR as patient's RR |
| Thick blanket covers patient | Thermal camera reads blanket surface | Reports ambient temperature as body temperature |

> **This is the silent failure problem:**  
> The sensor produces a *plausible-looking* but *clinically wrong* number — with no warning.

> *"A sensor that fails loudly is safe. A sensor that fails silently is dangerous."*  
> — TAMAR 315-patient trial (Shaya et al., Jun 2026): 30% of measurements were invalid under real conditions.

**How to Present:**
- This is your main problem slide — slow down here.
- *"Imagine a nurse looks at the monitor and sees RR: 22. Normal enough. But the patient turned in their sleep 3 minutes ago and the radar hasn't recovered."*
- The TAMAR stat (30% failure rate) is your proof — cite it.
- Transition: *"Our system solves this. Before it tells a nurse anything — it first asks: can we trust this reading?"*

---

## Slide 7 — Our Approach: The Hospital Bed as a Sensing Platform

**Display on Slide:**

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

**How to Present:**
- *"What if instead of attaching sensors to the patient, we embedded them in the bed?"*
- Go through the sensor placement table quickly — the audience doesn't need to memorise these, just understand that all sensors are hidden from the patient.
- The closing quote is your sound-bite — say it slowly.

---

## Slide 8 — Five Sensors — Three Independent Measurement Pathways

**Display on Slide:**

**Three independent ways to measure breathing and heartbeat:**

| Pathway | Sensor | Physical Mechanism | Blanket-proof? |
|---|---|---|---|
| **Pathway 1 — Through Air** | HLK-LD6002 60 GHz Radar | Measures sub-millimetre chest wall displacement via Doppler phase shift | Partially |
| **Pathway 2 — Through Structure** | SM-24 Geophone | Detects heartbeat recoil vibrations transmitted through mattress and bed frame (BCG) | ✅ Yes |
| **Pathway 3 — Through Contact** | Velostat Pressure Matrix | Captures micro-pressure changes from breathing and heartbeat through mattress surface | ✅ Yes |

**Additional sensors (validation & context):**
- **Load Cells ×4** → Weight, occupancy, visitor detection, bed-exit
- **MLX90640 + MLX90614** → Spatial thermal map, surface temperature trend (±0.2°C)

> **Why three pathways?**  
> When two or more independent pathways agree within ±2 bpm → the reading is trusted.  
> When they disagree → the system knows something is wrong.

**How to Present:**
- *"We don't just measure vital signs — we measure them three different ways, using three completely different physical principles."*
- Explain each pathway in one sentence. Don't over-explain the physics.
- Emphasise the key insight: agreement = confidence. Disagreement = flag.

---

## Slide 9 — Hardware Architecture

**Display on Slide:**

> 📊 **See:** [Slide 9 Diagram.md](Slide%209%20Diagram.md) — use the rendered Mermaid diagram directly or screenshot it for the slide.

**Key Components (display as a supporting table below the diagram):**

| Component | Role |
|---|---|
| Raspberry Pi 5 (8 GB) | Edge compute: signal processing, fusion engine, FastAPI server |
| ESP32 WROOM-32 | MCU: multiplexes pressure matrix (12×12), reads load cells, publishes via MQTT |
| ADS1115 ×2 | 16-bit ADC for geophone and pressure matrix analog signals |
| CD74HC4067 Mux ×3 | Scans 12×12 pressure matrix grid (144 cells) |
| HX711 ×2 | 24-bit ADC for 4 load cells (2 full-bridge pairs) |
| 12 V 5 A Supply + LM2596 ×3 | Regulated 5 V and 3.3 V rails for MCU and sensor subsystems |

**How to Present:**
- *"Two compute nodes: an ESP32 handling the slow sensors, and a Raspberry Pi 5 handling everything else."*
- Walk through the diagram top-to-bottom: Sensors → MCU → Edge Compute → Dashboard.
- Don't dwell on part numbers. The audience needs the concept, not the datasheet.

---

## Slide 10 — Software Architecture & Data Flow

**Display on Slide:**

> 📊 **See:** [Slide 10 Diagram.md](Slide%2010%20Diagram.md) — use the rendered Mermaid diagram directly or screenshot it for the slide.

**Pipeline stages to label on or below the diagram:**

| Stage | What Happens |
|---|---|
| Ingestion | ESP32 MQTT + Radar UART + Thermal I2C + Geophone ADC → raw data collected |
| Signal Processing | FFT (radar RR), dual bandpass (geophone RR + HR), centroid calculation (pressure) |
| Fusion Engine | Confidence state machine — occupancy, visitor, motion, blanket, 3-way agreement |
| Storage | SQLite database, flushed every 30 s |
| API | FastAPI WebSocket streams live data to dashboard |
| Dashboard | Nurse-facing single-bed view + Phase 2 ward queue |

**How to Present:**
- *"The software pipeline is a one-way street — raw sensor bytes in, actionable observations out."*
- Walk through the six stages in order.
- Emphasise that the fusion engine is the gatekeeper — nothing reaches the database or dashboard unless it passes the confidence gate.

---

## Slide 11 — The Confidence-Aware Fusion Engine

**Display on Slide:**

**Before reporting any measurement, the system evaluates five validity gates in order:**

| Step | Rule / Check | Trigger Condition | Resulting System State & Action |
|---:|---|---|---|
| **1** | Occupancy Check | Load cells $\le$ Tare weight baseline | 🔴 **Bed Unoccupied** — Suppress all physiological outputs |
| **2** | Visitor Gate | Weight delta > 30 kg **OR** 2nd centroid | 🟠 **Visitor Detected** — Suppress vitals, raise alert |
| **3** | Motion Gate | Pressure grid temporal change > threshold | 🟡 **Patient Moving** — Pause radar & geophone RR (30 s) |
| **4** | Blanket Gate | Thermal contrast index < 0.3 | 🟡 **Body Obscured** — Suspend temperature reading only |
| **5** | 3-Way Agreement | Radar RR & Geophone RR agree within $\pm2$ bpm | 🟢 **High Confidence** — Publish all validated vitals |
| **6** | Pathway Disagreement | Radar RR & Geophone RR disagree $>2$ bpm | 🟡 **Low Confidence** — Publish vitals with warning flag |

> *"A nurse sees either a green reading — trustworthy — or a flagged reading with an explicit reason. Never a silent wrong number."*

**How to Present:**
- This is your core research slide. Spend the most time here.
- Walk through the five questions as a narrative: *"First we check if anyone is in the bed. Then we check if it's one person or two..."*
- The table maps directly to the decision flow — it's self-explanatory once the logic is clear.
- The closing quote is your research contribution in one sentence. Say it twice if needed.

---

## Slide 12 — From One Bed to a Ward

**Display on Slide:**

**Phase 2: Software Ward Simulation (₹0 extra hardware)**

The single-bed prototype collects real, labelled scenario recordings:

| Scenario Label | What the prototype recorded |
|---|---|
| `quiet_rest` | Still patient, stable RR, normal temperature |
| `elevated_rr` | RR elevated >20% above personal baseline |
| `sustained_pressure` | Same body region under load > 2 hours |
| `bed_exit_attempt` | Load cell weight dropping, centroid at edge |
| `visitor_present` | Weight delta +30 kg, second pressure centroid |

These recordings are synthetically composed into multi-bed ward snapshots.  
An **XGBoost classifier** is trained on the snapshots to rank patient priority.  
**SHAP** generates a readable explanation for every decision:

> *"Bed 3 — HIGH PRIORITY: Elevated RR +35% above baseline (High Confidence) → +0.42 · Sustained sacral pressure 2.2 h → +0.31 · Surface temp +0.7°C → +0.18"*

**How to Present:**
- *"Phase 1 proves the hardware. Phase 2 proves what you can do with the data."*
- The scenario table is quick — just name two or three labels and describe what they represent.
- The SHAP quote is the payoff — read it slowly and let the audience parse it.
- Emphasis: *"This is explainable AI — it does not just rank patients, it tells the nurse exactly why."*

---

## Slide 13 — What the Dashboard Tells Nurses

**Display on Slide:**

**Single-Bed View (Phase 1):**

| Display Element | What It Shows |
|---|---|
| Occupancy Status | Occupied / Unoccupied (green / grey) |
| Body Position | Supine / Left Lateral / Right Lateral / Seated |
| Respiratory Rate | e.g. 16 bpm 🟢 High Confidence |
| Surface Temperature Trend | e.g. +0.4°C over last 60 min |
| Movement Level | Low / Medium / High |
| Active Alerts | e.g. "Patient stationary 3 hours — check pressure risk" |

**Ward Priority View (Phase 2):**

| Bed | Status | Priority | Reason |
|---|---|---|---|
| Bed 3 | Occupied, Supine | 🔴 HIGH | Elevated RR + sustained pressure |
| Bed 7 | Occupied, Moving | 🟡 MEDIUM | Patient restless — readings paused |
| Bed 1 | Occupied, Supine | 🟢 LOW | Stable, all sensors agree |

> **No diagnostic claims.** All outputs are *observational alerts*, not medical judgements.

**How to Present:**
- *"The dashboard has two modes. One bed, or the whole ward."*
- Walk through the single-bed table — the nurse sees exactly these six things.
- The ward view table shows how Phase 2 scales it — same information, multiple beds, ranked by urgency.
- End firmly: *"Nothing on this screen diagnoses anything. It alerts. The nurse decides."*

---

## Slide 14 — Evidence, Research Novelty, Budget & Expected Contribution

**Display on Slide:**

**Built on recent peer-reviewed evidence:**

| Paper | Key Support |
|---|---|
| Lee et al. (Aug 2025) | Load cells: 96.26% bed-exit detection |
| Pitafi et al. (Feb 2026) | Geophone BCG on Raspberry Pi: MAE < 2 bpm |
| Shaya et al. (Jun 2026) | 315-patient radar trial — 30% silent failure justifies our fusion approach |
| Reyes et al. (2026) | Multi-patient radar unsolved — justifies our simulation approach |

**The research gap we fill:**

> *"No study has demonstrated a system under ₹65,000 combining three independent physiological pathways with explicit confidence-aware interference detection and simulation-based explainable ward prioritisation."*

**Prototype Budget — ₹64,280:**

> 📊 **Use the pie chart from [Budget_Slide_Content.md](Budget_Slide_Content.md)** — the Mermaid donut chart renders natively and is optimised for slide use. The table below is a verbal reference only.

| Category | ₹ |
|---|---:|
| Processing (RPi 5 8 GB, microSD, PSU, case) | 25,020 |
| Sensors (radar, geophone, pressure, load cells, thermal) | 12,100 |
| Fabrication + calibration + validation | 19,260 |
| Contingency (~8%) | 4,555 |
| **Total** | **₹64,280** |
| Surplus for Phase 2 | ₹35,720 |

**Expected outputs:**
- Validated single-bed prototype with documented sensor accuracy
- Labelled scenario dataset from 10 volunteer sessions
- SHAP-explainable multi-patient simulation model
- Conference / journal paper

**How to Present:**
- This is a combined slide — move efficiently.
- Read two or three papers from the table; don't read all four.
- State the research gap quote once, clearly.
- Point to the pie chart total (₹64,280) and the surplus. One sentence: *"For ₹64,280, we build the prototype. The remaining ₹35,720 goes to Phase 2 clinical validation."*
- Close with the outputs: *"We are not just building a device — we are generating a dataset, a model, and a paper."*

---

## Slide 15 — Thank You

**Display on Slide:**

> # Thank You
>
> *"Affordable, Unobtrusive, Confidence-Aware Patient Monitoring for Resource-Constrained Healthcare."*
>
> **Project:** AI-Powered Multimodal Contactless Patient Monitoring System  
> **Team:** [Team Names]  
> **Institution:** [Department], Coimbatore, Tamil Nadu, India  
> **GitHub:** github.com/Stark6612/SmartBed  
> **Contact:** [Email Address]

**How to Present:**
- Say the one-line vision once: *"Affordable, unobtrusive, confidence-aware."*
- Pause. Invite questions.
- Keep the Q&A brief on budget and validation — all detail is in the preceding slides.

---

*Slidewise Content — Aligned with Slide Structure.md, Validated Concept.md, and Budget_Slide_Content.md | August 2026*