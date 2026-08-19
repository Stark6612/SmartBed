# Smart Bed V2 — Budget Verification & Procurement Validation Prompt

I have an AI-generated budget for the **Smart Bed V2** research prototype.

Independently verify the entire budget before it is used in a research funding proposal.

The project is based in:

**Coimbatore, Tamil Nadu, India**

The maximum funding available is:

**₹1,00,000**

The purpose is to build a **research prototype suitable for experimental evaluation and initial clinical validation**, NOT a premium production-ready medical device.

---

# Verification Objective

The objective is to determine whether every proposed budget item is:

1. Actually required
2. Technically appropriate
3. Correctly specified
4. Available for purchase
5. Offered by a credible seller
6. Priced realistically
7. Suitable for the proposed prototype
8. Worth purchasing rather than borrowing/accessing
9. Appropriate for the ₹1 lakh funding limit

Do not accept the AI-generated budget as correct simply because it contains a product name and price.

---

# Step 1 — Verify Whether the Item Is Actually Needed

For every budget item, compare it against the attached **Smart Bed V2.pdf**.

Classify every item as:

- **Essential**
- **Useful**
- **Optional**
- **Not required**
- **Missing but necessary**

Explain briefly why.

Do not introduce expensive components merely because they are technically possible.

The prototype should demonstrate the core research concept rather than achieve production-grade performance.

---

# Step 2 — Verify the Exact Product

For every purchasable item identify:

- Manufacturer
- Exact model
- Variant
- Required specification
- Interface
- Operating requirements
- Quantity

Do not treat generic product names as sufficient.

For example:

Incorrect:

> mmWave Radar — ₹18,000

Correct:

> Manufacturer + exact radar model + operating frequency + relevant sensing capability + interface + price + seller

Likewise distinguish between different:

- Raspberry Pi 5 RAM variants
- Thermal camera resolutions
- mmWave radar models
- Load-cell capacities
- Pressure sensor matrices
- ADC modules
- Power supplies
- Storage capacities

---

# Step 3 — Verify the Seller

For every major component, identify the seller and classify its reliability.

Use:

### A — Manufacturer / Authorized Distributor

Highest confidence.

### B — Established Specialist Electronics Supplier

Credible supplier with an established presence.

### C — Marketplace / Less-established Seller

Can be used only when the exact seller/product can be reasonably verified.

### D — Unverified / Suspicious

Do not use as the basis for the final budget.

Prefer A and B for important components.

Do not use an unknown website simply because it lists a much lower price.

---

# Step 4 — Verify the Price

For each product:

- Check the current listed price.
- Check whether GST is included.
- Check shipping where relevant.
- Check the exact variant.
- Check whether the displayed price is actually for the product or merely an accessory/component.
- Check whether the price is conditional on bulk purchase.
- Check whether the product is refurbished/used.
- Check whether the product is genuine.
- Compare at least two credible sellers for major/high-value components where possible.

Do NOT automatically select the cheapest listing.

For example:

If:

- Seller A: ₹5,000 — credible and available
- Seller B: ₹4,200 — credible and available
- Seller C: ₹2,000 — unknown seller

Do not use ₹2,000 simply because it is cheapest.

Use a defensible procurement price based on credible sources.

---

# Step 5 — Verify Availability

This is mandatory.

For every product determine whether it is:

- **In stock**
- **Low stock**
- **Out of stock**
- **Discontinued**
- **Pre-order**
- **Unavailable**
- **Availability unclear**

Do not use an out-of-stock or discontinued product's price as the final procurement price.

If the original product is unavailable:

1. Find a suitable currently available alternative.
2. Verify that the alternative meets the required specification.
3. Use the alternative's current price.
4. Explain the substitution.

---

# Step 6 — Detect Suspicious Prices

Identify situations such as:

- Unusually low price
- Fake-looking website
- Unclear seller identity
- No manufacturer information
- No model number
- Product image inconsistent with description
- Price applies only to an accessory
- Price applies only to a different variant
- Refurbished/used product
- Hidden GST
- Hidden shipping charges
- Product listed but unavailable
- Fake discount
- Marketplace seller with poor credibility

Flag these instead of silently accepting the price.

---

# Step 7 — Check Whether the Product Is Appropriate for the Research Prototype

A product can be genuine and available but still be inappropriate.

Check:

- Does it provide the required measurements?
- Does it have sufficient accuracy/resolution?
- Is its interface compatible?
- Can it integrate with ESP32/Raspberry Pi?
- Is its sensing range appropriate?
- Is its form factor appropriate?
- Is it suitable for the intended placement?
- Is it excessive for a research prototype?

Avoid over-specifying hardware.

The prototype should use the **lowest reasonable specification that can demonstrate the research concept**.

---

# Step 8 — Check Supporting Components

Look for hidden requirements.

For example:

If the budget contains:

> Load Cells — ₹3,000

check whether the prototype also requires:

- HX711/ADC
- Mounting hardware
- Wiring
- Connectors
- Power/interface electronics

Likewise check whether the proposed:

- Thermal camera
- mmWave radar
- Pressure matrix
- Raspberry Pi
- ESP32

requires additional components to actually operate.

Add genuinely necessary missing components to the revised budget.

---

# Step 9 — Check Purchase vs Institutional Access

For every expensive item determine whether it should be:

**PURCHASE**

or

**ACCESS THROUGH INSTITUTION / HOSPITAL**

Examples may include:

- ECG
- Pulse oximeter
- Blood pressure monitor
- Reference thermometer
- Other clinical validation equipment

Do not recommend purchasing expensive reference equipment if the same equipment can reasonably be accessed through a hospital, college laboratory, department, or research collaborator.

The purpose of these devices is validation, not becoming part of the final prototype.

---

# Step 10 — Verify the Complete ₹1 Lakh Budget

After verification:

- Remove unnecessary items.
- Replace unsuitable products.
- Replace unavailable products.
- Correct unrealistic prices.
- Add missing essential supporting components.
- Adjust quantities.
- Use realistic fabrication costs.
- Include calibration and experimentation.
- Include validation.
- Include reasonable contingency.

The final total must be:

**≤ ₹1,00,000**

Do not artificially increase prices simply to reach ₹1 lakh.

---

# Required Verification Table

Produce this table:

| Category | Item | Required Specification | Recommended Model | Seller | Listed Price | GST | Shipping | Availability | Reliability | Verified Price | Status |
|---|---|---|---|---|---:|---|---|---|---|---:|---|

Where **Status** must be one of:

- Verified
- Price corrected
- Product replaced
- Unavailable
- Suspicious listing
- Quote required
- Institutional access recommended
- Not required
- Missing component identified

---

# Source Requirements

For every significant purchased item provide:

- Product/model
- Seller
- Current price
- Availability
- Direct product URL
- Date checked

Prefer:

1. Manufacturer
2. Authorized distributor
3. Established Indian electronics supplier
4. Reputable marketplace seller

Do not rely on search-result snippets alone.

The final report must provide direct product links wherever possible.

---

# Price Confidence

Assign:

### High

Current price from manufacturer/authorized distributor or highly credible supplier.

### Medium

Current price from an established supplier but with some uncertainty.

### Low

Marketplace/less-established seller or insufficient independent confirmation.

### Estimate

No reliable current listing found.

### Quote Required

Price depends on custom fabrication, institutional quotation, or supplier quotation.

---

# Final Output

Produce the following sections:

## 1. Verification Summary

State:

- Original budget total
- Verified/revised budget total
- Number of items verified
- Number of prices changed
- Number of products replaced
- Number unavailable
- Number suspicious
- Number recommended for institutional access
- Number of missing components discovered

## 2. Corrected Procurement List

Only include items that should actually be considered for procurement.

## 3. Rejected/Changed Items

For every rejected or changed item explain:

- Original recommendation
- Problem
- Corrected recommendation
- Reason for correction

## 4. Unavailable Products

List products that were listed online but could not actually be purchased.

## 5. Suspicious/Unreliable Listings

Explain why each listing should not be used.

## 6. Institutional Access Recommendations

List equipment that should preferably be borrowed/accessed rather than purchased.

## 7. Missing Components

Identify any components that the original AI budget forgot but that are genuinely required to make the prototype functional.

## 8. Final Verified ₹1,00,000 Budget

Provide:

| Category | Verified Amount |
|---|---:|
| Core Hardware | ₹... |
| Electronics & Power | ₹... |
| Prototype Fabrication | ₹... |
| Calibration & Experimentation | ₹... |
| Data & Storage | ₹... |
| Validation | ₹... |
| Documentation | ₹... |
| Contingency | ₹... |
| **TOTAL** | **₹...** |

## 9. Procurement Links

Provide direct links for all significant purchasable components.

## 10. Final Procurement Recommendation

Give a concise conclusion stating:

- What should actually be purchased
- What should be borrowed/accessed
- What should be fabricated
- What requires quotation
- Which prices are strongly verified
- Which prices remain estimates

---

# Critical Rules

Do not fabricate a product link.

Do not fabricate a price.

Do not claim a product is available without checking availability.

Do not use an unavailable product as the final budget item.

Do not use a suspicious website merely because it has the lowest price.

Do not assume that two similarly named products are equivalent.

Do not use a generic product price when a specific model is required.

Do not artificially spend the full ₹1 lakh.

Do not turn the prototype into a premium medical device simply to consume the budget.

The final objective remains:

> **₹1 lakh → measurable research prototype → experimental data → validated proof of concept.**