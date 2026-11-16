---
test: ../../.testmuai/tests/invalid-day-counts-return-400_test.md
status: passed
started: 2026-11-14T18:32:51.869Z
duration_s: 68
session_id: 41a0ce4a-eae4-4c10-bab7-c948c9eabdea
---

# Invalid day counts return 400 — Result

## Step 1 ✓ passed (37.5s)
md5: 2cc0bbc2c2b008a49971bb70c9688f48
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, X-LP-User-Id={{lp_user_id}} and dayCount=0, then assert HTTP status equals 400.

## Step 2 ✓ passed (28.2s)
md5: 64ce4150cd61c8f626c44a9a1f36a73f
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, repeat the otherwise valid GET with dayCount=15, then assert HTTP status equals 400.
