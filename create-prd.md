# Rule: Generating a Product Requirements Document (PRD)
# Purpose: Template for creating detailed PRDs from prompts or chat history with clarifying questions

## Goal

To guide an AI assistant in creating a detailed Product Requirements Document (PRD) in Markdown format, based on (in order of priority):
1. **Markdown file path** (e.g., `/create-prd /path/to/requirements.md`) - Reads requirements from the specified markdown file
2. **Chat history** (e.g., `/create-prd`) - Analyzes the last 10 messages from chat history when no argument provided
3. **Command prompt** (e.g., `/create-prd "user authentication feature"`) - Uses the provided text prompt as initial context

The PRD should be clear, actionable, and suitable for a junior developer to understand and implement the feature.

## Design Principles

- **Simplicity First:** Always prefer the simplest solution that meets the requirements
- **YAGNI (You Aren't Gonna Need It):** Don't add functionality until it's actually needed
- **MVP Focus:** Start with the minimum viable implementation
- **Avoid premature abstractions:** Don't create abstractions for single use cases
- **Leverage existing solutions:** Use built-in features and existing libraries before creating custom solutions

## Process

1.  **Gather Context (in priority order):**
    - **First:** Check if argument is a path to an existing markdown file (ends with .md and file exists). If yes, read and use its contents as the initial context
    - **Second:** If no argument provided, analyze the last 10 messages from chat history to extract feature requirements
    - **Third:** If argument is provided but not a file path, treat it as a prompt string and use that as the initial context
    - **Deep Analysis:** Think deeply about the underlying business problem, user needs, and system implications

2.  **Deep Thinking (Ultrathink) Before Questions:**
    Before asking questions, think deeply about:
    - What is the real problem being solved?
    - Who are all the stakeholders affected?
    - What are the technical and business constraints?
    - What are potential risks and edge cases?
    - What similar features exist and what can we learn from them?
    - What are the long-term implications of this feature?
    - What assumptions are being made?

3.  **Ask Clarifying Questions:** Before writing the PRD, the AI *must* ask clarifying questions to gather sufficient detail. The goal is to understand the "what" and "why" of the feature, not necessarily the "how" (which the developer will figure out). Make sure to provide options in letter/number lists so I can respond easily with my selections.

4.  **Deep Analysis of Answers:**
    After receiving answers, deeply analyze:
    - Contradictions or conflicts in requirements
    - Hidden dependencies or prerequisites
    - Unstated assumptions that need validation
    - Potential scalability issues
    - Security and privacy implications
    - Performance impact on existing systems
    - User experience considerations
    - Integration challenges

5.  **Generate PRD:** Based on the context (command prompt or chat history) and the user's answers to the clarifying questions, generate a PRD using the structure outlined below. Apply deep thinking to ensure requirements are:
    - Complete and unambiguous
    - Testable and measurable
    - Achievable and realistic
    - Consistent and non-conflicting
    - Traceable to business goals

6.  **Save PRD:** Save the generated document as `prd-[feature-name].md` inside the `/tasks` directory.

## Clarifying Questions (Examples)

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **Problem/Goal:** "What problem does this feature solve for the user?" or "What is the main goal we want to achieve with this feature?"
*   **Target User:** "Who is the primary user of this feature?"
*   **Core Functionality:** "Can you describe the key actions a user should be able to perform with this feature?"
*   **User Stories:** "Could you provide a few user stories? (e.g., As a [type of user], I want to [perform an action] so that [benefit].)"
*   **Acceptance Criteria:** "How will we know when this feature is successfully implemented? What are the key success criteria?"
*   **Scope/Boundaries:** "Are there any specific things this feature *should not* do (non-goals)?"
*   **Data Requirements:** "What kind of data does this feature need to display or manipulate?"
*   **Design/UI:** "Are there any existing design mockups or UI guidelines to follow?" or "Can you describe the desired look and feel?"
*   **Edge Cases:** "Are there any potential edge cases or error conditions we should consider?"

## PRD Structure

The generated PRD should include the following sections:

1.  **Introduction/Overview:** Briefly describe the feature and the problem it solves. State the goal.
2.  **Goals:** List the specific, measurable objectives for this feature.
3.  **User Stories:** Detail the user narratives describing feature usage and benefits.
4.  **Functional Requirements:** List the specific functionalities the feature must have. Use clear, concise language (e.g., "The system must allow users to upload a profile picture."). Number these requirements.
5.  **Non-Goals (Out of Scope):** Clearly state what this feature will *not* include to manage scope.
6.  **Design Considerations (Optional):** Link to mockups, describe UI/UX requirements, or mention relevant components/styles if applicable.
7.  **Technical Considerations (Optional):** Mention any known technical constraints, dependencies, or suggestions (e.g., "Should integrate with the existing Auth module").
8.  **Success Metrics:** How will the success of this feature be measured? (e.g., "Increase user engagement by 10%", "Reduce support tickets related to X").
9.  **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary reader of the PRD is a **junior developer**. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the feature's purpose and core logic.

## Output

*   **Format:** Markdown (`.md`)
*   **Location:** `/tasks/`
*   **Filename:** `prd-[feature-name].md`

## Command Usage

- `/create-prd /path/to/requirements.md` - Reads requirements from the specified markdown file (highest priority)
- `/create-prd` - Analyzes last 10 chat messages to extract feature context
- `/create-prd "feature description"` - Uses the provided prompt string as initial context (lowest priority)

## Final instructions

1. Do NOT start implementing the PRD
2. Priority order for context: markdown file > chat history > prompt string
3. When checking for markdown file: verify it ends with .md AND file exists before reading
4. Make sure to ask the user clarifying questions
5. Take the user's answers to the clarifying questions and improve the PRD
