# PRD & Prototype Sprint

**Product:** RouteLogic Velocity · **Feature:** B1 One-Click Compliance Checklist · [Full specification](simplified-prd.md)

## Responses

### MoSCoW scope decisions

B1 One-Click Compliance Checklist. One screen, opened in one tap from the route the coordinator just assigned. Driver, vehicle, route, date, shift and coordinator are pre-filled, each check takes one tap, and the log submits once.

#### Must-haves

1. **M1** One-screen checklist, opened in one tap from the assigned route.
2. **M2** Auto-fill of system data only, read-only.
3. **M3** One tap per item, nothing pre-answered.
4. **M4** A reason from a pick list for every Fail.
5. **M5** Save only when all answers, Fail reasons and required Other notes are complete, in one action and the existing record format.
6. **M6** Event logging: checklist opened, item answered, submitted, time taken.

M6 is my override. The AI listed it as a pilot prerequisite, not a must-have, because logging works without it. It is needed for the interaction trace. The pilot also needs roster, assignment, both-arm completion and audit data to read +12 points versus concurrent control. [VEL-01 specifies those joins](../05-experimentation/experimentation-plan.md#overview).

#### Deferred scope

B5's "compliance not yet logged" marker is a should-have (S1). I initially planned it inside B1. Removing the marker still leaves the core recording flow intact. Whether the flow can meet the proposed 3-minute median needs timed sessions. S5, a separate checklist per account, stays out of this build. VEL-01 excludes mismatched accounts until configuration is scoped and the estimate is approved.

### Record integrity

Every item starts blank, there is no "mark all as pass", and every saved result must match a tap event (FR3 and Edge case 7). That prevents the interface from inventing answers. It does not prove the physical check happened. The PRD also names the 12-item list as an assumption: verify the actual checklist and checking time before treating 3 minutes as feasible.

### Prototype findings

I found a counting problem in the first prototype. With all 12 checks answered but one Fail still missing its reason, the first build showed "11 of 12 answered · Answer 1 more". The coordinator could not tell that a reason was missing. The specification had not defined how a Fail without a reason counts. The requirement is now explicit: a Fail counts as answered, and Submit reads "Add 1 reason" until every Fail has one. The second build shows "12 of 12 answered · Add 1 reason".

The first build also missed the early-submit behavior: an early Submit did not show which check was open. The second build outlines the first open check in red. One gap remains in the hosted prototype: with the reason "Other" and no note yet, Submit still reads "Answer 1 more". The required behavior is "Add a note" for a missing or short Other note. Incomplete Submit can reveal the missing field but cannot save. The pre-exposure implementation gate checks these messages.

### Working prototype

[Open the B1 checklist prototype](https://route-ready-checklist.lovable.app), built in Lovable from the Simplified PRD. The original second-build checks covered the functional rules and edge cases then specified. The Other-note label remains wrong. State is held only in the current session, so it does not demonstrate date-key uniqueness after refresh, durable records or an audit-correction integration. The pre-exposure implementation gate must verify those requirements. No 15-session coordinator usability study has run.

![Checklist with one failed check and its reason](images/prototype-checklist.png)

![Demo confirmation: 11 passed, 1 failed. The displayed 0:33 is not a coordinator usability measurement](images/prototype-confirmation.png)

![Early Submit outlines the first open check in red](images/prototype-early-submit.png)

### Stakeholder decisions

Stakeholders receive the specification and prototype together.

| Stakeholder | Evidence | Decision needed |
|---|---|---|
| Manager | Prototype route R-104, the scenario evidence and VEL-01 | Agreement to observe the job first, then test +12 points versus concurrent control with record quality protected |
| Eng Lead | Smart behaviors, date-key uniqueness, production persistence and measurement joins | A feasible estimate after the pre-build evidence gate, including the implementation checks, flag operation and rollback |
| Design Lead | The demonstrated happy path and the three screens | A high-fidelity design for the checklist row and the fail-reason panel |
