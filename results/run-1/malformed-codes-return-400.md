---
test: ../../.testmuai/tests/malformed-codes-return-400_test.md
status: failed
started: 2026-11-14T18:32:51.844Z
duration_s: 100
session_id: 1e4fa6cc-975f-4a54-a14c-7edd49b19d1c
---

# Malformed codes return 400 — Result

## Step 1 ✓ passed (37s)
md5: c1b4850d928cd19181bf1eb173de150f
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, productCode={{product_code}}, X-LP-User-Id={{lp_user_id}} and no marketCode, then assert HTTP status equals 400.

## Step 2 ✗ failed (60s)
md5: e227a74b41e6a39111f525f59e72bf87
Reason: Captured requests lacked the specified invalid code variants, so their required statuses cannot be verified. — bug verdict: Required invalid API request variants were not sent [automation_bug/agent_misstep, confidence 0.98]
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, repeat otherwise valid GETs with a space-containing marketCode or productCode, a 21-letter marketCode or productCode, and omitted productCode, varying only one field at a time, then assert each HTTP status equals 400.
