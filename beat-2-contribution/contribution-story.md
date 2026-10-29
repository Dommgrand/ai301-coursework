# Contribution: [Style]: The width should not change even when the toggle is switched.

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Dominique Fraser
**GitHub Username:** Dommgrand
**Issue:** https://github.com/oqtopus-team/qdash/issues/1218
**Pull Request:** Pending (not opened yet)

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 9: Building and Refining My Open-Source Issue Scout**

I built an `issue-scout` Claude skill using my technical interests to create GitHub search queries, ranking filters, and a five-check grading rubric for evaluating open-source issues. My initial scan returned 300 results, narrowed them to 250 candidates, and graded the top five, but further investigations showed that an issue could appear available even when an unlinked pull request had already resolved it. I improved the rubric to search related pull requests and inspect whether the reported problem was already fixed, then validated the change by regrading EMF Camp #1931 from accept to reject. I also graded three issues from the CodePath selection site and learned that passing all five checks does not necessarily reveal partially completed work, unclear implementation scope, or slow reviews for outside contributors.

**Unit 10: Building a Voice Guard and QDash Repository Memory**

I extended my shared voice guide with rules for upstream communication and installed a voice-guard hook to review GitHub issue comments before posting. My first claim attempt was blocked because the hook could not resolve $HOME in the --body-file path, so I retried with an absolute path and successfully posted the checked comment. I also created a 41-line CLAUDE.local.md in my QDash clone to preserve repository conventions, testing instructions, and Region Zoom investigation notes, then excluded it from Git using .git/info/exclude. A later audit caught an outdated assignment status and an incorrect source-code line range in the memory file, so I corrected both while keeping the file local and untracked.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I found this issue through a mix of my own issue-scout and the CodePath selection process. My first live scout scan in Unit 9 surfaced mostly brand-new, batch-filed Python test tasks. Next, I picked three candidates from the CodePath selection site and graded each one with the scout in direct mode: oqtopus-team/qdash#1218, PowerGridModel/power-grid-model-io#107 and AlphaWaveSystems/flutter-probe#401. After I patched the rubric in Unit 10, I regraded all three. QDash #1218 came back with an accept verdict, 5/5 required checks passed, and a difficulty of moderate. The issue is a `good first issue` opened by a QDash collaborator: the Region Zoom toggle on the `/metrics` and `/chip` pages changes width when it is switched, and the fix should keep the width stable. I chose it over the other accepted issues because it combines front-end development with a visible user-experience problem, which fits my interest in both software engineering and UX/UI design. It also builds on my JavaScript/TypeScript/React experience, even though it isn't the Python work I had first aimed for. I want to learn how to reproduce a real bug in an established project's local environment, measure what actually changes, write a fix that follows the project's UI guidelines, and test it the way the maintainers expect before it goes through code review.

The scout was useful, but it wasn't perfect. Its availability check caught claims hidden in issue text and fixes in unlinked PRs. Even so, it accepted issues that were partly done: on #401 the maintainer quietly removed one of the three items after I first graded it. For #1218, it guessed the wrong control (the Qubit/Coupling tabs) until the issue's video was inspected and showed the Region Zoom card, so I corrected the saved entry. The bigger change was the rubric itself. My original "Newcomer scope" check rejected issues whose design was still open, which would have ruled out many real, identifiable tasks. The `scope-feasible` patch fails only issues with no single piece of work, and moves open design questions into a difficulty note instead. I posted my claim on October 28, 2026 (https://github.com/oqtopus-team/qdash/issues/1218#issuecomment-6485516502). Thirty minutes later, maintainer orangekame3 assigned the issue to me and replied, "Thanks! Please go ahead." (https://github.com/oqtopus-team/qdash/issues/1218#issuecomment-6485956018). I haven't reproduced or fixed the bug yet; reproducing it locally is my next step.

**Toolkit**

- Tool: my `issue-scout` Claude skill (my search strategy plus a five-check rubric). I ran it in scan mode for the Unit 9 live search and in direct mode on the three CodePath selection-site issues, gathering the evidence through `gh` and the GitHub API, and saved every read-out in `scan-output.md`.
- What it produced: in Unit 9, a live scan narrowed 300 results to 250 candidates and graded the top 5, and on 2026-10-23 it accepted all three selection-site issues. After the patch, the Unit 10 regrades (the "Unit 10 — Direct Re-grade" sections in `scan-output.md`, 2026-10-28) gave QDash #1218 accept, 5/5, moderate; power-grid-model-io#107 accept, ambitious; and flutter-probe#401 accept, straightforward.
- Difficulties: the original "Newcomer scope" check was too restrictive. It failed an issue whenever the design was still being debated or a maintainer said it touched core internals, but most real issues have some open edge even when the work is clearly identifiable. #107, where four fixes were proposed and none chosen, was at risk of rejection for that reason alone. The scout also misidentified the #1218 control before the video was inspected, and its availability check passes partly resolved issues such as #401.
- What changed: I applied the `scope-feasible` patch. It fails an issue only when there is no single piece of work (a codebase-wide checklist, an "improve X everywhere" or a container issue), and it sends open design edges to a difficulty note: straightforward, moderate or ambitious. The regrade confirmed the improvement: #107 is now accepted and labeled ambitious instead of being at risk, while umbrella issues like oppia#21970 should still fail (I haven't regraded that one). I also corrected the #1218 entry after the video inspection, and I would update the evidence guide to inspect issue attachments before naming where a change lives.

---

## Understanding the Issue

**Problem Description**

The Region Zoom card in QDash's chip and metrics grids changes width when it is switched on or off (12.59375 px in my local measurements), so it and the controls beside it shift each time it is toggled.

**Expected Behavior**

From the issue: "The width should not change even when the toggle is switched. Use a fixed width." In measurable terms: the card's outer `<label>` has the same width with the toggle off and on, in all four views on `/metrics` and `/chip`.

**Current Behavior**

I reproduced it locally on `develop` at `917f2da5` (Chrome 153, 957 × 827 viewport; details under Reproduction Process). With the toggle off the card's outer `<label>` is 332.578125 px wide, and with it on it is 345.171875 px, a change of +12.59375 px that is the same in all four views. Switching it on changes the subtitle from "Enable to zoom into specific regions" to "Click any region on the grid to zoom in" and adds an `Active` badge; switching it off returns the card to the narrower width. The issue's video shows the same thing: frames I extracted and measured show the card's right edge moving from about 1117 px to about 1142 px in the recording.

**Affected Components**

- `ui/src/components/ui/RegionZoomToggle.tsx`, the shared component. On `develop` its `<label>` has no width, min-width or reserved space for its text, so it is as wide as its content.
- Four grids in `ui/src/components/features/` render it, each inside a wrapper `<div>` that sets no width: `chip/QubitGrid.tsx` (`<RegionZoomToggle` at :753), `chip/CouplingGrid.tsx` (:777, with the Forward/Reverse button after it), `metrics/QubitMetricsGrid.tsx` (:697) and `metrics/CouplingMetricsGrid.tsx` (:631, in a row that also holds the Forward/Reverse button).
- Cause: the card's content changes between states (see Analysis below). I have measured the card, not each line inside it, so which line sets the width is still an inference.

**Toolkit**

- Tool: Claude Code investigation using `gh` / the GitHub API, plus frame extraction and measurement of the issue's attached video; then my own measurements in Chrome DevTools during reproduction.
- What it produced: identified `RegionZoomToggle.tsx` as the affected shared component, measured the width change in the recording, and confirmed the component is unchanged on `develop` apart from #1321 (which kept its classes and text). The local reproduction then confirmed the change (+12.59375 px in all four views), and I updated these answers from the video estimate to the measured values.
- Difficulties: the scout's first guess about the location was wrong (the Qubit/Coupling tabs), and the UI guidelines path cited in #1422 had moved (now `docs/developer-guide/ui/guidelines.md`).
- What changed: inspecting the video corrected the target before I claimed the issue.

---

## Reproduction Process

**Environment Setup**

- QDash: `develop` at commit [`917f2da5`](https://github.com/oqtopus-team/qdash/commit/917f2da5) ("docs(repo): align pi package guides and policies (#1700)"), with no local source changes.
- Machine: macOS 26.6.2 (arm64), Docker Desktop 4.97.0 (Engine 29.9.2), Node 24.22.2, Bun 1.4.4, uv 0.13.6.
- Browser: Google Chrome (user-agent version 153.0.0.0) on macOS, viewport 957 × 827 CSS px, device pixel ratio 2.
- Setup: I started the stack with `task dev-local`. That runs MongoDB, PostgreSQL, the Prefect server, the deployment service and the user-flow worker in Docker, the API on the host at `:5715`, and the UI with `bun run dev` at `:5714`. I logged in as the local admin, whose default project is created on the first API start.
- Test chip: I created a disposable 16-qubit chip through the API with `POST /chips` and `{"chip_id": "repro-1218-16q", "size": 16, "topology_id": "square-lattice-mux-16", "config": {"create": false}}`. It gives a 4×4 square grid with 16 qubits and 48 couplings, and has no calibration data, so the grid cells are empty.
- Challenge: on the first start, the MongoDB container kept crashing. MongoDB 9.0.4 refuses to run on Linux kernels 6.19.0 to 7.0.13 (SERVER-121912), and Docker Desktop's VM was on a kernel in that range. I stopped the stack without removing volumes or changing the image, updated Docker Desktop to 4.97.0 (kernel 7.0.14-linuxkit), and the stack then started cleanly.
- Difference from the issue: the issue does not state a browser, OS or window size.

**Steps to Reproduce**

1. Open each view with the chip `repro-1218-16q` selected:
   - `/metrics`, Qubit: `http://localhost:5714/metrics?chip=repro-1218-16q&type=qubit`
   - `/metrics`, Coupling: `http://localhost:5714/metrics?chip=repro-1218-16q&type=coupling`
   - `/chip`, Qubit tab: `http://localhost:5714/chip?chip=repro-1218-16q&view=1q`
   - `/chip`, Coupling tab: `http://localhost:5714/chip?chip=repro-1218-16q&view=2q`
2. Keep the **Lock** tab selected and stay at full zoom (no region clicked). The Region Zoom card shows next to the Lock/Zoom tabs.
3. In Chrome DevTools, measure the width of the Region Zoom card's outer `<label>` (classes starting `flex items-center gap-3 p-3 rounded-lg border-2`) with the toggle off.
4. Turn the toggle on (the `Active` badge appears) and measure the width again.
5. Observed result: the card is 12.59375 px wider with the toggle on, in all four views. The issue expects the width to stay the same.

**Reproduction Evidence**

- **Commit showing reproduction:** none. The reproduction needed no code changes, so there is no reproduction commit. It was run on QDash commit [`917f2da5`](https://github.com/oqtopus-team/qdash/commit/917f2da5).
- **Screenshots/logs:** none verified yet. The evidence is the width measurements below, which I took manually in Chrome DevTools at the viewport above.

  | View | Off | On | Change |
  |---|---|---|---|
  | Metrics — Qubit | 332.578125 px | 345.171875 px | +12.59375 px |
  | Metrics — Coupling | 332.578125 px | 345.171875 px | +12.59375 px |
  | Chip — Qubit | 332.578125 px | 345.171875 px | +12.59375 px |
  | Chip — Coupling | 332.578125 px | 345.171875 px | +12.59375 px |

- **My findings:** the bug reproduces locally. The Region Zoom card grows by 12.59375 px when the toggle is switched on, the same amount in every view on `/metrics` and `/chip`, which matches the issue's "its width changes slightly". In `ui/src/components/ui/RegionZoomToggle.tsx`, the on state adds an `Active` badge and swaps the subtitle from "Enable to zoom into specific regions" to "Click any region on the grid to zoom in", and the `<label>` has no fixed width. That content change is the likely cause, but I have not confirmed the root cause. I have not modified QDash source code, and I have only checked one window size in one browser.
- **Links:** issue https://github.com/oqtopus-team/qdash/issues/1218; my claim https://github.com/oqtopus-team/qdash/issues/1218#issuecomment-6485516502; the maintainer's go-ahead https://github.com/oqtopus-team/qdash/issues/1218#issuecomment-6485956018.

**Toolkit**

- Tool: my `repro-check` Claude skill, which grades a claim comment and a repro report against the issue on five required checks (Environment, Steps, Behavior Match, Outcome Honesty and Repo Communication) and the voice guide. I ran it on `claim-draft.md` and `repro-draft.md` for #1218 before posting anything.
- What it produced: the first run returned reject. Four checks passed, but Environment failed because my report said the browser, browser version and window width were "not recorded for these measurements", and for a bug about rendered width those details matter. It also suggested naming the exact element I measured. After the revision, the second run returned accept, with all five checks passing and no voice-guide rules broken.
- Difficulties: I had measured the widths before writing down the browser setup, so the first draft could only say honestly that it was missing. The grader also could not confirm that the `?type=` and `?view=` URL parameters select the tabs, so I will click each link once before finalizing this documentation.
- What changed: I added Chrome 153.0.0.0, the 957 × 827 CSS px viewport and the device pixel ratio of 2 to the Environment section, removed the "not recorded" line, and named the card's outer `<label>` as the measured element. The measurements stayed the same.

---

## Solution Approach

**Analysis**

The cause is in the shared component `RegionZoomToggle` (`ui/src/components/ui/RegionZoomToggle.tsx`), not in the grids that use it. On `develop` (`917f2da5`) its outer `<label>` is `flex items-center gap-3 p-3 ...` with no `w-*` or `min-w-*`, so the card is exactly as wide as its content. Two parts of that content depend on `enabled`:

- line 27: `{enabled && <span className="badge badge-primary badge-xs">Active</span>}` adds the badge to the title row only when it is on;
- lines 29–33: the subtitle `<p>` shows "Enable to zoom into specific regions" when it is off and the longer "Click any region on the grid to zoom in" when it is on.

The text column is `flex-1`, but because the label itself has no width, there is no extra space for it to fill. So whichever line is widest in the current state sets the card's width, and switching states changes it. The only other per-state differences are colors (border, background, icon tile), which don't affect width.

The four callers in `ui/src/components/features/` (`chip/QubitGrid.tsx`, `chip/CouplingGrid.tsx`, `metrics/QubitMetricsGrid.tsx`, `metrics/CouplingMetricsGrid.tsx`) keep `regionSelectionEnabled` in local state, pass it in, and wrap the card in a `<div>` that adds `invisible pointer-events-none` when the card shouldn't show. That wrapper sets no width, so the card's width flows straight into each toolbar row. In the two Coupling views the Forward/Reverse button sits beside it, so it should shift by the same amount (I haven't measured the button). Because every caller gets the same component, fixing it once should fix all four views, which matches my identical +12.59375 px measurement in each.

A related accessibility detail: the checkbox gets its accessible name from the whole `<label>`, so on `develop` that name already changes with the state, from "Region Zoom Enable to zoom into specific regions" to "Region Zoom Active Click any region on the grid to zoom in". That is existing behavior and not part of this bug. What matters for this fix is that keeping both subtitles in the page must not add the hidden one, or the hidden badge, to the name.

Confirmed vs. inferred: the width change, its size and the fact that it is identical in all four views are measured. That the conditional content causes it follows from the component code. Which line sets the width is an inference: the title row ("Region Zoom" plus the badge) looks shorter than either subtitle, which would make the longer "on" subtitle the cause, but I measured the whole card, not each line. Step 1 below checks it.

**Proposed Solution**

Keep the card's width stable by giving it the same content in both states, sized to whichever state is wider, instead of setting a hard-coded CSS width.

- Keep the `Active` badge mounted in both states, hidden with Tailwind's `invisible` (`visibility: hidden`, which still takes up space) and `aria-hidden="true"` while off.
- Put both subtitles in one `grid` cell (`col-start-1 row-start-1`) so the `<p>` is always as wide and as tall as the longer one. Show the one for the current state, and hide the other with `invisible` and `aria-hidden="true"`.
- Keep the existing accessibility structure. The checkbox stays a native `<input type="checkbox">` inside the `<label>`, which is still the click target and still provides its accessible name. The only requirement the fix adds is that hidden content (`aria-hidden`) stays out of that name.

*Fixed CSS width vs. stable intrinsic width.* The issue's author, `dvlpwork` (a repository collaborator), wrote "Use a fixed width." Maintainer `orangekame3`, who assigned me the issue, said "Please go ahead" and gave no implementation direction. These are two different things, and they are not equivalent:

- A **fixed CSS width** is an explicit value on the card, such as a `w-*` class on the `<label>`. It matches the issue's words exactly and is one class. But the number has to be picked to fit the longer subtitle at the current font, so it can clip or wrap the text if the copy, font, browser zoom or user font size changes. Without `max-w-full` it can also overflow narrow toolbars, against QDash's design policy that "Interactive targets remain usable at narrow viewport widths."
- A **stable intrinsic width** (this plan) reserves the space of the wider state in both states, so the browser sizes the card the same way every time. It achieves what the issue wants, a width that doesn't change on toggle, without a guessed number, and it follows the text if anything changes. At narrow widths it behaves like `develop`. Its costs: the off state becomes as wide as the on state, the component keeps two hidden elements, and it is not the literal fixed width the issue asks for.

I prefer the stable intrinsic width, but it departs from the issue's stated approach, so I'll ask in my plan comment which the maintainers prefer before opening a PR. **Fallback** if they want an explicit width: replace the hidden-badge and stacked-subtitle markup with a `w-*` class on the `<label>`, sized from the measured on-state width, plus `max-w-full` so it can't overflow its row. Then re-check the same browser checks below, including that the subtitle doesn't clip or wrap differently between states.

*Scope.* In scope: `ui/src/components/ui/RegionZoomToggle.tsx` and its test file `ui/src/components/ui/__tests__/RegionZoomToggle.test.tsx`. Not in scope:

- the four callers and their wrapper `<div>`s, and the toolbar rows;
- the component's props (`enabled`, `onToggle`) and the toggle's click behavior;
- the subtitle wording, the colors and the badge styling;
- the checkbox's accessible-name structure (no new `aria-labelledby` or `aria-describedby`; the name already changes with the state on `develop`, which is a separate accessibility question);
- the zoom logic itself;
- `globals.css`, inline styles, other components, and generated code (`ui/src/client/`, `ui/src/schemas/`).

The styling follows the project's DaisyUI-first, Tailwind-for-layout policy.

*Status.* My QDash working tree has an uncommitted draft of this change: the hidden badge and the stacked subtitles. On 2026-10-29 that draft passed the focused test (5/5), `task ci-ui` (877 tests) and `task ci-ui-build`. It has not been reviewed by a maintainer and has not been checked in a browser. It is a draft to check against this plan, not a finished fix.

*Risks and unknowns.*

- The maintainers may prefer a literal fixed width, as the issue suggests; the fallback covers that.
- Which line sets the width is unconfirmed (step 1).
- jsdom honors `aria-hidden` when it computes accessible names, but that doesn't prove Chrome leaves hidden content out of the name. Step 4 checks that in the browser.
- I have only checked one browser at one window size so far.

**Implementation Plan**

1. **Confirm the cause in the browser.** With the dev server running (`task dev-local`), measure in DevTools the title row and each subtitle line in both states, to confirm which line sets the card's width. Record the result under Analysis.
2. **Review the component draft** in `ui/src/components/ui/RegionZoomToggle.tsx` against the Proposed Solution: the badge always mounted and `invisible`/`aria-hidden` while off, both subtitles stacked in one grid cell, and no props, colors, wording, callers or accessible-name structure changed. Adjust it only if step 1 or this review finds a problem.
3. **Regression tests** in `ui/src/components/ui/__tests__/RegionZoomToggle.test.tsx`. jsdom does no layout and loads no Tailwind CSS, so these tests check structure and accessibility attributes, not pixel width or real visibility.
   - Keep the two existing click tests.
   - Keep the test that both states render the same elements and text, described as a proxy for stable width.
   - Accessible checkbox: the checkbox is found by role with a name containing "Region Zoom" in both states.
   - Checked state: add `toBeChecked()` / `not.toBeChecked()` for each state.
   - Inactive content hidden from assistive technology: keep the `aria-hidden="true"` assertions on the inactive subtitle and on the badge while off, and keep the draft's `not.toHaveAccessibleName(expect.stringContaining(...))` checks that the hidden text is not in the checkbox's name. Treat the `invisible` class assertions only as class checks.
   - The draft's positive checks that the name contains the visible subtitle and "Active" describe how the name already works on `develop`. They don't by themselves show the accessibility is correct, so the hidden-content checks above carry that weight.
   - For keyboard use, assert the checkbox is an enabled native `<input type="checkbox">` that can take focus and has no negative `tabindex`. The project has no `@testing-library/user-event`, and `fireEvent` doesn't trigger a native checkbox's Space key, so actual key presses are checked by hand in step 4.
   - Run `cd ui && bun run test:run src/components/ui/__tests__/RegionZoomToggle.test.tsx`.
4. **Manual browser verification (not done yet).** Re-run my reproduction steps on the changed code in Chrome at 957 × 827, with the Lock tab at full zoom, on all four views: `/metrics` Qubit and Coupling, `/chip` Qubit and Coupling. Pass if:
   - the card's outer `<label>` has the same width and height off and on, in every view;
   - neither subtitle is clipped or cut off;
   - in the Coupling views, the Forward/Reverse button keeps the same position.

   Then repeat at a narrow viewport (about 375 px wide). Pass if the card's width still doesn't change on toggle and the toggle stays reachable and usable. Check keyboard use: Tab reaches the toggle with a visible focus ring, and Space switches it on and off. In Chrome's Accessibility pane, check that the checkbox's role is checkbox, its checked state matches, and its name includes only visible text: neither the hidden subtitle nor the hidden badge. Record the before and after widths in Testing Strategy.
5. **Repository checks.**
   - Run the ship-gate manifest's three checks: the focused test, `task ci-ui` and `task ci-ui-build`. `docs/developer-guide/ui/testing.md` asks for the last two because this is a shared component.
   - Before pushing, run `task check` from the repo root by hand, as `docs/developer-guide/development-flow.md` requires, and review its auto-fix diff. It's in the manifest's second table because it rewrites files. My fork's `develop` may lag upstream, so I'll check which `LEAKS_BASE` to use first.
   - Only push once each command exits 0.
6. **Commit and PR** (later step, after a maintainer has answered the fixed-width question): a Conventional Commit with scope `ui` that references #1218, and a PR into `develop` using the repo's template. The PR records the commands and results, and says which width approach was used and why.

Deviations:

- 2026-10-29: the component and test changes were drafted in my working tree before I wrote this plan. I've kept them uncommitted, and the steps above treat them as a draft to check rather than finished work.
- 2026-10-29: in my review before plan-check, I moved the fixed-width question from the PR to the plan comment, so it's answered before I build further. I also added a new accessible-name structure (`aria-labelledby`/`aria-describedby`) to the plan. Plan-check accepted that version.
- 2026-10-29, after plan-check: I took the accessible-name structure back out to keep the change focused on #1218. It's an optional accessibility improvement that the width fix doesn't need, so I'll only revisit it if testing shows the width fix requires it. The tests and browser checks still make sure the hidden content is not exposed. I also corrected the attribution: "Use a fixed width" comes from the issue's author, not from the maintainer who assigned me.

**Toolkit**

- Tool: my `plan-check` Claude skill, which grades a plan and a draft plan comment against the issue and my posted reproduction evidence on six required checks (Diagnosis & Grounding, Bounded Scope, Executability, Honesty & Unknowns, Observable Test, Thread & Repo Communication), plus my voice guide. Before running it, I used Claude Code to read issue #1218 with `gh`, the component and its four callers, `docs/developer-guide/ui/design-policy.md` and `docs/developer-guide/ui/testing.md`, and to review the uncommitted draft against them.
- What it produced: ACCEPT, with all six required checks passing (6/6) on `plan.md` and `plan-comment.md`. Its review feedback noted that the `aria-labelledby`/`aria-describedby` change in that version was an optional accessibility improvement, not something the width bug needs.
- Difficulties: the fixed-width tradeoff. The issue asks for "a fixed width", but a hard-coded width risks clipping the text and works against the design policy's narrow-width rule, so the literal request and the fix I prefer pull in different directions. Accessibility scope: reviewing the draft's tests showed the checkbox's name already changes with the state, and I overreached by planning a new name structure for it. jsdom: it does no layout and loads no CSS, so unit tests can't show the width stays the same or that Chrome hides the inactive text; only manual browser checks can. Running plan-check headlessly also failed at first, because `claude -p` couldn't approve reads of the skill's own files, so the graded run happened outside headless mode.
- What changed: I narrowed the accessibility scope. I removed the `aria-labelledby`/`aria-describedby` work and kept the tests for an accessible checkbox, its checked state, inactive content hidden from assistive technology, the existing clicks, and manual keyboard checks. I also clarified the plan: "Use a fixed width" is now attributed to the issue's author rather than to the maintainer, the fixed-width question moved into the plan comment with an explicit `w-*` + `max-w-full` fallback, and both changes are recorded as dated deviations. `plan.md` and this section stay word-for-word the same.
---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

**2026-10-28: Claim posted (claim only, not assigned)**

- My repro-check skill graded the claim draft (claim-only mode) and accepted it. Outcome Honesty and Repo Communication passed; Environment, Steps and Behavior Match were not yet applicable.
- My voice guard's manual check passed the final draft. My first post attempt was blocked by my own voice-guard hook, because the hook could not resolve `$HOME` in the `--body-file` path. Nothing was posted that time. I retried once with the absolute path, and the hook passed.
- I posted the claim comment as Dommgrand at 9:40 PM Eastern: https://github.com/oqtopus-team/qdash/issues/1218#issuecomment-6485516502
- When I checked afterwards, the issue was open and unassigned, and there was no maintainer response yet.
- No reproduction, code, PR or merge exists yet.
- Next step: wait for assignment, and prepare to reproduce locally (run the UI with `task dev-local`, toggle Region Zoom on `/metrics` and `/chip`, and measure the card's width in both states).

**Toolkit**

- Tool: my repro-check skill (claim-only live mode) to grade the claim draft, and my voice guard, run both as a manual check (`check_voice.py --draft`) and as the PreToolUse hook on the `gh issue comment` command.
- What it produced: repro-check accepted the claim draft. The manual voice check passed, and the hook passed the final post.
- Difficulties: the hook blocked the first post attempt because it read `$HOME` in the `--body-file` path literally and could not find the file.
- What changed: I retried once with the absolute path. I would update the hook to expand `$HOME` and `~` in body-file paths.

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
