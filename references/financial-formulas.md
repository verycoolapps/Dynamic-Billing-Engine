# Financial Formulas

Extended formula library: unit conversions, compound scenarios, NPV-lite/budget variance, labor productivity, equipment rates, escalation/inflation adjustment.

---

## 1. UNIT CONVERSIONS

### 1.1 Length / Area / Volume

| From | To | Factor | From | To | Factor |
|---|---|---|---|---|---|
| mm | m | ÷ 1.000 | cm² | m² | ÷ 10.000 |
| cm | m | ÷ 100 | ft² | m² | × 0,092903 |
| km | m | × 1.000 | ha | m² | × 10.000 |
| ft | m | × 0,3048 | are | m² | × 100 |
| inch | cm | × 2,54 | liter | m³ | ÷ 1.000 |
| — | — | — | ft³ | m³ | × 0,028317 |
| — | — | — | gallon (US) | liter | × 3,78541 |
| — | — | — | barrel (oil) | liter | × 159 |

### 1.2 Weight / Mass

| From | To | Factor |
|---|---|---|
| gram | kg | ÷ 1.000 |
| kg | ton | ÷ 1.000 |
| lb | kg | × 0,453592 |
| oz | g | × 28,3495 |
| ton (short) | kg | × 907,185 |
| tonne (metric) | kg | × 1.000 |

### 1.3 Density-based conversions

```
WEIGHT = VOLUME × DENSITY
VOLUME = WEIGHT ÷ DENSITY
DENSITY = WEIGHT ÷ VOLUME
```

Common densities (kg/m³): water 1.000 · concrete 2.400 · RC 2.500 · steel 7.850 · aluminum 2.700 · brick 1.600–1.800 · soil 1.600–1.800 · sand 1.500–1.700 · timber dry 500–700 · glass 2.500 · ceramic ~2.100 · gypsum board ~800.

**Example:** 10 m³ concrete × 2.400 kg/m³ = 24.000 kg = 24 ton.

### 1.4 Currency

```
IDR = USD × rate    USD = IDR ÷ rate
```

Record the rate used and its source/date (e.g., BI mid-rate). Use mid-market rate for estimates; actual rates vary. For IDR-denominated work, prefer IDR sources.

### 1.5 IDR formatting

```
Whole rupiah:   1.500.000
With decimals:  1.500.000,00
Abbreviation:   Rp 1,5 M / Rp 1,5 Miliar / Rp 1,5 Juta
```

Always use Indonesian format for IDR unless user specifies otherwise. Never use US format ($1,000.00) for IDR.

---

## 2. BASIC FORMULAS (REFERENCE)

```
LINE SUBTOTAL   = QUANTITY × UNIT PRICE
CATEGORY TOTAL  = Σ LINE SUBTOTAL
DIRECT COST     = MAT + LAB + EQP + SUB + LOG + PKG + PER + INS_T
INDIRECT COST   = ADM + OVH + STO + INS + WAR + TRN
PROJECT COST    = DIRECT + INDIRECT
CONTINGENCY     = RATE × ELIGIBLE BASE
FINAL ESTIMATE  = PROJECT COST + CONTINGENCY + TAXES

SELLING (markup) = COST × (1 + MARKUP)
SELLING (margin) = COST / (1 − MARGIN)
GROSS MARGIN     = (SELLING − COST) / SELLING
MARKUP           = (SELLING − COST) / COST

AREA = L × W    PERIMETER = 2(L+W)    VOLUME = L × W × H    WEIGHT = VOLUME × DENSITY

LABOR HOURS  = QUANTITY / PRODUCTIVITY
MAN-DAYS     = LABOR HOURS / EFFECTIVE HOURS PER DAY
CREW OUTPUT  = CREW SIZE × INDIVIDUAL PRODUCTIVITY × CREW EFFICIENCY

EQUIPMENT RATE/HR = (OWNERSHIP + OPERATION + MAINTENANCE) / ANNUAL HOURS
```

---

## 3. COMPOUND SCENARIOS

### 3.1 Multi-period escalation

```
YEAR N COST = BASE COST × (1 + ESCALATION)^N
TOTAL = Σ YEAR N COST
```

Example: IDR 1jt/year base, 5% escalation, 3 years → 1.000.000 + 1.050.000 + 1.102.500 = 3.152.500.

### 3.2 Quantity × price with wastage

```
GROSS QTY = NET QTY × (1 + WASTAGE)
TOTAL     = GROSS QTY × UNIT PRICE
```

Example: 100 m² tile, 8% wastage, Rp 150.000/m² → 108 m² × 150.000 = Rp 16.200.000.

### 3.3 Discount cascading

```
SUBTOTAL → −DISC1 → −DISC2 → TAXABLE → +TAX → TOTAL
```

Example: Rp 10jt, 10% + 5% discounts, 11% PPN → taxable 8.550.000, PPN 940.500, total 9.490.500.

---

## 4. NPV-LITE / BUDGET VARIANCE

### 4.1 Budget variance

```
VARIANCE   = ACTUAL − PLANNED
VARIANCE % = (ACTUAL − PLANNED) / PLANNED × 100
```

Positive = over budget; negative = under budget. Example: planned 50jt, actual 55jt → +5jt (+10%).

### 4.2 Earned value lite

```
PV = budget × planned %    EV = budget × actual %    AC = actual spend
SV = EV − PV (schedule)    CV = EV − AC (cost)
```

Example: budget 100jt, 50% planned, 40% actual, spent 45jt → SV = −10jt (behind), CV = −5jt (over).

### 4.3 Payback & ROI lite

```
PAYBACK = INITIAL INVESTMENT / ANNUAL NET BENEFIT
ROI      = (NET BENEFIT − COST) / COST × 100
```

---

## 5. LABOR PRODUCTIVITY

```
PRODUCTIVITY     = OUTPUT / LABOR-HOURS
LABOR-HOURS      = QUANTITY / PRODUCTIVITY
MAN-DAYS         = LABOR-HOURS / EFFECTIVE HOURS PER DAY
LABOR COST       = MAN-DAYS × DAILY WAGE (if man-days = person-days)
                 = MAN-DAYS × CREW SIZE × DAILY WAGE (if man-days = crew-days)
OVERTIME         = REGULAR HOURS × WAGE × PREMIUM (Indonesia ~1.5× first hr, 2× after — verify PP 35/2021)
```

Clarify whether man-days count persons or crews before multiplying.

---

## 6. EQUIPMENT RATE

```
OWNERSHIP/HR   = (PURCHASE − SALVAGE) / ECONOMIC HOURS + INTEREST/HR
ECONOMIC HOURS = NOMINAL LIFE × UTILIZATION
OPERATION/HR   = FUEL × PRICE + LUBRICANTS + OPERATOR/HR
MAINTENANCE/HR = ANNUAL MAINT. / ANNUAL HOURS  (or OWNERSHIP × 50–100%)
TOTAL RATE/HR  = OWNERSHIP + OPERATION + MAINTENANCE
EQUIP COST     = RATE/HR × HOURS USED
```

Example: excavator IDR 800jt, salvage 100jt, life 10.000h, util 70%, diesel 20L/h @ Rp 7.000:
- Economic hours = 7.000 → depreciation ≈ Rp 100.000/h
- Operation ≈ Rp 158.750/h (fuel + operator)
- Maintenance ≈ 75% × ownership ≈ Rp 83.000/h
- **Total ≈ Rp 340.000–355.000/hour**

Rental comparison: `OWNERSHIP COST = RATE × HOURS` vs `RENTAL = DAILY RATE × DAYS` — include mobilization, insurance, operator.

---

## 7. ESCALATION / INFLATION

```
FUTURE COST = CURRENT × (1 + ESCALATION)^YEARS
PRESENT VALUE = FUTURE / (1 + DISCOUNT)^YEARS
```

Component rates (guidance): materials 3–8%, labor 5–10% (UMP-driven), equipment 3–6%, overhead 3–5%.

Example: IDR 100jt in 3 years at 5% → 115.762.500. PV at 10% discount → 75.131.000.

In estimates: apply per-component escalation, state assumptions (`ASSUMPTION: 5% materials, 7% labor, 18-month duration`).

---

## 8. FULL DOCUMENT FORMULA

Correct order — contingency base excludes taxes:

```
SUBTOTAL    = DIRECT + INDIRECT
CONTINGENCY = SUBTOTAL × RATE
TAXABLE     = SUBTOTAL + CONTINGENCY
TAX         = TAXABLE × TAX RATE
TOTAL       = TAXABLE + TAX
```

Example: direct 80jt + indirect 20jt, contingency 10%, PPN 11% → taxable 110jt, PPN 12,1jt, total 122,1jt.

Selling variant: `SELLING = COST × (1 + MARKUP)`; then tax on selling if applicable.

---

## 9. FORMULA QUICK REFERENCE

| Need | Formula |
|---|---|
| Line total | Qty × Unit price |
| Direct/indirect | Σ category groups |
| Project cost | Direct + indirect |
| Contingency | Rate × eligible base |
| Final | Cost + contingency + tax |
| Selling (markup) | Cost × (1 + markup) |
| Selling (margin) | Cost ÷ (1 − margin) |
| Area / Volume / Weight | L×W / L×W×H / V×density |
| Labor hours | Qty ÷ productivity |
| Man-days | Hours ÷ hrs/day |
| Equip rate/hr | (Own+Op+Maint) ÷ hours |
| Variance | Actual − planned |
| Escalated | Current × (1+esc)^yrs |
| PV | Future ÷ (1+rate)^yrs |
| Payback | Investment ÷ annual benefit |
| ROI | (Benefit − cost) ÷ cost × 100 |

---

## 10. FORMATTING RULES

- **IDR:** `1.500.000,00` (dot thousands, comma decimals); abbreviations `Rp 1,5 M / Miliar / Juta`.
- **USD:** `$1,500,000.00`; abbreviations `$1.5M`.
- **Percentages:** Indonesian `20,5%` vs English `20.5%` — match user language.
- **Quantities:** m²/m³ to 2 decimals; match user's decimal separator.
