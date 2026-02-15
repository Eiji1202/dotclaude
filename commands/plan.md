Restate requirements, assess risks, and create step-by-step implementation plan.
WAIT for user CONFIRM before touching any code.

## Steps

1. **Restate Requirements** — Clarify what needs to be built in your own words
2. **Identify Risks** — Surface potential issues, blockers, and edge cases
3. **Assess Current Codebase** — Read relevant files to understand existing patterns and dependencies
4. **Create Step Plan** — Break down implementation into phases with:
   - Specific files to create or modify
   - What each change does and why
   - Dependencies between steps
   - Risk level (Low / Medium / High) per step
5. **Wait for Confirmation** — Present the plan and MUST receive explicit user approval before writing any code

## Output Format

```
# Implementation Plan: <Feature Name>

## Requirements Restatement
- (bullet points of what will be built)

## Risks & Considerations
- (potential issues and how to mitigate them)

## Implementation Phases

### Phase 1: <Name>
1. **<Action>** (File: <path>)
   - What: ...
   - Why: ...
   - Risk: Low/Medium/High

### Phase 2: <Name>
...

## Awaiting Confirmation
Ready to proceed? Type "go" or suggest changes.
```
