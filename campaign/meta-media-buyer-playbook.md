# Meta Ads Media Buyer Playbook
## Ikaria Lean Belly Juice — healthreport.today
**Date:** May 2026 | **Budget:** $50/day Week 1 → $70/day Week 2+

---

## PRE-LAUNCH CHECKLIST (Before Opening Ads Manager)

- [ ] Business Manager created at business.facebook.com
- [ ] Ad Account added to Business Manager (billing method attached)
- [ ] healthreport.today domain DNS live and resolving
- [ ] Bridge page accessible at https://healthreport.today
- [ ] ClickMagick account active ($49/month plan minimum)
- [ ] ClickBank HopLink ready: `https://theikariajuice.com/?hopId=fc9cf72c-12b2-4b90-9c01-ac9eaf8e1ba5`

---

## STEP 1 — DOMAIN VERIFICATION IN BUSINESS MANAGER

> Meta requires domain verification before running conversion campaigns.

1. Go to **Business Manager → Brand Safety → Domains**
2. Click **Add Domain** → enter `healthreport.today`
3. Select **DNS Verification** method
4. Copy the TXT record Meta gives you (format: `facebook-domain-verification=XXXXXXXXXXXX`)
5. Go to your DNS provider (Hostinger) → DNS Zone → Add TXT record:
   - **Type:** TXT
   - **Name:** @ (root)
   - **Value:** paste the full facebook-domain-verification string
   - **TTL:** 3600
6. Back in Business Manager → click **Verify Domain**
7. DNS propagation can take up to 24h — run this step first, before anything else

---

## STEP 2 — CREATE THE META PIXEL

### 2.1 Create the Pixel

1. Go to **Events Manager** (business.facebook.com/events_manager)
2. Click **+ Connect Data Sources → Web**
3. Select **Meta Pixel** → click **Connect**
4. Name: `HealthReport - Lean Belly`
5. Enter website URL: `https://healthreport.today`
6. Click **Continue**

### 2.2 Install the Pixel on the Page

Choose **Install Code Manually**:

1. Copy your **Pixel ID** (16-digit number, e.g. `1234567890123456`)
2. Open the file: `bridge-pages/advertorial-MASTER.html`
3. Find the text: `XXXXXXXXXXXXXXXXXX`
4. Replace with your Pixel ID — it appears in **2 places** (base code + noscript)
5. Do the same in `index.html` at the repo root
6. Re-deploy to GitHub / upload to healthreport.today hosting

**Your Pixel base code block is already embedded in the page** — just the ID swap is needed.

### 2.3 Verify Pixel Fires Correctly

1. Install **Meta Pixel Helper** Chrome extension
2. Open https://healthreport.today in Chrome
3. Pixel Helper should show: **PageView ✓**
4. Scroll to 30% of the page → should show: **ViewContent ✓**
5. Click the CTA button → should show: **BridgeClick ✓** (custom event)
6. If events don't fire: check browser console for JS errors

### 2.4 Configure Aggregated Event Measurement (AEM)

> Required for iOS 14+ conversion tracking.

1. In Events Manager → **Aggregated Event Measurement**
2. Click your domain `healthreport.today`
3. Set event priority order (top = highest priority):
   1. Purchase (from ClickBank postback — will configure via CAPI below)
   2. ViewContent
   3. PageView
4. Save

### 2.5 Conversions API (CAPI) — ClickMagick Bridge

> This is how purchase conversions get back to Meta without relying on cookies.

1. In Events Manager → **Settings** → **Conversions API**
2. Select **Set up through a partner integration**
3. Look for **ClickMagick** in the partner list → follow OAuth flow
4. If ClickMagick is not listed, use **Manual setup** and enter:
   - Access Token: (generate in Events Manager → Settings → Generate Access Token)
   - Save this token — you'll paste it into ClickMagick's CAPI settings
5. In ClickMagick → Settings → Conversions API → paste Access Token + Pixel ID

**ClickBank → ClickMagick postback** (already in tracking-setup-guide.md):
```
https://api.clickmagick.com/api/postback?cid=[tid]&type=s&amount=[amount]
```
Paste this URL in ClickBank → Account → My Account → Instant Notification URL (IPN)

---

## STEP 3 — CAMPAIGN SETUP IN ADS MANAGER

### CAMPAIGN 1: MITOCHONDRIAL (PRIMARY — 70% of budget)

#### Campaign Level

| Setting | Value |
|---|---|
| Campaign Name | `LBJ - Mito - CBO - [DATE]` |
| Objective | **Sales** (Conversions) |
| Buying Type | Auction |
| Campaign Budget Optimization | **ON** |
| Daily Budget | **$35/day** (Week 1) |
| Bid Strategy | **Lowest Cost** |
| Special Ad Category | None |

> If the account is new (<50 purchases in 7 days), use **Traffic** objective temporarily for the first 3-5 days to build signal, then switch to Sales.

---

#### Ad Set 1: Broad Interest — Women 45+

| Setting | Value |
|---|---|
| Ad Set Name | `Mito - Broad - W45+ - US` |
| Conversion Event | **ViewContent** (Week 1) → switch to Purchase once 50 events/week |
| Conversion Location | Website |
| **Countries** | United States, Canada, United Kingdom, Australia |
| **Age** | 44 – 65+ |
| **Gender** | Women |
| **Detailed Targeting** | LEAVE BLANK (Meta Advantage+ Audience) |
| Advantage+ Audience | ON — Suggestion: "Weight loss, Healthy Living, Women's Health" |
| Placements | **Advantage+ Placements** (let Meta decide) |
| Schedule | Run continuously starting today |

---

#### Ad Set 2: Interest Stack — Metabolism/Hormones

| Setting | Value |
|---|---|
| Ad Set Name | `Mito - Interest - Metabolism - US` |
| (Same geo/age/gender as above) | |
| **Detailed Targeting** | Interests: "Metabolism", "Menopause", "Women's Health", "Weight loss", "Dr. Oz", "Prevention Magazine" |
| Advantage+ Audience | ON |
| Everything else | Same as Ad Set 1 |

---

#### Ads Inside Each Ad Set (3 per ad set = 6 ads total for Campaign 1)

**Ad 1 — Video Hook "The Blocker" (30s)**

| Setting | Value |
|---|---|
| Ad Name | `Mito-V1-TheBlocker` |
| Format | Single Video |
| Video | Upload Script #1 video (from meta-ad-copy-v1.md) |
| Primary Text | "Doctors are baffled by this strange morning ritual that's helping women over 45 finally lose stubborn belly fat — without dieting or exercise..." |
| Headline | `The Ceramide Discovery That's Changing Everything` |
| Description | `Free report reveals the real reason you can't lose weight` |
| CTA Button | **Learn More** |
| Destination URL | `https://healthreport.today?utm_source=meta&utm_medium=cpc&utm_campaign=mito&utm_content=v1-blocker&utm_term=broad` |
| URL Parameters | Add `cm_id={{YOUR_CLICKMAGICK_TRACKING_LINK_ID}}` |

**Ad 2 — Static Image "Ceramide Mechanism"**

| Setting | Value |
|---|---|
| Ad Name | `Mito-I1-Ceramide` |
| Format | Single Image |
| Image | Mechanism visual (the mitochondria/ceramide graphic from the page) |
| Primary Text | "Scientists at Keio University found ONE compound blocking the mitochondria of women over 45. Here's the natural ingredient that flushes it out in days..." |
| Headline | `Why Your Metabolism is Broken (It's Not Your Fault)` |
| Description | `Read the full discovery →` |
| CTA Button | **Learn More** |
| Destination URL | `https://healthreport.today?utm_source=meta&utm_medium=cpc&utm_campaign=mito&utm_content=i1-ceramide&utm_term=broad` |

**Ad 3 — Static Image "Karen Transformation"**

| Setting | Value |
|---|---|
| Ad Name | `Mito-I2-Karen` |
| Format | Single Image |
| Image | Brunette woman lifestyle photo (hero image from page) |
| Primary Text | `"I lost 34 lbs after my doctor told me to try THIS instead of another diet. I'm 54 and I feel better than I did at 35." — Karen L., Nashville TN` |
| Headline | `54-Year-Old Nashville Mom Drops 34 lbs` |
| Description | `See what she did differently →` |
| CTA Button | **Learn More** |
| Destination URL | `https://healthreport.today?utm_source=meta&utm_medium=cpc&utm_campaign=mito&utm_content=i2-karen&utm_term=broad` |

> Duplicate all 3 ads into Ad Set 2 — change `utm_term=broad` to `utm_term=interest`

---

### CAMPAIGN 2: GRANDMA/ENERGY (SECONDARY — 30% of budget)

#### Campaign Level

| Setting | Value |
|---|---|
| Campaign Name | `LBJ - Grandma - CBO - [DATE]` |
| Objective | Sales (or Traffic — same logic as above) |
| CBO | ON |
| Daily Budget | **$15/day** (Week 1) |
| Bid Strategy | Lowest Cost |

---

#### Ad Set 3: Broad — Women 50+

| Setting | Value |
|---|---|
| Ad Set Name | `Grandma - Broad - W50+ - US` |
| Age | 50 – 65+ |
| Gender | Women |
| Geo | US, CA, UK, AU |
| Targeting | Advantage+ (no detailed targeting) |

---

#### Ad Set 4: Interest — Grandparents/Family

| Setting | Value |
|---|---|
| Ad Set Name | `Grandma - Interest - Family - US` |
| Detailed Targeting | "Grandparents", "Family", "Healthy aging", "Active seniors" |
| Everything else | Same as Ad Set 3 |

---

#### Ads for Campaign 2 (3 per ad set = 6 ads)

**Ad 4 — Video "Grandma Energy" (45s)**

| Setting | Value |
|---|---|
| Ad Name | `Fam-V1-GrandmaEnergy` |
| Primary Text | "She could barely walk up the stairs. 3 months later she's chasing her grandkids at the park. She's 61." |
| Headline | `What Grandma Added to Her Morning Routine` |
| CTA | Learn More |
| URL | `https://healthreport.today?utm_source=meta&utm_medium=cpc&utm_campaign=fam&utm_content=v1-grandma&utm_term=broad` |

**Ad 5 — Static "Diane Story"**

| Setting | Value |
|---|---|
| Ad Name | `Fam-I1-Diane` |
| Primary Text | "My granddaughter asked why I couldn't run with her at the park. That was my wake-up call. 90 days later — I beat her to the swings." |
| Headline | `A Grandma's Promise She Actually Kept` |
| URL | `https://healthreport.today?utm_source=meta&utm_medium=cpc&utm_campaign=fam&utm_content=i1-diane&utm_term=broad` |

**Ad 6 — Static "Energy Before/After Story"**

| Setting | Value |
|---|---|
| Ad Name | `Fam-I2-Energy` |
| Primary Text | "No more 2pm crashes. No more skipping family dinners because I'm too tired. This one change made all the difference." |
| Headline | `Women Over 50 Are Getting Their Energy Back` |
| URL | `https://healthreport.today?utm_source=meta&utm_medium=cpc&utm_campaign=fam&utm_content=i2-energy&utm_term=broad` |

> Duplicate all 3 into Ad Set 4 — change `utm_term=broad` to `utm_term=family`

---

## STEP 4 — CLICKMAGICK TRACKING LINKS

For each ad destination URL, wrap it in a ClickMagick tracking link:

1. Log into ClickMagick → **Tracking Links → New Link**
2. Set the destination URL to: `https://healthreport.today` (with UTM params)
3. Enable **TrueTracking** → paste your ClickBank Postback URL
4. Copy the ClickMagick link (e.g. `https://clkmg.com/YOURID/mito-broad`)
5. Use this ClickMagick link as the ad destination in Meta — OR use your domain URL and pass `cm_id` as a URL parameter

**Recommended structure:**
```
Meta Ad → ClickMagick Link → healthreport.today (bridge) → theikariajuice.com (HopLink)
```

ClickMagick captures the click → passes `cm_id` → ClickBank fires IPN on sale → ClickMagick fires postback → Meta registers Purchase conversion

---

## STEP 5 — COMPLIANCE FINAL CHECK BEFORE PUBLISHING

- [ ] No "before/after" image pairs in ads
- [ ] No disease claims ("treats obesity", "cures diabetes")
- [ ] No income claims
- [ ] Advertorial page does NOT look like a news article (no fake news logos)
- [ ] "This is an advertisement" disclosure visible on bridge page
- [ ] Individual results disclaimer present ("Results not typical")
- [ ] CTA goes to bridge page, bridge page goes to vendor — NO direct link to ClickBank in ads
- [ ] Ad creative matches bridge page (bridge consistency rule)
- [ ] All testimonials are attributed to real identifiers (name, location)

---

## STEP 6 — LAUNCH SEQUENCE

### Day 1 (Today)
1. Complete domain verification (Step 1)
2. Create Pixel (Step 2)
3. Build all 4 ad sets + 12 ads (Steps 3)
4. Set Campaign 1 + Campaign 2 budgets: **$35 + $15 = $50/day total**
5. Submit all ads for review
6. Set up ClickMagick tracking links (Step 4)
7. Verify Pixel fires on healthreport.today

### Day 2-3 (Learning Phase)
- Do NOT edit budgets, targeting, or creatives during learning phase
- Meta needs 50 optimization events before exiting learning — patience required
- Monitor: CTR, CPM, Link Click Cost only (no conversion data yet)

### Day 4-7 (First Kill/Keep Decision)
Apply kill rules from `campaign/meta-campaign-structure.md`:

| Metric | Threshold | Action |
|---|---|---|
| CTR (link) | < 0.8% after 2,000 impressions | Kill the ad |
| Ad Set CPA | > 3x target CPA with 0 conversions | Kill the ad set |
| Ad Set CTR | Top performer | Duplicate + increase budget 20% |

### Day 7 (Week 1 Review)
- If EPC on ClickMagick ≥ $0.80 → increase daily budget to $70
- If EPC < $0.80 with < 300 hops → wait (not enough data)
- If EPC < $0.80 with > 300 hops → review copy/angle, not budget

---

## STEP 7 — PIXEL ID PLACEHOLDER REPLACEMENT

**CRITICAL — Do this before going live:**

In both files:
- `bridge-pages/advertorial-MASTER.html`
- `index.html`

Find and replace:
```
XXXXXXXXXXXXXXXXXX  →  [YOUR 16-DIGIT PIXEL ID]
YOUR_CLICKMAGICK_ID  →  [YOUR CLICKMAGICK ACCOUNT SUBDOMAIN]
```

After editing, re-upload or re-deploy to healthreport.today.

---

## QUICK REFERENCE — KEY NUMBERS

| Item | Value |
|---|---|
| HopLink | `https://theikariajuice.com/?hopId=fc9cf72c-12b2-4b90-9c01-ac9eaf8e1ba5` |
| Bridge Page URL | `https://healthreport.today` |
| Week 1 Daily Budget | $50/day ($35 Mito + $15 Grandma) |
| Week 2+ Daily Budget | $70/day (if EPC ≥ $0.80) |
| Target CPA | ≤ $143 (APV = $143.06) |
| Target EPC | ≥ $0.80 (breakeven) → $1.35 (Ikaria avg) |
| Kill Threshold CTR | < 0.8% after 2k impressions |
| Scale Trigger | ROAS > 1.3 sustained 3 days → +20% budget |
| Plan B Offer | Java Burn (EPC $1.62) — switch if EPC < $0.80 for 14 days + 300 hops |

---

*Media Buyer Playbook — Ikaria Lean Belly Juice — healthreport.today — May 2026*
