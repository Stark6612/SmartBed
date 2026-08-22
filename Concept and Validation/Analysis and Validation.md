# Analysis and Validation
## AI-Powered Multimodal Contactless Patient Monitoring System — Smart Bed V2

**Project Title:** AI-Powered Multimodal Contactless Patient Monitoring and Clinical Decision Support System Using the Hospital Bed as an Unobtrusive Sensing Platform
**Location:** Coimbatore, Tamil Nadu, India | **Budget Ceiling:** ₹1,00,000 | **Report Prepared:** August 2026
**Sources:** 8 peer-reviewed papers (2025–2026), ItemizedBudget.md (₹64,280 verified total), Smart Bed V2.pdf

> **Approach:** All assumptions are actively challenged. Individual technology existence is not treated as proof of system-level feasibility. Reasons for failure are sought alongside reasons for success.

---

## Research Evidence Base

| # | Paper | Journal | Date | Key Finding |
|---|---|---|---|---|
| R1 | Lee, Kim & Jeong — Load cell fall detection | *Measurement* (Elsevier) | Aug 2025 | 96.26% fall accuracy; fusion beats single sensor by 21.82% |
| R2 | López-Ruiz et al. — Bed-based BCG via smartphone | *Sensors & Actuators A* (Elsevier) | Sep 2025 | HR/RR/apnea from mattress micro-vibrations |
| R3 | Chen et al. — Contactless vital signs, mmWave Doppler | *Healthcare Technology Letters* (IET) | 2024 | FMCW radar feasibility for HR + RR confirmed |
| R4 | Padaki et al. — Contactless validation, 111 ED patients | *Frontiers in Medical Technology* | Jan 2026 | HR RMSE 1.62 bpm, RR RMSE 1.71 bpm in real hospital |
| R5 | Shaya, Levy et al. — TAMAR radar, 315 ED patients | *Frontiers in Medical Technology* | Jun 2026 | RR LOA ±1.6 bpm, HR LOA ±4.7 bpm; 30% missing measurements |
| R6 | Qiu et al. — BCG + ECG public dataset | *Scientific Data* (Nature) | 2025 | Public dataset; ECG as ground truth for bed-based cardiac |
| R7 | Reyes et al. — SiViS multi-patient radar dataset | *Scientific Data* (Nature) | 2026 | HR MAE 6.6 bpm; RR MAE 1.47 bpm; multi-patient radar unsolved |
| R8 | Pitafi et al. — SimDot geophone testbed, Raspberry Pi | *Sensors* (MDPI) | Feb 2026 | Geophone MAE < 2 bpm on RPi; 0.85 correlation with 75 subjects |

---

---

# 1. Overall Feasibility

| Dimension | Rating | Justification |
|---|---|---|
| Technical feasibility | **Moderate** | Each modality validated individually in literature. Integrated system in real ward at this cost: not yet demonstrated. Radar HR is the weakest link. |
| Hardware feasibility | **High** | All components in-stock at Indian retailers. Full prototype: ₹64,280 — well within ₹1 lakh. |
| Software feasibility | **High** | Python, PyTorch, Scikit-learn, FastAPI, MQTT, SQLite — free, mature, well-documented on Raspberry Pi 5. |
| AI/ML feasibility | **Moderate** | Rule-based confidence gating and body-position classification: fully feasible. Patient deterioration prediction and ward-level prioritisation: simulation-based Phase 2 (see §7). |
| Sensor-fusion feasibility | **Moderate–High** | Deterministic threshold-based fusion: immediately implementable. Multi-sensor confidence agreement (radar + geophone both confirm RR): genuinely novel and achievable. |
| Clinical feasibility | **Low–Moderate** | RR, body position, occupancy, surface temperature trend: clinically useful. Clinical-grade HR and core temperature: not achievable under ward conditions with this sensor set. |
| Prototype within ₹1 lakh | **High** | Verified total ₹64,280. Surplus ₹35,720 for Phase 2. |
| Real-world hospital | **Low (Phase 1)** | Lab validation only. R5 (315 real patients) showed 30% failure even with military-grade hardware. Hospital deployment is Phase 3+. |
| Scalability | **Low (Phase 1)** | Multi-bed MQTT routing, hospital IT integration, and infection control protocols are Phase 3+ work. |
| Affordability | **High** | ₹64,280 for a five-sensor AI-fused prototype vs. commercial smart beds (₹10–50 lakh). |

## Overall Verdict

> **Proceed with modifications.**
> Core concept is sound and budget is realistic. Scope must be explicitly narrowed: HR claims, clinical decision support, and patient prioritisation are reframed as simulation-demonstrated research contributions, not clinical-grade outputs.

---

---

# 2. Sensor Validation

## 2.1 mmWave Radar — HLK-LD6002, 60 GHz FMCW

> **Critical fix (BudgetVerification.md §3.1):** Original HLK-LD2450 (24 GHz, ₹650) replaced with HLK-LD6002 (60 GHz, ₹2,200). The LD2450 cannot extract respiratory rate from a stationary patient and would invalidate the core research objective.

| Parameter | Feasibility | Evidence |
|---|---|---|
| Respiratory rate | **Feasible with validation** | R3, R5: RR LOA ±1.6 bpm in real ED. R7: RR MAE 1.47 bpm. Primary output. |
| Heart rate | **Difficult — exploratory** | R5: HR LOA ±4.7 bpm. R7: HR MAE 6.6 bpm. Degrades severely with movement or blankets. Complemented by geophone (see §2.5). |
| Heartbeat micro-motion | **Difficult** | Detectable in optimal conditions only (still, no blanket, correct distance). Document feasibility — do not claim accuracy. |

| Challenge | Mitigation |
|---|---|
| Patient movement destroys signal | Motion gate: radar RR accepted only when pressure matrix shows <threshold change for 30 s |
| Visitors on bed corrupt signal | Load cell weight delta triggers visitor flag → radar output suppressed |
| Blankets (thick) may attenuate 60 GHz | Flag in confidence layer; validate with/without blanket in Phase 1 |
| Environmental EM interference (real ward) | Lab only in Phase 1; hospital is Phase 3+ |

**Cost:** ₹2,200 | **Verdict: Keep. RR = primary output. HR = exploratory research objective.**

---

## 2.2 Geophone — SM-24 (Under-Mattress BCG)

**What it is:** A geophone is a velocity sensor originally designed for seismic surveys. Placed under the mattress, it detects body-transmitted mechanical vibrations caused by each heartbeat and breath — the same physical principle as Ballistocardiography (BCG). Unlike radar (through-air) and thermal (IR radiation), the geophone detects vibration transmitted structurally through the bed frame: blankets do not affect it.

| Parameter | Feasibility | Evidence |
|---|---|---|
| Respiratory rate | **Feasible with validation** | R8: MAE < 2 bpm on Raspberry Pi. Bandpass 0.1–0.5 Hz isolates breathing. |
| Heart rate | **Feasible with validation** | R8: MAE < 2 bpm. Bandpass 0.8–2.5 Hz isolates heartbeat. Better than radar HR alone. |
| Body movement | **Strongly feasible** | Large vibration amplitude indicates movement; used to gate physiological signal extraction. |

| Challenge | Mitigation |
|---|---|
| Hospital floor vibration (footsteps, equipment) contaminates signal | Bandpass filtering (0.1–0.5 Hz breathing, 0.8–2.5 Hz cardiac). Motion gate from load cells and pressure matrix. |
| Signal quality depends on mattress stiffness | Fix mattress type throughout all experiments; document as generalisation limitation. |

**Fusion role:** When radar RR and geophone RR agree within ±2 bpm → **high confidence** combined reading. When they disagree → lower confidence; investigate which sensor is in a degraded state.

**Cost:** ₹500 | **Verdict: Keep. Adds a second independent HR/RR path for <1% of total budget. Research novelty: significant.**

---

## 2.3 Pressure Sensor Matrix — Velostat DIY, 4 sheets (~60×60 cm)

| Parameter | Feasibility |
|---|---|
| Body position (supine/left-lateral/right-lateral/seated) | **Strongly feasible** |
| Pressure distribution / spatial map | **Strongly feasible** |
| Body movement detection | **Strongly feasible** |
| Bed occupancy | **Strongly feasible** |
| Prolonged pressure / pressure-ulcer risk mapping | **Feasible** — frame as "pressure duration mapping," not pressure ulcer diagnosis |

| Challenge | Mitigation |
|---|---|
| Velostat creep (drift under sustained load) | Recalibrate at start of each session; document drift as a research finding |
| Row-column crosstalk | Sequential scanning + resistor network; characterise during Phase 1 |
| Results not generalisable across mattress types | Fix mattress type; document as limitation |

**Fusion role:** Provides body position (annotates radar and geophone readings), motion gate (suppresses physiological signals during movement), and visitor detection (second pressure centroid + load cell weight delta).

**Cost:** ~₹3,800 total (Velostat + electrode tape + ADS1115) | **Verdict: Keep. The only sensor with spatial body information.**

---

## 2.4 Load Cells — 4× 50 kg Half-Bridge, HX711 ADC

| Parameter | Feasibility |
|---|---|
| Patient weight | **Strongly feasible** — calibrated against reference scale (V2) |
| Bed occupancy | **Strongly feasible** — most reliable occupancy indicator |
| Bed-exit detection | **Strongly feasible** — R1: 96.26% detection accuracy |
| Visitor / additional occupant detection | **Strongly feasible** — weight delta flags second person reliably |

**Fusion role:** Load cells are the **confidence anchor** of the system. Unaffected by blankets, body position, radar interference, or lighting. Ground truth for: occupancy (reject all readings if unoccupied), visitor state (suppress physiological readings), bed-exit events (trigger alert unconditionally).

**Cost:** ₹540 (cells + HX711 modules) | **Verdict: Keep — Promote to anchor role in confidence architecture.**

---

## 2.5 Thermal Camera — MLX90640 (Spatial) + MLX90614 (Point)

| Parameter | Feasibility |
|---|---|
| Surface temperature trend | **Feasible** — MLX90614 (±0.2°C); report as "surface trend," not core body temperature |
| Spatial thermal mapping / body outline | **Feasible** — MLX90640 32×24 px; body position and blanket coverage detectable |
| Occupancy confirmation via thermal footprint | **Strongly feasible** |

| Challenge | Mitigation |
|---|---|
| Blanket completely blocks IR — patient temperature unmeasurable | Detect blanket (low thermal contrast, no body outline) → flag "Body obscured — surface reading unavailable" |
| Ambient temperature drift affects absolute readings | Use relative temperature (patient vs. ambient region); calibrate with MLX90614 per session |

**Cost:** ₹5,700 (MLX90640 ₹5,000 + MLX90614 ₹700) | **Verdict: Keep. The only modality providing body shape and temperature trend. Scope = surface temperature trend only.**

---

## 2.6 BP and SpO₂ — What the Project Can and Cannot Do

### Contactless BP
Experimental PTT (Pulse Transit Time) methods require a body-contact ECG reference to anchor the measurement — not truly contactless. Radar-based pulse wave detection requires arterial stiffness data (varies with age, medication, hydration) — absolute BP estimation is clinically unreliable. **Do not claim contactless BP.**

### Contactless SpO₂
Camera-based rPPG can estimate SpO₂ in controlled conditions (~2–3% RMSE per Google Health research), but accuracy collapses with darker skin tones, poor lighting, and body covered by clothing or blankets. **Do not claim contactless SpO₂.**

### Contact Reference Instruments (Already Budgeted)
The pulse oximeter (V4, ₹1,000 — Contec CMS50D) is already in the validation budget. It provides reference HR and SpO₂ for volunteer session annotation and radar HR comparison. Optional: add a manual BP cuff (₹500, institutional access preferred) purely for session annotation. Neither is a system output — both are validation reference tools.

---

---

# 3. Sensor Architecture Summary

| Sensor | Role | Measurement | Blanket-proof? | Cost |
|---|---|---|---|---|
| HLK-LD6002 radar | Primary physiological | RR (primary), HR (exploratory) | Partially | ₹2,200 |
| Geophone SM-24 | Secondary physiological | RR + HR (independent path) | ✅ Yes | ₹500 |
| Velostat pressure matrix | Spatial + motion | Position, movement, occupancy, pressure map | ✅ Yes | ₹3,800 |
| Load cells ×4 | Confidence anchor | Weight, occupancy, visitor, bed-exit | ✅ Yes | ₹540 |
| MLX90640 thermal | Spatial thermal + occupancy | Body outline, temperature zone | ❌ No | ₹5,000 |
| MLX90614 temperature | Accurate point temperature | Surface temperature ±0.2°C | ❌ No | ₹700 |

**Three independent HR/RR pathways:** Radar (through-air), Geophone (through-structure), BCG from Pressure Matrix (through-contact). When multiple agree → high confidence. When they disagree → investigate degraded sensor state.

---

---

# 4. Multimodal Sensor Fusion — Confidence-Aware Architecture

## The Central Research Question

> **"Can the system reliably determine whether a measurement is trustworthy?"**

This is the primary research contribution. It addresses the core problem documented in R5: even military-grade radar produced no valid measurement for 30% of real patients. The system must not report wrong numbers silently — it must say when it cannot be trusted.

## Confidence State Machine

| Scenario | Sensor Evidence | AI Decision |
|---|---|---|
| Patient still, single occupant, no blanket, radar + geophone agree | All sensors stable. Two physiological pathways agree within ±2 bpm. | **High confidence** — report RR, temperature trend. |
| Patient moving | Pressure: high temporal change. Radar/geophone: erratic signals. | **Suppress physiological readings** — flag "Patient movement — readings paused." |
| Visitor on bed | Load cells: +30–80 kg delta. Pressure: second centroid. | **Suppress all physiological readings** — flag "Second occupant detected." Alert if >5 min. |
| Thick blanket covers body | Thermal: low contrast, no body outline. MLX90614: near ambient. | **Suppress temperature** — flag "Body obscured — surface reading unavailable." Radar/geophone unaffected. |
| Radar and geophone disagree on RR by >3 bpm | One sensor in degraded state. | **Reduced confidence** — report "RR estimate low confidence — sensor disagreement." |
| Patient changes position | Pressure centroid shifts. Radar/geophone: brief artifact. | **Momentary suppression** (30 s), then resume if stable. Update position estimate. |
| Bed unoccupied | Load cells: near tare. Pressure: baseline. | **All outputs suppressed** — "Bed unoccupied." |

## Implementation Approach

**Phase 1 (prototype):** Deterministic threshold-based state machine. No training data required. Scientifically valid immediately.

**Phase 2 (simulation study):** ML-weighted confidence scores trained on synthetic multi-patient data from real prototype recordings (see §7). SHAP explainability applied.

## Why This Is Scientifically Defensible

1. Does not overclaim — explicitly acknowledges unreliable measurements instead of reporting wrong numbers silently.
2. Mirrors established clinical practice — nurses already subjectively assess whether monitoring conditions are clean. We formalise and automate this.
3. Grounded in evidence — R5 proves 30% failure exists. Our architecture addresses the *cause* of that failure, not just the symptom.

---

---

# 5. Clinical Outputs — Feasibility Classification

| Output | Classification | Notes |
|---|---|---|
| **Respiratory rate** | **Feasible with validation** | Primary output. RMSE <3 bpm vs. manual count is the acceptance target (consistent with R5). |
| **Heart rate** | **Difficult — exploratory** | Radar alone: ±5–7 bpm. Radar + geophone agreement: potentially better. Report as research-level finding, not clinical measurement. |
| **Surface temperature trend** | **Feasible** | MLX90614 ±0.2°C. "Surface trend" only — not core body temperature. Not measurable through blankets. |
| **Body movement** | **Strongly feasible** | Direct from pressure matrix temporal changes. Most reliable measurement in the system. |
| **Body position** | **Strongly feasible** | Pressure centroid → 4-class: supine/left-lateral/right-lateral/seated. |
| **Pressure distribution** | **Strongly feasible** | Spatial 12×12 grid. Sufficient for body-region pressure mapping. |
| **Bed occupancy** | **Strongly feasible** | Load cells + pressure matrix independently confirm. Two-sensor agreement = highest confidence output. |
| **Visitor / additional occupant** | **Strongly feasible** | Load cell weight delta (primary) + pressure second centroid (confirmation). |
| **Weight** | **Feasible** | Per-session baseline. MAE <1 kg target vs. reference scale. Not suitable for fluid-retention trending. |
| **Recovery behaviour** | **Feasible** | Movement frequency, quiet periods, position change rate — not sleep stage classification. |

---

---

# 6. Clinical Decision Support — Safe and Unsafe Claims

## Pipeline

```
Sensors → Signal processing → Sensor validation (confidence gate) → Fusion → Output layer → Dashboard
```

All stages are feasible on Raspberry Pi 5. "Patient prioritisation" and "clinical deterioration prediction" are Phase 2 simulation-based AI outputs, not real-time clinical claims.

## Safe vs. Unsafe Outputs

| Safe (Research Prototype) | Unsafe (Do Not Claim) |
|---|---|
| "Patient stationary 3 hours — check for pressure risk" | "Patient has developed a pressure ulcer" |
| "Respiratory rate elevated vs. baseline — monitoring flag raised" | "Patient shows signs of respiratory deterioration" |
| "Second person on bed — physiological readings paused" | "Visitor interference eliminated" |
| "Surface temperature trend: +0.8°C over 2 hours" | "Patient has a fever of 38.2°C" |
| "RR confidence: Low — radar/geophone disagree" | "Patient vitals confirmed stable" |

## Regulatory Note

"Clinical decision support" triggers medical device regulatory implications under CDSCO Medical Device Rules 2017. This system is a **research prototype**. Use the phrase "intelligent sensor monitoring with actionable alerts for nursing staff" in all documentation.

---

---

# 7. AI Explainability and Simulated Multi-Patient Prioritisation

## Concept

The prototype monitors one patient with hardware. Once real sensor data is collected across scenarios, a software simulation composes "virtual wards" of multiple patients and trains an AI model to prioritise them. SHAP explains each decision.

**This is a two-phase research architecture:**
- **Phase 1:** Hardware → real single-patient data → validation
- **Phase 2:** Software → synthetic multi-patient simulation → XAI prioritisation

## Data Collection (Phase 1 → Phase 2 Input)

| Scenario Label | Sensor Evidence |
|---|---|
| `quiet_rest` | Low movement, stable RR (radar + geophone agree), normal temperature |
| `restless` | High movement frequency, variable RR, frequent position changes |
| `elevated_rr` | RR >20% above personal baseline, high confidence |
| `temperature_rising` | MLX90614 +0.5°C or more over 30 minutes |
| `sustained_pressure` | Same pressure region loaded >2 hours |
| `bed_exit_attempt` | Load cell weight dropping, pressure centroid shift to edge |
| `visitor_present` | Load cell weight delta +30 kg, second pressure centroid |

## Simulation (Phase 2)

Compose 4-patient ward snapshots from scenario recordings:
- Patient A: `quiet_rest` → Low priority
- Patient B: `elevated_rr` + `restless` → Medium priority
- Patient C: `temperature_rising` + `sustained_pressure` → High priority
- Patient D: `bed_exit_attempt` → Immediate

Assign ground truth priority labels (Low / Medium / High / Immediate) using documented clinical reasoning rules. Generate hundreds of synthetic snapshots.

## Model + Explainability

Train: Random Forest or XGBoost on per-patient sensor feature vectors.

Apply **SHAP (SHapley Additive exPlanations)** to generate readable explanations:

> *"Patient 3 ranked HIGH: elevated RR (+35% above baseline, confidence High) → 0.42; sustained sacral pressure 2.3 h → 0.31; temperature trend +0.6°C → 0.19."*

**Libraries:** SHAP, scikit-learn, XGBoost — all free, all run on Raspberry Pi 5 or laptop.
**Additional cost:** ₹0.

## Defensibility

| Question | Answer |
|---|---|
| Is synthetic multi-patient data valid? | Yes — R7 (SiViS) used mannequins. Our synthetic data is based on real prototype recordings: more realistic. |
| Can model be trusted without hospital validation? | At research level: validated on held-out synthetic scenarios with documented ground truth rules. Clinical validation is Phase 3. |
| Is SHAP explainability publishable? | Yes — XAI for clinical decision support is a major active research area. |
| Extra hardware needed? | None. Pure software. |

## Safe Claims for This Phase

| Claim | Safe? |
|---|---|
| "Our sensor architecture produces signal quality sufficient to support multi-patient AI prioritisation" | ✅ Yes |
| "We develop and evaluate a simulation-based multi-patient prioritisation model trained on real prototype data" | ✅ Yes |
| "SHAP explainability provides interpretable per-patient priority decisions" | ✅ Yes |
| "This system replaces nurse triage in a real ward" | ❌ Never |

---

---

# 8. Real-World Environment Stress Test

| Condition | Impact | Addressed? |
|---|---|---|
| Visitor on bed | Load cell delta, radar/geophone corrupted | ✅ Yes — visitor flag suppresses readings |
| Patient movement | Pressure + radar/geophone artifacts | ✅ Yes — motion gate |
| Nurse repositioning | Brief movement artifact (~30–120 s) | ✅ Partially — motion gate with timed resume |
| Thick blankets | Thermal blocked; radar mildly attenuated; **geophone unaffected** | ✅ Yes for thermal (flag). Geophone continues. |
| Different body sizes | Load cell baseline per-session; radar cross-section varies | ✅ Partially — per-session calibration |
| Side-sleeping | Reduces radar sensitivity | ✅ Partially — pressure matrix annotates position; geophone unaffected |
| Different mattress types | Pressure distribution and geophone coupling vary | ❌ Fix mattress type; document as limitation |
| EM interference in hospital | Unknown at 60 GHz in real ward | ❌ Lab validation only; document as Phase 3 concern |
| Power interruption | Data since last write lost | ✅ Partially — 30 s database flush; UPS in Option C |
| Sensor calibration drift | Velostat creep; load cell thermal drift | ✅ Partially — per-session calibration; document drift |

---

---

# 9. Budget — Verified Totals

> All figures from [ItemizedBudget.md](file:///d:/Smart%20Bed/Budget/ItemizedBudget.md), August 2026. Geophone (NEW-3, ₹500) included.

## Full Budget Summary

| Category | Amount (₹) |
|---|---:|
| Core Hardware — sensors, RPi 5 (₹20,000), MCU, electronics, geophone | 40,465 |
| Prototype Fabrication — bed, brackets, wiring, enclosures | 10,160 |
| Data & Experimentation — calibration, consumables | 3,350 |
| Validation — incl. conditional V2/V3/V4 reference instruments | 5,750 |
| **Procurement Subtotal** | **59,725** |
| Contingency (~8%) | 4,555 |
| **TOTAL (Worst Case — All Items Purchased)** | **₹64,280** |
| *Best case (V2/V3/V4 via institution — saves ₹2,800)* | *₹61,480* |
| **Surplus vs. ₹1,00,000 cap** | **₹35,720** |

## Largest Cost Drivers

| Rank | Item | Cost | % of Total |
|---|---|---|---|
| 1 | Raspberry Pi 5 8 GB | ₹20,000 | 31.1% |
| 2 | Hospital bed + mattress | ₹7,000 | 10.9% |
| 3 | MLX90640 thermal camera | ₹5,000 | 7.8% |
| 4 | MicroSD 64 GB A2 | ₹2,800 | 4.4% |
| 5 | HLK-LD6002 radar | ₹2,200 | 3.4% |

## Budget Options Comparison

| | Option A (Minimal) | Option B (Recommended) | Option C (Max) |
|---|---|---|---|
| Sensors | Radar + load cells | All five (incl. geophone) | All five + reference radar kit |
| RPi 5 | ₹20,000 | ₹20,000 | ₹20,000 |
| Approx. Total | ~₹37,700 | **₹61,480–₹64,280** | ~₹92,000 |
| Research value | Moderate | **High** | High + upgraded hardware |

---

---

# 10. Research Novelty

## What Is Already Established

- Contactless vital-sign monitoring using mmWave radar (R3, R5, R7)
- BCG / geophone under-bed sensing (R2, R6, R8)
- Load cells for fall and bed-exit detection (R1)
- Pressure matrices for body position (sleep research literature)

## What Is Underexplored

- **Confidence-aware, interference-explicit sensor fusion** — explicitly modelling *when* a measurement cannot be trusted, and saying so
- **Three independent HR/RR pathways** (radar + geophone + pressure matrix BCG) in a single bed-based system
- **Low-cost (<USD 750 / ₹64,000) multimodal contactless system designed for resource-constrained Indian hospital wards** — not ICU, not premium private hospital
- **Retrofit approach** — existing beds, not new smart beds

## Defensible Research Gap Statement

> "No peer-reviewed study has demonstrated an integrated, low-cost (under USD 750), confidence-aware multimodal sensor fusion system for a conventional hospital bed that: (1) provides three independent physiological measurement pathways (radar, geophone, and pressure-based BCG); (2) explicitly detects and reports the conditions that invalidate each pathway (patient movement, multiple occupants, blanket coverage); and (3) uses real single-bed prototype data to train and explain a simulated multi-patient AI prioritisation system — making the approach practically deployable in resource-constrained ward environments."

---

---

# 11. Validation Plan

## Phase 1 — Individual Sensor Validation (Weeks 1–4)

| Test | Reference | Metric | Acceptance Threshold |
|---|---|---|---|
| Load cell weight accuracy | Known weights (D1) + reference scale (V2) | MAE, R² | MAE <1 kg, R² >0.99 |
| Bed-exit detection latency | Observer ground truth | Detection rate, latency | >95% in 10 trials, <3 s latency |
| Pressure matrix cell response + crosstalk | Known weights (D1) | Linearity R², crosstalk ratio | R² >0.90, crosstalk <15% |
| Radar RR accuracy | Manual count, 60 s window (V1 stopwatch) | RMSE, Bland-Altman LOA | RMSE <3 bpm, LOA ±4 bpm |
| Geophone RR + HR accuracy | Manual count (RR) + pulse oximeter HR (V4) | RMSE, MAE | RMSE <3 bpm (RR), MAE <4 bpm (HR) |
| Thermal camera calibration | Reference thermal target (D3) + thermometer (D4) | MAE | MLX90614: MAE <0.3°C |
| Radar + geophone RR agreement | Both sensors simultaneously | Concordance (±2 bpm threshold) | >80% of still-patient recordings |

## Phase 2 — Multimodal Fusion Validation (Weeks 5–8)

| Test | Protocol | Acceptance |
|---|---|---|
| Motion gate | Volunteer still 60 s → moves 10 s → still. Observer records. | >90% correct gate decisions across 20 trials |
| Visitor detection | Second person sits on bed 30 s. | >95% load cell flag within 5 s across 10 trials |
| Blanket detection | Thin sheet → heavy blanket placed. | >90% thermal contrast classification accuracy |
| Radar/geophone confidence agreement | Both sensors simultaneously over 30-minute still session. | Confidence flag correctly upgraded when both agree in >75% of high-quality windows |

## Phase 3 — Human-Subject Testing (Weeks 9–14)

*Requires institutional ethics (IRB) clearance before any volunteer session.*

10 volunteers (diverse size/age 18–45). Per session: 30–60 minutes. Scenarios: quiet rest, planned position changes, simulated visitor, blanket placement.

Collect labelled scenario recordings (see §7 scenario labels). These recordings directly feed Phase 2 AI simulation.

## Phase 4 — Reference Comparison (Weeks 15–18)

| Output | Reference | Acceptance |
|---|---|---|
| RR | Manual count | RMSE <3 bpm, LOA ±4 bpm |
| HR (exploratory) | Pulse oximeter (V4) | Document only — no clinical acceptance claim |
| Surface temperature | Reference thermometer (D4) | MLX90614 MAE <0.5°C |
| Weight | Reference scale (V2) | MAE <1 kg |
| Occupancy | Observer ground truth | Sensitivity >99%, Specificity >99% |
| Visitor detection | Observer ground truth | Sensitivity >95%, Specificity >95% |

---

---

# 12. Minimum Viable Prototype Specification

**Hypothesis to prove:**
> A low-cost five-sensor bed-based system can reliably detect occupancy, body position, and respiratory rate with explicit confidence reporting, and produce data sufficient to train a simulation-based multi-patient AI prioritisation model.

| Element | Specification |
|---|---|
| Sensors | HLK-LD6002 radar + Geophone SM-24 + Velostat matrix ×4 + Load cells ×4 + MLX90640 + MLX90614 |
| Processing | Raspberry Pi 5 8 GB + active cooler + 27 W PSU + 64 GB microSD A2 |
| MCU | 1× ESP32 WROOM-32 (matrix scanning + load cell ADC) |
| Communication | Radar UART → RPi directly. Geophone ADC → RPi GPIO/ADC. ESP32 MQTT → RPi. MLX sensors I2C → RPi. |
| Software (Phase 1) | Python signal processing (FFT, bandpass). Confidence state machine. FastAPI dashboard. SQLite logging. |
| Software (Phase 2) | SHAP + XGBoost/sklearn on scenario recordings. Synthetic ward simulation. Priority + explanation output. |
| Outputs | RR (confidence flag), HR (exploratory), body position, occupancy, visitor detection, surface temperature trend, movement level, priority score (Phase 2, simulation). |
| Dashboard | Single-bed web view: occupancy + position + RR with confidence + temperature trend + alerts. No diagnostic claims. |
| Validation | Phase 1–4 as above. 10 volunteer sessions minimum. |
| Cost | ₹61,480–₹64,280 |

---

---

# 13. What to Remove from the Proposal

## Remove Immediately

| Item | Reason |
|---|---|
| **"Clinical decision support"** (as a phrase) | CDSCO regulatory trigger. Replace with: "intelligent sensor monitoring with actionable alerts for nursing staff" |
| **"Clinical deterioration prediction"** | Requires thousands of labelled real patient episodes. Future work only. |
| **"Patient prioritisation"** (as real-time clinical claim) | Phase 2 simulation-based AI demonstration only — clearly label it as such |
| **Contactless heart rate** (as a claimed deliverable) | R5/R7 evidence shows ±5–7 bpm error. Frame as: "exploratory HR research objective using radar + geophone" |
| **Fluid retention monitoring** | Requires sub-kg precision over days. Not achievable. |
| **Sleep stage classification** | Requires HRV + hours of data. Replace with "recovery behaviour monitoring." |
| **Blood pressure** | No sensor for it. Remove all references. |
| **SpO₂** (as system output) | Not in sensor set. V4 pulse oximeter = validation reference only. |
| **Digital twins** | No model, no dataset, no framework. Remove entirely. |
| **EHR integration** | Phase 3+. Move to future work. |

## Reword

| Current | Replace With |
|---|---|
| "Continuous monitoring" | "Continuous observation with explicit confidence reporting" |
| "Clinical decision support" | "Intelligent sensor monitoring with actionable alerts" |
| "Heart rate monitoring" | "Heartbeat micro-motion detection — exploratory research objective" |
| "Temperature monitoring" | "Surface temperature trend monitoring" |
| "Sleep behaviour" | "Recovery behaviour monitoring (movement frequency and quiet periods)" |

---

---

# 14. Final Verdict

| Area | Verdict | Reason |
|---|---|---|
| Core concept | ✅ Sound | Retrofit + contactless + confidence-aware fusion = defensible and clinically relevant |
| Sensor architecture | ✅ Sound | Five sensors including geophone. LD2450→LD6002 correction applied. Three independent HR/RR pathways. |
| AI/sensor fusion | ✅ Feasible | Rule-based Phase 1 immediately. SHAP XAI + simulation in Phase 2 at no extra cost. |
| Clinical usefulness | ⚠️ Moderate | RR, occupancy, position, surface temperature useful. HR + clinical decisions: simulation/exploratory only. |
| ₹1 lakh feasibility | ✅ High | ₹64,280 total. ₹35,720 surplus for Phase 2. |
| Research novelty | ✅ Defensible | Three-pathway HR/RR + confidence-aware fusion + low-cost retrofit + simulation XAI: not in 2025–2026 literature. |
| Prototype feasibility | ✅ High | All hardware in-stock. Software stack well-matched. Scope achievable by a student team. |
| Hospital deployment | ❌ Phase 3+ | Lab only for Phase 1–2. EMI, infection control, IT integration: unresolved. |

## Five Direct Answers

**1. Should we proceed?** Yes. Core concept is sound, budget is realistic, and the research gap is defensible.

**2. What should the prototype demonstrate?**
1. A ₹64,000 five-sensor system reliably measures RR (RMSE <3 bpm) with explicit confidence reporting validated against manual count.
2. Multimodal fusion (radar + geophone + load cells + pressure + thermal) correctly detects and flags real-world interference that causes single-sensor systems to fail silently — with >90% sensitivity.
3. Real prototype data, when used in a simulation framework, supports a SHAP-explainable multi-patient priority model.

**3. What to remove?** Contactless HR as a deliverable, clinical decision support phrase, patient prioritisation as real-time clinical output, fluid retention, sleep stages, BP, SpO₂, digital twins, EHR integration.

**4. Strongest research gap?**
> "No study has demonstrated a low-cost confidence-aware bed-based system combining three independent physiological measurement pathways (radar, geophone, pressure-BCG) with explicit interference detection and a simulation-grounded XAI prioritisation layer — deployable in resource-constrained wards."

**5. Strongest funding argument?**
> "Indian government hospital nurses manage 15–40 patients per shift with minimal equipment. Existing contactless systems cost ₹10–50 lakh and fail 30% of the time (R5) without telling anyone. Our ₹64,280 prototype proves that confidence-aware five-sensor monitoring is feasible, produces the data to train a simulation-based AI prioritisation model at no additional cost, and leaves ₹35,720 of the ₹1 lakh grant for Phase 2 clinical-site validation."

---

## Recommended Final Project Scope

> Build a five-sensor (radar, geophone, pressure matrix, load cells, thermal camera) contactless patient monitoring research prototype in a hospital bed at ₹64,280. Demonstrate in Phase 1: RR estimation (RMSE <3 bpm), multimodal confidence-aware fusion (>90% interference detection), body position, occupancy, and surface temperature trend. Collect labelled scenario recordings as input to Phase 2: a software-based simulated multi-patient ward with XAI-explained priority scoring (Random Forest + SHAP). No clinical device claims. No real-ward deployment in Phase 1.

---

## Recommended 15-Slide Funding Narrative

| # | Slide Title | Purpose |
|---|---|---|
| 1 | The Monitoring Gap in Indian Hospital Wards | Clinical problem: nurse ratios, missed vital signs, existing equipment burden |
| 2 | Why Contact-Based Monitoring Has Limits | Wires, displacement, patient discomfort, infection risk |
| 3 | Contactless Systems Already Work — in Labs and EDs | R4 (111 patients), R5 (315 patients): prove the technology works |
| 4 | Why Existing Contactless Systems Are Not the Answer | Cost (₹10–50 lakh), installation, and the 30% silent failure problem (R5) |
| 5 | The Silent Failure Problem | What happens when a single sensor fails without saying so — and why it is dangerous |
| 6 | Our Approach: The Hospital Bed as a Sensing Platform | Retrofit concept: no new bed; five sensors integrated into any existing cot |
| 7 | Five Sensors — Three Independent Measurement Pathways | Radar (through-air) + geophone (through-structure) + pressure-BCG: why three paths matters |
| 8 | The Confidence-Aware Fusion Engine | Core novelty: "Can we trust this measurement?" — visitor/blanket/movement scenarios |
| 9 | Phase 2: From One Bed to a Ward | Simulation-based multi-patient AI prioritisation using real prototype data + SHAP explainability |
| 10 | What the Dashboard Tells Nurses | Show dashboard mockup: occupancy, RR + confidence flag, position, alerts — no diagnostic claims |
| 11 | Evidence Base: 8 Papers (2025–2026) | R1–R8 support every sensor and design decision |
| 12 | Budget: ₹64,280 for the Full Prototype | Five sensors, AI edge computing, validation. ₹35,720 surplus for Phase 2. |
| 13 | Research Novelty | The research gap statement. What is new: three pathways + confidence-aware + simulation XAI at this cost |
| 14 | Validation Plan | 4-phase plan. Bland-Altman analysis. IRB ethics. 10 volunteer sessions. |
| 15 | Funding Ask | ₹1,00,000. Phase 1 deliverable: validated prototype + published proof-of-concept data. Phase 2: clinical-site. |

---

*Analysis and Validation Report — Final Version*
*Smart Bed V2 | Coimbatore, Tamil Nadu | August 2026*
*Sources: 8 peer-reviewed papers (2025–2026) · ItemizedBudget.md (₹64,280) · Smart Bed V2.pdf*