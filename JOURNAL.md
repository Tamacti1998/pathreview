## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/159

**Issue title:** structlog output is not captured by pytest caplog — log assertions fail suite-wide

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
Some unit tests that assert logging output are failing because `structlog` events are not being captured by pytest's `caplog` fixture. This causes log assertion failures across multiple test files; the underlying problem appears to be how `structlog` is configured relative to the standard `logging` handlers used by `caplog`. A successful fix will ensure test-time logging is routed so `caplog` can observe structlog output, restoring reliable log-based assertions. The change is likely in the test configuration or `core/logging.py` and affects tests under `tests/`.

**Branch name:** test/159-structlog-caplog

**Setup confirmation:** [ ] App runs locally at localhost:5173

**Cohort ledger:** [ ] Issue added to cohort ledger

**Checklist reasoning ("Is this right for me?"):**
- I am comfortable reading Python test code and runtime logging; this issue is primarily a test/configuration fix (no large unfamiliar subsystems).
- The change surface is small: adjust test logging capture or `core/logging.py` so `structlog` events route into the standard `logging` handlers that `pytest`'s `caplog` inspects.
- The fix doesn't require external services or data; unit tests and local test runs should validate the change.
- Therefore this is appropriate as a Tier 1 contribution for a first-time contributor.

