---
assurance:
  id: t-20
  base: sha256:7208f1e6ec351105d4d96827c59478f3fc70bf522de8cac1baa26f158cb54a3f
---
# Unknown division returns 404

> On forward look, a syntactically valid unknown division returns 404.

## Step 1 @verifies ac-28

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with valid-range but unknown divisionId={{unknown_division_id}}, marketCode={{market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 404.
