# Benefit claims lack specifics — dev spec
Site: nomadinternet.com · Priority 7 · Medium · Effort: Low (0.5-2 days)

## Problem
The copy repeatedly says the internet is fast and reliable but does not state concrete advantages over alternatives, such as no contracts, no data caps, or coverage in areas where cable is unavailable.

## Evidence (from the live site)
> The Fastest Rural & On-the-Go Internet in the USA
> Join America's Largest Wireless Internet Provider Featuring

## Current state
notes: Generic superlatives without specific differentiators.

## Required change
notes: Replace generic superlatives with specific, verifiable differentiators (e.g., no annual contract, unlimited data, works where cable does not reach).

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Replace generic superlatives with specific, verifiable differentiators (e.g., no annual contract, unlimited data, works where cable does not reach).
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_benefit_claims_lack_specifics` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
