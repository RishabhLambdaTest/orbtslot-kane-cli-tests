---
assurance:
  id: t-16
  base: sha256:cfbb31973e3ca9dd1bbaa0cfd955052e916930715d23316ab1ea14c10ac2ec16
---
# Invalid day counts each return 400

> On forward look, dayCount zero or fifteen independently returns 400.

## Step 1 @verifies ac-11

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, X-LP-User-Id={{lp_user_id}} and dayCount=0, then assert HTTP status equals 400.

## Step 2 @verifies ac-11

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request another GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, X-LP-User-Id={{lp_user_id}} and dayCount=15, then assert HTTP status equals 400.
