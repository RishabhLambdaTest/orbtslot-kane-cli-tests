---
test: ../../.testmuai/tests/one-day-forward-look-allows-an-unconfigured-date-to-be_test.md
status: passed
started: 2026-11-14T18:46:43.372Z
duration_s: 143
session_id: 07af903b-4136-4d65-95eb-b59b2be91e32
---

# One-day forward look allows an unconfigured date to be absent — Result

## Step 1 ✓ passed (140.3s)
md5: 9fe484fdc47b25233a25f28c3a805558
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate={{from_date}}, dayCount=1 and X-LP-User-Id={{lp_user_id}}; compare the result with {{configured_slots_fixture}} in {{market_timezone}}, then assert at most one day is returned, every returned date equals {{from_date}} on the requested market calendar, and a day without configured slots is absent.
