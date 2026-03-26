# Before state: black-box value chain

> Every layer hoards its data. HRS has zero visibility into traveler behavior. New features take 1-2+ years to reach end users.

```mermaid
graph TD
    V[Vendors — hotels, chains, GDS] --> HRS
    HRS[HRS — content aggregator] --> OBT
    OBT[OBTs — online booking tools] --> TRAV[Travelers book hotels]

    classDef vendor fill:#4a8bc2,color:#fff,stroke:#3670a0
    classDef hrs fill:#c68a2e,color:#fff,stroke:#a06e1e
    classDef obt fill:#d94f4f,color:#fff,stroke:#b33a3a
    classDef trav fill:#777,color:#fff,stroke:#555

    class V vendor
    class HRS hrs
    class OBT obt
    class TRAV trav
```

### The data black-box problem

```mermaid
graph TD
    HRS[HRS sends hotel content to OBT] --> OBT[OBT displays results to traveler]
    OBT --> TRAV[Traveler searches, clicks, compares, books]

    TRAV -->|Engagement data| OBT
    OBT -->|Shared back?| BLOCK[No — OBTs keep all engagement data]
    BLOCK --> HRS_BLIND[HRS has zero visibility into traveler behavior]

    HRS_BLIND --> P1[Cannot personalize content]
    HRS_BLIND --> P2[Cannot measure feature adoption]
    HRS_BLIND --> P3[Product decisions based on guesswork]

    classDef normal fill:#4a8bc2,color:#fff,stroke:#3670a0
    classDef block fill:#d94f4f,color:#fff,stroke:#b33a3a
    classDef pain fill:#e8a0a0,color:#2a0a0a,stroke:#c27070

    class HRS,OBT,TRAV normal
    class BLOCK,HRS_BLIND block
    class P1,P2,P3 pain
```

### The feature adoption delay

```mermaid
graph TD
    HRS_FEAT[HRS launches new feature] --> REQ[Request OBT to support it]
    REQ --> OBT_QUEUE[OBT adds to their backlog]
    OBT_QUEUE --> WAIT[Wait for OBT dev cycle]
    WAIT --> LIVE[Feature finally visible to travelers]

    WAIT -.->|Timeline| DELAY[1-2+ years in some cases]

    classDef start fill:#2d9d78,color:#fff,stroke:#1d7a5c
    classDef step fill:#c68a2e,color:#fff,stroke:#a06e1e
    classDef bad fill:#d94f4f,color:#fff,stroke:#b33a3a
    classDef result fill:#777,color:#fff,stroke:#555

    class HRS_FEAT start
    class REQ,OBT_QUEUE step
    class WAIT,DELAY bad
    class LIVE result
```

### What travel managers experienced

```mermaid
graph TD
    TM[Travel manager wants to know] --> Q1{What hotels do employees prefer?}
    TM --> Q2{Are travelers booking within policy?}
    TM --> Q3{Which sustainability options get selected?}

    Q1 --> ANS[No data — OBT will not share]
    Q2 --> ANS
    Q3 --> ANS

    ANS --> SURVEY[Only option: run internal surveys]
    SURVEY --> STALE[Slow, incomplete, outdated results]

    classDef tm fill:#4a8bc2,color:#fff,stroke:#3670a0
    classDef question fill:#c68a2e,color:#fff,stroke:#a06e1e
    classDef block fill:#d94f4f,color:#fff,stroke:#b33a3a
    classDef workaround fill:#e8a0a0,color:#2a0a0a,stroke:#c27070

    class TM tm
    class Q1,Q2,Q3 question
    class ANS block
    class SURVEY,STALE workaround
```

## Pain points summary

| Problem | Impact |
|---------|--------|
| **OBTs don't share engagement data** | HRS cannot see what travelers search, click, compare, or prefer. Product decisions based on aggregate booking volumes and anecdotes. |
| **New features take 1-2+ years to reach travelers** | OBTs have hardcoded logic. Getting them to add support for a new content type (e.g. sustainability certification) requires their dev cycle. One case took 2+ years for a single name addition. |
| **Travel managers have no visibility** | Cannot see what their employees actually book or prefer. Only option is internal surveys, which are slow and incomplete. |
| **No personalization possible** | Without behavioral data, every traveler sees the same generic results. No ability to learn individual preferences. |
| **Competitive content stays invisible** | HRS-exclusive features (negotiated rates, sustainability programs) remain hidden if OBTs don't implement them. |
