---
test: ../../.testmuai/tests/fourteen-day-forward-look-with-lead-stays-inside-requested_test.md
status: passed
started: 2026-11-14T18:45:21.979Z
duration_s: 55
session_id: c30be666-cb77-456a-b5f9-435636586d63
---

# Fourteen-day forward look with lead stays inside requested window — Result

## Step 1 ✓ passed (50.3s)
md5: 5cac8601cff46f4c8dc17d8e785b2b3a
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate={{from_date}}, dayCount=14, leadId={{lead_id}} and X-LP-User-Id={{lp_user_id}}; compare returned days to {{configured_slots_fixture}} in {{market_timezone}}, then assert at most 14 days are returned, every date falls from {{from_date}} through its thirteenth following market-local calendar day, and no returned day lacks configured slots.
