# After state: browser plugin bypasses the black box

> Plugin overlays HRS content directly on the OBT UI, captures engagement data, and feeds an AI personalization layer. No OBT cooperation required.

```mermaid
graph TD
    V[Vendors — hotels, chains, GDS] --> HRS
    HRS[HRS — content aggregator] --> OBT
    HRS -->|Exclusive content| PLUGIN
    OBT[OBT — online booking tool] --> TRAV[Traveler searches for hotels]

    PLUGIN[HRS browser plugin<br/>installed on corporate laptops] -->|Overlays HRS data<br/>on OBT UI| TRAV

    TRAV -->|Engagement data captured| PLUGIN
    PLUGIN -->|Behavioral data| AI[AI personalization model]
    AI -->|Individual recommendations| PLUGIN

    PLUGIN -->|Aggregated insights| TM[Travel manager dashboard]

    classDef vendor fill:#4a8bc2,color:#fff,stroke:#3670a0
    classDef hrs fill:#c68a2e,color:#fff,stroke:#a06e1e
    classDef obt fill:#777,color:#fff,stroke:#555
    classDef plugin fill:#2d9d78,color:#fff,stroke:#1d7a5c
    classDef ai fill:#7b6bb5,color:#fff,stroke:#5f519a
    classDef trav fill:#4a8bc2,color:#fff,stroke:#3670a0
    classDef tm fill:#a3dcc8,color:#0a2a1e,stroke:#5dbfa0

    class V vendor
    class HRS hrs
    class OBT obt
    class PLUGIN plugin
    class AI ai
    class TRAV trav
    class TM tm
```

### How the plugin activates

```mermaid
graph TD
    USER[Employee opens laptop] --> BROWSE[Normal browsing — plugin dormant]
    BROWSE --> NAV[Employee navigates to OBT booking page]
    NAV --> DETECT[Plugin detects OBT page]
    DETECT --> ACTIVATE[Plugin activates]
    ACTIVATE --> OVERLAY[Overlays HRS-exclusive labels and content]
    ACTIVATE --> CAPTURE[Captures search and click behavior]

    OVERLAY --> TRAV[Traveler sees enriched results]
    CAPTURE --> DATA[Engagement data stored — anonymized]

    classDef dormant fill:#777,color:#fff,stroke:#555
    classDef trigger fill:#c68a2e,color:#fff,stroke:#a06e1e
    classDef active fill:#2d9d78,color:#fff,stroke:#1d7a5c
    classDef output fill:#a3dcc8,color:#0a2a1e,stroke:#5dbfa0

    class USER,BROWSE dormant
    class NAV,DETECT trigger
    class ACTIVATE,OVERLAY,CAPTURE active
    class TRAV,DATA output
```

### AI personalization flow

```mermaid
graph TD
    D1[Search queries captured] --> MODEL
    D2[Hotel clicks and hovers captured] --> MODEL
    D3[Room rate selections captured] --> MODEL
    D4[Booking history captured] --> MODEL

    MODEL[AI model — learns individual preferences] --> REC[Personalized top 3 hotel recommendations]
    REC --> NEXT[Next search shows tailored results]

    MODEL --> NUDGE[Policy compliance nudges]
    NUDGE --> COMPLIANT[Traveler sees compliant alternatives]

    classDef input fill:#4a8bc2,color:#fff,stroke:#3670a0
    classDef model fill:#7b6bb5,color:#fff,stroke:#5f519a
    classDef output fill:#2d9d78,color:#fff,stroke:#1d7a5c
    classDef nudge fill:#c68a2e,color:#fff,stroke:#a06e1e

    class D1,D2,D3,D4 input
    class MODEL model
    class REC,NEXT output
    class NUDGE,COMPLIANT nudge
```

### What travel managers now see

```mermaid
graph TD
    PLUGIN[Plugin captures anonymized data] --> DASH[Travel manager dashboard]

    DASH --> I1[Which hotels employees actually prefer]
    DASH --> I2[Policy compliance rate per department]
    DASH --> I3[Sustainability label engagement]
    DASH --> I4[Booking patterns by region and role]

    classDef plugin fill:#2d9d78,color:#fff,stroke:#1d7a5c
    classDef dash fill:#c68a2e,color:#fff,stroke:#a06e1e
    classDef insight fill:#a3dcc8,color:#0a2a1e,stroke:#5dbfa0

    class PLUGIN plugin
    class DASH dash
    class I1,I2,I3,I4 insight
```

## Before vs. after comparison

| Dimension | Before | After |
|-----------|--------|-------|
| **Engagement data** | Zero. OBTs keep everything. | Full capture: searches, clicks, hovers, bookings, per individual traveler. |
| **New feature visibility** | 1-2+ years waiting for OBT adoption | Immediate. Plugin overlays new content directly, no OBT cooperation needed. |
| **Personalization** | None. Same generic results for everyone. | AI model generates individualized top 3 recommendations based on behavior. |
| **Travel manager visibility** | Internal surveys only. Slow, incomplete. | Real-time dashboard: preferences, policy compliance, sustainability engagement. |
| **Policy compliance** | ~40-45%, no way to nudge travelers | 15% improvement via non-blocking nudges showing compliant alternatives. |
| **Sustainability** | Labels invisible if OBT didn't implement them | 2.5% improvement in sustainability-compliant bookings via plugin overlay. |
| **Conversion rate** | Baseline | 12% improvement in hotel booking conversion. |
| **Customer retention** | At risk (two strategic accounts threatening to leave) | 60% improvement in retention among plugin customers. |
| **Plugin activity** | N/A | Dormant 99.99% of the time. Only active on OBT booking pages. |
| **Data privacy** | N/A | All engagement data anonymized. No non-travel data collected. Third-party pen testing passed. |

## Key architectural decisions

**Why a browser plugin, not an API-level solution:**
An API-level approach would require OBT cooperation, which was the exact bottleneck we were trying to bypass. The plugin operates at the browser layer, above the OBT, and can overlay content and capture data without any changes to the OBT's code.

**Why dormant by default, active only on OBT pages:**
This was a product decision driven by IT security requirements. Enterprise IT departments would not approve software that monitored all browsing activity. Making the plugin dormant 99.99% of the time and only activating on recognized OBT domains was what got IT sign-off.

**Why anonymized data shared with travel managers, not individual-level:**
Travel managers needed behavioral insights to improve policy compliance, but individual-level tracking would have raised privacy concerns and created internal resistance. The AI personalization happens on the HRS side; travel managers see aggregated trends, not individual profiles.

**Why the plugin UI matches each OBT's native look:**
If the plugin overlay looked visually different from the OBT, users would distrust it or ignore it. Designing the plugin to match each OBT's native UI meant travelers couldn't distinguish plugin-injected content from native content, which was critical for adoption and engagement.
