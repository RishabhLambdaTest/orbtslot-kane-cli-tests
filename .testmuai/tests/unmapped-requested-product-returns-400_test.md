---
assurance:
  id: t-19
  base: sha256:2b16a2185bee0124666cfcf1240471f0dd476a016c5412fc0827d0b37b0b3e25
---
# Unmapped requested product returns 400

> On forward look, a syntactically valid but unmapped product returns 400.

## Step 1 @verifies ac-15

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, known unmapped productCode={{unmapped_product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.
