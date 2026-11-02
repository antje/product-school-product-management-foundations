# Individual Insights: Development Process

Module 6 · Deliverable 6 (reflection). Scenario: RouteLogic Velocity.

## Friction points

**The biggest technical or strategic challenge you faced while developing your product concept.**

Letting go of the persona. I spent two modules on the driver. Seven of the 12 research notes came from drivers, and the three-tap doorstep moment was vivid. Then the Module 3 data put the driver outside the coordinator's workflow funnel. Drivers rated Core Dispatch 4.3, the best frontline score in the table. Coordinators rated Compliance 2.2 while 77% of them used it every day. I moved the persona to the coordinator and the friction to compliance logging. It also changed my Module 1 value proposition. I had counted compliance among the layers to move off frontline screens, and the data said it is core frontline work.

Writing a guardrail that can fail. My first guardrail was "no rise in incomplete or failed records". B1 blocks submit until every check has an answer, so that would mostly test the form's validation. It would not tell me whether anybody checked the vehicle. More Fails can mean more honest logging. Fewer can mean better maintenance, a different mix of routes or rubber-stamping. I now use record audits and the Fail rate to decide where to look, rather than treating one rate as proof.

Planning a launch before the result exists. The GTM plan had to be written while the experiment hadn't run. A cold pressure test caught a timing bug: the manager email carried the pilot result a week before the result existed.

## Key learnings

**A few surprising discoveries or insights you gained from the course overall.**

- **The Now lane holds one item.** The primary metric depends on one step, and the pilot has two engineers for four weeks. A second Now item would have split them. Six features went to the cut list.
- **My instincts needed the same audit as the AI.** Two of my three quick-win picks were wrong. B6 doesn't move the metric, and B5 shows the drop without removing it. The AI was wrong too. It scored B1's effort as 3 and still called it low, which breaks the framework's own cut-off of 1 or 2.
- **Behavioral data beat stated pain.** No interview mentions compliance. The funnel, the time gap and the CSAT cell all point at it.
- **A release is not a launch.** During the pilot, announcing B1 would contaminate the control arm. The launch only happens if the pilot ships, because go-to-market can amplify a proven result but can't create one.
- **B2B changes the experiment.** I wrote 540 coordinators into the plan before confirming the accounts had them. Repeated days from one person are not extra independent users. Enrollment, the full-day metric and power have to clear before the build. If they do not, I need more accounts or a revised protocol.
- **A fast prototype is not a measured saving.** I also subtracted a proposed 3-minute median from a 14.6-minute scenario mean. Those are different statistics, and the target had not been measured. The pilot must collect comparable durations before I put a time-saving claim in front of a buyer.

## Aha! moment

**Your main "aha" moment during the project process.**

The CSAT heatmap in Module 3. I went looking for the cell that matched my driver's misery, and it scored 4.3. Our persona was satisfied where I had placed the pain. The lowest score sat one row over: coordinators rating a feature they use every day at 2.2. The research had told me where people complain. The usage data told me where the workflow breaks, and those were different places.

Not yet proven: VEL-01 hasn't run, so B1's lift is a hypothesis. The pre-build evidence gate tests checklist fit, eligible enrollment, power and whether recording friction explains the problem. Working telemetry, write guards, usability and the canary are checked after build, before anyone enters the randomized test.

The stopping rule is part of what I learned. Under [VEL-01](../05-experimentation/experimentation-plan.md), no valid +12-point lift against concurrent control means no rollout. Confirmed severe harm stops exposure when it appears, without waiting for day 14. An inconclusive result earns a revised test, not a launch. A confidence interval entirely at or below zero ends this variant. After launch, failure to sustain the target locked from the verified baseline holds expansion and sends me back to the workflow. I want somebody else to be able to enforce those calls when I am still attached to the idea.

**Refined on 2 November 2026.** The pre-build evidence now includes checklist fit, eligible enrollment and power. First-use activation and time on task guide investigation. Neither substitutes for the controlled completion result.
