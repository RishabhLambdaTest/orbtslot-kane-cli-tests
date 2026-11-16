---
test: ../../.testmuai/tests/fourteen-day-forward-look-with-lead_test.md
status: failed
started: 2026-11-14T18:32:51.823Z
duration_s: 46
session_id: 442447c0-e97f-4f75-9a7f-53f9a0af855f
---

# Fourteen-day forward look with lead — Result

## Step 1 ✗ failed (43.8s)
md5: 02a062e62d6db1741cd6ff35d2b08660
Reason: Final verification failed: "the response contains 14 days on the {{global.market_timezone}} calendar" — bug verdict: Availability request was not issued before response assertion [automation_bug/agent_misstep, confidence 0.96]
At https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look, request GET with divisionId={{division_id}}, marketCode={{market_code}}, productCode={{product_code}}, fromDate={{from_date}}, dayCount=14, leadId={{lead_id}} and X-LP-User-Id={{lp_user_id}}, then assert the response contains 14 days on the {{market_timezone}} calendar.
