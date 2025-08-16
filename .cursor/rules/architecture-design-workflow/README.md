# Architecture & Design Workflow Cursor Rules

A comprehensive, AI-assisted workflow for designing robust, scalable system architectures before implementation. This workflow provides systematic guidance from requirements gathering through technical design and stakeholder sign-off, ensuring well-architected solutions that meet business and technical needs.

## Overview

This workflow provides a systematic approach to architecture design using AI assistance, breaking down the complex process of system architecture into manageable phases with clear deliverables, validation gates, and stakeholder involvement.

## Workflow Structure

The architecture-design workflow consists of four sequential phases that guide you through a complete architecture design process:

### 1. `01-define-architecture-requirements.mdc` - Requirements Gathering
**Purpose**: Capture comprehensive business, technical, and operational requirements  
**Trigger**: Manual invocation - `@architecture-design-workflow/01-define-architecture-requirements`  
**Output**: `architecture-requirements-[TARGET_NAME].md` in `/architecture/`

**What it does:**
- Conducts structured requirements gathering through guided questionnaires
- Captures business goals, success metrics, and stakeholder needs
- Documents non-functional requirements (NFRs) with measurable targets
- Identifies constraints, risks, and assumptions
- Validates requirements completeness and consistency

### 2. `02-propose-architecture-options.mdc` - Options Generation
**Purpose**: Generate and compare viable architecture alternatives  
**Trigger**: Manual invocation - `@architecture-design-workflow/02-propose-architecture-options`  
**Output**: `architecture-options-[TARGET_NAME].md` in `/architecture/`

**What it does:**
- Generates 2-3 distinct architecture options based on requirements
- Creates comprehensive diagrams (context, container, sequence) for each option
- Provides detailed trade-off analysis and comparison matrix
- Includes risk assessment and implementation considerations
- Facilitates informed decision-making with clear evaluation criteria

### 3. `03-create-technical-design.mdc` - Technical Design
**Purpose**: Create implementation-ready technical design document  
**Trigger**: Manual invocation - `@architecture-design-workflow/03-create-technical-design`  
**Output**: `technical-design-[TARGET_NAME].md` in `/architecture/`

**What it does:**
- Translates selected option into comprehensive Technical Design Document (TDD)
- Specifies components, interfaces, data models, and API contracts
- Addresses security, performance, deployment, and operational concerns
- Includes migration strategies and rollback procedures
- Provides implementation roadmap with quality gates

### 4. `04-architecture-signoff-and-readiness.mdc` - Review & Approval
**Purpose**: Facilitate stakeholder review and formal architecture approval  
**Trigger**: Manual invocation - `@architecture-design-workflow/04-architecture-signoff-and-readiness`  
**Output**: `architecture-signoff-[TARGET_NAME].md` and ADR files in `/architecture/adr/`

**What it does:**
- Coordinates comprehensive design reviews with all stakeholders
- Generates role-specific checklists for thorough evaluation
- Creates Architecture Decision Records (ADRs) for key choices
- Validates implementation readiness and risk mitigation
- Produces formal sign-off documentation and governance framework

## Usage Examples

### Complete Workflow
```bash
# 1. Gather and document requirements
@architecture-design-workflow/01-define-architecture-requirements

# 2. Generate and compare architecture options
@architecture-design-workflow/02-propose-architecture-options

# 3. Create detailed technical design
@architecture-design-workflow/03-create-technical-design

# 4. Conduct review and obtain sign-off
@architecture-design-workflow/04-architecture-signoff-and-readiness
```

### Focused Architecture Reviews
```bash
# Requirements-focused session
@architecture-design-workflow/01-define-architecture-requirements
# (Focus on NFR clarification and constraint validation)

# Options evaluation workshop
@architecture-design-workflow/02-propose-architecture-options
# (Collaborative option selection and trade-off analysis)

# Technical deep-dive
@architecture-design-workflow/03-create-technical-design
# (Detailed implementation planning)
```

### Iterative Design Process
```bash
# Initial architecture exploration
@architecture-design-workflow/01-define-architecture-requirements
@architecture-design-workflow/02-propose-architecture-options

# Refine based on feedback, then proceed
@architecture-design-workflow/03-create-technical-design
@architecture-design-workflow/04-architecture-signoff-and-readiness
```

## Integration with Other Workflows

### PRD-Driven Workflow Integration

**PRD → Architecture Design:**
```bash
# 1. Start with PRD for complex feature
@prd-driven-workflow/01-create-prd
# Creates: /tasks/prd-user-authentication.md

# 2. Generate architecture requirements from PRD
@architecture-design-workflow/01-define-architecture-requirements
# Reference PRD requirements in architecture planning

# 3. Design system architecture
@architecture-design-workflow/02-propose-architecture-options
@architecture-design-workflow/03-create-technical-design

# 4. Generate implementation tasks with architecture context
@prd-driven-workflow/02-generate-tasks
# Tasks now include architecture considerations
```

### Review-Driven Workflow Integration

**Architecture Review Process:**
```bash
# 1. Complete architecture design
@architecture-design-workflow/03-create-technical-design
# Creates: /architecture/technical-design-microservices.md

# 2. Initiate architecture review
@review-driven-workflow/01-initiate-review
# Target: /architecture/technical-design-microservices.md

# 3. Execute specialized review
@review-driven-workflow/03-execute-review-process
# Leverages architecture-specific review criteria
```

### Cross-Workflow Traceability
- PRD requirements → Architecture requirements → Technical design
- Architecture decisions → Implementation tasks → Code reviews
- Review findings → Architecture updates → PRD refinements

## Output Structure

### Architecture Artifacts Directory
```
/architecture/
├── [target-name]/
│   ├── architecture-requirements-[TARGET_NAME].md    # Requirements document
│   ├── architecture-options-[TARGET_NAME].md        # Options analysis
│   ├── technical-design-[TARGET_NAME].md            # Technical design
│   ├── architecture-signoff-[TARGET_NAME].md        # Sign-off record
│   └── artifacts/
│       ├── diagrams/                                # Architecture diagrams
│       ├── models/                                  # Data and API models
│       └── templates/                               # Reusable components
└── adr/
    ├── adr-YYYYMMDD-short-title.md                 # Architecture Decision Records
    └── adr-index.md                                 # ADR catalog
```

### Document Structure
Each architecture document includes:

- **Requirements Document**: Business context, NFRs, constraints, success criteria
- **Options Analysis**: Multiple approaches with trade-offs, diagrams, and recommendations
- **Technical Design**: Implementation-ready specifications with detailed guidance
- **Sign-off Record**: Stakeholder approvals, checklists, and governance documentation
- **Decision Records**: Rationale and context for key architectural choices

## Key Features

### Systematic Approach
- **Structured Process**: Four-phase workflow ensures comprehensive architecture coverage
- **Validation Gates**: Prerequisites and quality checks prevent incomplete designs
- **Stakeholder Involvement**: Clear roles and responsibilities for all participants

### Comprehensive Analysis
- **Multi-Option Evaluation**: Compare different approaches with clear trade-offs
- **NFR-Driven Design**: Explicit mapping of requirements to design decisions
- **Risk-Aware Planning**: Identification and mitigation of technical and business risks

### Implementation Ready
- **Detailed Specifications**: Technical designs ready for development teams
- **Clear Interfaces**: API contracts, data models, and component boundaries
- **Operational Readiness**: Deployment, monitoring, and maintenance considerations

### Decision Transparency
- **Architecture Decision Records**: Documented rationale for key choices
- **Traceability**: Clear links from requirements through design to implementation
- **Stakeholder Alignment**: Formal review and approval processes

## Best Practices

### Requirements Gathering
1. Always start with business goals before technical requirements
2. Make NFRs measurable with specific targets (e.g., "< 200ms response time")
3. Document constraints early - they shape all design decisions
4. Include both current and future scale requirements
5. Get stakeholder agreement on priorities and trade-offs

### Architecture Design
1. Start simple - evolve complexity only when proven necessary
2. Design for the 80% case, not edge cases
3. Prefer proven patterns over novel approaches
4. Make boundaries explicit with clear interfaces
5. Design for observability from the start

### Documentation
1. Keep diagrams minimal and focused on one concern
2. Use consistent notation (C4, UML, etc.)
3. Version control all architecture artifacts
4. Link decisions back to requirements
5. Update docs as implementation evolves

### Stakeholder Management
1. Tailor communication to audience expertise level
2. Use visual aids for complex concepts
3. Provide clear trade-off analysis for decisions
4. Get explicit sign-off at each phase
5. Document dissenting opinions and concerns

## Environment Setup

### Required Directory Structure
Ensure these directories exist in your project:
```
/architecture/          # Architecture artifacts and documents
/architecture/adr/      # Architecture Decision Records
```

### Prerequisites
- Clear project scope and business context
- Identified stakeholders and decision makers
- Access to business requirements and constraints
- Understanding of existing system landscape

## Performance Metrics

Track workflow effectiveness with these metrics:

### Process Metrics
- Time from requirements to approved design
- Number of design iterations required
- Stakeholder review cycles needed
- Percentage of requirements addressed

### Quality Metrics
- Post-implementation design accuracy (actual vs planned)
- Number of architecture changes during development
- Technical debt introduced vs avoided
- System performance vs design targets

### Team Metrics
- Developer understanding of architecture (survey)
- Time to onboard new team members
- Architecture documentation usage rates
- ADR reference frequency

### Business Metrics
- Feature delivery acceleration post-design
- Reduced rework from clear architecture
- System reliability improvements
- Cost savings from informed decisions

## Troubleshooting

### Common Issues and Solutions

**Issue**: Requirements keep changing during design  
**Solution**: Lock requirements at phase gates, document changes as new versions, assess impact before accepting changes

**Issue**: Cannot generate distinct architecture options  
**Solution**: Vary optimization dimensions (cost vs performance vs simplicity), consider buy vs build, explore different deployment models

**Issue**: Stakeholders don't understand technical designs  
**Solution**: Use layered documentation (executive summary → technical details), provide analogies, conduct walkthrough sessions

**Issue**: Design seems over-engineered  
**Solution**: Apply YAGNI principle, design for current + 1 year needs, plan evolution path instead of building everything upfront

**Issue**: Missing critical requirements discovered late  
**Solution**: Use requirement checklists, review similar systems, conduct threat modeling, perform capacity planning exercises

**Issue**: Cannot get stakeholder sign-off  
**Solution**: Address specific concerns individually, provide proof-of-concepts, offer phased implementation, escalate to sponsors

**Issue**: Technical design doesn't align with existing systems  
**Solution**: Map integration points explicitly, validate with platform teams, consider adapter patterns, plan migration strategy

**Issue**: Performance requirements seem impossible  
**Solution**: Challenge requirements with data, propose tiered SLAs, consider caching strategies, evaluate specialized technologies

## Comparison with Other Workflows

| Aspect | Architecture-Design | PRD-Driven | Review-Driven |
|--------|-------------------|------------|---------------|
| **Purpose** | System architecture design | Feature development | Code quality assurance |
| **Input** | Business requirements | User needs | Existing codebase |
| **Process** | Requirements → Options → Design → Sign-off | PRD → Tasks → Implementation | Planning → Tasks → Analysis → Publishing |
| **Output** | Architecture artifacts & ADRs | Working features | Review reports & recommendations |
| **Focus** | System design and technology choices | Feature delivery | Quality improvement |
| **Timeline** | Architecture design cycle | Development cycle | Review & improvement cycle |

## Future Enhancements

Planned improvements for the workflow:

- **Template Library**: Pre-built architecture patterns for common scenarios
- **Automated Validation**: AI-powered consistency checking across documents
- **Integration Expansion**: Enhanced connections with development and deployment tools
- **Metrics Dashboard**: Visual tracking of architecture quality and decision outcomes
- **Collaboration Tools**: Real-time stakeholder collaboration and review capabilities

---

**Architecture-Design Workflow**: Systematic approach to creating robust, scalable system architectures through structured analysis and stakeholder collaboration.

For more information about the overall AI Developer Workflow Collection, see the main [README](../../README.md).


