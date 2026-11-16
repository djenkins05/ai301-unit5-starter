# Search strategy: where your scout looks, and why

## Queries

The following queries target programming languages and project areas from my fit profile. Each query searches public GitHub issues and requests a generous number of results so ranking can narrow the candidates afterward.

### Query 1: Python newcomer issues

My fit profile states that "My strongest preferences are Python projects." This query searches all open Python issues without a label filter, so that issues using different beginner-friendly labels (`good first issue`, `beginner`, `help wanted`) are all discovered. The ranking filters, not the query, prefer those labels.

```bash
gh search issues --language python --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url
```

### Query 2: Python testing and debugging

My fit profile states "I am comfortable investigating bugs, writing or improving tests, fixing smaller application issues" and that I want more experience with "testing, and debugging."

```bash
gh search issues "test" --language python --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url
```

### Query 3: Java newcomer issues

My fit profile states "Java projects are also a good fit," and lists Java as a primary language. This query searches all open Java issues without a label filter so that varied newcomer labels are discovered.

```bash
gh search issues --language java --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url
```

### Query 4: JavaScript and React newcomer issues

My fit profile states "followed by JavaScript or React application issues" and that I have experience using JavaScript and React for web development. This query searches all open JavaScript issues without a label filter so that varied newcomer labels are discovered.

```bash
gh search issues --language javascript --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url
```

### Query 5: Python API/backend issues

My fit profile states "I am particularly interested in projects involving backend services, REST APIs, automation, application development, and developer tools." This query searches open Python issues mentioning "api" without a label filter so that varied newcomer labels are discovered.

```bash
gh search issues "api" --language python --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url
```

## Ranking filters

Combine the results from all five queries before ranking. Deduplicate issues by their URL before applying any filter, so that each issue appears only once.

Apply the following rules in order, using only the JSON fields already returned by the searches.

1. **Remove assigned issues.**
   Drop any issue with one or more entries in its `assignees` field. These issues are less likely to be available for an outside contributor.

2. **Remove stale issues.**
   Drop issues whose `updatedAt` date is more than 120 days before the scan date. This keeps the candidate list focused on issues with relatively recent activity.

3. **Prefer newcomer-friendly labels.**
   Rank issues with the label `good first issue` first, issues with `beginner` next, issues with `help wanted` next, and all remaining issues last. Label matching is case-insensitive. For issues with multiple matching labels, use the highest-priority label.

4. **Prefer recently updated issues.**
   Within the same label category, sort by `updatedAt` from newest to oldest.

5. **Prefer fewer comments.**
   When issues have the same label priority and update timestamp, prefer the lower `commentsCount`. Fewer comments may make an issue easier for a newcomer to investigate.

6. **Use a deterministic final tie-break.**
   If issues are still tied, sort by `url` alphabetically in ascending order.

The ranking stage must not fetch issue pages, read comment threads, or judge the complexity of an issue. Those checks belong to the rubric-based grading stage.

The ranking stage only determines which issues to inspect first. An issue that ranks highly can still be rejected by the rubric.

## How many to grade

Grade the top **5** ranked results per scan.

I am keeping the default of five because each candidate costs approximately $0.20 to grade, making a full scan approximately $1.

Five candidates provide enough variety to compare possible contributions without unnecessarily increasing grading cost.

## Reporting results

For each graded candidate, report:

- The issue title and GitHub URL.
- The query or queries that found the issue.
- The ranking signals that placed it in the top five.
- The result of every required and preferred rubric check.
- The final accept or reject verdict.
- For accepted issues, a brief explanation of how the issue matches my fit profile.

List accepted issues first, ranked by fit, followed by rejected issues and the required checks responsible for rejection.

Use the JSON output format specified in `SKILL.md`.

Do not claim any issue automatically. Only post a claim comment after I explicitly decide to work on that issue.
