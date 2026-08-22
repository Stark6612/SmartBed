# Slide 9 Diagram — Hardware Architecture

> **Usage:** Embed or screenshot this diagram for Slide 9 of the presentation.  
> Renders natively in GitHub, Obsidian, Notion, and VS Code with Mermaid extension.

---

```mermaid
flowchart TB
    subgraph SL["🔵 Sensor Layer"]
        direction TB
        R["📡 HLK-LD6002\n60 GHz mmWave Radar\nVital Sign FMCW"]
        G["🔊 SM-24 Geophone\nUnder-Mattress BCG\nStructural Vibration"]
        PM["🟩 Velostat Matrix\n12 × 12 Pressure Grid\nMattress Surface"]
        LC["⚖️ Load Cells × 4\n50 kg Half-Bridge\nBed Leg Footpads"]
        TA["🌡️ MLX90640\n32×24 Thermal Array\nOverhead 1.2 m"]
        TP["🌡️ MLX90614\nPoint IR ±0.2 °C\nHeadboard"]
    end

    subgraph ML["🟡 Microcontroller Layer — ESP32"]
        direction LR
        MUX["CD74HC4067\nMux × 3\nMatrix Scan"]
        ADC["ADS1115 × 2\n16-bit ADC\nGeophone + Matrix"]
        HX["HX711 × 2\n24-bit ADC\nLoad Cells"]
        LLC["Logic Level\nConverter × 2\n3.3 V ↔ 5 V"]
    end

    subgraph EL["🟢 Edge Compute — Raspberry Pi 5 (8 GB)"]
        direction LR
        SP["Signal\nProcessing\nSciPy / NumPy"]
        FE["Fusion\nEngine\nState Machine"]
        DB["SQLite\nDatabase\n30 s flush"]
        API["FastAPI\nWebSocket\nBackend"]
    end

    subgraph PW["⚡ Power Subsystem"]
        PS["12 V · 5 A\nRegulated Supply"]
        BK["LM2596 × 3\nBuck Converters\n5 V / 3.3 V Rails"]
        PS --> BK
    end

    subgraph OUT["🖥️ Output"]
        DASH["Nurse Dashboard\nSingle-Bed View\n+ Ward Priority Queue"]
    end

    R       -- "UART\ndirect"      --> EL
    TA      -- "I2C\ndirect"       --> EL
    TP      -- "I2C\ndirect"       --> EL
    G       -- "Analog"            --> ADC
    PM      -- "Analog"            --> MUX --> ADC
    LC      -- "Analog"            --> HX
    ADC     --> ML
    HX      --> ML
    LLC     --> ML
    ML      -- "Wi-Fi\nMQTT"       --> EL
    BK      -- "5 V / 3.3 V"       --> ML
    SP --> FE --> DB --> API --> DASH

    style SL fill:#0d2137,color:#cde,stroke:#2e75b6
    style ML fill:#1a2e1a,color:#cec,stroke:#70ad47
    style EL fill:#1a1a2e,color:#ccf,stroke:#7030a0
    style PW fill:#1a1a1a,color:#eee,stroke:#555
    style OUT fill:#1a2020,color:#cfe,stroke:#00b0a0
```

---

## Component Reference Table

| Layer | Component | Role |
|---|---|---|
| Sensor | HLK-LD6002 (60 GHz FMCW) | Chest wall displacement → RR (primary), HR (exploratory) |
| Sensor | SM-24 Geophone | Structural BCG → RR + HR independent pathway |
| Sensor | Velostat 12×12 Matrix | Body position centroid, movement gate, contact micro-vibration |
| Sensor | Load Cells ×4 + HX711 ×2 | Weight, occupancy, visitor (+30 kg delta), bed-exit (<3 s) |
| Sensor | MLX90640 (32×24 px) | Spatial thermal map, blanket detection, body outline |
| Sensor | MLX90614 (±0.2°C) | Point surface temperature trend |
| MCU | ESP32 WROOM-32 | Scans matrix (via CD74HC4067), reads load cells (via HX711), publishes MQTT |
| MCU | ADS1115 ×2 | 16-bit analog sampling for geophone and pressure matrix signals |
| MCU | CD74HC4067 ×3 | 16-channel mux for 12×12 grid (144-cell) row-column scanning |
| MCU | Logic Level Converters ×2 | 3.3 V ↔ 5 V signal translation at I2C and GPIO interfaces |
| Edge | Raspberry Pi 5 (8 GB) | Signal processing, confidence fusion engine, FastAPI server, SQLite |
| Power | 12 V 5 A Supply + LM2596 ×3 | Regulated 5 V and 3.3 V rails for MCU and sensor subsystems |

---

*Slide 9 Diagram — Hardware Architecture | Smart Bed V2 | August 2026*
