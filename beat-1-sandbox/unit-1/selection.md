# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/65

**Verdict output**

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
issue-select: grade these candidate first issues: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/75 https://github.com/codepath/pathreview-ai301-fa26-howard/issues/70 https://github.com/codepath/pathreview-ai301-fa26-howard/issues/65

I'll start by loading the issue-select skill, since that's what you invoked.

⏺ Skill(issue-select)
Successfully loaded skill

I'll read the skill's scope and rubric files first.

  Ran 3 shell commands

gh isn't on PATH. Let me check for it elsewhere and try the API.

  Ran 2 shell commands

Repo is in scope. Now gathering repo-level facts and all three issues.

  Ran 3 shell commands

#70 has an extra timeline event — checking it, plus the contribution policy.

  Ran 3 shell commands

All three fetched. Quick grounding check on the files each issue touches, to inform ranking.

  Ran 1 shell command

Grading read-out

Mode: live. All three candidates are in codepath/pathreview-ai301-fa26-howard, the only scoped source — in-field. Path Review house rule applied: classmate claim comments would not block an issue (moot here — all three threads are empty).

Shared repo-level evidence (today = 2026-09-27):
- Last 5 main commits all authored by a human, Andrew Burke (Aburke225), most recent 2026-09-16 → Maintainer activity passes for all three.
- archived: false, pushed_at: 2026-09-16 (11 days ago, well inside 180) → Repo activity passes. No releases, but the rule is an OR.
- docs/CONTRIBUTING.md is the only policy file; no AI_POLICY.md, AGENTS.md, or AI mention anywhere. Silence passes. It does set conditions to follow: green CI on all five jobs, Conventional Commits, and delete the @pytest.mark.xfail marker when your fix makes a seeded test pass.
- The 3 open PRs (#76, #74, #73) close #72, #60, #68 — none of our candidates.

Your rubric has no preferred checks — all five are required — so nothing beyond fit orders the accepted set.

Accepted, in fit order

1. #65 — review_service async mocks (5/5 pass) — the squarest hit on your profile: Python, testing, and debugging at once, on a backend service. Confined to one file (tests/unit/test_review_service.py, 379 lines, 19 tests), and the body hands you both the diagnosis and the approach (AsyncMock for execute, MagicMock for the result) plus a one-line repro, pytest tests/unit/test_review_service.py -q. The issue states the service code is already correct, so no production internals to learn. tier-1.

2. #70 — indented README parser fixture (5/5 pass) — testing plus the ingestion/data path. The maintainer renamed it on 2026-09-16 from "parser returns no sections" to "test fixture is indented," which means the design question is already settled for you — that rename is also the only non-label event on the thread. Ranked below #65 only because it's tier-2 (2–4h) and reaches across 3 files. One thing to watch: sample_readme_text in tests/conftest.py is shared, so de-indenting it can move other tests that consume it.

3. #75 — README vs .env.example key mismatch (5/5 pass) — verified live: README.md:24 says OPENROUTER_API_KEY, .env.example:17-19 offers only mock/openai and OPENAI_API_KEY. The tightest scope and the only good first issue label, so it's the lowest-risk way to get one PR through the workflow. Last on fit because it's a docs/config edit — it gives you the least Python, testing, and debugging practice of the three.

No rejections. If you want one PR: take #65. If you'd rather de-risk the workflow first, land #75, then come back for #65.

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/65",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "All 5 latest main commits authored by human Aburke225, newest 2026-09-16T21:42:18Z"},
      {"name": "Repo activity", "grade": "pass", "evidence": "archived=false; pushed_at 2026-09-16, 11 days before today, within 180"},
      {"name": "Newcomer scope", "grade": "pass", "evidence": "Bounded to one test file's mock setup; 'The service code correctly awaits db.execute(...)' so no core-internal change, with repro 'pytest tests/unit/test_review_service.py -q'"},
      {"name": "Issue availability", "grade": "pass", "evidence": "assignees: []; timeline is 3 labeled events only; 0 comments; open PRs 76/74/73 close #72/#60/#68; opened 2026-09-14"},
      {"name": "Contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md contains no AI mention and no ban; no AI_POLICY.md or AGENTS.md exist"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/70",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "All 5 latest main commits authored by human Aburke225; maintainer also renamed this issue 2026-09-16T21:52:18Z"},
      {"name": "Repo activity", "grade": "pass", "evidence": "archived=false; pushed_at 2026-09-16, 11 days before today, within 180"},
      {"name": "Newcomer scope", "grade": "pass", "evidence": "Cause settled by maintainer rename to 'test fixture is indented'; 3 named files with explicit 'remove the marker as part of the fix' and no design debate in an empty thread"},
      {"name": "Issue availability", "grade": "pass", "evidence": "assignees: []; timeline is 3 labeled events plus 1 rename; 0 comments; no linked or mentioning PR"},
      {"name": "Contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md contains no AI mention and no ban; no AI_POLICY.md or AGENTS.md exist"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/75",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "All 5 latest main commits authored by human Aburke225, newest 2026-09-16T21:42:18Z"},
      {"name": "Repo activity", "grade": "pass", "evidence": "archived=false; pushed_at 2026-09-16, 11 days before today, within 180"},
      {"name": "Newcomer scope", "grade": "pass", "evidence": "Two named files and 'Make the two files agree', est. 1-2 hours, labeled 'good first issue'; confirmed live as README.md:24 vs .env.example:17-19"},
      {"name": "Issue availability", "grade": "pass", "evidence": "assignees: []; timeline is 4 labeled events only; 0 comments; opened 2026-09-16 with no linked PR"},
      {"name": "Contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md contains no AI mention and no ban; no AI_POLICY.md or AGENTS.md exist"}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

agreement 2/3

agreement 3/3

agreement 16/20 scored items (bar 18/20: FAIL)

agreement 19/20 scored items (bar 18/20: PASS)

agreement 18/20 scored items (bar 18/20: PASS)


The final 18/20 score matches the agreement line in the committed `eval-run.txt`.


**Issue analysis**

Issue-14: My rubric initially decided reject, while the gold label was accept. The rubric failed the issue on Maintainer Activity because my original check required either a recent maintainer first-response sample or another specific activity signal. After reviewing the evidence guide, I recognized that recent human commits alone can establish maintainer activity, so I revised that check. The updated rubric then correctly accepted issue-14.

**Check rationale**

Newcomer scope

`Pass if the issue describes a bounded contribution and is not explicitly an umbrella/tracking issue, not a pure usage/support request, and does not require core-internal changes according to a maintainer; multiple related files, documentation pages, possible causes, or implementation approaches can still be one bounded contribution unless the issue or thread shows an unresolved design debate`

I changed this check because the earlier wording was too restrictive. Issue-19 showed that an issue can describe multiple possible causes or implementation approaches while still being one bounded contribution. The current wording allows that distinction while still rejecting umbrella issues, support requests, core-internal work identified by a maintainer, and unresolved design debates.

**Trade-offs**

The current Newcomer scope check gives up rejecting an issue simply because it has multiple possible causes or implementation approaches. I accepted that trade-off because issue-19 showed that those possibilities do not necessarily make an issue too broad for a newcomer. The check still requires the contribution to be bounded and rejects unresolved design debates, umbrella/tracking issues, usage/support requests, and core-internal changes identified by a maintainer.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

The issue’s fit to my interests and to the time available:
I chose issue #65 because the live skill specifically matched it to my interests in Python, testing, debugging, and backend/AI-engineering work. It is also a manageable first contribution because the issue is focused on the test setup for review_service.

What the verdict identified correctly, and what I weighed that the rubric could not:
The skill correctly identified that #65 passed all five required checks and was a good fit for my stated interests. The rubric could determine whether the issue was acceptable, but my fit profile helped identify that #65 was more aligned with what I want to learn than the other accepted issues.

The anticipated difficulty in claiming it:
The live run showed that #65 had no assignee, comments, or linked PR activity, so I did not see an existing claim that would make claiming it difficult. I still understand that I need to claim the issue before beginning the contribution.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
