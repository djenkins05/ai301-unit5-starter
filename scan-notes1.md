# Scan 2 notes: what the scout produced and what it taught me

Companion to `scan-output1.md` (run 2026-11-16T18:04Z). This is a retrospective: Issue #29 was claimed on 2026-11-12 and PR #362 opened on 2026-11-13, before this scan.

## What the scout produced
- 500 results from five queries, 500 unique, 417 after the ranking filters, top five graded.
- Top five: 2 accepted (memtomem-stm #1394, infinispan #18514), 3 rejected (openspective #11 on maintainer activity and repo in use, Starry-Palace #325 on scope, globalstack #135 on unclear scope and direction).
- Rafter CLI #29 never appeared in the 500 results. Graded directly, it is a REJECT under the rubric as written (scope fail from the evidence guide's umbrella clause; also fails "not already being worked on" today because of my own PR).
- The best result of the scan, memtomem-stm #1394, is close to what I did by hand: a Python, tests-only, tightly scoped `good first issue`.

## Difficulties
1. **#29 was outdated and nothing in the tool can see that.** Four of the five files it lists as missing already existed (added 2026-04-05 and 2026-05-07, after the issue was opened on 2026-03-25). No rubric check asks whether the issue's premise is still true. "Issue has enough direction" passed because the one valid row (`test_api_utils.py`) was concrete.
2. **Scenario overlap was invisible too.** Most of the Node `api-utils` scenarios already had Python coverage in `test_error_handling_gauntlet.py`, `test_config_secret_handling.py` and `test_api_scope.py`. Finding that took reading three test files by hand. One of my four PR tests (quiet single-line JSON) largely overlaps an existing test.
3. **Umbrella issues.** #29 is a list of independent slices. The rubric says "one focused bug fix or feature"; only the evidence guide mentions umbrella issues, and nothing says how to grade claiming one slice. I graded NS as fail per the guide, which is debatable.
4. **Own claim and PR.** The "not already being worked on" check cannot tell my own claim from a stranger's. Literal grade today: fail. Grade before I claimed: pass. For a retrospective, I had to report both.
5. **Target repo vs host repo.** openspective #11 asks for a PR to a different repo (discourse-perspective-api, last commit about 203 days ago). The rubric does not say which repo the maintainer and repo-in-use checks apply to. I used the repo where the work lands.
6. **Unstable search results.** GitHub's best-match top 100 changed in 15 minutes: scan 1 had 6 `good first issue` results in the ranked set, scan 2 had 1. The scan is a snapshot, not a reproducible query.

## False positives and noise in the scan
- 415 of 417 ranked results had no beginner label, so ranks 3 to 417 are ordered only by "newest update".
- Ranks 3 to 5 were issues opened within minutes of the scan, which is why they have 0 comments and no claims: "not already being worked on" passed because nobody had time to react.
- Non-contribution issues in the top 10: a deploy checklist (Starry-Palace #325), an investigation tied to a private workspace (globalstack #135), and a production alert (FuzeInfra #4821, rank 9).
- infinispan #18514 was accepted by the rubric but is unlabeled and untriaged, in a large codebase. Accept is not the same as a good first issue.

## Improvements to make
1. **Add a "premise still true" check** (required or preferred): compare the issue's claim against current main. For test-file issues: do the named files exist now? Cheap evidence: `gh api repos/OWNER/REPO/contents/PATH`.
2. **Add an "already covered elsewhere" step** for test and docs issues: grep the existing tests for the scenarios before accepting.
3. **Add an umbrella clause to the rubric itself** (not only the evidence guide): grade a claimed slice of an umbrella issue on the slice, but only if the issue says slices are independent. Decide this deliberately; do not leave it to the grader.
4. **Say how to treat the user's own claim or PR** in "not already being worked on" (ignore authors matching the user's GitHub login).
5. **Say which repo the activity checks use** when the issue points elsewhere.
6. **Add label-filtered queries** (`good first issue`, `help wanted`, `beginner`, `good-first-issue`, `testing`) for each language, so beginner-labeled issues are not a 0.2% slice of the pool. Add a `testing` label to the Python queries, since #29 carried `help wanted` and `testing`.
7. **Cap results per repository** (e.g. 2) so one repo cannot fill the top five.
8. **Require a minimum issue age** (e.g. 3 days) so claim-signal checks have time to mean something, and a minimum repo age.
9. **Record the scan date and save the raw JSON** next to the report so a scan can be replayed.

## Lessons learned
- A tool built to read only search fields plus issue evidence can pick a stale issue; the check that would have caught #29 (are the "missing" files still missing?) is outside the rubric.
- I did the substitute work by hand: before opening PR #362 I read the Node tests and found the existing Python coverage, which is why the PR's file header lists where the other scenarios live. The scout should do that step.
- Retrospective grading is useful: it exposed three ambiguities (umbrella, own claim, target repo) that a normal scan would have hidden behind a verdict.
- The rubric should not be bent to approve my own issue. It rejected #29 on scope, and that reflects a real gap in how the rubric treats umbrella issues rather than a bad contribution.

## Suggested Unit 5 Toolkit entry
> I ran my Issue-Scout scan (5 queries, 500 results, 417 ranked, top 5 graded: 2 accepted, 3 rejected) and then graded my already-claimed issue, Rafter CLI #29, retrospectively. Under my rubric as written #29 is a REJECT: it is an umbrella issue (the evidence guide fails these), and today it also fails "not already being worked on" because of my own PR #362. The scan taught me that my rubric cannot see two things I had to check by hand: the issue was outdated (4 of the 5 "missing" Python test files already existed) and most scenarios in the missing file were already covered in three other test files. Next patches: a "premise still true" check, an "already covered elsewhere" step, an explicit umbrella rule, and label-filtered queries.
