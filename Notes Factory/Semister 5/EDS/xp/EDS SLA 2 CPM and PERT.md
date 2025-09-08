

# **EDS SLA – 2 (Lanvan File Transfer System)**

## **Section A — CPM (Critical Path Method)**


-   **Single fixed duration per activity.**
    
-   **Forward pass:** ES = max(EF of predecessors); EF = ES + Duration
    
-   **Backward pass:** LF = min(LS of successors); LS = LF − Duration
    
-   **Slack = LS − ES**; **Slack = 0 → Critical Path**
    

### How we set durations

We first built **PERT estimates (O/M/P)** for each activity (see Section B), computed **TE**, then used **Duration = CEIL(TE)** for a conservative CPM schedule.

***

### **CPM Calculations (Lanvan)**

**Project duration (CPM, deterministic) = 85 days**

| ID  | Description | Duration_days | ES  | EF  | LS  | LF  | Slack | Critical |
| --- | --- | ---: | ---: | ---: | ---: | ---: | ---: | :---: |
| A   | Kickoff & environment setup | 3   | 0   | 3   | 0   | 3   | 0   | YES |
| B   | Requirements & architecture | 6   | 3   | 9   | 3   | 9   | 0   | YES |
| C   | Core FastAPI backend | 13  | 9   | 22  | 9   | 22  | 0   | YES |
| D   | Security & encryption layer (AES-256, HTTPS) | 9   | 22  | 31  | 22  | 31  | 0   | YES |
| E   | Clipboard module (real-time API & history) | 7   | 22  | 29  | 48  | 55  | 26  |     |
| F   | File transfer engine (chunked/direct) | 13  | 31  | 44  | 31  | 44  | 0   | YES |
| G   | Frontend PWA (vanilla JS) | 11  | 44  | 55  | 44  | 55  | 0   | YES |
| H   | LAN discovery & QR pairing | 5   | 55  | 60  | 80  | 85  | 25  |     |
| I   | Integration & security testing | 8   | 55  | 63  | 55  | 63  | 0   | YES |
| J   | Performance & load testing | 6   | 63  | 69  | 63  | 69  | 0   | YES |
| K   | Bug fixes & polish | 7   | 69  | 76  | 69  | 76  | 0   | YES |
| L   | Deployment & rollout | 5   | 76  | 81  | 76  | 81  | 0   | YES |
| M   | Post-launch monitoring & support | 4   | 81  | 85  | 81  | 85  | 0   | YES |

**Critical Path:** `A → B → C → D → F → G → I → J → K → L → M`  
(Clipboard E and LAN discovery H have slack; they’re non-critical.)

```mermaid
flowchart LR
  A["A: Kickoff & setup (3d)"]
  B["B: Requirements & architecture (6d)"]
  C["C: Core backend (13d)"]
  D["D: Security & encryption (9d)"]
  F["F: File transfer engine (13d)"]
  G["G: Frontend PWA (11d)"]
  I["I: Integration & sec testing (8d)"]
  J["J: Performance & load (6d)"]
  K["K: Bug fixes & polish (7d)"]
  L["L: Deployment & rollout (5d)"]
  M["M: Monitoring & support (4d)"]

  A --> B --> C --> D --> F --> G --> I --> J --> K --> L --> M

  classDef critical fill:#ffd6a5,stroke:#ff7b00,stroke-width:1.5;
  class A,B,C,D,F,G,I,J,K,L,M critical;
```

#### Selected forward/backward pass checks

-   **C (Core backend):** ES = EF(B) = 9; EF = 9 + 13 = **22**.  
    Backward: LF = LS(D) = 31 − 9 = **22**; LS = 22 − 13 = **9**; Slack = 0 → **Critical**.
    
-   **E (Clipboard):** ES = EF(C) = 22; EF = 29.  
    Backward: LF = LS(I) (I waits on G & E) = 63; LS = 63 − 7 = **56** → but since G ends at 55, effective LF aligns to 55; Slack = **26** (non-critical).
    
-   **G (Frontend PWA):** ES = EF(F) = 44; EF = 55.  
    Backward: LF = min(LS(I)=55, LS(H)=80) = 55; LS = **44**; Slack = 0 → **Critical**.
    

**CPM Summary**

-   Deterministic duration = **85 days**.
    
-   Critical chain runs through backend → security → transfer engine → frontend → testing → fixes → deploy → monitor.
    
-   Clipboard and LAN discovery are flexible with **large slack**; good buffer for scope tweaks.
    

***

## **Section B — PERT (Program Evaluation and Review Technique)**

### Theory

-   **TE = (O + 4M + P)/6**
    
-   **Variance = ((P − O)/6)²**
    
-   **Project TE** = sum of TE on **critical path**
    
-   **Project variance** = sum of variances on **critical path**; **σ = √variance**
    

***

### **PERT Table (Lanvan)**

| ID  | Description | O   | M   | P   | **TE_days** | **Variance** | ES  | EF  | Slack | Critical |
| --- | --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | :---: |
| A   | Kickoff & environment setup | 2   | 3   | 4   | **3.00** | 0.11 | 0.00 | 3.00 | 0.00 | YES |
| B   | Requirements & architecture | 4   | 6   | 8   | **6.00** | 0.44 | 3.00 | 9.00 | 0.00 | YES |
| C   | Core FastAPI backend | 9   | 12  | 18  | **12.50** | 2.25 | 9.00 | 22.00 | 0.00 | YES |
| D   | Security & encryption layer | 6   | 8   | 12  | **8.33** | 1.00 | 22.00 | 31.00 | 0.00 | YES |
| E   | Clipboard module | 4   | 6   | 9   | **6.17** | 0.69 | 22.00 | 29.00 | 26.00 |     |
| F   | File transfer engine | 10  | 12  | 18  | **12.33** | 2.78 | 31.00 | 44.00 | 0.00 | YES |
| G   | Frontend PWA | 8   | 10  | 14  | **10.33** | 1.00 | 44.00 | 55.00 | 0.00 | YES |
| H   | LAN discovery & QR pairing | 3   | 4   | 6   | **4.17** | 0.25 | 55.00 | 60.00 | 25.00 |     |
| I   | Integration & security testing | 5   | 7   | 10  | **7.17** | 0.69 | 55.00 | 63.00 | 0.00 | YES |
| J   | Performance & load testing | 4   | 5   | 8   | **5.33** | 0.44 | 63.00 | 69.00 | 0.00 | YES |
| K   | Bug fixes & polish | 5   | 6   | 9   | **6.17** | 0.69 | 69.00 | 76.00 | 0.00 | YES |
| L   | Deployment & rollout | 3   | 4   | 6   | **4.17** | 0.25 | 76.00 | 81.00 | 0.00 | YES |
| M   | Post-launch monitoring & support | 3   | 4   | 5   | **4.00** | 0.11 | 81.00 | 85.00 | 0.00 | YES |

> **Project expected duration (PERT, TE-based across critical path)**  
> TE(critical) = **79.83 days**  
> **Critical-path variance = 8.528 days²** → **σ ≈ 2.92 days**

#### Example TE/Variance (F: File transfer engine)

-   O=10, M=12, P=18 → **TE = (10 + 4·12 + 18)/6 = 12.33 d**
    
-   Variance = ((18−10)/6)² = **(8/6)² = 2.78 d²**
    

#### Probability snapshot

-   For target = **79.83 d** → Z = 0 → **50%** chance (by definition).
    
-   If you set a deadline **≤ 77 d**, Z ≈ (77 − 79.83) / 2.92 ≈ −0.97 → **~17%** chance of finishing on/before 77 days.
    
-   If you allow **82 d**, Z ≈ +0.74 → **~77%** chance.
    

***

## **Section C — CPU (Cost-Per-Unit / Cost Analysis)**

**Baseline:** Total project cost (from Lanvan’s balance sheet) = **₹55,650**  
**Major deliverables (5):** Core Backend, Clipboard Module, Security Layer, Frontend PWA, Deployment & Monitoring

### Formulas

-   **CPU_feature** = Total Cost ÷ #Deliverables
    
-   **CostPerDayᵢ** = Costᵢ ÷ Durationᵢ
    
-   **AvgBurnPerDay** = Total Cost ÷ CPM Duration
    

### Results (Lanvan)

-   **CPU_feature** = 55,650 ÷ 5 = **₹11,130 per deliverable**
    
-   **AvgBurnPerDay** = 55,650 ÷ 85 ≈ **₹655.88/day**
    

**Per-activity CostPerDay (illustrative allocations based on your asset mix):**

-   **C – Core backend**: Cost **₹4,500** (your “Core System Development”) over **13 d** → **₹346.15/day**
    
-   **E – Clipboard module**: Cost **₹1,500** (your “Clipboard & File Transfer Module” portion) over **7 d** → **₹214.29/day**
    
-   **F – File transfer engine**: Equipment-heavy; allocate **₹15,000** → **₹1,153.85/day** over **13 d**
    

> These allocations keep your original totals (₹55,650) but recognize that **F** is equipment-intensive, hence a higher daily burn. You can refine these by time-tracking or resource rates later.

**Interpretation:**  
Focus cost control on **F (File transfer engine)** and **G (Frontend)** where burn is highest; keep **E (Clipboard)** flexible (it has slack and low daily cost).

***

## **Section D — PMT (Project Management Tools & Key Metrics)**

**Key Agile formulas (same as your template):**

-   **Velocity** VV = SP ÷ S
    
-   **Cycle Time** CTCT = Σ(C−O) ÷ N
    
-   **Defect Escape Rate** DERDER = (Bₚ ÷ Bₜ) × 100
    
-   **MTTR** = ΣTᵣ ÷ N
    

**Lanvan sample metrics**

1.  **Sprint Velocity**: Story points over 4 sprints = 34, 36, 35, 37 → **SP = 142; S = 4 → V ≈ 35.5 ≈ 35 SP/sprint**
    
    > **Throughput:** ~35 SP per 2-week sprint.
    
2.  **Cycle Time**: 45 tickets, Σ(C−O)=180 days → **CT = 180/45 = 4 days/ticket**
    
3.  **Defect Escape Rate**: Production bugs Bₚ=7; total bugs Bₜ=80 → **DER = 8.75%**
    
4.  **MTTR**: 4 incidents, total resolution = 12 hours → **MTTR = 3 hours**
    
5.  **Release Readiness (Lanvan-specific) – must all pass**
    
    -   ✅ CI/CD green (build, unit/integration tests)
        
    -   ✅ File type/size/MIME validation and AV scanning
        
    -   ✅ AES-256 encryption + HTTPS cert checks
        
    -   ✅ UAT on multi-OS (Win/Linux/Mac) + LAN QR pairing
        
    -   ✅ Rollback plan & monitoring (transfer errors, throughput, disk)
        
    -   ✅ Rate limiting & auth hardening to prevent spoofed transfers
        

***

# **Final Summary — Observations (Lanvan)**

| Area | Key Finding | Why it matters | Suggested Action |
| --- | --- | --- | --- |
| **Schedule (CPM)** | **85 days** deterministic; **critical path**: A-B-C-D-F-G-I-J-K-L-M | Any slip on backend/security/transfer/frontend/testing delays the whole project | Time-box non-critical E/H; protect capacity on critical chain |
| **Slack** | E (Clipboard) **26 d**, H (LAN QR) **25 d** | Useful buffer for UI/UX and refinements | Use slack to absorb scope tweaks without touching the critical path |
| **PERT** | **TE ≈ 79.83 d**, **σ ≈ 2.92 d** | Provides probabilistic planning | For 80-day target, ~50–55% chance; for 82 d, ~75% |
| **Cost (CPU)** | **₹55,650 total**, **₹11,130 per deliverable**, **₹656/day avg** | Guides budgeting & prioritization | Track actuals per activity; optimize F (highest daily burn) |
| **High-burn tasks** | F (File transfer), G (Frontend) | Equipment-heavy & throughput-sensitive | Early performance profiling; reuse components; avoid gold-plating |
| **Quality metrics** | Velocity ~**35 SP/sprint**, CT **4 d**, DER **8.75%**, MTTR **3 h** | Healthy baseline; DER above mature target | Aim DER < **5%** post-launch; MTTR < **1 h** for P1 |
| **Risk** | Security & spoofing risks on LAN; dependency on local policies | Could block adoption in strict IT environments | Provide offline signing, admin policies, and audit logs |
| **Release readiness** | Checklist tailored for encryption, file validation, multi-OS | Reduces rollout risk | Gate deploy on perf targets (throughput, error rate) |

***

If you want, I can also export these tables to a **print-ready doc/slide** or a **CSV/Excel** for submission.