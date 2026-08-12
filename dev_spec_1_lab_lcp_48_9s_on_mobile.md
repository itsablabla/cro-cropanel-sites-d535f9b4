# Lab LCP 48.9s on mobile — dev spec
Site: nomadinternet.com · Priority 1 · Urgent · Effort: Medium (2-5 days)

## Problem
The page's main content takes 48.9 seconds to appear on a mid-range phone, causing most visitors to bounce before they can convert.

## Evidence (from the live site)
> Lighthouse (mobile emulation, single synthetic run via DataForSEO): Largest Contentful Paint 48.9 s against a ‘good’ threshold of 2500ms. Lab data, not real-user field data — confirms the defect class, not the field percentile.

## Current state
notes: Largest Contentful Paint 48.9 s (lab, mobile)

## Required change
notes: Largest Contentful Paint ≤ 2500ms (good)

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Largest Contentful Paint ≤ 2500ms (good)
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_lab_lcp_48_9s_on_mobile` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
