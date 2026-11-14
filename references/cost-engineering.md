# Cost Engineering Reference

Full cost taxonomy, Work Breakdown Structure (WBS) decomposition, the formula library, direct/indirect rules, anti-double-counting rules, and wastage/productivity factors.

---

## 1. PURPOSE AND SCOPE

This file defines how the Dynamic Billing Engine decomposes a project into cost components, assigns each component a class, and applies the formulas defined in `SKILL.md`. It exists so that two different runs on the same project produce the same cost skeleton, even when the price research differs.

The engine NEVER invents a category because it "feels relevant." Categories are included when and only when the project actually has that cost. An office renovation has demolition; a software license renewal does not.

---

## 2. THE 17 COST CATEGORIES

Every project cost maps to exactly one primary category. Composite items (e.g., "installed light fixture") are decomposed into material + labor unless the supplier quotes an installed price, in which case the single quoted price is recorded under the supplier's stated basis.

| # | Category | Code | Definition | Typical industries |
|---|----------|------|------------|--------------------|
| 1 | Raw materials | `MAT` | Consumable/direct inputs purchased for the project | All |
| 2 | Equipment | `EQP` | Machinery, tools, vehicles, site equipment | Construction, manufacturing, events |
| 3 | Labor | `LAB` | Human work, skilled or unskilled, day-rate or hourly | All except pure resale |
| 4 | Subcontractors | `SUB` | Third-party firms performing a scoped work package | Construction, IT, events |
| 5 | Permits & fees | `PER` | Government fees, licenses, building permits (PAD/PPnBM etc.) | Construction, events, regulated services |
| 6 | Transportation & logistics | `LOG` | Freight, handling, fuel for delivery, site haulage | All with physical goods |
| 7 | Storage & warehousing | `STO` | Off-site or on-site storage, guarding of stored goods | Construction, manufacturing, events |
| 8 | Packaging | `PKG` | Boxes, pallets, wrapping, crates, labeling | Manufacturing, retail, events |
| 9 | Administrative | `ADM` | Internal admin, document processing, coordination labor allocated to the project | All |
| 10 | Contingency | `CON` | Risk allowance for unknowns — applied as a RATE on an eligible base, never itemized blindly | All |
| 11 | Profit / markup | `PRF` | Seller margin applied at the end when the engine produces a commercial quote | Quotation context only |
| 12 | Overhead | `OVH` | Indirect operating costs (office, utilities, insurance, supervision not in LAB) | Construction, manufacturing |
| 13 | Taxes | `TAX` | Statutory taxes applied to the final amount (PPN where applicable) | All, Indonesia context |
| 14 | Insurance | `INS` | Project insurance, cargo insurance, liability cover | Construction, events, manufacturing |
| 15 | Warranty & guarantee | `WAR` | Reserve or cost of warranty obligations (separate from the warranty terms text) | Manufacturing, IT, equipment |
| 16 | Installation & commissioning | `INS_T` | Physical install/commissioning labor when quoted separately from product | IT, equipment, events |
| 17 | Training & documentation | `TRN` | User training, manuals, as-built docs, handover materials | IT, manufacturing, construction |

Code `INS_T` avoids colliding with `INS` (insurance). Use it consistently in cost tables.

---

## 3. WBS DECOMPOSITION RULES

A Work Breakdown Structure is a tree: project → phase/package → activity → line item. The engine follows these rules:

1. **Decompose until the line is measurable.** A line item must have a quantity, a unit, and a unit price basis. "Interior work" is not a line item; "partition wall 3 m × 2.4 m, gypsum board both sides" is.
2. **One primary category per leaf node.** If a line item genuinely mixes categories (e.g., turnkey supplier includes delivery), either (a) ask the supplier to split it, or (b) record the mixed price under the dominant category and note the mix in the `Source` column.
3. **Group by phase for documents, by category for recaps.** The detailed table groups rows under phase headings; the recap groups by the 17-category taxonomy.
4. **Depth guidance:** 3 levels is normal for small projects (project → phase → item), 4–5 for construction RAB (project → work package → activity → element → item).
5. **Never merge labor and material into one opaque row** unless the source quote is an all-in installed price and cannot be decomposed. If merged, flag `BASIS: installed package`.

### WBS Example — Office Renovation (construction)

```
PROJECT: Office Renovation 150 m²
├── 1. Demolition & Site Prep
│   ├── 1.1 Demolition of existing partitions   → LAB + EQP
│   ├── 1.2 Debris removal & disposal           → LOG + PER (if tipping fee)
│   └── 1.3 Site protection                     → MAT
├── 2. Civil & Structure
│   ├── 2.1 Floor leveling compound             → MAT + LAB
│   └── 2.2 Waterproofing (wet areas)           → MAT + LAB
├── 3. Partitions & Ceilings
│   ├── 3.1 Gypsum board partitions             → MAT + LAB
│   └── 3.2 Suspended ceiling + lighting grid   → MAT + LAB + INS_T
├── 4. MEP (mechanical, electrical, plumbing)
│   ├── 4.1 Electrical rewiring                 → MAT + LAB
│   └── 4.2 Plumbing fixtures                   → MAT + LAB
├── 5. Finishes
│   ├── 5.1 Flooring (tile/vinyl)                → MAT + LAB
│   └── 5.2 Paint                               → MAT + LAB
├── 6. Doors, Windows & Hardware
├── 7. External Works (signage, entrance)
└── 8. Closeout
    ├── 8.1 Testing & commissioning              → LAB
    └── 8.2 Handover documentation               → TRN
```

### WBS Example — Corporate Event (non-construction)

```
EVENT: 500-Person Corporate Event
├── 1. Venue & Logistics
│   ├── 1.1 Venue rental (1 day)                → SUB
│   ├── 1.2 Load-in / load-out                  → LOG
│   └── 1.3 Permits (public gathering, noise)   → PER
├── 2. Production
│   ├── 2.1 Stage, sound, lighting, LED wall    → EQP + SUB
│   └── 2.2 Crew (tech, stagehands)             → LAB
├── 3. Catering
│   ├── 3.1 Food & beverage                     → MAT (caterer price)
│   ├── 3.2 Service staff                       → LAB
│   └── 3.3 Bar & special drinks                → MAT
├── 4. Attendee Experience
│   ├── 4.1 Registration desk materials         → MAT
│   ├── 4.2 Name badges, lanyards               → MAT
│   └── 4.3 Photo documentation                 → SUB
├── 5. Marketing & Comms                        → MAT + SUB
├── 6. Contingency & Risk                        → CON
└── 7. Admin                                     → ADM
```

---

## 4. FORMULA LIBRARY

The canonical formulas live in `SKILL.md`. This section records the extended and edge-case variants. Use the SKILL.md version wherever they differ; SKILL.md wins.

### 4.1 Line and document level

```
LINE SUBTOTAL      = QUANTITY × UNIT PRICE
LINE SUBTOTAL TIN  = LINE SUBTOTAL × (1 + PPN_RATE)        -- only if tax shown per line
CATEGORY TOTAL     = Σ LINE SUBTOTAL (within category)
DIRECT COST        = MAT + LAB + EQP + SUB + LOG + PKG + PER + INS_T  (direct categories present)
INDIRECT COST      = ADM + OVH + STO + INS + WAR + TRN  (as applicable)
PROJECT COST       = DIRECT COST + INDIRECT COST
CONTINGENCY        = CONTINGENCY_RATE × CONTINGENCY_BASE
FINAL ESTIMATE     = PROJECT COST + CONTINGENCY + TAXES
```

### 4.2 Contingency base rules

Contingency is a rate applied to an **eligible base**, not to the grand total blindly. Eligible base defaults:

| Project maturity | Default base | Default rate (guidance, disclose as assumption) |
|---|---|---|
| Concept / feasibility | Full project cost | 10–15% |
| Basic design | Direct + indirect | 7–12% |
| Detailed design | Direct + indirect | 3–7% |
| Tender / fixed-price quote | Direct + indirect, or excluded entirely | 0–5% or none |

Rules:
- Never apply contingency on contingency.
- Never apply contingency on taxes.
- If the user is a contractor producing a fixed bid, contingency may be 0 — state it explicitly.
- Always state: `CONTINGENCY: 10% × (DIRECT + INDIRECT) = IDR X`.

### 4.3 Markup vs margin

```
SELLING PRICE (markup basis)   = COST × (1 + MARKUP)
TARGET MARGIN (margin basis)   = COST / (1 − MARGIN)
GROSS MARGIN                   = (SELLING − COST) / SELLING
MARKUP ON COST                 = (SELLING − COST) / COST
```

Conversion:
- Markup 20% ⇒ margin = 20/120 = 16.67%
- Margin 20% ⇒ markup = 20/80 = 25%

Always label which basis was used in quotations. Never quote "20% profit" without saying markup or margin.

### 4.4 Quantity takeoff

```
AREA      = LENGTH × WIDTH                              (m²)
PERIMETER = 2 × (L + W)                                  (m)
VOLUME    = L × W × H                                    (m³)
WEIGHT    = VOLUME × DENSITY                             (kg or tonne)
COUNT     = UNITS × UNITS_PER_PACKAGE (or manual count)  (pcs)
LABOR HOURS = PRODUCTION RATE⁻¹ × QUANTITY  →  QUANTITY / (units per labor-hour)
```

See `references/financial-formulas.md` for the full conversion library (density tables, currency formatting, productivity formulas, equipment rates, escalation).

---

## 5. DIRECT VS INDIRECT RULES

### Direct costs
Costs that vary directly with the quantity of work or units produced:

- Materials consumed in the work itself
- Labor performing the work itself
- Equipment used solely for the project (idle time rules apply — see §6.3)
- Subcontracted packages
- Permits, freight for project materials, packaging of deliverables
- Installation/commissioning directly tied to delivered items

### Indirect costs
Costs that support the project but do not scale with a measurable quantity:

- Site/project management and supervision (unless priced per unit)
- Head-office administration allocated to the project
- Insurance, bonds, guarantees
- General site overhead: temporary facilities, sanitation, security
- Training, documentation, closeout
- Warranty reserves
- Contingency (handled separately — it is a rate, not an itemized cost)

### Boundary cases

| Situation | Classification | Rule |
|---|---|---|
| Foreman salary | INDIRECT (OVH/LAB-admin) | Unless recharged as direct labor per man-day |
| Crane rented for one pour | DIRECT (EQP) | Allocated to the pour by duration |
| Site office rental | INDIRECT (OVH) | Project-duration allocation |
| Cement for the pour | DIRECT (MAT) | Per BOQ quantity + wastage |
| Delivery truck hired per trip | DIRECT (LOG) | Per trip or per tonne |
| Corporate insurance premium | INDIRECT (INS) | Annual premium × project share |
| Mobilization of subcontractor | DIRECT (SUB) | One-time, but attributable to this project |

---

## 6. ANTI-DOUBLE-COUNTING RULES

Double counting is the most common defect in generated estimates. These rules are mandatory:

### 6.1 Transport
- If the supplier's quoted unit price is **delivered** (DDP/DDU or stated "harga sampai lokasi"), do NOT add a separate `LOG` line for that material.
- If the price is **EXW / harga gudang**, add `LOG` separately. Record the price basis in the Source column: `basis: EXW` or `basis: delivered`.
- One transport line per material flow, not per document line. Aggregate identical freight legs.

### 6.2 Labor vs installed packages
- If a supplier quotes an **installed** price (material + labor + transport), do not add MAT, LAB, or LOG rows for the same scope.
- If the engine decomposes the same scope for transparency, the installed quote becomes reference-only and is NOT summed again.

### 6.3 Equipment idle time
- Equipment rates (see `financial-formulas.md`) already include ownership + operation + maintenance per productive hour.
- Do NOT add a separate maintenance line for the same equipment.
- Idle/standby time is a real cost: if equipment waits 2 of 8 hours, either use the effective utilization-adjusted rate or add an explicit idle-time line — never both.

### 6.4 Contingency and taxes
- Contingency base excludes contingency itself and taxes (see §4.2).
- PPN, if applicable, is computed once at document level on the eligible base. Never per line AND at total.

### 6.5 Overhead allocation
- If labor rates already include a supervision/overhead uplift (common in day-rate quotations), do not add a separate `OVH` line for the same function.
- Check the rate basis before adding `OVH`. Record the basis: `LAB rate includes supervision` or `LAB net + OVH 15%`.

### 6.6 Warranty and retention
- Retention money held from a contractor is a **cash-flow** item, not a cost. It belongs in payment terms, not in cost recaps.
- Warranty reserve (money set aside for future repairs) is a cost only for the party bearing the obligation — typically the contractor, not the client.

### 6.7 Permits
- One permit fee line per permit. Do not estimate "miscellaneous fees" on top of itemized permits without labeling it `PER-other`.

### 6.8 Duplicated documents
- The same item appearing in both a detailed table and a summary table is fine — but the recap must sum only once.
- When merging vendor quotations into a master BOQ, deduplicate identical scope items and record which vendor quote won each line.

---

## 7. WASTAGE AND PRODUCTIVITY FACTORS

### 7.1 Material wastage

Wastage is real consumption beyond the net quantity. It is a multiplier on material quantity, not a separate cost category.

| Material / work type | Typical wastage allowance | Notes |
|---|---|---|
| Concrete / mortar / plaster | 3–5% | Mixer losses, spillage |
| Reinforcing steel (rebar) | 3–5% | Cutting, lap splices, bends |
| Brick / block masonry | 5–8% | Breakage, cutting |
| Tiles / ceramics | 5–10% | Cutting waste, pattern matching |
| Timber / formwork | 5–10% | Cuts, defects rejected |
| Paint | 5–10% | Roller waste, touch-ups |
| Roofing sheets | 5–8% | Cutting, overlaps |
| Cables / pipes (linear) | 3–5% | Cuts, bends, joints |
| Glass | 10–15% | Cutting, breakage |
| Generic packaged goods | 0–2% | Only if repackaging |

Rules:
- Apply wastage to **material quantity only**, never to labor or equipment.
- State the factor explicitly: `Tile qty net 100 m² × 1.08 wastage = 108 m² purchased`.
- Wastage factors are assumptions — label `ASSUMPTION: tile wastage 8%` unless a standard schedule specifies otherwise.
- Never double-apply wastage if the unit price already reflects "per installed m²" pricing.

### 7.2 Labor productivity

Productivity = output per labor-hour. The engine uses it to convert BOQ quantities into man-days.

```
LABOR-HOURS NEEDED = NET QUANTITY / PRODUCTIVITY (units per hour)
MAN-DAYS          = LABOR-HOURS / EFFECTIVE HOURS PER DAY
```

Effective hours per day conventions:

| Context | Effective hours/day | Basis |
|---|---|---|
| Indonesia construction (typical) | 7–8 h | Including breaks, per common practice |
| International construction | 8 h | Standard shift |
| Manufacturing line | Per shift spec | OEE-adjusted |
| Event crew (call time) | Billable hours, not elapsed | Per contract terms |

Productivity benchmarks (illustrative — ALWAYS verify against local AHSP/HSPK or project norms before use):

| Work | Typical productivity (units/labor-hour) | Confidence |
|---|---|---|
| Brick masonry (skilled) | 0.8–1.2 m²/h | MODERATE |
| Gypsum board partition (both sides) | 1.5–2.5 m²/h | MODERATE |
| Painting (roller, 2 coats) | 8–12 m²/h | MODERATE |
| Concrete casting (incl. finishing) | 1.5–3.0 m³/h per crew | LOW-MODERATE |
| Electrical wiring (concealed) | 20–40 m/day per electrician | MODERATE |

Rules:
- Productivity is crew-dependent: a 4-person crew does not produce 4× a 1-person crew's output per hour; it produces roughly 3–3.5× due to coordination.
- For crew-based estimates: `MAN-DAYS = QUANTITY / (CREW SIZE × INDIVIDUAL PRODUCTIVITY × CREW EFFICIENCY)` where crew efficiency ≈ 0.85–0.95.
- Record productivity source: `prod: AHSP-based` / `prod: assumed` / `prod: vendor quote`.

### 7.3 Equipment utilization

```
EFFECTIVE EQUIPMENT COST PER UNIT = (OWNERSHIP + OPERATION + MAINTENANCE) / (ANNUAL HOURS × UTILIZATION)
```

Typical utilization assumptions (disclose as assumptions):

| Equipment | Utilization assumption |
|---|---|
| Tower crane (active project) | 60–75% |
| Mobile crane (per diem hire) | Billed per day — no utilization needed |
| Concrete mixer | 50–70% |
| Excavator | 60–80% |
| Generator (continuous) | 80–95% |

---

## 8. TAXONOMY APPLICATION CHECKLIST

Before finalizing any cost document:

- [ ] Every line item maps to exactly one of the 17 categories
- [ ] No line item lacks a unit and a quantity basis
- [ ] Transport included in supplier price is not re-added as `LOG`
- [ ] Installed prices are not decomposed AND summed
- [ ] Contingency applied once, on the correct eligible base
- [ ] Tax computed once at document level (or explicitly per-line if required)
- [ ] Wastage factors applied to materials only, and disclosed
- [ ] Productivity/equipment assumptions labeled `ASSUMPTION:` or sourced
- [ ] Direct and indirect subtotals reconcile to grand total
- [ ] Every figure has a source class (VERIFIED … UNAVAILABLE) per `SKILL.md`
