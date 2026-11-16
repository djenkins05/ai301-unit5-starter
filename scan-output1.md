# Issue-Scout scan 2 and retrospective grade of Issue #29

Scan run: 2026-11-16T18:04:52Z with the installed `issue-scout` skill (strategy, rubric and evidence guide unchanged). Rubric recency checks are measured against this date.

**Retrospective notice.** Issue #29 was claimed (2026-11-12) and PR #362 was opened (2026-11-13) before this scout ran. This is a retrospective grade, not evidence the scout selected the issue. The rubric was not adjusted to make #29 pass.

The rubric has no numeric score. A candidate is accepted only if every required check passes (an `unclear` required check counts as a fail). Preferred checks only rank accepted issues.

## Part 1: Raw search results

All five queries from `search-strategy.md`, run unmodified with `--state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url`.

| Query | Command shape | Returned |
|---|---|---|
| Q1 | `--language python` | 100 |
| Q2 | `"test" --language python` | 100 |
| Q3 | `--language java` | 100 |
| Q4 | `--language javascript` | 100 |
| Q5 | `"api" --language python` | 100 |

| Stage | Count |
|---|---|
| Total retrieved | 500 |
| Unique after URL dedupe | 500 |
| Dropped: has assignee | 83 |
| Dropped: not updated in 120 days | 0 |
| Ranked | 417 |
| Tier counts of ranked set | good first issue: 1, beginner: 0, help wanted: 1, none: 415 |

Not in the scan results: Raftersecurity/rafter-cli #29. It has `help wanted` and `testing` labels, no assignee, and its last update was 2026-11-12, so it was eligible for ranking. It did not appear in any query's top 100 (best-match order), so the scout never saw it.

The previous scan (same day, about 15 minutes earlier, `scan-output.md`) had 6 `good first issue` results in the ranked set. This scan had 1. The top-100 results for the same queries changed in that time.

## Part 2: Ranking (top 15 of 417)

| Rank | Tier | Updated (UTC) | Comments | Query | Issue |
|---|---|---|---|---|---|
| 1 | good first issue | 2026-11-14T01:36:34Z | 0 | Q2 | [memtomem/memtomem-stm](https://github.com/memtomem/memtomem-stm/issues/1394): test: direct tests for SurfacingFormatter._format_source |
| 2 | help wanted | 2026-11-16T04:48:54Z | 0 | Q5 | [aryan-tah/openspective](https://github.com/aryan-tah/openspective/issues/11): Upstream: make the API URL configurable in discourse-perspective-api |
| 3 | (none) | 2026-11-16T18:04:40Z | 0 | Q3 | [infinispan/infinispan](https://github.com/infinispan/infinispan/issues/18514): RESP: CONFIG GET returns the wrong reply shape for databases and unkno |
| 4 | (none) | 2026-11-16T18:04:39Z | 0 | Q4 | [annalisegeorge1/The-Starry-Palace](https://github.com/annalisegeorge1/The-Starry-Palace/issues/325): Deploy merged AI crawler and creator visibility policy update (#324) |
| 5 | (none) | 2026-11-16T18:04:37Z | 0 | Q4 | [divine-ai-com/globalstack](https://github.com/divine-ai-com/globalstack/issues/135): Investigate native Durable retry scheduling timestamps |
| 6 | (none) | 2026-11-16T18:04:35Z | 0 | Q3 | [yegor256/takes](https://github.com/yegor256/takes/issues/1851): BkBasic parses an unread request body as a new request |
| 7 | (none) | 2026-11-16T18:04:34Z | 0 | Q1 | [PyAutoLabs/autolens_inference](https://github.com/PyAutoLabs/autolens_inference/issues/69): fix: phase-4 wall estimates miss eval count, sampler floor and startup |
| 8 | (none) | 2026-11-16T18:04:30Z | 0 | Q1 | [suleymanozkeskin/horsies](https://github.com/suleymanozkeskin/horsies/issues/948): horsies-core: call the worker connection check from the live check and |
| 9 | (none) | 2026-11-16T18:04:29Z | 0 | Q1 | [FuzeOne/FuzeInfra](https://github.com/FuzeOne/FuzeInfra/issues/4821): 🔴 Prod alert: VolumeMountFailing [fuzeinfra] |
| 10 | (none) | 2026-11-16T18:04:29Z | 0 | Q1 | [fprime-community/fpy](https://github.com/fprime-community/fpy/issues/288): Add file path to AST meta information |
| 11 | (none) | 2026-11-16T18:04:28Z | 0 | Q1 | [Robin-IA/Congressional-Letters-Dev](https://github.com/Robin-IA/Congressional-Letters-Dev/issues/549): Reading batch 17: six letters not filed for want of a date |
| 12 | (none) | 2026-11-16T18:04:27Z | 0 | Q1 | [Robin-IA/Congressional-Letters-Dev](https://github.com/Robin-IA/Congressional-Letters-Dev/issues/548): Reading batch 17: scan with letterhead-only OCR text (Rep. Sewell) |
| 13 | (none) | 2026-11-16T18:04:24Z | 0 | Q4 | [finnonemo/neon](https://github.com/finnonemo/neon/issues/345): Release guardrails from the 1.0.2 retrospective |
| 14 | (none) | 2026-11-16T18:04:22Z | 0 | Q4 | [klondikemarlen/omp-verifier](https://github.com/klondikemarlen/omp-verifier/issues/263): Bug: Bounded Lockfile Recovery Still Hits the Whole-Source Size Limit |
| 15 | (none) | 2026-11-16T18:04:21Z | 0 | Q1 | [Luffytse/luffy-agentic-workflow](https://github.com/Luffytse/luffy-agentic-workflow/issues/254): Retro: implement-spec asks the owner to hand-copy a workflow file befo |

Ranking order: label tier, then newest `updatedAt`, then fewer comments, then URL.

## Part 3: Rubric evaluation of the top five

Required checks: Maintainer activity (MA), Repository in use (RU), Newcomer-sized scope (NS), Issue has enough direction (ED), Not already being worked on (NW), Contribution policy allows this work (CP). Preferred: Helpful guidance (HG).

| Rank | Issue | MA | RU | NS | ED | NW | CP | HG | Verdict |
|---|---|---|---|---|---|---|---|---|---|
| 1 | memtomem-stm #1394 | pass | pass | pass | pass | pass | pass | pass | **ACCEPT** |
| 2 | openspective #11 | fail | fail | pass | pass | pass | pass | pass | REJECT |
| 3 | infinispan #18514 | pass | pass | pass | pass | pass | pass | pass | **ACCEPT** |
| 4 | Starry-Palace #325 | pass | pass | fail | pass | pass | pass | fail | REJECT |
| 5 | globalstack #135 | pass | pass | unclear | unclear | pass | pass | pass | REJECT |

### 1. memtomem/memtomem-stm #1394: test: direct tests for SurfacingFormatter._format_source
https://github.com/memtomem/memtomem-stm/issues/1394 (found by Q2; rank 1, `good first issue`, updated 2026-11-14, 0 comments, no assignee)
- MA pass: last 5 default-branch commits all 2026-11-15 by maintainer `memtomem`.
- RU pass: pushed 2026-11-15; not archived.
- NS pass: "Tests only. Don't change formatter.py", "1 file, additive".
- ED pass: table of 8 calls with expected results, file and test location named, run command.
- NW pass: no assignee, 0 comments, no cross-referenced PR in the issue timeline. CONTRIBUTING.md says a comment is the claim.
- CP pass: CONTRIBUTING.md has no AI restriction; repo has CLAUDE.md.
- HG pass.
- Verdict: ACCEPT. Fit: Python, tests-only, tightly scoped.

### 2. aryan-tah/openspective #11: Upstream: make the API URL configurable in discourse-perspective-api
https://github.com/aryan-tah/openspective/issues/11 (found by Q5; rank 2, `help wanted`, updated 2026-11-16, 0 comments, no assignee)
- MA fail: the work is a PR to `discourse/discourse-perspective-api` (Ruby). Its last 3 default-branch commits are 2026-03-26, 2026-03-30 and 2026-04-27 (about 203 days ago), and its last 3 PRs are 2026-03-30 to 2026-04-26. No maintainer activity within 90 days was found.
- RU fail: 0 of the last 3 commits sampled are within 180 days (only 3 commits were retrieved, so "last 5" is not fully verified).
- NS pass: one site setting plus a guide update. ED pass: names the constant and file. NW pass: no assignee, 0 comments. CP pass: no restriction found. HG pass.
- Verdict: REJECT (MA and RU). The issue's host repo (openspective, created 2026-11-16) would pass both checks; the rubric does not say which repo applies when the work lands elsewhere.

### 3. infinispan/infinispan #18514: RESP: CONFIG GET returns the wrong reply shape
https://github.com/infinispan/infinispan/issues/18514 (found by Q3; rank 3, no label, updated 2026-11-16T18:04Z, 0 comments, no assignee)
- MA pass: maintainer `tristantarrant` committed 2026-11-16. RU pass: pushed 2026-11-16, 1,361 stars.
- NS pass: two wrong reply cases in `CONFIG.java`. ED pass: expected/actual output and `redis-cli` repro.
- NW pass: no assignee, 0 comments, no linked PR (issue opened minutes before the scan).
- CP pass: CONTRIBUTING.md "Use of Generative AI" allows AI assistance with conditions (understand the change, engage with review, be able to revise).
- HG pass.
- Verdict: ACCEPT. Fit: Java backend bug with a clear repro, but a large enterprise codebase and the issue has not been triaged.

### 4. annalisegeorge1/The-Starry-Palace #325: Deploy merged AI crawler and creator visibility policy update (#324)
https://github.com/annalisegeorge1/The-Starry-Palace/issues/325 (found by Q4; rank 4, no label, 0 comments, no assignee)
- MA pass, RU pass: owner committed 2026-11-16.
- NS fail: the work is a production deployment checklist (publish a Worker, verify traffic and rollback, reconfirm Cloudflare settings), not one bug fix or feature.
- ED pass: concrete checklist. NW pass. CP pass: no CONTRIBUTING file; nothing restricts contributors explicitly. HG fail: no reproduction, code location or expected behavior for an outside contributor.
- Verdict: REJECT (NS).

### 5. divine-ai-com/globalstack #135: Investigate native Durable retry scheduling timestamps
https://github.com/divine-ai-com/globalstack/issues/135 (found by Q4; rank 5, no label, 0 comments, no assignee)
- MA pass, RU pass: commits 2026-11-08 to 2026-11-16.
- NS unclear: an investigation that says it is "not yet a proven queue implementation defect"; the number and size of fixes is unknown.
- ED unclear: the evidence is held in a private "operator workspace", so an outside contributor cannot reproduce it.
- NW pass, CP pass, HG pass.
- Verdict: REJECT (unclear counts as fail).

### Scan JSON

```json
[
  {"item": "https://github.com/memtomem/memtomem-stm/issues/1394", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Last 5 commits 2026-11-15 by memtomem."},
    {"name": "Repository in use", "grade": "pass", "evidence": "Pushed 2026-11-15; not archived."},
    {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "Tests only, 1 file, additive."},
    {"name": "Issue has enough direction", "grade": "pass", "evidence": "Table of expected outputs, file and run command."},
    {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments, no linked PR."},
    {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI restriction."},
    {"name": "Helpful guidance", "grade": "pass", "evidence": "Acceptance criteria and file locations given."}], "verdict": "accept"},
  {"item": "https://github.com/infinispan/infinispan/issues/18514", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "tristantarrant committed 2026-11-16."},
    {"name": "Repository in use", "grade": "pass", "evidence": "Pushed 2026-11-16."},
    {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "Two wrong reply cases in CONFIG.java."},
    {"name": "Issue has enough direction", "grade": "pass", "evidence": "Expected/actual output and redis-cli repro."},
    {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments, no linked PR."},
    {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "Generative AI allowed with conditions."},
    {"name": "Helpful guidance", "grade": "pass", "evidence": "Repro steps and expected behavior."}], "verdict": "accept"},
  {"item": "https://github.com/aryan-tah/openspective/issues/11", "checks": [
    {"name": "Maintainer activity", "grade": "fail", "evidence": "Target repo discourse-perspective-api last commit 2026-04-27, no maintainer activity in 90 days."},
    {"name": "Repository in use", "grade": "fail", "evidence": "0 of 3 sampled commits within 180 days."},
    {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "One site setting plus a guide update."},
    {"name": "Issue has enough direction", "grade": "pass", "evidence": "Names the constant and file."},
    {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments."},
    {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "No restriction found."},
    {"name": "Helpful guidance", "grade": "pass", "evidence": "File and constant named."}], "verdict": "reject"},
  {"item": "https://github.com/annalisegeorge1/The-Starry-Palace/issues/325", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Owner committed 2026-11-16."},
    {"name": "Repository in use", "grade": "pass", "evidence": "Pushed 2026-11-16."},
    {"name": "Newcomer-sized scope", "grade": "fail", "evidence": "Production deployment checklist, not one bug fix or feature."},
    {"name": "Issue has enough direction", "grade": "pass", "evidence": "Concrete checklist of deploy steps."},
    {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments."},
    {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "No contribution policy found."},
    {"name": "Helpful guidance", "grade": "fail", "evidence": "No repro, code location or expected behavior for an outside contributor."}], "verdict": "reject"},
  {"item": "https://github.com/divine-ai-com/globalstack/issues/135", "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Commits 2026-11-08 to 2026-11-16."},
    {"name": "Repository in use", "grade": "pass", "evidence": "Pushed 2026-11-16."},
    {"name": "Newcomer-sized scope", "grade": "unclear", "evidence": "Investigation, not yet a proven defect; fix size unknown."},
    {"name": "Issue has enough direction", "grade": "unclear", "evidence": "Evidence is in a private operator workspace."},
    {"name": "Not already being worked on", "grade": "pass", "evidence": "No assignee, 0 comments."},
    {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "No restriction found."},
    {"name": "Helpful guidance", "grade": "pass", "evidence": "Timing table and upstream source links."}], "verdict": "reject"}
]
```

## Part 4: Retrospective grade of Raftersecurity/rafter-cli #29

https://github.com/Raftersecurity/rafter-cli/issues/29: "test: Python test parity — add missing test files". Opened 2026-03-25 by maintainer `Rome-1`; labels `help wanted`, `testing`; no assignee. Timeline: djenkins05 claim comment 2026-11-12T15:04Z, PR #362 cross-reference 2026-11-13T02:00Z (open, 1 file, +59 lines, no reviews, no CI status).

### Required and preferred checks

| Check | Grade | Evidence |
|---|---|---|
| Maintainer activity | pass | Rome-1 committed and merged PRs on 2026-11-16 (e.g. #371, #369); release v0.12.1 on 2026-11-16. |
| Repository in use | pass | Last 5 default-branch commits all 2026-11-16; v0.12.0 released 2026-11-16; not archived; 28 stars. |
| Newcomer-sized scope | **fail** (debatable) | Evidence guide, Family 3: scope fails when an issue is "explicitly an umbrella or tracking issue (a list of sub-items meant to be split into separate work)". #29 lists 5 files and says "Pick any one", "Each is independent". The slice you chose (one test file, ~1 hour per the issue) is bounded; the rubric has no wording for claiming one slice of an umbrella. |
| Issue has enough direction | pass (stale) | Names `tests/test_api_utils.py`, the Node reference `node/tests/api-utils.test.ts`, steps and "same scenarios, same assertions". That file did not exist on main (no commit history for `python/tests/test_api_utils.py` before PR #362). The other four listed files already existed. |
| Not already being worked on | pass at decision time; **fail** today | Before 2026-11-12T15:04Z: no assignee, no comments, no PR (pass). Today: open linked PR #362 and a claim comment, both by you. The rubric's first sentence says "no open linked pull request" with no author qualifier, so the literal grade today is fail. The claim and PR are yours, not another contributor's. |
| Contribution policy allows this work | pass | CONTRIBUTING.md "Use of AI": "We welcome AI-assisted contributions", asks for disclosure in the PR. PR #362 has an "AI Assistance" section. |
| Helpful guidance (preferred) | pass | File names, Node reference, run command. |

**Verdict under the rubric as written: REJECT.** The deciding check is Newcomer-sized scope (umbrella issue, per the evidence guide). Not already being worked on also fails when graded against today's state because of your own PR. If NS were graded `pass`, the only remaining blocker would be your own claim and PR, and the issue as it stood on 2026-11-12 would have been an ACCEPT.

No numeric score exists in this rubric.

### Suitability for your Python testing experience
Strong. The work was pytest tests only, using an existing Node test file as the specification, in a Python package with 104 test files and an established `tests/` layout. It touches no production code and matches your fit profile (Python, testing, API utilities). The effort estimate (~1 hour) was reasonable for a new file.

### Was the issue description outdated? Yes
| Listed as missing | Status on main (2026-11-16) | First added |
|---|---|---|
| tests/test_formatter.py | exists | 2026-04-05 (11 days after the issue was opened) |
| tests/test_git_utils.py | exists | 2026-04-05 |
| tests/test_binary_manager.py | exists | 2026-05-07 |
| tests/test_brief.py | exists | 2026-04-05 |
| tests/test_api_utils.py | did not exist until PR #362 | n/a |

The issue body was never edited after 2026-03-25 (last update on the issue is your comment). Only one of the five rows was still valid when you claimed it. Counts today: 104 Python `test_*.py` files, 126 Node `*.test.ts` files (naming differs, so this is not an exact parity gap).

### Were the missing file's scenarios already covered elsewhere? Mostly
Node `api-utils.test.ts` has 11 tests (API constants 2, resolveKey 4, writePayload 5). Python coverage before PR #362:
| Scenario | Existing Python coverage |
|---|---|
| resolveKey: CLI key, env var, precedence, no key | `test_error_handling_gauntlet.py` TestResolveKey; `test_config_secret_handling.py` TestResolveKeyPrecedence |
| writePayload: default JSON, markdown, markdown-missing fallback | `test_error_handling_gauntlet.py` TestWritePayload |
| writePayload: compact JSON when quiet | `test_error_handling_gauntlet.py` `test_compact_json_when_quiet` (asserts no newline only) |
| Exit code values | `test_error_handling_gauntlet.py` TestExitCodeConstants (5 codes); `test_api_scope.py` TestExitCodes (3-code collision check) |
| API base URL | not covered |
| Pretty-print when not quiet | not covered |
| All six exit codes distinct integers (incl. EXIT_CONFIRMATION_REQUIRED) | not covered |

PR #362's four tests: API_BASE (new), six distinct exit codes (new in part: adds EXIT_CONFIRMATION_REQUIRED), pretty-print (new), quiet single-line valid JSON (largely overlaps `test_compact_json_when_quiet`; adds a `json.loads` check). The PR's own file header lists the existing coverage, so the overlap was checked by you.

### Uncertainties and limitations
- The NS fail relies on the evidence guide's umbrella clause. It is the most debatable grade here.
- I did not run the PR's tests. I read the diff and the existing test files from GitHub.
- The gauntlet test named `test_falls_back_to_json_when_no_markdown` asserts empty output, which contradicts its name and the Node behavior. PR #362 documents this as a parity question.
- Candidate evidence for openspective #11 (target repo) used only 3 commits and 3 PRs.
- The scan results change between runs, so this ranking is a snapshot.
- PR #362 has had no review for 3 days; I did not check whether maintainers review outside PRs promptly (#358 by an outside contributor was merged on 2026-11-16).

### Issue #29 JSON

```json
{
  "item": "https://github.com/Raftersecurity/rafter-cli/issues/29",
  "checks": [
    {"name": "Maintainer activity", "grade": "pass", "evidence": "Rome-1 commits and merges on 2026-11-16; release v0.12.1."},
    {"name": "Repository in use", "grade": "pass", "evidence": "Last 5 commits all 2026-11-16; not archived."},
    {"name": "Newcomer-sized scope", "grade": "fail", "evidence": "Umbrella issue listing 5 independent files, per evidence guide Family 3; chosen slice (one file) is bounded."},
    {"name": "Issue has enough direction", "grade": "pass", "evidence": "Names tests/test_api_utils.py and its Node reference; 4 of 5 listed files already existed."},
    {"name": "Not already being worked on", "grade": "fail", "evidence": "Open linked PR #362 and claim comment, both by djenkins05 (pass before the 2026-11-12 claim)."},
    {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "CONTRIBUTING.md: AI-assisted contributions welcome, disclose in PR."},
    {"name": "Helpful guidance", "grade": "pass", "evidence": "File, Node reference and run command given."}
  ],
  "verdict": "reject"
}
```
