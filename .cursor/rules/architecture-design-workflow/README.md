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

## Integration with Existing Workflows

The architecture-design workflow seamlessly integrates with other workflow systems:

- **PRD-Driven Workflow**: Architecture requirements can be derived from PRDs, and approved designs feed into implementation planning
- **Review-Driven Workflow**: Technical designs provide context for code reviews and architecture compliance validation
- **Cross-Workflow Artifacts**: Requirements traceability from business needs through design to implementation

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

- Keep requirements measurable; map each NFR to a concrete design choice
- Prefer simple, evolvable designs; defer heavy complexity until proven necessary
- Use diagrams to clarify intent; keep them minimal and up to date
- Document risks and rollback strategies early

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

## Success Metrics

Track these metrics to measure workflow effectiveness:

- **Requirements Quality**: Completeness and measurability of captured requirements
- **Option Viability**: Number of feasible alternatives generated and quality of analysis
- **Design Completeness**: Implementation readiness of technical designs
- **Stakeholder Satisfaction**: Approval rates and feedback quality
- **Implementation Success**: Actual vs predicted performance and timelines
- **Decision Quality**: Effectiveness of architectural choices over time

## Troubleshooting

### Common Issues

1. **Incomplete Requirements**
   - Conduct additional stakeholder interviews
   - Use requirements templates and checklists
   - Validate against similar system patterns
   - Engage domain experts for clarification

2. **Option Generation Difficulties**
   - Relax constraints to enable more alternatives
   - Consider phased implementation approaches
   - Evaluate hybrid solutions combining approaches
   - Seek external architecture consultation

3. **Technical Design Complexity**
   - Break down into smaller, manageable components
   - Focus on MVP and essential features first
   - Simplify interfaces and reduce dependencies
   - Consider proven patterns and reference architectures

4. **Stakeholder Alignment Challenges**
   - Clearly document trade-offs and implications
   - Provide business impact analysis for decisions
   - Use workshops and collaborative sessions
   - Escalate conflicts to appropriate decision makers

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


