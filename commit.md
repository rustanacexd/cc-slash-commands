# Rule: Creating Git Commits

## Goal

To create clean, professional git commits following specific conventions without pushing to remote.

## Git Commit Rules

- Author should be: Rustan Corpuz <rustanacexd@gmail.com>
- Do NOT add "🤖 Generated with [Claude Code](https://claude.ai/code)" to commit messages
- Do NOT add "Co-Authored-By: Claude <noreply@anthropic.com>" to commit messages
- Do not do git push - only create the commit locally
- Keep commit messages clean and professional without AI generation markers

## Process

1. **Check Status:** Run `git status` to see all changes
2. **Review Changes:** Run `git diff` to understand what's being committed
3. **Stage Files:** Add appropriate files to staging area
4. **Create Commit:** Write a clear, concise commit message that describes the changes
5. **Verify:** Confirm the commit was created successfully

## Commit Message Guidelines

- Use present tense ("Add feature" not "Added feature")
- Keep the first line under 50 characters
- Capitalize the first letter
- No period at the end of the subject line
- Use the imperative mood in the subject line
- If needed, add a blank line and then a more detailed explanation

## Example Usage

When invoked with `/commit`, the assistant should:
1. Review the current changes
2. Create an appropriate commit message based on the changes
3. Execute the commit (without pushing)
4. Confirm successful commit creation