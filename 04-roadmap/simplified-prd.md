# B1 One-Click Compliance Checklist, Simplified PRD (RouteLogic)

**Author:** Antje Barth · **Status:** Draft · **Target:** High-Fidelity Prototype · **Persona:** fleet coordinator

---

## 1. The Big Picture
- **Vision:** A fleet coordinator logs every compliance check in about 3 minutes, right after assigning the route. No check counts as passed unless the coordinator confirmed it.
- **Press release:** **RouteLogic cuts compliance logging from 14.6 minutes to about 3.** Fleet coordinators assign routes, log compliance checks and hand off shifts every day. Compliance logging is where that day breaks. 71% of coordinators finish assigning routes, but only 48% go on to log compliance in RouteLogic. The new checklist opens with one tap from the route the coordinator just assigned. Driver, vehicle, route, date, shift and coordinator are already filled in from RouteLogic. The coordinator answers each check with one tap and submits once.

  **Faster, and the record stays complete.** Every check starts blank, so nothing counts as passed until the coordinator taps Pass. A failed check needs a reason from a short list. The log cannot be submitted until every check has an answer. Managers get the same compliance record they rely on today, filled in completely.
- **Success metric:** compliance-step completion, the share of coordinators who finish logging compliance checks in RouteLogic. Baseline 48%, target 60% across the 3 pilot accounts by the end of the 4-week pilot.
- **Guardrail:** record accuracy holds, meaning records corrected or flagged in audit do not rise. The share of checks marked Fail must not collapse, which would signal rubber-stamping. The CS lead also tracks manager Compliance CSAT, which must stay at 3.9 or higher.

---

## 2. The Details

### User stories

**US1. Open a checklist that is already filled in (M1, M2)**
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
- Submit stays inactive until all 12 items are answered and every Fail has a reason.
- One tap saves exactly one record for that route and shift.
- The confirmation screen shows the number of passes and fails, each failed item with its reason, and the time taken.
- On the route list, that row changes from "Log compliance" to "Logged hh:mm".

### Screens to build

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
  - on Fail: a reason dropdown (Missing, Expired, Damaged, Not performed, Other), plus a note field that is optional unless the reason is Other.
- A counter: "9 of 12 answered". A Fail counts as answered, even before its reason is chosen.
- A Submit button that sits at the bottom of the screen. It reads "Answer 3 more" while items are open, "Add 1 reason" when only fail reasons are missing, and "Submit compliance log" when complete.
- A discard dialog for leaving mid-checklist: "Leave without saving? Your answers will be lost." with Leave and Stay buttons.

**Screen 3: Compliance Logged (confirmation)**
- Headline: "Compliance logged for Route R-104 · Vehicle TRK-22".
- Summary line: "11 passed · 1 failed · Logged in 2:14 at 08:42".
- A list of failed items, shown at the top, with each reason and note.
- Primary button: "Back to today's routes". There is no "Next vehicle" button. That is S2.
- Prototype-only event log panel, collapsed by default. It lists M6 events with timestamps and is used to run the Evals.

### Functional requirements

| # | Rule | Source |
|---|---|---|
| FR1 | The checklist opens in 1 tap from any route row that has a driver and vehicle. All 12 items sit on one scrolling screen. | M1 |
| FR2 | 6 header fields are copied word for word from the route record. 0 fields can be edited. 0 characters are typed outside fail notes. | M2 |
| FR3 | 100% of items start blank. Each answer takes exactly 1 tap. There is no control that answers more than 1 item at once. | M3 |
| FR4 | Every Fail needs exactly 1 reason from the 5-option list. The reason "Other" needs a note of at least 5 characters. | M4 |
| FR5 | Submit saves only when 12 of 12 items are answered and every Fail has a reason. One tap writes one record with the fields routeId, vehicleId, driverId, date, shift, coordinatorId, submittedAt, and items[] holding itemId, result, reason and note. | M5 |
| FR6 | Only 1 record can exist per route per shift. After submit, the button is disabled within the same tap, and the route row shows "Logged hh:mm". | M5 |
| FR7 | Events are logged with millisecond timestamps: `checklist_opened` (routeId), `item_answered` (itemId, result, on every change), `checklist_submitted` (routeId, recordId). Time taken is `checklist_submitted` minus `checklist_opened`. | M6 |

### Smart behaviors (Situation → Outcome)

| Situation | Outcome |
|---|---|
| Coordinator taps Fail on an item | The reason dropdown appears inline under that item and takes focus. |
| Coordinator chooses the reason "Other" | The note field becomes required. Submit stays inactive until the note has at least 5 characters. |
| Coordinator switches an item from Fail to Pass | The reason and note are cleared, so no leftover reason is saved with a Pass. |
| Coordinator taps Submit while items are unanswered | Nothing saves. The page scrolls to the first unanswered item and outlines it in red until it is answered. |
| Every item answered, but a Fail has no reason yet | The counter shows 12 of 12. Submit reads "Add 1 reason" and stays inactive. |
| Last item answered and every Fail has a reason | Submit changes to "Submit compliance log" and becomes active. |
| One or more items failed at submit | The record saves as complete, because a Fail is a valid answer. Screen 3 lists the failed items first. |
| Coordinator presses Back with any item answered | The discard dialog appears. Choosing Leave saves nothing. |
| Coordinator presses Back with nothing answered | Returns to Screen 1 with no dialog. |
| Route already logged this shift | The row shows "Logged hh:mm". The checklist cannot be reopened for a second record. |
| Route has no driver or vehicle | The checklist does not open. The row shows the "Assign a driver and vehicle" message. |

### Technical constraints
- **No external APIs.** All data is hard-coded mock data: 1 coordinator, 1 account, 5 routes (1 of them with no driver), 12 checklist items, 5 fail reasons.
- **No login.** The coordinator is hard-coded.
- **useState only.** No Redux, Context, localStorage, IndexedDB or backend. A page refresh resets everything, as intended.
- **No routing library.** One state variable switches between the 3 screens.
- **No AI or model calls of any kind.** Nothing in this feature is generated.
- **Desktop only, 1280 px wide.** No mobile layout, because B4 is cut.
- **Events live in a state array** and appear only in the prototype event panel. No analytics SDK.

---

## 3. The Logistics

### Features out
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

### Edge cases & safety guard
1. **Route data missing.** A route with no driver or vehicle cannot open a checklist. The prototype never fills a gap with a guess or a default.
2. **Pre-filled details are wrong.** The header is read-only. The coordinator follows "Fix them in route assignment", so corrections happen in the existing flow. The checklist never holds data that differs from the route record.
3. **Coordinator leaves mid-checklist.** The discard dialog appears, and nothing is saved, so no partial record is created. In the event log, an open with no submit counts as abandoned.
4. **Double-tap on Submit.** The button disables within the same tap, so exactly 1 record is written.
5. **Second log attempt for the same route.** It is blocked by FR6.
6. **"Other" chosen with an empty note.** Submit is blocked.
7. **Safety guard against made-up answers.** Header fields are the only values the system writes. They are copied from the route record and never inferred. Every item result in a saved record must have a matching `item_answered` event from a tap. If any result has no matching tap event, the record does not save, and the eval counts it as a safety failure.

### Decision log

| # | Decision | Rejected alternative | Why |
|---|---|---|---|
| D1 | Every item starts blank, with no bulk answer of any kind. | Answers ticked "Pass" in advance, or a "Mark all as pass" button. That would be the fastest option. | A pass nobody checked is a guessed record, and it breaks the record accuracy guardrail. Even with one tap per item, 12 items fit inside the 3-minute target. |
| D2 | The "compliance not yet logged" marker (S1) stays out of sprint 1. The entry row only switches between "Log compliance" and "Logged hh:mm". | Status badges and an outstanding-count on Screen 1. | The marker nudges completion, but logging is no faster with it. Sprint 1 capacity goes to M1 to M6 so that 2 of the pilot's 4 weeks stay free for measuring. The "Logged" state exists only to block duplicate records (FR6). |

### Evals

| # | Eval | Target | How it is measured |
|---|---|---|---|
| E1 | **Time on task** | Median of 3:00 or less from open to submit for the 12-item checklist, against today's 14.6-minute baseline | `checklist_submitted` minus `checklist_opened`, in timed sessions with pilot coordinators. At least 5 sessions per account, 15 in total. |
| E2 | **Pre-fill accuracy and record completeness** | 100% of header fields match the mock route record. 100% of saved records have 12 of 12 items answered and a reason on every Fail. | Compare each saved record against the route record and FR4/FR5, across all 15 sessions. |
| E3 | **Safety triggers** | 0 item results without a matching tap event. 0 records written for routes with missing data. 0 duplicate records per route and shift. | Check the event log against the saved records. Any single occurrence blocks the prototype from going to the pilot. |

The primary metric, 48% to 60% compliance-step completion, is read in the 4-week pilot across the 3 accounts, not in the prototype. E1 to E3 decide whether the build is ready for the pilot.

## MoSCoW scope
- **Must:**
  - M1 One-screen checklist, opened in one tap from the assigned route.
  - M2 Auto-fill of system data only, read-only.
  - M3 One tap per item, nothing pre-answered.
  - M4 A reason from a pick list for every Fail.
  - M5 Submit blocked until every item has an answer, then saved in one action in the existing record format.
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

---
**Builder hook:** Build a working prototype based on this PRD. Use the User Story as the core flow, Functional Requirements as build constraints, and prioritize speed and clarity over visual complexity.
