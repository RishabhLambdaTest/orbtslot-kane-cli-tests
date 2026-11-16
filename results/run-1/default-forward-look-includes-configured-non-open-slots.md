---
test: ../../.testmuai/tests/default-forward-look-includes-configured-non-open-slots_test.md
status: failed
started: 2026-11-14T18:32:47.612Z
duration_s: 71
session_id: 25581b0e-6c3f-494b-8696-dd56b4755d6a
---

# Default forward look includes configured non-open slots — Result

## Step 1 ✓ passed (29.8s)
md5: ed8f078585c97fe84815d4d13feee208
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, omitting fromDate, dayCount, onlyOpen and leadId.

## Step 2 ✗ failed (36.5s)
md5: 6be6e86d262a4c9c7ece6479bde6eb3d
Reason: Final verification failed: "Compared to {{global.configured_slots_fixture}} and the current {{global.market_timezone}} calendar date, there are 12 market-local days, the known configured non-open slot appears, every returned slot is configured, and daily openSlots and totalSlots equal independent pre-filter fixture counts." — bug verdict: Availability fixture assertion does not match the verification result [automation_bug/test_data_issue, confidence 0.72]
Compare the result to {{configured_slots_fixture}} and the current {{market_timezone}} calendar date, then assert there are 12 market-local days, the known configured non-open slot appears, every returned slot is configured, and daily openSlots and totalSlots equal independent pre-filter fixture counts.
