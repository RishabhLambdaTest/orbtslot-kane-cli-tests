---
assurance:
  id: t-24
  base: sha256:2fd8b4e6c8568fff112b397652811d1924ac5379b319ed022dac27984175be7d
---
# Unexpected internal error returns 500

> On forward look, an unexpected internal failure returns 500.

## Step 1 @verifies ac-20

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, use controlled {{internal_failure_setup}} to cause an unexpected failure for divisionId={{division_id}}, marketCode={{market_code}} and productCode={{product_code}}; request GET with X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 500.
