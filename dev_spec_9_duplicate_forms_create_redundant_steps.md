# Duplicate forms create redundant steps — dev spec
Site: nomadinternet.com · Priority 9 · Medium · Effort: Low (0.5-2 days)

## Problem
Two separate coverage-check forms with identical CONTINUE buttons on the same page force users to choose between redundant paths, creating uncertainty and friction.

## Evidence (from the live site)
> Duplicate coverage forms on page: The homepage and plans pages each carry two separate coverage-check forms with identical CONTINUE submit buttons.

## Current state
cta: CONTINUE; notes: Two separate coverage-check forms with identical CONTINUE buttons on the same page.

## Required change
cta: CONTINUE; notes: Consolidate the two coverage-check forms into a single, clearly labeled form per page.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate the two coverage-check forms into a single, clearly labeled form per page.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_forms_create_redundant_steps` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
