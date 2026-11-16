---
assurance:
  id: t-23
  base: sha256:19c84bb4a8ba80c1ca2e1b0770e1372f22f3ac96f4fba61fd1038f2da28262b6
---
# Assignment-search limit returns 503

> On forward look, an assignment search exceeding the configured limit returns 503.

## Step 1 @verifies ac-19

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, use controlled {{search_limit_setup}} to exceed the assignment-search limit for divisionId={{division_id}}, marketCode={{market_code}} and productCode={{product_code}}; request GET with X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 503.
