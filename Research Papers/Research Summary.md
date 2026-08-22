# Research Summary — Smart Bed Project

> **Project Reference:** AI-Powered Multimodal Contactless Patient Monitoring & Clinical Decision Support System using the Hospital Bed as an Unobtrusive Sensing Platform.
>
> **Core Idea:** Retrofit a hospital bed with mmWave radar, pressure sensor matrix, load cells, and a thermal camera. Use AI to fuse sensor data, validate signal reliability, and generate clinically useful alerts — targeting resource-limited hospitals.

---

## How to Read This Document

Each paper is summarised under four headings:
- **What the paper is about** — A plain-language summary
- **Supports our project** — How it backs up our idea
- **Challenges our project** — What it warns us about
- **What we can learn / improve** — Practical takeaways

---

## Paper 1 — Multimodal Fall Detection Using Bed-Integrated Load Cells and Wrist Accelerometers

**Source:** Lee, Kim & Jeong — *Measurement*, Vol. 257 (2026), Elsevier
**DOI:** https://doi.org/10.1016/j.measurement.2025.118759
**Published:** August 2025

---

### What the paper is about

Researchers attached load cells to a bed frame and a wrist accelerometer to the subject's wrist. They trained a 1D Convolutional Neural Network (CNN) on data from 40 people doing fall and non-fall scenarios. The combined system reached **96.26% accuracy** for fall detection. The load-cell-only model was much weaker, but combining it with the wrist sensor improved performance dramatically by ~22%.

Key finding: **Low-frequency vibration signals (0–2 Hz) from load cells are the key biomarker** that distinguishes a fall event from normal bed movement.

---

### Supports our project

- Directly validates load cells on a bed frame as a practical, low-cost, contactless sensing option — exactly what we plan.
- Proves that load cells placed under the bed can detect meaningful physical events (not just weight).
- Shows that combining sensors (multimodal) always beats a single sensor — supports our entire fusion concept.
- The 1D CNN architecture they used is lightweight enough for embedded systems like Raspberry Pi.

---

### Challenges our project

- The hybrid system still needed a wrist-mounted accelerometer (a wearable) to reach high accuracy. Load cells alone were much less accurate.
- Testing was done on healthy young adults in simulated scenarios, not actual patients in a hospital ward.
- Bed conditions like mattress type, rail padding, and hospital bed construction were not varied — results may not transfer directly to our setup.

---

### What we can learn / improve

- Use the 0–2 Hz frequency band from load cells specifically for event detection (patient movement, bed exit, additional occupant).
- Even if we do not add a wearable, we can use this frequency-domain insight in our AI to flag suspicious load cell readings.
- We should test our load cell placement on the specific hospital bed frame we plan to use — different frames transmit vibration differently.
- Fall/bed-exit detection using load cells is a strong, publishable secondary feature we should include in our prototype.

---
---

## Paper 2 — A Novel Bed-Based Ballistocardiography System via Smartphone Integration

**Source:** Lopez-Ruiz et al. — *Sensors and Actuators: A. Physical*, Vol. 395 (2025), Elsevier
**DOI:** https://doi.org/10.1016/j.sna.2025.117058
**Published:** September 2025

---

### What the paper is about

Ballistocardiography (BCG) measures the tiny movements of the body caused by each heartbeat. This paper proposes an unusually simple approach: instead of embedding sensors in the mattress, they place a small ink dot marker on the side of the mattress and record it using a regular smartphone camera. Video processing extracts heartbeat-related and breathing-related signals. The longitudinal (lengthwise) and transverse (sideways) axes of the mattress naturally separate cardiac and respiratory signal components. The system detects heart rate, respiratory rate, sleep apnea, and cardiac arrhythmias.

---

### Supports our project

- Confirms that bed-based, non-contact vital sign monitoring is not only possible but achievable with very low-cost hardware (a smartphone camera).
- Validates that mattress micro-vibrations carry both cardiac and respiratory information — relevant to our pressure sensor matrix concept.
- Demonstrates that signal separation (cardiac vs. respiratory) is possible from the same physical signal, which parallels our AI fusion approach.
- The detection of arrhythmias and apnea (not just rates) shows that bed-based sensing has more clinical depth than people assume.

---

### Challenges our project

- This uses camera-based tracking of a visible marker — it requires a clear line of sight and is affected by lighting and blanket coverage.
- We are using radar and pressure sensors, not BCG cameras, so direct accuracy comparisons do not apply.
- The system was tested in controlled conditions — real hospital environments with multiple people, blankets, and frequent movement may degrade performance significantly.
- BCG is sensitive to body position changes and mattress type, which were not deeply explored.

---

### What we can learn / improve

- We should study which axis of mattress vibration carries cardiac vs. respiratory information — this can improve how we place and process our pressure sensor matrix readings.
- The idea of using mattress deformation data for arrhythmia hints (not diagnosis) is worth exploring as a future feature.
- Keep our scope realistic: this paper's system still requires controlled conditions. Do not claim our system can detect arrhythmias in a noisy hospital ward.
- Combining BCG-style signal analysis with our pressure matrix could be a novel direction for a future paper.

---
---

## Paper 3 — Contactless and Short-Range Vital Signs Detection with Doppler Radar (76–81 GHz mmWave)

**Source:** Chen, Lin, Zhong, Pai, Li & Lin — *Healthcare Technology Letters*, 2024, Wiley/IET
**DOI:** https://doi.org/10.1049/htl2.12075
**Published:** January 2024

---

### What the paper is about

This study built a contactless sensing system using a 76–81 GHz millimeter-wave Doppler radar in FMCW (Frequency-Modulated Continuous Wave) mode. The radar detects tiny chest movements from breathing and heartbeats. They tested it on healthy young participants in a lab, measuring Heart Rate (HR) and Respiratory Rate (RR). Results confirmed the feasibility of continuous, contactless vital sign detection using W-band mmWave radar.

---

### Supports our project

- Directly validates our mmWave radar choice — 76–81 GHz is the same frequency band used in affordable commercial mmWave modules (e.g., TI IWR1443).
- Shows that FMCW radar can isolate breathing and heartbeat signals from each other using frequency and phase analysis.
- Confirms that contactless monitoring eliminates the need for ECG patches, wires, and skin contact.
- The use of FMCW mode specifically to reduce motion interference is a practical technique we should implement.

---

### Challenges our project

- Tested on healthy young adults only — accuracy for elderly, obese, or unwell patients (our actual target population) is unknown.
- Lab conditions only — no blankets, no visitors, no movement interference tested.
- W-band radar is more expensive than lower-frequency options. We need to verify that an affordable module is sufficient.
- Heart rate estimation from radar remains harder than respiratory rate — accuracy for HR specifically needs validation.

---

### What we can learn / improve

- FMCW mode is the right radar mode for us — use chirp-based signal processing to separate breathing and heartbeat.
- Our AI should treat respiratory rate as a primary, more reliable output and heart rate as a secondary, lower-confidence output from the radar.
- We should implement a motion-detection pre-filter: radar output should only be processed for vitals when the patient is relatively still (confirmed by pressure matrix + load cells).
- Use this paper to justify our mmWave radar choice in our project report with a specific citation.

---
---

## Paper 4 — Clinical Validation of Non-Contact Vital Signs in an Emergency Department Setting

**Source:** Padaki, Zarzour, Keene, Canepa, Levin & Antonsen — *Frontiers in Medical Technology*, Vol. 7 (2026)
**DOI:** https://doi.org/10.3389/fmedt.2025.1728913
**Published:** January 2026

---

### What the paper is about

111 patients in a real hospital emergency department (ED) had their heart rate and respiratory rate measured using cameras on smartphones (Samsung Galaxy S24, iPhone 16 Pro) and a webcam, using software from Presage Technologies. These were compared against clinical-grade ECG and capnometry monitors. Results: camera-acquired HR correlated extremely highly (R = 0.99, RMSE = 1.62 bpm), and RR showed high correlation (R = 0.91, RMSE = 1.71). This is one of the first larger-scale clinical validations of camera-based contactless vital signs.

---

### Supports our project

- Proves that contactless vital sign monitoring can work in a real hospital setting (not just a lab) — the strongest form of validation.
- Demonstrates that HR and RR can be acquired without patient cooperation or skin contact in a busy ED.
- Confirms that the clinical problem we are targeting is real: vital signs are frequently missed in high-load settings like EDs and general wards.
- Supports the argument that contactless monitoring is clinically acceptable if validated — strengthens the case for our project.

---

### Challenges our project

- This uses camera-based rPPG (remote photoplethysmography), not radar or pressure sensors. Cameras work on skin colour changes — they require a clear view of exposed skin.
- Patients were seated and largely still — real ward patients lie under blankets, move, and turn.
- Camera-based vital signs require facial visibility, which is often not possible in a hospital bed.
- This technology uses proprietary commercial software — we cannot directly replicate this.

---

### What we can learn / improve

- This paper gives us a benchmark: our system should aim for RMSE less than 2 bpm for RR and less than 2 bpm for HR to be clinically comparable.
- We should report our accuracy numbers in the same format (RMSE, correlation, Bland-Altman) to make our results comparable and publishable.
- Include in our proposal that contactless vital sign monitoring has passed clinical validation in EDs — this builds the case for our approach.
- The 83% HR capture rate and 94% RR capture rate tell us to expect missed measurements — our system must handle gracefully the case where a reading is not available.

---
---

## Paper 5 — Development of Remote Radar-Based Vital Sign Acquisition for Emergency Department Patient Triage (TAMAR System)

**Source:** Shaya, Levy et al. — *Frontiers in Medical Technology*, Vol. 8 (2026)
**DOI:** https://doi.org/10.3389/fmedt.2026.1759641
**Published:** June 2026

---

### What the paper is about

ELTA Systems (an Israeli defence-tech company) developed a radar system called TAMAR for remotely measuring vital signs. It uses 24–24.24 GHz radar to detect chest/neck movement and pulse wave. 315 patients from 3 real hospital EDs were tested. The radar measured HR and RR simultaneously with a standard Mindray patient monitor. Result: Radar RR agreed within ±1.6 bpm and HR within ±4.7 bpm against clinical reference. The study concluded that TAMAR could potentially replace traditional monitors during triage.

---

### Supports our project

- Strongest clinical evidence that radar-based vital signs work in real hospitals with real patients — not a lab study.
- Multicenter study across 3 EDs, 315 patients — large and clinically significant.
- The HR and RR accuracy are within acceptable clinical limits, validating radar as a usable clinical tool.
- Specifically mentions use in infection control scenarios (COVID-like settings) — similar to our goal of monitoring without physical contact.

---

### Challenges our project

- TAMAR is a military-grade, proprietary system — our prototype cannot match its hardware quality.
- Patients were sitting/standing during triage, not lying in bed under blankets. Our use case is more complex.
- Only HR and RR were measured — no position, pressure, or fusion with other sensors.
- 30% of patients had missing measurements — even advanced commercial radar fails on a significant portion of patients. Our prototype should expect similar limitations.

---

### What we can learn / improve

- The 30% missing-measurement rate tells us: radar alone is not reliable enough. This is exactly why our multi-sensor fusion approach is justified — use this paper to make that argument.
- Use this paper's clinical validation framework (Bland-Altman analysis, LOA limits) as the template for our own validation experiment.
- Set realistic accuracy targets: LOA of ±10% of reference rate is the acceptance threshold used here. We should use the same.
- Our project's key novelty is combining radar with other sensors to reduce that missing-measurement problem — cite this paper to justify why fusion is needed.

---
---

## Paper 6 — A Ballistocardiogram Dataset with Reference ECG Signals for Bed-Based Heart Rhythm Assessment

**Source:** Qiu, Lyu, Liu, Cheng, Lu, Zhang & Shen — *Scientific Data* (Nature), 2025
**DOI:** https://doi.org/10.1038/s41597-025-05936-3
**Published:** 2025

---

### What the paper is about

This paper introduces a public dataset of ballistocardiogram (BCG) signals collected from subjects lying in bed, paired with ECG signals as reference. BCG captures the tiny mechanical movements of the body caused by each heartbeat — recorded through sensors embedded in or under the mattress. The dataset is designed to help researchers develop and benchmark AI models for non-contact heart rhythm monitoring (heart rate, inter-beat interval, rhythm irregularities).

---

### Supports our project

- Bed-based BCG is closely related to what our pressure matrix and load cells will capture — both measure body micro-vibrations from the mattress.
- Provides a public dataset we can potentially use to pre-train or test our AI signal processing algorithms without needing our own human subjects immediately.
- Confirms that heart rhythm information (including arrhythmia hints) can be extracted from bed-based mechanical sensing.
- Validates that ECG is the correct ground truth reference for benchmarking — we should use ECG comparison in our own validation.

---

### Challenges our project

- Most BCG datasets (including this one) use controlled lab conditions and healthy subjects — real patients with cardiac conditions produce noisier, weaker BCG signals.
- The paper notes that most BCG models do not generalise well to elderly or sick patients, which are our target users.
- BCG amplitude varies significantly with mattress type, body weight, and bed frame construction — what works in one setup may not work in another.

---

### What we can learn / improve

- Use this public dataset to test our signal processing pipeline before collecting real patient data — saves time and avoids ethical hurdles early in the project.
- Understand that different mattress types will change signal strength — we must test our pressure matrix on the specific mattress used in our target hospital.
- Focus our AI on respiratory rate and movement from the pressure matrix as primary outputs, and treat cardiac rhythm hints as a future enhancement.
- Cite this dataset in our report as evidence that bed-BCG is a recognised research area with available benchmarks.

---
---

## Paper 7 — SiViS: Simulated Multi-Patient Physiological Clinical States for Advanced Vital Sign Radar Monitoring Research

**Source:** Reyes, Gupta, Grosmaire et al. — *Scientific Data* (Nature), Vol. 13 (2026)
**DOI:** https://doi.org/10.1038/s41597-025-06449-9
**Published:** 2026

---

### What the paper is about

Researchers at VSB Technical University of Ostrava, in collaboration with a university training hospital, built a public radar dataset using medical simulation mannequins (SimMan 3G Plus). The mannequins can simulate different physiological states — healthy, apnea, cardiac arrest, severe respiratory distress. The dataset includes radar recordings from multiple distances, angles, and radar configurations. Preliminary results showed: mean heart rate error around 6.6 bpm, mean respiratory rate error around 1.47 bpm. The key challenge explored: simultaneously monitoring multiple patients using one radar.

---

### Supports our project

- Confirms that mmWave radar can detect physiological states beyond simple breathing (apnea, cardiac arrest scenarios).
- The 1.47 bpm RR error achieved even in multi-patient radar scenarios is clinically acceptable.
- Highlights that multi-patient monitoring is the next major challenge — directly relevant to our ward-deployment vision.
- The public dataset is available for us to test our algorithms on clinically simulated conditions.

---

### Challenges our project

- 6.6 bpm HR error is too high for clinical HR monitoring (typically ±5 bpm is the acceptable threshold) — this is in simulation, not real patients.
- Multi-patient radar monitoring is significantly harder than single-patient — overlapping signals, interference, and separation are unsolved problems.
- Mannequin data may not capture the full complexity of real human breathing and movement patterns.
- The study used advanced radar configurations not achievable with a single low-cost TI radar module.

---

### What we can learn / improve

- The 6.6 bpm HR error tells us: do not claim accurate heart rate monitoring from radar alone in our initial prototype. Frame it as HR trend estimation instead.
- Design our system to handle only one patient per bed in the first prototype — multi-patient radar is a research frontier, not a beginner project.
- Use the SiViS dataset to test our radar signal processing algorithms — it is publicly available and simulates real clinical scenarios.
- Note that varying radar placement (distance, angle) has a large impact — we need to fix and standardise our radar mounting position during our validation.

---
---

## Paper 8 — A Testbed for the Development and Validation of Contactless Vital Signs Monitoring Systems (SimDot)

**Source:** Pitafi, Yang, Chen, Song, Ye, Tse, Song & Song — *Sensors*, Vol. 26 (2026), MDPI
**DOI:** https://doi.org/10.3390/s26041092
**Published:** February 2026

---

### What the paper is about

The researchers built SimDot — a physical testbed (a mechanical simulator, not a human subject) that mimics heart and respiratory vibrations. It uses a Raspberry Pi-controlled voice coil motor as the vibration source. A geophone sensor placed under the bed detects the generated vibrations. The synthetic signals matched real human vibration data with a correlation of 0.85 (from 75 real subjects). The system helps researchers develop and test vital sign algorithms for extreme cases (40–240 bpm heart rate, arrhythmias) without needing to recruit patients.

---

### Supports our project

- Raspberry Pi is sufficient for controlling contactless vital sign sensing hardware — exactly what we plan to use.
- Validates that geophone/vibration-based under-bed sensing is a legitimate and accurate approach (MAE less than 2 bpm for HR and RR).
- Demonstrates that a testbed for algorithm development is a valid research contribution on its own — we could publish a similar testbed paper.
- The testbed concept is something we can build in our own lab to develop and test algorithms before real patient trials.

---

### Challenges our project

- Geophones are more sensitive to vibration than our planned pressure matrix — the type of sensor matters greatly, and direct accuracy comparisons do not apply.
- Vibration-based sensors under the bed are extremely sensitive to environmental noise (people walking nearby, hospital equipment vibrations, HVAC systems).
- The study used a single motor for both heart and lung signals — real human signals are more complex and irregular, especially in sick patients.
- No real human subjects were used in the testbed evaluation — the 0.85 correlation is promising but not equivalent to clinical validation.

---

### What we can learn / improve

- Consider building a simple testbed (even a basic mechanical vibration source) for early development — this lets us test algorithms without needing patients.
- Implement vibration noise filtering in our AI pipeline — hospital environments are much noisier than labs.
- The MAE less than 2 bpm benchmark is what we should target for our own system's RR estimation.
- If our project budget allows, adding a geophone or piezoelectric sensor under the mattress (in addition to the pressure matrix) could significantly improve our cardiac signal quality.

---

## Overall Cross-Paper Insights for Our Project

| Insight | Supported By |
|---|---|
| Multimodal sensing always beats single-sensor | Papers 1, 3, 5 |
| Load cells are proven, low-cost, and deployable | Papers 1, 6 |
| Radar HR accuracy has a known ~5–7 bpm error limit | Papers 5, 7 |
| Radar RR accuracy of ~1–2 bpm error is clinically acceptable | Papers 3, 4, 5, 7 |
| Blankets, movement, and visitors are the biggest real-world challenges | Papers 2, 3, 8 |
| Clinical validation requires Bland-Altman analysis + ECG reference | Papers 4, 5, 6 |
| Public datasets are available for pre-training our AI | Papers 6, 7 |
| Raspberry Pi is sufficient for our sensing and processing tasks | Paper 8 |
| Multi-patient radar monitoring is unsolved — single patient is realistic for now | Paper 7 |
| A testbed approach is a valid and publishable research output | Paper 8 |

---

## Key Warnings for the Team

- **Heart rate from radar:** All papers show ~5–7 bpm error in optimal conditions. In a real hospital, this will be worse. Label HR as "trend estimation" only — never claim clinical HR accuracy.

- **Blankets:** BCG and thermal camera performance degrades significantly under blankets. Our AI confidence scoring system must flag this explicitly.

- **Visitors:** Load cells are the only reliable way to detect an additional person on the bed. This must trigger reduced confidence in all physiological measurements.

- **Clinical claims:** None of these papers claim their system is ready to replace clinical ECG or SpO2 monitors. We must not claim this either. Our goal is to supplement monitoring, not replace it.
