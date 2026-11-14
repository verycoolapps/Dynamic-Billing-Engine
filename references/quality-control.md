# Quality Control — Audit Checklist & Test Scenarios

The mandatory audit gate, the 10 test scenarios from the specification, confidence classification rules, and common failure modes.

---

## 1. AUDIT GATE — MANDATORY BEFORE PRESENTING

Every deliverable must pass through this 10-step audit before being shown to the user. No exceptions.

### 1.1 Recalculation audit

| Step | Check | Pass criteria |
|---|---|---|
| 1.1 | Recalculate every line item | `Qty × Unit Price = Subtotal` verified for each row |
| 1.2 | Recalculate category subtotals | Σ line items = category total |
| 1.3 | Recalculate direct/indirect | Σ categories = direct/indirect totals |
| 1.4 | Recalculate project cost | Direct + indirect = project cost |
| 1.5 | Recalculate contingency | Rate × base = contingency amount |
| 1.6 | Recalculate taxes | Taxable base × rate = tax amount |
| 1.7 | Recalculate grand total | Project + contingency + tax = final |
| 1.8 | Verify discounts | Subtotal − discount = taxable base |
| 1.9 | Verify markup/margin | Selling price math correct for stated basis |
| 1.10 | Verify unit conversions | All conversions mathematically correct |

**If ANY calculation fails:** fix it before presenting. Never show wrong math.

### 1.2 Completeness audit

| Check | Pass criteria |
|---|---|
| All required fields present | Invoice/RAB/quotation has all sections per template |
| All line items have sources | Every price has verification class + source |
| All assumptions labeled | `ASSUMPTION:` or `SOURCE:` on every non-obvious number |
| All exclusions stated | Document lists what's NOT included |
| All placeholders correct | `________` for unknown company/bank/tax data |
| No fabricated data | No invented URLs, phone numbers, company names |
| Document ID + date + version | Present on every document |

### 1.3 Consistency audit

| Check | Pass criteria |
|---|---|
| Units consistent | Same unit used throughout (m² not m²/m sometimes) |
| Currency consistent | Single currency or clearly converted |
| Terminology consistent | Same term for same thing (e.g., "subtotal" not "total" then "subtotal") |
| Verification classes consistent | Class matches evidence (VERIFIED only if truly verified) |
| Language consistent | All Indonesian or all English (or clearly mixed if user prefers) |
| Formatting consistent | IDR format throughout if IDR used |

### 1.4 Source audit

| Check | Pass criteria |
|---|---|
| Every price has source | Source name + URL or citation |
| Every source dated | Access date recorded |
| Every URL real | URL actually exists and shows claimed content |
| Every reference real | SNI numbers, AHSP editions, schedule names verified |
| Source register complete | All sources listed in final section |

### 1.5 Confidence audit

| Check | Pass criteria |
|---|---|
| Confidence level stated | HIGH/MODERATE/LOW/INSUFFICIENT assigned |
| Confidence justified | Explanation of why that level |
| No fake percentages | Never say "95% confident" — use qualitative levels |
| Gaps acknowledged | What's missing or uncertain stated clearly |

---

## 2. THE 10 TEST SCENARIOS

These are the canonical test cases. Each must produce correct, auditable output.

### 2.1 Scenario 1: Invoice with 10 line items

**Input:** User requests invoice for 10 different items (e.g., office supplies).

**Expected output:**
- Standard invoice format
- 10 line items with No | Description | Spec | Unit | Qty | Unit Price | Subtotal
- Subtotal = Σ all line items
- Tax (if applicable) computed on correct base
- Total = subtotal + tax
- All fields present, placeholders for unknown data
- Verification: recalculate all subtotals and total

**Common failure:** Missing line items, wrong subtotal, tax on wrong base.

### 2.2 Scenario 2: Construction RAB for building project

**Input:** "Buat RAB untuk renovasi kantor 150 m² di Jakarta."

**Expected output:**
- Full RAB structure (sections A–F)
- WBS with realistic phases (demolition, structure, MEP, finishes)
- Detailed cost table with quantities, unit prices, sources
- Material quantities with wastage factors applied
- Labor calculated via productivity/man-days
- Recapitulation: direct/indirect/contingency/tax
- Indonesian standards cited where applicable (SNI, AHSP, regional schedules)
- All prices classified (VERIFIED/PARTIALLY/INDICATIVE/ESTIMATED)
- Assumptions and exclusions explicit

**Common failure:** Missing phases, unreal quantities, prices without sources, double-counting transport/labor.

### 2.3 Scenario 3: Find 5 suppliers for material

**Input:** "Cari 5 supplier semen di Indonesia."

**Expected output:**
- 5 supplier records with all required fields
- Each supplier: name, type, website, location, contact (public only), products, price evidence, trust grade A–E
- Trust grades based on evidence checklist
- Recommendation: primary + alternate
- All contact info from public sources only
- No fabricated phone/email/address

**Common failure:** Inventing suppliers, fabricating contact details, grading without evidence.

### 2.4 Scenario 4: Compare vendor quotes with spec mismatch

**Input:** Three vendor quotes for "gypsum board partition" — one is 9.5mm, one is 12.5mm, one is moisture-resistant.

**Expected output:**
- Comparison table showing spec differences
- Each deviation classified (equivalent/inferior/superior/missing scope)
- Price normalization or adjustment for spec differences
- Vendor scoring on weighted dimensions
- Recommendation with reasoning
- Clear statement of which spec each quote actually offers

**Common failure:** Comparing different specs as equal, ignoring spec mismatch, price-only comparison.

### 2.5 Scenario 5: Invoice with discount + tax

**Input:** "Invoice untuk jasa konsultasi Rp 10.000.000, diskon 5%, PPN 11%."

**Expected output:**
- Subtotal: Rp 10.000.000
- Discount: Rp 500.000 (5%)
- Taxable base: Rp 9.500.000
- PPN: Rp 1.045.000 (11% of 9.500.000)
- Total: Rp 10.545.000
- Service invoice type (not material)
- PPh 23 note if applicable (service type)
- All math verified

**Common failure:** Tax on pre-discount amount, wrong discount calculation, missing PPh 23 note.

### 2.6 Scenario 6: Budget for 500-person event

**Input:** "Buat budget untuk corporate event 500 orang di Jakarta."

**Expected output:**
- All cost categories: venue, production (stage/sound/light), catering, logistics, crew, documentation, marketing, admin, contingency
- Itemized breakdown with quantities (e.g., catering per person, stage size)
- Realistic unit prices with verification classes
- Contingency applied on correct base
- Direct/indirect separation
- Assumptions (venue type, duration, service level)
- Exclusions (e.g., talent fees if not included)

**Common failure:** Missing categories, unrealistic per-person costs, no contingency, prices without sources.

### 2.7 Scenario 7: Analyze vendor quotation for fairness

**Input:** "Analisis quotation vendor ini: [quote details]. Apakah harga ini wajar?"

**Expected output:**
- Breakdown of quoted items
- Market price comparison (if research possible)
- Spec match assessment
- Markup/margin calculation if cost basis known
- Fairness assessment: HIGH/MODERATE/LOW with reasoning
- Alternative options if over/under priced
- Clear verdict: fair / slightly high / significantly high / suspiciously low

**Common failure:** No market comparison, accepting quote at face value, no spec verification.

### 2.8 Scenario 8: Missing prices for some items

**Input:** RAB request where some material prices can't be found.

**Expected output:**
- Items with found prices: classified appropriately
- Items without prices: marked UNAVAILABLE with ESTIMATED fallback
- Fallback estimates clearly labeled with method and assumptions
- Confidence level reflects price gaps
- Source register shows what was found vs not found
- No fabricated prices presented as real

**Common failure:** Inventing prices for missing items, presenting estimates as verified, not acknowledging gaps.

### 2.9 Scenario 9: Incomplete specifications

**Input:** "Berapa biaya untuk merenovasi rumah?" (no size, no details)

**Expected output:**
- Ask max 3 essential questions OR proceed with labeled assumptions
- If proceeding: parametric estimate (cost per m² benchmark) OR clearly stated assumptions
- Document states: "Berdasarkan asumsi: rumah 100 m², 1 lantai, renovasi ringan"
- Confidence: LOW or INSUFFICIENT (insufficient specs)
- Explicit statement that actual cost requires detailed specs
- No pretense of precision

**Common failure:** Giving specific number without basis, not asking clarifying questions, pretending estimate is accurate.

### 2.10 Scenario 10: Generate PDF/XLSX output

**Input:** "Export RAB ini ke Excel" or "Buat PDF invoice."

**Expected output:**
- XLSX: proper spreadsheet with columns, formulas for subtotals/totals where possible, formatting
- PDF: clean document layout, tables intact, all sections present, readable
- Both: same data as markdown version, no data loss in conversion
- File naming: descriptive (e.g., `RAB_Kantor_150m2_2026-11-14.xlsx`)

**Common failure:** Broken table formatting, missing sections, data corruption, wrong formulas.

---

## 3. CONFIDENCE CLASSIFICATION RULES

### 3.1 Confidence levels

| Level | Meaning | Criteria |
|---|---|---|
| **HIGH** | Strong evidence, multiple consistent sources | ≥3 verified sources agree, specs match, recent data |
| **MODERATE** | Reasonable evidence, some gaps | 1–2 verified sources, or mix of verified + indicative |
| **LOW** | Weak evidence, significant uncertainty | Mostly estimates, stale data, spec mismatches, single sources |
| **INSUFFICIENT** | Not enough data to estimate reliably | Missing specs, no price data, contradictory sources |

### 3.2 Confidence vs verification class

| Verification class | Typical confidence |
|---|---|
| VERIFIED | HIGH (if multiple) or MODERATE (if single) |
| PARTIALLY VERIFIED | MODERATE |
| INDICATIVE | LOW to MODERATE |
| ESTIMATED | LOW |
| UNAVAILABLE | INSUFFICIENT (for that item) |

### 3.3 Confidence assignment procedure

1. Count VERIFIED prices: 3+ = HIGH candidate, 1–2 = MODERATE candidate
2. Check spec match: all exact = higher confidence, mismatches = lower
3. Check freshness: all < 30 days = higher, any > 90 days = lower
4. Check source diversity: multiple source types = higher, single source = lower
5. Check completeness: all items priced = higher, gaps = lower
6. Assign final level and justify in one sentence

### 3.4 Confidence statement format

```
CONFIDENCE: MODERATE
Alasan: 2 dari 5 material memiliki harga VERIFIED, 3 ESTIMATED;
harga semen dari 1 sumber (single-source); spek tidak lengkap
untuk finishing.
```

Never use fake precision: "87% confident" is meaningless. Use qualitative levels.

---

## 4. COMMON FAILURE MODES

These are the errors the audit gate must catch:

### 4.1 Calculation errors

| Failure | Example | Detection |
|---|---|---|
| Wrong subtotal | 10 × 150.000 = 1.500.000 (not 150.000) | Recalculate every line |
| Wrong tax base | Tax on pre-discount amount | Check formula order |
| Wrong markup/margin | Using margin formula for markup | Verify basis stated |
| Unit conversion error | 1 m³ = 100 liter (wrong) | Check conversion table |
| Wastage double-applied | 10% wastage on qty AND price | Check where applied |

### 4.2 Data integrity errors

| Failure | Example | Detection |
|---|---|---|
| Fabricated price | "Semen Rp 45.000" with no source | Check source column |
| Fake URL | `tokosemen.com` doesn't exist | Verify URL resolves |
| Invented company | "PT Sumber Daya Jaya" not real | Check if real entity |
| Wrong verification class | ESTIMATED presented as VERIFIED | Check class vs evidence |
| Stale price as current | 2023 price used for 2026 project | Check access date |

### 4.3 Completeness errors

| Failure | Example | Detection |
|---|---|---|
| Missing cost category | No contingency in RAB | Check all 17 categories |
| Missing section | Invoice without payment terms | Check template sections |
| Missing assumption | Price used without stating basis | Check for ASSUMPTION labels |
| Missing exclusion | "All costs included" without listing | Check exclusions section |
| Missing source | Price with no source cited | Check source column |

### 4.4 Logic errors

| Failure | Example | Detection |
|---|---|---|
| Double-counting | Transport in supplier price AND separate line | Check anti-double-counting rules |
| Spec mismatch ignored | Comparing 9.5mm and 12.5mm board as equal | Check spec match |
| Wrong invoice type | Service work billed as material invoice | Check invoice type |
| PPN on exempt item | Tax added to tax-exempt goods | Check tax applicability |
| Contingency on contingency | Contingency base includes contingency | Check base definition |

### 4.5 Presentation errors

| Failure | Example | Detection |
|---|---|---|
| Wrong currency format | $1,000 for IDR | Check formatting rules |
| Inconsistent language | Mixed Indonesian/English randomly | Check user preference |
| AI-slop language | "Sebagai AI, saya sarankan..." | Check anti-slop rules |
| Missing placeholders | Real-looking but fake bank account | Check for `________` |
| Unlabeled assumptions | Numbers appearing from nowhere | Check every figure has source |

---

## 5. AUDIT CHECKLIST TEMPLATE

Use this checklist for every deliverable:

```markdown
## AUDIT CHECKLIST — [Document Type] [ID]

### Calculations
- [ ] All line items recalculated
- [ ] All subtotals verified
- [ ] All totals verified
- [ ] Tax computed on correct base
- [ ] Discount applied correctly
- [ ] Markup/margin basis correct

### Completeness
- [ ] All required sections present
- [ ] All fields filled or placeholdered
- [ ] All line items have sources
- [ ] All assumptions labeled
- [ ] All exclusions stated

### Consistency
- [ ] Units consistent throughout
- [ ] Currency consistent
- [ ] Terminology consistent
- [ ] Language consistent
- [ ] Formatting correct

### Sources
- [ ] Every price has source
- [ ] Every source dated
- [ ] Every URL verified real
- [ ] Source register complete

### Confidence
- [ ] Confidence level assigned
- [ ] Confidence justified
- [ ] Gaps acknowledged

### Final
- [ ] No fabricated data
- [ ] No AI-slop language
- [ ] User language matched
- [ ] Ready to present
```

---

## 6. WHEN TO HALT AND ASK

Stop and ask the user when:

| Situation | Question to ask |
|---|---|
| Critical spec missing | "Ukuran/luas proyek berapa?" |
| Budget range unknown | "Berapa kisaran budget yang tersedia?" |
| Timeline critical | "Kapan proyek harus selesai?" |
| Supplier preference | "Apakah ada supplier pilihan?" |
| Tax status unclear | "Apakah anda PKP?" |
| Currency unclear | "Mata uang apa yang digunakan?" |

**Max 3 questions.** If still ambiguous after 3, proceed with labeled assumptions.

---

## 7. POST-AUDIT ACTIONS

After passing audit:

1. **Fix any errors found** — never present with known errors
2. **State confidence level** — with justification
3. **Note limitations** — what's uncertain, what's missing
4. **Provide next steps** — what user should do with this information
5. **Offer variations** — if relevant, show alternative scenarios

---

## 8. CONTINUOUS IMPROVEMENT

After each deliverable:

- Note what worked well
- Note what was missing or wrong
- Update this file if new failure modes discovered
- Update references if new standards/patterns found
