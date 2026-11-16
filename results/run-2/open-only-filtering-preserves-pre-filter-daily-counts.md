---
test: ../../.testmuai/tests/open-only-filtering-preserves-pre-filter-daily-counts_test.md
status: passed
started: 2026-11-14T18:46:51.423Z
duration_s: 68
session_id: d307f885-6858-44b6-b6bd-45605821036d
---

# Open-only filtering preserves pre-filter daily counts — Result

## Step 1 ✓ passed (65.6s)
md5: 111e5b270dd136f40b1d7f905511eefb
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate={{from_date}}, dayCount=12, onlyOpen=true and X-LP-User-Id={{lp_user_id}} using independent mixed open/non-open {{configured_slots_fixture}}; compare its market-local days and slots with {{market_timezone}} and the fixture, then assert each returned slot is configured and open, daily openSlots and totalSlots equal their pre-filter fixture counts, every date is in the twelve-day window starting {{from_date}}, and no day without configured slots appears.
