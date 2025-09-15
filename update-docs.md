# Update Documentation

Systematically review and update all documentation files in this project. Your goal is to ensure documentation is current, accurate, and valuable.

## Documentation Review Process

### 1. Discovery Phase
First, identify all documentation files in the project:
- README files (README.md, README.txt, etc.)
- Documentation directories (docs/, documentation/, wiki/, etc.)
- API documentation
- Configuration documentation (*.md files near config files)
- Code comments and docstrings
- CHANGELOG, CONTRIBUTING, LICENSE files
- Any other markdown or text files serving as documentation

### 2. Analysis Phase
For each documentation file found, evaluate:

**Outdated Content:**
- Commands or scripts that no longer work
- References to deprecated features or removed code
- Version numbers that are out of date
- Installation instructions that don't match current requirements
- API endpoints or methods that have changed
- Configuration options that have been modified
- Screenshots or diagrams showing old UI/architecture

**Redundant Content:**
- Information duplicated across multiple files
- Overlapping guides that could be consolidated
- Repeated setup instructions
- Multiple files covering the same topic

**Obsolete Content:**
- Documentation for features that no longer exist
- References to tools or dependencies no longer used
- Guides for workflows that have been replaced
- Historical information with no current relevance

**Missing Content:**
- New features without documentation
- Undocumented configuration options
- Missing setup or installation steps
- Absent troubleshooting guides
- Lack of examples or use cases

### 3. Update Actions

**For Outdated Content:**
- Update version numbers to current versions
- Correct commands and code examples to working versions
- Update file paths and directory structures
- Refresh API documentation with current endpoints
- Update dependency lists and requirements
- Fix broken links and references

**For Redundant Content:**
- Identify the most comprehensive version
- Merge unique valuable content from duplicates
- Create single source of truth
- Add cross-references where appropriate
- Remove or redirect duplicate files

**For Obsolete Content:**
- Remove documentation for non-existent features
- Delete references to deprecated tools
- Clean up historical information unless it serves a specific purpose
- Archive if historically important but not currently relevant

**For Missing Content:**
- Document any undocumented features found in code
- Add setup instructions if missing
- Create basic usage examples
- Document configuration options

### 4. Quality Improvements

**Consistency:**
- Ensure consistent formatting across all docs
- Standardize code example styles
- Align heading hierarchies
- Unify terminology and naming conventions

**Clarity:**
- Simplify complex explanations
- Add examples where helpful
- Break up large blocks of text
- Improve section organization

**Completeness:**
- Ensure README has: description, installation, usage, configuration
- Verify all features are documented
- Check that troubleshooting covers common issues

### 5. Validation

**Test all:**
- Commands and scripts in documentation
- Installation procedures
- Code examples
- Configuration samples
- Links and references

## Execution Instructions

1. Start by scanning the entire project for documentation files
2. Create a plan listing all files to be updated with specific changes needed
3. Systematically update each file based on the analysis
4. Consolidate redundant documentation
5. Remove obsolete content
6. Add any critical missing documentation
7. Validate that all updated documentation is accurate and working

## Important Notes

- Preserve important historical information in CHANGELOG or history sections
- Maintain backwards compatibility notes where relevant
- Keep documentation style consistent with project conventions
- Don't remove documentation without understanding its purpose
- Test any commands or code examples before finalizing
- Consider the target audience (developers, users, contributors)

## Output

After completing the updates, provide a summary of:
- Files updated with key changes
- Files consolidated or removed
- New documentation created
- Any documentation issues that need human review