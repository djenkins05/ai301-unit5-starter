# Scan 1 notes (2026-11-16)

Problems and friction found with the search strategy and rubric. Nothing was changed; these are candidates for patches.

## Search strategy
1. **No label filter means 415 of 425 ranked results have no beginner label.** Only 6 results were `good first issue`, 4 `help wanted`, 0 `beginner`. The top 5 were all `good first issue`, the 6th-ranked candidate is also `good first issue` (memtomem/memtomem-stm #1394, not graded), but ranks 7-10 are `help wanted` and everything after that is unlabeled, so a larger scan would quickly fall to weak candidates. Consider adding `--label` variants (separate queries for `good first issue`, `help wanted`, `beginner`, `good-first-issue`) now that dedupe and ranking exist.
2. **Zero `beginner` labels.** That tier of rule 3 never fired. Common alternatives (`good-first-issue`, `first-timers-only`, `easy`, `starter`) are not matched. Label matching is exact-name only.
3. **Top 5 is dominated by one repo.** 4 of 5 are Tech4Aditya/pipOS issues created in the same minute by a script (`create_issues.sh` is in the repo), all sharing the same repo evidence. No ranking rule limits results per repo. Consider "at most 2 per repository".
4. **Ranking by newest `updatedAt` favors brand-new issues.** All top 5 were updated within minutes of the scan and have 0 comments. That is partly why claim signals are empty: nobody has had time to claim anything. It also means maintainer intent can still change (see item 6).
5. **Irrelevant results.** Unlabeled results include non-software items (e.g. a Korean competition submission in `gisup89/competition`), AI-agent task tickets (e.g. `beetroot-salad/cyber-response-agent`), and other noise. The `"test"` and `"api"` queries match text, not intent. Rule 1 (drop assigned) removed 75 of 500.
6. **Queries never overlapped** (500 unique of 500), so query 2 and 5 contributed nothing to the top 5. Their text-only matching sorts by best match, not by label.
7. **Rule 2 (stale >120 days) removed nothing**, because `gh search issues` default order is by best match and these results are all recent. The filter is cheap but untested.
8. **`gh search issues --language` filters on repo language, not on issue relevance.** React/Java queries returned no top-5 results.

## Rubric
1. **"Not already being worked on" vs a maintainer reservation.** Gulliver #191 says "@dianatofficial ... has first claim on this if they want it. If they don't claim it within a couple of days, anyone can." The check's text only fails on assignee, open linked PR, or a contributor's own claim/WIP statement, so it passes. A human would likely wait. Consider adding a clause to the check for explicit maintainer reservations or "first claim" statements.
2. **"Newcomer-sized scope" has no case for audits/investigations.** Issue #120 ("review js/ ... fix any leaks found") is neither one bug fix nor an explicit refactor. I graded it `unclear` (so reject) because the number of fixes is unknown. A rubric sentence on open-ended audits would make that grade deterministic.
3. **"Maintainer activity" on a one-person repo.** pipOS owner and committer appear to be different accounts (Tech4Aditya opens issues, Aditya8369 commits), and the repo has 0 stars and was created 2026-10-19. The check passes on commit dates alone; it says nothing about review responsiveness for outside PRs.
4. **Repo age is not checked.** Both repos are weeks old (Gulliver created 2026-11-01, pipOS 2026-10-19). Recency checks pass trivially.
5. **Issues created minutes before the scan.** None have had comment time; the "no claim" evidence is weak. Consider a minimum issue age.
6. **Ambiguous evidence for "linked PRs".** `gh pr list --search <number>` matched an unrelated PR (#22 for pipOS #120) by text. Only the issue timeline's cross-references are reliable; the evidence guide does not say which `gh` call to use.

## Process
- First attempt at evidence gathering failed on a shell quoting error in my loop and was rerun; no rate-limit or auth problems.
- The `gh` search for linked PRs via `search/issues` hit an HTTP/2 stream error once; the timeline API worked.
- No GitHub issue was claimed, commented on, or modified. No skill files other than these two new files were created.
