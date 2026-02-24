# AUsenseR-mc_multiple-randomization
This repository contains a small JavaScript snippet for AUsenseR / formr that randomises the **display order** of answer options in `mc_multiple` items.

It is **opt-in**: only items explicitly marked in the survey sheet are affected.

## What this solves

formr does not provide a built-in way to randomise the order of answer options inside `mc_multiple` (and similar multiple choice widgets). This script:

- randomises answer options **within** a question
- keeps selected options **last**
- preserves saved values (it only reorders existing DOM nodes)

## Usage

### 1) Survey sheet: opt-in with `mc_multiple_rand`

In your survey spreadsheet, add `mc_multiple_rand` to the `class` column **only for items you want randomised**.

Example:

| class | type | name |
|------|------|------|
**mc_multiple_rand** | mc_multiple | q1

`mc_multiple` questions without `mc_multiple_rand` defined in class keeps original order defined in choices (choice1, choice2).

### 2) Survey sheet: keep specific options last (optional)

Add one or more `last__...` tokens in the `class` column. Please note that it uses double underscore (__)

- spaces in the choices to keep last must be written as underscores
- use ASCII only (`aa`, `oe`, `ae`) for now

Examples:

Keep one option fixed as last:
`mc_multiple_rand last__ingen_af_ovenstaaende`

Keep two options fixed as last (order respected):
`mc_multiple_rand last__ingen_af_ovenstaaende last__alle`

Randomise everything (no fixed last options):
`mc_multiple_rand`

### 3) Run: paste the JavaScript in settings

Navigate to your run in AUsenseR/formr and paste the JavaScript:  
`Runs → [The run] → Configuration: Settings → JS`
