---
assurance:
  id: t-13
  base: sha256:8f1b7edd0e50c474644c5eebeb1293309d561446af388830382645e055c5d15e
---
# One-day forward look allows an unconfigured date to be absent

> dayCount=1 returns at most one configured day within the one-day market-local window; a day with no configured slots may be omitted.

## Step 1 @verifies ac-23, ac-24, ac-25, ac-4

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate={{from_date}}, dayCount=1 and X-LP-User-Id={{lp_user_id}}; compare the result with {{configured_slots_fixture}} in {{market_timezone}}, then assert at most one day is returned, every returned date equals {{from_date}} on the requested market calendar, and a day without configured slots is absent.
