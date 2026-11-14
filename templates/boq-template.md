# BOQ Template — Bill of Quantities

Bill of Quantities table format for quantity takeoff without pricing. Use when user needs measured quantities only — prices added later or by contractor.

---

## BOQ / DAFTAR KUANTITAS

```
╔═════════════════════════════════════════════════════════════════╗
║  BILL OF QUANTITIES / DAFTAR KUANTITAS                         ║
║  BOQ No: BOQ-YYYY-NNNN/Series                                  ║
║  Date: DD-MM-YYYY                                              ║
║  Project: ______________________                               ║
║  Location: ______________________                              ║
╚═════════════════════════════════════════════════════════════════╝

PROJECT INFO / INFORMASI PROYEK
─────────────────────────────────────────────────────────────────
Project Name:      ______________________
Location:          ______________________
Client:            ______________________
Prepared By:       ______________________
Date:              DD-MM-YYYY
Drawing Ref:       [drawing numbers/revisions]
Scale Verified:    [scale] at [location on drawing]

─────────────────────────────────────────────────────────────────
WORK BREAKDOWN / RINCIAN PEKERJAAN
─────────────────────────────────────────────────────────────────

Phase 1: [Phase Name — e.g., Persiapan / Site Preparation]
─────────────────────────────────────────────────────────────────
No  Description              Spec          Unit    Qty    Remarks
──  ────────────────────────  ────────────  ──────  ────   ───────
1.1 ________________________  ____________  _____  _____  ________
1.2 ________________________  ____________  _____  _____  ________
1.3 ________________________  ____________  _____  _____  ________

Phase 2: [Phase Name — e.g., Struktur / Structure]
─────────────────────────────────────────────────────────────────
2.1 ________________________  ____________  _____  _____  ________
2.2 ________________________  ____________  _____  _____  ________
2.3 ________________________  ____________  _____  _____  ________

Phase 3: [Phase Name — e.g., Arsitektur / Architectural]
─────────────────────────────────────────────────────────────────
3.1 ________________________  ____________  _____  _____  ________
3.2 ________________________  ____________  _____  _____  ________

[Continue for all phases]

─────────────────────────────────────────────────────────────────
SUMMARY / REKAPITULASI
─────────────────────────────────────────────────────────────────
Phase                          Unit    Total Qty    Notes
─────────────────────────────────────────────────────────────────
1. [Phase 1]                   _____  __________  ________
2. [Phase 2]                   _____  __________  ________
3. [Phase 3]                   _____  __________  ________
...
─────────────────────────────────────────────────────────────────
GRAND TOTAL                    _____  __________

─────────────────────────────────────────────────────────────────
MEASUREMENT NOTES / CATATAN PENGUKURAN
─────────────────────────────────────────────────────────────────
• Deduction rule: [e.g., openings > 0.5 m² deducted]
• Wastage: [e.g., materials +5-10% per type]
• Rounding: [e.g., quantities to 2 decimals]
• Scale: [verified at 1:100]
• Assumptions: [list any measurement assumptions]

─────────────────────────────────────────────────────────────────
DRAWING REFERENCES / REFERENSI GAMBAR
─────────────────────────────────────────────────────────────────
• Architectural Plan: Drawing No. A-101 rev B
• Sections: Drawing No. A-201 rev A
• Structural: Drawing No. S-101 rev C
• MEP: Drawing No. M-101 rev A
• Finishing Schedule: Drawing No. F-001 rev A

─────────────────────────────────────────────────────────────────
SIGNATURES / TANDA TANGAN
─────────────────────────────────────────────────────────────────
Prepared by (Quantity Surveyor):
Name: __________________________
Signature: ______________________
Date: __________________________

Checked by:
Name: __________________________
Signature: ______________________
Date: __________________________

Approved by (Client):
Name: __________________________
Signature: ______________________
Date: __________________________
```

---

## COLUMN GUIDANCE

| Column | Content | Example |
|---|---|---|
| No | Item number (per phase or continuous) | 1.1, 2.3, etc. |
| Description | Work item description | "Pasangan dinding bata" |
| Spec | Material/specification | "Bata merah 1:2, plaster 1:3" |
| Unit | Unit of measure | m², m³, kg, unit, ls, OH |
| Qty | Measured quantity | 45,00 m² |
| Remarks | Notes, deductions, assumptions | "Includes openings < 0.5 m²" |

---

## MEASUREMENT RULES TO STATE

Always document measurement conventions in the notes section:

```
DEDUCTION RULES:
• Wall/floor areas: deduct openings > 0.5 m²
• Ceiling areas: deduct openings > 1.0 m²
• Rebar: add 10% lap allowance + 3% cutting waste
• Tiles: add 8% cutting waste
• Concrete: add 3% spillage

ROUNDING:
• Areas to 2 decimal places
• Volumes to 2 decimal places
• Linear to 2 decimal places
• Counts to whole numbers

SCALE:
• Verified at 1:100 on grid A-1
• Cross-checked with room schedule
```

---

## BOQ vs RAB

| | BOQ | RAB |
|---|---|---|
| **Purpose** | Quantities only | Quantities + prices |
| **Columns** | No description spec unit qty | No description spec unit qty price subtotal source |
| **Use case** | Tender documentation, contractor pricing | Client budget, cost planning |
| **Who prices** | Contractors submit prices | QS/client prepares estimate |

Use BOQ when:
- Issuing tender to multiple contractors
- User needs quantities only
- Prices to be determined by market bids

Use RAB when:
- Client needs cost estimate
- QS prepares budget
- Prices researched and included

---

## FILLING INSTRUCTIONS

1. **Complete project info** — name, location, client, date
2. **Verify drawing scale** — measure known dimension, confirm
3. **Define phases** — adapt to project type
4. **Measure quantities** — follow takeoff procedure in rab-methodology.md §6
5. **Document rules** — state deduction/wastage/rounding conventions
6. **Cross-check** — total areas vs room schedules, counts vs fixture schedules
7. **Get signatures** — QS prepares, someone checks, client approves
8. **Reference drawings** — list all source drawings with revision numbers

---

## COMMON BOQ ERRORS

| Error | Prevention |
|---|---|
| Wrong scale | Always verify scale before measuring |
| Missing deductions | State deduction rules explicitly |
| Double-counting | Check if area counted in two phases |
| Wrong units | Confirm unit matches spec (m² vs m vs unit) |
| No wastage noted | State whether qty is net or includes wastage |
| Vague descriptions | "Wall" → "Interior wall, gypsum board both sides" |
| Missing references | Always cite source drawing number |
