# Hypothesis & Success Metrics

**Product:** RouteLogic Velocity · **Bet:** Optimize the existing coordinator workflow

## Evidence and scope

All business and workflow figures are supplied course-scenario evidence. VEL-01 has not run. The scenario's 14.6-minute compliance time is a mean. The proposed prototype median of 3 minutes is a separate, unproven usability bar.

Initial discovery focused on delivery drivers confirming stops at a doorstep: three taps across three screens, with a package in one hand (UXR-01, BUG-2055). Drivers text dispatchers, carry paper manifests and screenshot routes. The dispatcher also runs a WhatsApp group as "the real system" (UXR-02). The [historical driver journey](../02-discovery/competitive-and-journey.md#historical-baseline-the-original-driver-journey) records that hypothesis. The coordinator funnel and CSAT evidence below establish the current priority.

## Scenario data

### Snapshot 1 of 3 · Feature adoption by role

Driver adoption is low for some features: Financial Reporting reaches 3% of them, AI Predictive ETAs 11% and Shift Scheduling 15%. But their daily work clusters on three features: Live Dispatch Board (88%), Route Optimizer (72%) and Compliance Checklist (64%). The three-tap delivery sits inside that core, so the burden is less about unused tools than about how the used ones work. Coordinators' scheduling adoption is 42%, but no research note describes scheduling friction. The surprise is compliance, the third most used feature for both frontline roles (77% of coordinators, 64% of drivers). Compliance is core frontline work, so it belongs in the coordinator workflow. These snapshots slice by role only, the behavioral lens. Tenure and account tier are not in the data, so I cannot tell whether compliance hurts new coordinators most or specific accounts most.

### Snapshot 2 of 3 · Coordinator daily dispatch workflow completion

Coordinators, the dispatchers in the research, get through route assignment in RouteLogic: 71% finish it. Then the workflow falls apart. Only 48% log compliance checks, 31% complete the shift handoff and 18% file the daily report. Of the coordinators who assign routes, 56% never finish the handoff. That fits a WhatsApp group running the day once the routes go out (UXR-02). The largest time gap is compliance: a scenario mean of 14.6 minutes against a 3-minute benchmark, nearly five times longer. Its 11.6-minute gap is part of the 29.8 minutes the five steps run over benchmark, not a demonstrated saving from B1. The driver is outside this funnel. Compliance is the largest measured coordinator bottleneck.

### Snapshot 3 of 3 · Account health & CSAT by segment

Coordinators × Compliance scores 2.2 out of 5, the lowest score any role gives a feature it uses daily. Drivers × Core Dispatch scores 4.3, the best frontline score in the table. That cluster average can still hide delivery-confirmation friction. It does not establish how much the driver issue contributes to the account risk.

Coordinator NPS fell from +18 to -12 in two years. Daily time lost to manual workarounds rose from about 9 to 31 minutes. Four of five churned accounts now cite complexity, against one of eight two years ago. The data gives two points in time, not a full cohort table, so the shape between them is unknown.

Managers rate Compliance 3.9 and Reporting 4.5. The current bet focuses on coordinators and compliance logging while preserving the reporting managers value.

## Product hypothesis and measures

### Qualitative evidence

Dispatchers do not trust RouteLogic for the live day. They say "I can't trust the board" (UXR-09) and "We keep a WhatsApp group as the real system" (UXR-02). An enterprise ops manager adds: "My frontline people use maybe 5% of it and can't find that 5%" (UXR-04). Gap: no interview mentions compliance. The qualitative evidence shows coordinators leaving the tool. It does not show that compliance is the reason.

### Quantitative evidence

Logging compliance checks has a scenario mean of 14.6 minutes against a 3-minute benchmark, and completion falls from 71% at route assignment to 48% at compliance. Coordinators rate Compliance 2.2 out of 5 while 77% of them use it daily. Coordinator NPS fell from +18 to -12, and four of five churned accounts cite complexity.

### Target coordinator

Role: a fleet coordinator, the dispatcher in our research, who assigns routes, logs compliance checks and hands off shifts every day. Goal: run the whole daily workflow inside RouteLogic. Friction: compliance logging, at 14.6 minutes against a 3-minute benchmark, the step where the workflow breaks. The driver stays at the other end of the handoff, and drivers also fill in the checklist (64% use it, CSAT 2.8).

### Problem

Compliance logging averages nearly five times the benchmark, at the step where daily workflow completion drops. Whether interface friction causes that drop is the hypothesis to test.

### Strategic outcome

The intended outcome is more coordinators completing their daily workflow in RouteLogic. In the AARRR funnel, this is retention of daily use. The pilot directly tests compliance completion, while later workflow completion and account retention remain downstream signals. More complete frontline records may support the reporting managers value, but the supplied research does not measure that dependency. This is an optimization bet in an existing workflow.

### Primary success metric

Daily compliance-step completion, calculated per coordinator on scheduled workdays fixed before assignment, including non-use as zero. A completed day requires all required route/shift logs by shift end. Compare account-standardized variant and control means, as defined in [VEL-01](../05-experimentation/experimentation-plan.md).

The minimum worthwhile effect is +12 percentage points versus concurrent control. At the scenario's 48% reference this corresponds to 60%, a 25% relative increase. The PM's planning judgment is to recover roughly half the 23-point funnel leak: 12/23 ≈ 52%. The 48% source uses app-openers. Validate baseline and variance on the experimental roster denominator before build. An absolute 60% result alone cannot establish lift. The PRD's prototype median bar of 3 minutes is exploratory and does not establish mean time savings.

### Quality guardrails

Compliance quality. Managers rate Compliance 3.9 and Reporting 4.5 in the scenario. Record correction/flag rates may not rise more than 2 points against concurrent control. A Fail-rate ratio below half of control triggers an audit of case mix, newly captured logs, real improvements, and rushed answers. It does not prove rubber-stamping. Both thresholds are PM planning judgments requiring the compliance owner's agreement before exposure. The snapshots supply no accuracy baseline. Manager CSAT is descriptive because managers see both arms. [VEL-01](../05-experimentation/experimentation-plan.md) owns the definitions and live stop rules.

### Readiness and decision window

The pre-build evidence gate covers five current-flow observations per account, checklist fit, eligible enrollment, baseline variance, and a feasible measurement and audit design. The binary planning approximation is 270 per arm for 48% versus 60%, at 80% power and two-sided 5% significance. The daily-rate design must pass its own power check. Insufficient enrollment holds the build for recruitment or a newly powered protocol.

Weeks 1 and 2 build and test the implementation. The pre-exposure implementation gate then checks telemetry, persistence, write guards, prototype usability, and the canary before randomization. Read efficacy after 14 days, planned as pilot weeks 3 and 4 if both gates pass on schedule. A gate delay moves the read rather than shortening the test. Monitor safety throughout. Apply [VEL-01's ordered policy](../05-experimentation/experimentation-plan.md). Investigate invalid data and pause on guardrail concerns. Stop confirmed severe harm. Ship only when all evidence bars hold. Kill a sufficiently precise nonpositive result, and iterate on remaining inconclusive or small effects without rollout.

## Finalized product hypothesis

> Based on dispatchers who "can't trust the board" and the scenario's 14.6-minute mean compliance step, I believe removing observed interface friction will increase fleet coordinators' daily compliance completion by at least 12 points versus concurrent control. I will protect compliance quality and decide at the fixed day-14 read. Enrollment, checklist fit, measurement design, and power must clear before build, with the implementation verified before exposure.

## Success metrics

| Metric | Type | Target | Why it matters |
|---|---|---|---|
| **Compliance completion** | Primary leading indicator | Pilot: +12 points versus concurrent control. Rollout: verified baseline +12 points, locked before exposure. Scenario illustration: 48% → 60%. | Measures the behavior B1 directly tests. **Read:** pilot day 14, then four weeks after switch-on. |
| **Workflow through handoff** | Lagging north star | Lock the projection before exposure using the verified completion target and matched-cohort handoff ratio. Scenario illustration: 60% × (31/48) = 38.75%, rounded to 39%. | Tracks completion beyond compliance. B3 could change this outcome too. **Read:** week 12 if rollout stays on schedule. |
| **Audited records and Fail rate** | Quality guardrails | Accuracy deterioration ≤ 2 points. Fail ratio below 0.5 triggers an audit. These planning judgments require agreement before launch. | Protects record quality. Confirmed harm blocks shipping. **Read:** live monitoring and the day-14 audit under VEL-01. |
| **Manager Compliance CSAT** | Descriptive trust signal | Scenario reference 3.9. Investigate a decline. | Managers see both arms, so this cannot estimate B1's causal effect. **Read:** pilot monitoring and week-12 follow-up. |

Prototype median ≤ 3 minutes remains a separate usability hypothesis. It is not the completion metric or evidence of mean time savings.
