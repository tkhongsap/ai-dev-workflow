# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a collection of AI-powered developer workflows organized as markdown documentation and MDC (Markdown Component) rules. The repository provides **five comprehensive workflow systems** designed for different phases of software development, available in two formats:

1. **Root directories** (`/prd-driven-workflow/`, `/review-driven-workflow/`): Markdown guides for general AI assistants
2. **Cursor rules** (`.cursor/rules/`): MDC-formatted rules optimized for Cursor IDE integration

## Architecture: Dual-Format Workflow System

### Root Workflow Directories (Markdown Format)
General-purpose workflow documentation designed for use with any AI assistant:

- **`/prd-driven-workflow/`**: Requirements → Tasks → Implementation
  - `01-create-prd.md`, `02-generate-tasks.md`, `03-process-task-list.md`
  - Includes Replit-specific variants (`*-replit.md`)

- **`/review-driven-workflow/`**: Comprehensive code review with specialist reviewers
  - Contains `.mdc` files: `review-workflow.mdc`, `extract-issues.mdc`, `branch-review.mdc`
  - Specialist reviewers: `code-reviewer.mdc`, `security-reviewer.mdc`, `performance-reviewer.mdc`, `api-reviewer.mdc`, `mr-reviewer.mdc`

### Cursor Rules Directory (`.cursor/rules/`)
MDC-formatted workflow rules for Cursor IDE with auto-apply capabilities and glob patterns:

1. **`architecture-design-workflow/`**: System architecture design and documentation
   - 4 rules: requirements → options → design → signoff

2. **`prd-driven-workflow/`**: Feature development from requirements
   - 3 rules: create PRD → generate tasks → process tasks

3. **`refactoring-tech-debt-workflow/`**: Code refactoring and technical debt management
   - Rules for systematic refactoring processes

4. **`review-driven-workflow/`**: Multi-phase code review execution
   - 4 rules: initiate → generate tasks → execute → publish

5. **`test-generation-workflow/`**: Automated test creation and maintenance
   - 4 rules: analyze → generate cases → create plan → execute/maintain

**Total**: 19 MDC rule files across 5 workflow systems

### Claude Code Integration (`.claude/`)

The `.claude/` directory contains Claude Code-specific configurations:

**Agents** (`.claude/agents/` - 11 specialized agents):
- **PRD System**: `prd-creator.md`, `prd-task-generator.md`, `prd-task-processor.md`
- **Review System**: `review-planner.md`, `review-task-generator.md`, `review-executor.md`, `review-publisher.md`
- **Specialist Reviewers**: `review-api-reviewer.md`, `review-performance-reviewer.md`, `review-security-reviewer.md`, `review-mr-reviewer.md`

**Commands** (`.claude/commands/` - 4 slash commands):
- `/branch-review` - Review specific branch or issue
- `/context` - Manage context and conversation state
- `/extract-issues` - Extract GitLab issues and map to branches
- `/parallel` - Execute multiple tasks in parallel

**Skills** (`.claude/skills/` - Reusable capabilities):
- `english-to-thai-cultural-translation/` - Culturally-aware Thai translation
  - Structure: `[skill-name]/SKILL.md` (proper Claude Code format)
  - Invoked when translating content or adapting for Thai audiences

## Workflow Architecture Details

### PRD-Driven Workflow
**Purpose**: Transform ideas into shipped features through structured planning

Three-phase process:
1. **PRD Creation**: Interactive requirements gathering with clarifying questions
2. **Task Generation**: Codebase-aware hierarchical task breakdown
3. **Task Processing**: Systematic execution with testing and git integration

**Key outputs**:
- PRDs: `/tasks/prd-[feature-name].md`
- Tasks: `/tasks/tasks-prd-[feature-name].md`
- Commits: Conventional commit messages with proper testing

### Review-Driven Workflow
**Purpose**: Multi-specialist code analysis for quality assurance

Four-phase process:
1. **Initiate Review**: Define scope and create review plan
2. **Generate Tasks**: Break down into actionable review items
3. **Execute Process**: Run specialist reviewers and document findings
4. **Publish Results**: Create GitHub/GitLab issues and reports

**Key outputs**:
- Review plans: `/reviews/[target]/review-plan-*.md`
- Findings: `/reviews/[target]/review-report-*-en.md` (English), `*-th.md` (Thai)
- Artifacts: `/reviews/[target]/artifacts/`

### Specialist Reviewers
Each reviewer focuses on specific quality dimensions:
- **code-reviewer**: Patterns, maintainability, best practices
- **security-reviewer**: OWASP vulnerabilities, secure coding
- **performance-reviewer**: Bottlenecks, optimization opportunities
- **api-reviewer**: RESTful design, consistency, documentation
- **mr-reviewer**: Educational feedback for mentoring junior developers

## Working with This Repository

### File Organization

**Workflow Documentation** (`.md` files):
- Root `/prd-driven-workflow/` and `/review-driven-workflow/`: General AI assistant guides
- Includes Replit variants for cloud development environments
- README files provide workflow overviews and usage instructions

**Cursor Rules** (`.mdc` files):
- `.cursor/rules/[workflow-name]/`: Cursor IDE-specific implementations
- Each rule has numbered prefixes indicating execution order (01, 02, 03, 04)
- Front matter controls activation: `alwaysApply`, `globs` patterns, `description`

**Claude Code Configuration**:
- `.claude/agents/`: Specialized agent definitions (11 agents)
- `.claude/commands/`: Slash command implementations (4 commands)
- `.claude/skills/[skill-name]/SKILL.md`: Reusable skill capabilities

**Output Directories**:
- `/tasks/`: PRD documents and task lists
- `/reviews/`: Review plans, reports, and artifacts
- `/workflow/`: Legacy review outputs (preserved for compatibility)
- `/architecture/`: Architecture design documents (when using architecture workflow)

### MDC Rule Structure

MDC files use YAML front matter for configuration:

```yaml
---
description: "Rule purpose and behavior"
globs: ["**/*.py", "**/*.js"]  # Auto-apply to matching files
alwaysApply: false             # Manual invocation only
---
```

**Activation modes**:
- `alwaysApply: true` - Active in all contexts
- `globs: ["pattern"]` - Auto-attach when files match patterns
- Manual invocation - Explicit `@workflow-name/rule-name` calls

### Using Workflows

**Cursor IDE** (recommended for `.mdc` workflows):
```bash
@prd-driven-workflow/01-create-prd
@review-driven-workflow/03-execute-review-process
@architecture-design-workflow/02-propose-architecture-options
```

**General AI Assistants** (use `.md` guides):
- Reference files: `/prd-driven-workflow/01-create-prd.md`
- Follow step-by-step instructions in each guide
- AI will use the workflow as a prompt template

**Claude Code Slash Commands**:
```bash
/extract-issues                    # Extract GitLab issues
/branch-review #123                # Review specific issue
/branch-review feature/auth        # Review specific branch
/context                           # Manage conversation context
/parallel                          # Execute tasks in parallel
```

**Invoking Skills**:
- Skills auto-activate based on `description` triggers
- Example: Mentioning "translate to Thai" activates `english-to-thai-cultural-translation`
- Skills are context-aware and maintain conversation state

### Bilingual Support

The repository provides comprehensive English and Thai (ภาษาไทย) documentation:

- **README files**: Available in both languages (`README.md`, `README-TH.md`)
- **Review reports**: Generated in parallel (`*-en.md`, `*-th.md`)
- **Thai translation skill**: Ensures cultural appropriateness and proper formality levels
- **Technical terms**: Preserved in English with Thai explanations where appropriate

### Integration with External Systems

**GitLab Integration** (optional):
```bash
export GITLAB_ACCESS_TOKEN="your_token"
export GITLAB_PROJECT_ID="your_project_id"
export GITLAB_URL="https://gitlab.yourdomain.com"  # Optional, defaults to gitlab.com
```

**GitHub Integration** (optional):
```bash
export GITHUB_ACCESS_TOKEN="your_token"
export GITHUB_REPOSITORY="owner/repo-name"
```

These credentials enable:
- Automatic issue extraction from project boards
- Posting review findings as comments
- Creating issues for critical findings
- Linking code reviews to merge requests

## Important Notes

**Repository Nature**:
- Pure documentation repository - no executable code or build system
- No package.json, requirements.txt, or other dependency files
- No test, lint, or build commands exist
- Workflows are meant to be used *on other projects*, not on this repository itself

**Workflow Selection**:
- Use **PRD-Driven** for new feature development from requirements
- Use **Review-Driven** for quality assurance and code analysis
- Use **Architecture-Design** for system design before implementation
- Use **Test-Generation** for creating comprehensive test suites
- Use **Refactoring-Tech-Debt** for systematic code improvements

**Output Locations**:
- Always save PRDs to `/tasks/` directory
- Review outputs go to `/reviews/[target-name]/`
- Architecture docs go to `/architecture/`
- Maintain consistent naming: `prd-[feature].md`, `review-plan-[target].md`

**File Naming Conventions**:
- PRDs: `prd-[feature-name].md`
- Tasks: `tasks-prd-[feature-name].md`
- Review plans: `review-plan-[target].md`
- Review reports: `review-report-[target]-en.md` (English), `review-report-[target]-th.md` (Thai)
- Architecture: `technical-design-[component].md`

**Workflow Integration**:
- PRD-Driven can feed into Review-Driven (implement → review → refine)
- Architecture-Design should precede PRD-Driven for complex features
- Review-Driven findings can generate new PRDs for improvements
- All workflows respect bilingual documentation requirements