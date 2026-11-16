---
assurance:
  id: t-21
  base: sha256:6728f58485321dc103156b187e276f08c79b5775badb8ee4ca525f811e6bdf0f
---
# Unknown market returns 404 for known division

> On forward look, a syntactically valid unknown market for a known division returns 404.

## Step 1 @verifies ac-17

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, syntactically valid unknown marketCode={{unknown_market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 404.
