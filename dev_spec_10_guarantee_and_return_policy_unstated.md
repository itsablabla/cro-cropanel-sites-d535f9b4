# Guarantee and return policy unstated — dev spec
Site: nomadinternet.com · Priority 10 · Medium · Effort: Medium (2-5 days)

## Problem
No page digest text mentions a money-back guarantee, return window, or satisfaction promise, despite the site selling hardware and monthly plans, which is notable given the one-time equipment fees shown.

## Evidence (from the live site)
> Prices shown on the page: $99.95 /month $129.95 /month $99.95/Mo $99.95 /month $129.95 /month $99.95
> A section heading reads “$0.00 (one-time)”.
> A section heading reads “$99.99 (one-time)”.

## Current state
notes: No mention of guarantee or return policy.

## Required change
notes: Add an explicit guarantee or return policy statement near pricing and the coverage form.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add an explicit guarantee or return policy statement near pricing and the coverage form.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_guarantee_and_return_policy_unstated` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
