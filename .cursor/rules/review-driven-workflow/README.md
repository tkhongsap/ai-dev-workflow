# Review-Driven Workflow Cursor Rules

A comprehensive set of cursor rules that implement a structured code review workflow, similar to the PRD-driven workflow but focused on analyzing and reviewing existing codebases, programs, and components.

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

## Integration with Existing Reviewers

The workflow seamlessly integrates with existing specialist reviewers:

- **@code-reviewer**: General code quality and pattern analysis
- **@security-reviewer**: Security vulnerability assessment
- **@performance-reviewer**: Performance bottleneck identification
- **@api-reviewer**: API design and consistency review
- **@mr-reviewer**: Educational merge request reviews

These specialist reviewers are automatically invoked during the execution phase based on the type of analysis being performed.

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

### When to Use Each Phase

1. **Initiate Review**: 
   - Before major releases or deployments
   - After significant feature additions
   - For security audits or compliance checks
   - When onboarding new team members

2. **Generate Tasks**:
   - When you need structured analysis approach
   - For complex codebases requiring systematic review
   - When multiple review aspects need coordination

3. **Execute Review**:
   - For thorough, evidence-based analysis
   - When you need detailed findings with specific recommendations
   - For generating comprehensive documentation

4. **Publish Results**:
   - When findings need to be tracked as issues
   - For stakeholder communication and reporting
   - When creating permanent documentation records

### Customization Options

- **Review Depth**: Adjust based on project criticality and timeline
- **Focus Areas**: Emphasize specific aspects (security, performance, etc.)
- **Output Format**: Customize report structure for different audiences
- **Language**: Generate reports in English, Thai, or both
- **Integration**: Configure GitHub/GitLab publishing preferences

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

## Success Metrics

Track these metrics to measure workflow effectiveness:

- **Review Completion Rate**: Percentage of initiated reviews that reach publication
- **Finding Resolution**: How many identified issues get addressed
- **Quality Improvement**: Measurable improvements in subsequent reviews
- **Team Adoption**: Usage frequency and team feedback
- **Time Efficiency**: Average time from initiation to publication

## Troubleshooting

### Common Issues

1. **Review Scope Too Broad**
   - Break large codebases into smaller, focused reviews
   - Use specific review types (security-only, performance-only)
   - Review critical paths or recent changes first

2. **Specialist Reviewers Not Available**
   - Ensure existing reviewer files are in correct location
   - Check file permissions and cursor rule activation
   - Fall back to general analysis if specialists unavailable

3. **Publishing Failures**
   - Verify environment variables are correctly set
   - Check API permissions for GitHub/GitLab
   - Validate network connectivity and rate limits

4. **Report Quality Issues**
   - Ensure review tasks are specific and actionable
   - Provide clear context and objectives in review plan
   - Use appropriate review depth for project complexity

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
