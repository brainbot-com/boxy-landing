# Boxy Landing Page

Landing page for **Boxy** - Independent AI Hardware

**Live Site:** https://brainbot-com.github.io/boxy-landing/

---

## Overview

This is the landing page for Boxy, a zero-configuration AI appliance that delivers ChatGPT-level AI completely locally. The page is designed with a bright, clean, architectural aesthetic inspired by IKEA minimalism.

### Key Features
- ✅ **Email capture** (hero + footer CTAs)
- ✅ **Analytics ready** (Matomo tracking placeholders)
- ✅ **Privacy-first** (no external dependencies except fonts)
- ✅ **Responsive design** (mobile, tablet, desktop)
- ✅ **Fast loading** (<2s target)
- ✅ **GitHub Pages** hosting

---

## Quick Start

### 1. Enable GitHub Pages

1. Go to **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** → **/ (root)**
4. Click **Save**

Your site will be live at: `https://brainbot-com.github.io/boxy-landing/`

### 2. Configure Email Collection

**Option A: Formspree (Recommended - Easy)**

1. Go to [Formspree.io](https://formspree.io)
2. Create free account
3. Create new form
4. Copy your form endpoint
5. Update `script.js`:
   ```javascript
   const CONFIG = {
       formEndpoint: 'https://formspree.io/f/YOUR_FORM_ID', // Replace this
   };
   ```

**Option B: Mailchimp**

1. Create Mailchimp account
2. Get API key and list ID
3. Update `script.js` with Mailchimp endpoint

**Option C: Custom Backend**

Create your own endpoint to handle POST requests with `{ email, formId, timestamp }`.

### 3. Set Up Matomo Analytics

**Self-Hosted (Recommended for privacy):**

1. Deploy Matomo on DigitalOcean/Hetzner (~€5/month)
2. Follow [Matomo installation guide](https://matomo.org/docs/installation/)
3. Create a new site in Matomo
4. Copy tracking URL and Site ID
5. Update `script.js`:
   ```javascript
   const CONFIG = {
       matomoUrl: 'https://analytics.yourdomain.com/',
       matomoSiteId: 1, // Your site ID
   };
   ```

**Cloud Alternative:**

Use [Plausible Analytics](https://plausible.io) for simpler setup (€9/month).

### 4. Custom Domain (Optional)

1. Buy domain (e.g., `boxy.ai`)
2. Add `CNAME` file to repository root:
   ```
   boxy.ai
   ```
3. Configure DNS:
   - Type: `CNAME`
   - Name: `@` (or `www`)
   - Value: `brainbot-com.github.io`
4. Wait for DNS propagation (~24 hours)
5. Enable **Enforce HTTPS** in GitHub Pages settings

---

## File Structure

```
boxy-landing/
├── index.html          # Main landing page
├── thank-you.html      # Post-signup confirmation page
├── style.css           # Bright, clean design system
├── script.js           # Form handling + analytics
├── README.md           # This file
└── CNAME              # (Optional) Custom domain
```

---

## Design System

### Colors
- **Primary Blue:** `#0066FF` - Bright, energetic
- **Accent Green:** `#00CC66` - Fresh, growth
- **Warm Cream:** `#FFFBF0` - Clean backgrounds
- **Dark Grey:** `#2A2A2A` - Headings

### Typography
- **Font:** Inter (Google Fonts)
- **Headings:** Bold, uppercase, large spacing
- **Body:** Regular weight, readable line-height

### Visual Style
- Generous white space
- Soft pastel accents
- Minimal decoration
- Clear hierarchy
- Mobile-first responsive

---

## Analytics Setup Guide

### Events Tracked
1. **Email signups** (hero form, footer form)
2. **Scroll depth** (25%, 50%, 75%, 100%)
3. **CTA clicks** (all buttons)
4. **FAQ interactions** (question opens)
5. **Page load performance** (slow loads flagged)

### Goals to Configure in Matomo
1. **Email Signup** - Triggered on `/thank-you.html` page view
2. **Scroll >75%** - High engagement indicator
3. **FAQ Engagement** - FAQ question opened

### UTM Tracking
All UTM parameters are automatically captured and stored:
- `utm_source` - Traffic source (e.g., "google", "reddit")
- `utm_medium` - Medium (e.g., "cpc", "organic")
- `utm_campaign` - Campaign name
- `utm_term` - Keywords (paid search)
- `utm_content` - Ad variant

Example URL:
```
https://boxy.ai/?utm_source=google&utm_medium=cpc&utm_campaign=launch-q1-2026
```

---

## Advertising Setup

### Google Ads

1. Create Google Ads account
2. Create **Search Campaign**
3. **Keywords:** "private AI", "local AI hardware", "ChatGPT alternative"
4. **Landing page:** `https://boxy.ai/?utm_source=google&utm_medium=cpc&utm_campaign=search-privacy`
5. **Budget:** €500-1,000 test
6. Track conversions via Matomo Goal ID

### Reddit Ads

1. Go to [Reddit Ads](https://ads.reddit.com)
2. Target subreddits: r/privacy, r/selfhosted, r/degoogle
3. **Ad format:** Native (looks like a post)
4. **Landing page:** `https://boxy.ai/?utm_source=reddit&utm_medium=cpc&utm_campaign=privacy-community`
5. **Budget:** €200-300 test

### A/B Testing Headlines

5 headline variants are documented in `VALUE_PROPOSITION.md`:
1. Privacy-first: "Your AI. Your Data. Zero Cloud Dependency."
2. Ownership: "Buy AI Once. Own It Forever. No Subscriptions."
3. Freedom: "ChatGPT Power. Zero Surveillance. Unlimited Usage."
4. Simplicity: "Private AI That Actually Works. Plug In. Scan QR. Done."
5. Economic: "Stop Renting AI. Own It for Less Than 2 Years of ChatGPT Plus."

Rotate these in ad copy and landing page hero to find winner.

---

## Local Development

1. Clone repository:
   ```bash
   git clone https://github.com/brainbot-com/boxy-landing.git
   cd boxy-landing
   ```

2. Serve locally:
   ```bash
   # Option 1: Python
   python -m http.server 8000
   
   # Option 2: Node.js
   npx serve
   
   # Option 3: VS Code Live Server extension
   ```

3. Open: `http://localhost:8000`

---

## Testing Checklist

### Pre-Launch
- [ ] Email form works (test submission)
- [ ] Thank you page loads correctly
- [ ] All links work (footer, external)
- [ ] Mobile responsive (test on phone)
- [ ] Load time < 2 seconds (Lighthouse)
- [ ] Analytics events fire (check console)
- [ ] Custom domain working (if applicable)
- [ ] SSL certificate active (HTTPS)

### Post-Launch
- [ ] Monitor conversion rate (target >15%)
- [ ] Check Matomo dashboard daily
- [ ] A/B test headline variants
- [ ] Optimize slow-loading elements
- [ ] Collect user feedback

---

## Performance Optimization

### Current Optimizations
- ✅ Static HTML/CSS/JS (no build step)
- ✅ Single external dependency (Google Fonts)
- ✅ No images in critical path
- ✅ Minimal JavaScript (9KB)
- ✅ CSS in single file (10KB)

### Further Optimizations (if needed)
- Self-host Inter font (remove Google Fonts dependency)
- Add service worker for offline support
- Lazy load below-fold sections
- Compress CSS/JS (minify)
- Add resource hints (`preconnect`, `prefetch`)

---

## Maintenance

### Weekly Tasks
- Check email submissions (localStorage backup)
- Review Matomo dashboard
- Monitor CPA (cost per acquisition)
- Respond to contact emails

### Monthly Tasks
- Update FAQ based on common questions
- Iterate on underperforming elements
- A/B test new messaging
- Review and optimize ad campaigns

---

## Support & Contact

- **Email:** hello@boxy.ai (update this!)
- **GitHub Issues:** [brainbot-com/localai](https://github.com/brainbot-com/localai/issues)
- **Main Project:** [Boxy Product Repo](https://github.com/brainbot-com/localai)

---

## License

Copyright © 2025 Brainbot Technologies. All rights reserved.

This landing page is proprietary. The underlying product (Boxy) uses open-source components - see main project repository for details.

---

## Changelog

### v1.0.0 (2025-11-04)
- Initial landing page launch
- Email capture forms (hero + footer)
- Value propositions, comparison table, FAQ
- Matomo analytics placeholder
- Thank you page
- Mobile responsive design
- GitHub Pages deployment ready

---

**Built with ❤️ in Europe. No tracking. No cookies. Just a simple landing page.**