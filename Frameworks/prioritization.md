# Prioritization: Browser Plugin with Engagement Analytics

> How I prioritized a 0-to-1 product that didn't fit the company's identity, across three simultaneous build tracks (content overlay, data capture, AI personalization), while managing a small team that was already firefighting.

---

## The Core Tension

This wasn't a feature on an existing product. This was a new product category for a company that had little experience shipping client-side softwares. Every prioritization decision had to juggle three competing pressures:

1. **What to build first in the plugin itself** (overlay, data capture, personalization, nudging -- all valuable, but a small team can't do everything at once)
2. **Which customers to launch with** (large strategic accounts vs. smaller ones with easier IT departments)
3. **Which stakeholder to unblock first** (internal leadership skepticism, client IT resistance, or travel manager enthusiasm)

Standard feature prioritization frameworks assume you already have permission to build. Here, I had to prioritize *earning permission* alongside the actual build.

---

## Framework: Impact vs. Trust Sequencing

RICE worked for ongoing feature prioritization at the company (we used it for the broader ecosystem roadmap, aligned to the annual north-star metric which was conversion rate). But for this 0-to-1 product, the primary constraint wasn't engineering effort. It was **trust**. Each capability we shipped had to build enough trust with the next stakeholder to unlock the next phase.

So I sequenced the build around a trust ladder:

### The Trust Ladder

| Phase | What We Built | Trust It Earned | Who It Unlocked |
|-------|--------------|----------------|-----------------|
| **Phase 1: Content overlay** | Plugin displays HRS-exclusive labels (sustainability, negotiated rates) on the OBT UI. No data capture yet. | "This thing works. It shows useful info. It doesn't break anything." | Travel managers become active champions. Internal leadership sees a working demo. |
| **Phase 2: Engagement data capture** | Plugin captures search queries, clicks, hovers, room rate selections. All anonymized. | "The data is real. We can finally see what travelers do. And IT confirmed it's safe." | Client IT departments approve installation (after pen testing). Travel managers share insights internally. |
| **Phase 3: AI personalization** | ML model trained on engagement data. Top 3 recommendations per search personalized to individual traveler. | "This is differentiated. Competitors can't replicate this because they don't have the behavioral data." | Sales team can pitch the plugin as a retention tool. Leadership sees it as a strategic asset, not a side project. |
| **Phase 4: Policy nudging** | Non-blocking nudge when a traveler selects a hotel above approved rate or with high carbon footprint. Compliant alternatives shown. | "This drives measurable compliance improvements. We can quantify ROI for the customer." | Expansion to additional customers and OBTs. Renewal conversations anchored in compliance data. |

### Why This Order Mattered

**Phase 1 had to come first** because it was the lowest-risk proof of concept. No data collection, no privacy concerns, and little IT security review. Just: "Here's useful information overlaid on the page you're already using." This got travel managers excited and gave internal leadership something tangible to evaluate.

**Phase 2 had to come before Phase 3** because the AI model needed data to train on. But Phase 2 also required the most external trust (IT pen testing, privacy documentation, data anonymization architecture). By the time we reached Phase 2, we already had travel manager buy-in from Phase 1, which gave us internal champions to push back on IT resistance.

**Phase 3 before Phase 4** because personalization was the value differentiator (what makes the plugin worth keeping), while nudging was the ROI justifier (what makes the plugin worth paying for). You need people to love the product before you add friction, even helpful friction.

---

## Prioritization Within Each Phase

Within each phase, I used a simplified RICE approach aligned to the company's north-star metric (conversion rate) to sequence individual features.

### Phase 1 Example: Which Content to Overlay First

| Content Type | Reach | Impact on Conversion | Confidence | Effort | Decision |
|-------------|-------|---------------------|------------|--------|----------|
| Sustainability program labels | High (all hotels) | Medium (growing traveler awareness) | High (data exists in our APIs) | Low (label overlay) | **Build first** -- most visible proof that we show what OBTs don't |
| Negotiated rate indicators | High (exclusive content) | High (directly affects booking decision) | High | Low | **Build first** -- strong value prop |
| Loyalty program eligibility | Medium (chain hotels only) | High (travelers care deeply, especially in DACH) | Medium (requires vendor-specific mapping) | Medium | **Build second** -- more complex mapping |
| Hotel quality scores | Low-medium | Medium | Low (scoring methodology in flux) | High | **Defer** -- not enough confidence in the data |

### Phase 4 Example: Nudge Design Prioritization

The rate policy compliance was running at 40-45% when customers expected 60-65%. We had no prior data on what friction would do to booking behavior, so we prioritized based on gap severity and friction risk.

| Nudge Type | Reach | Impact on Compliance | Risk of User Friction | Decision |
|-----------|-------|---------------------|----------------------|----------|
| Rate policy nudge (over-budget hotel) | High | High (biggest compliance gap) | Medium (could annoy travelers) | **Build first** -- tested with one business unit of a large conglomerate before broad rollout |
| Preferred hotel nudge (hotels part of exclusive programs) | High | High | Medium (annoyed travel managers) | **Build first** -- tested with one business unit of a large conglomerate before broad rollout |
| Sustainability nudge (high-carbon hotel) | Medium | Medium (growing priority) | Low (non-blocking, informational) | **Build second** -- lower friction, easier to validate |
| Location nudge (hotel far from meeting venue) | Low | Low | High (assumptions about "better" location are risky) | **Defer** -- too many edge cases, low confidence |

For the rate policy and preferred hotel nudges specifically, we designed the concept, ran designs through customer sessions for feedback, and then launched to as a controlled test. Observed behavior, refined messaging to avoid creating escalation burden on the travel team, then rolled out broadly. Result: 15% improvement in policy compliance.

---

## The Bigger Prioritization: This Product vs. the Existing Backlog

The ecosystem team was small (2 PMs, ~10 devs) and already firefighting daily operational issues: vendor integration bugs, OBT onboarding timelines, customer escalations. Building a brand new product on top of that required explicit trade-offs.

### How I Made the Case

**Quantified the churn risk.**
Two large strategic accounts were threatening to leave. The sales team confirmed the revenue at stake. I framed the plugin as a retention play: "If we lose these two accounts, the revenue impact is X. The plugin directly addresses the problems they've been raising for the past year."

**Positioned it as revenue protection + revenue generation.**
- Revenue protection: retain at-risk strategic accounts by solving the visibility and compliance problems they'd been complaining about
- Revenue generation: once live, the plugin becomes a differentiator that the sales team can use in competitive deals. No competitor has this data.

**Scoped the build to be parallel, not blocking.**
The plugin build didn't require the entire dev team. The core ecosystem work (vendor integrations, OBT onboardings) continued. I carved out a subset of the team for the plugin and managed the two tracks in parallel.

---

## Handling the Metric Drop (Post-Launch Prioritization)

After launch, the plugin's conversion rate improvement climbed to 20%, then dropped back down. This became an urgent prioritization question: debug the drop or continue building new features?

**How I triaged:**
1. Checked dashboard integrity first (was the data itself correct?)
2. Segmented by customer, OBT, and geography to isolate where the drop happened
3. Checked for recent internal changes (new releases, config changes)
4. Checked for OBT-side changes

**Root cause:** One OBT had overhauled their UI. The plugin couldn't load on the new version.

**Decision:** Paused Phase 4 feature work, fixed the OBT compatibility within 10 days, redesigned the plugin for the new OBT UI, and established a monitoring protocol to detect future OBT UI changes before they break the plugin.

**Lesson incorporated into prioritization:** Added a standing "OBT UI monitoring" item to every sprint. Pen testing was already repeated every 3-4 months for major releases; OBT compatibility checks were added to the same cadence.

---

## What I'd Do Differently

1. **Build OBT UI monitoring from day one.** We designed the plugin to visually match each OBT's native UI, but we didn't anticipate that OBTs would change their UI without notice. A lightweight check for OBT DOM changes would have caught the break before users did.

2. **Run the nudge experiment earlier.** We waited until Phase 4 for nudging because we wanted adoption first. But the compliance gap (40-45% vs. 60-65% target) was the most quantifiable ROI metric. Running a small nudge pilot in Phase 2 alongside data capture would have given us ROI numbers to accelerate IT approvals at other customers.

3. **Formalize the customer launch sequence.** We launched with strategic accounts first because they had the most pain. But their IT departments were also the strictest. Launching first with a mid-size customer (easier IT, faster approval) to build a case study, then approaching strategic accounts with proof, might have been faster overall.

---

*All company names, client names, and partner names have been anonymized. Metrics and decision frameworks are accurate as applied.*
