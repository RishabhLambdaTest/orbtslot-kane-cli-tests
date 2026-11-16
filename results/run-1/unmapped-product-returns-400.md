---
test: ../../.testmuai/tests/unmapped-product-returns-400_test.md
status: passed
started: 2026-11-14T18:34:15.679Z
duration_s: 32
session_id: 96fa93bf-a10b-4d51-aec3-e4a51033a3ca
---

# Unmapped product returns 400 — Result

## Step 1 ✓ passed (30s)
md5: a7b5ebcbdf7d91925de08e5c3d72f461
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{unmapped_product_code}} known to be unmapped, and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.
