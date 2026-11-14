# Invoice Standards

The 9 invoice types, required fields, numbering conventions, validation checklist, commercial invoice vs. Faktur Pajak distinction (Indonesian tax context), and payment terms vocabulary.

---

## 1. WHAT AN INVOICE IS — AND IS NOT

An **invoice** is a commercial document requesting payment for goods delivered or services rendered. It is a **demand for payment**, not proof of payment, not a receipt, and not a tax document.

Critical distinctions:

| Document | Issued by | Purpose | Tax authority |
|---|---|---|---|
| Commercial invoice / Invoice | Seller | Payment request | None — commercial only |
| **Faktur Pajak** | PKP (Pengusaha Kena Pajak) | Indonesian VAT (PPN) evidence | DJP (Direktorat Jenderal Pajak) |
| Receipt / Kwitansi | Seller | Proof payment received | None |
| Proforma invoice | Seller | Pre-sale price quote that functions as an order request | None |
| Purchase order (PO) | Buyer | Order commitment | None |

**RULE: this skill produces commercial invoices only. NEVER label a generated document "Faktur Pajak" or imply it is a tax invoice. See `tax-awareness.md`.**

---

## 2. THE 9 INVOICE TYPES

### 2.1 Standard invoice (Invoice Standar)

The default. One document covering goods or services delivered in a single transaction.

- Use for: one-off sales, completed work, product orders.
- Numbering: sequential per series.
- Trigger: delivery complete or service rendered.

### 2.2 Service invoice (Invoice Jasa)

For services rendered — consulting, installation labor, design, event staffing — where no physical goods change hands.

- Line items describe work performed (e.g., "Instalasi jaringan LAN — 3 titik akses").
- Often paired with timesheets, daily reports, or milestone sign-off as attachments.
- Tax treatment differs from goods in some jurisdictions — see `tax-awareness.md`.

### 2.3 Material invoice (Invoice Material)

For physical goods sold — hardware, furniture, raw materials, equipment.

- Requires per-item description, quantity, unit, unit price.
- Should reference delivery note (surat jalan) if goods shipped separately.
- Include weights/dimensions when freight was charged.

### 2.4 Project invoice (Invoice Proyek)

For a defined project scope delivered as one contract — e.g., "Office renovation package."

- Line items typically mirror the RAB/BOQ structure.
- May be issued at completion (final) or per billing schedule.
- Attach approved BOQ/RAB as appendix for traceability.

### 2.5 Progress billing invoice (Invoice Termin / Termin Pembayaran)

For long-running contracts billed at milestones or percentage completion.

- States cumulative % complete and amount certified this period.
- Requires quantity surveyor / consultant certification for construction work.
- Common pattern: `Termin 1 = 30%`, `Termin 2 = 40%`, `Termin 3 = 30%` of contract value.

### 2.6 Down payment invoice (Invoice Uang Muka / DP)

Pre-delivery payment request before work starts or goods ship.

- Usually 10–30% of contract value (state actual %).
- Recovered by deduction in later progress/final invoices.
- Must state clearly: `Uang muka / Down payment — akan diperhitungkan pada termin berikutnya`.
- Tax note: PPN on down payment follows specific rules — see `tax-awareness.md`.

### 2.7 Final invoice (Invoice Pelunasan / Final)

Closes out a contract — last payment covering retention release and final work.

- States cumulative billed vs. contract value.
- Deducts amounts already paid (DP + progress billings).
- Often includes retention money release (`uang jaminan` / `retensi`) if applicable.

### 2.8 Recurring invoice (Invoice Berkala / Subscription)

For periodic billing — monthly retainers, SaaS-like services, maintenance contracts, periodic supplies.

- States billing period covered (`Periode: Januari 2026`).
- May reference a master agreement/contract number.
- Numbering often uses period suffix: `INV-2026-001/JAN`.

### 2.9 Proforma invoice (Proforma Invoice)

A **pre-sale document** — not a payment demand, but a formal quote that a buyer can use to arrange payment, open an LC, or confirm order.

- Watermarked or titled `PROFORMA` — must be visually distinct from a real invoice.
- States: items, prices, payment terms, validity, bank details placeholders.
- Convert to standard invoice after payment confirmed.
- Common in export trade; less common domestically but useful for large orders.

---

## 3. REQUIRED FIELDS

Every invoice MUST contain these fields. Missing fields = incomplete document.

### Seller side
```
Seller legal name            ______________________
Seller address               ______________________
Seller NPWP (tax ID)         ____________  (placeholder — never fabricate)
Seller contact               ______________________
Seller bank account           ____________  (placeholder — never fabricate)
```

### Buyer side
```
Buyer legal name              ______________________
Buyer address                 ______________________
Buyer NPWP (if known)         ____________
Buyer contact / PIC           ______________________
```

### Document header
```
Invoice number                INV-YYYY-NNNN/Series
Invoice type                  Standard / Service / Material / Project /
                              Progress / Down Payment / Final / Recurring / Proforma
Invoice date                  DD-MM-YYYY
Due date                      DD-MM-YYYY
Payment terms                 See §6 vocabulary
Currency                      IDR / USD / other
```

### Line items
```
No | Description | Spec | Unit | Qty | Unit Price | Subtotal
```

### Totals
```
Subtotal (before discount)    Rp ________
Discount (if any)             Rp ________  (% or fixed — state which)
Taxable base                  Rp ________
Tax (PPN etc.)                Rp ________  (rate stated: 11% / 12% / n/a)
TOTAL DUE                     Rp ________
```

### Footer / conditions
```
Payment instructions          Bank transfer / cash / other
Validity (if proforma)        ________ days
Notes / terms                 Late payment penalty, warranty reference
Signature block               ____________  (seller) / ____________ (buyer ack.)
```

---

## 4. NUMBERING CONVENTIONS

Invoice numbers must be unique, sequential, and traceable. Recommended patterns:

| Pattern | Example | Use case |
|---|---|---|
| `INV-YYYY-NNNN` | INV-2026-0042 | General purpose |
| `INV-YYYYMM-NNN` | INV-202611-007 | Monthly series |
| `TYPE-YYYY-NNNN` | SRV-2026-0015 | Type-prefixed |
| `DOC-CUST-YYYY-NNNN` | PRJ-ACME-2026-0003 | Per-client series |
| Period-suffixed | INV-2026-0012/JAN | Recurring monthly |

Rules:
- Never reuse a number.
- Never skip numbers within a series (audit trail).
- Keep series per document type if the business issues multiple types.
- Include year to prevent ambiguity.
- The number goes in the filename too: `INV-2026-0042_AcmeOfficeRenovation.pdf`.

---

## 5. VALIDATION CHECKLIST

Before presenting any generated invoice, verify:

- [ ] Correct invoice type selected and labeled
- [ ] All required fields present (§3)
- [ ] Invoice number unique, sequential, dated
- [ ] Line items match the underlying BOQ/quotation/contract
- [ ] Quantities carry units; unit prices carry currency
- [ ] Subtotal = Σ line items (recalculate!)
- [ ] Discount applied correctly: `SUBTOTAL − DISCOUNT = TAXABLE BASE`
- [ ] Tax computed once on the correct base (see §7)
- [ ] TOTAL = TAXABLE BASE + TAX
- [ ] Payment terms stated and consistent with type (§6)
- [ ] Due date = invoice date + terms (or explicit date)
- [ ] No fabricated NPWP, bank account, or company data — placeholders used
- [ ] For down payment: states it will be deducted later
- [ ] For progress billing: states cumulative % and period
- [ ] For final: states total contract vs. billed vs. remaining
- [ ] For recurring: states billing period
- [ ] For proforma: clearly marked PROFORMA, has validity date
- [ ] NOT labeled "Faktur Pajak" or "Tax Invoice"
- [ ] Language matches user preference
- [ ] Currency formatting correct (IDR: `1.000.000,00`; USD: `$1,000,000.00`)

---

## 6. PAYMENT TERMS VOCABULARY

Standard terms — use these exact phrases for clarity:

| Term | Meaning | Net days |
|---|---|---|
| Due on receipt | Pay immediately on delivery of invoice | 0 |
| Net 7 | Pay within 7 days | 7 |
| Net 14 | Pay within 14 days | 14 |
| Net 30 | Pay within 30 days | 30 |
| Net 45 | Pay within 45 days | 45 |
| Net 60 | Pay within 60 days | 60 |
| 2/10 Net 30 | 2% discount if paid within 10 days; otherwise net 30 | 30 / 10 |
| COD (Cash on Delivery) | Pay on delivery of goods | 0 |
| Prepayment / 100% advance | Full payment before work starts | — |
| Milestone billing | Per agreed milestones (30/40/30 etc.) | Per schedule |
| Letter of Credit (LC) | Payment via bank LC — export/large contracts | Per LC terms |
| Retention | % held until defects liability period ends | Per contract |

Indonesian equivalents (use when outputting in Indonesian):

| Indonesian | English |
|---|---|
| Tunai | Cash |
| Kredit 30 hari | Net 30 |
| Termin pembayaran | Progress billing / payment milestone |
| Uang muka | Down payment |
| Pelunasan | Final settlement |
| Jaminan / Retensi | Retention / guarantee |
| Jatuh tempo | Due date |

Late payment clause (standard):
```
Keterlambatan pembayaran dikenakan denda 2% per bulan
(Late payment subject to 2% per month penalty)
```

Adjust rate per contract; never invent a rate without stating it as a term.

---

## 7. COMMERCIAL INVOICE vs FAKTUR PAJAK (Indonesian context)

This distinction is mandatory. Indonesian tax law separates commercial documents from tax documents:

| | Commercial Invoice | Faktur Pajak |
|---|---|---|
| Issuer | Any seller | PKP only (registered VAT collector) |
| Legal basis | Commercial practice | UU HPP / UU PPN |
| Purpose | Payment request | PPN evidence for buyer's input tax credit |
| Issued via | Any means | Coretax / e-Faktur system |
| Contains | Prices, items, totals | Tax invoice number, NPWP, tax lines |
| Generated by this skill | ✅ YES | ❌ NEVER |

Rules for the engine:

1. **Never produce a document titled "Faktur Pajak."** If a user asks for one, explain it must be issued through DJP's Coretax system by a PKP, and produce a commercial invoice + a note that PPN may apply.
2. **PPN awareness:** as of the UU HPP transition, PPN rates have been changing (11% general rate from 2022; 12% rate introduced with luxury-goods carve-outs from 2025 for certain categories). The engine records the applicable rate as an assumption and labels it `ASSUMPTION: PPN 11%/12% per current regulation — verify with tax consultant`.
3. **When PPN is shown on a commercial invoice:** show it as a separate line `PPN (x%)` computed on the taxable base, with a note that the official tax document is the Faktur Pajak issued separately by a PKP.
4. **PPh 23 withholding:** for certain services (consulting, management, technical services), the buyer may be required to withhold PPh 23 (typically 2% of the service value before PPN). The invoice should note `Harga belum termasuk PPh 23 yang wajib dipotong pemotong` when applicable — but this is a flag, not a computation the engine performs.
5. **Never give tax advice.** State facts about which document is which and which rates may apply; refer to `tax-awareness.md` and recommend a tax consultant for filings.

---

## 8. DOCUMENT ASSEMBLY

When generating an invoice, assemble in this order:

```
1. Header block (seller → buyer → doc meta)
2. Line items table
3. Totals block (subtotal → discount → tax → total)
4. Payment terms & instructions
5. Notes / conditions
6. Signature block
7. (Attachment list if applicable: PO, contract, delivery note, BOQ)
```

Use `templates/invoice-template.md` as the structural base. Fill placeholders; never invent company registration numbers, bank accounts, or NPWP.

Output formats:
- Markdown table → for chat display
- CSV → for spreadsheet import
- XLSX → when requested (single sheet, formulas for subtotals where possible)
- PDF → when requested (render from the template; preserve table structure)
