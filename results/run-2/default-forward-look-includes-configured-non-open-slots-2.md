---
test: ../../.testmuai/tests/default-forward-look-includes-configured-non-open-slots-2_test.md
status: passed
started: 2026-11-14T18:45:21.842Z
duration_s: 64
session_id: 416075d9-c22a-4730-bc6e-ead25b2dd2db
---

# Default forward look includes configured non-open slots within twelve-day window — Result

## Step 1 ✓ passed (59s)
md5: c904dbba84785c92cd0aaf08c9fb618a
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, omitting fromDate, dayCount, onlyOpen and leadId; compare the response against {{configured_slots_fixture}} and the current {{market_timezone}} date, then assert at most 12 days are returned, each returned day falls from the effective market-local fromDate through its eleventh following calendar day, no day without configured slots appears, the fixture's known configured non-open slot appears, every returned slot is configured, and each day's openSlots and totalSlots equal the fixture's pre-filter counts.
