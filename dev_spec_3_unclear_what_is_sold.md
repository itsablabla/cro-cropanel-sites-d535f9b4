# Unclear what is sold — dev spec
Site: nomadinternet.com · Priority 3 · High · Effort: Low (0.5-2 days)

## Problem
The homepage headline promises internet that works anywhere but never states what the product actually is (a wireless router plus monthly service) before the visitor commits to a coverage check.

## Evidence (from the live site)
> Reliable Internet That Works Anywhere in the U.S.
> CHECK COVERAGE
> Internet That Just Works

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: No mention of what the product is (wireless router + monthly service).

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Add a one-line descriptor above the fold stating the offer is a wireless router plus a monthly unlimited data plan.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a one-line descriptor above the fold stating the offer is a wireless router plus a monthly unlimited data plan.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_unclear_what_is_sold` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
