# Review Work Progress Against PRD
# Purpose: Deep review of completed work against PRD requirements and corresponding task lists with thorough analysis

## Command Overview
This command performs a comprehensive review of work done against a specific PRD and its corresponding task list. It uses deep analysis ("ultrathinking") to ensure quality, completeness, and alignment with the original requirements.

## Command Usage

```
/review-work prd-[feature-name].md
```

Example:
- `/review-work prd-user-auth.md` - Reviews work against user authentication PRD

## File Resolution

The command automatically resolves related files:
- PRD file: `prd-[feature-name].md` (provided by user)
- Task file: `tasks-prd-[feature-name].md` (automatically deduced)
- Both files are expected in the `/tasks/` directory

## ⚠️ CRITICAL ANTI-HALLUCINATION RULES ⚠️

**YOU MUST NOT:**
- Claim tasks are complete without verifying
- Assume tests pass without running them
- Report success without evidence
- Skip actual execution of validation
- Imagine or predict outcomes

**YOU MUST:**
- Actually run all tests and read outputs
- Actually execute code to verify it works
- Actually check for broken references (cache_data, undefined variables)
- Report failures honestly and specifically
- Show real command outputs, not imagined ones

## Review Process

### Phase 1: Context Gathering

1. **Load PRD Requirements:**
   - Parse the provided PRD file
   - Extract all functional requirements
   - Note user stories and acceptance criteria
   - Identify success metrics

2. **Load Task List:**
   - Automatically find `tasks-prd-[feature-name].md`
   - Parse all parent tasks and sub-tasks
   - Check completion status of each item
   - Note any additional tasks added during development

3. **Analyze Work Done:**
   - Review git history for related commits
   - Identify all files created or modified
   - **ACTUALLY RUN** the test suite and **READ** the output
   - **VERIFY** tests are passing (not assume)
   - **SEARCH** for broken references (grep for cache_data, undefined vars)
   - Check actual test coverage numbers
   - Review any documentation created

### Phase 2: Deep Analysis (Ultrathinking)

For **EACH** PRD requirement and task item, perform thorough analysis:

#### A. PRD Requirement Verification
**For each functional requirement in the PRD:**
- **Requirement:** What was specified?
- **Implementation:** How was it implemented?
- **Completeness:** Is it fully implemented?
- **Edge Cases:** Are all scenarios covered?
- **User Stories:** Does it satisfy the related user stories?
- **Acceptance Criteria:** Does it meet all criteria?

#### B. Task Completion Analysis
**For each task in the task list:**
- **Task Status:** Is it marked complete?
- **Evidence:** What proof exists of completion?
  - **MANDATORY:** Show actual test output
  - **MANDATORY:** Show linting results
  - **MANDATORY:** Show type checking results
  - **MANDATORY:** Demonstrate feature working
- **Quality:** How well was it executed?
- **Dependencies:** Were prerequisite tasks completed first?
- **Testing:**
  - **RUN THE TESTS NOW** - Do not rely on past results
  - Show the actual output
  - If tests fail, mark task as INCOMPLETE

#### C. Cross-Reference Check
- **Coverage:** Does every PRD requirement have corresponding tasks?
- **Alignment:** Do completed tasks fulfill PRD requirements?
- **Gaps:** Are there PRD requirements without implementation?
- **Extras:** Was work done beyond PRD scope?

#### D. Quality Deep Dive
Think deeply about:
- **Correctness:** Does the solution solve the actual problem stated in the PRD?
- **Robustness:** Will this handle production load and edge cases?
- **Maintainability:** Is the code clean and maintainable?
- **Performance:** Are there performance implications?
- **Security:** Have security requirements been met?
- **Scalability:** Will this scale as the product grows?
- **Technical Debt:** What debt was introduced?
- **Integration:** How well does it integrate with existing systems?
- **User Experience:** Does it deliver the intended UX from the PRD?

### Phase 3: Item-by-Item Review Report

Present findings in this structured format:

```markdown
# Work Review: [Feature Name from PRD]

## 📋 PRD Requirements Review

### Requirement #1: [Requirement from PRD]
**Status:** [✅ COMPLETE | ⚠️ PARTIAL | ❌ INCOMPLETE]
**Implementation:** [How it was implemented]
**Evidence:**
  - **Test Results:** [ACTUAL output from running tests NOW]
  - **Live Demo:** [ACTUAL execution showing it works]
  - **Code Location:** [file:line_number references]
  - **Verification Commands Run:**
    ```bash
    # Show the ACTUAL commands you ran and their output
    npm test
    # [paste actual output here]
    ```
**Issues:** [Any problems found - BE HONEST about failures]
**Deep Analysis:**
- Does it fully meet the requirement? [Yes/No + explanation]
- Edge cases handled? [List of cases + status]
- Performance implications? [Analysis]
- Security considerations? [Analysis]
- Future maintenance concerns? [Analysis]

[Repeat for each requirement...]

## 📝 Task List Review

### Parent Task 1.0: [Task Name]
**Status:** [✅ COMPLETE | ⚠️ PARTIAL | ❌ INCOMPLETE]

#### Sub-task 1.1: [Sub-task Name]
**Marked Complete:** [Yes/No]
**Actually Complete:** [Yes/No - based on YOUR verification NOW]
**Verification Performed:**
  ```bash
  # Commands you ran to verify (not from memory, run them NOW)
  npm test -- --grep "relevant test"
  # [ACTUAL output]
  ```
**Evidence:**
  - Tests passing: [Show output]
  - Feature working: [Show execution]
  - No broken code: [Show grep results for cache_data, etc.]
**Quality Score:** [1-10]
**Honesty Check:**
  - Did I actually run tests? [Yes/No]
  - Did they actually pass? [Yes/No]
  - Any broken references? [Yes/No]

[Repeat for each sub-task...]

## 🔍 Deep Analysis Summary

### Alignment Score: [X/10]
How well does the implementation align with PRD requirements?
- [Detailed explanation]
- [Specific alignments and misalignments]

### Completeness Score: [X/10]
What percentage of PRD requirements are fully implemented?
- Total requirements: [N]
- Fully complete: [N]
- Partially complete: [N]
- Not started: [N]

### Quality Score: [X/10]
Overall code quality and robustness:
- Code cleanliness: [Score + explanation]
- Test coverage: [Score + explanation]
- Error handling: [Score + explanation]
- Performance: [Score + explanation]
- Security: [Score + explanation]

### Risk Assessment
**High Risk Issues:**
- [Critical issue 1]
- [Critical issue 2]

**Medium Risk Issues:**
- [Issue 1]
- [Issue 2]

**Low Risk Issues:**
- [Minor issue 1]
- [Minor issue 2]
```

### Phase 4: Comprehensive Summary

After detailed review, provide:

1. **Executive Summary:**
   - PRD requirements met: X of Y (X%)
   - Tasks completed: X of Y (X%)
   - Overall quality score: X/10
   - Ready for production: [Yes/No/With conditions]

2. **Key Achievements:**
   - [Major accomplishment 1]
   - [Major accomplishment 2]
   - [Major accomplishment 3]

3. **Critical Gaps:**
   - [Missing requirement 1]
   - [Missing requirement 2]
   - [Quality issue 1]

4. **Recommendations:**
   Priority 1 (Must fix before release):
   - [Action item 1]
   - [Action item 2]

   Priority 2 (Should fix soon):
   - [Action item 1]
   - [Action item 2]

   Priority 3 (Nice to have):
   - [Enhancement 1]
   - [Enhancement 2]

5. **Sign-off Readiness:**
   - [ ] All PRD functional requirements implemented
   - [ ] All acceptance criteria met
   - [ ] All tests passing
   - [ ] Documentation complete
   - [ ] No critical bugs
   - [ ] Performance acceptable
   - [ ] Security review passed

   **Ready for sign-off:** [YES/NO]
   **Conditions:** [If no, what needs to be done]

## 🚨 FINAL HALLUCINATION PREVENTION CHECK 🚨

Before submitting your review:
1. **Did you ACTUALLY run the tests?** (Not remember/assume)
2. **Did you SEE them pass?** (Not imagine)
3. **Did you SEARCH for broken code?** (grep for cache_data, etc.)
4. **Are you reporting REAL outputs?** (Not predicted)
5. **Are you being HONEST about failures?** (Not hiding issues)

If ANY answer is "no", START OVER and do it properly.

## AI Instructions

When executing this review command:

1. **Parse Arguments:** Extract the PRD filename from the command arguments.

2. **File Resolution:**
   - Use provided PRD filename as-is
   - Derive task filename by adding `tasks-` prefix
   - Check both files exist in `/tasks/` directory
   - Error gracefully if files not found

3. **Ultra-Deep Thinking:** For each item reviewed, think deeply about:
   - **Root cause analysis:** Why was it implemented this way?
   - **Alternative approaches:** Were better solutions available?
   - **Future implications:** What problems might arise later?
   - **Hidden assumptions:** What assumptions were made?
   - **Cross-cutting concerns:** How does this affect other features?
   - **Non-functional requirements:** Performance, security, accessibility?
   - **Business impact:** Does this deliver the intended value?
   - **User perspective:** Will users find this intuitive?
   - **Developer perspective:** Is this maintainable?
   - **System perspective:** Does this fit the architecture?

4. **Evidence-Based Review:**
   - **MANDATORY:** Run tests NOW and show output
   - **MANDATORY:** Execute code NOW and show results
   - **MANDATORY:** Search for broken refs NOW (cache_data, undefined)
   - Always show actual code/test results (not remembered)
   - Reference specific file:line_number
   - Include command outputs (freshly executed)
   - Show before/after comparisons

   **Verification Checklist (DO NOT SKIP):**
   - [ ] Ran full test suite
   - [ ] All tests passed
   - [ ] Ran linting
   - [ ] No lint errors
   - [ ] Ran type checking
   - [ ] No type errors
   - [ ] Searched for broken references
   - [ ] No cache_data or undefined variables found

5. **Be Critical but Constructive:**
   - Point out issues honestly
   - Always suggest solutions
   - Acknowledge good work done
   - Provide actionable feedback

6. **Structured Presentation:**
   - Review items one by one systematically
   - Use clear headings and formatting
   - Provide scores with justification
   - End with clear next steps

7. **Interactive Review:**
   - After reviewing each major section, pause and ask if the user wants details on any specific item
   - Be prepared to dive deeper into any area of concern
   - Offer to generate fix scripts for identified issues

## Example Usage

```
User: /review-work prd-user-authentication.md

AI:
I'll review the work done against the PRD for user authentication. Let me first load the PRD and corresponding task list...

[Loads prd-user-authentication.md]
[Automatically loads tasks-prd-user-authentication.md]
[Analyzes implementation]

# Work Review: User Authentication Feature

## 📋 PRD Requirements Review

### Requirement #1: Users must be able to register with email/password
**Status:** ✅ COMPLETE
**Implementation:** Implemented in /api/auth/register endpoint using bcrypt for password hashing
**Evidence:**
- Endpoint tested with curl: successful user creation
- Unit tests passing: auth.test.js:45-67
- Database shows users table with hashed passwords

**Deep Analysis:**
- Fully meets requirement? Yes - registration flow complete
- Edge cases handled?
  ✅ Duplicate email check
  ✅ Password strength validation
  ⚠️ Missing rate limiting for registration attempts
- Performance: Fast (~200ms response time)
- Security: Bcrypt with 10 rounds, could increase for production
- Maintenance: Clean code, well-structured

[Continues with detailed review...]
```

## Special Considerations

- If PRD file doesn't exist, provide clear error message
- If task file doesn't exist, offer to review against PRD only
- If neither file exists, offer to review based on git history
- Handle partially completed work gracefully
- Highlight any work done outside PRD scope