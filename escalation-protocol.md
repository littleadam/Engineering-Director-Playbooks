# Escalation Protocol
### Engineering Director Framework | Decision Governance

---

## The Problem

Most engineers are taught to escalate problems. This is wrong.

Escalating a problem to a senior leader without options transfers your cognitive burden to them. It consumes their time, signals that you have not thought deeply, and — over time — trains stakeholders to expect problems from you instead of solutions.

The discipline that separates individual contributors from leaders, and managers from directors, is this:

**You escalate decisions. Not problems.**

This playbook formalises that discipline into a repeatable framework — for you, and for every Technical Lead you develop.

---

## The Framework: SIOR

Every escalation follows four elements — Situation, Impact, Options, Recommendation.

### S — Situation (Facts Only)

State what happened. Facts, not feelings. Data, not drama.

**Bad:** *"The build pipeline is broken and it's really bad."*
**Good:** *"The signing stage of the build pipeline has failed on 3 of 4 runs since 14:00. The failure rate under peak load is 75%."*

Rules for the Situation statement:
- One to three sentences maximum
- Quantified where possible (time, frequency, percentage, count)
- No attribution of blame
- No emotional language

---

### I — Impact (Business Language)

State what the situation means for the commitment — in business terms, not engineering terms.

**Bad:** *"This is causing a race condition in the signing stage."*
**Good:** *"At current failure rate, 1 in 4 builds requires a 4-hour manual rework cycle. If unresolved, this adds 2 days to the release timeline."*

Rules for the Impact statement:
- Translate to business consequence: time, cost, SLA, user impact, or commitment risk
- Be specific about the timeline implication
- State whether the impact is current or projected
- One to two sentences

**The translation table:**

| Engineering Language | Business Language |
|---|---|
| Race condition in signing stage | 1 in 4 builds fails under peak load |
| Memory leak in service | System degrades after 72 hours of uptime |
| Flaky test suite | 30% of CI runs require manual rerun (2 hours each) |
| Dependency not available | Feature delivery blocked until [date] |
| Build time regression | Release candidate creation now takes 3 days, not 4 hours |

---

### O — Options (Always Three)

Present three options. Not one. Not two. Three.

**Why three?**
- One option is an ultimatum. It removes the stakeholder's agency.
- Two options is a false dilemma. It forces a binary choice when reality is rarely binary.
- Three options demonstrates that you have thought through the problem space, considered trade-offs, and respected the stakeholder's right to choose.

**How to structure each option:**

```
Option [A/B/C]: [Name]
What: [One sentence — what this option does]
Effort: [Time and resource required]
Risk: [What could go wrong with this option]
Outcome: [What we get if this works]
Trade-off: [What we give up]
```

**The three option types that work in most engineering scenarios:**

| Option Type | When To Use |
|---|---|
| Fast / Tactical | When time pressure is highest; accepts technical debt |
| Balanced / Recommended | The option you believe delivers the best risk-adjusted outcome |
| Safe / Conservative | When the cost of being wrong is very high; slower but lower risk |

---

### R — Recommendation (Own It)

State your recommendation clearly. Do not hedge.

**Bad:** *"I think Option B might be the best choice, but I'm not sure — it depends on what you think."*
**Good:** *"My recommendation is Option B. Here is why: it delivers the fix within the release window, carries manageable risk, and does not require stakeholder approval from the dependency team."*

Rules for the Recommendation:
- Name the option explicitly
- Give the one or two reasons that make it your recommendation
- If you are genuinely uncertain, say that — but still give a recommendation with your current best judgment
- Own it. If it does not work, you will own the next set of options.

---

## The Full SIOR Template

```
ESCALATION: [System / Programme / Feature Name]
Date/Time: [When raised]
Raised by: [Your name and role]
Decision required by: [Specific time — creates urgency without panic]

SITUATION
[2–3 sentences. Facts only. Quantified.]

IMPACT
[1–2 sentences. Business consequence. Timeline implication.]

OPTIONS

Option A — [Name]
What: 
Effort: 
Risk: 
Outcome: 
Trade-off: 

Option B — [Name]
What: 
Effort: 
Risk: 
Outcome: 
Trade-off: 

Option C — [Name]
What: 
Effort: 
Risk: 
Outcome: 
Trade-off: 

RECOMMENDATION
My recommendation is Option [X] because [1–2 reasons].
I am available to discuss this immediately if needed.
```

---

## When To Escalate

Not every problem requires escalation. The decision to escalate is itself a judgment call.

**Escalate when:**
- The decision requires authority or resources beyond your scope
- The impact crosses a commercial SLA or contractual commitment
- The risk affects another team, stakeholder, or programme
- Two or more of your options require stakeholder input to be viable
- You have tried all available options within your authority and none have worked

**Do not escalate when:**
- You can resolve it within your authority within the committed timeline
- The impact is contained to your team and within sprint buffers
- You have an option that does not require stakeholder involvement

**The five-minute rule:** Before escalating, give yourself five minutes to structure the SIOR. If you cannot complete the Situation and Impact sections in five minutes, you do not yet understand the problem well enough to escalate it. Keep investigating.

---

## Coaching Your Technical Leads

The SIOR framework is most powerful when it becomes the team's shared language — not just yours.

**How to coach TLs on escalation quality:**

1. **When a TL brings you a problem without options:** Ask — *"What are our options?"* Do not answer for them. Wait.

2. **When a TL brings you a vague impact statement:** Ask — *"What does this mean for the release date?"* Force specificity.

3. **When a TL hedges on their recommendation:** Say — *"If you had to choose right now, which would you pick?"* Build the muscle.

4. **When a TL escalates something they could have resolved:** Acknowledge the instinct, then say — *"Walk me through what you tried before bringing this to me."* Teach scope of authority.

5. **Celebrate good escalations publicly.** When a TL brings you a well-structured SIOR and a strong recommendation, name it in front of the team. The behaviour you reward is the behaviour you get.

---

## The Pre-P1 Escalation Protocol

When an incident is developing, the SIOR framework needs to run fast. Here is the accelerated version for operations contexts:

```
FAST ESCALATION (< 3 minutes to prepare)

Situation: [What is failing and since when]
Impact: [SLA breach in / user impact now]
Options:
  - Rollback: [Yes/No + time to execute]
  - Hotfix: [Yes/No + time to execute]
  - Escalate to vendor/dependency: [Yes/No + contact available]
Recommendation: [Which one and why, in one sentence]
```

The structure does not change under pressure. The time budget does.

---

## Anti-Patterns to Eliminate

| Anti-Pattern | What It Looks Like | What It Signals |
|---|---|---|
| Problem dumping | "We have an issue with X. What should we do?" | You have not thought about it |
| Option-free escalation | "I think we need to do Y." | You are seeking approval, not a decision |
| Vague impact | "This could cause delays." | You have not assessed the real consequence |
| Recommendation hedging | "It depends on what leadership wants." | You are avoiding accountability |
| Over-escalation | Bringing every decision to the Director | You do not understand your own authority |
| Under-escalation | Resolving things within scope that have crossed into programme risk | You are protecting information that leadership needs |

---

## Key Principle

> *A stakeholder's job is to decide. Your job is to make that decision fast, easy, and well-informed. When you escalate a problem, you are outsourcing your thinking. When you escalate a decision — with a situation, an impact, three options, and a recommendation — you are exercising leadership.*

The day your Technical Leads stop bringing you problems and start bringing you options is the day your team has grown.

---

*Part of the [Engineering Director Playbooks](./README.md) series.*
