---
assurance:
  id: t-15
  base: sha256:fb3948668158f64c4e9ed88a3076a6f2d1ae4ad8c5536367f56b87e592ab0cd5
---
# Malformed market and product codes each return 400

> On forward look, each missing, space-containing or 21-letter required code independently returns 400.

## Step 1 @verifies ac-13

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode="AB CD", productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, encoding the space as a query value, then assert HTTP status equals 400.

## Step 2 @verifies ac-13

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode="AB CD" and X-LP-User-Id={{lp_user_id}}, encoding the space as a query value, then assert HTTP status equals 400.

## Step 3 @verifies ac-13

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode=ABCDEFGHIJKLMNOPQRSTU, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.

## Step 4 @verifies ac-13

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode=ABCDEFGHIJKLMNOPQRSTU and X-LP-User-Id={{lp_user_id}}, then assert HTTP status equals 400.

## Step 5 @verifies ac-13

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, omitting marketCode, then assert HTTP status equals 400.

## Step 6 @verifies ac-13

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}} and X-LP-User-Id={{lp_user_id}}, omitting productCode, then assert HTTP status equals 400.
