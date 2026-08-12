# Duplicate pricing creates confusion — dev spec
Site: nomadinternet.com · Priority 8 · High · Effort: Low (0.5-2 days)

## Problem
The plans pages show the same price points repeated as both monthly and one-time fees, making it hard for visitors to predict what they will actually pay.

## Evidence (from the live site)
> A section heading reads “$99.95 /month”.
> A section heading reads “$129.95 /month”.
> A section heading reads “$0.00 (one-time)”.
> A section heading reads “$99.99 (one-time)”.

## Current state
notes: Prices appear as both monthly and one-time fees without clear labeling.

## Required change
notes: Clearly label each price with its billing cycle and one-time vs recurring nature, and separate monthly plans from equipment fees visually.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Clearly label each price with its billing cycle and one-time vs recurring nature, and separate monthly plans from equipment fees visually.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_pricing_creates_confusion` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
