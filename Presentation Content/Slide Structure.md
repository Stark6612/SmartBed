# Presentation Slide Structure — Smart Bed V2

> **Presentation Overview:** 15-Slide Presentation Structure  
> **Target Audience:** Project Evaluators, Department Head, Technical Committee, Institutional Reviewers  
> **Budget Reflected:** ₹64,280 (5-sensor full research prototype)

---

## 📋 Master 15-Slide Presentation Table

| Slide # | Slide Title | Purpose |
|---|---|---|
| **1** | **Project Title** | Project name, one-line vision, team/institution |
| **2** | **The Monitoring Gap in Indian Hospital Wards** | Clinical problem: monitoring burden, staff workload, missed/limited continuous observations |
| **3** | **Why Contact-Based Monitoring Has Limits** | Wires, attachment, displacement, discomfort, maintenance and fragmented monitoring |
| **4** | **Contactless Systems Already Work — in Labs and Hospitals** | Establish evidence that contactless monitoring is technically feasible using recent research |
| **5** | **Why Existing Contactless Systems Are Not the Answer** | Cost, infrastructure requirements, limited integration and limitations of single-modality systems |
| **6** | **The Silent Failure Problem** | Explain how a sensor can produce unreliable data without clearly indicating that the measurement is unreliable |
| **7** | **Our Approach: The Hospital Bed as a Sensing Platform** | Retrofit existing beds/cots rather than replacing them; unobtrusive sensing architecture |
| **8** | **Five Sensors — Three Independent Measurement Pathways** | Explain the sensing strategy and why independent/complementary pathways improve reliability |
| **9** | **The Confidence-Aware Fusion Engine** | Core research concept: determine *whether a measurement can be trusted* before using it |
| **10** | **From One Bed to a Ward** | How the architecture can eventually scale to multiple beds, patient prioritisation and ward-level monitoring |
| **11** | **What the Dashboard Tells Nurses** | Show practical output: occupancy, RR, confidence, position, movement and alerts — without diagnostic claims |
| **12** | **Evidence Base: Recent Research (2025–2026)** | Present the key papers supporting the sensing technologies, multimodal monitoring and clinical direction |
| **13** | **Budget: ₹64,280 for the Full Prototype** | Show realistic prototype expenditure and explain how the remaining funding can support further research |
| **14** | **Research Novelty & Proposed Contribution** | Clearly state the research gap and what your project contributes: multimodal pathways + confidence-aware fusion + affordable retrofit architecture |
| **15** | **Thank You** | Final project statement/contact/team information |

---

---

## 🔍 Slide-by-Slide Content & Visual Details

### 📍 Slide 1: Project Title
- **Slide Title:** Project Title
- **Purpose:** Project name, one-line vision, team/institution.
- **Key Content:**
  - **Project Title:** AI-Powered Multimodal Contactless Patient Monitoring and Clinical Decision Support System Using the Hospital Bed as an Unobtrusive Sensing Platform
  - **One-Line Vision:** Transforming standard hospital cots into intelligent, confidence-aware patient monitoring platforms at moderate cost.
  - **Team & Institution:** Department of Biomedical Engineering / Computer Science, Coimbatore, Tamil Nadu, India.
- **Visual Suggestion:** High-impact hero graphic displaying the retrofitted hospital bed layout with 5 sensor callout badges.

---

### 📍 Slide 2: The Monitoring Gap in Indian Hospital Wards
- **Slide Title:** The Monitoring Gap in Indian Hospital Wards
- **Purpose:** Clinical problem: monitoring burden, staff workload, missed/limited continuous observations.
- **Key Content:**
  - High nurse-to-patient ratios (15 to 40 patients per nurse in general & government wards).
  - Intermittent vital signs checking (every 4 to 8 hours) leaves long unmonitored windows where deterioration can occur unnoticed.
  - Heavy documentation workload reduces time for direct patient care.
- **Visual Suggestion:** Split illustration: High nurse workload vs. timeline showing critical unmonitored gaps between manual rounds.

---

### 📍 Slide 3: Why Contact-Based Monitoring Has Limits
- **Slide Title:** Why Contact-Based Monitoring Has Limits
- **Purpose:** Wires, attachment, displacement, discomfort, maintenance and fragmented monitoring.
- **Key Content:**
  - **Attachment Friction:** Electrodes and pulse oximeter clips disconnect frequently during sleep or patient movement.
  - **Discomfort & Skin Trauma:** Adhesive pads cause skin irritation in pediatric and geriatric patients.
  - **Maintenance Burden:** Continuous cable sanitisation and replacement overhead.
  - **Fragmented Data:** Disconnected monitors result in missing or incomplete trend records.
- **Visual Suggestion:** Comparison icons showing sensor dislodgement, wire clutter, skin irritation, and data loss.

---

### 📍 Slide 4: Contactless Systems Already Work — in Labs and Hospitals
- **Slide Title:** Contactless Systems Already Work — in Labs and Hospitals
- **Purpose:** Establish evidence that contactless monitoring is technically feasible using recent research.
- **Key Content:**
  - **Padaki et al. (Jan 2026, 111 ED Patients):** Camera rPPG validated in emergency departments (HR RMSE 1.62 bpm, RR RMSE 1.71 bpm).
  - **Shaya, Levy et al. (Jun 2026, 315 ED Patients):** TAMAR 24 GHz Doppler radar validated across 3 emergency departments.
  - **Pitafi et al. (Feb 2026):** Geophone BCG under mattress achieved MAE < 2 bpm on Raspberry Pi edge hardware.
- **Visual Suggestion:** Summary evidence cards citing R4, R5, and R8 with clinical accuracy metrics.

---

### 📍 Slide 5: Why Existing Contactless Systems Are Not the Answer
- **Slide Title:** Why Existing Contactless Systems Are Not the Answer
- **Purpose:** Cost, infrastructure requirements, limited integration and limitations of single-modality systems.
- **Key Content:**
  - **Exorbitant Cost:** Commercial smart beds (Stryker, Invacare) cost ₹10–50 lakh per unit — unviable for general wards.
  - **Rigid Infrastructure:** Requires replacing entire hospital bed inventory rather than retrofitting.
  - **Single-Modality Fragility:** Single-sensor systems (camera-only or radar-only) fail under movement, blankets, or visitor presence.
- **Visual Suggestion:** High cost indicator graphic vs. single-sensor vulnerability examples.

---

### 📍 Slide 6: The Silent Failure Problem
- **Slide Title:** The Silent Failure Problem
- **Purpose:** Explain how a sensor can produce unreliable data without clearly indicating that the measurement is unreliable.
- **Key Content:**
  - **The Risk:** When patient movement, blankets, or visitors corrupt radar or thermal signals, single-sensor systems output erroneous numbers *without warning*.
  - Silent measurement failure is clinically more dangerous than acknowledging measurement unavailability.
  - **R5 Evidence:** TAMAR 315-patient trial proved radar failed to produce valid measurements in 30% of cases due to interference.
- **Visual Suggestion:** Flowchart showing a corrupt signal yielding a misleading false output vs. an intelligent confidence gate suppressing it.

---

### 📍 Slide 7: Our Approach: The Hospital Bed as a Sensing Platform
- **Slide Title:** Our Approach: The Hospital Bed as a Sensing Platform
- **Purpose:** Retrofit existing beds/cots rather than replacing them; unobtrusive sensing architecture.
- **Key Content:**
  - **Retrofit Philosophy:** Integrates sensor hardware directly onto existing single-person hospital metal cots (₹0 to ₹5,000 cot cost).
  - **Zero Body Contact:** Unobtrusive sensors placed at headboard, under mattress, on bed surface, and at bed leg footpads.
  - **Zero Workflow Friction:** Nurses operate normally without attaching or managing patient leads.
- **Visual Suggestion:** Annotated 3D schematic of retrofitted cot highlighting headboard, under-mattress, surface, and footpad sensor placements.

---

### 📍 Slide 8: Five Sensors — Three Independent Measurement Pathways
- **Slide Title:** Five Sensors — Three Independent Measurement Pathways
- **Purpose:** Explain the sensing strategy and why independent/complementary pathways improve reliability.
- **Key Content:**
  - 📡 **mmWave Radar (60 GHz FMCW, HLK-LD6002):** Through-air chest wall displacement (Pathway 1).
  - 🔊 **Geophone (SM-24):** Under-mattress structural BCG velocity micro-vibration (Pathway 2).
  - 🟩 **Pressure Matrix (Velostat 12×12):** Surface posture centroid & contact micro-vibration (Pathway 3).
  - ⚖️ **Load Cells (4× 50 kg):** Bed leg footpads for weight, occupancy, visitor detection (>30 kg delta), and bed exit (<3 s).
  - 🌡️ **Thermal Dual-Sensing:** Overhead MLX90640 spatial heatmap + Headboard MLX90614 point IR (±0.2°C).
- **Visual Suggestion:** Architecture diagram mapping 5 physical sensors into 3 independent HR/RR pathways and 2 validation channels.

---

### 📍 Slide 9: The Confidence-Aware Fusion Engine
- **Slide Title:** The Confidence-Aware Fusion Engine
- **Purpose:** Core research concept: determine *whether a measurement can be trusted* before using it.
- **Key Content:**
  - **Motion Gate:** Pressure matrix & load cell temporal variance detects patient movement → pauses physiological extraction.
  - **Visitor Gate:** Load cell weight delta (>30 kg) + secondary pressure centroid → flags second occupant & suppresses vitals.
  - **Blanket Detector:** Thermal contrast drop flags obscured skin → suppresses temperature with explicit warning.
  - **3-Way Pathway Agreement:** High confidence assigned when radar RR and geophone RR agree within ±2 bpm.
- **Visual Suggestion:** Logic decision-tree state machine showing inputs branching into High Confidence, Low Confidence, or Suppressed states.

---

### 📍 Slide 10: From One Bed to a Ward
- **Slide Title:** From One Bed to a Ward
- **Purpose:** How the architecture can eventually scale to multiple beds, patient prioritisation and ward-level monitoring.
- **Key Content:**
  - **Phase 1 Physical Prototype:** Single-bed hardware collects real scenario recordings (`quiet_rest`, `elevated_rr`, `sustained_pressure`, etc.).
  - **Phase 2 Ward Simulation:** Synthetically composes single-bed recordings into 4-to-8 bed virtual ward snapshots.
  - **AI Ward Prioritisation & XAI:** Trains an XGBoost classifier paired with SHAP (SHapley Additive exPlanations) to rank patient priority:
    > *"Bed 3 ranked HIGH: Elevated RR (+35% vs baseline) contributed +0.42; Sustained Sacral Pressure (>2.2h) contributed +0.31."*
  - **Cost:** ₹0 additional hardware cost for Phase 2 software expansion.
- **Visual Suggestion:** Architecture diagram showing Single-Bed Hardware → Scenario Logger → Virtual Ward Synthesizer → SHAP Priority Output.

---

### 📍 Slide 11: What the Dashboard Tells Nurses
- **Slide Title:** What the Dashboard Tells Nurses
- **Purpose:** Show practical output: occupancy, RR, confidence, position, movement and alerts — without diagnostic claims.
- **Key Content:**
  - **Single-Bed View:** Real-time occupancy status, posture classification map, RR with live confidence flag, surface temp trend.
  - **Ward Priority View (Phase 2):** Ranked patient queue with SHAP explainability tooltips.
  - **Actionable Observation Alerts:** "Patient stationary 3 hours — check pressure risk" (observational, non-diagnostic).
- **Visual Suggestion:** Clean UI wireframe mockups of the Single-Bed view and Ward Priority queue interface.

---

### 📍 Slide 12: Evidence Base: Recent Research (2025–2026)
- **Slide Title:** Evidence Base: Recent Research (2025–2026)
- **Purpose:** Present the key papers supporting the sensing technologies, multimodal monitoring and clinical direction.
- **Key Content:**
  - **R1 (Lee et al., Aug 2025):** Bed load cell fusion achieves 96.26% fall/exit detection accuracy.
  - **R2 (López-Ruiz et al., Sep 2025):** Mattress micro-vibrations carry reliable cardiac & respiratory signals.
  - **R5 (Shaya et al., Jun 2026):** 315-patient ED trial proves single-sensor radar needs multimodal validity gating.
  - **R7 (Reyes et al., 2026):** SiViS dataset highlights multi-patient radar challenges, justifying our simulation approach.
  - **R8 (Pitafi et al., Feb 2026):** Confirms Raspberry Pi 5 capability for geophone BCG signal extraction (MAE < 2 bpm).
- **Visual Suggestion:** Structured matrix linking each sensor component to its supporting 2025–2026 paper citation.

---

### 📍 Slide 13: Budget: ₹64,280 for the Full Prototype
- **Slide Title:** Budget: ₹64,280 for the Full Prototype
- **Purpose:** Show realistic prototype expenditure and explain how the remaining funding can support further research.
- **Key Content:**
  - **Processing Platform (40.7%):** Raspberry Pi 5 8 GB (₹20,000), active cooler, 64 GB microSD A2, PSU, case.
  - **Sensors & Electronics (25.1%):** Radar, geophone, Velostat sheets, load cells, thermal camera, ESP32, ADCs, muxes.
  - **Fabrication & Validation (34.2%):** Bed frame, foam mattress, MS mounts, enclosures, test weights, honoraria, ethics docs.
  - **Total Budget:** ₹64,280 (worst case) / ₹61,480 (best case with institutional access).
  - **Surplus Strategy:** Remaining ₹35,720 retained for Phase 2 clinical-site testing at an affiliated hospital.
- **Visual Suggestion:** Embedded Mermaid Donut Chart showing category percentages + key stat cards.

---

### 📍 Slide 14: Research Novelty & Proposed Contribution
- **Slide Title:** Research Novelty & Proposed Contribution
- **Purpose:** Clearly state the research gap and what your project contributes: multimodal pathways + confidence-aware fusion + affordable retrofit architecture.
- **Key Content:**
  - **Defensible Research Gap:** No prior study demonstrates an integrated <USD 750 system combining 3 independent physiological pathways (radar, geophone, pressure BCG) with explicit interference detection.
  - **Core Contributions:**
    1. Triple-pathway cross-validated physiological sensing.
    2. Confidence-aware validity gating for real-world ward conditions.
    3. Affordable bed-retrofit architecture for resource-constrained hospitals.
    4. Simulation-grounded XAI ward prioritisation using real single-bed recordings.
- **Visual Suggestion:** 4-quadrant contribution matrix comparing our system against current literature.

---

### 📍 Slide 15: Thank You
- **Slide Title:** Thank You
- **Purpose:** Final project statement/contact/team information.
- **Key Content:**
  - Project Title & Team Contact Email / Department Address.
  - GitHub Project Repository Link.
  - **Final Project Statement:** *"Affordable, Unobtrusive, Confidence-Aware Patient Monitoring for Resource-Constrained Healthcare."*
- **Visual Suggestion:** Minimalist closing slide with team contact details, repository QR code, and final project motto.

---

*Slide Structure Document — Aligned with Analysis and Validation.md & Validated Concept.md | August 2026*
