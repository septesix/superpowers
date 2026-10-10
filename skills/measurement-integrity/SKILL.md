---
name: measurement-integrity
description: Use when quoting any number, count, pass rate, or coverage figure — especially from a script, regex, or query you wrote in this same session — and when setting a threshold from measurements. A green result that graded nothing, or graded the wrong thing, is the most expensive kind of false report.
---

# Measurement Integrity

## Overview

Verification-before-completion says: run the command. This skill asks what it **graded**. Most measurement errors are not errors about the world — they are counts of something else: the checker instead of the checked, absent input instead of clean output, last version's evidence describing today's code.

**REQUIRED BACKGROUND:** superpowers:verification-before-completion

## The Gate Function

Before quoting any number, answer all four, in writing:

1. **How many artifacts did it grade?** Report `N graded of M (K ungradeable: reason)`. Zero graded is **untested** — never a pass.
2. **What kind of check was each?** Behaviour (something did it) | instrument (my tool can detect a violation) | prose (a sentence exists). Never sum them into one headline.
3. **Did I write the tool this session?** Then the number is a hypothesis until you hand-read one raw artifact that must pass and one known-bad that must fail. Synthetic fixtures only prove what you assumed about the data.
4. **Does the evidence carry the version it describes?** If the contract changed since, it is untested, not green.

## Common Failures

| Claim | Requires | Not sufficient |
|-------|----------|----------------|
| "168 checks pass" | Split by kind; N graded of M | One summed integer |
| "The scan found 3" | One hit and one clean file, read raw | Output of your hour-old script |
| "Coverage is fine" | The input the rule needs existed in what ran | No observable trace of it |
| "It failed" vs "it crashed" | Distinct exit channel per state | Any nonzero code |
| "We tested this" | Evidence from the current version | Evidence that exists |

## Setting a Threshold

No limit ships from fewer than 5 measurements; quote the distribution (n, median, max). **Cap the shape, not the sum** — a total is a quota, and quotas are met by spreading the same bulk thinner. When a threshold fails on the next ordinary sample, the quantity measured was wrong, not the number.

## Red Flags - STOP

- An aggregate count you have never decomposed
- Your own script's output as evidence about the world
- "No findings" from a check that received nothing
- A number you cannot reproduce with one command
- Editing guidance to fix a number, before checking the ruler
- Repeating a measurement instead of widening it

## Rationalization Prevention

| Excuse | Reality |
|--------|---------|
| "The suite is green" | What did it grade, and how many times? |
| "I ran it five times" | Five runs of one shape, or five shapes? |
| "The script reported it" | You wrote the script. Open a raw file. |
| "Nothing flagged" | Absence of detection ≠ absence of defect |
| "It passed last week" | Last week's artifact describes last week's code |
| "The cap failed once, raise it" | Measure 5, then choose — often the sum is the wrong cap |
