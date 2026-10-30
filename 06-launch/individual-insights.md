# Individual Insights: Development Process

Module 6 · Deliverable 6 (reflection). Scenario: RouteLogic Velocity.

## Friction points

**The biggest technical or strategic challenge you faced while developing your product concept.**

Letting go of the persona. I spent two modules on the driver. Seven of the 12 research notes came from drivers, and the three-tap doorstep moment was vivid. Then the Module 3 data put the driver outside the coordinator's workflow funnel. Drivers rated Core Dispatch 4.3, the best frontline score in the table. Coordinators rated Compliance 2.2 while 77% of them used it every day. I moved the persona to the coordinator and the friction to compliance logging. It also changed my Module 1 value proposition. I had counted compliance among the layers to move off frontline screens, and the data said it is core frontline work.

Writing a guardrail that can fail. My first guardrail was "no rise in incomplete or failed records". B1 blocks submit until every check has an answer, so incomplete records can't happen in the variant. More Fails can also mean more honest logging. The real risk of a faster form is coordinators tapping Pass without checking. So the guardrails became record accuracy and a Fail rate that must not collapse.

Planning a launch before the result exists. The GTM plan had to be written while the experiment hadn't run. A cold pressure test caught a timing bug: the manager email carried the pilot result a week before the result existed.

## Key learnings

**A few surprising discoveries or insights you gained from the course overall.**

- **The Now lane holds one item.** The primary metric depends on one step, and the pilot has two engineers for four weeks. A second Now item would have split them. Six features went to the cut list.
- **My instincts needed the same audit as the AI.** Two of my three quick-win picks were wrong. B6 doesn't move the metric, and B5 shows the drop without removing it. The AI was wrong too. It scored B1's effort as 3 and still called it low, which breaks the framework's own cut-off of 1 or 2.
- **Behavioral data beat stated pain.** No interview mentions compliance. The funnel, the time gap and the CSAT cell all point at it.
- **A release is not a launch.** During the pilot, announcing B1 would contaminate the control arm. The launch only happens if the pilot ships, because go-to-market can amplify a proven result but can't create one.
- **B2B changes the experiment.** A pilot of about 540 coordinators sits below the usual 1,000-user guide for an A/B test. Measuring each coordinator's daily rate is what makes the test readable.

## Aha! moment

**Your main "aha" moment during the project process.**

The CSAT heatmap in Module 3. I went looking for the cell that matched my driver's misery, and it scored 4.3. Our persona was satisfied where I had placed the pain. The lowest score sat one row over: coordinators rating a feature they use every day at 2.2. The research had told me where people complain. The usage data told me where the workflow breaks, and those were different places.

Not yet proven: VEL-01 hasn't run, so B1's lift is a hypothesis. Whether every account can use the same 12 checks is also unknown.
