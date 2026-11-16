# ORBT Slot Forward Look API: tests generated with kane-cli

This repository contains everything used to generate and run automated API tests for the ORBT Slot **Forward Look** endpoint with **kane-cli**:

```
GET https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net/api/v1/availability/forward-look
```

It contains the inputs kane-cli was given, the tests it generated, the test data, and the results of both runs. You can use it in two ways:

- **Read it:** see what kane-cli produced and how the tests went. No setup needed.
- **Run it yourself:** follow the step-by-step guide below. No terminal experience is assumed.

---

## Contents

1. [What's in this repository](#whats-in-this-repository)
2. [What happened](#what-happened)
3. [The tests](#the-tests)
4. [One-time setup](#one-time-setup)
5. [Option 1: Re-run the tests in this repository](#option-1-re-run-the-tests-in-this-repository)
6. [Option 2: Generate your own tests from the inputs](#option-2-generate-your-own-tests-from-the-inputs)
7. [Test data (variables)](#test-data-variables)
8. [Looking at results and evidence](#looking-at-results-and-evidence)
9. [Troubleshooting](#troubleshooting)
10. [Glossary](#glossary)

---

## What's in this repository

```
orbtslot-kane-cli-tests/
├── README.md                      this guide
├── inputs/
│   ├── orbtslot-swagger.json      the OpenAPI (Swagger) spec, downloaded from /v3/api-docs
│   └── API.txt                    the Swagger links and the sample curl request
├── .testmuai/                     kane-cli's working folder (hidden, see note below)
│   ├── tests/                     the 14 tests kane-cli generated, one file each
│   └── variables/
│       └── assurance.json         the test data the tests use
└── results/
    ├── run-1/                     results of the first run (7 tests)
    └── run-2/                     results of the second run (11 tests)
```

**About the hidden folder:** folders whose names start with a dot, like `.testmuai`, are hidden in Finder by default. To show them, open the repository folder in Finder and press **Cmd + Shift + .** (Command, Shift and the full stop together). Press it again to hide them. On GitHub they're always visible.

Every file in this repository is plain text. You can open any of them in TextEdit, VS Code or on GitHub.

---

## What happened

kane-cli was given only the two files in `inputs/`: the Swagger spec and the sample curl request. Nothing else was written by hand.

| Step | What kane-cli did | Result |
|---|---|---|
| 1. Read the inputs | Found the use cases described in the spec, including **"Find product-bookable times across dates"**, which is the Forward Look endpoint | Use cases with citations to the exact spec lines |
| 2. Design | For that use case, wrote acceptance criteria, scenarios and one test per scenario | Runnable test files in `.testmuai/tests/` |
| 3. Run 1 | Ran the first 7 tests against the dev API | **4 passed, 3 failed** |
| 4. Fix | kane-cli's own analysis showed the 3 failures were test-design issues, not API defects. One `kane-cli maintain evolve` command redesigned the affected tests and added 4 more | Updated and new tests |
| 5. Run 2 | Ran the 11 runnable tests | **11 passed, 0 failed** |

**Why run 1 had failures:**

| Test | What went wrong | How it was fixed |
|---|---|---|
| Default forward look (12 days) | It expected exactly 12 days of slots, but the dev environment only had slots up to 24 Nov | Redesigned to accept "at most 12 days", with no day outside the window |
| Fourteen-day forward look with lead | It checked the response before sending the request | Redesigned; passed in run 2 |
| Malformed codes return 400 | It sent only the first of several invalid values | Split so each invalid value is sent and checked |

Full details for every test are in `results/run-1/` and `results/run-2/`.

---

## The tests

All 14 tests are in `.testmuai/tests/`. Each file is written in plain English: kane-cli reads the sentences and carries them out.

| Test file | What it checks | Run 2 |
|---|---|---|
| `default-forward-look-includes-configured-non-open-slots-2_test.md` | Default request returns at most 12 market-local days, includes full slots, and the daily counts match | Passed |
| `fourteen-day-forward-look-with-lead-stays-inside-requested_test.md` | `dayCount=14` with a `leadId` stays inside the 14-day window | Passed |
| `one-day-forward-look-allows-an-unconfigured-date-to-be_test.md` | `dayCount=1` works, and a date with no slots is left out | Passed |
| `open-only-filtering-preserves-pre-filter-daily-counts_test.md` | `onlyOpen=true` returns only open slots and keeps the daily counts | Passed |
| `invalid-day-counts-each-return-400_test.md` | `dayCount` of 0, 15 and other invalid values each return 400 | Passed |
| `invalid-date-and-lead-id-each-return-400_test.md` | A malformed `fromDate` and an invalid `leadId` each return 400 | Passed |
| `malformed-market-and-product-codes-each-return-400_test.md` | Badly formatted `marketCode` and `productCode` values each return 400 | Passed |
| `out-of-range-division-ids-each-return-400_test.md` | `divisionId` outside 1–32767 returns 400 | Passed |
| `unmapped-requested-product-returns-400_test.md` | A product that isn't mapped to the division returns 400 | Passed |
| `unknown-division-returns-404_test.md` | An unknown division returns 404 | Passed |
| `unknown-market-returns-404-for-known-division_test.md` | An unknown market in a known division returns 404 | Passed |
| `unavailable-required-input-returns-503-2_test.md` | Returns 503 when a required input is unavailable | Not run (see below) |
| `assignment-search-limit-returns-503-2_test.md` | Returns 503 when the assignment search limit is exceeded | Not run (see below) |
| `unexpected-internal-error-returns-500-2_test.md` | Returns 500 on an unexpected internal error | Not run (see below) |

**The last three tests need a special environment.** They check how the API behaves during an outage or internal error, which can't be triggered on demand on the dev environment. They stay in the suite for completeness and will fail until someone provides a way to simulate those failures (see [Test data](#test-data-variables)).

---

## One-time setup

You only need to do this once per computer. It takes about 10 minutes.

### 1. Open Terminal

On a Mac, press **Cmd + Space**, type **Terminal**, and press **Return**. A window with a text prompt opens. You'll paste commands into it.

**How to run a command:** copy one command from a grey box below, paste it into Terminal with **Cmd + V**, and press **Return**. Wait for it to finish (the prompt comes back) before pasting the next one. Run the commands one box at a time.

### 2. Install Node.js

kane-cli is installed with Node.js. Download the **LTS** installer from [nodejs.org](https://nodejs.org) and run it like any Mac installer.

Check it worked:

```
node --version
```

You should see a version number such as `v22.x.x`.

### 3. Install kane-cli

```
npm install -g @testmuai/kane-cli
```

If you see a "permission denied" error, run this instead. It will ask for your Mac password; nothing appears on screen while you type it, which is normal.

```
sudo npm install -g @testmuai/kane-cli
```

Check it worked:

```
kane-cli --version
```

### 4. Sign in

```
kane-cli login
```

Follow the prompts. It signs you in to your TestMu AI account and asks which **project** and **folder** in Test Manager your results should go to.

### 5. Google Chrome

kane-cli runs its steps through Google Chrome. If it isn't installed, get it from [google.com/chrome](https://www.google.com/chrome/).

### 6. Get this repository

**The easy way:** on the GitHub page for this repository, click the green **Code** button, then **Download ZIP**. Double-click the ZIP in your Downloads folder to unpack it.

Then move Terminal into the folder:

```
cd ~/Downloads/orbtslot-kane-cli-tests-main
```

**If you use git:**

```
git clone https://github.com/RishabhLambdaTest/orbtslot-kane-cli-tests.git
```

```
cd orbtslot-kane-cli-tests
```

To check you're in the right place, run `ls`. You should see `README.md`, `inputs` and `results`.

---

## Option 1: Re-run the tests in this repository

This runs the 14 tests in `.testmuai/tests/` against the dev API.

### Step 1: Update the date

One test uses a fixed date, `from_date`. It must be a date the dev environment has slots for, usually today or later. Open the test data file:

```
open -e .testmuai/variables/assurance.json
```

It opens in TextEdit. Find this block:

```
"from_date": {
    "value": "2026-11-14",
```

Change `2026-11-14` to today's date in the same `YYYY-MM-DD` format, keeping the quotes. Save with **Cmd + S** and close TextEdit.

### Step 2: Check everything without running

```
kane-cli testrun run .testmuai/tests/*_test.md --override-start-url https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net --dry-run
```

This lists the 14 tests and checks the test data without sending any requests. A warning that **3 variables have no value** is expected: those are the three outage/500 tests.

### Step 3: Run the tests

```
kane-cli testrun run .testmuai/tests/*_test.md --override-start-url https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net
```

- A Chrome window opens and kane-cli works through each test. You don't need to touch it.
- It takes about **10–15 minutes**. Each test takes 30–200 seconds.
- When it finishes, Terminal shows a results table. Press **q** to close it and get the prompt back.

**Expected result:** 11 passed and 3 failed (the three outage/500 tests).

To run tests faster, add `--parallel 3` to the end of the command. That runs three at a time, at the same cost.

### Run a single test

```
kane-cli testmd run .testmuai/tests/unknown-division-returns-404_test.md --url https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net
```

Replace the file name with any test from the table above.

---

## Option 2: Generate your own tests from the inputs

This repeats what we did, starting from just the Swagger spec and the curl request. kane-cli writes the tests itself, so your tests may be worded differently from ours. They should cover the same ground.

### Step 1: Make a new, empty folder and copy the inputs into it

```
mkdir ~/orbtslot-my-tests
```

```
cp inputs/orbtslot-swagger.json inputs/API.txt ~/orbtslot-my-tests/
```

```
cd ~/orbtslot-my-tests
```

### Step 2: Let kane-cli read the inputs

```
kane-cli context ingest orbtslot-swagger.json API.txt
```

- It asks **"where should this folder's work go?"**. Choose **work locally**.
- It reads the spec and lists the **use cases** it found, each with a short ID such as `UC-7`.
- It may ask a few questions where the spec isn't clear. If unsure, pick the option marked **recommended**.
- When asked "Anything to add or change?", type **looks good** and press Return. Then choose **finish**.

Note the ID of the use case called **"Find product-bookable times across dates"**. That's the Forward Look endpoint. You can list them again at any time:

```
kane-cli context list
```

### Step 3: Generate the tests

Replace `uc-7` with your ID if it's different:

```
kane-cli design tests --use-case uc-7
```

kane-cli writes acceptance criteria, then scenarios, then one test per scenario, pausing between stages. At each pause choose **continue**. If it asks about a limit on the number of tests, choose **No limit**.

At the end it lists the **variables** (test data) the tests need, and saves the test files in `.testmuai/tests/`.

### Step 4: Fill in the test data

```
open -e .testmuai/variables/assurance.json
```

Fill in each `"value": ""` using the [test data table](#test-data-variables) below. Your variable names may differ slightly from ours; match them by their description. Save and close.

### Step 5: Check, then run

```
kane-cli testrun run .testmuai/tests/*_test.md --override-start-url https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net --dry-run
```

```
kane-cli testrun run .testmuai/tests/*_test.md --override-start-url https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net
```

### Step 6: If some tests fail because of how they were written

kane-cli explains every failure. If it says a failure is a **test issue** (for example "agent misstep" or "test data issue") rather than an API problem, let kane-cli redesign the affected tests:

```
kane-cli maintain evolve uc-7
```

It shows what it will change and asks before going ahead. Then run Step 5 again. This is exactly how run 1 (4 of 7) became run 2 (11 of 11).

**Don't edit the test files by hand.** kane-cli tracks each test against its requirements, and a manual edit is treated as a new version of the design. Use `maintain evolve` instead.

---

## Test data (variables)

The tests read their data from `.testmuai/variables/assurance.json`, so the same test can run against different data or environments without changing the test.

| Variable | Value used | What it is |
|---|---|---|
| `lp_user_id` | `12345` | Any positive number. Sent as the required `X-LP-User-Id` header. |
| `division_id` | `3` | A division that has seeded slots on dev |
| `market_code` | `BMT` | A market in that division |
| `product_code` | `KITCHEN` | A product mapped to that division and market |
| `from_date` | today, e.g. `2026-11-20` | A date with slots on dev. **Update before each run.** |
| `market_timezone` | `America/Chicago` | The time zone of the BMT market |
| `lead_id` | `1` | Any positive lead ID |
| `configured_slots_fixture` | `divisionId=3, marketCode=BMT, productCode=KITCHEN; use the onlyOpen=false response as the reference` | Tells the test where to read the expected slots from |
| `unmapped_product_code` | `ROOFING` | A product that is **not** mapped to division 3 |
| `unknown_market_code` | `ZZZ` | A market code that doesn't exist |
| `unknown_division_id` | `99` | A division number that doesn't exist |
| `required_input_outage_setup` | empty | Needed only for the 503 tests: a way to make a required input unavailable |
| `search_limit_setup` | empty | Needed only for the 503 tests: a way to exceed the assignment search limit |
| `internal_failure_setup` | empty | Needed only for the 500 test: a way to cause an internal error |
| `api_token` | `sample-token-do-not-use` | An example of a **secret**, not used by this API. Values marked `"secret": true` are hidden in logs and reports. |

**Keep slots seeded on dev.** Several tests need slots to exist for the chosen division, market and product over the coming 14 days. If the seed data runs out, those tests fail even though the API is fine. Pick a `division_id`, `market_code` and `product_code` that currently have slots, and set `from_date` to a date inside that window.

**Secrets:** never put real passwords or tokens in this file if you share it. Mark them `"secret": true` and keep the real values out of version control.

---

## Looking at results and evidence

### Test Manager (web)

Every run uploads to **TestMu Test Manager** in the project and folder you picked when you signed in. Open Test Manager in your browser to see each test with its steps, requests and responses. When a single test finishes, Terminal also prints a **ShareLink** you can send to anyone; it works without a login for 7 days.

### Evidence packs (on your computer)

Each run also saves a sealed **evidence pack**, a single `.evidence` file with every request, response and step result, in `.testmuai/evidence/`. To view one in your browser:

```
kane-cli evidence serve .testmuai/evidence/<file-name>.evidence
```

Terminal prints a `viewer` link. Cmd-click it to open it. The viewer reads the file from your computer; nothing is uploaded. Press **Ctrl + C** in Terminal to stop it when you're done.

To share evidence with someone, send them the `.evidence` file. They can open it the same way.

### Result files

After each run, kane-cli writes a short summary per test next to the tests, in folders named `output-<test name>/Result.md`. The `results/` folder in this repository holds copies of those summaries from our two runs.

---

## Troubleshooting

| What you see | What to do |
|---|---|
| `command not found: kane-cli` | Install it ([setup step 3](#3-install-kane-cli)), then close Terminal and open a new window |
| `command not found: npm` or `node` | Install Node.js ([setup step 2](#2-install-nodejs)), then open a new Terminal window |
| `No start URL provided` | Add `--url https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net` (for `testmd run`) or `--override-start-url https://app-orbtslot-dev-use2-fydm-api.azurewebsites.net` (for `testrun run`) |
| `unknown option '--url'` | You used `--url` with `testrun run`. Use `--override-start-url` instead |
| `not a *_test.md file: .testmuai/tests/` | Point at the files, not the folder: `.testmuai/tests/*_test.md` |
| `file not found` for a test | The tests are in the hidden `.testmuai/tests/` folder. Include that in the path |
| A warning that some variables have no value | Fill them in `.testmuai/variables/assurance.json`. An empty value is sent as the literal placeholder text, so the test will fail |
| A test expecting slots fails | Dev may have no slots for your date. Set `from_date` to today, or pick a division/market/product with slots |
| The results table won't go away | Press **q** |
| You're not signed in, or the wrong project | Run `kane-cli login` again |
| `dquote>` appears and nothing runs | A quote mark was left open. Press **Ctrl + C** and paste the command again |

---

## Glossary

| Term | Meaning |
|---|---|
| **Use case** | A goal someone has with the API, e.g. "Find product-bookable times across dates". kane-cli finds these in your spec. |
| **Acceptance criterion** | One promise the API must keep, e.g. "dayCount of 15 returns 400". Each cites the spec line it came from. |
| **Scenario** | A concrete situation that exercises one or more criteria: a happy path, a boundary, an error case. |
| **Test** | A runnable file (`*_test.md`) that carries out one scenario and checks the criteria. |
| **Gap** | Something kane-cli couldn't turn into a test, such as missing test data or behaviour the spec doesn't define. It records these instead of guessing. |
| **Variable** | A named piece of test data, e.g. `{{division_id}}`, filled in from `assurance.json`. |
| **Evidence pack** | A sealed `.evidence` file containing everything that happened in a run. |
| **Test Manager** | TestMu AI's web dashboard, where every run is uploaded. |

---

*Generated with kane-cli 0.10.4 against the ORBT Slot dev API on 14 Nov 2026.*
