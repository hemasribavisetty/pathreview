# JOURNAL

## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/146

**Issue title:** PII scrubber fails to redact parenthesized US phone numbers

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
This issue affects the safety layer of the application, specifically the PII scrubber that is responsible for detecting and redacting sensitive information. Currently, phone numbers written with parentheses around the area code, such as `(415) 555-1234`, are not detected and therefore remain visible. A successful fix will update the detection logic so these phone numbers are redacted while preserving the existing behavior for other supported phone number formats. I chose this issue because it has a well-defined scope and is a good first contribution to the project.

**Branch name:** fix/146-redact-parenthesized-phone-numbers

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger

### Selection notes ("Is this right for me?" checklist)

- [x] The issue has a clearly defined problem statement.
- [x] The expected behavior is easy to understand.
- [x] The issue appears to be limited to a small part of the safety layer.
- [x] I expect the fix to involve updating the phone-number detection logic and adding or updating tests rather than making large architectural changes.
- [x] I selected this issue because it is a Tier 1 issue and is appropriate for a first contribution to a larger codebase.

---

## Week 8 — Reproduction & solution planning

**Reproduction commit link:**
https://github.com/hemasribavisetty/pathreview/commit/99e431f

**Reproduction summary:**
I reproduced the issue by locating the PII scrubber implementation in `safety/pii_scrubber.py` and reviewing the current phone number detection logic. I confirmed that the issue is related to the regular expression used for US phone numbers, which does not reliably handle phone numbers written with parentheses around the area code, such as `(415) 555-1234`. I also identified the related unit tests in `tests/unit/test_pii_scrubber.py` that will be used to validate the fix.

**PLAN.md link:**
https://github.com/hemasribavisetty/pathreview/blob/fix/146-redact-parenthesized-phone-numbers/PLAN.md

**Walkthrough video (recommended):**
Not recorded.

**Blockers or open questions:**
The backend setup exposed startup issues in the provided starter repository. Although the frontend and Docker services were configured successfully, the backend initialization encountered database startup issues. While waiting for guidance from the course staff, I continued analyzing the relevant code and prepared a detailed implementation plan for the assigned issue.


## Week 9 — Solution building & PR submission

### Check-in 1 (mid-week)

**Current progress:**

- Investigated the PII scrubber implementation.
- Identified the phone-number regular expression causing the issue.
- Planned the implementation.
- Updated the regex.
- Verified issue-specific tests.

**Next steps:**

Open the pull request, request review, and complete final testing.

**Blockers:**

The backend setup exposed unrelated startup issues in the starter repository, but they did not prevent implementation of Issue #146.

---

### Check-in 2 (end of week)

**PR link:**

<GitHub PR URL>

**Branch:**

fix/146-redact-parenthesized-phone-numbers

**What you built:**

Updated the US phone-number detection logic so that phone numbers written with parentheses around the area code are correctly detected and redacted. Existing supported US phone-number formats continue to work.

**Tests added or updated:**

Updated:

- tests/unit/test_pii_scrubber.py

Verified phone-number detection and redaction behavior.

**Self-review confirmation:**

- [ ] make check passes
- [ ] make test-unit passes

**Draft PR feedback received from:**

None