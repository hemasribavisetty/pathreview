# JOURNAL

## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/146

**Issue title:** PII scrubber fails to redact parenthesized US phone numbers

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
This issue affects the safety layer, specifically the PII scrubber. The current scrubber can redact some phone number formats, but it fails when a US phone number uses parentheses around the area code, such as `(415) 555-1234`. A successful fix would update the phone-number detection logic so parenthesized US phone numbers are also redacted consistently without breaking existing redaction behavior. I chose this issue because it has a clear scope and is a manageable first contribution.

**Branch name:** fix/146-redact-parenthesized-phone-numbers

**Setup confirmation:** [x] Frontend runs locally at localhost:5173  
Backend setup was partially completed. Docker, PostgreSQL, Redis, and the frontend were configured, but backend startup exposed duplicate SQLAlchemy index issues in the starter project.

**Cohort ledger:** [ ] Issue added to cohort ledger

**Selection notes:**
I chose a Tier 1 safety issue because it appears focused on one behavior in the PII scrubber rather than requiring broad architectural changes. The expected fix should likely involve updating a regex or detection pattern and adding a focused test case.