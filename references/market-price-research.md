# Market Price Research

How to research market prices: source priority, price classification, freshness rules, spec mismatch handling, the minimum 3-seller rule, and shipping/tax/MOQ normalization.

---

## 1. PURPOSE

Market price research answers: "What does this item actually cost in the market right now?" The output feeds every cost table, RAB, and comparison report.

**Core rule:** NEVER invent a price. Every price must trace to a source with a verification class.

---

## 2. SOURCE PRIORITY ORDER

When multiple sources exist for the same item, prefer them in this order:

| Priority | Source type | Verification class | Examples |
|---|---|---|---|
| 1 | Manufacturer's official price list | VERIFIED | Brand website price page, official distributor quote |
| 2 | Authorized distributor/reseller | VERIFIED | Official store on brand site, authorized dealer quote |
| 3 | Government/official schedule | INDICATIVE | PUPR price schedule, provincial material index |
| 4 | B2B marketplace listing | PARTIALLY VERIFIED | Verified seller on trade platform |
| 5 | Retail marketplace listing | PARTIALLY VERIFIED | E-commerce product page |
| 6 | General web listing | INDICATIVE | Directory listing, classified ad |
| 7 | Historical/reference data | INDICATIVE | Old reports, industry averages |
| 8 | Calculated estimate | ESTIMATED | Derived from cost build-up, no direct price |
| 9 | No data found | UNAVAILABLE | — |

### 2.1 Source quality signals

**High-quality sources:**
- Official manufacturer/distributor websites with current prices
- Government-published price schedules (dated, authoritative)
- Verified marketplace sellers with transaction history
- Multiple consistent sources for the same item

**Lower-quality sources:**
- Single anonymous listing
- Undated or old price references
- Sources requiring login/payment to see prices
- Aggregator sites with no clear provenance
- Social media posts (WhatsApp broadcasts, Facebook groups)

### 2.2 When sources conflict

| Situation | Handling |
|---|---|
| Same item, different prices | Show range + median; explain divergence (spec, region, MOQ, date) |
| Price dropped significantly | Note the change; use most recent source |
| Price seems too low | Flag as potential quality issue or scam |
| Only one source found | Mark PARTIALLY VERIFIED, note single-source limitation |
| Sources are all old | Mark INDICATIVE, note staleness |

---

## 3. PRICE CLASSIFICATION

Every price MUST be classified per the SKILL.md ladder. Never upgrade a class.

| Class | Definition | When to use | How to present |
|---|---|---|---|
| **VERIFIED** | Live listed price on traceable seller, confirmed available | Price seen today on official site or verified seller | "Listed at Rp X by [Seller]" |
| **PARTIALLY VERIFIED** | Price seen but availability/terms unconfirmed | Marketplace listing, unverified seller | "Listed at Rp X (availability unconfirmed)" |
| **INDICATIVE** | Published reference, historical data, or official schedule | Government schedule, old report, industry benchmark | "Reference range Rp X–Y (per [source])" |
| **ESTIMATED** | Calculated with disclosed assumptions | Cost build-up, no direct market price | "Estimated Rp X (basis: [method])" |
| **UNAVAILABLE** | No reliable evidence found | Nothing found | "No reliable price found; estimated fallback: Rp X" |

### 3.1 Classification rules

1. **VERIFIED requires:** live URL, current date, identifiable seller, price in the seller's currency.
2. **PARTIALLY VERIFIED:** price visible but seller unverified OR availability unclear OR terms ambiguous.
3. **INDICATIVE:** any published reference that isn't a live offer — schedules, reports, benchmarks.
4. **ESTIMATED:** engine calculated it — must state the method and assumptions.
5. **UNAVAILABLE:** honest "we don't know" — still provide ESTIMATED fallback if possible.

### 3.2 Recording requirements

For EVERY price recorded, capture:

```
PRICE RECORD
├── Item description (match spec)
├── Price amount + currency
├── Verification class
├── Source name + URL
├── Date accessed (YYYY-MM-DD)
├── Seller name + location
├── MOQ / minimum order
├── Price basis: EXW / FOB / DDP / delivered / installed
├── Tax included? (PPN yes/no/unknown)
├── Shipping included? (yes/no/unknown)
└── Notes (spec differences, conditions, caveats)
```

---

## 4. FRESHNESS RULES

Prices decay. A price from 6 months ago is not a current price.

### 4.1 Freshness thresholds

| Price age | Classification | Action |
|---|---|---|
| Same day / < 7 days | VERIFIED (if source is live) | Use as-is |
| 7–30 days | VERIFIED/PARTIALLY VERIFIED | Note date; acceptable for most uses |
| 30–90 days | PARTIALLY VERIFIED → INDICATIVE | Flag as "may have changed" |
| 90 days–1 year | INDICATIVE | Use as reference only; recommend re-verification |
| > 1 year | INDICATIVE (stale) or UNAVAILABLE | Historical reference; do not use as current price |

### 4.2 Recording access date

Every price MUST record `Date accessed: YYYY-MM-DD`. This is non-negotiable — it's the only way to assess freshness later.

### 4.3 When prices are stale

```
Price found but > 90 days old:
→ Classify as INDICATIVE
→ Note: "Price from [date]; may not reflect current market"
→ If possible, find a more recent source
→ If not, provide ESTIMATED range around the stale price
```

### 4.4 Volatile vs stable prices

| Category | Volatility | Freshness need |
|---|---|---|
| Commodities (steel, copper, fuel) | High | < 30 days |
| Construction materials (cement, brick) | Medium | < 90 days |
| Electronics/hardware | Medium-High | < 60 days |
| Furniture | Low-Medium | < 6 months |
| Services/labor | Medium | < 90 days |
| Software licenses | Low | Contract-based |

---

## 5. SPEC MISMATCH HANDLING

The #1 cause of bad price comparisons: comparing different specs as if identical.

### 5.1 Spec mismatch types

| Type | Example | Handling |
|---|---|---|
| Material grade | SNI 15-2049 cement vs generic cement | Not comparable — different spec |
| Size/dimension | 12mm rebar vs 10mm rebar | Not comparable — different spec |
| Brand vs generic | Branded paint vs economy paint | Comparable only if spec equivalent |
| Package size | 50kg bag vs 25kg bag | Normalize to per-kg price |
| Included services | Supply-only vs supply+install | Add missing cost or exclude |
| Region | Jakarta price vs Surabaya price | Note region; may differ 10–30% |
| Currency | USD vs IDR | Convert at stated rate; record rate source |
| Tax basis | Price incl. PPN vs excl. PPN | Normalize before comparing |

### 5.2 Spec matching procedure

1. **Extract spec** from BOQ/RFP/user request: material, grade, size, standard, quantity.
2. **Search** for that exact spec first.
3. **If exact match found:** use it, record spec match = exact.
4. **If only near-match found:** document the difference; classify as equivalent/inferior/superior.
5. **If no match:** search for the closest spec; note the gap; provide ESTIMATED price for the requested spec based on the near-match.
6. **Never silently substitute** — always state "price is for [spec found], requested spec is [spec needed], difference is [X]."

### 5.3 Spec comparison table

When comparing quotes with spec differences:

| Vendor | Quoted Spec | Required Spec | Match | Price Adjustment Needed |
|---|---|---|---|---|
| A | Cement SNI 15-2049, 50kg | Same | Exact | None |
| B | Cement generic, 50kg | SNI 15-2049 | Inferior | +Rp X for SNI-grade premium |
| C | Cement SNI 15-2049, 40kg | Same spec, diff pack | Exact (normalize) | Convert to per-kg |

---

## 6. MINIMUM 3-SELLER RULE

### 6.1 The rule

For any commodity item, aim to find **at least 3 sellers** before recommending a price. This gives:

- Confidence the price is market-real, not an outlier
- Ability to identify low/median/high range
- Fallback if the cheapest seller fails verification

### 6.2 When 3 sellers aren't available

| Situation | Fallback |
|---|---|
| Only 1–2 sellers found | Use what's available; mark confidence LOWER; note "limited market options" |
| Sole distributor/manufacturer | Note "single source"; price is whatever they charge |
| New/emerging product | Use ESTIMATED from component costs; mark INSUFFICIENT confidence |
| Niche/custom item | Use vendor quote as primary; benchmark against similar items |

### 6.3 What counts as a "seller"

- Must be an actual seller, not just a directory listing
- Must have a reachable contact or ordering channel
- Must have price evidence (VERIFIED, PARTIALLY VERIFIED, or INDICATIVE)
- Marketplace sellers count if they're verified/established

### 6.4 Aggregation

With 3+ sellers, compute:

```
LOW    = minimum price found
MEDIAN = middle price (or mean of middle two if even count)
HIGH   = maximum price found
RANGE  = HIGH − LOW
```

Present as: `Market range: Rp X–Y, median Rp Z (n=3 sellers)`.

If prices diverge >30% between sellers, investigate why (spec, MOQ, region, terms) before recommending.

---

## 7. SHIPPING / TAX / MOQ NORMALIZATION

### 7.1 Shipping normalization

Prices come in different bases. Normalize before comparing:

| Basis | Meaning | Normalization |
|---|---|---|
| EXW (Ex Works) | Buyer picks up at seller's dock | Add freight cost to destination |
| FOB | Seller delivers to port, buyer handles rest | Add freight + insurance |
| CIF | Seller delivers to destination port, insurance included | Add local delivery |
| DDP (Delivered Duty Paid) | Seller delivers to buyer's door, all costs included | Use as-is |
| DDU | Delivered, duties unpaid | Add duties/taxes |
| "Harga sampai lokasi" | Delivered to site (Indonesian usage) | Use as-is |
| "Harga gudang" | Warehouse price, delivery extra | Add freight |

**Rule:** Always record the price basis. If comparing EXW vs DDP, add estimated freight to EXW before comparing — or present both bases separately.

### 7.2 Tax normalization

| Tax basis | Handling |
|---|---|
| Price includes PPN (11%/12%) | Note "incl. tax"; for comparison, may extract pre-tax price |
| Price excludes PPN | Note "excl. tax"; add PPN if needed |
| PPN not mentioned | Assume excl. tax; flag as assumption |
| Tax-exempt | Note exemption; don't add tax |

For Indonesia: PPN rate depends on goods/services and current regulation (11% general, 12% for certain luxury goods from 2025). Record the rate used and cite it as assumption.

### 7.3 MOQ normalization

| Situation | Handling |
|---|---|
| MOQ < needed qty | No issue — order needed qty |
| MOQ > needed qty | Note excess; calculate per-unit cost at MOQ vs needed qty |
| MOQ affects unit price | Record both prices: "Rp X/unit at MOQ 100, Rp Y/unit at qty 10" |
| Multiple MOQ tiers | Record each tier; use the tier matching user's quantity |

### 7.4 Currency normalization

```
IDR price = USD price × exchange rate
USD price = IDR price ÷ exchange rate
```

Rules:
- Record the exchange rate used and its source (e.g., "BI mid-rate 2026-11-14: 1 USD = Rp 16.500").
- Use mid-market rate for estimates; note that actual rates vary.
- For IDR-denominated work, prefer IDR sources; convert only when necessary.
- Never assume a fixed rate without stating it.

---

## 8. RESEARCH WORKFLOW

```
1. DEFINE ITEM
   - Exact spec from BOQ/RFP/user request
   - Quantity needed
   - Delivery location
   - Deadline

2. SEARCH
   - Generate queries per procurement-osint.md §3.3
   - Prioritize manufacturer/distributor sources
   - Target: 3+ sellers minimum

3. COLLECT
   - Record each price with full metadata (§3.2)
   - Note spec match for each
   - Note freshness (access date)

4. NORMALIZE
   - Shipping basis → comparable basis
   - Tax basis → consistent treatment
   - Currency → single currency
   - MOQ → match user's quantity

5. CLASSIFY
   - Assign verification class per price
   - Downgrade if stale or uncertain

6. AGGREGATE
   - Compute low/median/high if 3+ sellers
   - Identify outliers and explain

7. REPORT
   - Populate price intelligence section of output
   - Record all sources in source register
```

---

## 9. COMMON PITFALLS

| Pitfall | Consequence | Prevention |
|---|---|---|
| Comparing different specs | Wrong conclusion | Spec-match check before comparing |
| Using stale prices | Underestimate current cost | Check access date; downgrade if old |
| Ignoring shipping basis | Price appears cheaper but isn't | Normalize to delivered price |
| Ignoring tax basis | Wrong total | State tax treatment explicitly |
| Single-source reliance | No market validation | Minimum 3-seller rule |
| Trusting one marketplace listing | Seller may be unreliable | Cross-check with other sources |
| Mixing currencies without rate | Math errors | Record rate + source |
| Forgetting MOQ | Unit price misleading | Record MOQ alongside price |
| Presenting estimate as verified | Misleading user | Always classify correctly |

---

## 10. OUTPUT FORMAT FOR PRICE RESEARCH

When reporting price research, use this structure:

```markdown
## Market Price Intelligence: [Item]

**Spec:** [exact specification]
**Quantity needed:** [qty + unit]
**Delivery location:** [city/region]

### Price Findings

| Seller | Price | Class | Basis | MOQ | Date | Notes |
|---|---|---|---|---|---|---|
| [Name] | Rp X | VERIFIED | Delivered | 10 | 2026-11-14 | SNI grade |
| [Name] | Rp Y | PARTIALLY VERIFIED | EXW | 50 | 2026-11-13 | Availability unconfirmed |
| [Name] | Rp Z | INDICATIVE | — | — | 2026-10-01 | Provincial schedule |

### Analysis
- **Market range:** Rp X–Y (n=3 sellers)
- **Median:** Rp Z
- **Recommended:** [seller] — [reason]
- **Confidence:** [HIGH/MODERATE/LOW] — [why]
- **Caveats:** [spec differences, staleness, gaps]

### Sources
[Source register entries]
```
