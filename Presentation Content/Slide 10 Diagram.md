# Slide 10 Diagram — Software Architecture & Data Flow

> **Usage:** Embed or screenshot this diagram for Slide 10 of the presentation.  
> Renders natively in GitHub, Obsidian, Notion, and VS Code with Mermaid extension.

---

```mermaid
flowchart TD
    subgraph IN["📥 Data Ingestion"]
        E["ESP32 → MQTT\nPressure matrix + load cells\n10 Hz JSON payloads"]
        R["Radar → UART\nI/Q phase stream\nDirect serial to RPi"]
        T["Thermal → I2C\nMLX90640 + MLX90614\n1 Hz polling"]
        GE["Geophone → ADS1115\nAnalog voltage\n100 Hz sampling"]
    end

    subgraph SP["⚙️ Signal Processing  (NumPy / SciPy)"]
        direction LR
        SR["Radar\nFFT phase demodulation\nBandpass 0.1–0.5 Hz → RR"]
        SG["Geophone\nDual Butterworth filter\n0.1–0.5 Hz RR · 0.8–2.5 Hz HR"]
        SC["Pressure Matrix\nCentroid: X̄ = Σ(Xᵢ·Pᵢ)/ΣPᵢ\nPosition + movement gradient"]
        ST["Thermal\nContrast index\nAbsolute + relative temp"]
    end

    subgraph FU["🔀 Confidence-Aware Fusion Engine"]
        direction TB
        G1{"Occupancy\nCheck"}
        G2{"Visitor\nDetection"}
        G3{"Motion\nGate"}
        G4{"Blanket\nDetection"}
        G5{"3-Way RR\nAgreement\n±2 bpm?"}
        HC["🟢 HIGH CONFIDENCE\nPublish all outputs"]
        LC2["🟡 LOW CONFIDENCE\nPublish with flag"]
        SUP["🔴 SUPPRESSED\nAlert only"]
    end

    subgraph ST2["💾 Storage Layer"]
        DB["SQLite Database\nPer-session logs\nFlush every 30 s"]
    end

    subgraph AP["🚀 API Layer"]
        FA["FastAPI Server\nWebSocket real-time stream\nREST endpoint for history"]
    end

    subgraph UI["🖥️ Nurse Dashboard (HTML / JS)"]
        BV["Single-Bed View\nOccupancy · Position\nRR + Confidence · Temp Trend\nAlerts"]
        WV["Ward Priority Queue\nPhase 2 — XGBoost + SHAP\nRanked list + explanations"]
    end

    E & R & T & GE --> SP
    SR & SG & SC & ST --> G1
    G1 -- "Unoccupied" --> SUP
    G1 -- "Occupied" --> G2
    G2 -- "Visitor" --> SUP
    G2 -- "Single" --> G3
    G3 -- "Moving" --> LC2
    G3 -- "Still" --> G4
    G4 -- "Obscured" --> LC2
    G4 -- "Clear" --> G5
    G5 -- "Agree" --> HC
    G5 -- "Disagree" --> LC2

    HC & LC2 --> DB
    SUP --> FA
    DB --> FA
    FA --> BV & WV

    style IN  fill:#0d2137,color:#cde,stroke:#2e75b6
    style SP  fill:#1a2e1a,color:#cec,stroke:#70ad47
    style FU  fill:#1a1a2e,color:#ccf,stroke:#7030a0
    style ST2 fill:#1a1a1a,color:#eee,stroke:#888
    style AP  fill:#1a1e2e,color:#ccf,stroke:#4472c4
    style UI  fill:#1a2020,color:#cfe,stroke:#00b0a0
```

---

## Pipeline Stage Reference

| Stage | Technology | Inputs | Outputs |
|---|---|---|---|
| **Data Ingestion** | Mosquitto MQTT, pySerial, smbus2 | Raw sensor bytes | Parsed JSON / NumPy arrays |
| **Signal Processing** | SciPy (Butterworth, FFT), NumPy | Raw time-series | RR estimate, HR estimate, centroid (X̄, Ȳ), thermal contrast index |
| **Fusion Engine** | Python state machine (rule-based) | All processed signals | Confidence state + validated measurements |
| **Storage** | SQLite (WAL mode) | Validated outputs | Per-session time-series database |
| **API** | FastAPI + uvicorn + WebSocket | SQLite + fusion events | JSON streams to frontend |
| **Dashboard** | HTML / JS / Chart.js | FastAPI WebSocket | Real-time single-bed view + Phase 2 ward queue |

---

## Signal Processing Details

| Signal | Filter Type | Frequency Band | Output |
|---|---|---|---|
| Radar phase | FFT + Butterworth bandpass | 0.1–0.5 Hz | Respiratory Rate (bpm) |
| Geophone (breathing) | Butterworth bandpass | 0.1–0.5 Hz | Respiratory Rate — independent path |
| Geophone (cardiac) | Butterworth bandpass | 0.8–2.5 Hz | Exploratory Heart Rate |
| Pressure matrix | Spatial centroid computation | N/A | Body position (X̄, Ȳ) + movement level |
| Thermal | Contrast index + relative temp | N/A | Blanket flag + surface temperature trend |

---

*Slide 10 Diagram — Software Architecture & Data Flow | Smart Bed V2 | August 2026*
