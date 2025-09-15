# Claude Commands

A collection of custom command templates for Claude Code to streamline software development workflows.

## Overview

This repository contains markdown-based command templates that guide Claude Code through common development tasks like creating documentation, managing git commits, and processing task lists. Each template provides structured instructions to ensure consistent and high-quality outputs.

## Command Templates

### 📝 commit.md
Creates clean, professional git commits following specific conventions. Handles staging, commit message formatting, and verification without pushing to remote.

### 📋 create-prd.md
Generates detailed Product Requirements Documents (PRDs) based on user prompts or chat history. Includes clarifying questions, structured sections, and saves to `/tasks/` directory.

### ✅ generate-tasks.md
Converts PRDs into actionable task lists with parent tasks and detailed sub-tasks. Includes validation and cleanup steps, organized for junior developers.

### 🔄 process-task-list.md
Manages task list execution with strict verification requirements. Ensures tasks are completed with evidence before marking done, includes commit protocols.

### 📚 update-docs.md
Systematically reviews and updates all project documentation. Identifies outdated, redundant, or missing content and ensures consistency across all docs.

## Usage

These templates are designed to be used with Claude Code's custom command feature. Each template provides:

- Clear goals and objectives
- Step-by-step processes
- Output format specifications
- Validation requirements
- Best practices and guidelines

## Design Principles

- **Simplicity First:** Always prefer the simplest solution
- **YAGNI:** Don't add functionality until needed
- **MVP Focus:** Start with minimum viable implementation
- **No Premature Optimization:** Make it work first, optimize later
- **Leverage Existing Solutions:** Use built-in features before custom ones

## Contributing

When adding new command templates:
1. Follow the existing markdown structure
2. Include clear goals and processes
3. Specify output formats and locations
4. Add validation requirements where applicable
5. Document any prerequisites or dependencies

## License

This project is part of the Claude Code commands collection.