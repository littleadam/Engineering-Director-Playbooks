# Sprint Health Playbook
### Engineering Director Framework | Delivery Governance

---

## The Problem

Most engineering teams run sprints. Few run *healthy* sprints.

The symptoms of an unhealthy sprint culture are predictable:
- Teams consistently carry work forward sprint-over-sprint
- "Done" means different things to different people
- Velocity numbers look fine until a release date is missed
- Leadership asks "how are we tracking?" and gets effort narratives instead of delivery facts

Sprint health is not about process compliance. It is about delivery predictability — the ability to look a stakeholder in the eye and say: *"Here is what we will ship. Here is when. Here is how confident I am."*

This playbook builds that predictability.

---

## The Framework

### 1. Definition of Ready (DoR) — Nothing Enters the Sprint Broken

A story is Ready for sprint commitment only when all of the following are true:

| Criterion | Why It Matters |
|---|---|
| Acceptance criteria written and agreed | Without this, "done" is subjective |
| Dependencies identified and cleared | Uncleared dependencies are hidden blockers |
| Design or approach agreed with TL | Prevents mid-sprint pivot |
| Effort estimated by the implementing engineer | Estimates from someone else are guesses |
| Test approach defined | QA surprises at end of sprint destroy velocity |

**Director rule:** If a story fails DoR at sprint planning, it does not enter the sprint. No exceptions. The product backlog is the place for incomplete work — not the active sprint.

---

### 2. Definition of Done (DoD) — Nothing Leaves the Sprint Incomplete

A story is Done only when:

- [ ] Code complete and peer-reviewed
- [ ] Unit tests written and passing
- [ ] Integration tested in the target environment
- [ ] Acceptance criteria verified (by someone other than the author)
- [ ] Documentation updated if behaviour changed
- [ ] No new P1/P2 defects introduced

**Director rule:** A story that is "90% done" is not done. It is work-in-progress disguised as progress. Half-done features carry full carrying cost.

---

### 3. The 80% Capacity Rule

**Never plan a sprint to 100% capacity.**

Plan to 80% of available engineering hours. The remaining 20% absorbs:
- Unplanned incidents and production issues
- Review and feedback cycles
- Knowledge transfer and mentoring overhead
- Legitimate scope clarification mid-sprint

Teams that plan to 100% have no buffer. The first unplanned event breaks the sprint. The second one breaks the team's trust in the process.

**How to calculate available capacity:**

```
Available Hours = (Team Size × Sprint Days × 6 hrs/day) × 0.80
Subtract: planned leave, recurring ceremonies, on-call hours
Result: Plannable Sprint Capacity
```

Example: 5 engineers, 10-day sprint
- Gross: 5 × 10 × 6 = 300 hours
- 80% rule: 240 hours plannable
- Subtract ceremonies (15 hrs) + on-call (10 hrs): **215 hours actual capacity**

---

### 4. Sprint Governance — What the Director Tracks

Directors do not track individual story completion. They track **sprint health indicators**:

| Indicator | Healthy Signal | Warning Signal |
|---|---|---|
| Carry-forward rate | < 10% of points | > 20% of points |
| Mid-sprint scope additions | 0 unplanned additions | Any addition without removal |
| Defect injection rate | Flat or declining | Rising sprint-over-sprint |
| Blocked story days | < 2 days average | > 3 days average |
| Sprint goal clarity | Single, measurable goal | Multiple goals or vague goal |

**Weekly director check-in (15 minutes with each TL):**
1. What is the sprint goal?
2. Are we on track to hit it?
3. What is blocked and what is the plan?
4. Any risks to the release commitment?

That is the entire agenda. If it takes longer than 15 minutes, something is wrong with how the TL is preparing.

---

### 5. Sprint Review — Outcomes, Not Activities

Sprint reviews exist to demonstrate working software against acceptance criteria — not to narrate effort.

**Bad sprint review opening:** *"This sprint, the team worked on the authentication module and completed most of the stories..."*

**Good sprint review opening:** *"Sprint goal was: users can log in with SSO. We achieved that. Here is the demo. We also carry two stories forward — here is why and what it means for the release timeline."*

**Review agenda (30 minutes):**
1. Sprint goal restatement (1 min)
2. Goal achieved / not achieved — declared upfront (1 min)
3. Demo of completed work (15 min)
4. Carry-forward items and impact assessment (5 min)
5. Next sprint goal preview (5 min)
6. Stakeholder questions (3 min)

---

### 6. Retrospective — Systems, Not Blame

Retrospectives exist to improve the delivery system, not to assign blame.

**The three questions that matter:**
1. What slowed us down this sprint? (system gaps)
2. What one change would most improve our next sprint?
3. Are our previous retro actions actually being done?

**Director rule:** Every retrospective produces exactly one action item that is owned by a named person with a deadline. Not a list of ten. One. The most important one.

Track completion of retro actions at the next retrospective's opening. If the action was not done, it goes back on the list — with a conversation about why.

---

## Anti-Patterns to Eliminate

| Anti-Pattern | What It Looks Like | What It Actually Is |
|---|---|---|
| Velocity inflation | Closing stories on the last day of every sprint | Work that was not actually done |
| Sprint washing | Adding done stories retroactively | Gaming the metric |
| Heroics culture | Same engineer saves every sprint | A single point of failure and a team that is not learning |
| Perpetual carry-forward | Same stories appear sprint after sprint | Stories that were never truly estimated or never truly started |
| Meeting without decision | Sprint planning ends without a committed goal | A ceremony without accountability |

---

## Templates

### Sprint Goal Template
```
By the end of this sprint, [team/product] will [specific deliverable]
so that [business or user outcome].

Success is measured by: [specific, testable criterion]
```

### Carry-Forward Communication Template
```
Sprint [N] Carry-Forward Notice

Stories carried forward: [list]
Root cause: [one sentence — scope, dependency, or estimation gap]
Impact on release: [specific — days slipped, feature deferred, or no impact]
Mitigation: [what changes in Sprint N+1]
```

### Weekly TL Check-In Template
```
TL: [Name] | Date: [Date] | Sprint: [N] | Day: [X of Y]

Sprint Goal: [one line]
On Track: Yes / No / At Risk

Blockers:
- [Blocker] | Owner: [Name] | Expected resolution: [Date]

Release risk: None / Low / Medium / High
If Medium or High: [one sentence description and mitigation already in motion]
```

---

## Key Principle

> *Delivery predictability is not about having perfect sprints. It is about having a system that surfaces problems early enough to fix them — and a team that trusts the system enough to be honest about those problems.*

The Director's job is to build that system and maintain that trust. Sprint health is the output. The system is the work.

---

*Part of the [Engineering Director Playbooks](./README.md) series.*
