# Competing CTAs split funnel — dev spec
Site: nomadinternet.com · Priority 2 · High · Effort: Medium (2-5 days)

## Problem
Multiple competing CTAs on the homepage create ambiguity about the primary conversion path, diluting user focus.

## Evidence (from the live site)
> 7 distinct calls to action compete on the same page: “CHECK COVERAGE”, “CHECK IF IT WORKS AT MY ADDRESS”, “SEE MY OPTIONS”, “GET STARTED”, “START CHAT”, “SEE WHAT I QUALIFY FOR”, “CHECK MY COVERAGE”.

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Multiple CTAs present, including CHECK COVERAGE, CHECK IF IT WORKS AT MY ADDRESS, SEE MY OPTIONS, GET STARTED, START CHAT, SEE WHAT I QUALIFY FOR, CHECK MY COVERAGE.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Consolidate to a single primary CTA (CHECK COVERAGE) and demote secondary CTAs to text links or secondary button style.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate to a single primary CTA (CHECK COVERAGE) and demote secondary CTAs to text links or secondary button style.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_competing_ctas_split_funnel` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
