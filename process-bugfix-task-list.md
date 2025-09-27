# Bugfix Task List Management
# Purpose: Template for executing bugfix task lists with mandatory reproduction, diagnosis, and verification evidence

Guidelines for working through bugfix task lists in markdown files to ensure reproducibility, safe remediation, and regression prevention.

## Invocation

- Run `/process-bugfix-task-list` in Codex CLI.
- Immediately prompt the user for the path to the existing bugfix task list markdown file because the CLI does not pass command arguments.
- Confirm the file exists and ends with `.md`; if the user cannot provide one, coordinate to generate it (using `/generate-bugfix-tasks`) before proceeding.

## Implementation Principles
- **Prove the failure first:** Never touch code until you can reproduce the bug consistently
- **Fix what you measure:** Capture before/after evidence; if you cannot measure it, you cannot confirm the fix
- **Minimal viable change:** Apply the smallest safe code change that resolves the bug
- **Protect regressions:** Add or update automated tests to lock the behavior
- **Log responsibly:** Add diagnostic logging temporarily, then remove or downgrade before finishing
- **Favor observability:** Prefer metrics, logs, and traces over manual claims

## Bugfix Execution with Deep Analysis
- **One sub-task at a time:** Finish the active sub-task before moving on unless the user explicitly requests coordination pauses

### Before Starting Each Bugfix Task (Ultrathink):
Think deeply about:
- **Reproduction readiness:** Do I have the exact data, environment, and access to reproduce?
- **Failure signals:** Which logs, traces, metrics, or screenshots demonstrate the bug?
- **Root cause hypotheses:** What are the most likely failure points?
- **Blast radius:** What adjacent features or services could be impacted by the change?
- **Rollback/Safety nets:** How will I revert if the fix misbehaves?
- **Validation paths:** Which automated tests, manual checks, and monitoring dashboards will confirm success?
- **Observability:** Do I need to enhance logging or metrics temporarily to observe the fix?

## Bugfix Verification Requirements with Deep Analysis
**CRITICAL: DO NOT mark any bugfix sub-task as done `[x]` without real reproduction evidence AND deep verification.**

### ⚠️ ANTI-HALLUCINATION PROTOCOL ⚠️
**YOU ARE FORBIDDEN FROM:**
- Claiming the bug is fixed without re-running the original reproduction steps
- Reporting "cannot reproduce" without showing the attempted steps and outputs
- Assuming tests or monitors pass without executing them
- Leaving temporary feature flags or logging enabled without documenting them
- Skipping negative testing for regression-sensitive areas

**YOU MUST:**
- Capture evidence of the bug before implementing the fix (screenshots, logs, failing tests)
- Create or update automated tests that fail before the fix and pass after
- Run actual commands and show outputs
- Confirm related alerts or monitors are green after deployment
- Document any follow-up or deferred work explicitly

Before marking any bugfix task complete, you MUST:

1. **Show proof of reproduction:** Document the exact steps/commands/scripts used, including actual output demonstrating the failure.

2. **Deep Diagnosis (Ultrathink):**
   - **Root Cause:** Explain the precise defect (e.g., null check missing in module X)
   - **Scope:** Identify impacted code paths and risk to other features
   - **Dependencies:** Note configs, feature flags, or data dependencies involved
   - **Instrumentation:** Determine if new logs/metrics are required to observe the fix

3. **Implement & Demonstrate Fix:**
   - Apply the minimal change
   - Show diff snippets for relevant files
   - Run targeted unit/integration tests covering the bug path and show actual output

4. **Deep Validation:**
   - **Reproduction Steps (Post-Fix):** Re-run original reproduction steps and show success evidence
   - **Regression Sweep:** Execute relevant automated suites (`npm test`, `pytest`, `go test`, etc.) and document results
   - **Monitoring:** Verify dashboards/alerts for error rates, latency, or other KPIs are healthy
   - **Edge Cases:** Test boundary conditions discovered during diagnosis
   - **Environment Parity:** Confirm fix across all affected environments (local, staging, prod-like) when feasible

5. **Security & Compliance Check:**
   - Ensure no sensitive logs were added
   - Validate permissions/access changes adhere to policy
   - Confirm data integrity (no unintended migrations)

6. **Cleanup:**
   - Remove temporary logging, feature flags, or test data
   - Update runbooks, docs, and on-call notes if workflows changed
   - Ensure follow-up tickets are captured for any deferred items

7. **Explain validation:** Explicitly state which tests ran, what evidence was collected, and the outcomes.

8. **Deep Reflection:**
   - What caused the bug and how can we prevent similar issues?
   - Did we improve observability or documentation?
   - Are additional monitors or tests recommended?
   - Any risk remaining in production?

**Examples of required evidence:**
- Failing unit/integration test output before fix, passing after fix
- CLI transcript of reproduction script showing failure then success
- Screenshots of metrics dashboards (before/after) with timestamps
- Database queries confirming data integrity
- Links to alert acknowledgements or incident timelines

### ❌ FAILURE PROTOCOL
**If reproduction fails unexpectedly:**
1. **STOP** - Do not proceed with the fix
2. **REPORT** - Document the discrepancy and request updated info from reporter
3. **COLLECT** - Gather logs or recordings of the attempt

**If tests fail or new issues appear:**
1. **STOP** - Leave task unchecked
2. **REPORT** - Share exact errors/output
3. **FIX** - Address failures or escalate blockers
4. **RE-RUN** - Repeat until all validations pass

**If you cannot provide evidence, DO NOT mark complete.** Keep the task as `[ ]` and state explicitly which evidence is missing.

## Validation Sub-Task Requirements (Bugfix Deep Analysis)

For every "Review and validate bugfix" sub-task:

### Deep Pre-Validation Thinking (Ultrathink):
- **Original Failure:** Confirm we can demonstrate the fix resolves the initial failure mode
- **Regression Risk:** Identify adjacent features to retest
- **Stress & Load:** Consider load/scale conditions if relevant
- **Rollout Strategy:** Decide on flagging, canary, or staged release plans
- **Alerting:** Ensure alerts fire if the issue resurfaces

### Validation Checklist must include:
1. Re-run original reproduction steps (ideally automated) and capture success evidence
2. Execute automated tests covering the fix and surrounding behavior; attach output
3. Perform targeted regression testing (manual or automated) on adjacent features
4. Verify monitoring dashboards show healthy metrics; attach screenshots or query outputs
5. Confirm error budgets/SLAs are unaffected
6. Ensure feature flags/configs are in correct final state (and rollback plan documented)
7. Update documentation/runbooks with the new expected behavior and detection strategy

**Completion Protocol for Validation Tasks:**
- Only mark `[x]` after all checklist items above have evidence

## Cleanup Protocol (Bugfix-Specific)
1. **Temporary Artifacts:** Remove reproduction scripts, debug logs, feature toggles, or tracing configs introduced during investigation unless intentionally permanent.
2. **Data Hygiene:** Delete temporary test data or anonymize before retaining.
3. **Monitoring Updates:** Ensure newly added alerts/dashboards are documented and linked.
4. **Git Hygiene:**
   - Stage only intended files (`git status` must be clean)
   - Run formatters/lints as required by the repository
   - Prepare commit message in conventional style (`fix:`/`chore:`) referencing bug ID

## Bugfix Task List Maintenance

1. **Update task list continuously:**
   - Record evidence links (log archive, screenshots, test output) alongside tasks
   - Add new subtasks for discovered work (e.g., "Create follow-up ticket for tech debt")

2. **Maintain Relevant Files section:**
   - Include source files, tests, scripts, observability assets, and documentation touched
   - Note any config/feature flag changes requiring follow-up

3. **Status Discipline:**
   - Do not skip sub-tasks even under time pressure; evidence is mandatory
   - If SLA pressure exists, coordinate with incident commander but keep documentation accurate

## AI Instructions

When executing a bugfix task list, the AI must:

1. Request the next unchecked sub-task and focus solely on it.
2. Before coding, prove the bug reproduces and attach evidence.
3. After implementing changes:
   - Run targeted tests first (unit/integration), then full suite as required
   - Run linting/type-checking commands mandated by the repo
   - Capture outputs verbatim and store references in the task list
4. If new issues arise, create sub-tasks instead of silently fixing them.
5. Pause only if the user asks for interim approval.

### 🚨 HALLUCINATION CHECK 🚨
Before marking ANY bugfix task complete, ask yourself:
- Did I capture BEFORE evidence of the bug?
- Did I apply a minimal fix and document the diff?
- Did I collect AFTER evidence showing the bug is resolved?
- Did all required tests/linters/type-checks run and pass? (attach outputs)
- Did I remove temporary assets and reset flags/configs?
- Are monitoring and alerts up to date?

If ANY answer is "no", keep the task unchecked and resolve the gap.
