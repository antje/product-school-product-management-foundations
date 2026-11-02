# Hypothesis & Success Metrics

Module 3 · Deliverable 3. Scenario: RouteLogic Velocity. Bet type: optimizing the existing.

**Refined on 2026-11-02.** The pre-work below preserves the driver persona and original value proposition from Modules 1 and 2. The snapshots moved the bet to coordinators. The current experiment uses a fixed workday denominator and +12 points versus concurrent control, replacing my earlier absolute 60% ship rule. The scenario's 14.6 minutes is a mean. The prototype's proposed median of 3 minutes is a separate, unproven usability bar.

## Pre-work · Hypothesis check

**Role, who you are solving for (from M2)**

A delivery driver making dozens of stops a day, often at a doorstep with one hand free.

**Goal, what this user is ultimately trying to achieve**

To confirm each stop and move on in seconds, with the rest of the route still there.

**Friction / moment of misery, the specific pain blocking their goal**

Marking a stop delivered takes three taps across three screens, at a doorstep in the rain with a package in one hand (UXR-01, BUG-2055).

**Current workaround, the external tool or manual process they rely on (M2)**

The driver texts the dispatcher instead of tapping. Drivers keep a paper manifest and a morning screenshot of the route as backup. The dispatcher runs a WhatsApp group as "the real system".

**Problem Hook, your one-sentence framing of the business crisis (M1)**

We must keep our largest account and win back daily use by making frontline work faster in RouteLogic than texts, WhatsApp and paper.

**Value Proposition, the outcome your initiative promised to deliver (M1)**

For drivers and their dispatchers, we will make core actions faster than texts and paper, because our largest account is deciding during its trial. Compliance and finance layers move off their screens, one step away for the managers who bought them.

## Read your data snapshots

### Snapshot 1 of 3 · Feature adoption by role

**Does the low adoption confirm your persona is burdened by tools they don’t use? Note whether the low scheduling adoption (42%) for coordinators matches your M2 moment of misery.**

Partly. Drivers carry tools they don't use: Financial Reporting reaches 3% of them, AI Predictive ETAs 11% and Shift Scheduling 15%. But their daily work clusters on three features: Live Dispatch Board (88%), Route Optimizer (72%) and Compliance Checklist (64%). The three-tap delivery sits inside that core, so the burden is less about unused tools than about how the used ones work. The coordinators' 42% scheduling adoption does not match our Module 2 misery: no research note mentions scheduling. It is a gap worth noting, not the pain we found. The surprise is compliance, the third most used feature for both frontline roles (77% of coordinators, 64% of drivers). That makes it core work, not a layer to move off their screens, which contradicts our Module 1 value proposition. These snapshots slice by role only, the behavioral lens. Tenure and account tier are not in the data, so I cannot tell whether compliance hurts new coordinators most or specific accounts most.

### Snapshot 2 of 3 · Coordinator daily dispatch workflow completion

**Does the workflow data match the manual process or hack you documented in M2? Note whether the specific drop-offs or time gaps explain why your persona avoids the digital tool.**

It explains the dispatcher's side of the Module 2 workaround, and it moves the main pain away from our persona. Coordinators, the dispatchers in our research, get through route assignment in RouteLogic: 71% finish it. Then the workflow falls apart. Only 48% log compliance checks, 31% complete the shift handoff and 18% file the daily report. Of the coordinators who assign routes, 56% never finish the handoff. That fits a WhatsApp group running the day once the routes go out (UXR-02). The largest time gap is compliance: a scenario mean of 14.6 minutes against a 3-minute benchmark, nearly five times longer. Its 11.6-minute gap is part of the 29.8 minutes the five steps run over benchmark, not a demonstrated saving from B1. Our persona, the driver, is not in this funnel. The main bottleneck sits with the coordinator at compliance, not with the driver at the doorstep.

### Snapshot 3 of 3 · Account health & CSAT by segment

**Look at the CSAT heatmap. Which specific cell most directly maps to your persona’s friction? Note how the NPS trend justifies the urgency of your M1 Problem Hook.**

Coordinators × Compliance, at 2.2 out of 5: the lowest score any role gives a feature it uses daily. The cell for our Module 2 misery, Drivers × Core Dispatch, scores 4.3, the best frontline score in the table. That is the second pivot check: our persona is satisfied where we placed the pain. A three-tap annoyance can hide inside a high cluster average, but it is not the leak behind the account crisis. The trend shows where the urgency is. Coordinator NPS fell from +18 to -12 in two years. Daily time lost to manual workarounds rose from about 9 to 31 minutes. Four of five churned accounts now cite complexity, against one of eight two years ago. Over time this is a decline, so it is a leak that needs a fix to restore lost value. The data gives two points in time, not a full cohort table, so the shape between them is unknown. Managers rate Compliance 3.9 and Reporting 4.5, so the buyer is content while the frontline struggles. That is the gap the Module 1 hook named: losing the daily user while winning the executive demo. The pivot: the persona becomes the coordinator, and the friction becomes compliance logging.

## Step 3 · Craft your hypothesis

**Qualitative evidence (from M2), quote the specific friction / moment of misery for your persona**

Dispatchers do not trust RouteLogic for the live day. They say "I can't trust the board" (UXR-09) and "We keep a WhatsApp group as the real system" (UXR-02). An enterprise ops manager adds: "My frontline people use maybe 5% of it and can't find that 5%" (UXR-04). Gap: no interview mentions compliance. The qualitative evidence shows coordinators leaving the tool. It does not show that compliance is the reason.

**Quantitative evidence (from M3), name the metric or data point that confirms the pain; cite the number**

Logging compliance checks has a scenario mean of 14.6 minutes against a 3-minute benchmark, and completion falls from 71% at route assignment to 48% at compliance. Coordinators rate Compliance 2.2 out of 5 while 77% of them use it daily. Coordinator NPS fell from +18 to -12, and four of five churned accounts cite complexity.

**Persona, role, goal, and the friction you confirmed in the reconciliation steps**

Role: a fleet coordinator, the dispatcher in our research, who assigns routes, logs compliance checks and hands off shifts every day. Goal: run the whole daily workflow inside RouteLogic. Friction: compliance logging, at 14.6 minutes against a 3-minute benchmark, the step where the workflow breaks. The driver stays at the other end of the handoff, and drivers also fill in the checklist (64% use it, CSAT 2.8).

**Problem you are solving, one sentence describing the specific friction this initiative removes**

Compliance logging averages nearly five times the benchmark, at the step where daily workflow completion drops. Whether interface friction causes that drop is the hypothesis to test.

**Strategic outcome, what behaviour change do you expect, and how does it map to retention / revenue / churn?**

Coordinators finish the daily workflow in RouteLogic instead of leaving after route assignment. On the AARRR funnel this is retention of daily use, a stage the product directly controls. It cuts the complexity that four of five churned accounts cite, which is the churn risk behind our largest account's trial. The funnel we own is the coordinator's daily workflow. The manager's funnel depends on it. The proposed link is that more complete frontline records support the reporting managers value. The supplied research does not measure that dependency. The bet is optimizing the existing: fix friction in a known workflow and measure retention and conversion, not activation.

**Primary success metric (initiative signal), the leading indicator that tells you the gap is closing**

Daily compliance-step completion, calculated per coordinator on scheduled workdays fixed before assignment, including non-use as zero. A completed day requires all required route/shift logs by shift end. Compare account-standardized variant and control means, as defined in [VEL-01](../05-experimentation/experimentation-plan.md).

The minimum worthwhile effect is +12 percentage points versus concurrent control. At the scenario's 48% reference this corresponds to 60%, a 25% relative increase. The PM's planning judgment is to recover roughly half the 23-point funnel leak: 12/23 ≈ 52%. The 48% source uses app-openers. Before build, validate baseline and variance on the experimental roster denominator. Do not treat 60% alone as proof of lift. My original 7.3-minute time target halved the supplied mean. It is superseded by the PRD's exploratory prototype median bar of 3 minutes, not by a claim that the mean saving has been measured.

**Guardrail metric (product signal), the metric that must NOT drop; it protects your existing base**

Compliance quality. Managers rate Compliance 3.9 and Reporting 4.5 in the scenario. Record correction/flag rates may not rise more than 2 points against concurrent control. A Fail-rate ratio below half of control triggers an audit of case mix, newly captured logs, real improvements, and rushed answers. It does not prove rubber-stamping. Both thresholds are PM planning judgments requiring the compliance owner's agreement before exposure. The snapshots supply no accuracy baseline. Manager CSAT is descriptive because managers see both arms. [VEL-01](../05-experimentation/experimentation-plan.md) owns the definitions and live stop rules.

**Decision window, how much time or data before you scale, pivot, or kill? minimum threshold to proceed?**

The pre-build evidence gate covers five current-flow observations per account, checklist fit, eligible enrollment, baseline variance, and a feasible measurement and audit design. The binary planning approximation is 270 per arm for 48% versus 60%, at 80% power and two-sided 5% significance. The daily-rate design must pass its own power check. Insufficient enrollment holds the build for recruitment or a newly powered protocol.

Weeks 1 and 2 build and test the implementation. The pre-exposure implementation gate then checks telemetry, persistence, write guards, prototype usability, and the canary before randomization. Read efficacy after 14 days, planned as pilot weeks 3 and 4 if both gates pass on schedule. A gate delay moves the read rather than shortening the test. Monitor safety throughout. [VEL-01's ordered policy](../05-experimentation/experimentation-plan.md) replaces my original rule. Investigate invalid data and pause on guardrail concerns. Stop confirmed severe harm. Ship only when all evidence bars hold. Kill a sufficiently precise nonpositive result, and iterate on remaining inconclusive or small effects without rollout.

## Finalized product hypothesis

**Draft your full hypothesis sentence, one to three sentences; quote the metric, name the persona, name the outcome**

> Based on dispatchers who "can't trust the board" and the scenario's 14.6-minute mean compliance step, I believe removing observed interface friction will increase fleet coordinators' daily compliance completion by at least 12 points versus concurrent control. I will protect compliance quality and decide at the fixed day-14 read. Enrollment, checklist fit, measurement design, and power must clear before build, with the implementation verified before exposure.

Checked against the four pitfalls:

- **Vague or broad:** it names the persona (fleet coordinators), the behavior (finishing the daily workflow in RouteLogic) and the metric (compliance-step completion).
- **Biased framing:** it states the problem to solve (compliance takes five times the benchmark), not a feature.
- **Not testable:** it has a baseline, a target and a sample size.
- **Misaligned:** it moves daily use, which is what the hook and the churned accounts are about.

## Success metrics

| Metric | Type | Target | Why it matters |
|---|---|---|---|
| Full daily workflow completion (through handoff), read at the end of week 12 if the rollout schedule holds | North-star, success signal, lagging | Scenario reference 31% → planning target 39% | 60% × (31/48) = 38.75%, rounded to 39%, assumes the downstream handoff ratio holds. Rebaseline on the roster denominator before setting the rollout target. B3 would change this metric too. |
| Compliance-step completion | Leading indicator, initiative signal | +12 points versus concurrent control. Scenario illustration 48% → 60% | Tests the proposed behavior change. Prototype median ≤ 3 minutes is a separate usability hypothesis. |
| Record accuracy and Fail-rate audit | Guardrail, counter-metric | Accuracy deterioration ≤ 2 points. Fail ratio below 0.5 triggers an audit | Planning judgments agreed before launch, defined in VEL-01. A positive primary result cannot override confirmed harm. |
| Manager Compliance CSAT | Descriptive trust signal | Scenario reference 3.9. Investigate a decline | Managers see both arms. This is not a randomized estimate of B1's effect. |
