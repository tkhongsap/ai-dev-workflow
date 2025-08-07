# Review-Driven Workflow

A comprehensive AI-powered code review system that integrates specialized reviewers, GitLab automation, and educational feedback to ensure high-quality code delivery.

## Overview

This workflow provides a structured approach to code review using multiple specialized AI reviewers that analyze different aspects of your code. Each reviewer focuses on specific quality dimensions, providing comprehensive feedback that helps teams maintain high standards and mentor junior developers.

## Components

### Core Orchestrator

#### `review-workflow.mdc`
The main workflow orchestrator that coordinates all review activities and integrates with GitLab.
- **Purpose**: Complete review pipeline management
- **Features**: Issue extraction, branch review coordination, GitLab integration
- **Output**: Comprehensive review reports in `/workflow/` directory

### Issue and Branch Management

#### `extract-issues.mdc`
Extracts and maps GitLab issues to their corresponding branches.
- **Trigger**: `@extract-issues`
- **Output**: `issues-extraction-[date].md`
- **Use Case**: Setting up context for branch reviews and tracking issue implementation

#### `branch-review.mdc`
Coordinates comprehensive branch and merge request reviews.
- **Trigger**: `@branch-review #123` or `@branch-review branch-name`
- **Features**: Automatically invokes relevant specialist reviewers
- **Output**: `review-[issue-num]-[date].md`

### Specialist Reviewers

#### `code-reviewer.mdc`
General code quality and pattern analysis.
- **Auto-applies to**: `*.py`, `*.ts`, `*.tsx`, `*.js`, `*.jsx`
- **Focus**: Code quality, design patterns, maintainability, best practices
- **Always Active**: Yes

#### `security-reviewer.mdc`
Security vulnerability and risk analysis.
- **Auto-applies to**: Code files, Docker files, environment configurations
- **Focus**: Security vulnerabilities, authentication, data protection, secure coding
- **Key Areas**: OWASP Top 10, input validation, authentication/authorization

#### `performance-reviewer.mdc`
Performance optimization and scalability analysis.
- **Auto-applies to**: All code files and Docker configurations
- **Focus**: Performance bottlenecks, memory management, algorithm efficiency
- **Always Active**: Yes

#### `api-reviewer.mdc`
RESTful API design and consistency review.
- **Auto-applies to**: `**/api/**`, `**/routes/**`, `**/endpoints/**`
- **Focus**: RESTful principles, endpoint consistency, API documentation
- **Key Areas**: HTTP methods, status codes, request/response structure

#### `mr-reviewer.mdc`
Educational merge request reviews for mentoring junior developers.
- **Trigger**: Manual invocation or agent request
- **Focus**: Constructive feedback, learning opportunities, best practice education
- **Features**: Interactive approval workflow, iterative revision support

## Usage Examples

### Basic Workflow

```bash
# 1. Extract GitLab issues
@extract-issues

# 2. Review a specific issue implementation
@branch-review #123

# 3. Post review to GitLab
@branch-review #123 --post
```

### Focused Reviews

```bash
# Security-focused review
@branch-review feature/authentication --security-focus

# Performance-focused review
@branch-review feature/data-processing --performance-focus

# API design review
@branch-review feature/rest-api --api-focus
```

### Educational Review

```bash
# Mentor a junior developer through MR review
@mr-reviewer https://gitlab.com/project/merge_requests/45
```

### Batch Operations

```bash
# Review multiple issues
@branch-review #123 #124 #125 --post

# Process review queue
@branch-review --queue
```

## Review Output Structure

Reviews are saved as markdown files with the following structure:

```markdown
# Review: [Issue/Branch Name]
Date: [YYYY-MM-DD]
Type: [Comprehensive/Security/Performance/API/Educational]

## Executive Summary
[High-level review summary]

## Code Quality Assessment
[Score and detailed analysis]

## Security Analysis
[Vulnerabilities and recommendations]

## Performance Review
[Bottlenecks and optimization suggestions]

## API Design Review
[RESTful compliance and consistency]

## Recommendations
[Actionable improvement items]

## GitLab Integration
[Status updates and automated actions]
```

## GitLab Integration

### Required Environment Variables

```env
GITLAB_ACCESS_TOKEN=your_gitlab_access_token
GITLAB_PROJECT_ID=your_project_id
GITLAB_URL=https://gitlab.yourdomain.com
```

### Automated Actions

- **Issue Comments**: Review summaries and action items
- **MR Feedback**: Line-by-line code comments
- **Status Updates**: Automatic issue/MR state changes
- **Label Management**: Apply review result labels
- **Approval Workflow**: Approve or request changes

## Review Quality Metrics

### Scoring System

- **Code Quality**: 1-10 scale based on maintainability, readability, and best practices
- **Security Level**: Critical/High/Medium/Low vulnerability classification
- **Performance Impact**: Identified bottlenecks with severity ratings
- **API Consistency**: Percentage compliance with RESTful standards

### Coverage Areas

- **Requirements Validation**: ✅ Met / ⚠️ Partial / ❌ Missing
- **Test Coverage**: Percentage and quality assessment
- **Documentation**: Completeness and clarity evaluation
- **Integration Status**: GitLab synchronization state

## Best Practices

### When to Use Each Reviewer

1. **Code Reviewer**: Every code change for general quality
2. **Security Reviewer**: Authentication, data handling, external integrations
3. **Performance Reviewer**: Data processing, algorithms, high-traffic endpoints
4. **API Reviewer**: New endpoints, API modifications, contract changes
5. **MR Reviewer**: Junior developer submissions, learning opportunities

### Review Frequency

- **Pre-commit**: Run focused reviews during development
- **Pre-merge**: Comprehensive review before merging
- **Post-merge**: Educational reviews for knowledge sharing

### Customization

Reviewers can be customized by modifying their MDC files:
- Adjust review criteria in the rule definitions
- Modify output formats in the report templates
- Configure auto-application patterns in the front matter

## Workflow Benefits

### Quality Assurance
- Multiple specialist perspectives on every change
- Standardized review criteria
- Automated review coordination
- Clear traceability from issue to review

### Team Efficiency
- Faster review cycles through automation
- Consistent feedback format
- Reduced manual review effort
- Parallel specialist analysis

### Developer Growth
- Educational feedback for skill development
- Pattern recognition and best practice guidance
- Constructive mentoring through reviews
- Recognition of good work

## Troubleshooting

### Common Issues

1. **GitLab Integration Fails**
   - Verify environment variables are set
   - Check access token permissions
   - Ensure project ID is correct

2. **Reviewers Not Auto-Applying**
   - Check file patterns in MDC front matter
   - Verify `alwaysApply` settings
   - Ensure file extensions match patterns

3. **Review Output Missing**
   - Check `/workflow/` directory exists
   - Verify write permissions
   - Look for error messages in console

## Future Enhancements

- AI-powered trend analysis across reviews
- Custom review templates per issue type
- Support for GitHub and Bitbucket
- Visual metrics dashboard
- Automated code fix suggestions

---

For more information about the overall AI Developer Workflow Collection, see the main [README](../README.md).