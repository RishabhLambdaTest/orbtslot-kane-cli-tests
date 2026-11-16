---
assurance:
  id: t-14
  base: sha256:d8556e8d27abc79018e63b1659cd6c675fee2f24adf51ef05610908203a0d8ed
---
# Open-only filtering preserves pre-filter daily counts

> On forward look, a known mixed open/nonopen fixture shows onlyOpen excludes nonopen entries while daily totals still count them.

## Step 1 @verifies ac-6, ac-1, ac-2, ac-3, ac-4, ac-24, ac-25

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate={{from_date}}, dayCount=12, onlyOpen=true and X-LP-User-Id={{lp_user_id}} using independent mixed open/non-open {{configured_slots_fixture}}; compare its market-local days and slots with {{market_timezone}} and the fixture, then assert each returned slot is configured and open, daily openSlots and totalSlots equal their pre-filter fixture counts, every date is in the twelve-day window starting {{from_date}}, and no day without configured slots appears.
