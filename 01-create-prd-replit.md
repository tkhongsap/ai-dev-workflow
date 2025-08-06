# Rule: Generating a Product Requirements Document (PRD) for Replit Development

## Goal

To guide an AI assistant in creating a detailed Product Requirements Document (PRD) in Markdown format, specifically tailored for development and deployment on the Replit platform. The PRD should be clear, actionable, and suitable for a junior developer to understand and implement the feature within Replit's environment and constraints.

## Process

1. **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2. **Ask Clarifying Questions:** Before writing the PRD, the AI *must* ask clarifying questions to gather sufficient detail. The goal is to understand the "what" and "why" of the feature, not necessarily the "how" (which the developer will figure out). Make sure to provide options in letter/number lists so I can respond easily with my selections.
3. **Generate PRD:** Based on the initial prompt and the user's answers to the clarifying questions, generate a PRD using the structure outlined below.
4. **Save PRD:** Save the generated document as `prd-[feature-name].md` inside the `/tasks` directory.

## Replit-Specific Clarifying Questions

The AI should adapt its questions based on the prompt, but here are Replit-specific areas to explore:

### Core Feature Questions
* **Problem/Goal:** "What problem does this feature solve for the user?" or "What is the main goal we want to achieve with this feature?"
* **Target User:** "Who is the primary user of this feature?"
* **Core Functionality:** "Can you describe the key actions a user should be able to perform with this feature?"
* **User Stories:** "Could you provide a few user stories? (e.g., As a [type of user], I want to [perform an action] so that [benefit].)"

### Replit Platform Questions
* **Deployment Type:** "Should this be deployed as:
  a) A web application (Flask/FastAPI)
  b) A webhook service (like LINE Bot)
  c) A background service/API
  d) A static site
  e) Other (specify)"

* **Database Requirements:** "What data storage needs does this feature have:
  a) PostgreSQL database (for complex relational data)
  b) Simple file storage (JSON/CSV files)
  c) No persistent storage needed
  d) External database/API integration"

* **Performance Expectations:** "What are the performance requirements:
  a) Real-time responses (<500ms)
  b) Standard web responses (<2s)
  c) Background processing (no time constraint)
  d) Batch processing (minutes/hours acceptable)"

* **External Services:** "Does this feature require integration with:
  a) Third-party APIs (OpenAI, payment gateways, etc.)
  b) Webhook providers (LINE, Discord, Slack, etc.)
  c) File upload/storage services
  d) Email/SMS services
  e) No external integrations"

### Technical Scope Questions
* **Tech Stack Preference:** "Preferred technology stack:
  a) Python (Flask/FastAPI)
  b) Node.js (Express)
  c) HTML/CSS/JavaScript (static)
  d) Other (specify)"

* **Security Requirements:** "What security considerations are needed:
  a) User authentication/authorization
  b) API key management (secrets)
  c) Data encryption
  d) Rate limiting
  e) Public access (no security needed)"

* **Replit Workflow:** "How should this run on Replit:
  a) Always-on web server
  b) Run on-demand
  c) Scheduled tasks
  d) Development/testing only"

## PRD Structure for Replit

The generated PRD should include the following sections:

1. **Introduction/Overview:** Briefly describe the feature and the problem it solves. State the goal.

2. **Goals:** List the specific, measurable objectives for this feature.

3. **User Stories:** Detail the user narratives describing feature usage and benefits.

4. **Functional Requirements:** List the specific functionalities the feature must have. Use clear, concise language (e.g., "The system must allow users to upload a profile picture."). Number these requirements.

5. **Replit Deployment Specifications:**
   - **Platform Type:** Web app, webhook service, API, etc.
   - **Port Configuration:** Default port requirements (e.g., 5000 for Flask, 3000 for Node.js)
   - **Workflow Command:** The command to start the application (e.g., `python main.py`, `npm start`)
   - **Dependencies:** Required packages and how to install them
   - **Environment Variables:** Required secrets and configuration

6. **Database & Storage Requirements:**
   - **Database Type:** PostgreSQL, file-based, or external
   - **Schema Design:** Tables/collections needed (if applicable)
   - **Data Migration:** How to handle existing data
   - **Backup/Recovery:** Data persistence requirements

7. **Performance Requirements:**
   - **Response Time Targets:** Expected performance benchmarks
   - **Resource Constraints:** Memory/CPU limitations on Replit
   - **Scalability Needs:** Expected load and growth requirements
   - **Monitoring:** How to track performance metrics

8. **External Integrations:**
   - **APIs Required:** Third-party services and their purposes
   - **Authentication:** API keys, OAuth, webhook secrets needed
   - **Rate Limits:** Understanding of external service limitations
   - **Error Handling:** How to handle external service failures

9. **Security & Configuration:**
   - **Secrets Management:** What API keys/secrets are needed
   - **Access Control:** Who can access the feature
   - **Data Privacy:** How sensitive data is handled
   - **CORS/Headers:** Web security configurations needed

10. **Non-Goals (Out of Scope):** Clearly state what this feature will *not* include to manage scope.

11. **Replit Development Considerations:**
    - **File Structure:** Recommended project organization
    - **Replit Features Used:** Database, secrets, deployments, etc.
    - **Testing Strategy:** How to test within Replit environment
    - **Debugging:** Console logging and error handling approach

12. **Success Metrics:** How will the success of this feature be measured? Include both technical metrics (response time, uptime) and business metrics.

13. **Deployment Checklist:**
    - [ ] Dependencies installed
    - [ ] Environment variables configured
    - [ ] Database schema created (if needed)
    - [ ] External API keys tested
    - [ ] Health check endpoint implemented
    - [ ] Error handling tested
    - [ ] Ready for Replit deployment

14. **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary reader of the PRD is a **junior developer working in Replit**. Therefore, requirements should be explicit, unambiguous, and account for Replit's specific environment, tools, and constraints. Provide enough detail for them to understand both the feature's purpose and how to implement it within Replit's platform.

## Replit-Specific Considerations

When generating PRDs, always consider:

- **Resource Limitations:** Replit has memory and CPU constraints
- **Always-On vs On-Demand:** Whether the service needs to run continuously
- **Database Options:** PostgreSQL is available, but consider if simpler storage suffices
- **Deployment Simplicity:** Replit's one-click deployment capabilities
- **Environment Variables:** How to securely manage API keys and secrets
- **Monitoring:** Built-in health checks and logging approaches
- **Development Workflow:** How to test and iterate within Replit

## Output

* **Format:** Markdown (`.md`)
* **Location:** `/tasks/`
* **Filename:** `prd-[feature-name].md`
* **Update replit.md:** Add entry to Architecture Decisions Log with date and brief description

## Final Instructions

1. Do NOT start implementing the PRD
2. Make sure to ask the user clarifying questions, especially Replit-specific ones
3. Take the user's answers to the clarifying questions and improve the PRD
4. Ensure all Replit deployment considerations are addressed
5. Include realistic performance expectations for Replit environment
6. Consider both development and production deployment scenarios

## Example Replit Tech Stacks

**Flask Web Application:**
- Dependencies: flask, gunicorn, requests
- Workflow: `gunicorn --bind 0.0.0.0:5000 main:app`
- Database: PostgreSQL with SQLAlchemy
- Secrets: API keys via environment variables

**Node.js API:**
- Dependencies: express, cors, axios
- Workflow: `npm start` or `node server.js`
- Database: PostgreSQL or JSON files
- Secrets: dotenv for environment variables

**Webhook Service:**
- Dependencies: flask/express + webhook SDK
- Workflow: Always-on server for webhook receiving
- Database: Optional, depends on logging needs
- Secrets: Webhook verification tokens

Remember: Replit optimizes for rapid development and deployment. Prioritize simplicity and leverage Replit's built-in features whenever possible.
