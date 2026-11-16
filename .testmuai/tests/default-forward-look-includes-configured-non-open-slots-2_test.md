---
assurance:
  id: t-11
  base: sha256:53469b18961efce291b66cde54abdc11fd104d20502a2b5b4af3701bd020a783
---
# Default forward look includes configured non-open slots within twelve-day window

> Successful request without fromDate, dayCount, onlyOpen or leadId returns configured days within the default 12-day market-local unfiltered look, omitting days with no configured slots.

## Step 1 @verifies ac-21, ac-24, ac-25, ac-8, ac-1, ac-2, ac-3, ac-4

At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}} and X-LP-User-Id={{lp_user_id}}, omitting fromDate, dayCount, onlyOpen and leadId; compare the response against {{configured_slots_fixture}} and the current {{market_timezone}} date, then assert at most 12 days are returned, each returned day falls from the effective market-local fromDate through its eleventh following calendar day, no day without configured slots appears, the fixture's known configured non-open slot appears, every returned slot is configured, and each day's openSlots and totalSlots equal the fixture's pre-filter counts.
