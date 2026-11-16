---
assurance:
  id: t-17
  base: sha256:b26ec64b6132648f06f725f9bdd0a9ae87f5f91220762e298fd43b14f1d24793
---
# Out-of-range division IDs each return 400

> On forward look, divisionId zero or 32768 independently returns 400.

## Step 1 @verifies ac-26

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId=0, marketCode={{market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.

## Step 2 @verifies ac-26

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId=32768, marketCode={{market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.
