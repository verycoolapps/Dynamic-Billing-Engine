# Tax Awareness

Boundaries of tax-related output: this skill produces estimates and commercial documents, not tax filings. PPN on material vs. services, PPh 23 withholding awareness, when to refer to a tax consultant, and why "Faktur Pajak" is never generated.

---

## 1. CORE BOUNDARY

**This skill produces:**
- Cost estimates and RABs (planning documents)
- Commercial invoices (payment requests)
- Quotations (price offers)
- BOQs (quantity lists)
- Budget analyses and comparisons

**This skill does NOT produce:**
- Tax returns or filings
- Faktur Pajak (Indonesian tax invoices)
- Tax calculations for compliance purposes
- Legal tax advice
- NPWP registration or verification

**The line:** We show tax as a line item when relevant (e.g., "PPN 11% = Rp X"). We never claim our document IS the tax document. We never compute withholding amounts as authoritative figures. We flag when a tax consultant is needed.

---

## 2. INDONESIAN TAX CONTEXT (2024–2026)

### 2.1 PPN — PPN (Value Added Tax)

| Aspect | Current status (as of 2026) |
|---|---|
| General rate | 11% (since April 2022) |
| Luxury goods rate | 12% (since January 2025, per PMK-131/2024 categories) |
| Exempt goods | Basic necessities, certain services |
| Document | Faktur Pajak (issued via Coretax/e-Faktur by PKP) |

**What the engine does:**
- Shows PPN as separate line: `PPN (11%) = taxable base × 0.11`
- States rate used: `ASSUMPTION: PPN 11% per regulation in effect`
- Notes when 12% may apply: `PPN 12% may apply for luxury goods per PMK-131/2024`
- NEVER issues Faktur Pajak — only commercial invoice with PPN line

### 2.2 PPh 23 — Withholding Tax on Services

| Aspect | Detail |
|---|---|
| Applies to | Certain services: consulting, management, technical services, royalties |
| Rate | 2% of service value (before PPN) |
| Withholder | Buyer (pemotong) — not the service provider |
| Document | Bukti Pemotongan (withholding slip) issued by buyer |

**What the engine does:**
- Adds note to service invoices: `Harga belum termasuk PPh 23 yang wajib dipotong pemotong`
- Does NOT calculate the withholding amount — that's the buyer's obligation
- Does NOT deduct PPh 23 from invoice total — invoice shows gross service fee
- Flags when service type likely triggers PPh 23

### 2.3 PPh 21/26/4(2) — Other withholding

- **PPh 21:** employee income tax — not relevant to this skill
- **PPh 26:** foreign taxpayer withholding — relevant for foreign contractors
- **PPh 4(2):** final tax on certain income (interest, dividends, etc.) — not typical for construction/services

The engine mentions these exist but does not compute them.

### 2.4 PPN on different transaction types

| Transaction | PPN treatment | Notes |
|---|---|---|
| Sale of goods (materials) | 11% or 12% | Standard rate applies |
| Construction services | 11% | Including labor + materials if bundled |
| Equipment rental | 11% | Treated as service |
| Professional services | 11% + possible PPh 23 | Consulting, design, engineering |
| Freight/transportation | 11% | If provided as service |
| Export of services | 0% or exempt | If qualifying as export |
| Down payment (uang muka) | PPN applies on receipt | Per tax regulation timing rules |

---

## 3. COMMERCIAL INVOICE vs FAKTUR PAJAK

This is the most critical distinction. See `invoice-standards.md` §7 for full details.

### 3.1 What the engine produces

**Commercial invoice** — a payment request document:
- Shows items, quantities, prices, totals
- May show PPN as a line item
- Is NOT a tax document
- Can be issued by anyone

### 3.2 What the engine NEVER produces

**Faktur Pajak** — an Indonesian tax invoice:
- Issued only by PKP (Pengusaha Kena Pajak = VAT-registered business)
- Generated through DJP's Coretax system
- Contains tax invoice number, NPWP, specific tax lines
- Is the legal evidence for PPN input tax credit

### 3.3 If user asks for "Faktur Pajak"

Respond:
```
Faktur Pajak hanya dapat diterbitkan oleh PKP melalui sistem Coretax DJP.
Engine ini menghasilkan invoice komersial — dokumen penagihan pembayaran.
Jika anda PKP, gunakan invoice ini sebagai dasar untuk menerbitkan Faktur Pajak
melalui Coretax. Jika bukan PKP, invoice ini sudah cukup untuk keperluan komersial.
```

Then provide the commercial invoice with PPN line if applicable.

---

## 4. WHEN TO REFER TO A TAX CONSULTANT

The engine should recommend professional advice when:

### 4.1 Always refer

- User asks about tax filing obligations
- User asks whether they are PKP
- User asks about tax deductions/credits
- User asks about cross-border transactions
- User asks about tax audit risk
- User asks about specific tax law interpretation

### 4.2 Likely refer

- Large project (> IDR 5 M) with complex tax treatment
- Mixed goods + services in one contract
- Government project with specific tax requirements
- Export/import transactions
- User is unsure about PPN rate applicability

### 4.3 Probably not needed

- Small internal cost estimate
- Simple goods purchase
- Personal/non-business use
- Educational/planning purposes

### 4.4 Referral language

```
"Untuk keperluan perpajakan resmi, konsultasikan dengan konsultan pajak atau
akuntan yang terdaftar. Engine ini menyediakan estimasi biaya dan dokumen
komersial — bukan nasihat perpajakan."
```

---

## 5. PPN CALCULATION IN DOCUMENTS

### 5.1 When to show PPN

Show PPN line when:
- Document is a commercial invoice for taxable goods/services
- User is PKP or selling to PKP
- Project is subject to PPN

Do NOT show PPN when:
- Document is a quotation (PPN may be added later)
- Document is an internal estimate/RAB (PPN depends on contract structure)
- Transaction is PPN-exempt
- User explicitly requests "harga belum termasuk PPN"

### 5.2 PPN calculation format

```
Subtotal (sebelum PPN)     Rp 10.000.000
PPN (11%)                   Rp 1.100.000
Total (termasuk PPN)        Rp 11.100.000
```

Or with discount:

```
Subtotal                     Rp 10.000.000
Diskon (5%)                  Rp   500.000
Dasar Pengenaan PPN          Rp  9.500.000
PPN (11%)                    Rp 1.045.000
Total                        Rp 10.545.000
```

### 5.3 PPN assumptions to state

```
ASSUMPTION: PPN 11% applied to all taxable items
ASSUMPTION: PPN 12% applies to luxury goods per PMK-131/2024
ASSUMPTION: No PPN on exempt items [list if known]
ASSUMPTION: PPN rate per regulation in effect at time of estimate
```

---

## 6. PPh 23 AWARENESS

### 6.1 What triggers PPh 23

PPh 23 (2% withholding) applies to payments for certain services:

- Management/consulting services
- Technical services
- Engineering services
- Legal services
- Accounting/audit services
- Royalties
- Rent for certain assets

### 6.2 How the engine handles it

On service invoices/quotations, add note:

```
Catatan: Harga belum termasuk PPh 23 yang wajib dipotong oleh pemotong
(Note: Price excludes PPh 23 withholding tax to be deducted by the payer)
```

Do NOT:
- Calculate the 2% amount
- Deduct it from the invoice total
- Show it as a line item
- Claim it's the final tax treatment

### 6.3 When PPh 23 doesn't apply

- Construction services (typically not subject to PPh 23)
- Sale of goods (PPN applies, not PPh 23)
- Services to individuals (different rules)
- Export services (may be exempt)

---

## 7. OTHER TAX CONSIDERATIONS

### 7.1 BPHTB — Land/Building Transfer Tax

- Applies to property transfers, not typical for this skill
- Mention only if user asks about property purchase costs

### 7.2 PBJT — Local Service Tax

- Some regions impose local taxes on services
- Varies by province/regency
- Mention as potential additional cost if relevant

### 7.3 Import duties

- For imported goods, duties + PPN may apply
- Engine can note "import duties may apply" but doesn't calculate them

### 7.4 Withholding on rent

- Equipment rental may trigger PPh 23 or PPh 4(2)
- Note as potential tax implication

---

## 8. DOCUMENT TEMPLATES — TAX-RELATED PLACEHOLDERS

Use these placeholders in documents:

```
NPWP Penjual          : ____________  (never fabricate)
NPWP Pembeli          : ____________
No. Faktur Pajak     : ____________  (only if user provides — engine doesn't issue)
DPP (Dasar Pengenaan Pajak) : Rp ________
PPN                   : Rp ________  (11% or 12% as applicable)
PPh 23 dipotong       : Rp ________  (if applicable — buyer's obligation)
```

For commercial invoice footer:

```
"Invoice ini adalah dokumen komersial dan bukan Faktur Pajak.
Untuk keperluan perpajakan, gunakan sistem Coretax DJP."
```

---

## 9. COMMON TAX MISTAKES TO AVOID

| Mistake | Correct handling |
|---|---|
| Calling commercial invoice "Faktur Pajak" | NEVER — different documents |
| Calculating PPh 23 as deduction from invoice | NEVER — it's buyer's withholding obligation |
| Assuming all services have same tax treatment | Check service type; some exempt, some PPh 23 |
| Using wrong PPN rate | State rate used; note it may have changed |
| Ignoring import duties on imported goods | Flag as potential additional cost |
| Giving definitive tax advice | Refer to tax consultant for compliance |
| Fabricating NPWP or tax numbers | Use placeholders only |

---

## 10. SUMMARY — TAX RULES FOR THE ENGINE

1. **Estimates and commercial documents only** — no tax filings
2. **PPN shown as line item** when applicable — never as the document itself
3. **PPh 23 noted as buyer's obligation** — never calculated by engine
4. **Faktur Pajak NEVER generated** — refer to Coretax/DJP
5. **NPWP and tax IDs are placeholders** — never fabricated
6. **Tax consultant referral** for compliance questions
7. **State assumptions** about tax rates and treatment
8. **Indonesian + English** when discussing tax (user's language)

---

## 11. REFERENCES

For authoritative tax information, consult:

- **DJP (Direktorat Jenderal Pajak):** tax.go.id — official tax portal
- **Coretax:** coretaxdjp.pajak.go.id — e-Faktur system
- **PMK-131/2024:** PPN rate regulation for luxury goods
- **UU HPP:** tax law amendments
- **KUP (Ketentuan Umum Perpajakan):** general tax provisions

This skill's tax awareness is for **estimation and document preparation**, not tax compliance. For actual tax obligations, engage a registered tax consultant (konsultan pajak) or public accountant (akuntan publik).
