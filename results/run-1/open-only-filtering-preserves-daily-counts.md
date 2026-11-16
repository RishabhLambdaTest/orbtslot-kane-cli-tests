---
test: ../../.testmuai/tests/open-only-filtering-preserves-daily-counts_test.md
status: passed
started: 2026-11-14T18:32:52.205Z
duration_s: 67
session_id: 52cbe876-e645-4047-9b08-0138b7433779
---

# Open-only filtering preserves daily counts — Result

## Step 1 ✓ passed (28.9s)
md5: d49a1bd579334b707e51f860aa18ceec
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate={{from_date}}, dayCount=12, onlyOpen=true and X-LP-User-Id={{lp_user_id}}, using the independent mixed open/non-open {{configured_slots_fixture}}.

## Step 2 ✓ passed (36s)
md5: 07301ff38464dd1f58a06c103d998fda
Compare the returned days to {{configured_slots_fixture}} and {{market_timezone}}, then assert each returned slot is configured and open, each day's openSlots equals the fixture's pre-filter open count, totalSlots equals its pre-filter full count, and each date is the corresponding market-local day.
