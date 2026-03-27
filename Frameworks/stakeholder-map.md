# Stakeholder Map: Browser Plugin with Engagement Analytics

> This was our only product that required installation on an end user's machine. Every stakeholder group had a different reason to be skeptical, and the order in which I addressed their concerns determined whether the product shipped or died in committee.

---

## Why This Project Had Unusual Stakeholder Complexity

Most product initiatives face resistance from one direction: maybe engineering pushes back on scope, or leadership questions the business case. This project faced resistance from three directions simultaneously, and the resistance was existential, not incremental:

- **Internal leadership** questioned whether the company should build this kind of product at all (identity challenge)
- **Client IT departments** questioned whether they could trust a new vendor's software on employee machines (security challenge)
- **OBT partners** were implicitly being bypassed, which risked the company's most important channel relationships (political challenge)

Meanwhile, one stakeholder group was enthusiastically in favor: **travel managers**. The entire stakeholder strategy was built around weaponizing that enthusiasm to overcome the other three objections.

---

## Stakeholder Map

### Internal Leadership (C-suite, VPs of Product)

**What they cared about**: Revenue growth, competitive positioning, not taking unnecessary risk on the company's core business model.

**Their concern with this project**: "We are a content aggregator. We are an API-first, server-side business. Building client-side software that sits on people's laptops is not who we are. What if it fails publicly? What if it damages our reputation with OBT partners? What if IT departments blacklist us?"

**How I managed them**:
- Did not pitch this as "let's build a browser plugin." Pitched it as "here's a way to capture the engagement data we've been asking OBTs for years and never getting, while simultaneously solving the feature adoption delay that's costing us competitive positioning." The plugin was the delivery mechanism, not the pitch.
- Built the revenue case with the sales team: projected upside from interested customers, plus quantified churn risk from two large strategic accounts threatening to leave. Made it a revenue protection argument, not a product innovation argument.
- Showed that the team could build this in parallel with existing ecosystem work, not as a replacement for it. No pausing of vendor integrations or OBT onboardings.
- After the first successful pen test, shared the results with leadership proactively. Security credibility was the unlock that moved leadership from "maybe" to "proceed."

**What they needed from me**: A business case framed in revenue terms (not product terms), proof that it wouldn't damage existing channel relationships, and evidence that the team could handle the additional scope.

**Alignment mechanism**: Business case document with revenue projections from sales, quarterly updates on pilot results, pen test reports shared proactively.

---

### Sales Team

**What they cared about**: Pipeline, competitive differentiation, having something new to sell, protecting existing accounts.

**Their concern with this project**: Initially minimal. Sales saw the plugin as exactly what two strategic accounts had been asking for. Their concern was timing: "When can I tell these accounts it's ready? They're threatening to leave."

**How I managed them**:
- Made sales a co-owner of the business case. The revenue projections that convinced leadership came from the sales team's confirmed pipeline, not my estimates. This gave them ownership of the initiative.
- Set clear expectations about launch timeline and what would be available in each phase. No overselling capabilities that weren't built yet.
- After launch, the plugin gave sales a completely new competitive angle: "No other content aggregator can show you what your travelers actually prefer. No one else has this data." Sales used this in every competitive deal.
- The plugin also became a retention tool: renewal conversations could now be anchored in concrete data ("Here's what your travelers did this quarter, here's how compliance improved, here's the ROI").

**What they needed from me**: A launch timeline they could share with at-risk accounts, talking points for competitive positioning, and post-launch data they could use in renewal conversations.

**Alignment mechanism**: Joint customer calls, shared ownership of revenue projections, post-launch data summaries for account reviews.

---

### Travel Managers (at Client Organizations)

**What they cared about**: Knowing what their employees actually do during hotel bookings, improving policy compliance, reducing travel costs, sustainability reporting.

**Their concern with this project**: Almost none. This was the one stakeholder group that was enthusiastically in favor from day one. They had been voicing the exact problems the plugin solved on every weekly and biweekly call for months.

**How I managed them**:
- Armed them with information to sell internally. When their IT departments pushed back, travel managers had the arguments: "This solves the visibility gap we've been complaining about for years. Here's what it does, here's what it doesn't do, here's the pen test report."
- Involved them in the nudge design process. Ran nudge concepts through customer sessions for feedback before building. Their input shaped the messaging (non-blocking, suggestion-based, not punitive) and the configuration (nudge behavior configurable at organization and OBT level).
- Shared engagement data with them post-launch via a dashboard view. This made them permanent advocates: every quarter, they had new data to show their own leadership about traveler behavior and policy compliance.

**What they needed from me**: A product that actually solved their problems (not a watered-down version), the ability to configure it to their organization's policies, and data they could report upward.

**Alignment mechanism**: Weekly/biweekly calls (existing cadence), customer feedback sessions during nudge design, post-launch dashboard sharing.

**Why they were the strategic lynchpin**: Travel managers were the only stakeholder who could push from the inside at client organizations. Internal leadership could approve the build, but only travel managers could convince client IT departments to install the plugin. Every stakeholder management move was designed to give travel managers what they needed to win their internal battles.

---

### Client IT Departments

**What they cared about**: Security, compliance, not introducing risk onto corporate devices, not setting a precedent for unknown vendors installing software.

**Their concern with this project**: "This company has never shipped client-side software. They're an API provider. Why should we trust a browser extension from them? What data does it collect? What happens when it's running? Does it have access to browsing history? Has it been tested by anyone credible?"

**How I managed them**:
- Conducted two full third-party penetration tests before the first launch. For each major release (every 3-4 months), repeated pen testing to maintain trust. This was expensive and time-consuming, but it was the only way to earn IT credibility from zero.
- Documented exactly what the plugin does and doesn't do in a format IT departments could review:
  - Active only on recognized OBT booking pages. Dormant rest of the time.
  - No non-travel data collection. No browsing history, no personal information.
  - All engagement data anonymized and travel-specific only.
  - Plugin cannot access any data outside the OBT booking context.
- Let travel managers fight the internal battle first. By the time IT got the formal request, their travel management colleagues had already been advocating for it. IT's job shifted from "should we do this?" to "is this safe enough?" -- a much easier question to answer with pen test results in hand.

**What they needed from me**: Third-party security validation, clear documentation of data collection scope, and assurance that the plugin wouldn't create ongoing security overhead for their team.

**Alignment mechanism**: Pen test reports shared directly, data collection documentation, technical Q&A sessions during onboarding, repeat testing every 3-4 months.

---

### OBT Partners (Online Booking Tools)

**What they cared about**: Their platform, their users, their roadmap, their data.

**Their concern with this project**: The plugin overlays content on top of the OBT's UI without their involvement. In theory, this could be seen as hostile: we're modifying their product experience without permission. In practice, it was more nuanced.

**How I managed them**:
- Did not ask for permission (we didn't need it -- the plugin operates at the browser layer, not the API layer). But also did not antagonize. The plugin was designed to enhance the OBT experience, not compete with it.
- Designed the plugin UI to visually match each OBT's native UI so seamlessly that users couldn't tell which elements were plugin-injected. This was a deliberate product decision: if the overlay looked foreign, OBTs and even customers might have pushed back. If it looked native, it was a non-issue.
- Monitored OBT UI changes to maintain compatibility (learned this the hard way after the metric drop incident where an OBT UI overhaul broke the plugin).
- Over time, an interesting dynamic emerged: once OBTs saw the plugin gaining traction, they started proactively adding HRS-requested features to avoid being bypassed. The plugin gave us negotiating leverage we'd never had before. The relationship shifted from "please add our sustainability label to your code" to "we're already showing it, but we'd rather you support it natively."

**What they needed from me**: Nothing explicitly. But I needed to ensure the plugin didn't create friction in the OBT relationship. The UI matching strategy and the non-aggressive positioning were the key.

**Alignment mechanism**: No direct engagement on the plugin. Monthly OBT partnership calls (existing cadence) continued as normal. The plugin was positioned as complementary, not competitive.

---

### Dev Team (~10 developers, shared with ecosystem work)

**What they cared about**: Interesting technical challenges, sustainable pace, clear requirements, not being pulled between two competing priorities.

**Their concern with this project**: "We're already stretched thin on ecosystem work (vendor integrations, OBT onboardings, customer escalations). Now we have to build a completely new product category we've never worked in? Browser extensions? ML models?"

**How I managed them**:
- Carved out a dedicated subset of the team for the plugin build. The rest continued ecosystem work. Clear ownership, no context-switching between the two tracks.
- The plugin presented genuinely interesting technical challenges that the team hadn't encountered before: browser extension architecture, real-time DOM overlay matching different OBT UIs, engagement data pipelines, ML model integration. This made it a motivating project, not a burden.
- Used the phased trust ladder to keep scope manageable. Each phase had a clear, shippable outcome. The team wasn't staring at a 12-month monolith; they were shipping something tangible every few months.
- When the metric drop happened (OBT UI change broke the plugin), I prioritized the fix immediately, paused feature work, and didn't blame anyone. The fix took 10 days. Then we established monitoring to prevent recurrence.

**What they needed from me**: Clear separation between plugin work and ecosystem work, phased scope that felt achievable, and fast triage when things broke.

**Alignment mechanism**: Separate standups for plugin and ecosystem tracks, shared sprint cadence, direct access to me for blockers.

---

### Account Managers

**What they cared about**: Customer satisfaction, retention, upselling, maintaining relationships.

**Their concern with this project**: "Will this create friction with IT at my accounts? Will the plugin break something and make me look bad? Can I even explain what a browser plugin is to a travel procurement team?"

**How I managed them**:
- Created talking points for every customer conversation about the plugin: what it does, what it doesn't do, why IT should trust it, what the pen test showed.
- Involved account managers in the customer launch sequence. They knew which accounts had receptive IT departments and which would be a harder sell. Their input shaped the rollout order.
- Post-launch, the plugin gave account managers something they'd never had: concrete behavioral data to bring into quarterly business reviews. Instead of "we think your travelers prefer X," they could say "here's the data showing your travelers prefer X, and here's how compliance improved since the plugin went live."

**What they needed from me**: Talking points, launch sequence input, and post-launch data they could use in customer conversations.

**Alignment mechanism**: Account manager briefings before each customer launch, shared access to engagement dashboards, joint quarterly business reviews.

---

## How Stakeholder Dynamics Shifted Over the Project Lifecycle

| Phase | Who Had the Loudest Voice | My Focus |
|-------|--------------------------|----------|
| **Pre-approval** (building the case) | Internal leadership | Revenue framing, churn risk, "data strategy initiative not a software product" |
| **Phase 1: Content overlay** | Travel managers + leadership | Working demo, travel manager enthusiasm as proof of demand |
| **Phase 2: Data capture + pen testing** | Client IT departments | Pen test coordination, privacy documentation, data scope clarity |
| **Phase 3: AI personalization** | Sales team | Competitive positioning, "no one else has this data" |
| **Phase 4: Policy nudging** | Travel managers + account managers | Nudge design feedback, compliance data as renewal anchor |
| **Post-launch expansion** | OBT partners (indirectly) | Monitoring OBT UI changes, maintaining compatibility, leveraging new negotiating position |

---

## Key Takeaway

The conventional stakeholder management approach is to align everyone upfront and then build. That doesn't work when your product challenges organizational identity. For the plugin, I had to sequence stakeholder buy-in the same way I sequenced the build: earn trust with one group, use that trust to unlock the next group, repeat.

Travel managers were the strategic fulcrum. They were the only stakeholder who sat inside the client organization and cared enough about the problem to fight for the solution internally. Every decision I made about what to build first, how to position the product, and what data to share was designed to arm travel managers for their internal battles.

---

*All company names, client names, and partner names have been anonymized. Stakeholder dynamics and management approaches are accurate as experienced.*
