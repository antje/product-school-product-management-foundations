# B1 One-Click Compliance Checklist, Simplified PRD (RouteLogic)

**Owner:** Antje Barth · **Status:** Proposed pilot specification · **Persona:** fleet coordinator

The hosted session prototype demonstrates the interaction, with limitations in the [prototype findings](prd-and-prototype.md). It does not establish production persistence, record accuracy or time savings. The supplied 14.6 minutes is a scenario mean, and the median ≤3-minute usability bar is unproven. [VEL-01](../05-experimentation/experimentation-plan.md) defines readiness, measurement and shipping decisions.

---

## Product direction

- **Vision:** A coordinator records compliance from the assigned route, with each answer explicit and the saved result visible.
- **Proposed benefit:** **RouteLogic would put compliance recording in one checklist.** The scenario's mean logging time is 14.6 minutes against a 3-minute benchmark. Its coordinator funnel falls from 71% at route assignment to 48% at compliance. B1 tests whether reusing route details and reducing navigation removes recording friction. No supplied interview describes compliance logging, so current-flow observation must verify the mechanism before build.

  **Every check starts blank.** A Pass takes one tap. A Fail needs a reason. Submit saves only a complete response. The proposed record format and correction process must be confirmed with the compliance owner. A tap proves an answer was recorded, not that a physical check occurred.
- **Success metric:** +12 points in daily compliance completion versus concurrent control, using [VEL-01's fixed workday denominator and ordered policy](../05-experimentation/experimentation-plan.md). The scenario's 48% → 60% illustrates that effect, not an absolute ship rule.
- **Guardrail:** audited correction/flag deterioration ≤ 2 points versus control. A Fail-rate ratio below 0.5 triggers an audit and pauses shipping. These planning boundaries require compliance-owner agreement before exposure. Manager CSAT is descriptive because managers see both arms.

---

## Product requirements

### User stories

**US1. Open a checklist with route details filled in (M1, M2)**
As a fleet coordinator, I want to open a pre-filled checklist from the route I just assigned, so that I never re-type data RouteLogic already has.
- From the route row, it takes 1 tap to open the checklist.
- All 6 header fields (driver, vehicle, route, date, shift, coordinator) match the route record exactly.
- None of the header fields can be edited. The coordinator types 0 characters to complete the header.
- If the route has no driver or vehicle assigned, the checklist does not open (see Edge Cases).

**US2. Answer each check with one tap (M3, M4)**
As a fleet coordinator, I want one tap per check and a reason only on a Fail, so that I can work through all 12 checks quickly without guessing.
- All 12 items start blank. No item is answered in advance.
- One tap records Pass or Fail. Tapping the other option changes the answer.
- Choosing Fail shows a reason list inline. Choosing a reason is one selection.
- Choosing the reason "Other" makes the note field required.

**US3. Submit once and know it is saved (M5, M6)**
As a fleet coordinator, I want to submit once and see that it saved, so that I can get back to dispatch knowing the record is complete.
- Before completion, Submit can be activated to reveal what is missing but cannot save. All 12 items, every Fail reason and any required Other note must be complete before a write.
- One valid tap saves one record for the account's date + route + shift key. Production must enforce uniqueness at storage, not only by disabling the button.
- The confirmation screen shows the number of passes and fails, each failed item with its reason, and the time taken.
- On the route list, that row changes from "Log compliance" to "Logged hh:mm".

### Screens

**Screen 1: Today's Routes (entry point)**
- Header: coordinator name, account name, date, shift.
- Table of 5 assigned routes. Each row shows route ID, driver, vehicle, departure time and an action button.
- Action button "Log compliance". It changes to "Logged hh:mm" after submit and opens nothing more.
- Rows with no driver or vehicle show the text "Assign a driver and vehicle before logging compliance" instead of the button.
- Not included: badges, counts or highlights that mark logs still outstanding. That is S1, and it is not in sprint 1.

**Screen 2: Compliance Checklist (feature core)**
- A "Back to routes" link.
- Pre-filled header card titled "From RouteLogic", with 6 read-only fields: driver, vehicle, route, date, shift, coordinator.
- A text link: "Details wrong? Fix them in route assignment". It returns to Screen 1 without saving.
- The checklist: 12 items on one scrolling page, with no tabs or pages. Each item has:
  - the item label
  - Pass and Fail buttons side by side, both unselected to start
  - on Fail: a reason dropdown (Missing, Expired, Damaged, Not performed, Other), plus a note field that is optional unless the reason is Other. Other requires at least 5 non-whitespace characters.
- A counter: "9 of 12 answered". A Fail counts as answered, even before its reason is chosen.
- A Submit button at the bottom. Validation priority is unanswered items, missing Fail reasons, then a missing or short Other note. Labels are "Answer 3 more", "Add 1 reason", "Add a note", and "Submit compliance log" when complete. Before completion, activation scrolls to and identifies the first missing input without saving. Only an in-progress or finished save disables activation.
- A discard dialog for leaving mid-checklist: "Leave without saving? Your answers will be lost." with Leave and Stay buttons.

**Screen 3: Compliance Logged (confirmation)**
- Headline: "Compliance logged for Route R-104 · Vehicle TRK-22".
- Summary line: "11 passed · 1 failed · Logged in 2:14 at 08:42".
- A list of failed items, shown at the top, with each reason and note.
- Primary button: "Back to today's routes". There is no "Next vehicle" button. That is S2.
- Prototype-only event log panel, collapsed by default. It lists M6 events with timestamps for interaction checks. Demo timestamps do not measure real-world logging speed.

### Functional requirements

| # | Rule | Source |
|---|---|---|
| FR1 | The checklist opens in 1 tap from any route row that has a driver and vehicle. All 12 items sit on one scrolling screen. | M1 |
| FR2 | 6 header fields are copied word for word from the route record. 0 fields can be edited. 0 characters are typed outside fail notes. | M2 |
| FR3 | 100% of items start blank. Each answer takes exactly 1 tap. There is no control that answers more than 1 item at once. | M3 |
| FR4 | Every Fail needs exactly 1 reason from the 5-option list. The reason "Other" needs a note of at least 5 non-whitespace characters. | M4 |
| FR5 | Submit saves only when all 12 items, Fail reasons and required Other notes are complete. Earlier activation shows the missing input and saves nothing. One valid tap writes one record with routeId, vehicleId, driverId, date, shift, coordinatorId, submittedAt and items[] containing itemId, result, reason and note. | M5 |
| FR6 | Within an account, at most 1 record exists for date + routeId + shift. Disable Submit during and after the save; production storage must reject duplicate keys across devices and reloads. The row shows "Logged hh:mm". The prototype demonstrates only session-level blocking. | M5 |
| FR7 | Events are logged with millisecond timestamps: `checklist_opened` (routeId), `item_answered` (itemId, result, on every change), `checklist_submitted` (routeId, recordId). Time taken is `checklist_submitted` minus `checklist_opened`. | M6 |

### Smart behaviors (Situation → Outcome)

| Situation | Outcome |
|---|---|
| Coordinator taps Fail on an item | The reason dropdown appears inline under that item and takes focus. |
| Coordinator chooses the reason "Other" | Require a note of at least 5 non-whitespace characters. If it is missing or short after the other fields are complete, Submit reads "Add a note". Activation focuses the note and saves nothing. |
| Coordinator switches an item from Fail to Pass | The reason and note are cleared, so no leftover reason is saved with a Pass. |
| Coordinator activates Submit while items are unanswered | Nothing saves. Scroll to the first unanswered item and show a text error with a visible outline until answered. |
| Every item answered, but a Fail has no reason yet | The counter shows 12 of 12. Submit reads "Add 1 reason". Activation focuses the missing reason and saves nothing. |
| All items, reasons and required Other notes complete | Submit reads "Submit compliance log". Activation saves once, then disables the control. |
| One or more items failed at submit | The record saves as complete, because a Fail is a valid answer. Screen 3 lists the failed items first. |
| Coordinator presses Back with any item answered | The discard dialog appears. Choosing Leave saves nothing. |
| Coordinator presses Back with nothing answered | Returns to Screen 1 with no dialog. |
| Date + route + shift already logged in this account | The row shows "Logged hh:mm". A second record is blocked. Corrections follow the agreed audit process rather than creating another log. |
| Route has no driver or vehicle | The checklist does not open. The row shows the "Assign a driver and vehicle" message. |

### Prototype constraints

- **No external APIs.** All data is hard-coded mock data: 1 coordinator, 1 account, 5 routes (1 of them with no driver), 12 checklist items, 5 fail reasons.
- **No login.** The coordinator is hard-coded.
- **useState only.** No Redux, Context, localStorage, IndexedDB or backend. Refresh resets the demo. Session-level duplicate blocking is not evidence of durable uniqueness. Production persistence, date-key uniqueness and the audit-correction integration must be implemented and verified before pilot exposure.
- **No routing library.** One state variable switches between the 3 screens.
- **No AI or model calls of any kind.** Nothing in this feature is generated.
- **Desktop only, 1280 px wide.** No mobile layout, because B4 is cut.
- **Events live in a state array** and appear only in the prototype event panel. No analytics SDK.

---

## Scope and delivery

### Scope exclusions

- A "Mark all as pass" button, or pass answers ticked in advance.
- AI-suggested answers, or carrying forward yesterday's answers (B2 territory).
- Any change to the compliance record format or to what the checklist legally requires.
- Mobile or native app (B4).
- Audit PDF export (B9).
- Manager dashboard (B8).
- Driver notifications (B6).
- Connecting to shift handoff (B3).
- In-app training (B10). The CS lead onboards the 3 accounts by hand.
- Third-party telematics integrations.
- Also held for later, as Should-Haves: S1 to S5. See the MoSCoW scope below.

### Edge cases and safety

1. **Route data missing.** A route with no driver or vehicle cannot open a checklist. The prototype never fills a gap with a guess or a default.
2. **Pre-filled details are wrong.** The header is read-only. The coordinator follows "Fix them in route assignment", so corrections happen in the existing flow. The checklist never holds data that differs from the route record.
3. **Coordinator leaves mid-checklist.** The discard dialog appears, and nothing is saved, so no partial record is created. In the event log, an open with no submit counts as abandoned.
4. **Double-tap on Submit.** Disable activation during the write. Production enforces the date + route + shift key even when two devices submit.
5. **Second log attempt for the same date, route and shift.** Block it under FR6. A new date permits the next scheduled log. Refreshing the prototype resets the demo and does not test persistence.
6. **"Other" chosen with an empty or short note.** Once other inputs are complete, Submit reads "Add a note". Activation focuses that note and saves nothing.
7. **Guard against automatic answers.** Copy header fields from the verified route record. Every saved item result must match the latest `item_answered` tap event for that item. A mismatch blocks saving. This checks interface behavior, not whether the coordinator performed the physical inspection. Audits and VEL-01's live safety monitoring address that separate risk.

### Decision rationale

| # | Decision | Rejected alternative | Why |
|---|---|---|---|
| D1 | Every item starts blank, with no bulk answer of any kind. | Answers ticked "Pass" in advance, or a "Mark all as pass" button. That would be the fastest option. | Pre-ticked answers could create a complete-looking record without an explicit response. Blank checks reduce that interface risk, but cannot prove a physical inspection. Timed sessions will test whether the proposed 12-item flow fits the 3-minute usability bar. |
| D2 | The "compliance not yet logged" marker (S1) stays out of sprint 1. The entry row only switches between "Log compliance" and "Logged hh:mm". | Status badges and an outstanding-count on Screen 1. | The marker nudges completion, but logging is no faster with it. Sprint 1 capacity goes to M1 to M6 so that 2 of the pilot's 4 weeks stay free for measuring. The "Logged" state exists only to block duplicate records (FR6). |

### Evals

| # | Eval | Target | How it is measured |
|---|---|---|---|
| E1 | **Time on task** | Proposed prototype median ≤ 3:00 from open to submit for the verified checklist. This is an unproven usability bar. | Five timed sessions per account, 15 total, using `checklist_submitted` minus `checklist_opened`. Record time spent checking versus entering data. The scenario's 14.6 is a mean; measure control and variant mean and median separately before claiming savings. |
| E2 | **Header mapping and record validation** | Every saved demo header matches its fixture; every required answer, reason and Other note passes FR4/FR5. | Run deterministic checks of all validation states and inspect the 15 usability sessions. These sessions do not establish production accuracy or truthful inspection. |
| E3 | **Write guards** | No result without a matching tap event; no write for missing assignment data; no duplicate date + route + shift record. | Test happy and failure paths, repeated taps and duplicate keys. The local demo covers session behavior; production storage, reload and multi-device cases require separate verification before exposure. A failed guard holds exposure. |

The 15 sessions assess usability and reveal problems. They do not prove completion lift, an error-rate bound or production reliability. E1 to E3 belong to [VEL-01's pre-exposure implementation gate](../05-experimentation/experimentation-plan.md#overview), after build weeks 1 and 2. The earlier pre-build evidence gate confirms observed mechanism, checklist fit, enrollment, power, feasible measurement/audit design and staffing, then starts the four-week plan. Before randomization, implemented both-arm telemetry, persistence/write guards, the 15 usability sessions and canary must pass. A failure holds exposure and moves the read without shortening the 14-day test. The pilot uses VEL-01's fixed workday denominator, ordered decision policy and live harm monitoring.

## MoSCoW scope

- **Must:**
  - M1 One-screen checklist, opened in one tap from the assigned route.
  - M2 Auto-fill of system data only, read-only.
  - M3 One tap per item, nothing pre-answered.
  - M4 A reason from a pick list for every Fail.
  - M5 Save only when all answers, Fail reasons and required Other notes are complete, in one action and the existing record format.
  - M6 Event logging: opened, item answered, submitted, time taken.
- **Should:**
  - S1 "Compliance not yet logged" marker.
  - S2 "Next vehicle" button after submit.
  - S3 Save and resume a draft.
  - S4 Keyboard-only use.
  - S5 A separate checklist per account, set in a config file.
- **Could:**
  - Items ordered by failure rate.
  - A photo on a failed item.
  - An admin screen for checklist items.
  - Telematics pre-fill, once its accuracy is checked.
  - A maintenance ticket from a failed item.
  - A mobile layout, if coordinators log away from their desks.
- **Won't (now):**
  - "Mark all as pass" or pre-ticked passes.
  - AI-suggested or carried-forward answers.
  - Changes to the record format or the legal checklist.
  - Mobile app (B4), audit export (B9), manager dashboard (B8), driver notifications (B6), handoff link (B3), in-app training (B10).
  - Third-party telematics.
