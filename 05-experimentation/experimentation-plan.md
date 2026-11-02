# Experimentation Plan

**Product:** RouteLogic Velocity · **Experiment:** VEL-01 One-Click Compliance Checklist · **Owner:** Antje Barth (PM) · **Sign-off:** CS lead and compliance owner

## Evidence and scope

VEL-01 has not run. The 48% completion rate and 14.6-minute mean are scenario references, not measurements of B1 or the proposed experimental cohort. The prototype demonstrates interface behavior on mock data. Its proposed median of 3 minutes is an unproven usability bar, not a measured reduction in mean task time.

## Overview

VEL-01 tests whether B1 changes coordinators' daily compliance behavior. The proposed pilot has two weeks to build and two weeks to test at three accounts. Its four-week plan starts after the pre-build evidence gate. The pre-exposure implementation gate follows the build in weeks 1 and 2. If that gate fails, hold randomization and move the read date. The experiment still gets its full 14 days.

**Why it matters.** Our largest account is trialing a leaner rival. The scenario's compliance step averages 14.6 minutes against a 3-minute benchmark. Whether navigation and retyping cause that gap is a hypothesis: no supplied interview describes compliance logging.

**Why this method.** An A/B test compares the B1 package with the existing flow. A login-bound feature flag controls exposure and rollback. A two-day canary at the end of week 2 checks stability before randomization. Its participants are excluded from the A/B sample because they have already seen B1. A multivariate test would ask about combinations and need more traffic. A fake door would measure interest, not completed, accurate logs.

**Pre-build evidence gate.** Antje records a pass or hold for each item before authorizing the two-week build. All must pass:

1. **Observe the job.** The CS lead observes five current-flow sessions per pilot account, 15 total. Record screens, retyped fields, checklist obligations, checking versus data-entry time, and why people leave. This small discovery sample tests the proposed mechanism, not lift. If B1 does not remove the observed obstacle, revise it before the build.
2. **Confirm checklist fit.** The compliance owner matches each pilot's required items and record format to B1. Known mismatches are ineligible until account-specific configuration is scoped and the plan re-estimated.
3. **Confirm enrollment and power.** Count eligible coordinators after canary exclusions, get prior daily rates, and check variance and account mix. The 540-person population is unconfirmed. If the available sample cannot meet the locked power calculation, hold, recruit more accounts, or approve a newly powered protocol before build and randomization.
4. **Approve the measurement and operating design.** The compliance owner defines a completed daily requirement, an accurate record, and comparable audit sampling and follow-up in both arms. The pilot engineer confirms that roster joins, both-arm telemetry, assignment, persistence, and rollback fit the build estimate. Antje approves the analysis method, boundaries, audit capacity, staffing, and proposed 14-day window. These are design and feasibility decisions, not tests of an implementation that has not been built.

**Pre-exposure implementation gate, after the build.** Before day 1 of randomization, the pilot engineer verifies both-arm telemetry, denominator joins, assignment, production persistence, write guards, and rollback. The CS lead completes the PRD's 15 prototype usability sessions after build, distinct from the 15 current-flow observations before build. Then run the two-day canary planned for the end of week 2. Antje and the compliance owner confirm that the tested behavior, audit process, enrolled sample, and locked analysis still match the protocol. A failure holds exposure and moves the planned test and launch dates.

**Instrumentation.** PRD M6 checklist events alone cannot count non-users. Join assignment and account/coordinator IDs to the work roster, route/shift obligations, app opens, completed records in both flows, block reasons, corrections, and audit outcomes. These joins and missing-event handling must pass the pre-exposure implementation gate and canary. A failed denominator or control-arm check holds randomization.

## Test definition

| Element | Detail |
|---|---|
| Hypothesis under test | B1 increases daily compliance-step completion by at least 12 percentage points versus concurrent control without degrading records. |
| Experiment design (A/B, etc.) | 50/50 by coordinator within each of three eligible accounts, through a login-bound flag. |
| Primary metric | Each coordinator's fraction of scheduled workdays with required compliance logging completed. Compare arm means at a fixed account mix. |
| Guardrail metric | Audited record accuracy and the Fail-rate audit trigger. |
| Decision rule (ship / kill / pivot) | Apply the ordered table below at day 14. No rollout on an invalid, inconclusive, underpowered, or harmful result. |

## Parameters

| Parameter | Decision |
|---|---|
| Feature under test | B1 after observation and checklist-fit confirmation |
| Persona | Fleet coordinator responsible for daily compliance logging |
| Expected outcome | Required logs completed in RouteLogic by shift end |
| Primary success metric | Account-standardized difference between coordinator daily completion rates |
| Baseline rate | 48%, scenario reference among daily app-openers. Validate on the experimental denominator before build |
| Guardrail boundary | Audited correction/flag rate no more than 2 points above concurrent control |
| Second guardrail | Fail-rate ratio, variant/control, below 0.5 triggers an audit and pauses shipping |
| Minimum worthwhile effect | +12 percentage points versus concurrent control |
| Planning sample | 270 per arm, 540 total. Final eligible sample and power checked before build |
| Traffic split | 50/50 within each account |
| Test duration | 14 days after build and canary, two full weekly dispatch cycles |
| Significance threshold | Two-sided p < 0.05. 95% confidence interval wholly above zero |

## Measurement and analysis

### Tested package

Test the scoped B1 package, not its individual components. Observation may change it before the protocol locks. A material change after exposure requires a new test.

### Eligible coordinators

Fleet coordinators with compliance responsibility, enrolled before randomization. The coordinator focus follows the funnel and CSAT evidence in [Hypothesis & Success Metrics](../03-analytics/hypothesis-and-metrics.md).

### Expected behavior

Coordinators complete their required daily compliance logs in RouteLogic. Observation establishes today's workflow and workaround. The experiment tests the change.

### Primary estimator

Enroll coordinators scheduled for compliance work in both test weeks. For each coordinator, divide completed compliance workdays by scheduled workdays in the 14-day window. Fix the denominator from the roster before assignment. A successful day requires all required route/shift compliance logs completed by shift end, using the obligation definition the compliance owner approved before randomization. Non-use, including no app open, counts as zero. Remove planned absences before assignment. Do not drop unplanned non-use afterward.

Average daily outcomes within each coordinator. Calculate variant minus control mean within each account, then weight those differences by the account's share of the eligible population fixed before assignment. This difference, Δ, is the primary estimate. Use coordinator-level variance within account strata for the confidence interval and p-value. Daily observations are not independent extra users. The pre-build power check uses this estimator. Broken telemetry makes the read invalid, not a zero-use result.

### Baseline

The scenario's 48% uses daily app-openers. Our fixed roster also includes non-openers, so re-estimate baseline and variance on that exact base using the prior two full dispatch weeks before locking power. The scenario's 48/71 ≈ 68% and 60/71 ≈ 85% are daily conditional funnel ratios, not weekly first-use targets.

### Quality guardrails and live monitoring

- **Record accuracy:** share of submitted logs corrected or flagged under the same audit sampling and follow-up protocol in both arms. More than +2 points versus control pauses exposure and triggers investigation. Two points is a PM planning judgment, agreed with the compliance owner before exposure using baseline audit variation. Incomplete required audits at day 14 mean no ship.
- **Fail rate:** share of matching required items marked Fail. A variant/control ratio below 0.5 triggers an audit and pauses shipping. This PM screening judgment is agreed before launch. It does not prove rubber-stamping or statistical significance. Check case mix, newly captured low-risk logs, real improvements, and rushed answers. All-Pass logs under 20 seconds are one diagnostic: 20/12 is under 2 seconds per item, a sensitive screen that may flag legitimate pre-checked work. With zero or too few control Fails, use the agreed audit instead of declaring the ratio passed.

Antje and the compliance owner monitor harm daily. Antje orders immediate flag rollback through the pilot engineer on confirmed severe harm. The engineer is the backup flag operator. Severe means an incorrect B1 record caused an unsafe operational decision, or a matched audit confirms deterioration above +4 points, twice the agreed accuracy boundary. Other boundary breaches pause exposure pending an audit within two working days. A positive lift cannot override confirmed harm.

Manager Compliance CSAT has a planning floor of 3.9, its scenario baseline. Managers see both arms, so it cannot identify an arm effect. A decline or written compliance concern triggers investigation.

### Minimum Detectable Effect (MDE)

+12 points versus concurrent control. The PM's planning judgment is to recover roughly half the scenario's 23-point assignment-to-compliance leak: 12/23 ≈ 52%. This explains the bar. It does not validate the mechanism.

### Sample and power

The independent binary-outcome approximation gives n = 269.6, rounded up to 270 per arm, for 48% versus 60%, 80% power, and two-sided 5% significance. This is a planning calculation, not a power guarantee for the daily-rate estimator or extra shipping conditions. Verify enrollment and re-power from prior daily-rate variance, fixed account weights, and the segment/persistence checks before build.

Fewer eligible users means hold and recruit, or agree a new design, sample, and read date before exposure. Repeated days, CUPED, or account stratification do not automatically rescue low power. The signed protocol locks the sample and analysis. An insufficient sample at read-out cannot produce a ship.

### Assignment and duration

Randomize 50/50 within account to preserve precision. Assignment follows login on shared devices. Run 14 days after the canary. Check assignment and sample ratio at launch and daily. An unexplained sample-ratio p < 0.001 triggers a data hold. This planning alarm limits false alerts from ordinary imbalance. Do not interpret efficacy until assignment and exposure are resolved.

### Statistical threshold

One primary comparison, two-sided p < 0.05 with its 95% interval wholly above zero. Account, shift, and tenure slices are diagnostic except for the locked account check below. A post-hoc segment cannot rescue the primary result.

## Control and variant

### Control (A)

The existing compliance flow, unchanged. Its scenario average is 14.6 minutes against a 3-minute benchmark. Several screens and retyped driver, vehicle, or route details are proposed causes, not observed facts. The 15 pre-build sessions establish the sequence and where time goes. If substantive inspection rather than interface friction explains the gap, change the variant and target before build.

### Variant (B)

- **Today's Routes:** checklist entry from an assigned route. Missing driver or vehicle blocks entry with an explanation.
- **Compliance Checklist:** read-only system fields, initially blank checks, a reason on Fail and a note for Other. Saving is blocked until complete.
- **Compliance Logged:** complete record with failed items first, reasons, and elapsed time.
- **Rules:** FR1–FR7 in the [PRD](../04-roadmap/simplified-prd.md), plus the measurement contract above. Obligations and record format match control.

### Isolation

Route assignment, optimizer, dispatch board, handoff, daily reports, driver app, checklist obligations, record format, and app version stay the same in both arms. General onboarding is identical and never demonstrates B1 before assignment. Exclude canary participants. Log crossovers and analyze original assignment. No other Velocity change ships during the test.

## Shipping criteria

### Hypothesis

I believe the observed-friction version of B1 will lift fleet coordinators' daily compliance completion by at least 12 points versus concurrent control over 14 days, while protecting accurate records. Both mechanism and effect remain unproven.

### Ordered decision policy

Antje applies this table in order. The first matching row decides the outcome.

**Shipping evidence.** Every condition must hold:

- Δ ≥ +12 points, two-sided p < 0.05, and a 95% interval wholly above zero.
- Completed audits within the accuracy boundary, with Fail-rate concerns resolved.
- Positive effects in at least 2 of 3 accounts.
- A positive week-2 effect at least half of week 1's effect.

| Order | Condition | Decision and consequence |
|---|---|---|
| 1 | Assignment, telemetry, required sample, or the locked audit read is invalid or incomplete | **Investigate, no ship.** Hold exposure and rollout. Live harm stops still apply. Repair and rerun under a newly locked protocol if the causal read cannot be recovered. |
| 2 | Severe B1 harm is confirmed | **Stop / kill this variant.** Disable B1, return to the old flow, and log the cause before redesign. This action can occur before day 14. |
| 3 | Accuracy exceeds +2 points, a Fail-rate audit or compliance concern is unresolved, or an account's completion effect has a 95% interval wholly below zero | **Pause / investigate.** No expansion. Resolve the affected account and records before proposing another test. |
| 4 | All shipping evidence above is present | **Ship to eligible matching-checklist accounts**, starting with pilot accounts in week 5. |
| 5 | The primary 95% interval is wholly at or below zero | **Kill this variant.** The sufficiently precise nonpositive result rejects it. Re-score the roadmap. |
| 6 | Every remaining valid result, including small positive lift, an interval crossing zero, or failed persistence/account checks | **Iterate, no rollout.** Investigate the mechanism and plan a sharper variant or more accounts before a new test. |

The half-week persistence bar is a PM planning judgment screening a novelty-only result, not proof of durability. The 2-of-3 sign check prevents one account carrying the claim. A third account's noisy negative estimate is not automatically harm. Row 3 defines the harmful-account stop.

Read efficacy only at the end of day 14, planned as the end of pilot week 4 if both gates pass on schedule. Do not inspect interim lift to stop for success or change targeting, variant, or metric. Daily safety and data monitoring continue throughout. Report Δ, uncertainty, account effects, persistence, guardrails, and sample validity together. Log every outcome and rationale. Report elapsed-time mean and median separately. Subtracting the prototype median from the scenario mean cannot establish time savings.

## Findings & decision

**Not run.** There is no measured lift, guardrail result, or ship decision. The prototype demonstrates interface behavior on mock data. VEL-01 remains a proposed test. The pre-build evidence gate and pre-exposure implementation gate are both outstanding.
