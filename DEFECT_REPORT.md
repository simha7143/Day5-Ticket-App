# Defect Reports

## Defect 1: Incorrect Ticket Priority Sorting

- **Defect Type:** Logic defect
- **File:** app.py
- **Function:** sort_by_priority()
- **Problem:** Tickets were sorted alphabetically by priority instead of by urgency.
- **Expected Result:** High → Medium → Low.
- **Actual Result:** High → Low → Medium.
- **Root Cause:** The sorting function used the priority text directly as its sorting key.
- **Fix Applied:** Added a priority mapping to sort tickets in the correct order.
- **Test:** test_tickets_are_sorted_by_priority
- **Status:** Fixed and tested.

## Defect 2: Empty Ticket Title Accepted

- **Defect Type:** API validation defect
- **File:** app.py
- **Function:** create_ticket()
- **Problem:** The API accepted an empty ticket title.
- **Expected Result:** Empty or whitespace-only titles should return HTTP 400.
- **Actual Result:** An empty title returned HTTP 201 Created.
- **Root Cause:** The validation checked only whether the title was None.
- **Fix Applied:** Added string validation using strip() to reject empty and whitespace-only titles.
- **Tests:** test_empty_title_returns_400, test_missing_title_returns_400, test_whitespace_title_returns_400
- **Status:** Fixed and tested.

## Defect 3: Incorrect Resolved Status on UI

- **Defect Type:** UI defect
- **File:** app.py
- **Section:** STATUS_LABELS
- **Problem:** Resolved tickets appeared as Open on the screen.
- **Expected Result:** The screen should display the actual ticket status, Resolved.
- **Actual Result:** The screen displayed Open.
- **Root Cause:** The STATUS_LABELS mapping assigned Open to the Resolved status.
- **Fix Applied:** Changed the mapping from "Resolved": "Open" to "Resolved": "Resolved".
- **Test:** test_resolved_ticket_displays_real_status
- **Status:** Fixed and tested.