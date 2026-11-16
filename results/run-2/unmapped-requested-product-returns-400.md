---
test: ../../.testmuai/tests/unmapped-requested-product-returns-400_test.md
status: passed
started: 2026-11-14T18:48:23.390Z
duration_s: 31
session_id: a78ba884-1f15-4ce1-a4ef-02a9f78049c8
---

# Unmapped requested product returns 400 — Result

## Step 1 ✓ passed (29s)
md5: 2bf79cdadd09e7fd278e65f101061bb5
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, known unmapped productCode={{unmapped_product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.
