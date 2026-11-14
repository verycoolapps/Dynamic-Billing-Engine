# Invoice Template

Fill-in-the-blank invoice with all required fields. Replace `________` placeholders with actual data. NEVER invent company names, NPWP, bank accounts, or tax IDs.

---

## TEMPLATE — STANDARD INVOICE

```
┌─────────────────────────────────────────────────────────────────┐
│ INVOICE / FACTUR PENJUALAN                                      │
│ Invoice No: INV-YYYY-NNNN/Series                                │
│ Date: DD-MM-YYYY                                                │
│ Type: [Standard / Service / Material / Project / Progress /     │
│        Down Payment / Final / Recurring / Proforma]             │
│ Validity: [if proforma — X days]                                │
└─────────────────────────────────────────────────────────────────┘

SELLER / PENJUAL                          BUYER / PEMBELI
─────────────────────────────             ─────────────────────────────
Company Name: ______________________      Company Name: ______________________
Address: __________________________      Address: __________________________
City, Province, Postal Code: _______      City, Province, Postal Code: _______
NPWP: ____________________________       NPWP: ____________________________
Contact: __________________________      Contact Person: ____________________
Phone: ____________________________      Phone: ____________________________
Email: ____________________________      Email: ____________________________
Bank: _____________________________      Reference PO/Contract: ______________
Account No: ________________________      Project/Description: ______________

─────────────────────────────────────────────────────────────────
LINE ITEMS / RINCIAN
─────────────────────────────────────────────────────────────────
No  Description              Spec          Unit    Qty    Unit Price    Subtotal
──  ────────────────────────  ────────────  ──────  ────   ──────────   ──────────
1   ________________________  ____________  _____  _____  Rp ________  Rp ________
2   ________________________  ____________  _____  _____  Rp ________  Rp ________
3   ________________________  ____________  _____  _____  Rp ________  Rp ________
4   ________________________  ____________  _____  _____  Rp ________  Rp ________
5   ________________________  ____________  _____  _____  Rp ________  Rp ________

[Add rows as needed — maintain continuous numbering]

─────────────────────────────────────────────────────────────────
TOTALS / JUMLAH
─────────────────────────────────────────────────────────────────
Subtotal (before discount)     Rp ______________________
Discount [% or fixed]          Rp ______________________  [% / keterangan]
Taxable Base                   Rp ______________________
PPN [11% / 12% / n/a]          Rp ______________________  [rate]
PPh 23 [if applicable]         Rp ______________________  [note only]
TOTAL DUE                      Rp ______________________

─────────────────────────────────────────────────────────────────
PAYMENT TERMS / SYARAT PEMBAYARAN
─────────────────────────────────────────────────────────────────
Terms: [Net 30 / COD / Milestone / Prepayment / etc.]
Due Date: DD-MM-YYYY
Payment Method: [Bank transfer / Cash / etc.]
Bank Details:
  Bank: ___________________________
  Account Name: ___________________________
  Account No: _____________________________
  Branch: _________________________________

─────────────────────────────────────────────────────────────────
NOTES / KETERANGAN
─────────────────────────────────────────────────────────────────
[Late payment penalty, warranty reference, special instructions]

─────────────────────────────────────────────────────────────────
SIGNATURES / TANDA TANGAN
─────────────────────────────────────────────────────────────────
Seller: _________________________    Buyer Acknowledgment: _____________
Name: __________________________     Name: ___________________________
Title: __________________________    Title: __________________________
Date: __________________________     Date: __________________________

─────────────────────────────────────────────────────────────────
ATTACHMENTS / LAMPIRAN
─────────────────────────────────────────────────────────────────
[PO, contract, delivery note, BOQ, spec sheets — list if applicable]
```

---

## INVOICE TYPE VARIATIONS

### Service Invoice (Invoice Jasa)

Same structure. Line items describe work performed:

```
No  Description                    Spec              Unit    Qty   Unit Price    Subtotal
──  ─────────────────────────────  ────────────────  ──────  ────  ──────────   ──────────
1   Instalasi jaringan LAN         3 titik akses     titik   3     Rp ________  Rp ________
2   Konfigurasi server             1 unit             unit    1     Rp ________  Rp ________
3   Testing & commissioning        full system        ls      1     Rp ________  Rp ________
```

Add note: `Harga belum termasuk PPh 23 yang wajib dipotong pemotong` if service type likely triggers PPh 23.

### Material Invoice (Invoice Material)

Same structure. Line items are products:

```
No  Description                    Spec              Unit    Qty   Unit Price    Subtotal
──  ─────────────────────────────  ────────────────  ──────  ────  ──────────   ──────────
1   Semen Portland Komposit        SNI 15-2049, 50kg  sak     100   Rp ________  Rp ________
2   Baja Tulangan                  Ø10mm, 11.7kg/m   kg      500   Rp ________  Rp ________
3   Keramik Lantai 40×40           anti-slip          m²      200   Rp ________  Rp ________
```

Reference delivery note (surat jalan) if goods shipped separately.

### Progress Billing Invoice (Invoice Termin)

Add progress tracking section:

```
PROGRESS BILLING / TAGIHAN TERMIN
─────────────────────────────────────────────────────────────────
Contract Value:                    Rp ______________________
Previous Billings:                 Rp ______________________
This Billing (% complete):         Rp ______________________  [%]
Cumulative Billed:                 Rp ______________________  [%]
Remaining:                         Rp ______________________

Certification: [QS / Consultant / Client approval]
Certified By: _____________________________
Date: _________________________________
```

### Down Payment Invoice (Invoice Uang Muka)

Add clear down payment language:

```
DOWN PAYMENT / UANG MUKA
─────────────────────────────────────────────────────────────────
This is a DOWN PAYMENT invoice for [project description].
Amount:  [X]% of contract value = Rp ______________________

The down payment will be deducted from subsequent progress/final
invoices as per contract terms.

Contract Value: Rp ______________________
DP Percentage:  [X] %
DP Amount:      Rp ______________________
```

### Final Invoice (Invoice Pelunasan)

Show cumulative settlement:

```
FINAL SETTLEMENT / PELUNASAN
─────────────────────────────────────────────────────────────────
Total Contract Value:              Rp ______________________
Total Previously Billed:           Rp ______________________
Retention Held:                    Rp ______________________  [%]
This Final Payment:                Rp ______________________

Retention Release Date: DD-MM-YYYY (if applicable)
```

### Recurring Invoice (Invoice Berkala)

Add billing period:

```
RECURRING / BERKALA
─────────────────────────────────────────────────────────────────
Billing Period: [Month/Year] — e.g., "Januari 2026"
Service Description: [what the recurring fee covers]
Master Agreement Ref: [contract number if applicable]
```

### Proforma Invoice

Mark clearly as PROFORMA — not a payment demand:

```
╔═════════════════════════════════════════════════════════════════╗
║  PROFORMA INVOICE — BUKAN INVOICE RESMI / NOT A TAX INVOICE   ║
║  Dokumen ini untuk keperluan penawaran harga dan konfirmasi   ║
║  order. Bukan dokumen penagihan pembayaran.                   ║
╚═════════════════════════════════════════════════════════════════╝

All standard invoice fields apply.
Add: Validity period prominently displayed.
Add: "Setelah pembayaran dikonfirmasi, akan diterbitkan invoice resmi."
```

---

## MATH VERIFICATION TEMPLATE

Before finalizing, verify:

```
LINE 1:    Qty [____] × Price [____] = Subtotal [____]  ✓/✗
LINE 2:    Qty [____] × Price [____] = Subtotal [____]  ✓/✗
...
SUM LINE SUBTOTALS: [____]
DISCOUNT:  [____] or [%]
TAXABLE:   SUBTOTAL − DISCOUNT = [____]
TAX:       TAXABLE × [rate] = [____]
TOTAL:     TAXABLE + TAX = [____]
```

All must check out before presenting.

---

## FILLING INSTRUCTIONS

1. **Copy the template** for each invoice type needed
2. **Replace all `________`** with actual data or leave as placeholder
3. **Never invent:** company registration, NPWP, bank account, tax ID
4. **Verify math:** recalculate all subtotals and totals
5. **Check type:** correct invoice type for the transaction
6. **Add notes:** late payment, warranty, special terms as needed
7. **Get signatures:** actual signatures required for legal validity
8. **File naming:** `INV-YYYY-NNNN_CustomerName_ProjectType.pdf`
