# Rule: Generating a Task List from a PRD
# Purpose: Template for converting PRDs into actionable task lists with parent tasks and sub-tasks

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list in Markdown format based on an existing Product Requirements Document (PRD). The task list should guide a developer through implementation.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `/tasks/`
- **Filename:** `tasks-[prd-file-name].md` (e.g., `tasks-prd-user-profile-editing.md`)

## Invocation

- Run `/generate-tasks` in Codex CLI.
- Immediately prompt the user for the PRD markdown file path because the CLI does not pass command arguments.
- Confirm the file exists before reading; if the user cannot supply one, gather the necessary requirements context directly from them.

## Process

1.  **Receive PRD Reference:** Immediately after the command starts, ask the user for the path to the PRD markdown file (since Codex CLI ignores command arguments). Verify the path exists before reading it.

2.  **Deep Analysis of PRD (Ultrathink):**
    Before breaking down tasks, think deeply about:
    - **Core Requirements:** What are the essential vs nice-to-have features?
    - **Hidden Complexity:** What complexity is not immediately obvious?
    - **Dependencies:** What must be built first for other things to work?
    - **Risk Areas:** Which parts are most likely to have issues?
    - **Integration Points:** How will this interact with existing systems?
    - **Data Flow:** How will data move through the system?
    - **State Management:** What state needs to be tracked and where?
    - **Error Scenarios:** What can go wrong and how should it be handled?
    - **Performance Bottlenecks:** Where might performance issues arise?
    - **Security Vulnerabilities:** What attack vectors need consideration?

3.  **Assess Current State:** Review the existing codebase to understand existing infrastructure, architectural patterns and conventions. Also, identify any existing components or features that already exist and could be relevant to the PRD requirements. Then, identify existing related files, components, and utilities that can be leveraged or need modification.

4.  **Deep Task Planning (Ultrathink):**
    Before creating tasks, deeply consider:
    - **Logical Sequence:** What's the optimal order of implementation?
    - **Parallel Work:** What can be done simultaneously?
    - **Critical Path:** What tasks block others?
    - **Testing Strategy:** How will each piece be tested?
    - **Incremental Delivery:** Can we deliver value incrementally?
    - **Rollback Plan:** How can changes be safely reversed?
    - **Migration Needs:** Do we need to migrate existing data/functionality?

5.  **Phase 1: Generate Parent Tasks:** Based on the PRD analysis and current state assessment, create the file and generate the main, high-level tasks required to implement the feature. Use your judgement on how many high-level tasks to use.

6. **Inform the user:** Present these tasks to the user in the specified format (without sub-tasks yet) For example, say "I have generated the high-level tasks based on the PRD. Ready to generate the sub-tasks? Respond with 'Go' to proceed."

7.  **Wait for Confirmation:** Pause and wait for the user to respond with "Go".

8.  **Phase 2: Generate Sub-Tasks with Deep Analysis:** Once the user confirms, break down each parent task into smaller, actionable sub-tasks. For each sub-task, think deeply about:
    - **Necessity:** Is this sub-task truly needed or is it over-engineering?
    - **Completeness:** Will this sub-task fully address its parent task?
    - **Dependencies:** What must be done before this sub-task?
    - **Validation:** How will we know this sub-task is done correctly?
    - **Edge Cases:** What edge cases must this sub-task handle?
    - **Time Estimate:** How complex is this sub-task really?
    - **Risk Level:** What could go wrong with this sub-task?

    **Anti-Overengineering Guidelines for Sub-Tasks:**
    - Prefer direct implementation over creating new abstractions
    - Avoid creating unnecessary interfaces, factories, or design patterns
    - Start with inline code before extracting to separate functions/files
    - Don't create configuration files unless there are multiple environments
    - Limit layers of indirection (max 2-3 levels)
    - Use existing framework features instead of custom implementations

    **Validation Task Generation:**
    - Always include a "Review and validate implementation" sub-task as the SECOND-TO-LAST item for each parent task (before cleanup)
    - This validation task MUST include checks for:
      - Verify all PRD requirements for this task are met
      - Test the feature/functionality manually with different inputs
      - Check edge cases and error scenarios
      - Confirm error handling works correctly
      - Validate UI/UX matches PRD specifications (if applicable)
      - Run automated tests and ensure they pass
      - Verify no regressions in existing functionality

    **Cleanup Task Generation:**
    - Always include a "Cleanup development artifacts" sub-task as the LAST item before commit for each parent task
    - This cleanup task should specify:
      - Remove debug/test scripts created during development
      - Remove research/analysis files
      - Clean up console.log/print statements added for debugging
      - Remove commented-out experimental code
      - Delete temporary test data files
      - Remove any POC files not part of final solution
8.  **Identify Relevant Files:** Based on the tasks and PRD, identify potential files that will need to be created or modified. List these under the `Relevant Files` section, including corresponding test files if applicable.
9.  **Generate Final Output:** Combine the parent tasks, sub-tasks, relevant files, and notes into the final Markdown structure.
10.  **Save Task List:** Save the generated document in the `/tasks/` directory with the filename `tasks-[prd-file-name].md`, where `[prd-file-name]` matches the base name of the input PRD file (e.g., if the input was `prd-user-profile-editing.md`, the output is `tasks-prd-user-profile-editing.md`).

## Output Format

The generated task list _must_ follow this structure:

```markdown
## Relevant Files

- `path/to/potential/file1.ts` - Brief description of why this file is relevant (e.g., Contains the main component for this feature).
- `path/to/file1.test.ts` - Unit tests for `file1.ts`.
- `path/to/another/file.tsx` - Brief description (e.g., API route handler for data submission).
- `path/to/another/file.test.tsx` - Unit tests for `another/file.tsx`.
- `lib/utils/helpers.ts` - Brief description (e.g., Utility functions needed for calculations).
- `lib/utils/helpers.test.ts` - Unit tests for `helpers.ts`.

### Notes

- Unit tests should typically be placed alongside the code files they are testing (e.g., `MyComponent.tsx` and `MyComponent.test.tsx` in the same directory).
- Use `npx jest [optional/path/to/test/file]` to run tests. Running without a path executes all tests found by the Jest configuration.

## Tasks

- [ ] 1.0 Parent Task Title
  - [ ] 1.1 [Sub-task description 1.1]
  - [ ] 1.2 [Sub-task description 1.2]
- [ ] 2.0 Parent Task Title
  - [ ] 2.1 [Sub-task description 2.1]
- [ ] 3.0 Parent Task Title (may not require sub-tasks if purely structural or configuration)
```

## Interaction Model

The process explicitly requires a pause after generating parent tasks to get user confirmation ("Go") before proceeding to generate the detailed sub-tasks. This ensures the high-level plan aligns with user expectations before diving into details.

## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature with awareness of the existing codebase context.