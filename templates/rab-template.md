# RAB Template — Rencana Anggaran Biaya

Complete RAB skeleton with all required sections (A–F). Fill in project-specific data. All prices must carry verification class and source.

---

## A. PROJECT INFORMATION / INFORMASI PROYEK

```
PROJECT NAME        : ______________________
PROJECT LOCATION    : ______________________
CLIENT / OWNER      : ______________________
PREPARED BY         : ______________________
DATE                : DD-MM-YYYY
CURRENCY            : IDR / USD / ________
EXCHANGE RATE       : (if applicable) ________
VALIDITY            : ________ days from issue
DOCUMENT ID         : RAB-____-____
VERSION             : 1.0
REFERENCE DRAWINGS  : [list drawing numbers/titles]
```

---

## B. WORK BREAKDOWN / RINCIAN PEKERJAAN

Hierarchical work packages. Group by phase.

```
1. [Phase Name — e.g., Pekerjaan Persiapan / Site Preparation]
   1.1 [Activity — e.g., Mobilisasi / Mobilization]
   1.2 [Activity — e.g., Pagar pengaman / Site fencing]

2. [Phase Name — e.g., Pekerjaan Tanah / Earthworks]
   2.1 [Activity — e.g., Galian pondasi / Foundation excavation]
   2.2 [Activity — e.g., Timbunan / Backfill]

3. [Phase Name — e.g., Pekerjaan Struktur / Structure]
   3.1 [Activity — e.g., Pasang bekisting / Formwork]
   3.2 [Activity — e.g., Pasang tulangan / Rebar placement]
   3.3 [Activity — e.g., Pengecoran / Concrete pouring]

4. [Phase Name — e.g., Pekerjaan Arsitektur / Architectural]
   4.1 [Activity — e.g., Pasangan dinding / Masonry]
   4.2 [Activity — e.g., Plesteran / Plastering]
   4.3 [Activity — e.g., Lantai / Flooring]

5. [Phase Name — e.g., Pekerjaan MEP]
   5.1 [Activity — e.g., Instalasi listrik / Electrical]
   5.2 [Activity — e.g., Instalasi plumbing / Plumbing]
   5.3 [Activity — e.g., AC / HVAC]

6. [Phase Name — e.g., Pekerjaan Finishing / Finishes]
   6.1 [Activity — e.g., Cat / Painting]
   6.2 [Activity — e.g., Door & window installation]

7. [Phase Name — e.g., Pekerjaan Eksterior / External Works]

8. [Phase Name — e.g., Testing & Handover / Serah Terima]
```

**Adapt phases to project type:** renovation skips earthworks; fit-out starts at demolition; infrastructure has different phases.

---

## C. DETAILED COST TABLE / RINCIAN BIAYA

The core of the RAB. Every line must have: description, spec, unit, quantity, unit price, subtotal, source class.

```
No  Uraian Pekerjaan / Description          Spesifikasi / Spec       Satuan  Volume/Qty  Harga Satuan    Jumlah        Sumber/Class
──  ──────────────────────────────────────  ───────────────────────  ──────  ──────────  ──────────────  ─────────────  ────────────────
   PHASE 1: [Phase Name]
1  ______________________________          ______________________  _____  _________  Rp _________  Rp _________  [VERIFIED/INDICATIVE/ESTIMATED] — [source]
2  ______________________________          ______________________  _____  _________  Rp _________  Rp _________  [class] — [source]
3  ______________________________          ______________________  _____  _________  Rp _________  Rp _________  [class] — [source]

   PHASE 2: [Phase Name]
4  ______________________________          ______________________  _____  _________  Rp _________  Rp _________  [class] — [source]
5  ______________________________          ______________________  _____  _________  Rp _________  Rp _________  [class] — [source]

[Continue for all phases — maintain numbering or restart per phase]
```

### Column guidance

| Column | Content | Example |
|---|---|---|
| No | Sequential or per-phase numbering | 1, 2, 3... or 1.1, 1.2, 1.3 |
| Uraian | Specific work description | "Pasangan bata merah 1:2, plaster 1:3" |
| Spesifikasi | Material grade, standard, dimensions | "SNI 15-2049, tebal 10 cm" |
| Satuan | Unit of measure | m², m³, kg, unit, ls, OH |
| Volume/Qty | Measured quantity (net or with wastage — state which) | 45,00 m² |
| Harga Satuan | Unit price with verification class | Rp 185.000 — INDICATIVE |
| Jumlah | Subtotal (Qty × Unit Price) | Rp 8.325.000 |
| Sumber | Price source and verification class | "Jadwal PUPR Jabar 2024" / "ESTIMATED — asumsi" |

### Price class labels (append to Harga Satuan or Sumber)

```
— VERIFIED          (live listed price, confirmed)
— PARTIALLY VERIFIED (listed, availability unconfirmed)
— INDICATIVE         (reference/schedule/historical)
— ESTIMATED          (calculated with assumptions)
— UNAVAILABLE        (no reliable price found)
```

---

## D. RECAPITULATION / REKAPITULASI

```
A. BIAYA LANGSUNG / DIRECT COSTS
   A.1 Material / Bahan                     Rp ______________________
   A.2 Labor / Upah Tenaga Kerja            Rp ______________________
   A.3 Equipment / Peralatan                Rp ______________________
   A.4 Subcontractor / Subkontrak           Rp ______________________
   A.5 Other Direct / Lain-lain Langsung    Rp ______________________
   ─────────────────────────────────────────────────────────────
   TOTAL DIRECT / TOTAL LANGSUNG            Rp ______________________

B. BIAYA TIDAK LANGSUNG / INDIRECT COSTS
   B.1 Overhead / Biaya Umum                Rp ______________________
   B.2 Administration / Administrasi        Rp ______________________
   B.3 Contingency / Kontingensi            Rp ______________________
   B.4 Other Indirect / Lain-lain           Rp ______________________
   ─────────────────────────────────────────────────────────────
   TOTAL INDIRECT / TOTAL TIDAK LANGSUNG    Rp ______________________

C. TAXES / PAJAK
   C.1 PPN [rate]%                          Rp ______________________
   ─────────────────────────────────────────────────────────────
   SUBTOTAL SEBELUM PAJAK                   Rp ______________________

D. GRAND TOTAL / JUMLAH TOTAL
   D.1 Total Project Cost                   Rp ______________________
   D.2 Contingency (if separate)            Rp ______________________
   D.3 Taxes                                Rp ______________________
   ─────────────────────────────────────────────────────────────
   GRAND TOTAL / JUMLAH KESELURUHAN        Rp ______________________
```

**Note:** If contingency is inside indirect (B.3), don't double-count in D.2. Clarify structure once.

---

## E. TECHNICAL ASSUMPTIONS / ASUMSI TEKNIS

```
ASSUMPTION: Drawing scale verified at [scale]
ASSUMPTION: Soil bearing capacity [value] (no soil test conducted)
ASSUMPTION: Wastage factors per cost-engineering.md §7.1
ASSUMPTION: Labor productivity per [AHSP/assumed/benchmark]
ASSUMPTION: Equipment rates per [source/method]
ASSUMPTION: Prices valid for [X] days from date of RAB
ASSUMPTION: Work executed during [season/conditions]
ASSUMPTION: Site access [conditions]
ASSUMPTION: Working hours [X] hours/day
ASSUMPTION: Crew size [X] persons per activity
```

List every assumption that materially affects the estimate.

---

## F. EXCLUSIONS / PENGECUALIAN

```
- Pekerjaan di luar gambar arsitektur yang direvisi
- Perizinan lingkungan / AMDAL
- Relokasi utilitas di luar batas tapak
- Pemeliharaan pasca-serah terima
- [Project-specific exclusions]
- [Anything NOT included in this RAB]
```

Exclusions prevent disputes. When in doubt, exclude and note.

---

## FILLING INSTRUCTIONS

1. **Complete section A** with project metadata
2. **Define WBS** in section B — adapt phases to project type
3. **Fill section C** with measured quantities and priced items
   - Every line: description + spec + unit + qty + price + source class
   - Apply wastage to materials only
   - Label every price with verification class
4. **Complete section D** — verify all math reconciles
5. **List assumptions** in section E — be specific
6. **List exclusions** in section F — be comprehensive
7. **Audit** — recalculate everything before presenting
8. **Format** — IDR uses `1.000.000,00`; USD uses `$1,000,000.00`

---

## VARIATIONS

### BOQ (Bill of Quantities) — Unpriced

Same structure but section C has no prices — only quantities:

```
No  Description          Spec          Unit    Qty
──  ──────────────────  ────────────  ──────  ────
1   Pasangan bata        1:2           m²      45,00
```

Use when user needs quantities only, prices to be added later.

### Simplified RAB (Class 5 Estimate)

For early-stage budgeting:

- Section B: high-level phases only
- Section C: benchmark costs per m² or lump sums
- Section D: simpler recap
- Section E: more assumptions, less detail
- Mark clearly: `CLASS 5 ESTIMATE — feasibility level`
