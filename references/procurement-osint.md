# Procurement OSINT — Supplier Discovery

How to find suppliers, classify source types, capture supplier data, score trust, and make recommendations — ethically and within public information only.

---

## 1. PURPOSE

Procurement OSINT = finding who sells what you need, at what price, with what credibility — using only public, verifiable information. The engine NEVER contacts suppliers, NEVER uses private data, NEVER fabricates contact details.

Output per supplier: a structured record feeding `supplier-verification.md` and the comparison report.

---

## 2. SUPPLIER DISCOVERY WORKFLOW

```
1. DEFINE NEED
   - What exactly? Spec, quantity, delivery location, deadline.
   - Write the requirement in spec-sheet language, not marketing language.

2. GENERATE SOURCE LIST
   - Industry-specific source types (§3)
   - Search queries per source type

3. COLLECT CANDIDATES
   - Target: 5–10 candidates per requirement (minimum 3 for comparison)
   - Record every candidate — even rejected ones — in the source register

4. CAPTURE DATA PER SUPPLIER (§4)
   - Name, website, location, contact (public only), price evidence, MOQ, terms

5. VERIFY (§5 + supplier-verification.md)
   - Grade A–E per trust rubric

6. COMPARE & RECOMMEND
   - Score per quotation-methodology.md §5
   - Recommend primary + alternate

7. REPORT
   - Populate templates/procurement-report.md sections 05–06
```

---

## 3. SOURCE TYPES BY INDUSTRY

### 3.1 Source type taxonomy

| Type | Code | Description | Trust signal |
|---|---|---|---|
| Manufacturer | MFR | Produces the product directly | Highest — controls spec/price |
| Authorized distributor | DIST | Official channel partner | High — manufacturer-backed |
| Independent distributor | IND_DIST | Resells multiple brands | Medium — depends on track record |
| Marketplace seller | MKT | Sells via e-commerce/B2B platform | Medium — platform-verified only |
| B2B portal listing | B2B | Listed on trade directories | Medium-low — self-reported |
| Government/official schedule | GOV | Price published by authority | High for reference prices, not sellers |
| Retail store | RET | Physical store | Medium — depends on verification |
| Contractor/subcontractor | SUB | Performs services, not goods | Evaluated on portfolio/references |

### 3.2 Industry-specific discovery

#### Construction materials

| Need | Primary sources | Secondary |
|---|---|---|
| Cement, steel, aggregate | Manufacturer plants (Semen Indonesia, Astra, etc. — verify current), authorized depots | Toko bangunan, marketplace building-material sellers |
| Timber, finishing | Timber suppliers, plywood factories | Wood market (pasar kayu), distributors |
| MEP materials | Brand distributors (Schneider, Panasonic, etc. — verify), electrical wholesalers | Hardware stores |
| Fixtures (sanitary, doors) | Manufacturer showrooms, authorized dealers | Building material marts |
| Labor/subcontractors | Local contractor associations, referrals, portfolio sites | BUMN vendor lists for government work |

#### Events

| Need | Primary sources | Secondary |
|---|---|---|
| Venue | Venue websites, event platforms | Local convention bureau listings |
| AV/stage production | Production house websites, portfolios | Event vendor directories |
| Catering | Caterer websites, food platforms | Restaurant groups with event packages |
| Talent/MC/crew | Agency sites, LinkedIn (public), portfolios | Event staffing platforms |

#### IT & technology

| Need | Primary sources | Secondary |
|---|---|---|
| Hardware | Brand-authorized resellers, manufacturer stores | B2B IT marketplaces |
| Software licenses | Vendor direct, authorized resellers | Cloud marketplaces |
| Services/consulting | Company websites, professional directories | Referrals, case studies |
| Cloud services | Official cloud provider | Resellers for committed-use discounts |

#### Office supplies & furniture

| Need | Primary sources | Secondary |
|---|---|---|
| Furniture | Manufacturer, authorized dealers | Office furniture retailers, marketplaces |
| Electronics | Brand stores, authorized resellers | Electronics retailers |
| Consumables | Wholesalers, bulk suppliers | Office supply stores, marketplaces |

#### Manufacturing / industrial

| Need | Primary sources | Secondary |
|---|---|---|
| Raw materials | Producer direct, commodity exchanges | Distributors, importers |
| Machinery | OEM, authorized dealers | Used equipment dealers (verify condition) |
| Components | Component distributors | Broker networks (verify authenticity) |

#### Services (general)

| Need | Primary sources | Secondary |
|---|---|---|
| Professional services | Firm websites, credential registries | Industry associations |
| Maintenance/repair | Service company sites | Manufacturer service networks |
| Logistics | Freight forwarders, 3PL sites | Freight marketplaces |

### 3.3 Search query patterns

```
"[product]" + "supplier" / "distributor" / "dealer" / "authorized"
"[product]" + "harga" / "price" + "Indonesia" (for IDR pricing)
"[product]" site: marketplace-domain
"[product]" + "TDP" / "NPWP" / "business registration" (for verification)
"[industry]" + "asosiasi" / "association" (for member directories)
```

For Indonesian suppliers specifically: include `"Indonesia"`, city names, and Indonesian terms (`pemasok`, `distributor`, `gudang`, `toko`).

---

## 4. DATA TO CAPTURE PER SUPPLIER

Every supplier record MUST contain these fields. Missing fields = incomplete record — flag what's missing.

```
SUPPLIER RECORD
├── Identity
│   ├── Legal/trade name
│   ├── Type (MFR / DIST / MKT / etc.)
│   ├── Website URL
│   ├── Location (city, province, country)
│   ├── Public contact: phone, email, address — ONLY if published
│   └── Business registration evidence (if public): NIB/TDP/NPWP mention
│
├── Product fit
│   ├── Products/services offered (relevant subset)
│   ├── Spec match assessment (exact / equivalent / inferior / superior)
│   ├── Brands carried (if applicable)
│   └── Certifications claimed (ISO, SNI, etc.)
│
├── Commercial
│   ├── Price evidence (with verification class)
│   ├── MOQ / minimum order
│   ├── Price basis (EXW / delivered / installed)
│   ├── Payment terms
│   ├── Delivery/lead time
│   └── Warranty terms
│
├── Verification
│   ├── Trust grade (A–E, see §5)
│   ├── Evidence summary (what was checked, what was found)
│   ├── Red flags (if any)
│   └── Gaps (what could NOT be verified)
│
└── Metadata
    ├── Source of discovery (search query, directory, referral)
    ├── Date accessed
    ├── Analyst notes
    └── Confidence level (HIGH / MODERATE / LOW / INSUFFICIENT)
```

---

## 5. TRUST SCORING RUBRIC (A–E)

Grade each supplier on public evidence only. This rubric aligns with `supplier-verification.md`.

### Grade definitions

| Grade | Label | Criteria |
|---|---|---|
| **A** | Strong evidence | Verified business registration, official website with consistent info, verifiable physical address, active contact channels, positive independent reviews, authorized-seller status where applicable |
| **B** | Moderate evidence | Real business with website and contact info, some public footprint, no major red flags, but limited independent verification |
| **C** | Limited evidence | Basic web presence or directory listing, minimal independent footprint, contact info partially verifiable |
| **D** | Insufficient evidence | Almost no public footprint, unverifiable claims, or only self-reported information |
| **E** | Warning signals | Active red flags: inconsistent identity, scam reports, unverifiable registration, suspicious pricing, no real contact channel |

### Scoring dimensions (check each)

| Dimension | Strong (A/B) | Weak (D/E) |
|---|---|---|
| Business registration | Verifiable NIB/TDP/NPWP or equivalent | No registration found or unverifiable |
| Website quality | Professional, consistent, current | No website, parked domain, or template-only |
| Contact consistency | Phone/email/address match across sources | Inconsistent or unreachable |
| Domain age | Established (>2 years) | New or recently registered |
| Authorized status | Manufacturer/distributor badge verified | Claims authorization but can't verify |
| Independent reviews | Reviews on multiple platforms | No reviews or only self-posted |
| Physical presence | Verifiable address, maps listing | No address or virtual office only |
| Price realism | Within market range | Suspiciously low or high |

### Grade assignment rules

- **A** requires ≥6 strong dimensions AND no red flags.
- **B** requires ≥4 strong dimensions AND no red flags.
- **C** is the default when evidence is mixed or minimal.
- **D** when most dimensions are weak/unverifiable.
- **E** when ANY critical red flag is present (see supplier-verification.md §4).

**IMPORTANT:** Grade D ≠ scam. "Insufficient evidence" is a statement about available information, not about the supplier's legitimacy. Always say "insufficient public evidence to verify" rather than "possibly fraudulent."

---

## 6. RECOMMENDATION LOGIC

### 6.1 Recommendation hierarchy

```
Tier 1: Grade A or B + spec match + competitive price → RECOMMENDED
Tier 2: Grade A or B + spec match + higher price → ALTERNATE (quality pick)
Tier 3: Grade C + spec match + best price → CONDITIONAL (verify first)
Tier 4: Grade D → NOT RECOMMENDED unless no alternatives
Tier 5: Grade E → EXCLUDED
```

### 6.2 Recommendation statement format

```
REKOMENDASI / RECOMMENDATION:
Primary: [Supplier Name] — Grade [A-E]
Reason: [spec match, price position, terms, credibility]

Alternate: [Supplier Name] — Grade [A-E]
Reason: [why it's the backup — e.g., better warranty, faster delivery]

Excluded: [Supplier Name(s)] — Grade [E or spec fail]
Reason: [red flags or non-compliance]

Confidence: [HIGH/MODERATE/LOW] — [why]
```

### 6.3 When to recommend multiple

- **Single source / sole distributor:** recommend one, note no alternative exists.
- **Commodity items:** recommend 2–3 for price comparison.
- **Strategic/long-term:** recommend primary + alternate for supply chain resilience.
- **Emergency/urgent:** recommend fastest-credible, note price premium.

---

## 7. ETHICAL AND LEGAL BOUNDARIES

These rules are absolute:

### 7.1 Public information only

- Use search engines, company websites, government registries (e.g., OSS/NIB system), business directories, review platforms, LinkedIn (public profiles), maps.
- NEVER scrape private databases, breach data, or use leaked information.
- NEVER create fake accounts to access gated content.

### 7.2 No fabrication

- NEVER invent phone numbers, emails, addresses, registration numbers, or URLs.
- NEVER guess a website URL — search for it or omit.
- NEVER present a marketplace listing as the supplier's official site.
- If contact info isn't published, write `contact: not publicly listed`.

### 7.3 No misrepresentation

- Distinguish "manufacturer" from "authorized reseller" from "marketplace seller" — these are different trust levels.
- Don't claim a supplier is "verified" unless you actually verified them.
- Don't say "scam" — say "insufficient evidence" or "warning signals observed."

### 7.4 Cultural/legal sensitivity (Indonesia)

- Some businesses operate informally (warung, home industry). Lack of formal registration ≠ illegitimate — assess context.
- Government supplier lists (e.g., for PUPR projects) are authoritative for that context but not universal.
- Personal data protection (UU PDP): don't collect or store personal data beyond what's publicly posted for business purposes.

### 7.5 When you can't find enough

- State clearly: "Only X suppliers found meeting criteria; market may have more."
- Provide the search methodology so the user can expand.
- Offer to broaden criteria (adjacent products, different grades, import options).

---

## 8. SUPPLIER RECORD TEMPLATE

Use this structure for every supplier in the report:

```markdown
### Supplier: [Name]
- **Type:** [MFR/DIST/MKT/IND_DIST/B2B/RET/SUB/GOV]
- **Website:** [URL or "not found"]
- **Location:** [City, Province, Country]
- **Contact:** [public phone/email or "not publicly listed"]
- **Registration:** [NIB/TDP/NPWP evidence or "not verified"]
- **Products:** [relevant items]
- **Spec match:** [exact/equivalent/inferior/superior — detail]
- **Price evidence:** [class + amount + basis + source]
- **MOQ:** [quantity or "not stated"]
- **Terms:** [payment/delivery/warranty]
- **Trust grade:** [A/B/C/D/E]
- **Evidence:** [what was checked]
- **Red flags:** [none / list]
- **Gaps:** [what couldn't be verified]
- **Date accessed:** [YYYY-MM-DD]
- **Confidence:** [HIGH/MODERATE/LOW/INSUFFICIENT]
```
