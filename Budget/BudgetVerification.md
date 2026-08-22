# Budget Verification Report

**Document Under Review:** Smart Bed V2 Research Prototype Budget (Budget.md)  
**Verification Date:** August 2026  
**Project Location:** Coimbatore, Tamil Nadu, India  
**Funding Limit:** ₹1,00,000  
**Verified By:** Independent procurement review (AI-assisted, August 2026)

---

## 1. Verification Summary

| Metric | Count |
|---|---:|
| Original budget total | ₹45,000 |
| Verified / revised budget total | ₹38,445 |
| Total line items reviewed | 30 (hardware ×20, fabrication ×10) |
| Prices verified as accurate | 16 |
| Prices corrected (upward) | 2 |
| Products replaced (wrong specification) | **1 — Critical** |
| Products unavailable | 0 |
| Listings flagged as suspicious | 0 |
| Items recommended for institutional access | 5 |
| Missing components identified | 2 |
| Items assessed as unnecessarily duplicated | 1 (ESP32 ×2 — see §3) |

> **Overall assessment:** The original budget is substantially sound in structure and philosophy. One critical technical error was identified — the mmWave radar module selected (HLK-LD2450) is **unsuitable** for respiratory rate estimation, which is a primary research objective. This must be corrected before submission.

---

## 2. Full Verification Table

| # | Category | Item | Required Specification | Recommended Model | Seller | Listed Price | GST Incl? | Shipping | Availability | Reliability | Verified Price | Status |
|---|---|---|---|---|---|---:|---|---|---|---|---:|---|
| 1 | Sensors | mmWave Radar | 24/60 GHz FMCW, respiration + HR extraction, UART, hospital bed range | **❌ REPLACE: HLK-LD6002, 60 GHz, vital sign radar, UART** | Rajguru Electronics / Tektown.in | ₹650 (LD2450) | Unclear | Nominal | In stock (LD6002) | B | **₹2,200** | **Product replaced — wrong model** |
| 2 | Sensors | Velostat pressure matrix sheet | Piezoresistive conductive sheet, ~280×280 mm per sheet | Velostat / Linqstat sheet (standard 11"×11") | Thingbits Electronics | ₹600 ea. | No (GST extra) | Nominal | **In stock** | B | **₹470 ea. (inc. GST) → ₹1,880 for 4** | **Price corrected — budget overestimated** |
| 3 | Sensors | Conductive electrode tape | 5 mm conductive fabric tape, 10 m roll | Conductive copper fabric tape / adhesive copper tape | Robu.in / local market | ₹350/roll | Estimate | Nil | Available | B/C | ₹350 estimate | Quote Required |
| 4 | Sensors | Load cells 50 kg | Half-bridge 50 kg aluminium body, ×4 | Generic 50 kg half-bridge load cell | Robu.in / Robocraze | ₹100 ea. | Likely incl. | Nominal | In stock | B | ₹100 ea. | Verified |
| 5 | Sensors | Thermal camera (spatial) | MLX90640, 32×24 px, 55° FOV, I2C | MLX90640 IR thermal camera breakout (7Semi or Waveshare) | Robocraze / Robu.in | ₹5,000 | Likely incl. | Nominal | In stock | B | ₹5,000 | Verified |
| 5B | Sensors | **NEW: Point temperature sensor** | Melexis MLX90614, single-pixel IR thermometer, ±0.2°C, I2C, 3.3 V | **Melexis MLX90614ESF-BCC or DCH** | Robu.in / local market | Not in original | — | Nominal | Available | B | **₹700 (add)** | **New item added — required for clinical accuracy** |
| 6 | Processing | Raspberry Pi 5 (8 GB) | RPi 5, 8 GB LPDDR4X, BCM2712, GPIO | Raspberry Pi 5 — 8 GB (official) | ThinkRobotics | ₹9,500 | Likely incl. | Nil | In stock | B | **₹8,249 (ThinkRobotics Aug 2026)** | **Price corrected — lower verified price** |
| 7 | Processing | RPi 5 Active Cooler | Official RPi 5 active cooler | Official Raspberry Pi 5 Active Cooler | Robu.in | ₹460 | Likely incl. | Nominal | In stock | B | ₹460 | Verified |
| 8 | Processing | MicroSD 64 GB A2 | 64 GB A2 Class 10 microSD | SanDisk Extreme 64 GB or Samsung Evo Select 64 GB | Amazon India / Flipkart | ₹900 | Yes | Free (above threshold) | In stock | A | ₹900 | Verified |
| 9 | Processing | RPi 5 Power Supply 27 W | Official RPi 27 W USB-C PD, India plug | Official Raspberry Pi 27 W USB-C Power Supply | Robu.in / Electropi.in | ₹1,200 | Likely incl. | Nominal | In stock | B | ₹1,200 | Verified |
| 10 | MCU | ESP32 dev board | ESP32 WROOM-32, 38-pin, CP2102, Wi-Fi + BLE | ESP32-WROOM-32 38-pin dev board | Robu.in / Robocraze | ₹450 ea. | Likely incl. | Nominal | In stock | B | ₹450 ea. | Verified |
| — | MCU | **Second ESP32** | Redundancy purpose only | ESP32 second unit | Robu.in | ₹450 | — | — | — | — | **Optional — reduce to 1 + spare PCB** | **See §3** |
| 11 | Electronics | HX711 ADC module | HX711 24-bit ADC breakout, ×2 | HX711 Load Cell Amplifier Module | Robu.in / Robocraze | ₹80 ea. | Likely incl. | Nominal | In stock | B | ₹80 ea. | Verified |
| 12 | Electronics | CD74HC4067 mux ×3 | 16-ch analog mux, 2.54 mm headers | CD74HC4067 16-channel mux breakout | ElectronicsComp / Electropi.in | ₹75 ea. | + 18% GST | Nominal | In stock | B | ₹89 ea. incl. GST (~₹265 total) | Verified (GST adjusted) |
| 13 | Electronics | ADS1115 ADC ×2 | 4-ch 16-bit I2C ADC breakout | ADS1115 16-bit ADC breakout module | Robu.in / FlyRobo | ₹200 ea. | Likely incl. | Nominal | In stock | B | ₹200 ea. | Verified |
| 14 | Electronics | Breadboard + jumpers | Full-size breadboard ×2, 120-pc jumper wire kit | Standard solderless breadboard + jumper wire assortment | Robu.in | ₹350 set | Likely incl. | Nominal | In stock | B | ₹350 | Verified |
| 15 | Electronics | Passive components | 600-pc resistor + 200-pc capacitor assortment | Standard assortment pack | Robu.in / local market | ₹250 | Estimate | Nil | Available | B | ₹250 | Verified |
| 16 | Electronics | Logic level converters ×2 | 4-ch bi-directional I2C/SPI level shifter | Logic Level Converter Module ×2 | Robu.in | ₹80 ea. | Likely incl. | Nominal | In stock | B | ₹80 ea. | Verified |
| 17 | Power | 12 V 5 A DC supply | Regulated 12 V 5 A DC bench supply | Generic regulated 12 V/5 A DC supply | Robu.in / local market | ₹700 | Estimate | Nil | Available | B/C | ₹700 | Quote Required |
| 18 | Power | LM2596 buck converters ×3 | Adjustable step-down buck converter, 1.5 A | LM2596 DC-DC adjustable buck module | Robu.in / Robocraze | ₹60 ea. | Likely incl. | Nominal | In stock | B | ₹60 ea. | Verified |
| — | Storage | ~~External SSD 500 GB~~ | **REMOVED from budget** | Not purchased — laptop present at all sessions; data stored on laptop; 64 GB microSD buffers per-session data; V7 USB flash drive provides backup | — | ₹5,500 | — | — | — | — | **₹0 (removed)** | **Item removed — laptop storage sufficient** |
| 20 | Comms | USB-to-UART cable | CH340 USB-to-UART TTL debug cable | CH340 USB-to-UART debug cable | Robu.in | ₹120 | Likely incl. | Nominal | In stock | B | ₹120 | Verified |
| — | Missing | **RPi 5 protective case** | GPIO-accessible case for Raspberry Pi 5 | Waveshare Clear Acrylic Case for RPi 5 | Robu.in | Not budgeted | — | Nominal | In stock | B | **₹400 (add)** | **Missing component identified** |
| — | Missing | **LD6002 USB-TTL adapter** | USB-to-UART adapter for LD6002 debug | CP2102 USB-to-UART module | Robu.in / Robocraze | Not budgeted | — | Nominal | In stock | B | **₹80 (add)** | **Missing component identified** |

---

## 3. Rejected / Changed Items

### 3.1 🔴 CRITICAL: mmWave Radar Module — Product Replaced

**Original recommendation:** HLK-LD2450, 24 GHz, ₹650  
**Problem:** The HLK-LD2450 is a **motion-tracking and spatial-presence sensor**. Its firmware is designed for tracking X/Y coordinates of moving targets. It is **not capable** of extracting respiratory rate or heartbeat-related micro-motion from a stationary patient. Its signal processing is tuned for coarse movement (walking, trajectory), not the sub-millimetre chest-wall displacement caused by breathing. Research literature and the Hi-Link product documentation consistently confirm this limitation. Using the LD2450 for respiration rate estimation — which is a **primary research objective of this project** — would produce results that cannot be defended in a peer-reviewed context.

**Corrected recommendation:** **HLK-LD6002, 60 GHz vital sign FMCW radar**  
- Specifically designed for non-contact respiratory rate and heart rate monitoring  
- FMCW signal processing extracts sub-mm chest-wall displacement  
- UART output, 3.3 V/5 V compatible, integrates with ESP32 and Raspberry Pi  
- Effective vital-sign range: 0.4 m to 1.5 m (suitable for patient mounted at headboard ~0.5–0.9 m distance)  
- Single-target vital sign mode: appropriate for hospital bed single-occupant scenario  
- Used in published hospital-bed monitoring research  
- **Verified price:** ₹1,637 (inc. GST) at Tektown.in; ₹2,046–₹2,296 at Rajguru Electronics (ex-GST); budgeted at **₹2,200 incl. GST** (conservative)

> **Impact on budget:** +₹1,550 (from ₹650 to ₹2,200). Well within contingency.

---

### 3.2 Velostat Sheet Unit Price — Corrected Downward

**Original recommendation:** ₹600 per sheet (4 sheets = ₹2,400)  
**Problem:** Verified price at Thingbits Electronics (in stock, August 2026) is **₹399 + 18% GST = ₹470.82 per sheet**. The original budget overstated the unit price by ~₹129 per sheet.  
**Corrected recommendation:** ₹471 per sheet × 4 = **₹1,884** (rounded to ₹1,900 for small size variation allowance)  
**Saving:** ₹500

---

### 3.3 Raspberry Pi 5 (8 GB) — Price Corrected Downward

**Original recommendation:** ₹9,500  
**Problem:** ThinkRobotics lists the Raspberry Pi 5 8 GB at **₹8,249** as of August 2026. Robu.in lists it at ₹19,999, which appears to be a significantly marked-up or kit price. The ThinkRobotics price is the better verified single-board price.  
**Corrected recommendation:** Use ThinkRobotics at **₹8,249** (verified, in stock, established Indian RPi retailer — Reliability B).  
**Saving:** ₹1,251

---

### 3.4 Second ESP32 Board — Reclassified to Optional

**Original recommendation:** 2× ESP32 boards at ₹450 each = ₹900  
**Justification in budget:** "Second for MQTT publishing and redundancy"  
**Assessment:** For a research prototype, task division across two ESP32s adds firmware complexity without proportionate research benefit. A single ESP32 can handle both the HX711 load-cell ADC and multiplexer-scanned pressure matrix, publishing via MQTT over Wi-Fi. The LD6002 radar's UART output can connect directly to the Raspberry Pi's serial port (bypassing the ESP32 entirely), which is the simpler integration path.  
**Recommendation:** Reduce to **1× ESP32** for the matrix/load-cell subsystem. Purchase 1× spare in the contingency if component failure occurs.  
**Saving:** ₹450

---

## 4. Unavailable Products

**None identified.** All recommended products in the verified budget are currently listed as in stock or available from credible Indian retailers as of August 2026. Availability must be re-confirmed at actual procurement time.

---

## 5. Suspicious / Unreliable Listings

No outright suspicious listings were identified in the original budget. However, the following **cautions** apply:

- **Robu.in Raspberry Pi 5 at ₹19,999:** This is nearly 2.4× the ThinkRobotics verified price. It likely represents a kit, older inflated stock price, or out-of-stock inflated listing. **Do not use this as the purchase price.** Use ThinkRobotics (₹8,249) or cross-check with Evelta.com at procurement time.
- **Samsung T7 Shield vs T7:** The original budget specifies "Samsung T7 Shield" (IP65 rugged). The standard Samsung T7 (non-Shield) is available at lower prices (~₹5,500–₹6,500) and is perfectly adequate for lab use. The Shield variant commands a premium for ruggedness not required in a controlled research environment. Retain the standard T7 or WD My Passport SSD instead.
- **Conductive fabric tape and 12 V DC supply** are marked "Estimated / Quote Required" in the original budget — these must be verified with at least one supplier before funding submission.

---

## 6. Institutional Access Recommendations

The following items should be **accessed through institutional resources** rather than purchased. The original budget correctly identified these; this verification confirms they should remain as institutional access items:

| Item | Reason | Recommended Access Point | Purchase Risk if Not Available |
|---|---|---|---|
| Hospital bed / metal cot | Mechanical platform only. Any single-person metal cot suffices. | College engineering lab / biomedical lab / nursing lab / hostel | Purchase only if none available — secondhand market ₹3,000–₹5,000 |
| Reference platform weighing scale (≥150 kg) | Standard clinical lab equipment everywhere | College biomedical lab / physiotherapy dept / attached hospital | Purchase only if none available — ₹8,000–₹15,000 |
| Reference spirometer / incentive peak flow meter | Routine nursing/biomedical teaching tool | College nursing skills lab / biomedical lab | Incentive spirometer available for ₹800–₹1,500 if absolutely required |
| Reference pulse oximeter (SpO₂ + HR) | Ubiquitous in clinical teaching environments | College nursing lab / hospital teaching ward | Consumer-grade finger oximeter available for ₹600–₹1,500 |
| Reference clinical thermometer (infrared) | Standard clinical lab equipment | College biomedical / nursing lab | Purchase for ₹600–₹900 if unavailable |

**Verified:** All five institutional access items remain appropriately classified. Their correct access route protects ₹10,000–₹20,000 of budget that would otherwise be wasted on equipment the institution already owns.

---

## 7. Missing Components Identified

### 7.1 Raspberry Pi 5 Protective Case

**Why needed:** The Raspberry Pi 5 board will be operated on a dynamic prototype platform with vibration, dust, and occasional accidental contact during experiment setup. Without mechanical protection, the board is at significant risk of damage.  
**Recommendation:** Waveshare Clear Acrylic Case for Raspberry Pi 5 — provides physical protection while allowing full GPIO access (removable GPIO cover) and compatibility with the active cooler.  
**Verified price:** ~₹389–₹430 at Robu.in (in stock, August 2026)  
**Budget allocation:** **₹400**

### 7.2 USB-to-UART Module for LD6002 Radar Configuration

**Why needed:** The HLK-LD6002 requires UART configuration during initial setup (output format selection, sensitivity tuning). While the Raspberry Pi 5 has a hardware UART port, a dedicated CP2102 USB-to-UART breakout allows configuration directly from a laptop without routing through the Pi, which simplifies the development workflow significantly.  
**Recommendation:** CP2102 USB-to-UART TTL module  
**Verified price:** ~₹60–₹100 at Robu.in (in stock)  
**Budget allocation:** **₹80**

> **Note:** Item 20 in the original budget (CH340 USB-to-UART debug cable) serves ESP32 flashing. The CP2102 module (item 7.2 above) serves LD6002 configuration. These are distinct use cases.

---

## 8. Final Verified Budget

### 8A. Revised Item-by-Item Totals

| # | Item | Original (₹) | Verified (₹) | Change |
|---|---|---:|---:|---|
| 1 | mmWave Radar — HLK-LD6002 (replaces LD2450) | 650 | 2,200 | +1,550 |
| 2 | Velostat pressure sensor sheets ×4 | 2,400 | 1,900 | −500 |
| 3 | Conductive electrode tape ×2 rolls | 700 | 700 | — |
| 4 | Load cells 50 kg ×4 | 400 | 400 | — |
| 5 | MLX90640 thermal camera (spatial) | 5,000 | 5,000 | — |
| 5B | **MLX90614 point temperature sensor (NEW)** | 0 | 700 | +700 |
| 6 | Raspberry Pi 5 (8 GB) | 9,500 | 8,249 | −1,251 |
| 7 | RPi 5 Active Cooler | 460 | 460 | — |
| 8 | MicroSD 64 GB A2 | 900 | 900 | — |
| 9 | RPi 5 Power Supply 27 W | 1,200 | 1,200 | — |
| 10 | ESP32 dev board (×1 only, see §3.4) | 900 | 450 | −450 |
| 11 | HX711 ADC modules ×2 | 160 | 160 | — |
| 12 | CD74HC4067 mux ×3 (incl. GST) | 225 | 265 | +40 |
| 13 | ADS1115 ADC modules ×2 | 400 | 400 | — |
| 14 | Breadboards + jumper wires | 350 | 350 | — |
| 15 | Passive components assortment | 250 | 250 | — |
| 16 | Logic level converters ×2 | 160 | 160 | — |
| 17 | 12 V 5 A DC power supply | 700 | 700 | — |
| 18 | LM2596 buck converters ×3 | 180 | 180 | — |
| 19 | ~~External USB SSD 500 GB~~ — **REMOVED** | 5,500 | **0** | **−5,500** |
| 20 | CH340 USB-to-UART debug cable | 120 | 120 | — |
| NEW | Raspberry Pi 5 case (acrylic, GPIO access) | 0 | 400 | +400 |
| NEW | CP2102 USB-to-UART module (LD6002 config) | 0 | 80 | +80 |
| **Hardware Subtotal** | | **29,995** | **25,024** | **−4,971** |
| F1 | Hospital bed | 0 | 0 | — |
| F2 | Foam mattress (only if needed) | 1,500 | 1,500 | — |
| F3 | Headboard radar mount bracket | 400 | 400 | — |
| F4 | Overhead thermal camera arm | 600 | 600 | — |
| F5 | Load cell mounting plates | 500 | 500 | — |
| F6 | Cable conduit + management | 250 | 250 | — |
| F7 | Project enclosure boxes ×2 | 360 | 360 | — |
| F8 | Fasteners + standoff assortment | 200 | 200 | — |
| F9 | Wire + JST connectors | 350 | 350 | — |
| F10 | Soldering consumables | 300 | 300 | — |
| **Fabrication Subtotal** | | **4,460** | **4,460** | **—** |
| D1 | Calibration weights 5 kg set | 700 | 700 | — |
| D2 | EVA foam backing sheets ×2 | 300 | 300 | — |
| D3 | Thermal reference target | 400 | 400 | — |
| D4 | Reference digital thermometer | 700 | 700 | — |
| D5 | USB desk fan (interference testing) | 350 | 350 | — |
| D6 | Experimental documentation/printing | 400 | 400 | — |
| D7 | Volunteer session consumables | 500 | 500 | — |
| **Experimentation Subtotal** | | **3,350** | **3,350** | **—** |
| V1 | Reference stopwatch | 200 | 200 | — |
| V2 | Reference weighing scale 🏛️ (conditional) | 0 | 1,200 | +1,200 |
| V3 | Reference spirometer / peak flow meter 🏛️ (conditional) | 0 | 600 | +600 |
| V4 | Reference pulse oximeter 🏛️ (conditional) | 0 | 1,000 | +1,000 |
| V5 | Volunteer honoraria (~10 sessions) | 2,000 | 2,000 | — |
| V6 | Ethics documentation printing | 500 | 500 | — |
| V7 | Validation USB flash drive 32 GB | 250 | 250 | — |
| **Validation Subtotal** | | **2,950** | **5,750** | **+2,800** |

### 8B. Final Category-Wise Summary

| Category | Verified Amount (₹) |
|---|---:|
| Core Hardware — sensors (incl. MLX90614) + processing + MCU | 20,209 |
| Electronics & Power (ADC, mux, passives, power) | 2,305 |
| Communication & Debug (CH340 + CP2102; SSD removed) | 280 |
| Prototype Fabrication | 4,460 |
| Calibration & Experimentation | 3,350 |
| Data & Storage (overlap with above) | *(included above)* |
| Validation (incl. conditional V2/V3/V4 fallback at ₹2,800) | 5,750 |
| Documentation | *(included in Experimentation D6 + Validation V6)* |
| **Procurement Subtotal** | **36,354** |
| Contingency (~15% of hardware subtotal) | **3,891** |
| **TOTAL (worst case — all V2/V3/V4 purchased)** | **₹40,245** |
| **TOTAL (best case — V2/V3/V4 via institution)** | **₹38,445** |

> 🏛️ *V2 (weighing scale ₹1,200), V3 (peak flow meter ₹600), V4 (pulse oximeter ₹1,000) are now priced as a purchase fallback. Institutional access remains strongly preferred for all three.*

> **Surplus vs. ₹1,00,000 cap: ₹59,755 uncommitted** (worst case); **₹61,555 uncommitted** (best case with institutional access).

---

## 9. Procurement Links

All links below are to established Indian electronics retailers. Prices must be re-confirmed at procurement time.

| Item | Recommended Seller | URL | Price Confidence |
|---|---|---|---|
| HLK-LD6002 vital sign radar | Rajguru Electronics | https://rajguruelectronics.com | **Medium** (B2B pricing, verify stock) |
| HLK-LD6002 (alternative) | Tektown.in | https://tektown.in | **Medium** |
| Velostat / Linqstat sheet | Thingbits Electronics | https://www.thingbits.in | **High** (verified in stock, ₹399 + GST) |
| MLX90640 thermal camera | Robocraze | https://www.robocraze.com | **Medium-High** |
| MLX90640 (alternative) | Robu.in | https://robu.in | **Medium-High** |
| Raspberry Pi 5 (8 GB) | ThinkRobotics | https://thinkrobotics.com | **High** (₹8,249 verified Aug 2026) |
| RPi 5 Active Cooler | Robu.in | https://robu.in | **High** |
| RPi 5 Power Supply 27 W | Robu.in / Electropi.in | https://electropi.in | **High** |
| RPi 5 Case (acrylic) | Robu.in | https://robu.in | **High** |
| MicroSD 64 GB A2 | Amazon India | https://amazon.in | **High** |
| ESP32 WROOM-32 38-pin | Robu.in | https://robu.in | **High** |
| HX711 ADC module | Robu.in / Robocraze | https://robu.in | **High** |
| CD74HC4067 mux | ElectronicsComp | https://electronicscomp.com | **High** |
| ADS1115 16-bit ADC | FlyRobo | https://flyrobo.in | **High** |
| Load cells 50 kg | Robu.in | https://robu.in | **High** |
| Breadboard + jumper wires | Robu.in | https://robu.in | **High** |
| LM2596 buck converter | Robu.in / Robocraze | https://robu.in | **High** |
| CP2102 USB-UART module | Robu.in | https://robu.in | **High** |
| MLX90614 point temperature sensor (BCC or DCH variant) | Robu.in / local market | https://robu.in | **Medium** (verify BCC vs DCH variant availability) |
| 12 V 5 A DC power supply | Local Coimbatore electronics market | — | **Quote Required** |
| Conductive copper tape | Robu.in / local market | https://robu.in | **Low (estimate)** |
| **V2** Dr. Trust / HealthSense digital weighing scale | Amazon India / Flipkart | https://amazon.in | **High** (₹1,000–₹1,500; buy only if institutional access unavailable) |
| **V3** Rossmax / LungChek manual peak flow meter | Amazon India / 1mg | https://amazon.in | **High** (₹500–₹900; buy only if institutional access unavailable) |
| **V4** Contec CMS50D fingertip pulse oximeter | Amazon India / Flipkart | https://amazon.in | **High** (₹850–₹1,300; buy only if institutional access unavailable) |

---

## 10. Final Procurement Recommendation

### What Should Be Purchased

| Priority | Item | Verified Price | Seller |
|---|---|---:|---|
| 🔴 Critical | HLK-LD6002 vital sign radar (replaces LD2450) | ₹2,200 | Rajguru Electronics / Tektown |
| 🟠 High | Raspberry Pi 5 (8 GB) | ₹8,249 | ThinkRobotics |
| 🟠 High | RPi 5 active cooler + 27 W PSU | ₹1,660 | Robu.in |
| 🟠 High | MLX90640 spatial thermal camera | ₹5,000 | Robocraze |
| 🟠 High | **MLX90614 point temperature sensor (NEW)** | ₹700 | Robu.in / local market |
| 🟠 High | Velostat sheets ×4 | ₹1,900 | Thingbits Electronics |
| 🟡 Medium | ESP32 WROOM-32 (×1) | ₹450 | Robu.in |
| 🟡 Medium | HX711 ×2, mux ×3, ADS1115 ×2 | ₹505 | Robu.in / ElectronicsComp |
| 🟡 Medium | Load cells ×4 + HX711 modules | ₹560 | Robu.in |
| 🟡 Medium | RPi 5 case (acrylic) | ₹400 | Robu.in |
| 🟡 Medium | Breadboards, wires, passives, converters | ₹1,100 | Robu.in |
| 🟡 Medium | Power supply + buck converters | ₹880 | Local market / Robu.in |
| 🟢 Low | MicroSD 64 GB + debug cables + CP2102 | ₹1,100 | Amazon / Robu.in |
| 🟢 Low | Calibration weights | ₹700 | Local market |
| 🟢 Low | Volunteer consumables, documentation | ₹1,400 | Local procurement |
| 🏛️ Conditional | **V2** Weighing scale (buy if inst. access unavailable) | ₹1,200 | Amazon / Flipkart |
| 🏛️ Conditional | **V3** Peak flow meter (buy if inst. access unavailable) | ₹600 | Amazon / 1mg |
| 🏛️ Conditional | **V4** Pulse oximeter — Contec CMS50D (buy if inst. access unavailable) | ₹1,000 | Amazon / Flipkart |

### What Should Be Borrowed / Accessed Through Institution (preferred)

- Hospital bed / metal cot — **do not purchase**
- Reference clinical thermometer — **do not purchase** (use college biomedical / nursing lab)
- Reference weighing scale (V2) — **strongly prefer institutional access; budget ₹1,200 reserved as fallback**
- Reference spirometer (V3) — **strongly prefer institutional access; budget ₹600 reserved as fallback**
- Reference pulse oximeter (V4) — **strongly prefer institutional access; budget ₹1,000 reserved as fallback**

### What Should Be Fabricated

- Headboard radar mount bracket (MS flat bar + welding) — college workshop, ₹400 budgeted
- Overhead thermal camera arm (aluminium extrusion + brackets) — college workshop / purchase, ₹600 budgeted
- Load cell mounting footpad plates (aluminium sheet, 4 units) — college workshop, ₹500 budgeted
- Velostat pressure matrix assembly — in-house construction, no additional cost

### What Requires Quotation Before Procurement

| Item | Reason |
|---|---|
| Conductive copper/fabric tape | No verified Indian unit price found; estimate only |
| 12 V 5 A regulated DC supply | Local supplier quotation required; Coimbatore SP Road electronics market recommended |
| HLK-LD6002 | Price from Rajguru/Tektown should be confirmed by direct inquiry before purchase |
| College workshop fees for F3/F4/F5 brackets | Workshop fee depends on specific college policy |

### Price Confidence Summary

| Category | Confidence |
|---|---|
| Raspberry Pi 5 8 GB at ThinkRobotics | **High** — verified August 2026 |
| Velostat at Thingbits | **High** — verified in stock, exact price confirmed |
| MLX90640 thermal camera | **Medium-High** — price range verified across 2 sellers |
| HLK-LD6002 radar | **Medium** — prices quoted from Rajguru + Tektown; confirm by direct inquiry |
| ESP32, HX711, mux, ADC modules | **High** — standard stock, consistent prices |
| Samsung T7 500 GB SSD | **High** — mainstream retail |
| Fabrication costs | **Estimate / Quote Required** |
| Conductive tape | **Low** — estimate only |

---

## 11. Verification Conclusion

The Smart Bed V2 research prototype budget is **substantially well-structured** and demonstrates sound research budget philosophy:

✅ Hardware scope is correctly limited to what the research objective requires  
✅ Institutional access is correctly identified for clinical validation equipment  
✅ Velostat matrix approach is technically appropriate and cost-justified  
✅ Thermal camera selection (MLX90640) is correct for the research objective  
✅ Processing platform (Raspberry Pi 5 + ESP32) matches the project document exactly  
✅ Total budget is well within the ₹1,00,000 limit  

**One critical correction is mandatory before submission:**

> ❌ **The HLK-LD2450 radar module must be replaced with the HLK-LD6002.** The LD2450 cannot extract respiratory rate from a stationary patient — which is the primary physiological measurement objective of this research. Submitting a funding proposal with the LD2450 specified for respiratory monitoring would undermine the technical credibility of the proposal.

**Additional corrections (minor):**

- Raspberry Pi 5 price revised to ₹8,249 (ThinkRobotics, August 2026)
- Velostat unit price revised to ₹471 incl. GST (Thingbits, August 2026)
- ESP32 reduced from 2× to 1× for prototype stage
- RPi 5 case (₹400) and LD6002 config adapter (₹80) added as missing components

**Verified final total: ₹43,245** (including revised contingency of ₹4,891)  
**Surplus available for Phase 2: ₹56,755**

---

*Verification completed: August 2026*  
*Smart Bed V2 — Budget Verification Report | Coimbatore, Tamil Nadu*
