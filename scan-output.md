# Issue-Scout scan 1 (2026-11-16)

## Funnel counts

| Stage | Count |
|---|---|
| Total retrieved (5 queries x 100) | 500 |
| Unique candidates after URL dedupe | 500 (no overlap between queries) |
| Ranked (after dropping assigned and >120-day-stale) | 425 (75 dropped as assigned; 0 stale) |
| Label tiers in ranked set | good first issue: 6, beginner: 0, help wanted: 4, other: 415 |
| Graded | 5 |
| Accepted | 4 |
| Rejected | 1 |

Query 1 = python, Query 2 = python "test", Query 3 = java, Query 4 = javascript, Query 5 = python "api". All five used `--state open --limit 100`.

Top 5 by ranking (rank order): 1) Gulliver #191, 2) pipOS #122, 3) pipOS #120, 4) pipOS #119, 5) pipOS #117. All five are tier 0 (`good first issue`), no assignee, updated 2026-11-14 to 2026-11-16, 0 comments. Order within the tier is newest `updatedAt` first.

Accepted issues are listed below in fit order (not rank order).

## Accepted

### 1. GV005: three fix-advice cases still suggest a rewrite that changes results
https://github.com/laaielichter/Gulliver/issues/191
- Found by: Query 1 (python). Ranking: rank 1; `good first issue` tier; updated 2026-11-16T17:50Z; 0 comments; no assignee.
- Maintainer activity: pass. Last 5 default-branch commits all 2026-11-16 (merges by laaielichter, fixes by dianatofficial).
- Repository in use: pass. Pushed 2026-11-16, latest release 2026-11-12, not archived, many merged outside PRs today.
- Newcomer-sized scope: pass. One rule (GV005) in `src/gulliver/lint.py`, three listed cases plus exact-text tests; no refactor or migration required.
- Issue has enough direction: pass. Exact commands, current vs expected text, file and test names, "Done when" checklist.
- Not already being worked on: pass (see tension below). No assignee; linked PR #174 is closed (earlier work it follows up); zero comments, so no claim comment.
- Contribution policy allows this work: pass. CONTRIBUTING.md has no AI restriction; repo ships AGENTS.md (AI-friendly signal).
- Helpful guidance (preferred): pass. Repro commands, file/test names, acceptance checklist.
- Verdict: accept.
- Fit: Python, backend/developer tool (SQL lint CLI), debugging and writing tests (`tests/test_lint.py`), clearly scoped with expected behavior, welcoming `good first issue` repo.
- TENSION: the issue body says "@dianatofficial wrote #174 and has first claim on this if they want it. If they don't claim it within a couple of days, anyone can." That is a reservation by the maintainer, not a claim by a contributor, so the rubric's check passes literally. Read the thread again before claiming; do not claim before the "couple of days" pass (issue created 2026-11-16T17:50Z).

### 2. Share Pip: Web Share API button with copy-link fallback
https://github.com/Tech4Aditya/pipOS/issues/117
- Found by: Query 4 (javascript). Ranking: rank 5; `good first issue` tier; updated 2026-11-16T17:47Z; 0 comments; no assignee.
- Maintainer activity: pass. Default-branch commits and merges on 2026-11-16 (Aditya8369, owner Tech4Aditya opened the issue).
- Repository in use: pass. Pushed 2026-11-16, not archived (0 stars, created 2026-10-19).
- Newcomer-sized scope: pass. One button using `navigator.share` with a clipboard fallback.
- Issue has enough direction: pass. Names API, fallback, `PIP.toast`, and a "Done when".
- Not already being worked on: pass. No assignee, 0 comments, no PR referencing it.
- Contribution policy allows this work: pass. CONTRIBUTING.md welcomes first-timers; no AI restriction.
- Helpful guidance (preferred): pass. API and toast helper named, done-when criteria.
- Verdict: accept.
- Fit: JavaScript application feature, small and bounded. Weaker fit than #1 (frontend, not Python/backend).

### 3. Haptic feedback on toys (opt-in)
https://github.com/Tech4Aditya/pipOS/issues/119
- Found by: Query 4. Ranking: rank 4; `good first issue` tier; updated 2026-11-16T17:48Z; 0 comments; no assignee.
- Maintainer activity: pass. Same repo evidence as #117.
- Repository in use: pass. Same.
- Newcomer-sized scope: pass. One opt-in feature using `navigator.vibrate`; touches several toys but one capability.
- Issue has enough direction: pass. Names API, three trigger points, opt-in and Quiet-mode/reduced-motion constraints.
- Not already being worked on: pass. No assignee, 0 comments, no PR referencing it.
- Contribution policy allows this work: pass. Same.
- Helpful guidance (preferred): pass. Expected behavior stated.
- Verdict: accept.
- Fit: JavaScript feature work; weaker fit than #1 and #117 (touches several modules, no tests mentioned).

### 4. Docs: 'First PR in 10 minutes' and architecture guide
https://github.com/Tech4Aditya/pipOS/issues/122
- Found by: Query 4. Ranking: rank 2; `good first issue` tier; updated 2026-11-16T17:48Z; 0 comments; no assignee.
- Maintainer activity: pass. Same repo evidence.
- Repository in use: pass. Same.
- Newcomer-sized scope: pass. Two documentation files plus README links.
- Issue has enough direction: pass. Names `docs/FIRST_PR.md` and `docs/ARCHITECTURE.md` and what each covers.
- Not already being worked on: pass. No assignee, 0 comments, no PR referencing it.
- Contribution policy allows this work: pass. Same.
- Helpful guidance (preferred): pass. File names, contents, done-when ("newcomer can follow without asking").
- Verdict: accept.
- Fit: documentation is on your list, but it is not Python/backend/testing and the architecture guide needs unfamiliar frontend code reading. Lowest fit of the accepted four.

## Rejected

### Event listener and memory audit
https://github.com/Tech4Aditya/pipOS/issues/120
- Found by: Query 4. Ranking: rank 3; `good first issue` tier; updated 2026-11-16T17:48Z; 0 comments; no assignee.
- Maintainer activity: pass. Repository in use: pass. Not already being worked on: pass (no assignee, no comments, no PR). Contribution policy allows this work: pass. Issue has enough direction: pass (review `js/`, measure before and after).
- Newcomer-sized scope: UNCLEAR. "Review `js/` for listeners, timers and requestAnimationFrame loops ... fixes any leaks found": an audit of the whole `js/` directory whose number of fixes is unknown until the audit is done, so one focused change cannot be confirmed.
- Helpful guidance (preferred): pass (names `js/`, measurement requirement).
- Verdict: reject (required check unclear is treated as fail).

## Final JSON

```json
[
  {
    "item": "https://github.com/laaielichter/Gulliver/issues/191",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commits and maintainer merges on 2026-11-16 (e.g. merge of PR #174 at 17:47Z)."},
      {"name": "Repository in use", "grade": "pass", "evidence": "Last 5 commits all 2026-11-16; latest release 2026-11-12; not archived."},
      {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "One rule (GV005 fix advice in lint.py): three listed cases plus exact-text tests; no refactor or migration."},
      {"name": "Issue has enough direction", "grade": "pass", "evidence": "Exact repro commands, current vs expected text, files named, Done-when checklist."},
      {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments, linked PR #174 closed; body says @dianatofficial has first claim if they want it (reservation, not a claim)."},
      {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI restriction; repo ships AGENTS.md."},
      {"name": "Helpful guidance", "grade": "pass", "evidence": "Repro commands, file and test names, acceptance checklist."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/Tech4Aditya/pipOS/issues/117",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commits and merges on 2026-11-16; owner opened the issue."},
      {"name": "Repository in use", "grade": "pass", "evidence": "Pushed 2026-11-16T17:36Z; not archived."},
      {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "One Share button via navigator.share with copy-link fallback."},
      {"name": "Issue has enough direction", "grade": "pass", "evidence": "Names the API, the fallback, PIP.toast, and a Done-when."},
      {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments, no PR referencing it."},
      {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "CONTRIBUTING.md welcomes first-timers; no AI restriction."},
      {"name": "Helpful guidance", "grade": "pass", "evidence": "API, toast helper and done-when criteria given."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/Tech4Aditya/pipOS/issues/119",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commits and merges on 2026-11-16; owner opened the issue."},
      {"name": "Repository in use", "grade": "pass", "evidence": "Pushed 2026-11-16T17:36Z; not archived."},
      {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "One opt-in feature using navigator.vibrate."},
      {"name": "Issue has enough direction", "grade": "pass", "evidence": "Names the API, trigger points, opt-in, Quiet mode and reduced-motion constraints."},
      {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments, no PR referencing it."},
      {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "CONTRIBUTING.md welcomes first-timers; no AI restriction."},
      {"name": "Helpful guidance", "grade": "pass", "evidence": "Expected behavior stated in Done-when."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/Tech4Aditya/pipOS/issues/122",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commits and merges on 2026-11-16; owner opened the issue."},
      {"name": "Repository in use", "grade": "pass", "evidence": "Pushed 2026-11-16T17:36Z; not archived."},
      {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "Two documentation files plus README links."},
      {"name": "Issue has enough direction", "grade": "pass", "evidence": "Names docs/FIRST_PR.md and docs/ARCHITECTURE.md and their contents."},
      {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments, no PR referencing it."},
      {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "CONTRIBUTING.md welcomes first-timers; no AI restriction."},
      {"name": "Helpful guidance", "grade": "pass", "evidence": "File names, contents and done-when criterion given."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/Tech4Aditya/pipOS/issues/120",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Default-branch commits and merges on 2026-11-16; owner opened the issue."},
      {"name": "Repository in use", "grade": "pass", "evidence": "Pushed 2026-11-16T17:36Z; not archived."},
      {"name": "Newcomer-sized scope", "grade": "unclear", "evidence": "Audit of all of js/ with an unknown number of fixes; one focused change cannot be confirmed."},
      {"name": "Issue has enough direction", "grade": "pass", "evidence": "Review js/ for listeners, timers and rAF loops; Done-when asks for fixes and before/after measurements."},
      {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments, no PR referencing it."},
      {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "CONTRIBUTING.md welcomes first-timers; no AI restriction."},
      {"name": "Helpful guidance", "grade": "pass", "evidence": "Names js/ and the measurement requirement."}
    ],
    "verdict": "reject"
  }
]
```
