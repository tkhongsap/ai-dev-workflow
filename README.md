# AI Developer Workflow

A structured methodology for leveraging AI assistants to efficiently plan, document, and implement software features with consistency and quality.

## 🎯 Purpose

This repository provides a comprehensive framework for developers working with AI assistants, ensuring:
- Clear requirements documentation
- Systematic task breakdown
- Consistent implementation patterns
- Traceable development progress

## 📋 Available Workflows

### PRD-Driven Workflow
A structured three-phase approach for systematic feature development:

#### Phase 1: Requirements Documentation
**Create a Product Requirements Document (PRD)**
- Standard process: [`prd-driven-workflow/01-create-prd.md`](prd-driven-workflow/01-create-prd.md)
- Replit-specific: [`prd-driven-workflow/01-create-prd-replit.md`](prd-driven-workflow/01-create-prd-replit.md)

#### Phase 2: Task Planning
**Generate a structured task list from the PRD**
- Standard process: [`prd-driven-workflow/02-generate-tasks.md`](prd-driven-workflow/02-generate-tasks.md)
- Replit-specific: [`prd-driven-workflow/02-generate-tasks-replit.md`](prd-driven-workflow/02-generate-tasks-replit.md)

#### Phase 3: Implementation
**Execute tasks systematically**
- Standard process: [`prd-driven-workflow/03-process-task-list.md`](prd-driven-workflow/03-process-task-list.md)
- Replit-specific: [`prd-driven-workflow/03-process-tasks-replit.md`](prd-driven-workflow/03-process-tasks-replit.md)

## 📁 Repository Structure

```
ai-dev-workflow/
├── prd-driven-workflow/        # PRD-based development methodology
│   ├── 01-create-prd.md       # PRD generation guidelines
│   ├── 01-create-prd-replit.md # PRD rules for Replit environment
│   ├── 02-generate-tasks.md   # Task list creation methodology
│   ├── 02-generate-tasks-replit.md # Task generation for Replit
│   ├── 03-process-task-list.md # Task execution and management
│   └── 03-process-tasks-replit.md # Task processing for Replit
├── LICENSE                     # MIT License
├── README.md                   # This file
└── tasks/                      # Directory for PRDs and task lists (create as needed)
    ├── prd-[feature].md        # Feature requirements documents
    └── tasks-prd-[feature].md  # Corresponding task lists
```

## 🚀 Getting Started

### Prerequisites
- An AI assistant (e.g., Claude, GPT-4, or similar)
- A development environment (standard or Replit)
- Version control system (Git recommended)

### Workflow Steps

1. **Initialize the project**
   ```bash
   # Create tasks directory if it doesn't exist
   mkdir -p tasks
   ```

2. **Start with a feature idea**
   - Provide a brief description of the desired functionality
   - The AI will ask clarifying questions based on the PRD template

3. **Generate the PRD**
   - Save as `tasks/prd-[feature-name].md`
   - Include all technical specifications, constraints, and acceptance criteria

4. **Create the task list**
   - Generate from the PRD following the task generation rules
   - Save as `tasks/tasks-prd-[feature-name].md`
   - Tasks should be atomic, measurable, and ordered by dependency

5. **Implement systematically**
   - Work through tasks sequentially
   - Update task status as you progress
   - Commit changes with meaningful messages referencing task IDs

## 💡 Best Practices

### When Creating PRDs
- Be specific about technical requirements
- Include edge cases and error handling
- Define clear acceptance criteria
- Consider performance and scalability

### When Generating Tasks
- Break down complex features into atomic units
- Order tasks by dependency
- Include testing and documentation tasks
- Estimate complexity for each task

### During Implementation
- Complete one task before moving to the next
- Run tests after each significant change
- Use conventional commit messages
- Reference task IDs in commits

## 🧪 Testing Guidelines

Before committing any changes:

```bash
# For Node.js projects
npm test

# For Python projects
pytest

# For other languages, use appropriate test runners
```

Ensure all tests pass and consider adding new tests for implemented features.

## 🤝 Contributing

1. Follow the established workflow for new features
2. Maintain consistency with existing patterns
3. Document any workflow improvements
4. Submit pull requests with clear descriptions

## 📝 Commit Message Convention

Use conventional commit messages with task references:

```
feat: implement user authentication [TASK-001]
fix: resolve database connection timeout [TASK-015]
docs: update API documentation [TASK-023]
test: add unit tests for payment module [TASK-008]
```

## 🛠️ Platform-Specific Notes

### Replit Environment
The `*-replit.md` files contain platform-specific adaptations for:
- Replit's file system structure
- Environment variable management
- Database integrations
- Deployment considerations

### Standard Development
The standard rule files apply to:
- Local development environments
- Traditional CI/CD pipelines
- Self-hosted or cloud deployments

## 📄 License

This project is licensed under the [MIT License](LICENSE) - see the LICENSE file for details.

## 🔗 Additional Resources

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)

---

*This workflow framework helps maintain consistency, quality, and efficiency when working with AI assistants on software development projects.*
