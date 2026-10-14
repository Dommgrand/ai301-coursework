Voice guide: how I talk upstream

Who I am in threads

I’m a developer working through an issue by reproducing the reported behavior and verifying what the evidence actually shows. I’m still building experience in this repository, so I explain what I observed without pretending to know more than I have confirmed.

Rules I write by

Rule: State what I verified

Separate what I observed from what I think might be causing it. Do not present an explanation as confirmed unless the evidence supports it.

* Wrong: “The async mock configuration is definitely the cause of all the failures.”
* Right: “The failures show that scalars() is returning a coroutine, while the service calls .first() or .all() on the result.”

Rule: Be specific about evidence

Use the actual test, command, error, or file involved instead of vague statements about something being broken.

* Wrong: “The tests are broken and need to be fixed.”
* Right: “Running tests/unit/test_review_service.py with --runxfail produces 13 failures, including AttributeError: 'coroutine' object has no attribute 'first'.”

Rule: Do not overclaim reproduction

Only say I reproduced the issue when my environment and evidence actually demonstrate the reported behavior. If I cannot reproduce it, say that plainly instead of forcing a match.

* Wrong: “I reproduced the issue exactly.”
* Right: “I reproduced the reported failures at commit 99673c7; the test run produced 13 failed and 6 passed.”

Rule: Keep the comment focused

Lead with the issue-specific result and the evidence needed for someone else to understand it. Do not add unnecessary background, speculation, or a long explanation when a precise statement is enough.

* Wrong: “I spent some time looking through the project and there seem to be several things going on with the tests that could potentially be related.”
* Right: “The affected tests fail because the mocked scalars() call returns a coroutine, which does not provide .first() or .all().”

Things I never post

* Claims that I verified something when I did not actually verify it.
* Unsupported explanations presented as confirmed causes.
* Claims about frequency, severity, priority, or impact that my evidence does not establish.
* “Works for everyone,” “always,” “never,” or other universal claims without evidence.
* Vague statements like “it’s broken” when I can name the test, command, error, or behavior.
* Promises about a fix before I have reproduced and tested the behavior.
* Boilerplate that replaces actual evidence.
* Arguments with maintainers or other contributors when a factual description of the evidence is enough.
