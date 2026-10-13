# Plan: Fix async mocks in review service tests

## Diagnosis

The failures in tests/unit/test_review_service.py initially stemmed from an incorrect result-object mock configuration. After that issue was corrected, a second defect became apparent in the ordered-results test assertion.

First, the result object returned by mock_db_session.execute was configured as an AsyncMock. Although execute() is asynchronous, the returned database result object exposes synchronous methods such as scalars().first() and scalars().all(). Using AsyncMock for this result object causes these methods to behave incorrectly, producing coroutine-related AttributeError failures. The result object should instead use Mock, while mock_db_session.execute remains an AsyncMock.

Second, the ordered-results test expected mock_db_session.execute to be called only once. However, list_reviews() executes two database queries: one to retrieve the review results and another to retrieve the total count. The assertion should reflect the observed execution sequence by checking that mock_db_session.execute is called twice.

Both issues can be corrected within tests/unit/test_review_service.py without changing production code, database queries, schemas, or configuration. The existing reproduction and test suite provide a way to verify the corrections.

## Scope

### In scope

- Update the affected mocks in `tests/unit/test_review_service.py` so the result object returned by `db.execute()` uses a synchronous `Mock` interface.
- Keep `mock_db_session.execute` as an `AsyncMock` because the database execution boundary is asynchronous.
- Remove the obsolete `xfail` markers from the affected tests once the corrected mock behavior is verified.
- Update the ordered-results assertion to reflect the corrected execution behavior.
- Verify the affected tests and the broader unit test suite after the mock changes.

### Not in scope

- Changes to the production implementation in `review_service.py`.
- Changes to the application's asynchronous database behavior.
- Changes to database queries or schemas.
- Changes to unrelated test files.
- Changes to project configuration or test infrastructure.
- Refactoring the review service beyond what is necessary to correct the test mocks.

## Files / Areas

### Primary file

- `tests/unit/test_review_service.py` — affected async database mocks, obsolete `xfail` markers, and the ordered-results assertion.

### Related area

- The review service's database interaction pattern, specifically the boundary where `db.execute()` returns a result object whose `scalars()`, `first()`, and `all()` methods are used synchronously.

No production source files are expected to require changes.

## Approach

1. Review the affected tests in `tests/unit/test_review_service.py` and identify each instance where the result of `db.execute()` is represented by an `AsyncMock`.
2. Replace the result-object `AsyncMock` instances with `Mock` instances so their synchronous result methods behave like the objects returned by the database layer.
3. Keep `mock_db_session.execute` as an `AsyncMock`, preserving the asynchronous behavior at the database execution boundary. 
4. Remove the `xfail` markers from tests that are expected to pass after the mock correction.
5. Update the ordered-results test assertion to expect two calls to mock_db_session.execute, reflecting the separate results and total-count queries performed by list_reviews().
6. Run the affected test file to confirm that the coroutine-related `AttributeError` failures are resolved.
7. Run the broader unit test suite and project checks to verify that the correction does not introduce regressions.

## Test Plan

### Before-change reproduction

Run the affected test file at the reproduced failing state:

```bash
python3 -m pytest tests/unit/test_review_service.py --runxfail -q
```

Expected before-change result:

* 13 tests fail and 6 tests pass.
* The failures include AttributeError errors caused by coroutine results not providing the synchronous .first() or .all() methods expected by the review service tests.

### After-change verification

Run the affected test file after correcting the mocks:
```bash
python3 -m pytest tests/unit/test_review_service.py -q
```
Expected result:

* All tests in tests/unit/test_review_service.py pass.
* The previous coroutine-related AttributeError failures no longer occur.
* The asynchronous execute() boundary and synchronous result-object methods behave as expected.

Then run the broader unit test suite:
```bash
python3 -m pytest tests/unit -q
```
Expected result:

* The unit test suite passes without introducing new failures.

Finally, run the project’s complete check:
```bash
make check
```
Expected result:

* The project’s configured linting, type checking, and test checks pass.

### Success condition

The issue is considered resolved when the affected review service tests pass without the previous coroutine-related AttributeError failures and the broader project checks show no regression.

## Risks / Unknowns

### Risks

- Some tests may use the result-object mock differently from the affected cases, so each affected `AsyncMock` result setup must be reviewed rather than changing only the first failure encountered.
- Changing the mock type must not remove the asynchronous behavior of `db.execute()`. The session's `execute` method must remain an `AsyncMock`.
- Removing `xfail` markers before confirming the corrected behavior could hide an unresolved test failure, so they should be removed only after the affected tests are verified.


## Resolved Unknowns

* Affected mock setups: The affected result-object mocks were identified and corrected in tests/unit/test_review_service.py.
* Production-code changes: No production-code changes were necessary. The fix remained limited to the test file.
* Synchronous result methods: The corrected Mock result objects support the synchronous methods expected by the tests, including .first() and .all().
* Ordered-results assertion: The original assert_called_once() expectation was incorrect because list_reviews() executes two database queries: one for the results and one for the total count. The assertion now verifies mock_db_session.execute.call_count == 2.

These uncertainties were resolved during implementation and verification.

## Implementation and Verification

Implemented changes

* Replaced the affected result-object AsyncMock instances with synchronous Mock instances.
* Kept mock_db_session.execute as an AsyncMock.
* Removed the obsolete xfail markers from the affected tests.
* Updated the ordered-results assertion to check mock_db_session.execute.call_count == 2.
* Kept the changes limited to tests/unit/test_review_service.py; no production-code changes were needed.

Verification results

* Affected tests: 19 passed.
* Full unit test suite: 388 passed, 40 xfailed, 1 warning.
* Project checks: make check passed.
* Pull request: PR #78.

The reported baseline was 13 failures and 6 passes when the affected test file was run with --runxfail. After correcting the mocks, the affected tests passed without the previous coroutine-related AttributeError failures.


## Deviations

The implementation followed the final plan. During testing, fixing the asynchronous mock configuration exposed a second issue in the ordered-results test: list_reviews() executes two database queries, one for the review results and one for the total count. The test had expected only one call, so I updated the assertion to expect two. I also updated the plan to document this clarification. The changes remained limited to the unit tests; no production code was changed.
