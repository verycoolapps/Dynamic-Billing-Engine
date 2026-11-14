# Indonesian Cost References

Indonesian construction and procurement standards: SNI, AHSP, HSPK, regional price schedules, PPN context (2024–2026), citation rules, and the critical disclaimer that schedules vary by region and year.

---

## 1. PURPOSE

This file documents the Indonesian reference framework for cost estimation. It explains what each standard is, how to use it, how to cite it, and — critically — that **none of these references are universal**.

**Golden rule:** A price or coefficient from one province's schedule does not apply to another province. A 2023 schedule does not reflect 2026 prices. Always record: authority, region, year, document name.

---

## 2. SNI — STANDAR NASIONAL INDONESIA

### 2.1 What it is

National standards published by **BSN (Badan Standardisasi Nasional)**. SNI codes specify materials, methods, and performance — they do NOT set prices.

### 2.2 Relevant SNI families for construction/cost work

| Code family | Domain | Examples |
|---|---|---|
| SNI 15-xxxx | Cement, lime, gypsum | SNI 15-2049 (cement Portland), SNI 15-3014 (lime) |
| SNI 03-xxxx | Structural/concrete/earthquake | SNI 2847 (concrete), SNI 03-1726 (seismic), SNI 03-2849 (RC execution) |
| SNI 03-3800 | Electrical installations | LV installations, earthing |
| SNI 03-6574 | Plumbing installations | Water supply, drainage |
| SNI 03-6575 | HVAC / ventilation | AC, smoke control |
| SNI 03-2441 | Ceramic tiles | Floor/wall tile specs |
| SNI 03-2396/2397 | Doors, windows | Frame and leaf specs |
| SNI 06-xxxx | Sanitary fixtures | WC, basin, tap specs |
| SNI 07-xxxx | Paints/coatings | Interior/exterior paint |
| SNI 08-xxxx | Aluminum frames | Window/door frames |
| SNI 19-xxxx | Safety/labels | Warning signs, labels |

### 2.3 How to use SNI in cost work

- **In specifications:** cite the SNI number that defines the required material/method.
- **In supplier matching:** search for products certified to that SNI.
- **In quality assessment:** SNI compliance is a verification signal.
- **In price research:** SNI-grade materials cost more than generic — note the premium.

### 2.4 SNI citation rules

```
Correct:  "Semen Portland komposit SNI 15-2049:2019"
Correct:  "Beton K-225 sesuai SNI 2847:2019"
Correct:  "Keramik lantai 40×40 cm SNI 03-2441"
WRONG:    "SNI cement" (vague)
WRONG:    "SNI 15-2049" without context (what does it cover?)
WRONG:    Fabricated SNI numbers — NEVER invent codes
```

If unsure of exact SNI number: write `SNI (refer to current BSN catalogue)` or describe the spec without a code.

---

## 3. AHSP — ANALISIS HARGA SATUAN PEKERJAAN

### 3.1 What it is

The standard Indonesian **unit-rate analysis** for construction work. AHSP decomposes each work item into:

```
HARGA SATUAN = (Material coefficient × material price)
              + (Labor coefficient × labor wage)
              + (Equipment coefficient × equipment rate)
```

### 3.2 How AHSP works

- **Coefficients** are fixed ratios per unit of work (e.g., 0.05 m³ mortar per m² of masonry).
- **Prices** are local — you must substitute current material/labor/equipment prices.
- AHSP is published by various entities: PUPR, BUMN contractors, provincial governments, industry associations.

### 3.3 AHSP vs HSPK

| | AHSP | HSPK |
|---|---|---|
| **Output** | Coefficients (material + labor + equipment per unit) | Lump-sum rate per activity |
| **Use** | Detailed estimating, sensitivity analysis | Quick budgeting, government schemes |
| **Flexibility** | High — adjust any coefficient | Low — take the rate as given |
| **Availability** | Widely referenced, various editions | Published periodically by PUPR/provinces |

### 3.4 Using AHSP in the engine

When AHSP coefficients are available (from a cited source):

```
Example: Masonry work 1 m²
- Material: 0.0125 m³ mortar + 0.25 m² plaster = X kg cement, Y kg sand...
- Labor: 1.5 OH per m² (or per AHSP coefficient)
- Equipment: mixer 0.02 hour per m²
```

When AHSP is not available:
- Derive equivalent coefficients from BOQ norms or vendor quotes.
- Label the basis: `prod: assumed` or `coef: derived from [source]`.
- Never present assumed coefficients as AHSP-verified.

### 3.5 AHSP citation

```
Correct:  "Koefisien material AHSP Dinas PUPR Prov. Jawa Barat 2024"
Correct:  "Analisa harga satuan berdasarkan AHSP referensi [publisher] edisi [year]"
WRONG:    "AHSP price" (AHSP gives coefficients, not prices)
WRONG:    Fabricated AHSP edition numbers
```

---

## 4. HSPK — HARGA SATUAN POKOK KEGIATAN

### 4.1 What it is

Lump-sum unit rates for common construction activities, primarily used in **government-funded projects** (PUPR, DAK, APBN/APBD schemes).

Where AHSP decomposes into coefficients, HSPK gives one package rate per activity.

### 4.2 How to use HSPK

- **Applicability:** best for government scheme projects where HSPK items match.
- **Coverage:** varies by province and year — not all activities covered.
- **Authority:** published by KemenPUPR and provincial Dinas PUPR/Bina Marga.

### 4.3 HSPK citation

```
Correct:  "HSPK Pekerjaan Pondasi Dingin — Dinas PUPR Prov. X, 2024"
Correct:  "Harga satuan pokok kegiatan sesuai jadwal [province] tahun [year]"
WRONG:    "HSPK price" without specifying which HSPK
WRONG:    Assuming national HSPK applies everywhere
```

---

## 5. REGIONAL PRICE SCHEDULES

### 5.1 What they are

Provinces, regencies, and state-owned contractors publish annual price schedules for materials, labor, and equipment. Names vary:

| Publisher | Typical document name |
|---|---|
| Provincial PUPR / Bina Marga | "Jadwal Harga Pekerjaan", "Analisa Harga Satuan", "HSPK" |
| Municipal Dinas (Jakarta, Bandung, etc.) | "Harga Satuan Material", "Upah Minimum", "Standar Biaya" |
| BUMN contractors | Internal reference schedules (less public) |
| KemenPUPR | National technical guidelines, reference analyses |

### 5.2 Critical caveat — NOT universal

**Regional schedules are NOT universal.** This is the most important rule:

- A schedule for **Jawa Barat** does not apply to **Sulawesi**.
- A schedule for **2023** does not reflect **2026** prices.
- A schedule for **government projects** may differ from **private market** prices.
- A schedule for **PUPR work** may differ from **building construction**.

### 5.3 When to use regional schedules

| Situation | Use? | Confidence |
|---|---|---|
| Government project in that province | Yes — cite exact schedule | HIGH (if current) |
| Private project in same province | Yes — as INDICATIVE reference | MODERATE |
| Project in different province | No — find local schedule or use market prices | — |
| Historical analysis | Yes — as INDICATIVE with date noted | LOW-MODERATE |
| Quick benchmark | Yes — as ESTIMATED range | LOW |

### 5.4 Citation format

```
Correct:  "Sumber: Jadwal Harga Dinas PUPR Prov. Jawa Barat Tahun 2024"
Correct:  "Referensi: Analisa Harga Satuan Pemkot Bandung 2023 (perlu verifikasi harga terbaru)"
Correct:  "Indikasi: Standar Biaya Material Pemprov. DKI Jakarta 2024"
WRONG:    "Harga semen Rp 60.000" without source
WRONG:    "Jadwal harga provinsi" without naming which province/year
```

Always include: **authority + region + year + document name** (if known).

---

## 6. PPN CONTEXT — 2024–2026

### 6.1 Current rate structure

Indonesia's PPN (Pajak Pertambahan Nilai = Value Added Tax) has been transitioning:

| Period | Rate | Notes |
|---|---|---|
| Until 31 Mar 2022 | 10% | Original rate |
| 1 Apr 2022 – 31 Dec 2024 | 11% | First increase per UU HPP |
| 1 Jan 2025 onwards | 12% for luxury goods; 11% for most goods/services | Dual-rate system |

**As of 2026:** Most goods and services remain at **11%**. The 12% rate applies to specific luxury goods categories per PMK regulations. Some services may have different treatment.

### 6.2 What the engine does with PPN

- **Records the applicable rate** as an assumption: `ASSUMPTION: PPN 11% (general rate) per regulation in effect [date]`
- **Shows PPN as a separate line** when applicable: `PPN (11%) = taxable base × 0.11`
- **Never claims to be a tax document** — see `tax-awareness.md`
- **Never calculates PPh 23 withholding** — flags it as a note only

### 6.3 PPN on different cost types

| Cost type | PPN treatment |
|---|---|
| Materials (goods) | PPN applies at standard rate |
| Construction services | PPN applies (11%) |
| Equipment rental | PPN applies |
| Professional services | PPN applies; PPh 23 may also apply |
| Exempt goods (basic necessities) | May be exempt or different rate |
| Export services | May be exempt or zero-rated |

### 6.4 PPN citation in documents

```
"PPN (11%)" — for general goods/services
"PPN (12%)" — for luxury goods per PMK-131/2024 category
"PPN tidak berlaku" — if exempt (verify category)
"PPN sesuai peraturan berlaku" — when uncertain
```

Always state the rate used and note: `PPN rate per regulation in effect at time of estimate; verify with tax consultant for current rate`.

---

## 7. LABOR WAGES — UMP/UMK

### 7.1 What they are

**UMP (Upah Minimum Provinsi)** and **UMK (Upah Minimum Kabupaten/Kota)** are provincial/regency minimum wages, revised annually by provincial government regulation (Peraturan Gubernur).

### 7.2 Usage in construction

- Construction labor is typically quoted per **OH (orang hari = man-day)** or per skill grade.
- AHSP labor coefficients translate BOQ quantities into required man-days.
- Multiply man-days by applicable daily wage.

### 7.3 Wage hierarchy (typical construction)

| Grade | Typical role | Wage relation to UMP |
|---|---|---|
| Mandor (foreman) | Crew supervisor | 1.5–2× UMP |
| Tukang (skilled worker) | Mason, carpenter, electrician | 1.2–1.5× UMP |
| Kuli (unskilled) | Helper, carrier | 1.0–1.2× UMP |
| Kepala tukang (head craftsman) | Senior specialist | 1.5–2× UMP |

These ratios are **indicative** — actual wages vary by region, project, and negotiation.

### 7.4 Citation

```
"Upah buruh berdasarkan UMK [region] [year]"
"Upah mandor Rp X/hari (referensi UMK [region])"
"Wage rate per AHSP [publisher] [year]"
```

---

## 8. MATERIAL PRICE SOURCES (INDONESIA-SPECIFIC)

Priority order for Indonesian material prices:

| Priority | Source | Class | Examples |
|---|---|---|---|
| 1 | Manufacturer price list | VERIFIED | Semen Indonesia, Astra, dealer network |
| 2 | Authorized distributor | VERIFIED | Official dealer quote, brand store |
| 3 | Government schedule material annex | INDICATIVE | Provincial PUPR schedule material prices |
| 4 | B2B marketplace | PARTIALLY VERIFIED | Verified seller on trade platform |
| 5 | Retail marketplace | PARTIALLY VERIFIED | E-commerce building materials |
| 6 | Toko bangunan (building store) | PARTIALLY VERIFIED | Physical store with online listing |
| 7 | Industry benchmark | INDICATIVE | Published average prices |
| 8 | Estimated | ESTIMATED | Cost build-up from components |

### 8.1 Major Indonesian material categories

| Category | Key manufacturers/suppliers (verify current) |
|---|---|
| Cement | Semen Indonesia (Semen Gresik, Semen Padang, Semen Kupang, Semen Tonasa), Astra International, Semen Baturaja |
| Steel/rebar | Krakatau Steel, Gunung Raja, Mitra Keluarga, workshops |
| Concrete | Ready-mix plants (Schwing, Kian Hoong, local) |
| Timber | Sinar Mas, RGE, local timber suppliers |
| Ceramic tiles | Muli, Roma, Jasaka, local producers |
| Paint | Avian, Dulux (AkzoNobel), Jotun, Catylac |
| Sanitary | American Standard, Toto, local brands |
| Electrical | Schneider, Panasonic, Chint, Schneider Electric distributors |
| Aluminum | Star Alu, locally extruded profiles |
| Glass | Asahimas, K Glass, local processors |

**Note:** This list is illustrative. Verify current manufacturers, distributors, and market presence before citing.

---

## 9. CITATION FORMAT SUMMARY

Every Indonesian cost reference must include:

```
[Authority/Publisher] — [Document Name] — [Region/Scope] — [Year]
```

Examples:

```
Kementerian PUPR — Jadwal Harga Pekerjaan — Nasional — 2024
Dinas PUPR Provinsi Jawa Barat — Analisa Harga Satuan — Jawa Barat — 2023
Dinas Perumahan dan Kawasan Permukiman DKI Jakarta — Standar Biaya Material — DKI Jakarta — 2024
BSN — SNI 15-2049:2019 — Nasional — 2019
```

When citing in a cost table:

```
Unit price source: "Jadwal Harga Dinas PUPR Prov. Jabar 2024, item 3.2.1"
Coefficient source: "AHSP Dinas PUPR Prov. Jabar 2024, analisa 3.2.1"
Wage source: "UMK Kabupaten [X] 2024"
```

---

## 10. DISCREPANCY HANDLING

When Indonesian references conflict:

| Conflict | Resolution |
|---|---|
| Two provincial schedules differ | Use the one matching project location; note the other exists |
| AHSP coefficient vs vendor quote differ | Use vendor quote for price; AHSP for coefficient validation |
| HSPK rate vs market price differ | HSPK for government compliance; market for private estimate |
| Old schedule vs current market | Prefer current market; mark schedule as historical |
| National vs provincial standard | Provincial for local work; national for reference |

Always document which source was chosen and why.

---

## 11. DISCLAIMER

**This reference describes Indonesian cost-estimation standards as of 2024–2026. Regulations, schedules, and prices change frequently. Always verify current sources before use in actual projects. Regional schedules are NOT universal — they apply only to their specified region and year. This engine provides estimates for planning purposes; for actual procurement, tender, or tax purposes, consult qualified local professionals (quantity surveyor, tax consultant, procurement specialist).**
