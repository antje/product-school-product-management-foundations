# Problem Hook & Value Proposition: RouteLogic Velocity

Initial discovery focused on drivers and delivery confirmation. Module 3's workflow and CSAT data moved the priority to coordinators and compliance logging. The [historical driver journey](../02-discovery/competitive-and-journey.md#historical-baseline-the-original-driver-journey) records the earlier reasoning. All business and workflow figures below come from the course scenario. B1's improvement has not been measured.

## Chosen scenario

**Path:** RouteLogic Velocity (B2B)

The scenario's largest enterprise account is trialing a leaner competitor while daily frontline use declines. I chose the operational simplicity problem because it connects a user workflow to an account decision.

## The strategic crisis

> RouteLogic risks becoming the reporting system managers buy while coordinators run the day elsewhere. The brief reports declining frontline use and our largest account's trial of a leaner rival. UXR-02 describes WhatsApp as "the real system". Losing that daily workflow threatens the reporting value, but the scenario does not quantify the revenue at risk or give the account's decision date.

## The moment of misery

> Coordinator completion falls from 71% at route assignment to 48% at compliance logging. The compliance step has a supplied mean of 14.6 minutes against a 3-minute benchmark, and coordinators rate it 2.2 out of 5 while 77% use it daily. This is the step to investigate first. The interviews describe WhatsApp and an untrusted dispatch board, but no interview describes compliance logging or proves that compliance is done off-platform. Before build, observe current-flow sessions and check whether recording friction explains the gap.

The driver problems remain in scope for separate engineering decisions: delivery confirmation takes three taps (UXR-01, BUG-2055), route changes arrive late (UXR-02, BUG-2044), and long routes can crash (UXR-03, BUG-2031). B1 does not fix them, so it cannot guarantee the renewal.

## Problem hook

> We must win back coordinators' daily use by removing verified compliance-recording friction, while preserving the records managers rely on.

## Value proposition

> For **fleet coordinators**, B1 would **reuse route details and make every compliance answer explicit in one checklist**, because **daily use is falling while our largest account evaluates a rival**. The pilot tests whether this improves completed daily logs without weakening record accuracy. The existing compliance obligations and record format stay in place.

This is a proposed benefit. The 3-minute prototype median is an unproven usability bar, not a measured reduction from the scenario mean. The [pre-build evidence gate](../05-experimentation/experimentation-plan.md#overview) must confirm the actual workflow, checklist fit, enrollment, power, feasible measurement/audit design and staffing. Passing it starts the four-week plan. Build weeks 1 and 2 implement the flow and measurement. The pre-exposure implementation gate then verifies telemetry, write guards, usability and the canary before randomization. A failed check delays exposure and the read, not the 14-day test duration.

## Decision rationale

**Business stakes.** The scenario reports declining daily use and the largest account trialing a rival. The account's revenue and decision date are missing. Obtain both before deciding whether the pilot can affect that decision.

**Evidence strength.** The scenario funnel, mean time and CSAT point to compliance across coordinators. They do not prove the cause. Observe five sessions per pilot account before build, as VEL-01 requires, and validate the baseline on its fixed workday denominator.

**Mechanism to validate.** B1 removes the proposed recording obstacle if route-field copying and checklist navigation are the time cost. If required physical checks consume most of the 14.6 minutes, a faster form cannot remove that work. The pre-build observation must settle this before the estimate is approved. Sync and crash failures need separate owners.

## Finalized hypothesis

> Based on dispatchers who "can't trust the board" and the scenario's 14.6-minute mean compliance step, I believe removing observed interface friction will increase fleet coordinators' daily compliance completion by at least 12 points versus concurrent control. I will protect compliance quality and decide at the fixed day-14 read. Enrollment, checklist fit, measurement design, and power must clear before build, with the implementation verified before exposure.

[Module 3 hypothesis and metric definitions](../03-analytics/hypothesis-and-metrics.md#finalized-product-hypothesis) · [VEL-01 measurement and ordered decision rules](../05-experimentation/experimentation-plan.md).

## Supporting evidence

[Current coordinator journey](../02-discovery/competitive-and-journey.md) · [Hypothesis and metrics](../03-analytics/hypothesis-and-metrics.md) · [B1 PRD](../04-roadmap/simplified-prd.md).
