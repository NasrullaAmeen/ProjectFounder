# Requirements

> **In plain terms:** what the system must actually do, derived from every MVP-tier feature in `FEATURES.md`. Written by `workflows/requirements.md`'s `requirements` step (§ 7.9 Requirements Engine) against `examples/bookmark-manager/FEATURES.md`, `CONSTRAINTS.md`, and `ASSUMPTIONS.md`.

Each requirement traces to one `FEATURES.md` entry. V1/V2/Future-tier features don't have requirements yet — this covers MVP only, per `skills/requirements/SKILL.md`'s own procedure.

| ID | Type | Feature | Statement | Acceptance criteria | Classification (§ 163.4) |
|---|---|---|---|---|---|
| REQ-001 | Functional | Capture | The system SHALL allow a user to save a URL as a bookmark from the web app, PWA, or browser extension. | GIVEN a user is authenticated (or using a single-user self-hosted instance) WHEN they submit a URL to save THEN the bookmark appears in their bookmark list within the same session. | executable |
| REQ-002 | Functional | Organization (folders) | The system SHALL allow a user to organize bookmarks into folders. | GIVEN a user has at least one bookmark WHEN they assign it to a folder THEN the bookmark appears under that folder and no longer only in the unfiled view. | executable |
| REQ-003 | Functional | Search (keyword) | The system SHALL allow a user to find a saved bookmark by keyword matching its title or URL. | GIVEN a user has saved a bookmark with a distinctive title WHEN they search that title's keyword THEN that bookmark appears in the results. | executable |
| REQ-004 | AI | Semantic Search | The system SHOULD allow a user to find a saved bookmark by meaning, not just exact keyword match. | GIVEN a user has saved a bookmark about a topic WHEN they search using different wording for the same topic THEN that bookmark still appears in the results. | judged — no mechanical relevance-quality check exists yet |
| REQ-005 | Non-functional | Search indexing | The system SHALL index a newly saved bookmark for search within a bounded time of it being saved. | GIVEN a bookmark was just saved WHEN a fixed short interval has passed THEN a search for that bookmark's content returns it. | judged — the specific interval is an architecture/performance decision (Phase 3), not yet made |
| REQ-006 | Functional | Import | The system SHALL allow a user to import bookmarks from a standard browser bookmark export file. | GIVEN a user has a browser bookmark export file WHEN they upload it THEN each valid bookmark in the file appears in their account. | executable |
| REQ-007 | Functional | Export | The system SHALL allow a user to export all of their bookmarks to a file they can save outside the system. | GIVEN a user has saved bookmarks WHEN they request an export THEN they receive a file containing every one of their saved bookmarks. | executable |
| REQ-008 | Security | Authentication | The system SHALL require authentication to access a user's bookmarks on the hosted (cloud) deployment. | GIVEN a user is not authenticated WHEN they attempt to view a bookmark list on the hosted deployment THEN access is denied. | executable |
| REQ-009 | Functional | Sync | The system SHALL reflect a bookmark saved from one client (web, PWA, or extension) in the others for the same account. | GIVEN a user saves a bookmark from the browser extension WHEN they open the web app for the same account THEN that bookmark is present. | executable |
| REQ-010 | Functional | Browser Extension | The system SHALL provide a browser extension that can save the current page as a bookmark in one action. | GIVEN a user has the extension installed and is authenticated WHEN they click the extension's save action on any page THEN that page is saved as a bookmark. | executable |
| REQ-011 | Security | Extension permissions scoping | The browser extension SHALL request only the browser permissions required to read the current tab's URL/title and submit a bookmark, not broad host permissions across all sites by default. | GIVEN the extension's manifest WHEN its requested permissions are reviewed THEN none exceed what capturing the current page requires. | judged — no automated manifest-permission check exists yet |

**Executable/judged ratio (§ 163.4):** 8 of 11 executable, 3 judged (REQ-004, REQ-005, REQ-011 — each blocked on a decision or check that doesn't exist yet, not on ambiguity in the requirement itself).

## Conventions

- A requirement with no traceable `FEATURES.md` source shouldn't exist — if one is needed, add the feature first.
- V1+ requirements get written when that tier is scoped for active work, not preemptively.
