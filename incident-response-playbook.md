# Incident Response Playbook
### Engineering Director Framework | Operations Governance

---

## The Problem

Incidents are not the problem. How organisations respond to incidents is.

The failure patterns are consistent across every engineering team that has not built a response system:

- No one knows who owns the incident
- Multiple people are working the problem with no coordination
- Stakeholders are receiving fragmented, contradictory updates
- The same incident recurs because the root cause was never fixed — only the symptom
- The post-incident review, if it happens at all, produces a list of action items that are never completed

The cost is not just the incident downtime. It is the erosion of stakeholder trust that accumulates across every unmanaged incident.

This playbook builds an incident response system that eliminates these failure patterns.

---

## The Framework

### Layer 1: Incident Classification

Every incident is classified at the moment of detection. Classification drives response — not the other way around.

| Priority | Definition | Response SLA | Escalation |
|---|---|---|---|
| **P1 — Critical** | Production system down or degraded for all users. SLA breach in progress or imminent. Revenue or contractual impact. | Acknowledge: ≤ 1 min. Bridge open: ≤ 5 min. First update to stakeholders: ≤ 15 min | Immediate. Director notified. War room open. |
| **P2 — Major** | Significant functionality impaired. Workaround available. Subset of users impacted. | Acknowledge: ≤ 15 min. Work begins: ≤ 30 min. First stakeholder update: ≤ 1 hr | TL notified. Director informed at next check-in unless escalating. |
| **P3 — Minor** | Non-critical degradation. No user-facing SLA impact. Cosmetic or edge-case defect. | Acknowledge: ≤ 4 hrs. Scheduled for next sprint or patch cycle. | Tracked in backlog. No immediate escalation. |

**Classification principle:** When in doubt, classify higher. It is operationally cheaper to stand down a P1 bridge than to under-respond to a real P1.

---

### Layer 2: The Yellow Flag Protocol

**The Yellow Flag Protocol is pre-P1 intelligence.**

The Yellow Flag is triggered when a leading indicator suggests a P1 is developing — before it becomes one.

Yellow Flag triggers include:
- System metrics crossing 70% of P1 threshold (CPU, memory, queue depth, error rate)
- A P2 that has not resolved within 50% of MTTR target
- Two or more P3s in the same subsystem within a 24-hour window
- An engineer's gut instinct that something is wrong (this is a legitimate trigger)

**When Yellow Flag is raised:**
1. Engineer raises the flag in the incident channel
2. TL is notified immediately
3. A 15-minute assessment begins: Is this escalating or stabilising?
4. Director receives a one-line Yellow Flag notification — not an escalation, an awareness signal
5. At 15 minutes: either stand down (document why) or escalate to P1/P2

**Why this matters:** The Yellow Flag gives leadership visibility before the problem becomes a surprise. My stakeholders hear bad news from me before they hear it from anyone else — and always with a plan already in motion.

---

### Layer 3: The 4-Layer Shift Handoff

Round-the-clock operations fail at handoff points. This is where incidents fall through the gaps, context is lost, and the incoming engineer spends the first hour of their shift understanding what the outgoing engineer already knows.

The 4-layer handoff eliminates this.

**Handoff Structure:**

```
LAYER 1 — SYSTEM STATUS (5 minutes)
Current state of all monitored systems: Green / Yellow / Red
Any active incidents: P1 / P2 / P3 with current status
Any systems in degraded mode or under observation

LAYER 2 — ACTIVE WORK (5 minutes)
What work is in progress right now?
Who owns it?
What is the expected resolution time?
What does the incoming engineer need to do if resolution does not happen by [time]?

LAYER 3 — WATCH ITEMS (3 minutes)
What is not yet an incident but needs monitoring?
What thresholds trigger escalation?
Any scheduled maintenance or deployments in the next shift?

LAYER 4 — KNOWLEDGE TRANSFER (2 minutes)
Any runbook gaps discovered this shift?
Any new failure modes observed?
Any stakeholder commitments made that the incoming engineer needs to honour?
```

**Handoff is synchronous.** Both engineers on a call — no asynchronous handoffs for operations teams. The outgoing engineer does not close their laptop until the incoming engineer confirms they have context.

Total handoff time: 15 minutes. Non-negotiable.

---

### Layer 4: The 48-Hour Post-Incident Review

Every P1 and significant P2 triggers a mandatory post-incident review within 48 hours of resolution.

**Why 48 hours?** Close enough that the team remembers the detail. Far enough that the adrenaline has cleared and people can think clearly.

**Post-Incident Review Structure:**

```
INCIDENT SUMMARY
- What happened (timeline, not narrative)
- Impact: users affected, duration, SLA status
- Detection: how was it found, and how long after it started?
- Resolution: what fixed it?

ROOT CAUSE ANALYSIS
- Immediate cause: what directly caused the incident?
- Contributing factors: what conditions allowed it to happen?
- Detection gap: why didn't we catch it earlier?

SYSTEMIC FIX
- What changes to the system, runbook, or monitoring prevent recurrence?
- Owner: [named person]
- Deadline: [specific date]

RUNBOOK UPDATE
- Which runbook was used?
- Was it accurate?
- What has been updated? (attach diff)
```

**Director rule:** Every P1 closes with a runbook update. Repeat incidents from runbook gaps are unacceptable and tracked at programme level.

---

### Layer 5: Stakeholder Communication During Incidents

Communication during an incident is as important as the technical response. Silence is the worst thing you can offer a stakeholder during a P1.

**Communication cadence for P1:**

| Time | Action |
|---|---|
| T+0 to T+15 min | Initial notification: "We are aware of [impact]. Bridge is open. Next update at T+30." |
| T+30 min | Status update: what we know, what we are doing, next update time |
| Every 30 minutes | Progress update until resolved |
| T+Resolution | Resolution notice: what happened, what fixed it, what comes next |
| T+48 hours | Post-incident summary to stakeholders |

**Communication template — P1 Initial Notification:**
```
SUBJECT: [P1] [System Name] — Active Incident | [Date Time]

Impact: [What users/systems are affected]
Detected: [Time detected]
Status: Active — investigation in progress
Bridge: [Link or dial-in]
Incident Owner: [Name]
Next update: [Specific time]

We will provide updates every 30 minutes until resolved.
```

---

## SLA Compliance Tracking

SLA compliance is a director-level metric. Track it weekly, report it monthly.

| Metric | Definition | Target |
|---|---|---|
| MTTA (Mean Time to Acknowledge) | Time from incident detection to acknowledgement | ≤ 1 minute for P1 |
| MTTR (Mean Time to Resolve) | Time from detection to full resolution | ≤ 24 hours for P1 |
| SLA Compliance Rate | % of incidents resolved within SLA commitment | 100% (P1) |
| Repeat Incident Rate | % of incidents caused by previously known failure modes | Target: 0% |

**Repeat incident rate at zero** is the highest-value operational metric. It means your post-incident reviews are producing real systemic fixes — not checkbox documentation.

---

## Anti-Patterns to Eliminate

| Anti-Pattern | What It Looks Like | The Real Problem |
|---|---|---|
| Heroic resolution | One engineer fixes every P1 | Single point of failure. Team is not learning. |
| Post-incident amnesia | Review happens once, fixes never implemented | Governance without accountability |
| Blame culture | Post-incident focuses on who made the mistake | People hide problems instead of surfacing them |
| Stakeholder silence | Director communicates only at resolution | Trust erodes. Stakeholders fill the silence with assumptions. |
| Classification inflation | Every alert becomes a P1 | Desensitises the team. Real P1s get slow responses. |

---

## Key Principle

> *The goal of incident response is not to resolve the incident. It is to build a system where each incident makes the next one less likely — and where no incident ever surprises a stakeholder.*

SLA compliance is the outcome. The system — classification, early warning, handoff, review, and communication — is what produces it.

---

*Part of the [Engineering Director Playbooks](./README.md) series.*
