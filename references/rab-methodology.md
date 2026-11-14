# RAB Methodology — Rencana Anggaran Biaya

Indonesian construction cost-estimation methodology: full RAB structure, measurement formulas, unit conversions, Indonesian standards (SNI, AHSP, HSPK, regional schedules), and quantity takeoff from drawings and specifications.

---

## 1. WHAT A RAB IS

**RAB (Rencana Anggaran Biaya)** is the Indonesian standard construction cost plan. It answers: "How much will this building/structure cost, broken down to the last sack of cement?"

A RAB is produced by a **quantity surveyor (Juru Ukur / QS)** and reviewed by the **owner (Pemilik), consultant (Konsultan), and contractor (Pemborong/kontraktor)**. In procurement it is often called the BOQ (Bill of Quantities) priced out.

Two related but distinct documents:

| Document | Purpose | Price basis |
|---|---|---|
| **BOQ (Bill of Quantities)** | Lists measured quantities only — no prices | Quantities only |
| **RAB (Rencana Anggaran Biaya)** | BOQ + unit prices + cost totals | Priced estimate |

The engine produces RAB directly when prices are researched; produces BOQ when only quantities are known. Never label a priced RAB "BOQ" and never label an unpriced BOQ "RAB".

---

## 2. FULL RAB STRUCTURE

A complete RAB has six sections, lettered A–F. Keep this order in every generated document.

### A. Project Information (Informasi Proyek)

```
PROJECT NAME        : ______________________
PROJECT LOCATION    : ______________________
CLIENT / OWNER      : ______________________
CONTRACTOR / PREPARER: ______________________
DATE OF PREPARATION : ______________________
CURRENCY            : IDR / USD / other ______
EXCHANGE RATE       : (if applicable) ________
VALIDITY            : ________ days from issue
DOCUMENT ID         : RAB-____-____
VERSION             : 1.0
```

### B. Work Breakdown (Rincian Pekerjaan)

Hierarchical list of work packages following the WBS rules in `references/cost-engineering.md`. Typical construction phases:

```
1. Mobilisasi & Personil (Mobilization & Personnel)
2. Pekerjaan Persiapan (Site Preparation)
3. Pekerjaan Tanah (Earthworks)
4. Pekerjaan Pondasi (Foundations)
5. Pekerjaan Struktur (Structure)
6. Pekerjaan Arsitektur (Architectural works)
7. Pekerjaan MEP (Mechanical, Electrical, Plumbing)
8. Pekerjaan Finish (Finishes)
9. Pekerjaan Eksterior (External works)
10. Testing, Commissioning & Handover (Serah Terima)
```

Phases are project-specific — a renovation skips earthworks/foundations; a tenant fit-out starts at demolition/finishes.

### C. Detailed Cost Table (Rincian Biaya)

The heart of the RAB. Columns:

| No | Uraian Pekerjaan / Description | Spesifikasi / Spec | Satuan / Unit | Volume / Qty | Harga Satuan / Unit Price | Jumlah / Subtotal | Sumber / Source |
|---|---|---|---|---|---|---|---|
| 1 | Pekerjaan pasangan bata | Bata merah 1:2, campuran 1:4 | m² | 45,00 | Rp 185.000 | Rp 8.325.000 | INDICATIVE — AHSP ref |

Rules for this table:
- Group rows under phase headings; number continuously or restart per phase (state which).
- `Uraian` must be specific enough to price: material + workmanship + key dimensions.
- `Spesifikasi` carries grade/standard references: `SNI 15-2049` for cement, `t thickness 10 cm`, etc.
- `Volume` is the **measured quantity with wastage already applied** if the unit is a purchase unit (sack, m² tile); or net quantity if the unit price is "per installed unit." State the basis once in section E.
- `Harga Satuan` always carries a verification class: append `— VERIFIED`, `— INDICATIVE`, `— ESTIMATED` etc., or use a separate legend.
- `Sumber` cites: AHSP edition, HSPK, regional schedule name + year, live URL, or `ESTIMATED — assumption basis`.

### D. Recapitulation (Rekapitulasi)

```
A. BIAYA LANGSUNG (Direct Cost)          Rp ________
   A.1 Material                          Rp ________
   A.2 Upah / Tenaga Kerja               Rp ________
   A.3 Peralatan / Equipment             Rp ________
   A.4 Subkontrak / Lain-lain            Rp ________
B. BIAYA TIDAK LANGSUNG (Indirect Cost)   Rp ________
   B.1 Biaya Umum (Overhead)             Rp ________
   B.2 Administrasi                      Rp ________
   B.3 Kontingensi                       Rp ________
C. PPN (if applicable)                    Rp ________
D. JUMLAH TOTAL (Grand Total)            Rp ________
```

For client-side budgets, markup may appear as `E. KEUNTUNGAN / PROFIT` on contractor-prepared estimates — state whose perspective the document represents.

### E. Technical Assumptions (Asumsi Teknis)

```
ASSUMPTION: drawing scale verified at 1:100
ASSUMPTION: soil bearing capacity 1.5 kg/cm² (no soil test)
ASSUMPTION: wastage factors per references/cost-engineering.md §7.1
ASSUMPTION: labor productivity per AHSP 2024 / assumed crew norms
ASSUMPTION: prices valid 30 days from date of RAB
ASSUMPTION: work executed during dry season
```

### F. Exclusions (Pengecualian)

```
- Pekerjaan di luar gambar arsitektur yang direvisi
- Perizinan lingkungan / AMDAL
- Relokasi utilitas di luar batas tapak
- Pemeliharaan pasca-serah terima (di luar masa warranty)
```

Exclusions prevent disputes. When in doubt, exclude and note it — an unstated exclusion discovered later is a claim.

---

## 3. MEASUREMENT FORMULAS

| Quantity type | Formula | Unit |
|---|---|---|
| Area (rectangular) | L × W | m² |
| Area (triangular) | ½ × base × height | m² |
| Area (circle) | π × r² | m² |
| Area (trapezoid) | ½ × (a + b) × h | m² |
| Perimeter | Σ sides (or 2(L+W)) | m |
| Volume (rectangular) | L × W × H | m³ |
| Volume (cylinder) | π × r² × H | m³ |
| Volume (cone/pyramid) | ⅓ × base area × height | m³ |
| Weight | Volume × density | kg / tonne |
| Labor hours | Quantity ÷ productivity | man-hour |
| Man-days | Man-hours ÷ effective hours/day | OH |
| Equipment hours | Quantity ÷ equipment productivity | jam alat |
| Linear runs | Σ segment lengths − deductions + additions | m |
| Reinforcement weight | Bar length × unit weight (kg/m) | kg |

### Common quantity pitfalls

- **Deductions:** deduct openings > 0.5 m² from wall/floor areas unless the standard says otherwise; state the rule used.
- **Additions:** add waste laps for rebar (typically +10% lap allowance beyond cutting waste), formwork overlaps.
- **Net vs gross:** always state which. RAB lines are usually net-of-deductions with wastage as a separate multiplier.
- **Rounding:** quantities to 2 decimals (m², m³), currency to whole rupiah (or 2 decimals for invoices).
- **Scale:** verify drawing scale; state it in assumptions. A misread scale is the #1 cause of wrong quantities.

---

## 4. UNIT CONVERSION TABLE

| From | To | Factor | Example |
|---|---|---|---|
| m³ | liter | × 1.000 | 0,5 m³ = 500 liter |
| m³ | kg (water) | × 1.000 | density-dependent — use table below |
| kg | ton | ÷ 1.000 | 2.500 kg = 2,5 ton |
| cm | m | ÷ 100 | 30 cm = 0,30 m |
| mm | m | ÷ 1.000 | 12 mm = 0,012 m |
| ha | m² | × 10.000 | 1 ha = 10.000 m² |
| ft² | m² | × 0,092903 | 1.000 ft² ≈ 92,9 m² |
| lb | kg | × 0,453592 | 100 lb ≈ 45,36 kg |
| gallon (US) | liter | × 3,78541 | 55 gal ≈ 208 liter |
| pack (material) | base unit | per product spec | e.g., 1 dus = 12 pcs |

### Material densities (kg/m³) — reference, verify per product

| Material | Density kg/m³ | Material | Density kg/m³ |
|---|---|---|---|
| Water | 1.000 | Steel (carbon) | 7.850 |
| Concrete (normal) | 2.400 | Aluminum | 2.700 |
| Reinforced concrete | 2.500 | Timber (dry, mixed) | 500–700 |
| Brick masonry | 1.600–1.800 | Sand (dry) | 1.500–1.700 |
| Soil (average) | 1.600–1.800 | Gravel | 1.500–1.800 |
| Gypsum board | ~800 (board) | Ceramic tile | ~2.000–2.200 |
| Glass | 2.500 | Plastic (PE/PP avg) | 900–960 |

Density converts volume to weight for freight costing and material ordering. When the product datasheet gives kg/pcs or kg/m directly, prefer that over density math.

---

## 5. INDONESIAN STANDARDS AND REFERENCES

### 5.1 SNI — Standar Nasional Indonesia

National standards published by BSN (Badan Standardisasi Nasional). Relevant families:

| Code family | Domain |
|---|---|
| SNI 15-xxxx | Cement and lime |
| SNI 03-xxxx / SNI 2847 | Concrete design/structural |
| SNI 03-1726 | Earthquake loads |
| SNI 03-2849 | Reinforced concrete execution |
| SNI 03-3440 | Structural steel |
| SNI 03-6954 | Concrete flatwork |
| SNI 03-1731 / 1732 | Roof waterproofing |
| SNI 03-3800 | Electrical installations |
| SNI 03-6574 | Plumbing installations |
| SNI 03-6575 | HVAC / ventilation |
| SNI 03-2396 / 2397 | Doors, windows |
| SNI 03-2441 | Ceramic floor/wall tiles |
| SNI 06-xxxx | Plumbing fixtures / sanitary |
| SNI 07-xxxx | Paints and coatings |
| SNI 08-xxxx | Door and window frames (aluminum) |

Rules:
- Cite SNI by full number in the `Spesifikasi` column when the spec invokes it.
- NEVER fabricate an SNI number. If unsure of the exact code, write `SNI (refer to current BSN catalogue)` or omit.
- SNI is a national standard — it does not set prices.

### 5.2 AHSP — Analisis Harga Satuan Pekerjaan

The standard Indonesian unit-rate analysis: decomposes each work item into material coefficients + labor coefficients + equipment coefficients per unit of work.

```
HARGA SATUAN PEKERJAAN = (Material coefficient × material price)
                       + (Labor coefficient × labor wage)
                       + (Equipment coefficient × equipment rate)
```

AHSP editions are published/referenced by PUPR (Kementerian Pekerjaan Umum dan Perumahan Rakyat), BUMN contractors, and provincial governments. Key points:

- AHSP gives **coefficients**, not universal prices — you must multiply by current local prices.
- Different provinces/municipalities publish their own AHSP or adopt national versions.
- Labor wages in AHSP differ between provinces (UMP/UMK-based).
- For the engine: use AHSP coefficients when known; when not, derive equivalent coefficients from BOQ norms or vendor quotes and label the basis.

### 5.3 HSPK — Harga Satuan Pokok Kegiatan

Lump-sum unit rates for common activities used mainly in government-funded projects (PUPR, DAK, APBN/APBD schemes). Where AHSP decomposes into coefficients, HSPK gives one package rate per activity.

- HSPK is published periodically by PUPR and referenced in provincial Dinas PUPR schedules.
- Availability and coverage vary by province and year.
- Use HSPK when the project is a government scheme and the activity matches an HSPK item; cite the exact schedule.

### 5.4 Regional Price Schedules (Jadwal Harga / HSPK daerah / Analisa Harga Satuan)

Provinces, regencies, and state-owned contractors publish annual price schedules, e.g.:

| Publisher type | Examples (pattern, not exhaustive) |
|---|---|
| Provincial PUPR / Bina Marga | Provincial construction price schedule ("Jadwal Harga Pekerjaan" / "Analisa Harga Satuan") |
| Municipal Dinas (Jakarta, Bandung, Surabaya…) | Local material price references, UMR-based labor tables |
| BUMN contractors | WIKA, PTPN-adjacent, Adhi Karya reference schedules |
| KemenPUPR | National technical guidelines and reference analyses |

**Critical caveat:** regional schedules are **NOT universal**. A schedule for Jawa Barat does not apply to Sulawesi. A 2023 schedule is stale for 2026 pricing. Always record: issuing authority, region, year, and exact document name. When citing, write e.g. `Sumber: Jadwal Harga Dinas PUPR Prov. X Tahun 2024 (verify current edition)`.

Never fabricate a schedule name or number. If you cannot verify a specific schedule exists, cite the category (`provincial PUPR schedule`) and mark the price `INDICATIVE`.

### 5.5 Labor wages

- **UMP/UMK** (Upah Minimum Provinsi/Kabupaten-Kota): the legal floor, revised annually per province regulation.
- Construction labor is usually quoted per OH (orang hari = man-day) or per OH skill grade (kepala tukang, tukang, mandor, kuli).
- AHSP labor coefficients translate BOQ quantities into required man-days; multiply by the applicable daily wage.
- For non-construction labor (office, events, IT), use market day-rates, not UMP — but flag if a UMP-based rate is used as floor.

### 5.6 Material prices

Primary sources in Indonesia, in priority order:

1. Official producer/distributor price lists (e.g., cement manufacturers' dealer networks).
2. B2B marketplaces with listed prices (e.g., regional hardware e-commerce with IDR pricing).
3. Retail hardware stores (Indomaret-kelas tidak berlaku; toko bangunan / supermarket bangunan) — usually PARTIALLY VERIFIED via online listing.
4. Regional schedules' material price annexes — INDICATIVE.
5. Quoted offers from suppliers — VERIFIED for that supplier only.

Record per `market-price-research.md`: source, URL, access date, MOQ, delivered-vs-EXW, tax basis.

---

## 6. EXTRACTING QUANTITIES FROM DRAWINGS AND SPECS

### 6.1 Drawing types and what they give you

| Drawing | Provides |
|---|---|
| Architectural plan (denah) | Floor areas, room dimensions, partition locations |
| Sections (potongan) | Heights, floor-to-floor, ceiling levels |
| Elevations (tampak) | Facade areas, openings, finishes schedule |
| Structural drawings (struktur) | Concrete volumes, rebar schedules ( bending schedule ), formwork |
| MEP drawings | Pipe/cable runs, fixture counts, equipment schedules |
| Finishing schedule (daftar finishing) | Finish type per room → drives material choice |
| Door/window schedule | Opening sizes, counts, hardware sets |
| BOQ/Quantity survey from consultant | Direct quantities — verify, don't recompute blindly |

### 6.2 Takeoff procedure

1. **Scale check** — confirm drawing scale; measure a known dimension and verify.
2. **Grid/axis pass** — establish the axis system; measure bay by bay to avoid drift.
3. **Area pass** — floor, wall (both sides where applicable), ceiling, roof plan areas.
4. **Linear pass** — skirting, cornice, pipe runs, cable trays, perimeter drainage.
5. **Count pass** — fixtures, outlets, doors, windows, lights, sanitary ware.
6. **Volume pass** — excavation, concrete, masonry, plaster thickness.
7. **Rebar pass** — use the structural bending schedule (daftar penulangan) if provided; else estimate from member sizes with labeled assumptions.
8. **Deduction/addition pass** — openings, laps, wastage.
9. **Cross-check** — total floor area vs. sum of room areas; perimeter vs. sketch; counts vs. schedule.
10. **Document** — record every measurement rule used (deduction threshold, wastage factors, rounding) in section E assumptions.

### 6.3 When drawings are unavailable or incomplete

- Ask the user for: total floor area, number of rooms, ceiling height, structural system, finish level. That minimum set produces a defensible class-5 estimate.
- Otherwise produce a **parametric estimate**: cost per m² benchmarks by building type (label INDICATIVE/ESTIMATED, cite source class), clearly marked as benchmark-based, not quantity-based.
- Never silently switch from measured quantities to benchmark m² rates — the document must state which basis was used.

### 6.4 Specification extraction

From specs/drawings, extract for each line:
- Material type and grade (e.g., `bata merah kelas I`, `K-225`, `SNI 15-2049`)
- Dimensions and tolerances (thickness, size)
- Workmanship standard (e.g., `pasangan 1:2`, `plesteran 1:3`)
- Applicable SNI codes
- Finish level (e.g., `super matte`, `clasik`, `semi gloss`)

These become the `Spesifikasi` column content and drive supplier matching in procurement steps.

---

## 7. RAB QUALITY CHECKLIST

- [ ] Sections A–F present in order
- [ ] Every line has: description, spec, unit, qty, unit price, subtotal, source class
- [ ] Quantities include stated deduction/wastage rules
- [ ] Wastage applied to materials only
- [ ] Unit prices carry verification class; sources dated
- [ ] Indonesian standards cited only when verified (SNI numbers real; AHSP/HSPK cited by name+edition+region+year)
- [ ] Recap separates direct/indirect/contingency/tax; math reconciles
- [ ] Assumptions and exclusions explicit
- [ ] Document ID, date, version, validity present
- [ ] No fabricated schedule names, prices, or supplier names
