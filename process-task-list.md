# Task List Management
# Purpose: Template for executing task lists with strict verification and evidence requirements

Guidelines for managing task lists in markdown files to track progress on completing a PRD

## Invocation

- Run `/process-task-list` in Codex CLI.
- Immediately prompt the user for the path to the existing task list markdown file because the CLI does not pass command arguments.
- Confirm the file exists and ends with `.md`; if the user cannot provide one, coordinate with them to identify or create the correct task list before proceeding.

## Implementation Principles
- **Start simple:** Write the most straightforward code that works
- **No premature optimization:** Make it work, then make it better if needed
- **Inline first:** Keep code in the same file until it needs to be shared
- **Avoid unnecessary patterns:** No factories, builders, or decorators unless truly needed
- **Use framework defaults:** Don't customize what already works

## Task Implementation with Deep Analysis
- **One sub-task at a time:** Finish the current sub-task before beginning the next, unless the user explicitly requests step-by-step approval

### Before Starting Each Task (Ultrathink):
Think deeply about:
- **Understanding:** Do I fully understand what this task requires?
- **Approach:** What are the possible approaches and which is best?
- **Dependencies:** What needs to be in place for this to work?
- **Impact:** How will this change affect the rest of the system?
- **Risks:** What could go wrong during implementation?
- **Testing:** How will I verify this works correctly?

## Task Verification Requirements with Deep Analysis
**CRITICAL: DO NOT mark any task as done `[x]` without concrete evidence AND deep verification**

### ⚠️ ANTI-HALLUCINATION PROTOCOL ⚠️
**YOU ARE FORBIDDEN FROM:**
- Claiming tests pass without running them
- Marking tasks complete without actual execution
- Imagining or predicting outcomes
- Assuming code works without verification
- Skipping test execution
- Leaving broken references (cache_data, old variables)

**YOU MUST:**
- Run actual commands and read actual outputs
- Fix all test failures before proceeding
- Report failures honestly and immediately
- Verify with real tool execution, not assumptions

Before marking any task complete, you MUST:

1. **Show proof of implementation:** Display the actual code/changes made

2. **Deep Verification (Ultrathink):**
   - **Correctness:** Does this solve the intended problem?
   - **Completeness:** Are all aspects of the task addressed?
   - **Edge Cases:** Have I handled all edge cases?
   - **Integration:** Does this work with existing code?
   - **Performance:** Will this perform acceptably?
   - **Security:** Are there any security implications?
   - **Maintainability:** Is this code maintainable?

3. **Demonstrate it works:**
   - **MANDATORY:** Run ALL tests (`npm test`, `pytest`, etc.)
   - **MANDATORY:** Show the ACTUAL test output
   - **MANDATORY:** If tests fail, FIX THEM before continuing
   - Run the code with real inputs
   - Show actual output, not predicted output
   - Execute validation commands

4. **Verify no errors:**
   - **RUN** linting: `npm run lint` or equivalent
   - **RUN** type checking: `npm run typecheck` or equivalent
   - **READ** the actual output
   - **FIX** any errors found
   - **RE-RUN** to confirm fixes
   - Search for broken references (undefined variables, missing imports)

5. **Explain what you verified:** Explicitly state what you tested and what the results were

6. **Deep Reflection:**
   - What assumptions did I make?
   - What could still go wrong?
   - What follow-up work might be needed?
   - What did I learn from this task?

**Examples of required evidence:**
- For UI changes: Show the component renders without errors
- For API endpoints: Make a test request and show the response
- For functions: Run the function with test inputs and show outputs
- For database changes: Query the database and show the schema/data
- For configurations: Show the config loads and applies correctly
- For validation tasks: Show PRD requirements checklist with each item verified
- For validation tasks: Demonstrate feature working with multiple test cases
- For validation tasks: Show automated test results passing
- For validation tasks: Provide screenshots/output proving edge cases work
- For cleanup tasks: Show `ls` output proving temporary files are gone
- For cleanup tasks: Run grep/search to confirm no debug statements remain
- For cleanup tasks: Show git status to confirm only intended files are staged

### ❌ FAILURE PROTOCOL
**If tests fail or errors occur:**
1. **STOP** - Do not mark the task complete
2. **REPORT** - Tell the user exactly what failed
3. **SHOW** - Display the actual error messages
4. **FIX** - Attempt to fix the issues
5. **VERIFY** - Re-run tests to confirm fixes
6. **ITERATE** - Repeat until all tests pass

**If you cannot provide evidence, DO NOT mark as complete.** Instead:
- Keep the task as `[ ]`
- State explicitly: "Task incomplete - [specific reason]"
- Show the actual failure/error
- Ask the user for help if needed

## Validation Sub-Task Requirements with Deep Analysis
**For "Review and validate implementation" sub-tasks specifically:**

### Deep Pre-Validation Thinking (Ultrathink):
Before validating, think deeply about:
- **Success Criteria:** What defines success for this implementation?
- **Failure Modes:** How could this fail in production?
- **User Scenarios:** How will real users interact with this?
- **System Load:** How will this behave under stress?
- **Data Integrity:** Could this corrupt or lose data?
- **Backward Compatibility:** Does this break existing functionality?
- **Future Maintenance:** Will future developers understand this?

Before marking validation task complete, you MUST:
1. **Create a checklist** from the PRD requirements for this parent task
2. **Test each requirement** with actual execution/demonstration
3. **Document test results** with specific inputs and outputs
4. **Test edge cases** like empty inputs, invalid data, boundary values
5. **Run automated tests** and show passing results
6. **Compare implementation** against PRD specifications line by line
7. **Verify no regressions** by testing related existing functionality

### Deep Validation Analysis (Ultrathink):
During validation, deeply consider:
- **Real-World Usage:** Test with realistic data and scenarios
- **Stress Testing:** What happens at scale or under load?
- **Error Recovery:** How does it handle and recover from errors?
- **User Experience:** Is it intuitive and user-friendly?
- **Performance:** Are there any performance bottlenecks?
- **Security:** Are there any vulnerabilities?
- **Monitoring:** Can we detect if something goes wrong?

**DO NOT mark validation task complete without showing:**
- ✅ Each PRD requirement checked off with evidence
- ✅ Multiple test scenarios with results
- ✅ Edge case handling demonstration
- ✅ Test suite passing
- ✅ Explicit statement: "All PRD requirements for [parent task] are verified and working"

- **Completion protocol:**
  1. When you finish a **sub‑task**:
     - **FIRST** run all tests and verify they pass
     - **THEN** run linting and type checking
     - **ONLY IF ALL PASS** mark it as completed by changing `[ ]` to `[x]`
     - **IF ANY FAIL** keep as `[ ]` and fix the issues
  2. If **all** subtasks underneath a parent task are now `[x]`, follow this sequence:
    - **First**: Run the full test suite (`pytest`, `npm test`, `bin/rails test`, etc.)
      - **READ THE OUTPUT** - Do not assume it passed
      - **VERIFY** every test is green/passing
      - **FIX** any failures before proceeding
    - **Second**: Run linting (`npm run lint`, `ruff`, etc.)
      - **READ THE OUTPUT** - Check for any warnings/errors
      - **FIX** all issues found
    - **Third**: Run type checking (`npm run typecheck`, `mypy`, etc.)
      - **READ THE OUTPUT** - Verify no type errors
      - **FIX** any type issues
    - **Only if ALL checks pass**: Stage changes (`git add .`)
    - **Clean up Development Artifacts**:
      1. List all temporary files created during this task
      2. Remove each temporary file with confirmation (debug scripts, research files, etc.)
      3. Search for and remove debug statements (console.log, print, debugger)
      4. Remove commented-out experimental code
      5. Verify no .env.local, .env.test or temporary configs remain
      6. Show proof of cleanup (ls output, grep results showing no debug statements)
    - **Commit**: Use a descriptive commit message that:
      - Uses conventional commit format (`feat:`, `fix:`, `refactor:`, etc.)
      - Summarizes what was accomplished in the parent task
      - Lists key changes and additions
      - References the task number and PRD context
      - **Formats the message as a single-line command using `-m` flags**, e.g.:

        ```
        git commit -m "feat: add payment validation logic" -m "- Validates card type and expiry" -m "- Adds unit tests for edge cases" -m "Related to T123 in PRD"
        ```
  3. Once all the subtasks are marked completed and changes have been committed, mark the **parent task** as completed.
- Stop after each sub-task only if the user has asked for step-by-step confirmation.

## Task List Maintenance

1. **Update the task list as you work:**
   - Mark tasks and subtasks as completed (`[x]`) per the protocol above.
   - Add new tasks as they emerge.

2. **Maintain the "Relevant Files" section:**
   - List every file created or modified.
   - Give each file a one‑line description of its purpose.

## AI Instructions

When working with task lists, the AI must:

1. Regularly update the task list file after finishing any significant work.
2. Follow the completion protocol:
   - Mark each finished **sub‑task** `[x]`.
   - Mark the **parent task** `[x]` once **all** its subtasks are `[x]`.
3. Add newly discovered tasks.
4. Keep "Relevant Files" accurate and up to date.
5. Before starting work, check which sub‑task is next.
6. After implementing a sub‑task:
   - Run tests to verify it works
   - Update the task file with evidence of completion
   - If tests fail, report the failure and fix it
   - Pause for user approval only when the user has asked for it

### 🚨 HALLUCINATION CHECK 🚨
Before marking ANY task complete, ask yourself:
- Did I ACTUALLY run the tests? (Not imagine/predict)
- Did I SEE the tests pass? (Not assume)
- Did I FIX all failures? (Not ignore)
- Can I SHOW the evidence? (Not claim)
- Are there NO broken references? (cache_data, undefined vars)

If ANY answer is "no", DO NOT mark complete.
