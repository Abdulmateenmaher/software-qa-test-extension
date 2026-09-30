\# QA Extension — Product Requirements (Functional)



\## Purpose

This document describes the functional requirements for a Chrome extension that enables testers to capture visual feedback, log issues, and track statuses directly from any testing webpage into a central Firebase/Firestore database. The focus is strictly on user-facing behavior and data requirements (no technical implementation details).



\## Overview

The extension provides a small floating widget visible on test pages. Testers use the widget to capture a screenshot of the visible page, complete a short form (tester name, status, comments), and submit the log to the central database. Each submission includes automatic timestamping and stores the screenshot for later review.



\## Target users

\- QA testers doing manual testing of websites

\- Product owners and developers who need reproducible visual bug reports

\- Test coordinators tracking progress across multiple test sites



\## Goals

\- Make reporting visual bugs extremely fast (one to three clicks)

\- Preserve contextual screenshots and descriptive comments with each report

\- Track issue status (Fixed / Not Fixed / Assigned) for easy triage

\- Provide clear confirmation that a report was saved



\## Where the widget appears

\- The extension injects a floating action icon onto the active page under test.

\- The icon remains fixed on screen (e.g., bottom-right) and overlays above page content so it is always visible while testing.

\- The widget only appears on approved test sites (limit to the defined list of target sites; see “Target sites” section).



\## Main user interactions

1\. Click floating icon to open the reporting panel.

2\. In the panel, optionally capture a screenshot of the visible browser area.

3\. Complete the form fields (tester name, select status, add comments).

4\. Submit the report.

5\. Receive immediate visual confirmation of success and automatic close/reset of the form.



\## Core features (user-facing)

\- Floating widget:

&#x20; - Clearly labeled and easy to click (e.g., “QA” badge).

&#x20; - Persistent on screen regardless of scroll.

\- In-panel screenshot capture:

&#x20; - Single-button to capture current visible page.

&#x20; - Thumbnail preview of the captured image shown in the panel.

\- Data entry form:

&#x20; - Tester name (required)

&#x20; - Issue status (single choice): Fixed, Not Fixed, Assigned

&#x20; - Comments / reproduction steps (multi-line)

\- Submit and confirmation:

&#x20; - Single-submit button that saves all data as a single record.

&#x20; - Immediate success message once saved.

&#x20; - Form resets or closes after successful save.

\- Scope control:

&#x20; - Widget appears only on the defined list of test websites (no appearance on unrelated sites).



\## Submission contents (what must be stored for each record)

\- Tester name (user-entered)

\- Issue status (Fixed / Not Fixed / Assigned)

\- Comments (free text)

\- Screenshot (visual evidence of the page at time of submission)

\- Timestamp (automatic date \& time of submission)

\- Origin site (which test site/page the report was created on)

\- Optional: identifier of the page / URL for navigation and context



\## UX details and validation

\- Tester name is required; show inline validation if empty.

\- Status must be chosen; default may be preselected but user can change.

\- Screenshot is optional but encouraged; if captured, show a clear thumbnail and allow retake before submission.

\- Provide clear success and error messages in natural language (e.g., “Log submitted — thank you!” or “Could not save. Please try again.”).

\- Minimize friction: prefer modal/panel that overlays but does not block the page content.



\## Acceptance criteria (when a feature is “done”)

\- A floating widget appears on approved test pages and opens a panel when clicked.

\- A tester can capture a screenshot and see a thumbnail preview inside the panel.

\- A tester can fill out name, pick a status, add comments, and submit.

\- A submission creates one complete record containing all required fields and a timestamp.

\- After successful submission, the UI displays a confirmation and the panel closes or resets.

\- The widget does not appear on sites outside the approved target list.



\## Test cases (functional)

\- Open a target test site and verify the widget is visible.

\- Click widget, click capture, and confirm thumbnail preview displays the visible page.

\- Submit with all fields filled and confirm a success message appears.

\- Submit without tester name and confirm validation prevents submission.

\- Change status selection and verify the selected status is recorded.

\- After submission, open another page from the same test site and confirm the widget still shows.

\- Open a non-target site and confirm the widget does not appear.



\## Privacy \& data considerations (functional)

\- The system stores screenshots and comments as part of the report; testers must be informed that visual captures may contain sensitive information visible on the page.

\- The UI should present a short privacy notice or reminder before the first capture, clarifying what is saved and who can access it.

\- There should be an option to redact or avoid capturing sensitive data prior to submission (user-level guidance, not automatic redaction).



\## Workflow examples (user stories)

\- As a tester, I want to capture a visual of a layout bug, add reproduction steps, and mark it "Not Fixed" so developers can reproduce and fix it.

\- As a QA lead, I want all submissions to include who reported them and when, so I can track progress and ownership.

\- As a developer, I want a screenshot and clear comments attached to each report so I can triage and assign remediation.



\## Target sites

\- Limit the widget to a curated list of up to 10 test sites (examples / placeholders below). Replace these placeholders with your real testing domains:

&#x20; 1. test-site-1.example.com

&#x20; 2. test-site-2.example.com

&#x20; 3. test-site-3.example.com

&#x20; 4. test-site-4.example.com

&#x20; 5. test-site-5.example.com

&#x20; 6. test-site-6.example.com

&#x20; 7. test-site-7.example.com

&#x20; 8. test-site-8.example.com

&#x20; 9. test-site-9.example.com

&#x20; 10. test-site-10.example.com



\## Post-submission UX (functional)

\- Provide a clear success toast or dialog after submit.

\- Optionally provide a simple way to copy or view the stored record ID or link for reference (so the tester can communicate the report with developers).

\- Reset form fields after success to support multiple quick submissions.



\## Future enhancements (product ideas)

\- Attach browser metadata (viewport size, user agent) to help reproduction.

\- Allow optional tagging (e.g., Severity: Low/Medium/High).

\- Support assigning reports to a team member from the popup (status “Assigned” with assignee).

\- Enable optional comment threading or follow-up notes on the saved record.

\- Provide dashboard views for QA leads to filter and export logs.



\## Summary

This extension is a simple, high-impact tool for manual QA that turns ad-hoc visual feedback into structured, timestamped records. The functional focus is speed, clarity, and consistent data so teams can triage and act on visual bugs quickly.

