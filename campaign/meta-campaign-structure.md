# META ADS — CAMPAIGN STRUCTURE & LAUNCH PROTOCOL
## Ikaria Lean Belly Juice | $3,000 Budget | Tier-1 | May 2026

---

## ACCOUNT SETUP CHECKLIST (Day 1 — before any ad goes live)

- [ ] Business Manager verified and in good standing
- [ ] Ad account spending limit set to $100/day (safety cap)
- [ ] Meta Pixel installed on bridge page — PageView firing confirmed
- [ ] Custom event "BridgeClick" firing on CTA button click (via fbq('trackCustom', 'BridgeClick'))
- [ ] Domain verified in Meta Business Manager (your bridge page domain)
- [ ] UTM parameters template saved in account
- [ ] Payment method confirmed — daily budget won't be interrupted
- [ ] 2FA enabled on account

---

## BUDGET OVERVIEW

| Phase | Days | Daily Budget | Total |
|-------|------|-------------|-------|
| Validation | 1–7 | $50/day | $350 |
| Optimization | 8–21 | $70/day | $980 |
| Scale | 22–30 | Up to $150/day | $770–$1,300 |
| Infrastructure (ClickMagick, domain, hosting) | — | — | ~$150 |
| **Total** | | | **~$3,000** |

---

## CAMPAIGN ARCHITECTURE

### CAMPAIGN 1: [MITO] Mitochondrial Mechanism Angle
**Objective:** Traffic (Week 1–2) → Conversions (Week 3+ if 15+ sales on pixel)
**Budget:** CBO — $25/day
**Bid strategy:** Lowest cost (no cap in Week 1)
**Attribution:** 7-day click, 1-day view
**Bridge page:** advertorial-v1-mitochondrial.html

#### AD SET 1-A: Broad — Women 45-64
- Location: US, CA, UK, AU
- Age: 45–64
- Gender: Women
- Interests: NONE (true broad)
- Placements: Automatic (let Meta optimize)
- Budget: Parity within CBO

**Ads in set:**
| Ad ID | Format | Copy | Status |
|-------|--------|------|--------|
| 1-A-1 | Static image | "Metabolism Isn't Broken" | Active |
| 1-A-2 | Static image | "She Ate 1,200 Calories" | Active |
| 1-A-3 | Static image | "Cellular Reason" | Active |

#### AD SET 1-B: Interest Stack — Menopause/Wellness
- Location: US, CA, UK, AU
- Age: 45–64
- Gender: Women
- Interests: Menopause, Weight Loss, Women's Health, Healthy Aging
- Placements: Automatic
- Budget: Parity within CBO

**Ads in set:**
| Ad ID | Format | Copy | Status |
|-------|--------|------|--------|
| 1-B-1 | Static image | "What Changes After Menopause" | Active |
| 1-B-2 | Video 30s | Script #1 "The Blocker" | Active |
| 1-B-3 | Static image | Best headline from rotation bank | Active |

---

### CAMPAIGN 2: [FAM] Grandma / Family / Energy Angle
**Objective:** Traffic (Week 1–2) → Conversions (Week 3+ if data)
**Budget:** CBO — $25/day
**Bid strategy:** Lowest cost
**Attribution:** 7-day click, 1-day view
**Bridge page:** advertorial-v2-grandma.html

#### AD SET 2-A: Broad — Women 45-64
- Location: US, CA, UK, AU
- Age: 45–64
- Gender: Women
- Interests: NONE (true broad)
- Placements: Automatic

**Ads in set:**
| Ad ID | Format | Copy | Status |
|-------|--------|------|--------|
| 2-A-1 | Static image | "Granddaughter Stopped Asking" | Active |
| 2-A-2 | Static image | "12 Years of Trying" | Active |
| 2-A-3 | Static image | "Body Changed the Rules" | Active |

#### AD SET 2-B: Interest Stack — Family/Aging
- Location: US, CA, UK, AU
- Age: 45–64
- Gender: Women
- Interests: Grandparenting, Women Over 50, Healthy Aging, Family
- Placements: Automatic

**Ads in set:**
| Ad ID | Format | Copy | Status |
|-------|--------|------|--------|
| 2-B-1 | Static image | "Grandma Loses 35 lbs" | Active |
| 2-B-2 | Video 45s | Script #2 "Grandma Energy" | Active |
| 2-B-3 | Static image | Best headline from rotation bank | Active |

---

## LAUNCH SEQUENCE

### Day 1 (Setup)
1. Upload bridge pages to hosting — test load speed (target LCP < 2.5s on mobile 4G)
2. Verify Pixel PageView fires on bridge page
3. Verify BridgeClick event fires on CTA button
4. Create ad account structure (campaigns, ad sets — no ads yet)
5. Set spending limit to $100/day

### Day 2 (Creative Upload)
1. Upload all static image creatives (10 thumbnails)
2. Submit for Meta review — do NOT launch yet
3. Set up UTM parameters on all ad URLs
4. Connect ClickMagick tracking links

### Day 3 (Launch — Campaign 1 only)
1. Launch Campaign 1 only ($25/day CBO)
2. Monitor for disapprovals in first 2 hours
3. If no disapprovals by hour 4 — launch Campaign 2

### Day 4 (Monitor)
1. Check delivery — are all ad sets spending?
2. Check CTR — any ad below 0.3% CTR in first 500 impressions is a creative issue, not an optimization issue
3. Do NOT make any changes. Learning phase.

### Day 5–7 (Data Collection)
- No edits to campaigns
- Log all data in daily tracker (see below)
- Note: it takes 3–4 days of data to see CTR patterns stabilize

---

## OPTIMIZATION RULES (Week 2 — Day 8 onward)

### Kill Rules
| Condition | Action | Wait period |
|-----------|--------|-------------|
| CTR < 0.8% after 2,000 impressions | Pause the ad | No wait |
| Ad set: 3x CPA target, 0 conversions | Pause ad set | 3 days of spend |
| Ad set frequency > 3.5 with no CTR improvement | Refresh creative | After 7 days |
| Account-level CPM spikes > 40% week-over-week | Review targeting | Weekly |

### Scale Rules
| Condition | Action |
|-----------|--------|
| CTR > 2.5% consistently (3 days) | Increase ad set budget 20% |
| EPC own > $1.20 for 5 days | Increase campaign budget 30% |
| ROAS > 1.5 for 7 days | Duplicate winning ad set with new creative |

**NEVER:** Increase a budget by more than 30% in a single edit. It resets learning.
**NEVER:** Edit an ad set that is in Learning Phase (shown in Delivery column).

---

## KPIs & BENCHMARKS

| Metric | Kill | Hold | Scale |
|--------|------|------|-------|
| Ad CTR | < 0.8% | 0.8–1.5% | > 2.5% |
| Bridge page CTR to offer | < 25% | 25–40% | > 50% |
| EPC own (revenue / ad click) | < $0.80 | $0.80–$1.20 | > $1.20 |
| ROAS | < 1.0 | 1.0–1.3 | > 1.5 |
| CPM (US cold) | Benchmark | $15–$25 | — |
| CPC to bridge | Kill creative | $0.80–$1.50 | < $0.70 |

**North Star KPI:** EPC own (your revenue per dollar of ad spend, tracked via ClickMagick + ClickBank postback)

---

## DAILY TRACKING LOG TEMPLATE
*(Fill in each morning for previous day)*

```
DATE: __________
TOTAL SPEND: $______
IMPRESSIONS: ______
CLICKS TO BRIDGE: ______
CTR: ______%
BRIDGE → HOPLINK CLICKS: ______
BRIDGE CTR: ______%
SALES (from ClickBank): ______
REVENUE: $______
EPC OWN: $______  (Revenue / Bridge clicks)
ROAS: ______

TOP CREATIVE TODAY: __________  CTR: _____%
BOTTOM CREATIVE TODAY: __________  CTR: _____%

ACTIONS TAKEN:
- 
- 

NOTES:
```

---

## WEEK 3 ADDITIONS (if validation positive)

### YouTube Ads — Launch ($20/day)
- Platform: Google Ads
- Campaign type: Video — In-stream skippable
- Budget: $20/day, separate from Meta
- Creative: Video Script #3 "The Mechanism" (60s)
- Targeting:
  - Custom Intent: ["how to lose belly fat after menopause", "why can't I lose weight over 50", "metabolic health women 45", "ikaria lean belly juice", "weight loss after menopause"]
  - Placements: Dr. Berg channel, Thomas DeLauer channel, TODAY Show Health playlist
- Bridge page: advertorial-v1-mitochondrial.html (same page, different UTM source=youtube)
- KPI: CPV < $0.10, bridge CTR > 30%

---

## TIER-1 GEO NOTES

| Geo | CPM (est.) | Notes |
|-----|-----------|-------|
| US | $18–$28 | Highest CPM, best EPC. Primary volume. |
| CA | $12–$18 | Good quality, lower CPM. Worth including. |
| UK | $10–$16 | Strong health/wellness audience. Include. |
| AU | $10–$15 | Smaller audience but quality. Include. |

**Decision:** Run all 4 geos in same ad sets from Day 1. If US is clearly outperforming in Week 2, split into US-only ad set at higher budget and ROW ad set at lower budget.

---

## PIVOT PROTOCOL — If Ikaria underperforms

**Trigger:** EPC own < $0.80 for 14 consecutive days with > 300 hops sent

**Action:** Pause Ikaria campaigns. Launch Java Burn as Plan B.
- Java Burn EPC: $1.62 (vs. Ikaria $1.35)
- Java Burn Hop Conv Rate: 1.23% (vs. Ikaria 0.94%)
- Same bridge page framework — swap product name and offer link only
- Do NOT rebuild from scratch — reuse creative angles, update copy references only
