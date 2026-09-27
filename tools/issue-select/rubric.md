# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | Repo facts: last 5 default-branch commits and maintainer first-response sample; issue thread comments and author associations | Pass if at least 1 of the last 5 default-branch commits was authored by a human OR the maintainer first-response sample shows at least 1 owner/member/collaborator response within 90 days of the sampled issue activity | required |
| Repo activity | Repo facts: archived status, last push, latest release | Pass if the repo is not archived and either the last push or latest release is within the last 180 days | required |
| Newcomer scope | Issue body and comment thread | Pass if the issue describes a bounded contribution and is not explicitly an umbrella/tracking issue, not a pure usage/support request, and does not require core-internal changes according to a maintainer; multiple related files, documentation pages, possible causes, or implementation approaches can still be one bounded contribution unless the issue or thread shows an unresolved design debate | required |
| Issue availability | Repo facts: assignees and linked PRs; issue comment thread | Pass if there is no assignee, no open linked PR, no unmerged active PR claim, no recent comment claiming or actively working on the issue, and no years-old issue history with repeated abandoned claims or closed unmerged PR attempts indicating unresolved work | required |
| Contribution policy | Repo facts: contribution policy and dedicated AI policy files | Pass if there is no outright ban on AI-assisted contributions; if the repo has AI-use conditions such as disclosure, understanding, testing, or human review, treat those as requirements to follow rather than a failure | required |

## Verdict rule

Accept an issue if every required check passes. Reject an issue if any required check fails. Treat unclear as fail for required checks.
