# Guided setup vs. current card: experiment plan

## Goal

Determine whether a guided onboarding experience helps more new tailnets reach a useful state than the current generic setup card.

The control shows the same three steps to everyone. The variant asks where the user’s resources are and what they want to set up first, then shows one relevant workflow. Required actions are presented as a numbered sequence, with installation options and admin-console actions available inside the flow. Each workflow explains what success looks like and includes an appropriate connection or capability check.

[View the guided setup variant](VARIANT_URL_PLACEHOLDER)

This experiment evaluates the guided experience as a complete package. It will not identify whether personalization, sequencing, embedded actions, confirmation guidance, or connection checks caused the result.

## Hypothesis

Some users fail to complete setup because they cannot tell which instructions apply to them or whether a step worked.

If onboarding selects instructions based on the intended use case, keeps required actions in the workflow, and gives users observable success criteria, then more new tailnets will connect at least two devices within seven days. The effect may be strongest for subnet-router and exit-node use cases, which the current generic instructions do not cover.

## Experiment design

- **Population:** New tailnets eligible for onboarding, excluding employee, test, automated, and previously activated tailnets.
- **Unit of assignment:** Tailnet, because setup affects the organization and multiple administrators may participate.
- **Assignment:** Randomize 50/50 at the first eligible card render and store the assignment on the tailnet.
- **Analysis:** Intention to treat, using every eligible assigned tailnet regardless of whether setup was completed.
- **Arms:** Current card versus complete guided experience. A picker-only test can follow if the guided experience succeeds.

## Measures

**Primary outcome:** Percentage of eligible new tailnets with at least two connected devices within seven days of assignment.

Before launch, define exactly what counts as connected. For example, decide whether authentication alone qualifies or whether the devices must establish a successful peer connection.

This gives both arms one comparable primary outcome, but it does not represent full completion for every goal. Use the goal-specific outcomes below to diagnose where the variant succeeds or fails.

**Secondary outcomes:**

- Time to second connected device, analyzed as a time-to-event outcome
- Percentage reaching three connected devices within 14 days
- Successful connection checks within seven days
- Completion of the selected use case, reported separately: subnet route approved and used, exit node selected and used, remote connection tested, internal resource reached, user invited, or device shared
- Variant progression by required action: viewed, started, completed, bypassed, or failed

**Guardrails:**

- First-device activation, if onboarding appears before the first connection
- Onboarding abandonment
- Installation errors
- Support contacts per eligible tailnet within 14 days

Week-four retention and paid conversion are useful follow-up measures, but they are unlikely to be sensitive enough for the initial launch decision.

## Sample and analysis

Using a placeholder 45% baseline, 80% power, a two-sided 5% significance level, and a 3 percentage point minimum detectable effect requires approximately 4,400 tailnets per arm, or 8,800 total. Replace the baseline and effect threshold with production data before committing to the test.

Report the absolute difference between arms with a 95% confidence interval. Check assignment balance and instrumentation quality before interpreting the result. Treat segmented and step-level findings as diagnostic unless the analysis plan accounts for multiple comparisons.

Instrumentation should capture assignment, card views and dismissals, selected location and goal, exit-node device type when applicable, download choice, required-action interactions, continuation with incomplete actions, connection-test results, and server-side device or capability activation.

## Before launch

Run five to eight moderated usability sessions with realistic setup scenarios, including participants with limited networking knowledge. Confirm that they can select the correct path, distinguish actions in the admin console from actions on another device, complete the instructions, recognize success, and recover from a failed connection test.

Also validate the event schema with an A/A test or equivalent instrumentation check before measuring treatment effects.

## Decision rule

Set these thresholds before launch:

- Minimum worthwhile improvement in two-device activation: `[X percentage points]`
- Maximum acceptable regression in first-device activation: `[Y percentage points]`
- Maximum acceptable increase in support contacts: `[Z per 1,000 tailnets]`

Ship when the primary result meets the worthwhile-effect threshold and no guardrail exceeds its limit. If activation improves but first-device setup declines, move the guided questions until after the first installation and retest. If failures concentrate in one step, revise that step before rejecting the overall approach.
