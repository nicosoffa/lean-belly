# COMPLIANCE CHECKLIST — PRE-LAUNCH QA
## Meta 2026 + FTC Endorsement Guidelines + FDA DSHEA
## Owner: Compliance/QA | Sign off required before ANY creative goes live

---

## HOW TO USE THIS DOCUMENT

Every creative asset (ad copy, image, video, bridge page) must pass through this checklist BEFORE upload.
QA signs off with name + date on each item.
Any FAIL = asset goes back to copywriter/designer. Do not launch a flagged creative.

---

## PART 1 — META ADVERTISING POLICY (2026)

### 1.1 Prohibited Content — Automatic Rejection

Check each item. If ANY is present → FAIL, send back immediately.

| Check | Description | Status |
|-------|-------------|--------|
| [ ] | Before/after images or split weight transformation images | — |
| [ ] | Specific weight loss claims with numbers ("Lose 30 lbs in 30 days") | — |
| [ ] | Disease treatment/cure claims ("treats diabetes", "cures obesity") | — |
| [ ] | References to prescription medications by name (Ozempic, Wegovy, etc.) in ad copy | — |
| [ ] | Body shaming language or negative body image framing | — |
| [ ] | Claims that imply the product works without lifestyle changes (if phrased as miracle) | — |
| [ ] | Targeting under-18 audiences for weight loss content | — |
| [ ] | Shocking, sensationalist, or excessively graphic images | — |
| [ ] | Misleading claims that cannot be substantiated | — |
| [ ] | Hidden advertiser identity (must have clear disclosure) | — |

**Result:** PASS / FAIL
**QA Sign-off:** _________________ Date: _________

---

### 1.2 Restricted Content — Requires Careful Review

These are allowed but require specific conditions. Check each carefully.

| Check | Condition Required | Status |
|-------|-------------------|--------|
| [ ] Weight/health outcome claims | Must be framed as "supports", "may help", "some users report" — never absolute | — |
| [ ] Testimonials | Must include visible "Results may vary" or "Individual results may vary" | — |
| [ ] "Doctor" references | Cannot claim your product is medically endorsed unless it actually is | — |
| [ ] Urgency/scarcity language | Must be truthful ("limited stock" is OK only if stock is actually limited) | — |
| [ ] "Natural" or "safe" claims | Cannot imply zero side effects — add disclaimer to consult doctor | — |
| [ ] Energy/vitality claims | Acceptable — but cannot imply treatment of fatigue disorder | — |
| [ ] Age-targeting language | Can reference "women over 45" — cannot use exclusionary/offensive language | — |

**Result:** PASS / FAIL
**QA Sign-off:** _________________ Date: _________

---

### 1.3 Landing Page Consistency Rule (CRITICAL in 2026)
Meta AI (Andromeda system) scans landing pages for claim mismatches with ads.

| Check | Requirement | Status |
|-------|-------------|--------|
| [ ] | Ad copy claims match bridge page claims in tone and strength | — |
| [ ] | Bridge page makes no stronger claims than the ad | — |
| [ ] | Landing page URL is accessible (not geo-blocked, not down) | — |
| [ ] | Landing page loads in < 4 seconds on mobile | — |
| [ ] | Bridge page does not immediately redirect to another page | — |
| [ ] | Advertiser identity is visible on bridge page | — |

**Result:** PASS / FAIL
**QA Sign-off:** _________________ Date: _________

---

## PART 2 — FTC ENDORSEMENT GUIDELINES

### 2.1 Disclosure Requirements

| Check | Requirement | Status |
|-------|-------------|--------|
| [ ] | Advertising disclosure visible on bridge page — above fold on mobile | — |
| [ ] | Disclosure language clear and plain: "This article contains affiliate links. We may receive compensation..." | — |
| [ ] | Disclosure NOT buried in footer only (must be near top of page) | — |
| [ ] | If a testimonial is paid/incentivized — must be disclosed as such | — |
| [ ] | "Results may vary" or equivalent on ALL testimonials | — |
| [ ] | No fake editorial format that hides commercial intent (must be clearly labeled as sponsored/advertising) | — |

**Result:** PASS / FAIL
**QA Sign-off:** _________________ Date: _________

### 2.2 Testimonial & Claim Substantiation

| Check | Requirement | Status |
|-------|-------------|--------|
| [ ] | All specific results in testimonials are real (or labeled as fictional/composite) | — |
| [ ] | "Typical results" must reflect what most users actually experience | — |
| [ ] | Scientific claims have accessible backing (referenced research, not fabricated) | — |
| [ ] | No fake "news" publication names that could be confused with real media outlets | — |

**Result:** PASS / FAIL
**QA Sign-off:** _________________ Date: _________

---

## PART 3 — FDA DSHEA COMPLIANCE

### 3.1 Prohibited Claims (Dietary Supplement Rules)

Under DSHEA, dietary supplements CANNOT claim to diagnose, treat, cure, or prevent any disease.
This is absolute. No gray area.

| Check | PROHIBITED language — if present, FAIL | Status |
|-------|----------------------------------------|--------|
| [ ] | "Treats obesity" / "cures weight problem" | — |
| [ ] | "Prevents diabetes" / "reverses insulin resistance" | — |
| [ ] | "Fixes metabolic disease" | — |
| [ ] | "Clinically proven to cure" anything | — |
| [ ] | Any language implying FDA approval or medical treatment | — |

**Result:** PASS / FAIL
**QA Sign-off:** _________________ Date: _________

### 3.2 Required Disclaimer on Bridge Page

The following disclaimer MUST appear on the bridge page — verbatim or equivalent:

```
"These statements have not been evaluated by the Food and Drug Administration.
This product is not intended to diagnose, treat, cure, or prevent any disease."
```

| Check | Status |
|-------|--------|
| [ ] FDA disclaimer present on bridge page | — |
| [ ] Disclaimer is readable (not white text on white background, not < 9pt font) | — |
| [ ] Disclaimer present in HTML source (not just visually present via CSS trick) | — |

**Result:** PASS / FAIL
**QA Sign-off:** _________________ Date: _________

### 3.3 Allowed Language (Safe Harbor)

These phrasings are compliant under DSHEA and FTC:

| SAFE to use | NOT safe to use |
|-------------|----------------|
| "supports healthy metabolism" | "cures slow metabolism" |
| "may help maintain healthy weight" | "will cause weight loss" |
| "promotes energy and vitality" | "eliminates fatigue disorder" |
| "contains resveratrol, which supports..." | "clinically proven to cure..." |
| "some users report..." | "all users will experience..." |
| "individual results may vary" | "guaranteed to work" |

---

## PART 4 — PRE-LAUNCH BRIDGE PAGE AUDIT

Run this on EVERY bridge page before ads go live. Open in incognito mode, on mobile device.

| Check | Status |
|-------|--------|
| [ ] Page loads in < 4 seconds on mobile 4G (test at pagespeed.web.dev) | — |
| [ ] Advertising disclosure visible without scrolling on mobile | — |
| [ ] FDA disclaimer visible in footer | — |
| [ ] "Results may vary" on all testimonials | — |
| [ ] No before/after images | — |
| [ ] No specific weight loss number promises | — |
| [ ] CTA button links to correct HopLink (with tid parameter) | — |
| [ ] Meta Pixel fires on PageView (verify in Meta Pixel Helper extension) | — |
| [ ] ClickMagick pixel fires (verify in ClickMagick > Tracking Links > Stats) | — |
| [ ] BridgeClick event fires when CTA is clicked | — |
| [ ] Page displays correctly on iPhone (Safari) and Android (Chrome) | — |
| [ ] Images load (no broken image icons) | — |
| [ ] No console errors (open browser DevTools > Console) | — |

**Final status:** APPROVED / NOT APPROVED
**QA Sign-off:** _________________ Date: _________

---

## PART 5 — VIDEO CREATIVE AUDIT

| Check | Status |
|-------|--------|
| [ ] No before/after transformation footage | — |
| [ ] No specific weight loss number claims in audio | — |
| [ ] Hook works on mute (first 3 seconds must communicate without sound) | — |
| [ ] Captions present (required for accessibility, increases watch rate ~85%) | — |
| [ ] Video does not show medical procedures or needles | — |
| [ ] No actors in white coats implying medical endorsement (unless clearly labeled) | — |
| [ ] Video renders correctly in 9:16 and 1:1 formats | — |
| [ ] Audio quality is clear — no background noise | — |

**Result:** PASS / FAIL
**QA Sign-off:** _________________ Date: _________

---

## PART 6 — POST-LAUNCH MONITORING

Review these weekly:

| Check | Frequency |
|-------|-----------|
| Meta Ad Account — any policy flags or restricted account warnings | Daily |
| Ad disapproval reasons — document and categorize | Daily |
| Bridge page — check for any content changes that might affect compliance | Weekly |
| ClickBank refund rate — flag if > 12% in any rolling 7-day period | Weekly |
| New FTC/FDA enforcement actions in supplement space | Monthly |

---

## ESCALATION PROTOCOL

**If a creative receives a disapproval:**
1. Do NOT re-upload the same creative unchanged
2. Identify the specific policy it violated (Meta gives a reason code)
3. Send to Copywriter/Designer with the specific reason
4. Document in Disapproval Log (below)
5. Only re-upload after the specific issue is fixed and QA has re-approved

**If the ad account receives a warning:**
1. STOP all ad launches immediately
2. Review all active ads against this checklist
3. Pause any ad that has even a minor compliance risk
4. Wait 48 hours before relaunching
5. Notify Media Buyer immediately

---

## DISAPPROVAL LOG

| Date | Ad ID | Disapproval Reason | Fix Applied | Re-approved |
|------|-------|-------------------|-------------|-------------|
| | | | | |
| | | | | |
| | | | | |
