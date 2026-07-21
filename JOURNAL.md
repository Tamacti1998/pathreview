## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/159

**Issue title:** structlog output is not captured by pytest caplog — log assertions fail suite-wide

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
Some unit tests that assert logging output are failing because `structlog` events are not being captured by pytest's `caplog` fixture. This causes log assertion failures across multiple test files; the underlying problem appears to be how `structlog` is configured relative to the standard `logging` handlers used by `caplog`. A successful fix will ensure test-time logging is routed so `caplog` can observe structlog output, restoring reliable log-based assertions. The change is likely in the test configuration or `core/logging.py` and affects tests under `tests/`.

**Branch name:** test/159-structlog-caplog

**Setup confirmation:** [ ] App runs locally at localhost:5173

**Cohort ledger:** [ ] Issue added to cohort ledger
