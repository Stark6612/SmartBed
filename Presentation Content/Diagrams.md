# Presentation Diagrams — Napkin AI Prompt Guide

> **Purpose:** Detailed descriptions and copy-paste prompts for generating visual diagrams in **Napkin AI** (or similar visual diagram generators) for all 15 presentation slides of the Smart Bed V2 project.
>
> **How to Use with Napkin AI:**
> 1. Copy the text inside the **"📋 Napkin AI Copy-Paste Text"** block for the desired slide.
> 2. Paste it directly into Napkin AI text editor.
> 3. Click **"Generate Visual"** next to the text block.
> 4. Adjust the diagram style (Flowchart, Grid, Comparison, Matrix, Timeline) using the suggested format.

---

## 📍 Slide 1: Hero Concept Diagram

* **Diagram Title:** Smart Bed V2 Unobtrusive Sensing Platform
* **Suggested Napkin AI Format:** Hero Conceptual Product Diagram / Key Pillars Grid

### 📋 Napkin AI Copy-Paste Text:
```text
Smart Bed V2: Retrofitting Hospital Cots into Intelligent Sensing Platforms

Core Retrofit Approach:
• Standard Metal Bed Cot — Zero replacement cost; fits existing hospital furniture
• Zero Patient Contact — No wires, adhesive patches, or body-attached leads
• Five Sensor Modalities — Multi-sensory observation array integrated into bed structure
• Confidence-Aware AI — Real-time measurement validity verification before nurse alert

Key Advantages:
1. Low Cost: ₹64,280 prototype total vs ₹10–50 Lakh commercial smart beds
2. Unobtrusive: Patients rest naturally without monitoring discomfort
3. Workflow Friendly: Zero change to routine clinical nursing procedures
```

---

## 📍 Slide 2: Clinical Monitoring Gap Matrix

* **Diagram Title:** Ward Monitoring Reality vs Patient Risk
* **Suggested Napkin AI Format:** Stat Callout Grid / 2x2 Problem Comparison

### 📋 Napkin AI Copy-Paste Text:
```text
The Clinical Monitoring Gap in Resource-Constrained Wards

Current Ward Reality:
• Staff Ratio: 15 to 40 Patients per Nurse in general/government wards
• Round Frequency: Manual vital sign checks occur only every 4 to 8 hours
• Documentation Burden: Heavy paperwork reduces bedside clinical observation time
• Equipment Shortage: ICU continuous monitoring hardware is unavailable in general wards

Impact on Patient Safety:
→ Long Unmonitored Windows: 6+ hours between manual rounds
→ Silent Deterioration: Early physiological decline missed until acute crisis
→ Delayed Intervention: Emergency response triggered late in disease progression
```

---

## 📍 Slide 3: Pain Points of Contact-Based Sensors

* **Diagram Title:** Operational Failure Points of Wired Contact Sensors
* **Suggested Napkin AI Format:** Feature List with Warning Icons / Problem Tree

### 📋 Napkin AI Copy-Paste Text:
```text
Why Contact-Based Sensors Fail in Routine Wards

1. Sensor Displacement
   • ECG leads & finger clips detach frequently during movement or sleep
   • Triggers frequent false alarms and clinical alarm fatigue

2. Skin Trauma & Discomfort
   • Prolonged adhesive pads cause skin tears in pediatric and geriatric patients
   • Conscious patients voluntarily detach uncomfortable cables

3. Maintenance Overhead
   • Continuous cleaning, sanitisation, untangling, and cable replacement
   • High recurring operational expenditure for hospitals

4. Fragmented Data Records
   • Intermittent lead dislodgement creates broken health records
   • Hinders continuous trend tracking in electronic health records
```

---

## 📍 Slide 4: Clinical Research Evidence Map

* **Diagram Title:** 2025–2026 Clinical Evidence Benchmarks
* **Suggested Napkin AI Format:** Evidence Table / Milestone Cards

### 📋 Napkin AI Copy-Paste Text:
```text
Clinically Validated Feasibility of Contactless Sensing (2025–2026 Literature)

1. Padaki et al. (Jan 2026) — Frontiers in Medical Technology
   • Sample Size: 111 Emergency Department Patients
   • Technology: Camera rPPG
   • Result: Heart Rate RMSE 1.62 bpm | Respiratory Rate RMSE 1.71 bpm

2. Shaya, Levy et al. (Jun 2026) — Frontiers in Medical Technology
   • Sample Size: 315 Emergency Department Patients across 3 Hospitals
   • Technology: 24 GHz Doppler Radar (TAMAR System)
   • Result: Respiratory Rate Limit of Agreement ±1.6 bpm

3. Pitafi et al. (Feb 2026) — MDPI Sensors
   • Sample Size: 75 Human Subjects + Raspberry Pi Testbed
   • Technology: Geophone Under-Mattress BCG
   • Result: HR & RR Mean Absolute Error < 2 bpm on edge hardware

4. Lee, Kim & Jeong (Aug 2025) — Elsevier Measurement
   • Technology: Bed-Frame Load Cells
   • Result: 96.26% Fall and Bed-Exit Detection Accuracy
```

---

## 📍 Slide 5: Existing Approach Comparison Matrix

* **Diagram Title:** Commercial Smart Beds vs Single-Sensor vs Smart Bed V2
* **Suggested Napkin AI Format:** 3-Column Comparison Matrix

### 📋 Napkin AI Copy-Paste Text:
```text
Comparison: Existing Contactless Approaches vs Smart Bed V2

1. Commercial Smart Beds (Stryker / Invacare)
   • Cost: ₹10,000,00 to ₹50,000,00 (High)
   • Infrastructure: Requires replacing entire hospital bed inventory
   • Sensor Modalities: 1 to 2 built-in sensors
   • Interference Handling: Poor (no movement/visitor gating)
   • Ward Accessibility: Low (ICU only)

2. Single-Sensor Systems (Radar-Only or Camera-Only)
   • Cost: ₹5,000,00 to ₹15,000,00 (Moderate)
   • Infrastructure: Fixed wall/ceiling mounting required
   • Sensor Modalities: 1 single modality
   • Interference Handling: Fails silently during movement or blankets
   • Ward Accessibility: Moderate

3. Smart Bed V2 (Our Proposed Retrofit System)
   • Cost: ₹64,280 (Low / Affordable)
   • Infrastructure: Retrofits existing hospital cots (Zero bed replacement)
   • Sensor Modalities: 5 complementary sensors
   • Interference Handling: Confidence-aware validity state machine
   • Ward Accessibility: High (Designed for general wards)
```

---

## 📍 Slide 6: The Silent Failure Problem (MAIN PROBLEM)

* **Diagram Title:** Single-Sensor Silent Corruption vs Confidence Gating
* **Suggested Napkin AI Format:** Split Scenario Diagram / Flowchart Comparison

### 📋 Napkin AI Copy-Paste Text:
```text
The Silent Failure Problem in Contactless Sensing

Scenario A: Standard Single-Sensor Radar (DANGEROUS)
Step 1: Patient turns over or visitor sits on bed
Step 2: Radar receives phase noise or visitor breathing signal
Step 3: System calculates corrupted data without warning
Step 4: Output → Reports false Respiratory Rate (e.g. 24 bpm) to nurse
Result: Clinical Danger — Nurse acts on wrong data

Scenario B: Smart Bed V2 Confidence-Aware Fusion (SAFE)
Step 1: Patient turns over or visitor sits on bed
Step 2: Pressure matrix & load cells detect movement/weight delta (>30 kg)
Step 3: Fusion Engine triggers Motion / Visitor Gate
Step 4: Output → Flags "Visitor Present / Movement — Vitals Paused"
Result: Clinical Safety — Suppresses corrupt reading explicitly
```

---

## 📍 Slide 7: Retrofit Cot Sensor Placement

* **Diagram Title:** Physical Sensor Integration Architecture
* **Suggested Napkin AI Format:** Annotated Product Callout Diagram

### 📋 Napkin AI Copy-Paste Text:
```text
Smart Bed V2 Physical Sensor Integration Zones

1. Headboard Mount (0.6 meters height)
   • HLK-LD6002 60 GHz mmWave Radar (facing chest for respiration)
   • MLX90614 Point IR Temperature Sensor (aimed at forehead, ±0.2°C)

2. Under Mattress (Torso area)
   • SM-24 Geophone Seismic Sensor (captures structural BCG heart/breath vibrations)

3. Mattress Surface (Under thin sheet)
   • Velostat 12×12 Pressure Matrix (captures body position centroid & contact micro-vibration)

4. Bed Leg Footpads (All 4 legs)
   • 4× 50 kg Load Cells (measures total weight, occupancy, visitor presence, bed-exit)

5. Overhead Arm (1.2 meters height)
   • MLX90640 Spatial Thermal Array (32×24 pixels for heat distribution & blanket detection)
```

---

## 📍 Slide 8: Sensing Architecture & 3 Independent Pathways (MANDATORY)

* **Diagram Title:** 5 Physical Sensors mapped to 3 Independent Physiological Pathways
* **Suggested Napkin AI Format:** Multi-Layered Branching Pathway Flowchart

### 📋 Napkin AI Copy-Paste Text:
```text
Five Sensors Mapped to Three Independent Physiological Pathways

Pathway 1: Through-Air Physiological Sensing
• Sensor: HLK-LD6002 60 GHz mmWave Radar
• Mechanism: Doppler phase shift detection of sub-millimetre chest wall movement
• Primary Target: Respiratory Rate (RR)

Pathway 2: Through-Structure Physiological Sensing
• Sensor: SM-24 Seismic Geophone
• Mechanism: Mechanical heart recoil vibration transmitted through mattress & frame (BCG)
• Primary Target: Heart Rate (HR) & Respiratory Rate (RR)

Pathway 3: Through-Contact Physiological Sensing
• Sensor: Velostat 12×12 Piezoresistive Pressure Matrix
• Mechanism: Surface contact micro-vibration & pressure centroid mapping
• Primary Target: Body Posture (Supine/Lateral/Seated) & Movement Level

Context & Validation Channels:
• 4× Load Cells → Bed Occupancy, Total Weight, Visitor Delta (>30 kg), Bed-Exit (<3 s)
• Dual Thermal Sensors → Surface Temperature Trend & Blanket Coverage Detection
```

---

## 📍 Slide 9: End-to-End Hardware Architecture (MANDATORY)

* **Diagram Title:** Complete System Hardware Block Architecture
* **Suggested Napkin AI Format:** 4-Tier Horizontal/Vertical Layered Architecture Flowchart

### 📋 Napkin AI Copy-Paste Text:
```text
Smart Bed V2 End-to-End Hardware Architecture

Tier 1: Physical Sensor Layer
• HLK-LD6002 60 GHz Radar (UART Interface)
• SM-24 Geophone (Analog Output)
• Velostat 12×12 Pressure Matrix (144 Analog Points)
• 4× 50 kg Load Cells (Analog Bridge Output)
• MLX90640 Spatial Thermal Camera (I2C Interface)
• MLX90614 Point IR Thermometer (I2C Interface)

Tier 2: Microcontroller & Signal Conditioning Layer
• ESP32 WROOM-32 Main Microcontroller Node
• 3× CD74HC4067 16-Channel Multiplexers (Matrix Scanning)
• 2× ADS1115 16-bit ADCs (Geophone & Matrix Sampling)
• 2× HX711 24-bit ADCs (Load Cell Signal Amplification)
• 2× Logic Level Converters (3.3V to 5V Translation)

Tier 3: Edge Computing & Processing Node
• Raspberry Pi 5 (8 GB LPDDR4X) Primary Edge Server
• Real-time Signal Processing Engine (SciPy / NumPy)
• Rule-based Sensor Fusion Engine
• Local SQLite Database Storage (30 s flush)
• FastAPI REST & WebSockets Server

Tier 4: Power Subsystem
• Main Input: 12V 5A DC Regulated Power Adapter
• 3× LM2596 Buck Converters (5V and 3.3V Regulated Power Rails)

Tier 5: System Output
• Nurse Web Dashboard Interface (Single-Bed View & Ward Priority Queue)
```

---

## 📍 Slide 10: Software Architecture & Data Flow Pipeline (MANDATORY)

* **Diagram Title:** Sequential Data Flow from Raw Sensors to Nurse UI
* **Suggested Napkin AI Format:** Linear Process Flowchart / Sequential Data Pipeline

### 📋 Napkin AI Copy-Paste Text:
```text
Smart Bed V2 Software Architecture & Data Flow Pipeline

Stage 1: Data Ingestion Layer
• ESP32 Wi-Fi MQTT Payloads (10 Hz JSON streams)
• Radar UART Serial Stream (I/Q phase data)
• Thermal I2C Polling (1 Hz sampling)
• Geophone Analog ADC Sampling (100 Hz signal)

Stage 2: Signal Processing Pipeline (NumPy / SciPy)
• Radar: FFT & phase demodulation → Extract Respiratory Rate (0.1–0.5 Hz)
• Geophone: Dual Butterworth bandpass filter → Extract RR (0.1–0.5 Hz) & HR (0.8–2.5 Hz)
• Pressure Matrix: Spatiotemporal centroid computation X̄ = Σ(Xᵢ·Pᵢ)/ΣPᵢ → Posture
• Thermal: Spatial contrast calculation → Blanket Index

Stage 3: Confidence-Aware Fusion Engine
• Applies state machine decision rules (Occupancy → Visitor → Motion → Blanket → Agreement)
• Assigns confidence rating: High Confidence, Low Confidence, or Suppressed

Stage 4: Storage & Data Persistence
• Local SQLite Database with Write-Ahead Logging (30-second batch flush)

Stage 5: API & Web Communications Layer
• FastAPI Backend with WebSockets stream engine & REST endpoints

Stage 6: User Interface Presentation Layer
• Web Nurse Dashboard (Real-time Single-Bed observation UI & Ward Priority Queue)
```

---

## 📍 Slide 11: Confidence-Aware Fusion Decision Tree (MANDATORY)

* **Diagram Title:** Multi-Level Sensor Validity State Machine
* **Suggested Napkin AI Format:** Branching Decision Tree / Flowchart

### 📋 Napkin AI Copy-Paste Text:
```text
Confidence-Aware Sensor Fusion Engine State Machine

Step 1: Occupancy Gate
• Condition: Load cell weight > tare threshold?
  ↳ NO → State: BED UNOCCUPIED (Suppress all physiological outputs)
  ↳ YES → Proceed to Step 2

Step 2: Visitor Interference Gate
• Condition: Weight delta > 30 kg OR second pressure centroid detected?
  ↳ YES → State: VISITOR DETECTED (Flag alert & pause vitals)
  ↳ NO → Proceed to Step 3

Step 3: Patient Motion Gate
• Condition: Pressure matrix temporal change > motion threshold?
  ↳ YES → State: PATIENT MOVING (Pause radar/geophone RR for 30 s)
  ↳ NO → Proceed to Step 4

Step 4: Blanket Coverage Gate
• Condition: Thermal contrast index < 0.3?
  ↳ YES → State: BODY OBSCURED (Suspend temperature reading only)
  ↳ NO → Proceed to Step 5

Step 5: 3-Way Pathway Agreement Gate
• Condition: Radar RR and Geophone RR agree within ±2 bpm?
  ↳ YES → State: HIGH CONFIDENCE (Publish validated vitals to dashboard)
  ↳ NO → State: LOW CONFIDENCE (Publish vitals with explicit warning flag)
```

---

## 📍 Slide 12: Ward Simulation & Explainable AI (XAI) Pipeline

* **Diagram Title:** Phase 1 Physical Data to Phase 2 Ward Prioritisation
* **Suggested Napkin AI Format:** 2-Phase Machine Learning Pipeline Flowchart

### 📋 Napkin AI Copy-Paste Text:
```text
Phase 1 Hardware Data to Phase 2 Explainable AI Ward Simulation

Phase 1: Physical Hardware Data Collection
• 10 Volunteer Testing Sessions on Physical Bed Prototype
• Labelled Scenario Dataset Generated:
  - quiet_rest (stable vitals)
  - elevated_rr (breathing >20% above baseline)
  - sustained_pressure (pressure area loaded >2 hours)
  - bed_exit_attempt (weight drop at bed edge)
  - visitor_present (secondary weight added)

Phase 2: Synthetic Ward Simulation & Machine Learning
• Ward Snapshot Synthesizer: Combines single-bed recordings into 4-to-8 bed virtual wards
• XGBoost / Random Forest Classifier: Trained on feature vectors to rank patient priority
  - Output Classes: Low Priority | Medium Priority | High Priority | Immediate Attention

Phase 3: SHAP Explainability Layer (XAI)
• Calculates Shapley values per feature for every patient
• Generates Natural Language Explanation for Nurse Dashboard:
  Example: "Bed 3 HIGH PRIORITY: Elevated RR (+35%, High Conf) [+0.42] + Sacral Pressure (>2.2h) [+0.31]"
```

---

## 📍 Slide 13: Nurse Dashboard Layout & User Interface

* **Diagram Title:** Dashboard Interface Components & Alert Layout
* **Suggested Napkin AI Format:** UI Layout Grid / Dashboard Wireframe Mockup

### 📋 Napkin AI Copy-Paste Text:
```text
Nurse Dashboard User Interface Layout

Section 1: Header Bar
• Hospital Ward Identifier | Total Occupied Beds | System Status: Active | Real-Time Clock

Section 2: Single-Bed Detailed Observation View (Bed 3)
• Bed Status Card: Occupied (Green Indicator)
• Patient Posture Card: Supine (Live 12×12 Heatmap Display)
• Vital Signs Display: Respiratory Rate 16 bpm [HIGH CONFIDENCE 🟢]
• Temperature Trend: Surface Temp +0.4°C over 60 min
• Movement Bar: Low Activity Level
• Active Alert Banner: "Patient stationary 3.1 hours — Check sacral pressure risk"

Section 3: Ward-Level Multi-Bed Priority Queue (Phase 2 View)
• Priority Rank 1: Bed 3 (HIGH) — Elevated RR + Sustained Sacral Pressure [SHAP Explained]
• Priority Rank 2: Bed 7 (MEDIUM) — Patient Restless / Movement Active
• Priority Rank 3: Bed 1 (LOW) — Stable Vitals, High Sensor Agreement
```

---

## 📍 Slide 14: Prototype Budget & Research Novelty Map

* **Diagram Title:** Budget Expenditure Distribution & Research Gap Matrix
* **Suggested Napkin AI Format:** Donut Chart Summary + 2x2 Research Gap Matrix

### 📋 Napkin AI Copy-Paste Text:
```text
Part A: Smart Bed V2 Verified Budget Distribution (Total ₹64,280)

1. Section A — Core Hardware: ₹40,465 (63.0%)
   • Raspberry Pi 5 8GB (₹20,000), 60GHz Radar, Geophone SM-24, Velostat Grid, Load Cells, MLX90640, MLX90614, ESP32, ADCs, Muxes, Power Rails
2. Section B — Prototype Fabrication: ₹10,160 (15.8%)
   • Hospital Cot Frame, Foam Mattress, MS Radar Mount, Overhead Camera Arm, Load Cell Footpads, Enclosures, Cabling
3. Section D — Validation: ₹5,750 (9.0%)
   • Reference Stopwatch, Volunteer Honoraria (10 sessions), Ethics Printing, Backup Drive + Fallback Instruments (V2/V3/V4)
4. Contingency Buffer (~8%): ₹4,555 (7.1%)
   • Component failure allowance, price variation, shipping buffer
5. Section C — Data & Experimentation: ₹3,350 (5.2%)
   • Calibration Weights Set (5 kg), EVA Foam Backing, Thermal Reference Target, Reference Thermometer, Desk Fan, Forms & Hygiene

Uncommitted Surplus: ₹35,720 retained for Phase 2 clinical-site testing (Funding Limit: ₹1,00,000)

Part B: The Academic Research Gap We Fill
• Gap 1: Multi-Pathway Sensing — 3 independent physical HR/RR pathways in 1 bed
• Gap 2: Explicit Validity Gating — Detects & reports when readings are invalid
• Gap 3: Affordable Bed Retrofit — <USD 775 cost on existing hospital cots
• Gap 4: Explainable Ward AI — SHAP interpretable priority queue from single-bed data
```

---

## 📍 Slide 15: Closing Vision Summary

* **Diagram Title:** Final Vision Pillars & Contact Summary
* **Suggested Napkin AI Format:** 3-Pillar Summary Card / Minimal Closing Visual

### 📋 Napkin AI Copy-Paste Text:
```text
Smart Bed V2 Project Vision Summary

Three Core Pillars:
1. Affordable — ₹64,280 total prototype cost retrofitting existing hospital cots
2. Unobtrusive — Zero patient body contact, wires, or workflow friction
3. Confidence-Aware — Intelligent multi-sensor fusion preventing silent false alerts

Academic Deliverables:
• Fully validated physical prototype
• Labelled volunteer session dataset
• SHAP-explainable multi-patient simulation model
• Research paper submission

Team & Repository:
• Project: AI-Powered Multimodal Contactless Patient Monitoring System
• Institution: Department of Biomedical Engineering / Computer Science, Coimbatore, Tamil Nadu
• Code Repository: github.com/Stark6612/SmartBed
```

---

*Diagrams Guide for Napkin AI — Aligned with Slidewise Content.md & Slide Structure.md | August 2026*
