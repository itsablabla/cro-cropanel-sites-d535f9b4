# Lab TBT 1780ms on mobile — dev spec
Site: nomadinternet.com · Priority 5 · High · Effort: Medium (2-5 days)

## Problem
Script work freezes the main thread, so taps and scrolls go dead during load.

## Evidence (from the live site)
> Lighthouse (mobile emulation, single synthetic run via DataForSEO): Total Blocking Time 1,780 ms against a ‘good’ threshold of 200ms. Lab data, not real-user field data — confirms the defect class, not the field percentile.

## Current state
notes: Total Blocking Time 1,780 ms (lab, mobile)

## Required change
notes: Total Blocking Time ≤ 200ms (good)

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Total Blocking Time ≤ 200ms (good)
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_lab_tbt_1780ms_on_mobile` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
