# Procedure: how this skill grades a plan package

## Read order

1. In eval mode, read the package in this order:
   1. Issue section.
   2. Thread highlights.
   3. Repo facts.
   4. Repro evidence.
   5. Candidate plan.
   6. Candidate plan comment.
2. In live mode, read `scope.md` first and refuse to grade if its repo scope is still an unfilled placeholder or the issue is outside the scoped source.
3. In live mode, read `voice-guide.md` before grading the candidate plan comment.
4. In live mode, gather the issue, thread, and posted reproduction evidence from the locations identified in `references/evidence-guide.md`.
5. Read the reproduction evidence before judging the candidate plan. Record the reported trigger, observed behavior, expected behavior, and any control or comparison result that the plan's diagnosis or test plan needs to explain.
6. Read the candidate plan only after the issue and reproduction evidence are understood. Record its stated diagnosis, scope, approach, test plan, risks, unknowns, and any deviation note.
7. Read the candidate plan comment last so it can be checked against both the plan and the evidence already gathered.

## Evidence gathering

### Diagnosis and grounding

1. Record the cause stated by the candidate plan.
2. From the Issue and Repro evidence, record the observed behavior the cause must explain.
3. If the plan relies on a maintainer or contributor finding, record that finding from the Thread highlights or live thread.
4. Compare the stated cause with those facts.
5. Record one deciding fact showing whether the cause is supported, contradicted, or left speculative.

### Scope

1. Record every file, area, behavior, or change the plan places in scope.
2. Record the plan's explicit not-in-scope items.
3. Compare the proposed change with the stated diagnosis and reproduced behavior.
4. Record whether the proposed work is limited to addressing the diagnosed problem or expands into unrelated behavior or cleanup.

### Executability

1. Record the files or areas where the plan says work will begin.
2. Record the concrete approach or change steps.
3. Ask whether a developer who did not write the plan could begin the implementation without needing an essential decision from the author.
4. Record the missing decision if the answer is no; otherwise record the first concrete implementation action the plan enables.

### Test plan

1. Record the reproduction step or equivalent real-path behavior the plan intends to test.
2. Record the expected result the plan uses as the success condition.
3. Record any control, regression check, or additional case the plan proposes.
4. Compare the test's observable result with the reproduced issue behavior.
5. Record the specific observable outcome that would distinguish success from failure.

### Honesty

1. Review the plan's diagnosis, approach, risks, unknowns, and any deviation note.
2. Mark statements that are confirmed by the issue, reproduction evidence, or thread as confirmed.
3. Mark explanations or implementation details that are not established by the evidence as hypotheses or unknowns.
4. Check whether the plan labels those uncertainties honestly rather than presenting them as facts.
5. Record any unsupported claim about cause, outcome, compatibility, scope, or certainty.

### Comms

1. Record the main claim made by the candidate plan comment.
2. Compare that claim with the candidate plan and the reproduction evidence.
3. Check the Thread highlights or live thread for maintainer requests, constraints, or relevant discussion.
4. Check Repo facts for contribution requirements, templates, and AI-use requirements.
5. Record any mismatch between the comment and the plan, thread, evidence, or repository requirements.

## Check execution

1. Grade the six rubric checks in this order:
   1. Diagnosis & Grounding
   2. Bounded Scope
   3. Executability
   4. Observable Test
   5. Honesty & Unknowns
   6. Thread & Repo Communication
2. For each check, use only the evidence gathered for that check and apply the rubric's pass condition literally.
3. Assign `pass` when the pass condition is satisfied by the gathered evidence.
4. Assign `fail` when the evidence contradicts the pass condition or shows that the required outcome is not met.
5. Assign `unclear` when the required evidence is genuinely absent or does not establish whether the pass condition is met. Do not fill an evidence gap with assumptions.
6. Record one concise evidence line for every check. The line must state the fact that decided the grade rather than simply repeating the check name.
7. Do not re-grade a check based on the plan's formatting, length, headings, or writing style unless that affects the actual outcome described by the check.
8. If a procedure step above does not provide enough information to execute a check, record the missing procedure step as a procedure gap rather than inventing a grading rule.

### Comment status and voice validation

Before grading Thread & Repo Communication:

1. Determine whether implementation is planned, in progress, or already completed using the plan and available verification evidence.
2. Check that the comment accurately represents that status. A comment describing completed work must not present the work as merely proposed.
3. If implementation is already complete, require the comment to identify itself as retrospective and to report only results supported by the plan or verification evidence.
4. Read voice-guide.md and check the comment against its applicable rules. If the guide contains only an unfilled template, record that limitation instead of inventing voice requirements.
5. If the comment’s status or claims conflict with the plan or evidence, grade Thread & Repo Communication as fail and cite the conflicting statements.
6. If the build has already happened, evaluate the documented implementation and results as retrospective evidence. Do not reject the package solely because the plan was written or finalized after implementation.

## Verdict assembly

1. Apply the verdict rule in `rubric.md` to all six check grades.
2. Because all six checks are required, return `accept` only when all six grades are `pass`.
3. Return `reject` if any check is `fail` or `unclear`.
4. Before the final JSON, give a short summary with one line per check and any applicable live-mode voice-guide notes.
5. The final output must contain one fenced JSON block with:
   - `item`: the issue URL in live mode or bundle id in eval mode.
   - `checks`: every rubric check with its name, grade, and one-line deciding evidence.
   - `verdict`: `accept` or `reject`.
6. The JSON block must be the final content in the output, with nothing after it.
