---
test: ../../.testmuai/tests/invalid-day-counts-each-return-400_test.md
status: passed
started: 2026-11-14T18:45:23.495Z
duration_s: 70
session_id: b92919cd-322e-427b-a763-41b2a2f1da7c
---

# Invalid day counts each return 400 — Result

## Step 1 ✓ passed (35.8s)
md5: 2cc0bbc2c2b008a49971bb70c9688f48
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, X-LP-User-Id={{lp_user_id}} and dayCount=0, then assert HTTP status equals 400.

## Step 2 ✓ passed (30s)
md5: c9c920eddc4454a5b8b2ca3baf4fe647
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request another GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, X-LP-User-Id={{lp_user_id}} and dayCount=15, then assert HTTP status equals 400.
