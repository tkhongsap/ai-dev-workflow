# Review-Driven Workflow Cursor Rules

## Introduction

A structured workflow for high-quality code reviews at scale. It plans scope, generates targeted tasks, executes multi-specialist analyses, and publishes actionable reports—improving code quality, knowledge sharing, and readiness for change.

## What This Workflow Does

A comprehensive workflow for conducting thorough code reviews with multiple specialist perspectives. This workflow systematically analyzes existing code through planning, task breakdown, multi-dimensional analysis, and results publication - ideal for quality assurance, security audits, performance optimization, and team knowledge sharing through structured review processes.

## Workflow at a Glance

```
Review Target → Plan Review → Generate Tasks → Execute Analysis → Publish Results
   (Define)       (Scope)       (Break Down)      (Analyze)         (Document)
      ↓              ↓               ↓                ↓                 ↓
  Code/Branch    Review Plan    Task Hierarchy   Findings Report   Issues/Actions
```

## When to Use This Workflow

✅ **Use this workflow when:**
- Conducting comprehensive code quality assessments
- Performing security audits or vulnerability analysis
- Reviewing merge requests or pull requests
- Onboarding team members through code walkthroughs
- Analyzing performance bottlenecks systematically
- Preparing for major refactoring efforts
- Documenting technical debt and improvement areas

❌ **Consider other workflows when:**
- Building new features (→ PRD-Driven Workflow)
- Designing system architecture (→ Architecture Workflow)
- Actively refactoring code (→ Refactoring Workflow)
- Generating tests (→ Test Generation Workflow)

## Overview

This workflow provides a systematic approach to conducting thorough code reviews using AI assistance. It breaks down the review process into manageable phases, from initial planning through final publication of results, ensuring comprehensive coverage and actionable outcomes.

## Workflow Structure

The review-driven workflow consists of four sequential cursor rules that guide you through a complete review process:

### 1. `01-initiate-review.mdc` - Review Planning
**Purpose**: Start a comprehensive review process for any codebase or program component  
**Trigger**: Manual invocation - `@review-driven-workflow/01-initiate-review`  
**Output**: `review-plan-[target-name].md` in `/reviews/`

**What it does:**
- Accepts review targets (repositories, branches, specific files, or program components)
- Asks clarifying questions about scope, objectives, and focus areas
- Generates a structured review plan with clear objectives and success criteria
- Defines review scope, target components, and expected deliverables

### 2. `02-generate-review-tasks.mdc` - Task Breakdown
**Purpose**: Convert review plan into detailed, actionable tasks  
**Trigger**: Manual invocation - `@review-driven-workflow/02-generate-review-tasks`  
**Output**: `review-tasks-[target-name].md` in `/reviews/`

**What it does:**
- Analyzes the review plan and assesses the current codebase
- Generates high-level review tasks (Phase 1)
- Waits for user confirmation before proceeding
- Breaks down each parent task into specific, actionable sub-tasks (Phase 2)
- Identifies relevant files and components to review
- Suggests appropriate tools and commands for analysis

### 3. `03-execute-review-process.mdc` - Review Execution
**Purpose**: Execute review tasks and generate comprehensive analysis  
**Trigger**: Auto-attached to review task files + manual invocation  
**Output**: Comprehensive review reports in both English and Thai

**What it does:**
- Processes review tasks one sub-task at a time
- Automatically leverages specialist reviewers (@code-reviewer, @security-reviewer, etc.)
- Documents findings with specific evidence and code examples
- Classifies findings by severity, category, and impact
- Generates detailed analysis reports with actionable recommendations
- Creates bilingual reports (English and Thai) when requested

### 4. `04-publish-review-results.mdc` - Results Publication
**Purpose**: Publish review results and create final documentation  
**Trigger**: Manual invocation - `@review-driven-workflow/04-publish-review-results`  
**Output**: GitHub/GitLab issues, documentation updates, archived artifacts

**What it does:**
- Formats review findings for GitHub/GitLab publication
- Creates issues for critical and high-priority findings
- Generates executive summaries for stakeholders
- Creates technical implementation guides for developers
- Archives all review materials in organized structure
- Provides follow-up recommendations and next steps

## Usage Examples

### Complete Workflow
```bash
# 1. Start review process
@review-driven-workflow/01-initiate-review

# 2. Generate detailed tasks
@review-driven-workflow/02-generate-review-tasks

# 3. Execute review analysis
@review-driven-workflow/03-execute-review-process

# 4. Publish results
@review-driven-workflow/04-publish-review-results
```

### Quick Security Review
```bash
# Focus on security analysis
@review-driven-workflow/01-initiate-review
# (Select security-focused review type)

@review-driven-workflow/02-generate-review-tasks
@review-driven-workflow/03-execute-review-process
```

### Performance Audit
```bash
# Focus on performance optimization
@review-driven-workflow/01-initiate-review
# (Select performance-focused review type)

@review-driven-workflow/02-generate-review-tasks
@review-driven-workflow/03-execute-review-process
```

## Integration with Other Workflows

### With Specialist Reviewers

The workflow automatically leverages specialist reviewers:

- **@code-reviewer**: General code quality and pattern analysis
- **@security-reviewer**: Security vulnerability assessment
- **@performance-reviewer**: Performance bottleneck identification
- **@api-reviewer**: API design and consistency review
- **@mr-reviewer**: Educational merge request reviews

### PRD-Driven Workflow Integration

**Post-Implementation Review:**
```bash
# 1. Complete PRD implementation
@prd-driven-workflow/03-process-tasks
# Feature implemented and committed

# 2. Initiate comprehensive review
@review-driven-workflow/01-initiate-review
# Review the implemented feature

# 3. Generate and execute review tasks
@review-driven-workflow/02-generate-review-tasks
@review-driven-workflow/03-execute-review-process

# 4. Create improvement tasks from findings
@review-driven-workflow/04-publish-review-results
# Findings feed back into next PRD cycle
```

### Architecture-Design Workflow Integration

**Architecture Compliance Review:**
```bash
# 1. Reference approved architecture
# /architecture/technical-design-api-gateway.md

# 2. Review implementation against design
@review-driven-workflow/01-initiate-review
# Focus: Architecture compliance

# 3. Validate design decisions in code
@review-driven-workflow/03-execute-review-process
# Check: patterns, boundaries, contracts

# 4. Report compliance status
@review-driven-workflow/04-publish-review-results
```

## Output Structure

### Review Artifacts Directory
```
/reviews/
├── [target-name]/
│   ├── review-plan-[target-name].md          # Initial review plan
│   ├── review-tasks-[target-name].md         # Detailed task breakdown
│   ├── review-report-[target-name]-en.md     # English review report
│   ├── review-report-[target-name]-th.md     # Thai review report
│   ├── executive-summary-[target-name].md    # Management summary
│   ├── implementation-guide-[target-name].md # Developer guide
│   └── artifacts/                            # Supporting materials
│       ├── github-issues/                    # Created GitHub issues
│       ├── gitlab-comments/                  # GitLab feedback
│       └── supporting-files/                 # Additional evidence
```

### Review Report Structure
Each comprehensive review report includes:

- **Executive Summary**: High-level assessment and key findings
- **Critical Issues**: Must-fix problems with immediate impact
- **High Priority Issues**: Important improvements for next iteration
- **Recommendations**: Suggestions for long-term improvements
- **Category Analysis**: Security, performance, code quality assessments
- **Metrics & Statistics**: Quantitative analysis of code quality
- **Action Items**: Prioritized next steps with time estimates
- **References**: Links to best practices and resources

## Bilingual Support

The workflow supports generating reports in both English and Thai:

- **English Reports**: Technical accuracy with industry-standard terminology
- **Thai Reports**: Culturally appropriate translations maintaining technical precision
- **Code Examples**: Preserved in original language with translated explanations
- **Best Practices**: Referenced to both international and local standards

## Key Features

### Systematic Approach
- **Structured Process**: Four-phase workflow ensures comprehensive coverage
- **User Control**: Confirmation points prevent runaway analysis
- **Incremental Progress**: One task at a time with clear completion criteria

### Comprehensive Analysis
- **Multi-Domain Review**: Security, performance, code quality, architecture
- **Evidence-Based**: Specific file references, line numbers, code examples
- **Actionable Recommendations**: Clear fix instructions with estimated effort

### Integration Ready
- **GitHub/GitLab**: Direct issue creation and comment posting
- **Existing Tools**: Leverages specialist reviewers and analysis tools
- **Documentation**: Automatic updates to repository documentation

### Quality Assurance
- **Consistent Standards**: Standardized review criteria and classifications
- **Measurable Outcomes**: Quality scores and improvement metrics
- **Follow-up Planning**: Next review scheduling and progress tracking

## Best Practices

### Review Planning
1. Define clear objectives before starting - what are you trying to improve?
2. Scope reviews appropriately - comprehensive for releases, focused for sprints
3. Include the right stakeholders - developers, architects, security team
4. Set realistic timelines - allow time for fixes before deadlines
5. Document review context - why this review, why now?

### Task Generation  
1. Balance breadth and depth - cover critical paths thoroughly
2. Prioritize by risk and impact - security and performance first
3. Make tasks measurable - "review authentication" vs "verify OAuth implementation"
4. Include validation steps - how to verify findings are addressed
5. Set clear completion criteria - what constitutes "done"

### Review Execution
1. One finding at a time - provide full context and evidence
2. Be constructive - suggest solutions, not just problems
3. Use concrete examples - show actual code, not theoretical issues
4. Classify appropriately - don't inflate severity for attention
5. Track patterns - recurring issues indicate systemic problems

### Results Publication
1. Tailor communication to audience - technical for devs, summary for managers
2. Make findings actionable - include fix instructions and effort estimates
3. Create trackable items - use issue templates for consistency
4. Follow up on resolutions - verify fixes address root causes
5. Archive for learning - build institutional knowledge

### Quality Control
1. Validate findings before publishing - reduce false positives
2. Cross-reference with past reviews - track improvement trends
3. Get developer feedback - are findings helpful and accurate?
4. Measure impact - do reviews lead to better code?
5. Iterate and improve - refine process based on results

## Environment Setup

### Required Environment Variables
```env
# GitHub Integration (optional)
GITHUB_ACCESS_TOKEN=your_github_token_here
GITHUB_REPOSITORY=owner/repo-name

# GitLab Integration (optional)
GITLAB_ACCESS_TOKEN=your_gitlab_token_here
GITLAB_PROJECT_ID=your_project_id_here
GITLAB_URL=https://gitlab.yourdomain.com
```

### Directory Structure
Ensure these directories exist in your project:
```
/reviews/          # Review artifacts and reports
/workflow/         # Integration with existing review-driven-workflow
```

## Comparison with PRD-Driven Workflow

| Aspect | PRD-Driven Workflow | Review-Driven Workflow |
|--------|-------------------|----------------------|
| **Purpose** | Feature development | Code analysis & review |
| **Input** | User requirements | Existing codebase |
| **Process** | Requirements → Tasks → Implementation | Planning → Tasks → Analysis → Publishing |
| **Output** | Working features | Review reports & recommendations |
| **Focus** | Building new functionality | Improving existing code |
| **Timeline** | Development cycle | Review & improvement cycle |

## Performance Metrics

Track workflow effectiveness with these metrics:

### Process Metrics
- Time from review initiation to final report
- Number of findings per 1000 lines of code
- Percentage of automated vs manual analysis
- Review coverage (% of codebase reviewed)

### Quality Metrics  
- Critical findings caught before production
- False positive rate in findings
- Finding resolution rate within sprint
- Repeat issue rate in subsequent reviews

### Team Metrics
- Developer agreement with findings (survey)
- Time saved through automated reviews
- Knowledge transfer from review documentation
- Code quality improvement over time

### Business Metrics
- Reduced production incidents
- Decreased security vulnerabilities
- Performance improvements achieved
- Technical debt reduction rate

## Troubleshooting

### Common Issues and Solutions

**Issue**: Review takes too long to complete  
**Solution**: Focus on changed files only, limit scope to critical paths, use sampling for large codebases

**Issue**: Too many findings to address  
**Solution**: Prioritize by severity, focus on security/performance first, create phased improvement plan

**Issue**: Findings are too generic or obvious  
**Solution**: Provide specific review objectives, focus on business-critical aspects, skip basic linting issues

**Issue**: Team doesn't act on review findings  
**Solution**: Create actionable tickets, assign owners, include effort estimates, track resolution metrics

**Issue**: Reviews miss important issues  
**Solution**: Use multiple specialist reviewers, include domain experts, validate against past incidents

**Issue**: Report format doesn't suit stakeholders  
**Solution**: Customize executive summary, use visual metrics, provide technical appendix separately

**Issue**: Integration with GitHub/GitLab fails  
**Solution**: Check token permissions, verify API rate limits, use manual issue creation as fallback

**Issue**: Bilingual reports have quality issues  
**Solution**: Review technical terms separately, maintain glossary, have native speakers validate

## Future Enhancements

Planned improvements for the workflow:

- **Automated Scheduling**: Periodic review triggers based on code changes
- **Trend Analysis**: Track quality metrics over time
- **Custom Templates**: Project-specific review criteria and formats
- **Integration Expansion**: Support for additional platforms (Bitbucket, Azure DevOps)
- **AI Learning**: Improve recommendations based on team feedback and resolution patterns

---

**Review-Driven Workflow**: Systematic code analysis for continuous quality improvement and team knowledge sharing.

For more information about the overall AI Developer Workflow Collection, see the main [README](../../README.md).
