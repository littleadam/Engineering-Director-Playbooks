# Engineering Director Playbooks

**By Arul Muruga A D** · Technical Project Manager & Group Technical Architect · HCL Technologies  
PMP · Google Certified GenAI Leader · 16 years engineering leadership · Cisco ODC

---

## What This Is

This is a collection of **operational playbooks** developed through 15+ years of delivering large-scale engineering programmes at Cisco's Offshore Development Centre under real commercial accountability.

These are not textbook frameworks. Every playbook here has been tested in production — against live incidents, real client escalations, missed sprint goals, and budget conversations with Delivery Heads. They have been refined through failure as much as success.

**Who this is for:**
- Engineering Managers moving into Director-scope roles
- Technical Project Managers looking to lead at a higher level
- Directors of Engineering who want a second opinion on their operational model
- New engineering leaders who want a framework to start from, not reinvent

---

## Playbooks

```
engineering-director-playbooks/
├── README.md                            ← You are here
├── 01-incident-response-playbook.md     ← P1 protocol, MTTA/MTTR, Yellow Flag system
├── 02-sprint-health-framework.md        ← Sprint governance, capacity planning, DoD/DoR
├── 03-ai-transformation-programme.md   ← Running AI adoption across multiple teams
├── 04-team-onboarding-template.md       ← 30-60-90 day plan for engineers and TLs
├── 05-director-communication-model.md   ← How to communicate at Director level daily
├── 06-budget-and-headcount.md           ← Building business cases, managing costs
└── 07-stakeholder-management.md         ← Multi-stakeholder model, client governance
```

---

## Playbook 1: Incident Response — Overview

**Full document:** [`01-incident-response-playbook.md`](01-incident-response-playbook.md)

The incident response system I run across my 24×7 cloud operations team maintains **MTTA ≤ 1 minute** and **MTTR ≤ 24 hours** continuously. The key design principles:

### 3-Tier Incident Classification

| Priority | Definition | Response SLA |
|---|---|---|
| **P1 — Critical** | Customer-impacting service disruption. Production down or degraded beyond SLA threshold. | Acknowledge: 1 min · Resolve: 24 hrs |
| **P2 — High** | Significant issue, no current customer impact. Imminent risk of P1 if unresolved. | Acknowledge: 15 min · Resolve: 48 hrs |
| **P3 — Medium** | Non-urgent issue. No customer impact. Can be resolved in next sprint cycle. | Acknowledge: 4 hrs · Resolve: Next sprint |

### The Yellow Flag Protocol

The Yellow Flag is a **pre-P1 early warning system**. It triggers when a set of leading indicators suggests a P1 is likely within the next 24–72 hours, even though no SLA breach has occurred yet.

Yellow Flag triggers include: error rate trending upward over 4 hours, disk/memory utilisation crossing 80% threshold, two or more related P3s in 48 hours, or a deployment change with incomplete rollback testing.

**When Yellow Flag is raised:**
1. Delivery Head informed immediately — not at next status call
2. Mitigation plan activated within 2 hours
3. Cisco Manager informed if risk cannot be resolved within 24 hours
4. Daily status update until Yellow Flag is cleared

### The 48-Hour Post-Incident Review

Every P1 triggers a mandatory Post-Incident Review within 48 hours. The PIR covers:

1. **Timeline** — exact sequence of events from first signal to resolution
2. **Root cause** — technical root cause AND process/governance root cause (they are different)
3. **Customer impact** — quantified: downtime, affected users, SLA breach extent
4. **What worked** — elements of the response that should be preserved
5. **What failed** — elements that slowed resolution or caused confusion
6. **Systemic fix** — the process or architecture change that prevents this specific failure mode from recurring
7. **Owner and deadline** — named person responsible for the systemic fix, with a delivery date

**Rule:** A PIR without a systemic fix is just a post-mortem. The fix is the point.

---

## Playbook 2: Sprint Health Framework — Overview

**Full document:** [`02-sprint-health-framework.md`](02-sprint-health-framework.md)

### The 80% Capacity Discipline

Sprint capacity is planned at 80% of total available team hours. The remaining 20% is reserved for:
- Unplanned incidents and P2/P3 support
- Tech debt and code quality improvements
- Risk buffer for estimation variance

**Why this matters:** Teams that plan at 100% capacity have zero buffer for reality. A single unexpected dependency or a single incident breaks the entire sprint. The 80% rule makes sprint goal achievement predictable, not lucky.

### Sprint Goal Accountability Model

Every sprint begins with a single, customer-value sprint goal — not a list of stories, but one sentence that describes what the team will deliver that matters. Every story in the sprint is evaluated against: "Does this contribute to the sprint goal?"

At sprint review:
- **Goal achieved:** All sprint goal stories delivered, regardless of stretch stories
- **Goal at risk:** Sprint goal stories partially delivered — retrospective focuses on root cause
- **Goal missed:** Full retrospective with systemic fix identified before next sprint starts

Target sprint goal achievement rate: **≥ 90% over rolling 10 sprints.**

### Definition of Done and Definition of Ready

**Definition of Ready** — a story is Ready to enter a sprint when:
- Acceptance criteria are written and agreed by the team
- Dependencies are identified and unblocked or have a clear resolution path
- Story is estimated and fits within one sprint
- Technical approach is discussed (not fully designed, but not a black box)

**Definition of Done** — a story is Done when:
- All acceptance criteria pass
- Unit tests written and passing
- Code reviewed by at least one peer
- Documentation updated where required
- Deployed to test environment and verified

**Rule:** Stories that are "Done" without meeting the DoD are not Done. They are in-progress debt.

---

## Playbook 3: AI Transformation Programme — Overview

**Full document:** [`03-ai-transformation-programme.md`](03-ai-transformation-programme.md)

### Programme Structure

Running AI adoption across 8 engineering teams requires a programme structure that is light enough to not become overhead, and rigorous enough to track real results.

**Fortnightly PI-style Review** — every two weeks, all 8 teams present:
1. AI experiment outcome from the previous two weeks (what was tried, what was measured)
2. Next AI initiative (what is being tried next, what success looks like)
3. Cross-team dependencies (is any team blocked on another's AI tooling or pattern?)

Programme office (me) consolidates:
- Aggregate FTE-hours saved this fortnight
- Cumulative programme savings since launch
- Adoption rate per team (number of active AI initiatives)
- Programme ROI and payback period — updated fortnightly

### The Three Team States

Teams in an AI transformation programme are never uniformly adopting. Recognise the three states and respond accordingly:

| State | Indicators | Response |
|---|---|---|
| **Exploring** | First 1–2 AI experiments. Uncertain about use cases. | Pair with an adopter team. Share patterns. Reduce fear of failure. |
| **Adopting** | Regular AI experiments. Growing list of wins. | Amplify — share their successes across the programme. Reduce friction. |
| **Scaling** | Multiple AI initiatives running. Measurable ROI. | Make them mentors. Give them harder problems. |

**Warning sign:** A team that stays in "Exploring" for more than 3 fortnights needs a direct conversation with their TL — not about AI, about what is making adoption feel unsafe.

---

## Playbook 4: 30-60-90 Day Onboarding — Overview

**Full document:** [`04-team-onboarding-template.md`](04-team-onboarding-template.md)

### The Three Phases

**Days 1–30: Understand**
New engineer or TL focuses entirely on learning. No delivery pressure. Objectives:
- Understand the product, the codebase, the architecture
- Shadow every team ceremony at least once
- Build relationships with every team member
- Identify the three things about the team that are working well
- Identify the three things that need improvement (observation only — no fixes yet)

**Days 31–60: Contribute**
Begin contributing to sprint work. Objectives:
- Take ownership of at least two sprint stories end-to-end
- Attend first client/stakeholder meeting with manager
- Share one observation from the "understand" phase with the manager
- Present in at least one team ceremony (standup, sprint review, or retro)

**Days 61–90: Lead**
Begin leading within the team. Objectives (for TLs):
- Own the sprint planning facilitation for at least one sprint
- Identify and begin one process improvement initiative
- Have a 1:1 with every engineer on their team focused on growth, not just delivery
- Present programme status to Delivery Manager independently

**90-Day Review Criteria:**
- Can they operate independently without daily direction?
- Do they understand the commercial context of their work?
- Do they have the relationships needed to escalate and resolve issues?
- Are they growing the team, not just delivering for it?

---

## Playbook 5: Director Communication Model — Overview

**Full document:** [`05-director-communication-model.md`](05-director-communication-model.md)

### The Five Core Communication Shifts

The single most visible difference between a Technical Lead and a Director is communication — not technical knowledge.

| Technical Lead | Director |
|---|---|
| Reports activities | Reports outcomes |
| Brings problems | Brings decisions |
| Uses engineering language | Uses business language |
| Reacts to stakeholder questions | Anticipates them |
| Fixes individual issues | Fixes the system that caused them |

### The BLUF Model for All Status Updates

**Bottom Line Up Front.** Every status update — written or verbal — opens with the conclusion:

```
Opening (10 seconds): "Two things this week. One good, one a risk I want you to see early."
Good: [Outcome achieved + why it matters to the commitment]
Risk: [What the risk is + what I'm doing about it + whether I need a decision from you]
Close: "That's the summary. Do you want detail on anything?"
```

The Cisco Manager should know the health of the programme within 60 seconds of the status call starting.

---

## Playbook 7: Stakeholder Management — Overview

**Full document:** [`07-stakeholder-management.md`](07-stakeholder-management.md)

### The Dual Cisco Manager Model

I currently manage two distinct Cisco Manager relationships simultaneously — one for the Linux platform product team and one for the 24×7 cloud operations team. The design principle:

**Each stakeholder has:**
- Their own communication cadence (weekly call, separate agenda)
- Their own success metric set (product milestones vs SLA performance)
- Their own escalation path (different Cisco leadership chains)
- Their own governance rhythm (product review vs operational review)

**The common discipline across both:**
- Proactive disclosure — bad news arrives from me before it arrives from the programme
- Decision-ready updates — every status includes a clear statement of what, if anything, requires the Cisco Manager's input
- No surprises — if a risk is known to me for more than 24 hours, the Cisco Manager knows within 48 hours

### Managing Up: The Delivery Head Relationship

The Delivery Head sees 8+ programmes. What they need from me:

1. **Programme health in three metrics** — not a narrative, not a list of activities. Three numbers that tell the story.
2. **One flag** — one risk, one opportunity, or one decision that requires their awareness or input. Not a list.
3. **No decisions deferred to them that I can make myself** — I escalate when I need authority or perspective, not when I want someone else to own the risk.

---

## How to Use These Playbooks

These documents are starting points. Every team, every client, every organisational context requires adaptation. The value is not in copying them — it is in using them as a mirror to examine your own operating model and identify the gaps.

**Recommended reading order for a new Engineering Manager:**
1. Start with Playbook 4 (Onboarding) — this one is time-sensitive
2. Then Playbook 1 (Incidents) — because your first real test will come here
3. Then Playbook 2 (Sprint Health) — the foundational delivery rhythm
4. Then Playbook 5 (Communication) — because this determines how all the above is perceived
5. Then Playbooks 3, 6, and 7 — as your role grows in scope

---

## About the Author

**Arul Muruga A D** · Technical Project Manager & Group Technical Architect  
HCL Technologies · Cisco Offshore Development Centre · Chennai, India  
PMP · Google Certified GenAI Leader · AWS Cloud Practitioner  

📧 arulmuruga.ad@gmail.com · 💼 [linkedin.com/in/aruldswamy](https://linkedin.com/in/aruldswamy)
