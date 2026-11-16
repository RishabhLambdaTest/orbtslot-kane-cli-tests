---
assurance:
  id: t-12
  base: sha256:77ede68d1e38da1d8b1fc2f05514d24d6754010dc7dd67070102445c4ffc9cc5
---
# Fourteen-day forward look with lead stays inside requested window

> dayCount=14 with positive optional leadId returns only configured days within the fourteen-day market-local window without changing assignments.

## Step 1 @verifies ac-22, ac-24, ac-25, ac-4

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate={{from_date}}, dayCount=14, leadId={{lead_id}} and X-LP-User-Id={{lp_user_id}}; compare returned days to {{configured_slots_fixture}} in {{market_timezone}}, then assert at most 14 days are returned, every date falls from {{from_date}} through its thirteenth following market-local calendar day, and no returned day lacks configured slots.
