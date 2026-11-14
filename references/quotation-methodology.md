# Quotation Methodology

How to structure quotations, apply markup vs. margin correctly, compare vendor quotations, score vendors, and handle price validity.

---

## 1. WHAT A QUOTATION IS

A **quotation (penawaran / quotation / quote)** is a seller's formal offer of price for defined goods or services. Unlike an invoice (a demand for payment after delivery), a quotation precedes the transaction — it invites acceptance.

Legal character:
- A quotation becomes a **binding offer** when issued with clear terms.
- Acceptance creates a contract; delivery/payment terms in the quote govern.
- Validity period limits how long the offer stands.

The engine produces quotations in two directions:

| Direction | Use case |
|---|---|
| **Sales quotation** | User is selling → produce a quote to send to their customer |
| **Procurement analysis** | User is buying → analyze vendor quotes received, compare, recommend |

This file covers both. `templates/quotation-template.md` is the sales-quotation skeleton.

---

## 2. QUOTATION STRUCTURE

Required sections, in order:

```
1. HEADER
   - Quotation number + date + version
   - Validity period (e.g., "Harga berlaku 14 hari")
   - Issuer (seller) info — placeholders for unknown data
   - Buyer info
   - Reference: RFQ number, project name, contact person

2. SCOPE OF WORK / SCOPE OF SUPPLY
   - What is included, described precisely
   - Linked to BOQ/RAB when applicable

3. ITEMIZED PRICING TABLE
   No | Description | Spec | Unit | Qty | Unit Price | Subtotal | Notes

4. OPTIONAL / ALTERNATE ITEMS (if any)
   - Clearly separated, labeled "opsi" / "alternate"

5. COMMERCIAL TERMS
   - Delivery terms (EXW / DDP / FOB etc.)
   - Delivery timeline / lead time
   - Payment terms (see invoice-standards.md §6)
   - Warranty terms

6. EXCLUSIONS
   - What is NOT included — as important as scope

7. VALIDITY & CONDITIONS
   - Price validity period
   - Assumptions (currency, tax, freight)
   - Governing terms

8. ACCEPTANCE BLOCK
   - Signature lines for seller and buyer
   - "Accepted by / Disetujui oleh"

9. ATTACHMENTS
   - Spec sheets, drawings, BOQ reference, catalog pages
```

---

## 3. SCOPE, EXCLUSIONS, VALIDITY, WARRANTY, PAYMENT — DETAILS

### 3.1 Scope wording

Scope must be unambiguous enough that two people reading it price the same thing:

- BAD: "Supply and install office furniture."
- GOOD: "Supply and install 12 workstations per attached BOQ rev A: desks 140×70 cm, laminate top, steel legs; chairs with lumbar support; assembly included; delivery to 10th floor, no crane."

Rules:
- Reference the controlling document (BOQ rev, drawing number, spec section).
- Quantities in the quote must match the BOQ unless the quote proposes alternates.
- If the quote deviates from spec, flag it explicitly — spec mismatch is a comparison risk (see §5).

### 3.2 Exclusions

Always list exclusions. Common ones:

```
- Pengiriman di luar area Jabodetabek
- Pemasangan / instalasi (kecuali dinyatakan termasuk)
- Biaya crane / alat berat untuk lantai tinggi
- Izin gangguan / HO/relining gedung
- Perubahan scope setelah PO diterbitkan
- Spare parts di luar masa warranty
- Training operator (kecuali paket termasuk)
```

An exclusion list protects both sides. A quote without exclusions is incomplete — flag it during vendor analysis.

### 3.3 Validity

```
Harga penawaran ini berlaku selama 14 (empat belas) hari kalender
terhitung sejak tanggal penawaran.
```

- Standard validity: 14–30 days for goods; 30–90 days for construction/tender.
- After expiry, prices must be re-confirmed — material prices move.
- State what happens on expiry: `setelah masa berlaku, harga dapat berubah`.

### 3.4 Warranty

```
Garansi: 12 bulan untuk material, 3 bulan untuk instalasi
Warranty: 12 months materials, 3 months workmanship
```

- Distinguish **material warranty** (manufacturer defect) vs **workmanship warranty** (installer defect).
- State remedy: repair / replace / refund.
- State claim process briefly.
- Warranty terms affect vendor scoring (§5) — longer, clearer warranty = higher score.

### 3.5 Payment terms

Standard vocabulary in `invoice-standards.md` §6. For quotations, additionally state:

- Retention (if construction): `retensi 5% selama 90 hari masa defect liability`
- Advance payment: `uang muka 20%, termin 60%, pelunasan 20%`
- Late payment penalty if any.

---

## 4. MARKUP VS MARGIN — THE MATH

This is the most-misunderstood calculation in quoting. Get it exactly right.

### 4.1 Definitions

```
COST          = what you pay (supplier price + your direct costs)
MARKUP        = profit as % OF COST
MARGIN        = profit as % OF SELLING PRICE
```

### 4.2 Formulas

```
SELLING = COST × (1 + MARKUP)
SELLING = COST / (1 − MARGIN)
```

### 4.3 Worked examples

Cost = IDR 10.000.000

| Basis | Rate | Calculation | Selling | Profit | Check |
|---|---|---|---|---|---|
| Markup | 20% | 10jt × 1.20 | IDR 12.000.000 | IDR 2.000.000 | margin = 2/12 = 16,67% |
| Margin | 20% | 10jt ÷ 0.80 | IDR 12.500.000 | IDR 2.500.000 | markup = 2,5/10 = 25% |
| Markup | 30% | 10jt × 1.30 | IDR 13.000.000 | IDR 3.000.000 | margin = 3/13 = 23,08% |
| Margin | 30% | 10jt ÷ 0.70 | IDR 14.285.714 | IDR 4.285.714 | markup = 4,29/10 = 42,9% |

**The gap widens as the rate rises.** A "30% margin" quote is ~42.9% markup — meaningfully more expensive than a "30% markup" quote. Always state the basis.

### 4.4 In quotes

```
Harga jual = Harga pokok × (1 + markup)
Markup yang digunakan: 20% atas harga pokok
(Markup basis: cost-plus, NOT margin)
```

When the user asks "berapa margin yang saya dapat?" convert correctly:
`MARGIN = (SELLING − COST) / SELLING`, never `(SELLING − COST) / COST`.

### 4.5 When to use which

| Situation | Recommended basis |
|---|---|
| Cost-plus quoting (materials resale) | Markup on cost |
| Competitive tender (target margin known) | Margin on selling |
| Service work with fixed price | Margin (protects against cost overrun) |
| Government/regulated pricing | Whatever the regulation specifies |

---

## 5. VENDOR COMPARISON AND SCORING

### 5.1 Comparison dimensions

Never compare on price alone. Score each vendor on:

| Dimension | Weight (suggested) | What to measure |
|---|---|---|
| Price competitiveness | 25% | vs median of comparable quotes |
| Spec match | 25% | Does the quote meet the BOQ/spec exactly? |
| Delivery / lead time | 15% | Can they deliver in the project window? |
| MOQ / order flexibility | 10% | Minimum order vs needed quantity |
| Warranty & terms | 10% | Length, clarity, remedy |
| Credibility / trust grade | 10% | A–E per supplier-verification.md |
| Payment terms | 5% | Advance %, retention, credit period |

Weights are adjustable per project — state them in the report.

### 5.2 Scoring rubric (0–5 per dimension)

| Score | Meaning |
|---|---|
| 5 | Excellent — exceeds requirement |
| 4 | Good — meets requirement fully |
| 3 | Acceptable — meets with minor gaps |
| 2 | Weak — partial compliance |
| 1 | Poor — significant gaps |
| 0 | Non-compliant / absent |

Weighted score = Σ (dimension score × weight). Rank vendors; recommend the top scorer **unless** a critical dimension (spec match, trust) scores ≤ 2 — then flag the risk even if total score is high.

### 5.3 Spec mismatch handling

Vendor quotes often differ subtly from spec. Classify each deviation:

| Deviation type | Example | Handling |
|---|---|---|
| Equivalent substitute | Brand A vs Brand B, same spec | Acceptable if certified equivalent — note it |
| Inferior substitute | Thinner material, lower grade | Reject or price-adjust |
| Superior substitute | Better spec at higher price | Acceptable — note upgrade |
| Missing scope | Installation not included | Add cost or reject |
| Different unit basis | Price per box vs per piece | Normalize before comparing |
| Currency difference | USD vs IDR quote | Convert at stated rate, record rate source |

For each deviation, adjust the comparison: either normalize the price (add missing scope cost) or exclude the vendor. Never compare a "supply-only" quote against a "supply+install" quote as if equal.

### 5.4 Price validity handling

```
Quote received → check validity date
├── Still valid → use as-is
├── Expired → mark STALE, request re-quote or re-validate
└── Near expiry (< 7 days) → flag, plan re-confirmation
```

For historical quotes used in benchmarks: record access date; treat prices older than 90 days as `INDICATIVE` unless re-verified.

### 5.5 Award recommendation logic

```
1. Filter: spec match ≥ acceptable AND trust grade ≥ C AND price within reasonable range
2. Score remaining vendors on weighted dimensions
3. Rank by weighted score
4. If top two within 5% → prefer higher spec match / better terms
5. If price outlier (e.g., 40% below median) → investigate: too good = risk
6. Recommend ONE primary + ONE alternate (in case primary fails)
7. State reasoning explicitly — never just "vendor X is cheapest"
```

---

## 6. QUOTATION ANALYSIS WORKFLOW

When the user provides vendor quotations to analyze:

1. **Extract** each quote's line items into a normalized table (same columns as BOQ).
2. **Classify** each quote's price basis: supply-only / supply+install / all-in.
3. **Normalize** units, currency, tax basis, delivery terms.
4. **Adjust** for spec deviations per §5.3.
5. **Compare** per §5.1–5.5.
6. **Report** using `templates/supplier-comparison.md` structure.
7. **Audit** — recheck totals and math before presenting.

When the user asks to **create** a quotation:

1. Take the scope/BOQ.
2. Apply cost build-up: `COST → + markup/margin → SELLING`.
3. Fill `templates/quotation-template.md`.
4. Verify all placeholders are either filled or `________`.
5. State assumptions and validity.
