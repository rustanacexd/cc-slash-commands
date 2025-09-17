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
   - Check test results and coverage
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
- **Quality:** How well was it executed?
- **Dependencies:** Were prerequisite tasks completed first?
- **Testing:** Was it properly tested and validated?

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
**Evidence:** [Test results, code references, demos]
**Issues:** [Any problems found]
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
**Verified:** [Yes/No]
**Evidence:** [What proves it's done]
**Quality Score:** [1-10]
**Analysis:** [Deep thoughts on implementation quality]

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
   - Always show actual code/test results
   - Reference specific file:line_number
   - Include command outputs where relevant
   - Show before/after comparisons

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