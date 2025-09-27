# Rule: Generating an Issue Brief
# Purpose: Template for producing an evidence-backed issue brief that enables reliable reproduction and triage

## Goal

Guide the assistant to capture complete diagnostic context for a reported defect so engineers can reproduce, investigate, and prioritize the issue efficiently.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `/issues/`
- **Filename:** `issue-brief-[short-slug].md` (e.g., `issue-brief-checkout-timeout.md`)

## Invocation

- Run `/create-issue-brief` in Codex CLI.
- Immediately prompt the user for the path to an existing issue brief markdown file because the CLI does not pass command arguments.
- Confirm the file exists and ends with `.md`; if unavailable, gather the issue report facts interactively before proceeding.

## Process

1. **Gather Context (Priority Order):**
   1. Ask the user for the path to an issue report markdown file, verify it ends with `.md`, and read it if present.
   2. If no file exists, review the last 10 chat messages to extract issue details.
   3. If the chat lacks sufficient data, interview the user for the full report.

2. **Deep Pre-Question Analysis (Ultrathink):** Before asking clarifying questions, think deeply about:
   - Impact blast radius (users, systems, financial risk)
   - Preconditions that may trigger the issue
   - Environment-specific dependencies (browsers, OS, regions)
   - Historical regressions or similar issues
   - Required telemetry or logs to gather
   - Potential data integrity or security implications
   - Urgency indicators (frequency, revenue loss, compliance risk)

3. **Clarifying Questions:** Ask targeted questions to fill gaps. Offer lettered/numbered options for easy replies. Focus on:
   - **Reproduction Steps:** Precise sequence, data inputs, accounts, feature flags
   - **Environment Details:** App version, build SHA, infrastructure region, device/OS/browser, network conditions
   - **Expected vs Actual:** What should happen vs what occurs, including error messages
   - **Diagnostics:** Logs, screenshots, HAR files, metrics anomalies, Sentry IDs
   - **Severity & Priority:** User impact, frequency, SLA breaches, blocking status
   - **Workarounds:** Any temporary mitigation users can apply
   - **Related History:** Known incidents, recent deploys, toggles, migrations
   - **Data Sensitivity:** Any PII/security concerns while sharing evidence

4. **Deep Analysis of Answers:**
   - Validate reproduction steps are actionable and deterministic
   - Identify missing preconditions, toggles, or data setup steps
   - Surface suspicious subsystems or recently changed code paths
   - Flag security, privacy, or compliance risks needing escalation
   - Note required access (feature flags, admin roles, VPN) for engineers

5. **Construct the Issue Brief:** Populate the sections below:

```markdown
# Issue Brief: [Slug/Title]

## Summary
- Concise description of the issue and its business impact

## Impact Assessment
- Severity (Critical / High / Medium / Low)
- Frequency (Always / Intermittent / Rare)
- Affected user segments or tenants

## Environment & Build Details
- Application/service name and version
- Deployment region / cluster / data center
- Device, OS, browser (with versions)
- Feature flags or config toggles enabled
- Account/tenant IDs used (anonymize when required)

## Preconditions
- Data setup, permissions, or background jobs required before reproduction

## Reproduction Steps
1. Step-by-step actions (include inputs, APIs, scripts)
2. ...

## Expected Behavior
- Describe the correct outcome(s) clearly

## Actual Behavior
- Describe observed incorrect behavior
- Include exact error messages, stack traces, screenshots (links), or metrics where applicable

## Diagnostics & Evidence
- Logs (redact PII), monitoring screenshots, Sentry/Rollbar IDs
- Database queries, traces, HAR files, or packet captures
- Time windows for relevant telemetry (UTC timestamps)

## Hypotheses & Notes
- Initial theories about root cause (link to recent code changes, deployments, toggles)
- Related tickets or incidents

## Temporary Mitigations / Workarounds
- Document any mitigations already in place

## Open Questions
- Unknowns or additional info needed to proceed

## Attachments
- List files uploaded or linked (logs, screenshots, traces)
```

6. **Quality Gates:**
   - Ensure reproduction steps were verified by the reporter or ask them to re-run and confirm
   - Validate evidence is attached or linked; if missing, flag explicitly
   - Confirm sensitive data is anonymized before saving
   - Highlight any blockers preventing engineers from starting work (missing access, tooling)

7. **Save Output:**
   - Ensure `/issues/` exists; instruct the user to create it if absent
   - Save the issue brief using the naming format above
   - Notify the user of the saved path and remind them to share attachments securely (not embedded if confidential)

## Target Audience

Assume the primary reader is a **triage engineer or on-call responder** who needs to reproduce and prioritize the issue quickly. The brief must be explicit, verifiable, and include direct evidence where possible.

## Final Instructions

- Do NOT attempt to fix the issue here; focus solely on capturing reproducible context
- If information is missing, clearly mark the gaps and request follow-up
- Encourage reporters to re-validate reproduction after clarifications are gathered
