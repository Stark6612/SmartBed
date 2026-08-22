# Smart Bed V2 — Research Prototype Budget Planning Prompt

You are preparing a realistic procurement budget for the research project described in the attached **Smart Bed V2.pdf**.

Your goal is to estimate the budget required to build a **research prototype** of the proposed AI-Powered Multimodal Contactless Patient Monitoring & Clinical Decision Support System.

## Project Objective

The objective is **NOT** to build a premium, production-ready, hospital-certified smart bed.

The objective is to build a sufficiently functional **research prototype that proves the core technical concept**, generates measurable experimental data, and is suitable for **initial clinical validation** against reference medical equipment.

The funding limit is:

**₹1,00,000**

The existing project document estimates the prototype at approximately ₹50,000–₹70,000. Do not artificially increase hardware costs simply to consume the entire ₹1 lakh.

The funding should instead demonstrate:

> **₹1 lakh → research prototype → experimental data → validation → proof of concept**

and NOT:

> **₹1 lakh → expensive collection of sensors**

---

## Primary Source

Use the attached **Smart Bed V2.pdf** as the primary source for determining:

- The project's objectives
- Required clinical parameters
- Sensor architecture
- Sensor placement
- Hardware architecture
- Software architecture
- Research challenges
- Validation requirements
- Existing estimated costs

Do not introduce major components that are unrelated to the architecture described in the PDF.

The PDF identifies the core hardware as:

- mmWave Radar
- Pressure Sensor Matrix
- Load Cells
- Thermal Camera
- ESP32
- Raspberry Pi 5
- Electronics & Fabrication

It also identifies the need for calibration, validation, sensor synchronization, environmental-interference testing, signal reliability testing, and clinical validation.

---

# Budget Philosophy

Prioritize expenditure according to what is necessary to prove the research hypothesis.

Structure the ₹1,00,000 around:

## 1. Core Hardware

Include only the hardware necessary for the research prototype:

- Sensors
- Edge computing
- Microcontrollers
- ADC/interface electronics
- Power supplies
- Storage
- Communication hardware
- Necessary supporting electronics

## 2. Prototype Fabrication

Include:

- Bed modification
- Sensor mounting
- Mechanical brackets
- Wiring
- Cable management
- Enclosures
- Protective structures
- Fabrication/assembly costs

The hospital bed is being used as an unobtrusive sensing platform, not as the main product.

## 3. Calibration & Experimental Setup

Include:

- Calibration equipment
- Reference measurements
- Test materials
- Experimental accessories
- Storage for collected data
- Environmental/interference testing materials

Do NOT automatically purchase expensive clinical equipment if the same equipment can realistically be accessed through a college laboratory, hospital, research collaborator, or department.

Clearly mark such items as:

**"Institutional/clinical access recommended instead of purchase."**

## 4. Validation

Include realistic costs associated with:

- Testing
- Reference measurements
- Experimental sessions
- Data collection
- Calibration
- Validation documentation
- Comparison with clinically accepted equipment

The objective is to demonstrate that the prototype's measurements and derived observations can be evaluated against reference measurements.

## 5. Documentation & Contingency

Include reasonable amounts for:

- Technical documentation
- Prototype documentation
- Printing/labels if genuinely required
- Replacement components
- Unexpected fabrication/electronics requirements
- Minor repairs
- Price variation

Maintain a sensible contingency rather than artificially increasing individual component prices.

---

# Procurement Research Requirements

This is for a funding proposal, so every significant purchased item must have a realistic Indian-market price.

The project location is:

**Coimbatore, Tamil Nadu, India**

Prefer products that can realistically be purchased and delivered to India/Coimbatore.

For every item that receives a budget allocation, provide:

1. Item name
2. Exact required specification
3. Recommended product/model
4. Quantity
5. Unit price in INR
6. Total price
7. Why this amount is allocated
8. Purchase/access/fabrication status
9. Product/seller link where possible
10. Source type
11. Any important purchasing note

For example:

> **Thermal Camera — ₹5,000**  
> A basic thermal camera is sufficient for the prototype because the objective is to investigate surface-temperature trends rather than develop a clinical-grade thermography system.  
> **Product:** [Exact model]  
> **Price:** ₹5,000  
> **Link:** [Product URL]

Do not simply write generic estimates such as:

> Thermal camera — ₹5,000

unless a credible source cannot be found. In that case explicitly mark the price as:

**Estimated / Quote Required**

---

# Product Selection Rules

Do not select a product solely because it is the cheapest.

For every major component:

- Prefer established Indian electronics suppliers.
- Prefer manufacturer-authorized distributors where possible.
- Use established marketplaces only when the exact product and seller can be reasonably verified.
- Verify the exact model/specification.
- Check whether the item is currently available.
- Avoid discontinued products.
- Avoid suspiciously cheap listings.
- Avoid listings where the product identity is unclear.
- Do not use an unavailable product's price as the final budget price.
- Do not assume two products with similar names have equivalent specifications.
- Include GST considerations where relevant.
- Include shipping only if it materially affects the procurement cost.
- If a product requires a supporting module for operation, include that module in the budget.

---

# Prototype Scope

The prototype should be capable of demonstrating, as far as realistically possible:

- Bed occupancy detection
- Additional occupant/visitor detection
- Body movement detection
- Body position estimation
- Pressure distribution
- Patient weight estimation
- Respiratory-rate estimation
- Heartbeat-related radar measurements where feasible
- Surface-temperature measurement/trending
- Multimodal sensor fusion
- Measurement-confidence/reliability assessment
- Basic clinical decision-support outputs
- Experimental validation against reference measurements

Do not promise that the prototype will replace:

- ECG
- Blood pressure monitoring
- Pulse oximetry
- Other clinically validated monitoring equipment

The PDF explicitly identifies these as limitations of the proposed platform.

---

# Budget Optimization

The final budget must remain at or below:

**₹1,00,000**

Do not force every category to have an expenditure.

If an item can be:

- Borrowed
- Accessed through a laboratory
- Accessed through a hospital
- Fabricated internally
- Reused from existing equipment

then recommend that approach where appropriate.

For expensive clinical reference equipment, explicitly distinguish:

**Purchase** vs **Institutional Access**

The goal is to maximize the research value of ₹1 lakh.

---

# Required Output

Generate a Markdown file titled:

# Budget

The Markdown document should contain the following sections:

## 1. Budget Objective

Briefly explain that this is a research prototype budget intended to establish technical feasibility, generate experimental data, and enable initial validation.

## 2. Prototype Scope

Summarize what the funded prototype is expected to demonstrate.

## 3. Detailed Item-Wise Budget

Use a table containing:

| Category | Item | Specification / Model | Qty | Unit Cost | Total | Purchase/Access/Fabrication | Why This Cost? | Source |
|---|---|---|---:|---:|---:|---|---|---|

Every significant purchased item must have a source/product link where possible.

## 4. Hardware Budget

Break down:

- Sensors
- Processing
- Microcontrollers
- Electronics
- Power
- Storage

## 5. Prototype Fabrication Budget

Break down:

- Bed modification
- Mounting
- Wiring
- Enclosure
- Mechanical fabrication

## 6. Data & Experimentation Budget

Break down:

- Storage
- Test materials
- Calibration
- Experimental accessories
- Reference equipment access

## 7. Validation Budget

Include:

- Clinical/reference equipment access
- Testing
- Experimental sessions
- Documentation
- Validation-related expenses

## 8. Contingency

Explain what the contingency is intended to cover.

## 9. Category-Wise Summary

Provide:

| Category | Amount |
|---|---:|
| Hardware | ₹... |
| Prototype Fabrication | ₹... |
| Data & Experimentation | ₹... |
| Validation | ₹... |
| Documentation | ₹... |
| Contingency | ₹... |
| **TOTAL** | **₹1,00,000 or less** |

## 10. Purchase vs Institutional Access

Clearly identify expensive items that should preferably be accessed through:

- College laboratories
- Hospitals
- Research collaborators
- Department equipment

rather than purchased.

## 11. Budget Justification

Give a short explanation of why each major category contributes to producing:

> **A measurable research prototype → experimental data → validation → proof of concept**

## 12. Important Procurement Notes

Mention:

- Prices are market prices checked at the time of research.
- Prices and availability can change.
- Final procurement should be performed only after verification.
- Suspicious, unavailable, discontinued, or unverified listings should not be used as the basis of the final funding proposal.

---

# Important Instruction

Do not optimize the budget for appearance.

Optimize it for:

**technical feasibility + experimental usefulness + validation capability + realistic procurement.**

The final budget should make a funding committee believe:

> "This ₹1 lakh will produce a meaningful research prototype and experimental evidence."

rather than:

> "The researchers simply found ₹1 lakh worth of hardware to purchase."