# Quotation Template

Sales quotation skeleton with scope, itemized pricing, delivery, payment terms, validity, exclusions, warranty, and conditions. Fill placeholders; never invent company data.

---

## QUOTATION / PENAWARAN

```
╔═════════════════════════════════════════════════════════════════╗
║  QUOTATION / PENAWARAN HARGA                                  ║
║  Quote No: QUO-YYYY-NNNN/Series                                ║
║  Date: DD-MM-YYYY                                              ║
║  Validity: [14/30/60/90] days from date                        ║
╚═════════════════════════════════════════════════════════════════╝

ISSUED BY / DITERBITKAN OLEH          TO / KEPADA
─────────────────────────────         ─────────────────────────────
Company Name: ______________________  Company Name: ______________________
Address: __________________________  Address: __________________________
City, Province: ________________      City, Province: ________________
NPWP: ____________________________   Contact Person: ____________________
Contact: __________________________  Phone: ____________________________
Phone: ____________________________  Email: ____________________________
Email: ____________________________  Reference: [RFQ/Project Ref] _________

─────────────────────────────────────────────────────────────────
SCOPE OF WORK / RUANG LINGKUP PEKERJAAN
─────────────────────────────────────────────────────────────────
[Describe what is included — be specific]

Included:
• [Item 1 — e.g., Supply of materials per attached BOQ]
• [Item 2 — e.g., Installation and commissioning]
• [Item 3 — e.g., Testing and handover]

Reference Documents:
• [BOQ rev A dated DD-MM-YYYY]
• [Drawing set rev B]
• [Specification document]

─────────────────────────────────────────────────────────────────
ITEMIZED PRICING / RINCIAN HARGA
─────────────────────────────────────────────────────────────────
No  Description              Spec          Unit    Qty    Unit Price    Subtotal    Notes
──  ────────────────────────  ────────────  ──────  ────   ──────────   ──────────   ──────
1   ________________________  ____________  _____  _____  Rp ________  Rp ________  ______
2   ________________________  ____________  _____  _____  Rp ________  Rp ________  ______
3   ________________________  ____________  _____  _____  Rp ________  Rp ________  ______
4   ________________________  ____________  _____  _____  Rp ________  Rp ________  ______
5   ________________________  ____________  _____  _____  Rp ________  Rp ________  ______

─────────────────────────────────────────────────────────────────
OPTIONAL / ALTERNATE ITEMS / OPSI / ALTERNATIF
─────────────────────────────────────────────────────────────────
[If applicable — clearly separated]

Option A: [description]
  Unit Price: Rp ________  |  Subtotal: Rp ________

Option B: [description]
  Unit Price: Rp ________  |  Subtotal: Rp ________

─────────────────────────────────────────────────────────────────
COMMERCIAL TERMS / SYARAT KOMERSIAL
─────────────────────────────────────────────────────────────────
Delivery Terms:    [EXW / FOB / CIF / DDP / "delivered to site"]
Delivery Timeline: [X days/weeks from PO acceptance]
Payment Terms:     [Net 30 / 30-40-30 milestone / Prepayment 20%]
Warranty:          [X months materials / Y months workmanship]

─────────────────────────────────────────────────────────────────
EXCLUSIONS / YANG TIDAK DIHARGAI
─────────────────────────────────────────────────────────────────
• [Item not included — e.g., Delivery outside area X]
• [Item not included — e.g., Installation (unless stated above)]
• [Item not included — e.g., Crane/Heavy equipment for high floors]
• [Item not included — e.g., Permits/licenses]
• [Item not included — e.g., Changes after PO issuance]

─────────────────────────────────────────────────────────────────
VALIDITY & CONDITIONS / MASA BERLAKU & SYARAT
─────────────────────────────────────────────────────────────────
This quotation is valid for [X] days from the date above.
Harga penawaran ini berlaku selama [X] hari dari tanggal di atas.

After expiry, prices may change subject to market conditions.
Setelah masa berlaku, harga dapat berubah sesuai kondisi pasar.

Currency: [IDR / USD / other]
Tax: [PPN included / excluded / as applicable]
Governing Terms: [standard terms reference if any]

─────────────────────────────────────────────────────────────────
ACCEPTANCE / PENERIMAAN
─────────────────────────────────────────────────────────────────
Seller: _________________________    Buyer: _________________________
Name: __________________________     Name: _________________________
Title: __________________________    Title: _________________________
Signature: _______________________   Signature: ______________________
Date: __________________________     Date: __________________________

─────────────────────────────────────────────────────────────────
ATTACHMENTS / LAMPIRAN
─────────────────────────────────────────────────────────────────
[Spec sheets, drawings, BOQ, catalog pages, references]
```

---

## FILLING INSTRUCTIONS

### For sales quotations (user is seller)

1. **Header:** Fill quote number, date, validity period
2. **Scope:** Describe exactly what's included — reference controlling documents
3. **Pricing:** Itemize every deliverable with qty, unit, price, subtotal
4. **Options:** Add alternates if offering choices
5. **Terms:** Specify delivery, payment, warranty clearly
6. **Exclusions:** List everything NOT included — protect both parties
7. **Validity:** State how long prices hold
8. **Acceptance:** Signature block for both parties
9. **Verify math:** All subtotals and totals must be correct

### For procurement analysis (user is buyer analyzing vendor quotes)

Use `templates/supplier-comparison.md` instead — this template is for creating quotes, not analyzing them.

---

## KEY SECTIONS EXPLAINED

### Scope of Work

Must be unambiguous. Two people reading it should price the same thing.

```
BAD:  "Supply and install office furniture."
GOOD: "Supply and install 12 workstations per BOQ rev A:
       desks 140×70cm laminate top steel legs;
       chairs with lumbar support; assembly included;
       delivery to 10th floor, no crane."
```

### Exclusions

As important as scope. Common exclusions:

```
• Delivery outside specified area
• Installation/commissioning (unless stated as included)
• Crane/heavy equipment for high floors
• Permits and licenses
• Scope changes after PO issuance
• Spare parts beyond warranty period
• Training (unless in package)
• Taxes/duties not specified
```

### Payment Terms

Use standard vocabulary (see invoice-standards.md §6):

```
Net 30          — Pay within 30 days
30-40-30        — 30% advance, 40% mid, 30% on delivery
100% advance    — Full payment before work
COD             — Cash on delivery
Retention       — % held until defects liability ends
```

### Warranty

```
Material warranty: 12 months (manufacturer defect)
Workmanship warranty: 3 months (installation defect)
```

State remedy: repair / replace / refund.

---

## VARIATIONS

### Simplified Quote (for small orders)

```
QUOTE / PENAWARAN
No: QUO-YYYY-NNNN    Date: DD-MM-YYYY    Valid: 14 days

To: [Buyer name/address]

Items:
1. [Description] — [Qty] [Unit] @ Rp [Price] = Rp [Subtotal]
2. [Description] — [Qty] [Unit] @ Rp [Price] = Rp [Subtotal]

Total: Rp [Amount]

Terms: [payment/delivery/warranty]
Valid until: [date]
```

### Detailed Quote (for large projects)

Use full template with:
- BOQ reference
- Itemized pricing per BOQ line
- Alternates section
- Detailed terms and conditions
- Attachment list

---

## MATH VERIFICATION

Before sending:

```
LINE 1:  Qty [__] × Price [__] = Subtotal [__]  ✓
LINE 2:  Qty [__] × Price [__] = Subtotal [__]  ✓
...
SUM:     [__]
DISCOUNT: [__] or [%]
TAXABLE: [__]
TAX:     [__]
TOTAL:   [__]
```

All must verify.
