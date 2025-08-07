# Rule: GitLab Issues Extraction Workflow

## Goal

To extract current open and in-progress issues from GitLab using API access, map them to branches/MRs with confidence levels, and prepare structured data for the branch review workflow.

## Process

1. **Access GitLab API:** Use `GITLAB_ACCESS_TOKEN` from `.env` file to authenticate
2. **Extract Issues:** Pull open and in-progress issues with their details
3. **Map to Branches/MRs:** Use multiple detection methods with confidence scoring
4. **Generate Workflow Data:** Create structured data file for branch review step
5. **Save Extraction:** Save as `issues-extraction-[date].md` in `/workflow/` directory

## GitLab API Requirements

The AI must:
- **Never modify `.env`** - only read the `GITLAB_ACCESS_TOKEN`
- **Use GitLab API v4** endpoints:
  - `GET /projects/:id/issues?state=opened&scope=all`
  - `GET /projects/:id/merge_requests?state=opened&include_related_issues=true`
  - `GET /projects/:id/repository/branches`
  - `GET /projects/:id/issues/:issue_iid/related_merge_requests`
  - `GET /projects/:id/merge_requests/:mr_iid/closes_issues`

## Association Detection Methods

Use this priority order to map issues to branches/MRs:

### 1. **Direct GitLab API Associations** (High Confidence)
```bash
# Primary method - use GitLab's built-in associations
GET /projects/:id/issues/:issue_iid/related_merge_requests
GET /projects/:id/merge_requests/:mr_iid/closes_issues
```

### 2. **Branch Name Pattern Matching** (Medium-High Confidence)
Check for these patterns in branch names:
- `feature/123-description` or `fix/123-description`
- `issue-123-description` or `task-123-description`
- `123-description` (starts with issue number)
- `#123-description` (with hash prefix)

### 3. **MR Description Analysis** (Medium Confidence)
Scan MR descriptions for issue references:
- Closing keywords: `Closes #123`, `Fixes #123`, `Resolves #123`
- Reference keywords: `Relates to #123`, `References #123`, `Part of #123`

### 4. **Fallback Detection** (Low Confidence)
- Issue description mentions branch names
- Recent commits by same author around issue creation time
- Similar naming patterns or keywords

## Data to Extract

For each issue:
- **Issue Details:** Title, description, labels, assignee, due date, milestone
- **Branch Mapping:** Associated branch name(s) with confidence level
- **MR Status:** If MR exists, get status, diff stats, and review state
- **Priority Level:** Based on labels (critical, high, medium, low)
- **Review Readiness:** Determine if ready for code review

## Output Structure

```markdown
# GitLab Issues Extraction - [DATE]

**Project:** [PROJECT_NAME]  
**GitLab URL:** [PROJECT_URL]  
**Generated:** [TIMESTAMP]

## Workflow Summary
- **Total Open Issues:** X
- **Issues with High Confidence Mapping:** Y
- **Ready for Review:** Z
- **Needs Investigation:** W

## Issues Mapped to Branches/MRs

### #[ISSUE_NUM] - [TITLE]
- **Status:** [open/in-progress/ready-for-review]
- **Priority:** [critical/high/medium/low] 
- **Assignee:** @[username]
- **Due Date:** [date]
- **Labels:** [label1, label2]
- **Branch:** `[branch-name]` ✅ (High confidence - API linked)
- **MR:** ![MR_NUM] - "[MR_TITLE]" ✅ (High confidence - closes issue)
- **Review Status:** [ready/in-progress/needs-work]
- **Description:** [brief description]

### #[ISSUE_NUM] - [TITLE]
- **Status:** [open]
- **Priority:** [medium]
- **Assignee:** @[username]
- **Branch:** `[branch-name]` ⚠️ (Medium confidence - name pattern)
- **MR:** None found
- **Review Status:** not-ready
- **Description:** [brief description]

## Confidence Levels Legend
- ✅ **High:** GitLab API association or exact name match
- ⚠️ **Medium:** Pattern match or description reference  
- ❌ **Low:** Time-based or author-based guess
- ❓ **None:** No association found

## Review Queue (Ready for @branch-review)
1. Issue #[NUM] - `[branch-name]` (High confidence)
2. Issue #[NUM] - `[branch-name]` (High confidence)

## Needs Investigation
- Issue #[NUM] - No branch/MR found
- Issue #[NUM] - Low confidence mapping

## Next Steps
Run `@branch-review #[ISSUE_NUM]` for issues in Review Queue
```

## Output

- **Format:** Markdown (`.md`)
- **Location:** `/workflow/`
- **Filename:** `issues-extraction-[YYYY-MM-DD].md`

## AI Instructions

1. **Security First:** Never log or expose access tokens
2. **Handle API Errors:** Report connection issues gracefully
3. **Map Systematically:** Use all detection methods for each issue
4. **Score Confidence:** Be transparent about association reliability
5. **Prepare for Review:** Structure data for seamless branch review workflow
6. **Check Permissions:** Verify API access before proceeding
7. **Rate Limit Aware:** Handle GitLab API rate limits appropriately

## Error Handling

- **Missing Token:** "GITLAB_ACCESS_TOKEN not found in .env file"
- **API Errors:** "GitLab API error: [details]"
- **Permission Issues:** "Insufficient GitLab permissions for project access"
- **Rate Limiting:** "GitLab API rate limit reached, please wait"

## Workflow Trigger

After successful completion, inform user:
"Issues extracted successfully! Found [X] issues with [Y] ready for review. 
- Run `@branch-review #[ISSUE_NUM]` to review specific issues
- Run `@branch-review --queue` to review all ready issues
- Check 'Needs Investigation' section for unmapped issues"

## Environment Requirements

Ensure `.env` file contains:
```
GITLAB_ACCESS_TOKEN=your_gitlab_access_token_here
GITLAB_PROJECT_ID=your_project_id_here
```
