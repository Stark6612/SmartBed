# Presentation Slide Structure — Smart Bed V2

> **Presentation Overview:** 15-Slide Presentation Structure  
> **Target Audience:** Project Evaluators, Department Head, Technical Committee, Institutional Reviewers  
> **Prototype Budget:** ₹64,280 (5-sensor full research prototype)  
> **Core Architecture:** 5 Sensors, 3 Independent Physiological Pathways, Confidence-Aware Fusion, Ward-Level XAI Simulation

---

## 📋 Master 15-Slide Presentation Table

| # | Slide Title | Core Content | Visual |
|---:|---|---|---|
| **1** | **Project Title** | Project name + one-line vision | Hero concept visual |
| **2** | **The Monitoring Gap in Indian Hospital Wards** | Why continuous patient monitoring is difficult; patient/staff burden; need for unobtrusive monitoring | Supporting statistics / simple visual |
| **3** | **Why Contact-Based Monitoring Has Limits** | Attachment, wires, discomfort, displacement, maintenance, fragmented information | Patient + sensor illustration / comparison |
| **4** | **Contactless Systems Already Work — in Labs and Hospitals** | Recent research demonstrating contactless HR/RR, bed sensing, radar, thermal, etc.; establish that the underlying technologies are feasible | **Research evidence chart/table** |
| **5** | **Why Existing Contactless Systems Are Not the Answer** | Cost, infrastructure, single-modality limitations, limited accessibility, limited clinical intelligence | **Comparison table:** Existing approaches vs requirements |
| **6** | **The Silent Failure Problem** | **MAIN PROBLEM:** a sensor can produce a plausible but unreliable measurement due to movement, visitors, blankets, etc. Why blindly trusting one sensor is dangerous | **Scenario diagram:** True state → sensor disturbance → unreliable reading |
| **7** | **Our Approach: The Hospital Bed as a Sensing Platform** | Retrofit conventional beds; unobtrusive sensing; no need to replace the bed; overall concept | **Conceptual bed diagram** |
| **8** | **Five Sensors — Three Independent Measurement Pathways** | Explain the five sensors and group them into three complementary sensing pathways; show what each observes | **MANDATORY sensing architecture diagram** |
| **9** | **Hardware Architecture** | Sensor layer → microcontrollers/edge processing → communication → server/dashboard hardware | **MANDATORY hardware architecture diagram** |
| **10** | **Software Architecture & Data Flow** | Data acquisition → preprocessing → signal quality → sensor fusion → AI interpretation → database/API → dashboard | **MANDATORY software architecture + pipeline** |
| **11** | **The Confidence-Aware Fusion Engine** | Core research mechanism: determine whether observations are trustworthy; use cross-sensor agreement to handle movement, visitors, blankets, etc. | **MANDATORY fusion pipeline / decision diagram** |
| **12** | **From One Bed to a Ward** | Scale from one prototype to multiple beds; centralized monitoring; patient prioritisation; future ward-level intelligence | **Ward-level architecture diagram** |
| **13** | **What the Dashboard Tells Nurses** | Patient status, RR/HR trends, confidence, position, occupancy, alerts; raw data → actionable information | **Dashboard mock-up** |
| **14** | **Evidence, Research Novelty, Budget & Expected Contribution** | Recent research → remaining gap → your contribution → ₹64,280 prototype budget → expected research output | **Research-gap map + budget pie chart** |
| **15** | **Thank You** | One-line vision + team/institution | Minimal |

---

---

## 🔍 Detailed Slide-by-Slide Specifications

### 📍 Slide 1: Project Title
- **Slide Title:** Project Title
- **Core Content:**
  - **Full Project Name:** AI-Powered Multimodal Contactless Patient Monitoring and Clinical Decision Support System Using the Hospital Bed as an Unobtrusive Sensing Platform
  - **One-Line Vision:** Transforming standard hospital cots into intelligent, confidence-aware patient monitoring platforms at moderate cost.
  - **Team & Institution:** Department of Biomedical Engineering / Computer Science, Coimbatore, Tamil Nadu, India.
- **Visual:** **Hero Concept Visual** — High-impact rendering of a retrofitted hospital bed showing non-contact sensing zones.

---

### 📍 Slide 2: The Monitoring Gap in Indian Hospital Wards
- **Slide Title:** The Monitoring Gap in Indian Hospital Wards
- **Core Content:**
  - **Clinical Problem:** High patient-to-nurse ratios (15 to 40 patients per nurse) in general and government wards.
  - **Monitoring Burden:** Manual vital signs checks occur intermittently (every 4–8 hours), leaving long unmonitored windows.
  - **Patient Risk:** Early signs of physiological deterioration between manual rounds go unnoticed until acute decompensation.
  - **Staff Workload:** Heavy documentation load takes nurses away from direct bed-side care.
- **Visual:** **Supporting Statistics / Simple Visual** — Callout stat cards (40:1 Nurse Ratio, 6-Hour Monitoring Gap) + split ward graphic.

---

### 📍 Slide 3: Why Contact-Based Monitoring Has Limits
- **Slide Title:** Why Contact-Based Monitoring Has Limits
- **Core Content:**
  - **Attachment Friction:** Wires, ECG electrodes, and finger pulse oximeter clips detach frequently during movement or sleep.
  - **Discomfort & Skin Trauma:** Prolonged adhesive electrodes cause skin tears and irritation in pediatric and elderly patients.
  - **Displacement & False Alarms:** Lead dislodgement triggers constant false alarms, causing alarm fatigue.
  - **Maintenance Burden:** Continuous cleaning, untangling, and replacing expensive patient leads.
  - **Fragmented Data:** Cable detachment creates incomplete health records.
- **Visual:** **Patient + Sensor Illustration / Comparison** — Diagram showing wired clutter vs. unobtrusive contactless sensing.

---

### 📍 Slide 4: Contactless Systems Already Work — in Labs and Hospitals
- **Slide Title:** Contactless Systems Already Work — in Labs and Hospitals
- **Core Content:**
  - **Establish Feasibility:** Recent peer-reviewed studies (2025–2026) prove underlying contactless technologies are accurate.
  - **R4 (Padaki et al., Jan 2026):** 111-patient ED trial validating camera rPPG (HR RMSE 1.62 bpm, RR RMSE 1.71 bpm).
  - **R5 (Shaya et al., Jun 2026):** 315-patient ED trial validating 24 GHz Doppler radar (RR LOA ±1.6 bpm).
  - **R8 (Pitafi et al., Feb 2026):** Geophone BCG under mattress achieved MAE < 2 bpm on Raspberry Pi hardware.
- **Visual:** **Research Evidence Chart/Table** — Formatted table listing paper citations (R4, R5, R8), sample sizes, and accuracy metrics.

---

### 📍 Slide 5: Why Existing Contactless Systems Are Not the Answer
- **Slide Title:** Why Existing Contactless Systems Are Not the Answer
- **Core Content:**
  - **Prohibitive Cost:** Commercial smart beds (Stryker, Invacare) cost ₹10–50 lakh per unit — unviable for resource-constrained wards.
  - **Rigid Infrastructure:** Requires discarding existing hospital cots rather than retrofitting them.
  - **Single-Modality Fragility:** Single-sensor setups (radar-only or camera-only) fail under movement, blankets, or visitor presence.
  - **Limited Accessibility & Intelligence:** Lack confidence gating to tell clinical staff *when* a reading is unreliable.
- **Visual:** **Comparison Table: Existing Approaches vs Requirements** — Feature grid comparing Commercial Smart Beds, Single-Sensor Radar, and Our Solution across Cost, Retrofitability, and Fusion Intelligence.

---

### 📍 Slide 6: The Silent Failure Problem
- **Slide Title:** The Silent Failure Problem
- **Core Content:**
  - **MAIN PROBLEM:** Single-sensor devices produce plausible-looking but corrupted measurements when disturbed.
  - **Failure Modes:**
    - *Patient Movement:* Radar phase noise outputs incorrect spikes instead of pausing.
    - *Visitors Sitting on Bed:* Load cell weight increases + radar detects visitor breathing instead of patient.
    - *Thick Blankets:* Thermal camera measures blanket surface temp while silently reporting ambient.
  - **Danger:** Blindly trusting an uncalibrated single sensor is clinically more dangerous than having no reading at all.
  - **R5 Proof:** TAMAR 315-patient trial documented a 30% measurement failure rate under real-world interference.
- **Visual:** **Scenario Diagram: True State → Sensor Disturbance → Unreliable Reading** — Step-by-step flowchart contrasting silent failure vs. intelligent confidence suppression.

---

### 📍 Slide 7: Our Approach: The Hospital Bed as a Sensing Platform
- **Slide Title:** Our Approach: The Hospital Bed as a Sensing Platform
- **Core Content:**
  - **Retrofit Concept:** Transform standard, non-smart single hospital cots (₹0–5,000 cot cost) into intelligent platforms.
  - **Zero Body Attachment:** All 5 sensors integrated into the bed frame, headboard, mattress, and footpads.
  - **Zero Workflow Interference:** Nurses interact normally without attaching or managing patient cables.
  - **High Reliability at Moderate Cost:** ₹64,280 total prototype cost delivering multi-sensor confidence-gated monitoring.
- **Visual:** **Conceptual Bed Diagram** — Callout diagram of a standard metal cot showing non-contact sensor positions.

---

### 📍 Slide 8: Five Sensors — Three Independent Measurement Pathways
- **Slide Title:** Five Sensors — Three Independent Measurement Pathways
- **Core Content:**
  - **Sensor Array Specifications:**
    1. 📡 **mmWave Radar (HLK-LD6002 60 GHz):** Headboard mounted; measures chest wall displacement (**Air Pathway**).
    2. 🔊 **Geophone (SM-24):** Under-mattress; detects structural BCG micro-vibrations (**Structure Pathway**).
    3. 🟩 **Pressure Matrix (Velostat 12×12):** Mattress surface; posture centroid & contact micro-vibration (**Contact Pathway**).
    4. ⚖️ **Load Cells (4× 50 kg):** Bed leg footpads; weight, occupancy, visitor detection (>30 kg delta), bed exit (<3 s).
    5. 🌡️ **Thermal Dual-Sensing:** Overhead MLX90640 spatial heatmap + Headboard MLX90614 point IR (±0.2°C forehead temp).
  - **Why 3 Pathways?** Cross-validating 3 independent physical mechanisms guarantees high confidence when signals agree.
- **Visual:** **MANDATORY Sensing Architecture Diagram** — Structural block diagram mapping the 5 physical sensors into 3 independent HR/RR pathways and 2 validation channels.

---

### 📍 Slide 9: Hardware Architecture
- **Slide Title:** Hardware Architecture
- **Core Content:**
  - **Sensor Layer:** 60 GHz Radar, SM-24 Geophone, Velostat Matrix, 4× Load Cells, MLX90640 Spatial Thermal, MLX90614 Point IR.
  - **Microcontroller / Edge Layer:**
    - *ESP32 Node:* Multiplexes 12×12 pressure grid (CD74HC4067) + samples load cell ADCs (HX711).
    - *ADS1115 & Level Shifters:* High-resolution 16-bit analog sampling & 3.3V/5V logic conversion.
  - **Processing & Edge Compute:** Raspberry Pi 5 (8 GB LPDDR4X) running real-time signal processing & FastAPI.
  - **Communication & Power:** Wi-Fi MQTT, Direct UART (Radar), I2C (Thermal/ADS1115), regulated 12V DC supply + LM2596 buck converters.
- **Visual:** **MANDATORY Hardware Architecture Diagram** — Hardware block diagram illustrating Sensor Layer → ADC/MCU Layer → Raspberry Pi 5 → Dashboard hardware connection topology.

---

### 📍 Slide 10: Software Architecture & Data Flow
- **Slide Title:** Software Architecture & Data Flow
- **Core Content:**
  - **Data Acquisition:** ESP32 MQTT payloads (10 Hz) + Radar UART stream + I2C thermal polling.
  - **Preprocessing & Filtering:** NumPy/SciPy Butterworth bandpass filters ($0.1\text{–}0.5\text{ Hz}$ breathing, $0.8\text{–}2.5\text{ Hz}$ cardiac) + Pressure grid centroid calculation.
  - **Sensor Fusion & Validity Gating:** Confidence state machine rules.
  - **Storage & API:** SQLite local database flush (every 30 s) + FastAPI WebSocket streaming engine.
  - **Web Dashboard:** HTML/JS real-time single-bed view + Phase 2 simulated ward queue.
- **Visual:** **MANDATORY Software Architecture + Pipeline Diagram** — End-to-end software data flow pipeline from raw bytes to frontend UI.

---

### 📍 Slide 11: The Confidence-Aware Fusion Engine
- **Slide Title:** The Confidence-Aware Fusion Engine
- **Core Content:**
  - **Core Mechanism:** Determine *whether an observation can be trusted* before presenting it on the dashboard.
  - **State Machine Decision Rules:**
    - *Motion Gate:* Pressure matrix temporal change > threshold → Flag "Patient Movement" & pause radar/geophone RR.
    - *Visitor Gate:* Load cell weight delta (>30 kg) + second pressure centroid → Flag "Visitor Present" & suppress vitals.
    - *Blanket Detector:* Thermal contrast drop → Flag "Body Obscured" & pause temperature reading.
    - *3-Way Pathway Agreement:* Radar RR and Geophone RR agree within $\pm2\text{ bpm}$ → Upgrade to **High Confidence**.
- **Visual:** **MANDATORY Fusion Pipeline / Decision Diagram** — Branching decision-tree flow chart illustrating input signals progressing through validity gates.

---

### 📍 Slide 12: From One Bed to a Ward
- **Slide Title:** From One Bed to a Ward
- **Core Content:**
  - **Phase 1 Physical Prototype:** Single-bed hardware collects real scenario recordings (`quiet_rest`, `elevated_rr`, `sustained_pressure`, `visitor_present`, etc.).
  - **Phase 2 Software Ward Simulation:** Composes 4-to-8 virtual bed states into a synthetic ward snapshot.
  - **AI Ward Prioritisation Model:** Trains an XGBoost classifier to rank patient priority (Low, Medium, High, Immediate).
  - **SHAP Explainability Layer (XAI):** Generates readable explanations:
    > *"Bed 3 ranked HIGH: Elevated RR (+35% vs baseline, High Conf) contributed +0.42; Sustained Sacral Pressure (>2.2h) contributed +0.31."*
  - **Cost:** ₹0 extra hardware cost for Phase 2 software ward intelligence.
- **Visual:** **Ward-Level Architecture Diagram** — Network diagram showing Single Bed Hardware → Scenario Logger → Ward Synthesizer → XGBoost/SHAP Priority Dashboard.

---

### 📍 Slide 13: What the Dashboard Tells Nurses
- **Slide Title:** What the Dashboard Tells Nurses
- **Core Content:**
  - **Single-Bed View:** Real-time occupancy status, 4-class posture map, RR with live confidence flag, surface temp trend.
  - **Ward Priority View (Phase 2):** Ranked patient queue with SHAP explainability tooltips.
  - **Raw Data → Actionable Observations:** Translates complex signal states into simple nurse alerts:
    - *"Patient stationary for 3 hours — check pressure risk"* (observational, non-diagnostic).
    - *"Second person detected on bed — physiological readings paused"*.
- **Visual:** **Dashboard Mock-Up** — UI mockup screenshot displaying the Single-Bed observation UI and Ward Priority queue with SHAP tooltips.

---

### 📍 Slide 14: Evidence, Research Novelty, Budget & Expected Contribution
- **Slide Title:** Evidence, Research Novelty, Budget & Expected Contribution
- **Core Content:**
  - **Evidence Base (R1–R8):** Grounded in recent 2025–2026 literature (R1 load cells, R5 radar failure analysis, R8 geophone BCG).
  - **Research Gap:** No prior study combines 3 independent physiological pathways with explicit interference confidence gating in a low-cost retrofit bed.
  - **Prototype Budget (₹64,280 Verified):** RPi 5 8GB (₹20k), MLX90640 (₹5k), Radar (₹2.2k), Geophone (₹500), Velostat (₹3.8k), Load cells (₹540), Fabrication & Validation (₹32k). Surplus ₹35.7k reserved for Phase 2.
  - **Expected Research Contribution:** Validated physical prototype + dataset + SHAP explainable multi-patient ward simulation paper.
- **Visual:** **Research-Gap Map + Budget Pie Chart** — 4-quadrant research novelty matrix alongside the embedded Mermaid Donut Chart of the ₹64,280 budget.

---

### 📍 Slide 15: Thank You
- **Slide Title:** Thank You
- **Core Content:**
  - **Project Name:** AI-Powered Multimodal Contactless Patient Monitoring System
  - **One-Line Vision:** *"Affordable, Unobtrusive, Confidence-Aware Patient Monitoring for Resource-Constrained Healthcare."*
  - **Team & Institution:** Department of Biomedical Engineering / Computer Science, Coimbatore, Tamil Nadu, India.
  - **Project Links:** GitHub Repository Link & Contact Information.
- **Visual:** **Minimal** — Minimalist closing slide displaying team details, project logo, contact email, and repository QR code.

---

*Slide Structure Specification — Aligned with Analysis and Validation.md & Validated Concept.md | August 2026*
