---
test: ../../.testmuai/tests/invalid-date-and-lead-id-each-return-400_test.md
status: passed
started: 2026-11-14T18:45:22.241Z
duration_s: 69
session_id: 4e4d94d9-c047-4299-bc02-537930afaa6a
---

# Invalid date and lead ID each return 400 — Result

## Step 1 ✓ passed (31.3s)
md5: bff91725065278a2c6aa893b2d79b509
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate=not-a-date and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.

## Step 2 ✓ passed (33s)
md5: 0190378d408b03d75d685aff1872c98e
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, leadId=0 and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.
