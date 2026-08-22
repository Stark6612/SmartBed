# Slide Structure — Smart Bed V2 Proposal Presentation

> **Presentation Overview:** 15-Slide Presentation Structure  
> **Target Audience:** Project Evaluators, Department Head, Technical Committee, Institutional Reviewers  
> **Key Shift:** Funding ask and validation plan slides have been replaced with dedicated Technical Roadmap, Impact Summary, Title, and Thank You slides.

---

## Slide Overview Table

| Slide # | Slide Title | Core Purpose |
|---|---|---|
| **1** | Title Slide | Project Title, Subtitle, Presenters & Institutional Affiliation |
| **2** | Problem Statement | The Monitoring Gap in Resource-Constrained Hospital Wards |
| **3** | Limitations of Contact-Based Monitoring | Why traditional wired sensors fail in high-workload wards |
| **4** | State of Contactless Monitoring & Clinical Evidence | Proving technology feasibility using recent 2025–2026 clinical studies |
| **5** | The "Silent Failure" Problem | Why single-sensor contactless systems fail 30% of the time without warning |
| **6** | Proposed Solution: Bed-Retrofit Sensing Platform | The core concept: retrofitting standard hospital cots at minimal cost |
| **7** | Five-Sensor Architecture & 3 Physiological Pathways | Radar (air), Geophone (structural), Pressure Matrix, Load Cells, Thermal |
| **8** | Confidence-Aware Multimodal Fusion Engine | Rule-based state machine detecting movement, visitors, and blankets |
| **9** | Multi-Patient Simulation & Explainable AI (XAI) | Phase 2 software ward simulation + XGBoost priority queue + SHAP explanations |
| **10** | Nurse Dashboard & Actionable Observation Alerts | UI design: single-bed observation + ward priority queue without diagnostic overclaims |
| **11** | Scientific Evidence Base (2025–2026 Literature) | Backing every sensor selection with 8 peer-reviewed research papers (R1–R8) |
| **12** | Prototype Budget & Economic Viability | Cost breakdown: ₹64,280 prototype vs. ₹10–50 lakh commercial smart beds |
| **13** | Core Research Novelty & Defensible Research Gap | Defining the exact academic contribution and technical gap filled |
| **14** | Summary Impact & Technical Roadmap | 18-week execution milestones and expected research outputs |
| **15** | Thank You | Q&A, Contact Details, Project Repository Link |

---

---

## Detailed Slide-by-Slide Breakdown

### 📍 Slide 1: Title Slide
- **Title:** AI-Powered Multimodal Contactless Patient Monitoring System
- **Subtitle:** Using the Hospital Bed as an Unobtrusive Sensing Platform
- **Key Points:**
  - Student Research Team & Department Affiliation
  - Project Location: Coimbatore, Tamil Nadu, India
  - Prototype Focus: Low-Cost, Quality-Oriented Research Prototype
- **Visual Suggestion:** High-impact hero graphic showing the 5-sensor retrofitted hospital bed layout.

---

### 📍 Slide 2: Problem Statement
- **Title:** The Vital Signs Monitoring Gap in Resource-Constrained Wards
- **Core Message:** High patient-to-nurse ratios (15–40 patients per nurse) in general and government hospital wards lead to infrequent vital sign checks (every 4–8 hours).
- **Key Points:**
  - Patient deterioration between manual rounds often goes unnoticed until critical.
  - ICU continuous monitoring equipment is too expensive and scarce for general ward deployment.
  - Need for an affordable, continuous, non-intrusive observation solution.
- **Visual Suggestion:** Split visual showing a crowded hospital ward vs. a timeline illustrating missing vital checks between nurse rounds.

---

### 📍 Slide 3: Limitations of Contact-Based Monitoring
- **Title:** Why Traditional Contact-Based Sensors Fail in Routine Wards
- **Core Message:** Electrodes, pulse oximeter clips, and wires cause operational friction in non-ICU environments.
- **Key Points:**
  - **Sensor Displacement:** Leads disconnect frequently during patient movement or sleep.
  - **Skin Trauma & Discomfort:** Prolonged adhesive electrodes cause skin irritation in elderly/pediatric patients.
  - **Hygiene & Maintenance Burden:** Cables require constant sanitisation and replacement.
  - **Patient Resistance:** Conscious patients frequently detach wired sensors voluntarily.
- **Visual Suggestion:** Comparison icons illustrating tangled wires, skin irritation, and frequent sensor dislodgement.

---

### 📍 Slide 4: State of Contactless Monitoring & Clinical Evidence
- **Title:** Contactless Monitoring Works — Clinical Proof (2025–2026)
- **Core Message:** Recent peer-reviewed studies confirm contactless vitals (radar, camera, BCG) are accurate under controlled conditions.
- **Key Points:**
  - **Padaki et al. (Jan 2026, 111 ED Patients):** Camera rPPG achieved HR RMSE 1.62 bpm, RR RMSE 1.71 bpm in real hospital settings.
  - **Shaya, Levy et al. (Jun 2026, 315 ED Patients):** TAMAR 24 GHz radar validated in emergency departments (RR LOA ±1.6 bpm).
  - **Pitafi et al. (Feb 2026):** Geophone BCG under mattress achieved MAE < 2 bpm on Raspberry Pi hardware.
- **Visual Suggestion:** Summary cards featuring citations of R4, R5, and R8 with correlation graphs.

---

### 📍 Slide 5: The "Silent Failure" Problem in Single-Sensor Systems
- **Title:** The Unseen Danger: Silent Measurement Corruption
- **Core Message:** Single-sensor contactless devices fail up to 30% of the time under real ward conditions without notifying staff.
- **Key Points:**
  - **Movement Artifacts:** Patient motion causes radar/camera to output corrupted numbers instead of pausing.
  - **Multiple Occupants:** Visitors sitting on the bed corrupt radar phase signals without detection.
  - **Blanket Obstruction:** Blankets completely block thermal IR radiation while sensors silently report ambient temp.
  - **Our Solution:** Multimodal fusion to explicitly detect interference and state measurement confidence.
- **Visual Suggestion:** Flowchart showing a single-sensor false output vs. a confidence-gated suppressed output.

---

### 📍 Slide 6: Proposed Solution — Hospital Bed as a Sensing Platform
- **Title:** Retrofitting Standard Cots into Unobtrusive Sensing Platforms
- **Core Message:** Avoid buying expensive smart beds — integrate low-cost, robust sensors into existing hospital bed frames.
- **Key Points:**
  - Zero direct body contact — sensors integrated into bed frame, mattress, and headboard.
  - Zero modification to routine clinical workflows.
  - Moderate-cost, high-reliability design philosophy.
- **Visual Suggestion:** 3D diagram of a standard metal cot highlighting retrofitted sensor mount zones.

---

### 📍 Slide 7: Five-Sensor Architecture & 3 Physiological Pathways
- **Title:** Multimodal Sensing Array & Triple-Pathway Cross-Validation
- **Core Message:** Five complementary sensors create 3 independent measurement paths for vital signs.
- **Key Points:**
  - 📡 **mmWave Radar (60 GHz FMCW, HLK-LD6002):** Headboard mounted; measures chest wall displacement (Air path).
  - 🔊 **Geophone (SM-24):** Under mattress; measures structural BCG micro-vibrations (Structure path).
  - 🟩 **Pressure Matrix (Velostat 12×12):** Torso area; spatial posture centroid & contact micro-vibration (Contact path).
  - ⚖️ **Load Cells (4× 50 kg):** Bed leg footpads; weight, occupancy, visitor detection & bed-exit.
  - 🌡️ **Thermal Dual-Sensing:** Overhead MLX90640 spatial heatmap + MLX90614 point IR (±0.2°C forehead temp).
- **Visual Suggestion:** Sensor architecture table mapping each sensor to its physical placement and primary signal path.

---

### 📍 Slide 8: Confidence-Aware Multimodal Fusion Engine
- **Title:** Intelligent Validity Gating & Interference Detection
- **Core Message:** The AI fusion engine decides *if* a measurement can be trusted before publishing it.
- **Key Points:**
  - **Motion Gate:** Suppresses radar/geophone vitals when pressure matrix detects temporal movement.
  - **Visitor Gate:** Load cell weight delta (>30 kg) + secondary pressure centroid pauses physiological readings.
  - **Blanket Detector:** Thermal contrast drop suppresses surface temp reading with a clear warning flag.
  - **3-Way Pathway Agreement:** High confidence assigned when radar RR and geophone RR agree within ±2 bpm.
- **Visual Suggestion:** Logic decision-tree diagram showing input signals leading to High Confidence, Low Confidence, or Suppressed states.

---

### 9: Multi-Patient Simulation & Explainable AI (XAI)
- **Title:** Phase 2: Software Ward Simulation & SHAP Explainability
- **Core Message:** Single-bed hardware data powers a software-simulated multi-patient ward prioritisation system.
- **Key Points:**
  - **Scenario Data Collection:** Record labelled single-bed scenarios (`quiet_rest`, `restless`, `elevated_rr`, `sustained_pressure`).
  - **Ward Snapshot Synthesizer:** Composes virtual 4-to-8 bed wards to train an XGBoost priority ranking classifier.
  - **SHAP Explainability Layer:** Provides natural-language reasons for every priority decision:
    > *"Patient Bed 3 ranked HIGH: Elevated RR (+35% above baseline, High Conf) contributed +0.42; Sustained Pressure (>2.2h) contributed +0.31."*
  - **Cost Impact:** ₹0 extra — pure software Phase 2 running on Raspberry Pi 5 or laptop.
- **Visual Suggestion:** Diagram mapping Phase 1 hardware data → Synthetic Ward Simulation → XGBoost Model → SHAP Output string.

---

### 📍 Slide 10: Clinical Dashboard & Actionable Nurse Alerts
- **Title:** Intuitive Nurse Interface: Observations, Not Overclaims
- **Core Message:** A simple, high-visibility web dashboard designed for fast nursing interpretation.
- **Key Points:**
  - **Single-Bed View:** Real-time occupancy status, posture map, RR with confidence indicator, temperature trend.
  - **Ward Priority View (Phase 2):** Ranked patient queue with SHAP explainability tooltips.
  - **Actionable Alerts:** "Patient stationary 3 hours — check pressure risk" (no diagnostic overclaims).
- **Visual Suggestion:** Clean UI wireframe mockups of the Single-Bed view and Ward Priority queue.

---

### 11: Scientific Evidence Base (2025–2026 Literature)
- **Title:** Grounded in Recent Peer-Reviewed Research
- **Core Message:** Every sensor selection and architectural decision is directly justified by recent literature.
- **Key Points:**
  - **R1 (Lee et al., Aug 2025):** Bed load cell fusion achieves 96.26% fall/exit detection accuracy.
  - **R3 (Chen et al., 2024):** 60 GHz mmWave FMCW radar validated for chest displacement extraction.
  - **R5 (Shaya et al., Jun 2026):** 315-patient ED trial proves single-sensor radar needs multimodal validity gating.
  - **R7 (Reyes et al., 2026):** SiViS dataset highlights multi-patient radar challenges, justifying our simulation approach.
  - **R8 (Pitafi et al., Feb 2026):** Confirms Raspberry Pi 5 capability for geophone BCG signal extraction (MAE < 2 bpm).
- **Visual Suggestion:** A structured matrix linking each sensor component to its supporting 2025–2026 paper citation.

---

### 📍 Slide 12: Prototype Budget & Economic Viability
- **Title:** Comprehensive ₹64,280 Prototype Budget Breakdown
- **Core Message:** Delivering a 5-sensor AI-fused prototype at a fraction of commercial smart bed costs.
- **Key Points:**
  - **Processing Platform (40.7%):** Raspberry Pi 5 8 GB (₹20,000), active cooler, 64 GB microSD A2, PSU, case.
  - **Sensors & Electronics (25.1%):** Radar, geophone, Velostat sheets, load cells, thermal camera, ESP32, ADCs, muxes.
  - **Fabrication & Calibration (26.7%):** Bed cot frame, foam mattress, MS mounts, camera arm, enclosures, test weights.
  - **Contingency & Reserve (7.4%):** ₹4,555 buffer; institutional access for reference scale/spirometer/oximeter saves ₹2,800.
  - **Economic Comparison:** ₹64,280 prototype vs. ₹10,000,00+ commercial smart beds (93%+ cost reduction).
- **Visual Suggestion:** Embedded Mermaid Donut Chart showing category percentages + key stat cards.

---

### 📍 Slide 13: Core Research Novelty & Defensible Research Gap
- **Title:** Academic Contribution: What Makes This Research Novel
- **Core Message:** Filling a documented gap in affordable, interference-explicit healthcare sensing.
- **Key Points:**
  - **Triple-Pathway BCG Fusion:** Combining radar, geophone, and pressure matrix BCG in a single bed platform.
  - **Explicit Interference Awareness:** Systematically modeling *when* measurements are invalid (movement/visitor/blanket).
  - **Low-Cost Bed Retrofit:** Accessible architecture designed specifically for resource-constrained general wards.
  - **Simulated Ward XAI:** Combining single-bed physical data with synthetic ward composition and SHAP explainability.
- **Visual Suggestion:** A 4-quadrant feature comparison matrix highlighting our system vs. existing research papers.

---

### 📍 Slide 14: Summary Impact & Technical Roadmap
- **Title:** Execution Roadmap & Expected Outcomes
- **Core Message:** Structured 18-week execution plan delivering a validated physical prototype and software ward simulation.
- **Key Points:**
  - **Weeks 1–4 (Phase 1 Build):** Hardware integration, load cell tare calibration, pressure grid scan characterisation.
  - **Weeks 5–8 (Phase 2 Fusion):** Motion gate, visitor detection (>90% accuracy target), and 3-way RR agreement logic.
  - **Weeks 9–14 (Phase 3 Trials):** 10 volunteer testing sessions (IRB ethics cleared) collecting scenario dataset.
  - **Weeks 15–18 (Phase 4 Simulation & Paper):** SHAP multi-patient model training, reference comparison, conference paper draft.
- **Visual Suggestion:** Clean 4-phase horizontal timeline chart with milestone badges.

---

### 📍 Slide 15: Thank You & Q&A
- **Title:** Thank You
- **Subtitle:** Questions & Discussion
- **Key Points:**
  - Project Title & Team Contact Email / Department Address
  - GitHub Project Repository Link
  - Summary Highlight: *"Affordable, Unobtrusive, Confidence-Aware Patient Monitoring for Resource-Constrained Healthcare."*
- **Visual Suggestion:** Minimalist closing slide with team contact details, repository QR code, and core project motto.

---

*Slide Structure Document — Aligned with Analysis and Validation.md & Validated Concept.md | August 2026*
