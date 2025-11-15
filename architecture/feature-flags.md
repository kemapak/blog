# Feature Flags

Feature flags are a core part of modern development workflows. They enable controlled feature testing, safer releases, 
progressive rollouts, and operational throttling. While extremely powerful, feature flags also introduce complexity. 
When not properly governed, they accumulate, lead to code bloat, create unexpected behavior, and make code maintenance 
significantly harder.

To prevent feature flags from becoming a long-term liability, teams must follow consistent processes, enforce strict 
naming conventions, and ensure ongoing cleanup.

Below are recommended guidelines for managing feature flags effectively and safely.

## General Guidelines
1. **Set a removal timeframe the moment you add a feature flag**. 
Every flag should have a clear expiration date aligned with the intended rollout or experiment lifecycle.

2. **Avoid nested feature flags**.
Stacking flags inside other flags increases complexity and makes code behavior unpredictable.

3. **Use a strict naming convention and enforce it**.
Standardized naming helps identify flags, group them, and track which ones should be removed.

## Naming Conventions

Every feature flag must follow a clear, descriptive, and structured naming format. This helps with discoverability, 
categorization, and cleanup processes.

**Flag name structure**: `fflag-<meta>-<feature/purpose>`

- Prefix all feature flag names with **fflag**.
- Use hyphens (**-**) to separate words.
- **Team name** (e.g. **yoda** or **iam** 'identity access management') 
  - Use this only if multiple teams are working on a same code base or repo.
- **App/function name** (e.g., catalog, checkout, translation etc.)
  - Use this only if there are multiple functional areas or multiple apps that you are supporting.
- **Year** (e.g., 2026, 2025)
- **Quarter** (Q1, Q2, Q3, Q4)

**Examples**:
- `fflag-yoda-2025-Q1-show-license-documents`
- `fflag-iam-2024-Q4-abtest-federated-login`

## Feature Flag Lifecycle
Feature flags should not live indefinitely. Once the feature is stable and the rollout is complete, flags and 
associated legacy code must be removed.

### Removal Policy
- Remove feature flags and their old code after an agreed time frame. For example: 1 quarter or 2 quarters.
- **Formula**: Remove flags created in (current quarter – **agreed number**).

**Examples**:
Lets say we teams aligned to remove feature flags after a quarter.
- If the current quarter is 2025.Q4, remove flags and code from 2025.Q2 and earlier.
- If the current quarter is 2026.Q1, remove flags and code from 2024.Q3 and earlier.
