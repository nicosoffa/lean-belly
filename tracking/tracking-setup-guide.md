# TRACKING & ATTRIBUTION SETUP GUIDE
## Ikaria Lean Belly Juice | ClickMagick + ClickBank + Meta Pixel
## Complete setup: ~3-4 hours for Tech/Tracker role

---

## STACK OVERVIEW

```
[Meta Ad]
    |
    | UTM parameters
    v
[ClickMagick Tracking Link]
    |
    | Redirects to bridge page
    v
[Your Bridge Page — yourdomain.com/article]
    |  Meta Pixel fires: PageView
    |  ClickMagick pixel fires
    |
    | User clicks CTA button
    | Meta fires: BridgeClick (custom event)
    v
[Your HopLink — theikariajuice.com/?hopId=...&tid=CM_CLICK_ID]
    |
    v
[ClickBank Vendor Sales Page]
    |
    | On purchase:
    v
[ClickBank fires Postback URL → ClickMagick]
    |
    v
[ClickMagick records sale — tied to original click source]
```

---

## STEP 1 — DOMAIN & HOSTING SETUP

### Recommended: Cloudflare Pages (free) or Hostinger ($3/month)

**Hostinger Setup:**
1. Purchase hosting plan (Business or Premium — both support custom domain)
2. Register domain at Namecheap or Porkbun (avoid Godaddy — slower DNS)
3. Point domain nameservers to Hostinger
4. Upload bridge page HTML files via File Manager or FTP

**Domain naming strategy:**
- Use generic health editorial names — NOT your brand, NOT "ikaria"
- Examples: healthdailyreport.com / womenshealthinsights.com / metabolicwellness.net
- Check availability: namecheap.com/domains/registration/results/?domain=healthdailyreport

**Page speed requirements:**
- Target: LCP < 2.5 seconds on mobile (4G connection simulation)
- Test at: pagespeed.web.dev after upload
- The HTML files provided are already optimized for speed (no heavy frameworks)
- Do NOT add WordPress plugins, Elementor, or page builders — they kill LCP

**File paths:**
```
yourdomain.com/                     → (optional homepage/redirect)
yourdomain.com/article-1            → advertorial-v1-mitochondrial.html
yourdomain.com/article-2            → advertorial-v2-grandma.html
```

---

## STEP 2 — CLICKMAGICK SETUP

### Account
- Plan: Starter ($49/month) — sufficient for < 10,000 clicks/month
- Sign up at: clickmagick.com
- Note: ClickMagick is a legitimate tool. Do not use it for deceptive redirects.

### Create Tracking Links

**Link 1 — Campaign 1 (Mitochondrial Angle)**
- Name: `ikaria-mito-meta`
- Primary URL: `https://yourdomain.com/article-1`
- Tracking pixel: Add your ClickMagick pixel code to article-1 page (see Step 4)
- Tracking params: Enable "Pass click ID to destination URL"
- UTM template: `utm_source=meta&utm_medium=cpc&utm_campaign=mito&utm_content={{ad_name}}&utm_term={{adset_name}}`

**Link 2 — Campaign 2 (Grandma/Energy Angle)**
- Name: `ikaria-fam-meta`
- Primary URL: `https://yourdomain.com/article-2`
- Same setup as Link 1, campaign tag = `fam`

### ClickMagick Click ID Parameter
When ClickMagick redirects to your bridge page, it appends a click ID.
You need to pass this click ID through to ClickBank so the postback can attribute the sale.

**In your HopLink CTA button on the bridge page, replace:**
```html
<a href="https://theikariajuice.com/?hopId=fc9cf72c-12b2-4b90-9c01-ac9eaf8e1ba5">
```

**With:**
```html
<a href="https://theikariajuice.com/?hopId=fc9cf72c-12b2-4b90-9c01-ac9eaf8e1ba5&tid=[REPLACE_WITH_CLICKID]" id="cta-link">
```

Then add this JavaScript to the bridge page (before </body>):
```html
<script>
  // Pull ClickMagick click ID from URL and inject into HopLink
  (function() {
    var params = new URLSearchParams(window.location.search);
    var cmClickId = params.get('cm_click_id') || params.get('tid') || '';
    if (cmClickId) {
      var ctaLinks = document.querySelectorAll('a.cta-button');
      ctaLinks.forEach(function(link) {
        var url = new URL(link.href);
        url.searchParams.set('tid', cmClickId);
        link.href = url.toString();
      });
    }
  })();
</script>
```

---

## STEP 3 — CLICKBANK POSTBACK SETUP

### Where to configure
1. Log into ClickBank affiliate account
2. Go to: Account Settings → My Account → Tracking
3. Find "Instant Notification URL" / Postback URL field

### Postback URL to enter
```
https://api.clickmagick.com/api/postback?cid=[tid]&type=s&amount=[amount]
```

**Parameters explained:**
- `[tid]` = the click ID you passed through (ClickBank replaces this with the actual value)
- `[amount]` = commission amount ClickBank replaces this with actual payout
- `type=s` = sale event

### Test the postback
After setup, use ClickBank's "Test IPN/Postback" feature to send a test notification.
Confirm it appears in ClickMagick under "Conversions."

**Common issue:** If postback doesn't fire, check that your HopLink is correctly passing the `tid` parameter. Use ClickMagick's "Click Log" to verify the parameter is present on each click.

---

## STEP 4 — META PIXEL INSTALLATION

### Replace pixel ID in both HTML files
In both bridge page HTML files, find this line:
```javascript
fbq('init', 'XXXXXXXXXXXXXXXXXX');
```

Replace `XXXXXXXXXXXXXXXXXX` with your actual Meta Pixel ID.
Find your Pixel ID: Meta Business Manager → Events Manager → Your Pixel → Pixel ID

### Events to fire

**1. PageView** (already in the code — fires on page load)
```javascript
fbq('track', 'PageView');
```

**2. BridgeClick** (fires when user clicks CTA button)
Add this to the bridge page, inside the `<script>` tag, after the Pixel init:
```javascript
document.querySelectorAll('a.cta-button').forEach(function(btn) {
  btn.addEventListener('click', function() {
    fbq('trackCustom', 'BridgeClick');
  });
});
```

**3. ViewContent** (optional — fires after 30 seconds of reading, signals engaged visitors)
```javascript
setTimeout(function() {
  fbq('track', 'ViewContent', {content_name: 'Advertorial V1'});
}, 30000);
```

### Event Match Quality
After 1-2 days of traffic:
- Check: Meta Events Manager → Your Pixel → Event Match Quality
- Target: 6+ out of 10 for PageView
- If below 6: implement Conversions API (server-side) — instructions below

### Conversions API (Server-Side) — Optional but recommended
Increases event match quality and survivability vs. iOS ad blockers.
Easiest implementation for a static HTML page: use Cloudflare Workers or a simple server-side proxy.
For now, start with browser pixel only — add CAPI in Week 2 if event match quality is low.

---

## STEP 5 — UTM PARAMETER STRUCTURE

All ads must use consistent UTM parameters for accurate attribution.

**Template:**
```
utm_source=meta
utm_medium=cpc
utm_campaign=[ANGLE]        → mito | fam
utm_content=[CREATIVE_ID]   → img_metabolism_01 | vid_blocker_01
utm_term=[ADSET_ID]         → broad_women45 | interest_menopause
```

**Example full URL in Meta Ad:**
```
https://cm.clickmagick.com/ikaria-mito-meta?utm_source=meta&utm_medium=cpc&utm_campaign=mito&utm_content=img_metabolism_01&utm_term=broad_women45
```

Use ClickMagick's link, not your domain directly — ClickMagick handles the click ID injection.

---

## STEP 6 — UPTIME MONITORING

**Tool:** UptimeRobot (free tier)
- Sign up at uptimerobot.com
- Add HTTP monitor for each bridge page URL
- Alert: Email + SMS on downtime
- Check interval: every 5 minutes

This is critical. A bridge page that's down during active ad spend = pure loss.

---

## STEP 7 — DAILY VERIFICATION CHECKLIST

Run this every morning before reviewing Meta data:

- [ ] Bridge pages loading correctly (open in incognito, mobile + desktop)
- [ ] LCP still < 2.5s (check PageSpeed Insights 2x/week)
- [ ] ClickMagick click log showing today's clicks
- [ ] ClickBank sales appearing in ClickMagick (check yesterday's conversions)
- [ ] Meta Pixel firing in Events Manager (active today)
- [ ] No account flags/warnings in Meta Business Manager

---

## REPORTING DASHBOARD SETUP

### ClickMagick Report View
Configure columns: Clicks | Unique Clicks | Conversions | EPC | Revenue | Cost (manual input)

### Meta Ads Manager Custom Columns
Add these columns to your default view:
- Impressions
- Reach
- CPM
- Link Clicks (to bridge page)
- CTR (Link)
- CPC (Link)
- Amount Spent
- Frequency

**Custom Metrics to create:**
- "Bridge CTR": (ClickMagick HopLink clicks / Meta Link Clicks) — calculate manually daily
- "EPC Own": (ClickBank revenue / Meta Link Clicks) — calculate manually daily

---

## TROUBLESHOOTING

| Problem | Likely Cause | Fix |
|---------|-------------|-----|
| Sales showing in ClickBank but NOT in ClickMagick | Postback URL wrong | Re-check Step 3 — verify [tid] parameter syntax |
| No clicks in ClickMagick but Meta shows clicks | ClickMagick link not used as Ad URL | Replace ad URL with ClickMagick link |
| Meta Pixel shows 0 events | Pixel ID not replaced | Check HTML file — replace XXXXXXXXXXXXXXXXXX |
| Bridge page slow (LCP > 3s) | Images too large or external scripts | Compress images to WebP < 150kb, defer non-critical scripts |
| High CPM, low delivery | Ad set too narrow | Expand age range or remove interest constraints |
| Ad disapproved | Policy violation in creative | Review compliance checklist — adjust copy/image |
