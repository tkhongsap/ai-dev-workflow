# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a collection of AI-powered developer workflows organized as markdown documentation and MDC (Markdown Component) rules. The repository contains two main workflow systems:

1. **PRD-Driven Workflow** (`/prd-driven-workflow/`): Structured approach for Product Requirements Document creation and task management
2. **Review-Driven Workflow** (`/review-driven-workflow/`): Comprehensive code review system with specialized reviewers

## Workflow Architecture

### PRD-Driven Workflow
The PRD workflow follows a three-step process:
1. **PRD Creation** (`01-create-prd.md`): Interactive PRD generation with clarifying questions
2. **Task Generation** (`02-generate-tasks.md`): Breaks down PRDs into actionable development tasks
3. **Task Processing** (`03-process-task-list.md`): Manages and executes generated tasks

Key principles:
- PRDs are saved as `prd-[feature-name].md` in `/tasks/` directory
- Targets junior developers with clear, unambiguous requirements
- Includes Replit-specific versions for cloud development

### Review-Driven Workflow
The review system uses specialized MDC rules for different review aspects:
- **`review-workflow.mdc`**: Main orchestrator for the review process
- **`extract-issues.mdc`**: GitLab issue extraction and branch mapping
- **`branch-review.mdc`**: Comprehensive branch/MR review coordination
- **Specialist Reviewers**:
  - `code-reviewer.mdc`: General code quality and patterns
  - `security-reviewer.mdc`: Security vulnerability analysis
  - `performance-reviewer.mdc`: Performance optimization
  - `api-reviewer.mdc`: RESTful API design review
  - `mr-reviewer.mdc`: Educational merge request reviews for mentoring

Review outputs are saved in `/workflow/` as `review-[issue-num]-[date].md`

## Working with This Repository

### File Organization
- Documentation workflows use `.md` extension
- Review rules use `.mdc` extension (Markdown Component format)
- Both English and Thai (ภาษาไทย) documentation versions are provided
- No build system or package manager is used (pure documentation repository)

### MDC Rule Structure
MDC files contain:
- Front matter with `description`, `globs`, and `alwaysApply` settings
- Rule activation patterns for automatic file matching
- Structured review criteria and output formats
- GitLab integration configuration

### Key Workflow Commands
The repository uses `@` prefix commands for workflow invocation:
- `@extract-issues`: Extract GitLab issues and map to branches
- `@branch-review #123`: Review specific issue implementation
- `@code-reviewer`, `@security-reviewer`, etc.: Invoke specialist reviews

## Important Notes

- This is a documentation and workflow repository, not a code project
- No traditional build, test, or lint commands exist
- Workflows are designed to be used with AI assistants for code generation and review
- GitLab integration requires `GITLAB_ACCESS_TOKEN` and `GITLAB_PROJECT_ID` environment variables
- Review artifacts and PRDs should be saved in their designated directories (`/workflow/` and `/tasks/`)