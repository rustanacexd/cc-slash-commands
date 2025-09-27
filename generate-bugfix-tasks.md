# Rule: Generating a Bugfix Task List from a Bug Brief
# Purpose: Template for converting bug briefs into actionable remediation task lists with mandatory verification steps

## Goal

Enable the assistant to transform an evidence-backed bug brief into a structured Markdown task list that guides engineers through reproduction, diagnosis, remediation, validation, and cleanup.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `/bugs/tasks/`
- **Filename:** `bugfix-tasks-[bug-slug].md` (e.g., `bugfix-tasks-checkout-timeout.md`)

## Invocation

- Run `/generate-bugfix-tasks` in Codex CLI.
- Immediately prompt the user for the path to the bug brief markdown file because the CLI does not pass command arguments.
- Confirm the file exists and ends with `.md`; if unavailable, gather the bug context interactively before proceeding.

## Process

1. **Receive Bug Brief Reference:**
   - Ask for the bug brief path, verify its existence, and read it.
   - If no file exists, create a quick bug summary from the chat using the `create-bug-brief` process before continuing.

2. **Deep Analysis of the Bug (Ultrathink):** Before planning tasks, think deeply about:
   - Determinism of reproduction steps; identify missing data/setup
   - Likely failure domains (backend, frontend, infra, data pipeline)
   - Recent deploys, migrations, or config changes touching those domains
   - Logs/metrics required to confirm root cause
   - Risk of regression in adjacent features once fixed
   - Required access (feature flags, credentials) for engineers and QA
   - Additional observability or telemetry gaps to address

3. **Assess Current Codebase:**
   - Inventory relevant services/modules based on the bug brief
   - Identify tests covering the failing behavior (or missing coverage)
   - Note existing monitoring or alerting to update post-fix

4. **Deep Task Planning (Ultrathink):** Consider:
   - Minimal steps required to prove the bug exists before touching code
   - Sequencing for diagnosis vs mitigation vs permanent fix
   - How to ensure the fix is tested (automated + manual regression)
   - Whether feature flags or staged rollouts are needed
   - Cleanup activities (removing logging, disabling flags, deleting temp data)

5. **Phase 1: Generate Parent Tasks:**
   - Typical parent tasks might include: "Reproduce & Scope", "Identify Root Cause", "Implement Fix", "Validate & Guardrails", "Release & Postmortem".
   - Present parent tasks to the user with numbering but **without subtasks** yet.

6. **Inform the User:**
   - Say: "I have generated the high-level bugfix tasks. Ready for detailed subtasks? Reply 'Go' to continue." (or similar).

7. **Wait for Confirmation:** Pause until the user responds with "Go".

8. **Phase 2: Generate Sub-Tasks with Deep Analysis:**
   - For each parent task, break work into concise, verifiable subtasks.
   - Subtasks must always include:
     - **Reproduction Proof:** Re-run steps, capture evidence before coding
     - **Diagnosis:** Inspect logs, traces, or code to confirm root cause
     - **Fix Implementation:** Minimal change to resolve bug
     - **Automated Test Coverage:** Add failing test first when feasible
     - **Manual & Automated Validation:** Confirm bug no longer reproduces and run regression checks
     - **Guardrails:** Update monitors, feature flags, documentation if needed
     - **Cleanup Development Artifacts:** Remove temp diagnostics, reset toggles, delete sample data
   - Apply anti-overengineering rules: keep solutions simple, prefer direct fixes over new abstractions.

9. **Validation Task Requirements:**
   - Always include a "Review and validate bugfix" sub-task as the second-to-last item per parent task, covering:
     - Confirm original reproduction steps now pass
     - Execute regression tests for adjacent functionality
     - Verify logs/metrics are clean (no new errors, no alerts)
     - Ensure feature flags/configs are set to intended final state
     - Run automated test suites and document results
   - The final subtask per parent should be "Cleanup development artifacts" detailing the removal of debug logs, temporary scripts, sample data, feature flag cleanups, etc.

10. **Relevant Files Section:**
    - List expected code, test, config, and observability files involved, plus any scripts for reproduction or diagnostics.
    - Include failing test files to create/modify and monitoring dashboards to update.

11. **Generate Final Output:** Follow this structure:

```markdown
## Relevant Files

- `path/to/module.ts` - Core code path suspected to contain the bug
- `path/to/module.test.ts` - Unit tests covering the regression
- `scripts/reproduce-bug.sh` - Script to reproduce the issue locally
- `docs/runbook.md` - Runbook entry to update after fix
- `observability/dashboard.json` - Monitoring dashboard requiring adjustment

### Notes

- Capture before/after evidence (logs, metrics, screenshots) and link it in the task list.
- Add or update failing automated tests to prevent regressions.

## Tasks

- [ ] 1.0 Reproduce and Scope the Bug
  - [ ] 1.1 ...
- [ ] 2.0 Identify Root Cause
  - [ ] 2.1 ...
- [ ] 3.0 Implement Fix
  - [ ] 3.1 ...
- [ ] 4.0 Validate & Guardrails
  - [ ] 4.1 ...
- [ ] 5.0 Release & Postmortem (optional based on severity)
```

12. **Save Task List:**
   - Ensure `/bugs/tasks/` exists; instruct the user to create it if absent
   - Save the markdown as `bugfix-tasks-[bug-slug].md`

## Interaction Model

Follow the same two-phase interaction as feature task generation: parent tasks first, wait for "Go", then emit subtasks.

## Target Audience

Assume the reader is a **junior engineer** handling a production bug under time pressure. Tasks must be explicit, enforce evidence collection, and minimize context switching.

## Final Instructions

- Emphasize evidence at every stage (screenshots, logs, test output)
- Call out any missing context as new tasks/questions rather than guessing
- Keep tasks laser-focused on resolving the reported bug; defer enhancements unless required to fix regression
- Recommend creating follow-up tickets for identified tech debt instead of bloating the bugfix task list
