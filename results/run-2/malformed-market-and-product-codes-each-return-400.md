---
test: ../../.testmuai/tests/malformed-market-and-product-codes-each-return-400_test.md
status: passed
started: 2026-11-14T18:45:23.499Z
duration_s: 198
session_id: 01911a67-a407-4d60-9a11-1cc17517fc7f
---

# Malformed market and product codes each return 400 — Result

## Step 1 ✓ passed (36.8s)
md5: 24cf60deebae640787c9c3c1d19ec0f3
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode="AB CD", productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, encoding the space as a query value, then assert HTTP status equals 400.

## Step 2 ✓ passed (34s)
md5: 17461b01bd035d441863ebf69cb57a45
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode="AB CD" and X-LP-User-Id={{lp_user_id}}, encoding the space as a query value, then assert HTTP status equals 400.

## Step 3 ✓ passed (28.9s)
md5: 967b749ab7a8c93883fc37158d54a462
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode=ABCDEFGHIJKLMNOPQRSTU, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.

## Step 4 ✓ passed (33.5s)
md5: e4de4f8477046cce564504dbb216d1f8
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode=ABCDEFGHIJKLMNOPQRSTU and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.

## Step 5 ✓ passed (33s)
md5: 3b07f1507c771309c5de80a85968ddd3
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, omitting marketCode, then assert HTTP status equals 400.

## Step 6 ✓ passed (28.2s)
md5: b3189d4da4366688e69c134140d3def8
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}} and X-LP-User-Id={{lp_user_id}}, omitting productCode, then assert HTTP status equals 400.
