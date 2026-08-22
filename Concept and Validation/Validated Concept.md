# Validated Concept — AI-Powered Multimodal Contactless Patient Monitoring System
## Project System Specification & Architecture Document

**Project Title:** AI-Powered Multimodal Contactless Patient Monitoring and Clinical Decision Support System Using the Hospital Bed as an Unobtrusive Sensing Platform  
**Target Deployment Context:** Resource-constrained hospital wards, government hospitals, and general wards in India  
**Platform Concept:** Retrofit existing single-person hospital beds with an integrated five-sensor array  
**Budget Ceiling:** ₹1,00,000 | **Verified Prototype Cost:** ₹64,280 (Option B)  
**Location:** Coimbatore, Tamil Nadu, India | **Date:** August 2026  

---

## 1. Executive Summary & Vision

The core mission of this project is to transform conventional, non-smart hospital beds into intelligent sensing platforms without requiring expensive commercial smart beds (which cost ₹10–50 lakh). By retrofitting standard bed frames with a low-cost array of five non-obtrusive sensor modalities and an edge computing node, the system continuously observes patient status without attaching wires or patches directly to the patient's skin.

### Key Innovations

1. **Three Independent HR/RR Pathways:** Combines mmWave radar (through-air), geophone (through-structure BCG), and pressure matrix micro-vibrations to cross-validate physiological signals.
2. **Confidence-Aware Sensor Fusion:** Explicitly detects and flags real-world interference (patient movement, visitors sitting on the bed, blanket coverage) that causes single-sensor systems to fail silently.
3. **Two-Phase Research Architecture:**
   - **Phase 1 (Hardware Prototype):** Single-bed physical prototype collecting validated patient data.
   - **Phase 2 (Software Ward Simulation & XAI):** Replays scenario recordings to simulate multi-patient ward dynamics, training a Machine Learning classifier paired with SHAP (SHapley Additive exPlanations) to provide explainable patient prioritisation.

---

## 2. Core Capabilities & Scope

### In-Scope Deliverables (Phase 1 Prototype)

| Capability | Sensing Modality | Technical Mechanism |
|---|---|---|
| **Bed Occupancy Detection** | Load Cells + Pressure Matrix | Binary state derived from total weight delta and spatial pressure centroid |
| **Visitor / Second Occupant Detection** | Load Cells + Pressure Matrix | Weight delta (>30 kg) + secondary pressure centroid detection |
| **Bed-Exit Alert** | Load Cells | Immediate weight drop to near-zero tare baseline (<3 s latency) |
| **Body Position Classification** | Pressure Matrix | 4-class centroid mapping: Supine, Left Lateral, Right Lateral, Seated |
| **Body Movement Level** | Pressure Matrix + Load Cells | Temporal variance in pressure grid intensity and total load jitter |
| **Respiratory Rate (RR)** | mmWave Radar + Geophone | FFT phase extraction (radar) & bandpass filtering (geophone); validated against manual count |
| **Exploratory Heart Rate (HR)** | Geophone + mmWave Radar | Structural BCG vibration peak extraction (geophone) cross-checked with radar micro-motion |
| **Surface Temperature Trend** | Point IR + Thermal Array | High-accuracy forehead/chest reading (MLX90614, ±0.2°C) + spatial thermal mapping (MLX90640) |
| **Measurement Confidence Gate** | Multi-Sensor Fusion Engine | Deterministic state machine assigning per-reading validity confidence (High / Low / Suppressed) |

### Explicitly Out-Of-Scope for Phase 1

- **No Clinical Diagnosis Claims:** System provides observational alerts, not medical diagnoses.
- **No Direct Contactless BP or SpO₂ Claims:** Pulse oximeter (V4) is used strictly as a reference validation tool for volunteer sessions.
- **No Real-Time Ward Deployment:** Phase 1 is restricted to controlled laboratory and volunteer trial validation.

---

## 3. Hardware Architecture & Sensor Placement

```
                        ┌──────────────────────────────────────────┐
                        │      OVERHEAD ARM (Height: 1.2 m)        │
                        │  • MLX90640 Spatial Thermal Array (I2C)  │
                        └────────────────────┬─────────────────────┘
                                             │
 ┌───────────────────────────────────┐       │       ┌───────────────────────────────────┐
 │   HEADBOARD MOUNT (Height: 0.6 m) │       │       │       MATTRESS & BED FRAME        │
 │ • HLK-LD6002 60GHz Radar (UART)   │       │       │ • Velostat Pressure Matrix (Top)  │
 │ • MLX90614 Point Temp Sensor (I2C)│       │       │ • SM-24 Geophone (Under Mattress) │
 └─────────────────┬─────────────────┘       │       └─────────────────┬─────────────────┘
                   │                         │                         │
                   └─────────────────────────┼─────────────────────────┘
                                             ▼
                             ┌──────────────────────────────┐
                             │  ELECTRONICS ENCLOSURE BOX   │
                             │  • ESP32 MCU (ADC/Mux Scan)  │
                             │  • HX711, ADS1115, Buck Conv │
                             └───────────────┬──────────────┘
                                             │ MQTT / Serial
                                             ▼
                             ┌──────────────────────────────┐
                             │  RASPBERRY PI 5 (8 GB) NODE  │
                             │  • Signal Processing (SciPy) │
                             │  • Fusion State Machine      │
                             │  • FastAPI / SQLite Backend  │
                             └──────────────────────────────┘
                                             ▲
                                             │ Load Cell Signals
                             ┌───────────────┴──────────────┐
                             │ BED LEG FOOTPADS (4 Corner)  │
                             │ • 4× 50 kg Half-Bridge Cells │
                             └──────────────────────────────┘
```

### Sensor Placement & Specification Matrix

| Sensor | Model / Specification | Physical Placement | Interface | Purpose |
|---|---|---|---|---|
| **mmWave Radar** | HLK-LD6002 (60 GHz FMCW, vital sign radar) | Headboard mounted at 0.6 m height, directed at patient thorax (0.5–0.9 m distance) | UART (to Pi serial) | Non-contact chest wall displacement for Respiratory Rate (RR) |
| **Geophone** | SM-24 (Low-frequency seismic velocity sensor, ~28 Hz) | Placed under mattress, directly on bed frame beneath upper torso | Analog ADC (ADS1115 / Pi) | Structural Ballistocardiography (BCG): detects mechanical heart recoil & breathing micro-vibration |
| **Pressure Matrix** | 4× Velostat piezoresistive sheets (12×12 conductive tape grid, ~60×60 cm) | Placed directly on top of mattress under thin bed sheet (covering torso & hips) | Multiplexed Analog (CD74HC4067 → ADS1115 → ESP32) | Spatial pressure distribution, body centroid, position classification, movement tracking |
| **Load Cells** | 4× 50 kg half-bridge aluminium load cells | Sandwiched in custom aluminium footpads under all 4 bed legs | 2× HX711 24-bit ADCs → ESP32 | Total weight measurement, bed occupancy, visitor detection (weight delta), bed-exit detection |
| **Spatial Thermal** | MLX90640 IR Array (32×24 pixels, 55° FOV) | Overhead adjustable arm at 1.2 m height facing down on bed surface | I2C (to Raspberry Pi) | Spatial thermal footprint, body outline verification, blanket coverage detection |
| **Point Temperature** | Melexis MLX90614ESF-BCC (90° FOV, ±0.2°C accuracy) | Headboard mounted, aimed at patient forehead/chest region | I2C (to Raspberry Pi) | High-accuracy clinical-grade skin surface temperature reading |

---

## 4. Software Architecture & Signal Pipelines

### Multi-Node System Software Stack

```
 ┌─────────────────────────────────────────────────────────────────────────────┐
 │                         ESP32 SENSING NODE (C++)                            │
 │  • HX711 Load Cell Driver  • CD74HC4067 Multiplexer Sequencer (12×12 Grid) │
 │  • ADS1115 ADC Reader     • Wi-Fi MQTT Publisher (JSON Payloads @ 10 Hz)   │
 └──────────────────────────────────────┬──────────────────────────────────────┘
                                        │ Wi-Fi / MQTT
                                        ▼
 ┌─────────────────────────────────────────────────────────────────────────────┐
 │                      RASPBERRY PI 5 EDGE & AI NODE                          │
 │                                                                             │
 │  ┌───────────────────────────────────────────────────────────────────────┐  │
 │  │ Data Ingestion: Mosquitto MQTT Broker + Direct UART (Radar) + I2C     │  │
 │  └───────────────────────────────────┬───────────────────────────────────┘  │
 │                                      ▼                                      │
 │  ┌───────────────────────────────────────────────────────────────────────┐  │
 │  │ Signal Processing Pipeline (NumPy / SciPy)                            │  │
 │  │ • Radar FFT & Phase Demodulation (0.1–0.5 Hz Breathing Bandpass)       │  │
 │  │ • Geophone BCG Bandpass (0.8–2.5 Hz Cardiac, 0.1–0.5 Hz Respiratory)   │  │
 │  │ • Pressure Grid Centroid & Spatiotemporal Gradient Computation        │  │
 │  └───────────────────────────────────┬───────────────────────────────────┘  │
 │                                      ▼                                      │
 │  ┌───────────────────────────────────────────────────────────────────────┐  │
 │  │ Confidence-Aware Fusion Engine (State Machine Rule Logic)              │  │
 │  │ • Motion Gate  • Visitor Detector  • Blanket Detector  • 3-Way Check   │  │
 │  └───────────────────────────────────┬───────────────────────────────────┘  │
 │                                      ▼                                      │
 │  ┌───────────────────────────────────────────────────────────────────────┐  │
 │  │ Storage & API Layer: SQLite Database + FastAPI REST & WebSockets     │  │
 │  └───────────────────────────────────┬───────────────────────────────────┘  │
 └──────────────────────────────────────┼──────────────────────────────────────┘
                                        │ WebSockets / HTTP
                                        ▼
 ┌─────────────────────────────────────────────────────────────────────────────┐
 │                      NURSE DASHBOARD & WEB UI (HTML/JS)                     │
 │  • Real-Time Single-Bed View (Live Vitals, Pressure Heatmap, Confidence)    │
 │  • Phase 2 Simulated Ward View (Multi-Patient Priority List + SHAP XAI)     │
 └─────────────────────────────────────────────────────────────────────────────┘
```

### Signal Processing Pipelines

1. **Radar Respiratory Processing:**
   - Raw I/Q data → Phase unwrapping → Bandpass Butterworth filter ($0.1\text{ Hz} - 0.5\text{ Hz}$) → Peak detection / FFT spectrum peak → Respiratory Rate estimate (bpm).
2. **Geophone Structural BCG Processing:**
   - Raw voltage time-series ($100\text{ Hz}$ sampling) → Remove baseline offset → Dual Butterworth filters:
     - Breathing band ($0.1 - 0.5\text{ Hz}$) → Secondary RR estimate.
     - Cardiac band ($0.8 - 2.5\text{ Hz}$) → J-peak interval detection → Exploratory HR estimate.
3. **Pressure Grid Processing:**
   - 144 cell matrix scan ($10\text{ Hz}$) → Crosstalk suppression mask → Calculate Centroid $(\bar{X}, \bar{Y})$:
     $$\bar{X} = \frac{\sum (X_i \cdot P_i)}{\sum P_i}, \quad \bar{Y} = \frac{\sum (Y_i \cdot P_i)}{\sum P_i}$$
   - Classify position via SVM / Random Forest: Supine, Left Lateral, Right Lateral, Seated.

---

## 5. Confidence-Aware Fusion Engine Design

The fusion engine evaluates inputs from all five sensors to determine measurement validity before publishing to the dashboard.

```
                            ┌─────────────────────────┐
                            │   RAW SENSOR INPUTS     │
                            └────────────┬────────────┘
                                         │
                                         ▼
                            ┌─────────────────────────┐
                            │ LOAD CELL OCCUPANCY?    ├───── NO ──────► [BED UNOCCUPIED]
                            └────────────┬────────────┘                 Suppress Vitals
                                         │ YES
                                         ▼
                            ┌─────────────────────────┐
                            │ LOAD CELL WEIGHT DELTA  ├───── >30 kg ──► [VISITOR DETECTED]
                            │   OR SECOND CENTROID?   │                 Flag & Pause Vitals
                            └────────────┬────────────┘
                                         │ NO (Single Patient)
                                         ▼
                            ┌─────────────────────────┐
                            │ PRESSURE GRID MOVEMENT  ├───── >Threshold► [PATIENT MOVING]
                            │   OR GEOPHONE JITTER?   │                 Pause Radar/Geophone
                            └────────────┬────────────┘
                                         │ LOW (Patient Still)
                                         ▼
                            ┌─────────────────────────┐
                            │ THERMAL CONTRAST LOW?   ├───── YES ─────► [BODY OBSCURED]
                            └────────────┬────────────┘                 Flag Temp Only
                                         │ NO (Skin Visible)
                                         ▼
                            ┌─────────────────────────┐
                            │ RADAR vs GEOPHONE RR    ├───── Disagree ─► [LOW CONFIDENCE]
                            │   AGREE WITHIN 2 BPM?   │                 Flag Disagreement
                            └────────────┬────────────┘
                                         │ YES (Agreement)
                                         ▼
                            ┌─────────────────────────┐
                            │   HIGH CONFIDENCE RR    │
                            │   Publish Vitals + Flag │
                            └─────────────────────────┘
```

---

## 6. Phase 2: Simulated Multi-Patient Ward & Explainable AI (XAI)

### Overview

While Phase 1 proves hardware capability on a single bed, Phase 2 builds a software ward simulation using scenario recordings collected during Phase 1 volunteer trials.

### Pipeline

1. **Scenario Dataset (Phase 1 Output):** Labelled 10-minute sensor sessions (`quiet_rest`, `restless`, `elevated_rr`, `temperature_rising`, `sustained_pressure`, `bed_exit_attempt`, `visitor_present`).
2. **Synthetic Ward Composition:** Composes 4 to 8 virtual bed states into a synthetic ward snapshot.
3. **Priority Model Training:** Trains an XGBoost / Random Forest classifier on per-patient feature vectors to predict priority rank (Low, Medium, High, Immediate).
4. **SHAP Explainability Engine:** Calculates Shapley values for every feature per prediction to output natural-language explanations:
   > *"Patient Bed 3 ranked HIGH PRIORITY because: Elevated Respiratory Rate (+35% vs baseline, High Confidence) contributed +0.42; Sustained Sacral Pressure (>2.2 hours) contributed +0.31; Surface Temperature Trend (+0.7°C) contributed +0.18."*

---

## 7. System Budget & Procurement Summary

| Category | Major Items included | Verified Cost (₹) |
|---|---|---:|
| **Core Hardware (Section A)** | HLK-LD6002 radar (₹2,200), SM-24 geophone (₹500), Velostat ×4 (₹1,900), MLX90640 (₹5,000), MLX90614 (₹700), load cells ×4 (₹400), Raspberry Pi 5 8 GB (₹20,000), microSD 64GB A2 (₹2,800), RPi PSU & case (₹2,200), ESP32, ADCs, muxes, converters | 40,465 |
| **Prototype Fabrication (Section B)** | Cot frame & foam mattress (₹7,000 fallback), headboard bracket, camera arm, load cell footpads, cable conduits, project enclosures | 10,160 |
| **Data & Experimentation (Section C)** | Calibration weights, EVA foam backing, thermal reference target, desk fan, consumables | 3,350 |
| **Validation & Reference (Section D)** | Digital stopwatch, volunteer honoraria (10 sessions), ethics docs, USB drive + conditional V2/V3/V4 reference scale/spirometer/oximeter fallback (₹2,800) | 5,750 |
| **Procurement Subtotal** | | **59,725** |
| **Contingency (~8%)** | Shipping, price variations, component buffers | 4,555 |
| **TOTAL (Worst Case — All Items Purchased)** | | **₹64,280** |
| **TOTAL (Best Case — Institutional Access for Bed & Validation Tools)** | | **₹61,480** |
| **Uncommitted Surplus (Available for Phase 2)** | Retained in institutional grant account | **₹35,720–₹38,520** |

---

## 8. Experimental & Validation Roadmap

```
  WEEKS 1–4              WEEKS 5–8             WEEKS 9–14            WEEKS 15–18
┌───────────────┐      ┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│  PHASE 1:     │─────►│  PHASE 2:     │────►│  PHASE 3:     │────►│  PHASE 4:     │
│  Sensor       │      │  Multimodal   │     │  Volunteer    │     │  Clinical Ref │
│  Calibration  │      │  Fusion Test  │     │  Trials (IRB) │     │  Comparison   │
└───────────────┘      └───────────────┘     └───────────────┘     └───────────────┘
  • Load Cell Tare       • Motion Gate         • 10 Healthy          • Manual Breath
  • Pressure Grid Scan     Test (>90%)           Volunteers            Count (RMSE <3)
  • Radar RR Peak        • Visitor Flag        • 30–60 min           • Pulse Oximeter
  • Geophone Filter        Test (>95%)           Sessions              Ref HR
  • Thermal Calibration  • Blanket Detect      • Record Scenarios    • Scale Weight Ref
```

### Key Performance Targets

- **Respiratory Rate Accuracy:** RMSE < 3 bpm vs. manual observer count over 60-second windows.
- **Interference Detection Sensitivity:** > 90% detection rate for visitor presence, patient movement, and blanket coverage.
- **Occupancy & Bed-Exit Sensitivity:** > 99% accuracy for bed occupancy; bed-exit alert latency < 3 seconds.

---

*Validated Concept Document — Smart Bed V2 System Specification*  
*Aligned with Analysis and Validation.md, ItemizedBudget.md, and Budget_Slide_Content.md*  
*August 2026 | Coimbatore, Tamil Nadu, India*
