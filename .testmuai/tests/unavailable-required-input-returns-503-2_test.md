---
assurance:
  id: t-22
  base: sha256:ef8e4cc64a67058c37b1edfdc03cb717d47944f5b6e2af1b9f877750c717bc5d
---
# Unavailable required input returns 503

> On forward look, unavailable required inputs return 503 rather than calculated results.

## Step 1 @verifies ac-18

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, use controlled {{required_input_outage_setup}} to make required input unavailable for divisionId={{division_id}}, marketCode={{market_code}} and productCode={{product_code}}; request GET with X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 503.
