---
test: ../../.testmuai/tests/out-of-range-division-ids-each-return-400_test.md
status: passed
started: 2026-11-14T18:46:55.068Z
duration_s: 62
session_id: 54848a3e-3214-4ce5-a598-7ac2f88677c2
---

# Out-of-range division IDs each return 400 — Result

## Step 1 ✓ passed (29s)
md5: 9dee22855a9a4b805a35e999c38d3804
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId=0, marketCode={{market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.

## Step 2 ✓ passed (31.2s)
md5: aef59e196a933c3d12ed7952c8dccd00
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId=32768, marketCode={{market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.
