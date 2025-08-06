# Agentic Task Management for Replit Development

Guidelines for autonomous task implementation in Replit environment without requiring user permission for each step.

## Agentic Task Implementation Philosophy

- **Autonomous execution:** Work through sub-tasks continuously until completion or genuine blockers
- **Replit-optimized:** Leverage Replit's workflows, environment, and deployment features
- **Performance-driven:** Validate each change against Replit constraints (memory, response time)
- **Self-validating:** Include automatic testing and health checks at each milestone

## Task Execution Protocol

### 1. Autonomous Sub-Task Processing
- **Execute sub-tasks sequentially** without user permission
- **Validate each step** using Replit's built-in tools (console logs, workflow status)
- **Auto-test performance** against targets (response time <1.5s, memory <512MB)
- **Only pause for user input** when:
  - Requiring external API keys or secrets
  - Encountering unresolvable errors after 3 attempts
  - Major architectural decisions not covered in PRD
  - Production deployment confirmation

### 2. Replit-Specific Completion Protocol
When finishing a **sub-task**:

1. **Mark completed:** Change `[ ]` to `[x]` in task list
2. **Replit validation:**
   - Check workflow status (should be "running" and healthy)
   - Test endpoints using curl or health checks
   - Verify no console errors in workflow logs
   - Confirm memory usage <512MB if applicable
3. **Performance check:**
   - Test response times for affected endpoints
   - Verify database connectivity if database-related
   - Check file count remains minimal (<10 core files)

When **all subtasks** under a parent task are complete:

1. **Run comprehensive tests:**
   ```bash
   # Test the Replit workflow health
   curl -f http://localhost:5000/health
   
   # Check performance benchmarks
   time curl -X POST http://localhost:5000/webhook \
     -H "Content-Type: application/json" \
     -d '{"test": "performance"}'
   ```

2. **Replit deployment validation:**
   - Verify Gunicorn starts successfully (<30s)
   - Check all Replit Secrets are accessible
   - Confirm PostgreSQL connection via DATABASE_URL
   - Test endpoint accessibility on port 5000

3. **Clean up and commit:**
   - Remove temporary files and debug code
   - Stage changes: `git add .`
   - Commit with conventional format:
     ```bash
     git commit -m "feat(replit): implement simplified webhook architecture" \
       -m "- Reduced from 50+ files to 5 core files" \
       -m "- Response time optimized for <1.5s target" \
       -m "- Replit deployment ready with health checks" \
       -m "Completes Task 1.0 from REPLIT_SIMPLIFIED_LINEBOT_PRD"
     ```

4. **Mark parent task complete:** `[x]`

### 3. Autonomous Error Handling
- **Auto-retry:** Up to 3 attempts for recoverable errors
- **Self-diagnose:** Use Replit console logs and workflow status
- **Smart fallbacks:** Implement alternative approaches when possible
- **Document issues:** Add notes to task list for complex problems

## Replit-Specific Validation Steps

### During Development
- **File structure check:** Ensure minimal file count maintained
- **Memory monitoring:** Track memory usage during testing
- **Workflow status:** Confirm "Start application" workflow remains healthy
- **Environment variables:** Verify all Replit Secrets are accessible

### Performance Validation
- **Response time testing:** Use `time curl` to measure endpoint performance
- **Health endpoint:** Ensure `/health` responds in <100ms
- **Database connectivity:** Test PostgreSQL connection speed
- **Concurrent request handling:** Simple load testing when applicable

### Deployment Readiness
- **Port accessibility:** Confirm app responds on port 5000
- **Gunicorn startup:** Verify server starts without errors
- **Environment isolation:** Test with clean environment variables
- **External API connectivity:** Validate Azure OpenAI and LINE API integration

## Task List Maintenance (Autonomous)

### 1. Real-Time Updates
- **Auto-update** task list after each completed sub-task
- **Add emergent tasks** discovered during implementation
- **Update estimates** based on actual implementation time
- **Track blockers** and resolution approaches

### 2. Relevant Files Management
- **Auto-update** file list as new files are created/modified
- **Remove references** to deleted files during cleanup
- **Add descriptions** for new files with their purpose
- **Track file sizes** to maintain Replit optimization

### 3. Performance Tracking
- **Log response times** for each major milestone
- **Track memory usage** during testing phases
- **Document performance improvements** achieved
- **Note any Replit-specific optimizations** applied

## AI Autonomous Instructions

When working with Replit task lists, execute autonomously:

1. **Continuous execution:** Work through sub-tasks without stopping for permission
2. **Replit integration:** Use workflow console logs for debugging
3. **Performance validation:** Test against <1.5s response time targets
4. **Self-monitoring:** Check health endpoints and system metrics
5. **Smart progression:** Move to next task when current is validated
6. **Automatic documentation:** Update task list and relevant files continuously
7. **Error resilience:** Implement fallbacks and retry logic
8. **Deployment focus:** Ensure each change maintains Replit deployment readiness

### Stopping Conditions (When to Pause)
- **Secrets required:** External API keys needed from user
- **Major errors:** Unresolvable after 3 automated attempts
- **Architecture decisions:** Not covered in existing PRD
- **Production deployment:** Final production cutover confirmation
- **External dependencies:** Third-party service configuration needed

### Success Indicators
- ✅ All sub-tasks marked complete `[x]`
- ✅ Replit workflow shows "running" status
- ✅ Health endpoint responds <100ms
- ✅ Response times meet <1.5s target
- ✅ Memory usage <512MB
- ✅ File count optimized
- ✅ All tests passing
- ✅ Clean git commit created

## Replit-Optimized Commit Messages

Use conventional commit format with Replit-specific context:

```bash
# Feature implementation
git commit -m "feat(replit): add simplified webhook processing" \
  -m "- Direct Azure OpenAI integration without service layers" \
  -m "- Response time optimized for Replit deployment" \
  -m "- Memory footprint reduced for 512MB constraint"

# Performance optimization  
git commit -m "perf(replit): optimize database connection pooling" \
  -m "- Configured for Replit PostgreSQL environment" \
  -m "- Reduced connection overhead by 60%" \
  -m "- Health check response time <50ms"

# Bug fixes
git commit -m "fix(replit): resolve Gunicorn startup timeout" \
  -m "- Fixed port binding for Replit environment" \
  -m "- Startup time reduced to <20 seconds" \
  -m "- Workflow status now stable"
```

This autonomous process enables rapid development cycles while maintaining quality and Replit deployment readiness.