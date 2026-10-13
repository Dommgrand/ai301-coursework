# Unit 3 — Plan and Build

---

## Posted upstream

**GitHub username**

Dommgrand

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/65#issuecomment-6155010314

Comment text

Note: This plan comment is being posted after implementation and verification were completed. It documents the diagnosis, scope, and testing approach used for the existing fix.

Running tests/unit/test_review_service.py with –runxfail produced 13 failures and 6 passes, including AttributeError: ‘coroutine’ object has no attribute ‘first’. The result objects returned by mock_db_session.execute were configured as AsyncMock, causing synchronous result methods such as scalars().first() and scalars().all() to behave incorrectly. The result objects needed Mock, while mock_db_session.execute needed to remain an AsyncMock.

After correcting the mocks, a second defect became apparent in the ordered-results test: its assert_called_once() expectation was incorrect because list_reviews() executes two database queries—one for the review results and another for the total count. The assertion was updated to verify that mock_db_session.execute is called twice.

The changes were limited to tests/unit/test_review_service.py. The obsolete xfail markers were removed, and no production-code changes were necessary.

Verification completed successfully:

* Affected tests: 19 passed.
* Full unit suite: 388 passed, 40 xfailed, 1 warning.
* make check: passed.

The implementation is available in PR #78.

---

## Your branch

**Branch**

fix/65-async-mocks⁠

https://github.com/Dommgrand/pathreview-ai301-fa26-howard/tree/fix/65-async-mocks

**Evidence**

Before

* Baseline commit: 99673c7
* Command: python -m pytest tests/unit/test_review_service.py --runxfail -q
* Result: 13 failed, 6 passed.
* Observed failure: AttributeError: 'coroutine' object has no attribute 'first' and related errors involving .all(). The result objects returned by mock_db_session.execute were mocked asynchronously even though their result methods are synchronous.

After

* Branch: fix/65-async-mocks
* Commit: 6b05700
* Command: python3 -m pytest tests/unit/test_review_service.py --runxfail -q
* Result: 19 passed, 1 warning in 0.51 seconds.
* Warning: Pydantic reports that class-based configuration in core/config.py is deprecated. The tests still passed.
* Fix: Changed the database result-object mocks from AsyncMock to Mock, retained AsyncMock for mock_db_session.execute, removed obsolete xfail markers, and corrected the ordered-results test to expect two database queries.
* Scope: Changes were limited to tests/unit/test_review_service.py; no production-code changes were needed.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

18/20 scored items — PASS.

This was my final evaluation run, recorded in eval-run.txt. It met the required agreement threshold of 18/20.

**Package analysis**

Package: pkg-09

* My rubric’s verdict: Reject.
* Gold label: Accept.
* Reason: My rubric failed this package on the Honesty & Unknowns check. That check requires the plan to distinguish confirmed observations from working hypotheses and unresolved implementation details when the distinction matters. My rubric appears to have judged the package’s handling of uncertainty too strictly, while the gold label considered the plan acceptable. This disagreement shows that a plan can be acceptable without satisfying every expectation as explicitly as my rubric might prefer.

**Check rationale**

Exact check from rubric.md:

  A plan does not need to list an unknown separately when the available evidence is sufficient for the proposed bounded plan and test, and it may state a reasonable     implementation hypothesis without treating it as proven.

I included this clarification to avoid requiring artificial unknowns when the evidence already supports a bounded plan and a testable approach. I wanted the rubric to distinguish between a reasonable hypothesis that can be tested and a claim presented as a proven fact without enough evidence. This makes the check more practical while still requiring honest treatment of uncertainty.

**Trade-offs**

The Honesty & Unknowns check rejected pkg-09 and pkg-14, even though both gold labels were Accept. This produced two false negatives and contributed to the final 18/20 agreement score. The trade-off is that a conservative check can catch unsupported certainty but may also reject a reasonable plan whose uncertainty is handled adequately without being stated in exactly the way the rubric expects. The results show that this check is an area where the rubric could be calibrated further.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
