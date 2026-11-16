---
assurance:
  id: t-18
  base: sha256:4adfbd6930dfce0c05431a98d2d6ca1635db12697994f016606a35a29011f4b3
---
# Invalid date and lead ID each return 400

> On forward look, invalid ISO date or nonpositive leadId independently returns 400.

## Step 1 @verifies ac-27

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate=not-a-date and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.

## Step 2 @verifies ac-27

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, leadId=0 and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.
