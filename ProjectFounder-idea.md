# ProjectFounder

> **AI-Native Project Intelligence, Research, Architecture, Specification, Budgeting, Documentation, and Implementation Planning System**

**Version:** 0.1
**Status:** Minimum Viable Architecture / Implementation Specification
**Project Type:** AI-assisted project intelligence platform
**Primary Artifact:** `ProjectFounder-idea.md`
**Core Principle:** **Technology is replaceable data; project knowledge is the durable asset.**

Nothing here is reduced — v0.1 keeps the full ProjectFounder architecture: all engines, the artifact system, AI/agent/MCP documentation, research, budget, validation, lifecycle, and governance.

The core separation of concerns:

* **Engines** = intelligence and processing capabilities
* **Artifacts** = persistent outputs/data produced or maintained by those engines
* **Resources** = replaceable technology/provider knowledge
* **Policies** = rules controlling engines
* **Schemas** = machine-readable contracts
* **Workflows** = orchestration
* **Agents** = execution roles
* **Skills** = reusable procedures
* **Project state** = the source of truth about where the project currently is

---

# 1. Executive Summary

ProjectFounder transforms an incomplete project idea into a structured, researched, validated, budgeted, documented, and implementation-ready project.

The user should be able to provide something as simple as:

> "I want to build a bookmark app like Raindrop, with AI search and a browser extension."

ProjectFounder should progressively transform that idea into:

```text
RAW IDEA
   ↓
PROJECT CLASSIFICATION
   ↓
DISCOVERY
   ↓
RESEARCH
   ↓
RESOURCE DISCOVERY
   ↓
GAP ANALYSIS
   ↓
FEATURE DISCOVERY
   ↓
REQUIREMENTS
   ↓
ARCHITECTURE
   ↓
AI / AGENT / MCP DESIGN
   ↓
SECURITY / DATA / API / INFRASTRUCTURE
   ↓
BUDGET / TCO / BUSINESS MODEL
   ↓
DOCUMENTATION PLAN
   ↓
VALIDATION
   ↓
ROADMAP
   ↓
TASKS
   ↓
IMPLEMENTATION-READY PROJECT
```

ProjectFounder is not simply:

* an AI chatbot
* a project generator
* a documentation generator
* a research agent
* an architecture generator
* a task manager

It is a **project intelligence system** that coordinates all of these capabilities.

---

# 2. Vision

Build a general-purpose system capable of taking almost any software, AI, infrastructure, data, research, SaaS, open-source, or technical project idea and turning it into a coherent project blueprint.

The final output should be understandable by:

* humans
* developers
* architects
* product managers
* AI agents
* Claude Code
* Codex
* Gemini
* Cursor
* other coding agents
* MCP-enabled systems
* automation systems

The generated project should be capable of moving directly from:

```text
Idea
```

to:

```text
Research → Specification → Architecture → Tasks → Implementation
```

without requiring the user to manually reconstruct missing context.

---

# 3. Mission

ProjectFounder should answer:

1. What is this project?
2. Why should it exist?
3. Who is it for?
4. What problem does it solve?
5. What already exists?
6. What should be copied, inspired by, replaced, merged, or avoided?
7. What features are actually required?
8. What features are missing?
9. What requirements follow from those features?
10. What architecture should support them?
11. What technologies/resources fit?
12. What AI capabilities are useful?
13. What agents are needed?
14. What skills are needed?
15. What MCP tools/resources are needed?
16. What are the security and privacy implications?
17. What will it cost?
18. What are the risks?
19. What documentation is required?
20. What should be built first?
21. How should it be tested?
22. When is it ready?
23. How should it evolve later?

---

# 4. Core Design Principles

## 4.1 Technology Is Data

ProjectFounder must not be permanently coupled to:

* one programming language
* one database
* one AI provider
* one cloud provider
* one hosting provider
* one API
* one agent framework
* one MCP implementation
* one frontend framework

Instead:

```text
ProjectFounder Core
        │
        ├── Project Knowledge
        ├── Requirements
        ├── Architecture
        ├── Decisions
        ├── Research
        └── State
               │
               ▼
        Resource Intelligence
               │
        ┌──────┼────────┐
        ▼      ▼        ▼
     Language DB       AI Provider
```

Changing PostgreSQL to another database should not require redesigning ProjectFounder.

Changing Claude to another model should not require redesigning ProjectFounder.

---

# 5. What ProjectFounder Is Made Of

ProjectFounder consists of seven major layers.

```text
┌──────────────────────────────────────────────┐
│                 USER / AGENT                 │
├──────────────────────────────────────────────┤
│               ORCHESTRATION                  │
│        Workflows / Agents / Tasks            │
├──────────────────────────────────────────────┤
│                  ENGINES                     │
│ Research / Product / Architecture / etc.     │
├──────────────────────────────────────────────┤
│                 KNOWLEDGE                    │
│ Project / Research / Resource / Decisions    │
├──────────────────────────────────────────────┤
│                 ARTIFACTS                    │
│ Markdown / YAML / JSON / diagrams / schemas  │
├──────────────────────────────────────────────┤
│                  POLICIES                    │
│ Security / Quality / Budget / AI / Research  │
├──────────────────────────────────────────────┤
│             EXTERNAL RESOURCES               │
│ GitHub / Web / APIs / Models / Providers     │
└──────────────────────────────────────────────┘
```

---

# 6. Engines vs Artifacts

This distinction is fundamental.

## 6.1 Engines

An engine is an **active capability** that processes information.

Examples:

```text
Research Engine
Budget Engine
Architecture Engine
Security Engine
Documentation Engine
Validation Engine
```

An engine answers questions or performs transformations.

Example:

```text
Research Engine
Input:
  project idea

Output:
  research findings
```

## 6.2 Artifacts

An artifact is a **persistent representation of project knowledge**.

Examples:

```text
RESEARCH.md
ARCHITECTURE.md
BUDGET.md
TASKS.md
SPEC.md
PROJECT.yaml
```

Artifacts are not engines.

`ARCHITECTURE.md` is an artifact.

The **Architecture Engine** creates or updates it.

---

# 7. Complete Engine Inventory

ProjectFounder v0.1 defines the following engine model.

## 7.1 Project Engine

Determines:

* project identity
* project purpose
* project metadata
* project classification
* project lifecycle
* project state
* project mode
* project intent

---

## 7.2 Discovery Engine

Discovers:

* hidden requirements
* missing information
* unclear goals
* assumptions
* constraints
* unknowns
* open questions
* blockers

---

## 7.3 Brainstorm Engine

Expands the original idea into:

* possibilities
* features
* variants
* product directions
* technical approaches
* business approaches
* alternative architectures

---

## 7.4 Research Engine

Researches:

* competitors
* GitHub repositories
* technologies
* APIs
* frameworks
* standards
* documentation
* pricing
* ecosystem
* market
* users
* open-source alternatives
* implementation approaches

---

## 7.5 Resource Engine

Discovers and evaluates:

* languages
* frameworks
* databases
* APIs
* AI models
* AI providers
* hosting
* VPS
* cloud
* storage
* authentication
* payments
* observability
* testing
* security tools
* agent frameworks
* MCP servers

---

## 7.6 Product Engine

Defines:

* users
* personas
* problems
* jobs-to-be-done
* use cases
* user journeys
* product value
* product boundaries
* product features

---

## 7.7 Feature Discovery Engine

Finds:

* obvious features
* implied features
* missing features
* competitive features
* operational features
* security features
* administrative features
* future features

---

## 7.8 Gap Analysis Engine

Finds missing:

* requirements
* features
* documentation
* architecture
* security controls
* operational systems
* testing
* budget assumptions
* AI safeguards
* deployment considerations

---

## 7.9 Requirements Engine

Converts product intent into:

* functional requirements
* non-functional requirements
* technical requirements
* business requirements
* security requirements
* AI requirements
* operational requirements
* acceptance criteria

---

## 7.10 Architecture Engine

Designs:

* system architecture
* component architecture
* data flow
* control flow
* integrations
* deployment
* networking
* storage
* APIs
* scalability
* reliability

---

## 7.11 UX/UI Engine

Designs:

* information architecture
* navigation
* screens
* pages
* user flows
* responsive behavior
* accessibility
* design system
* interaction patterns

---

## 7.12 Data Engine

Designs:

* data model
* entities
* relationships
* schemas
* indexing
* migrations
* retention
* backup
* restore
* lineage

---

## 7.13 API Engine

Designs:

* API contracts
* endpoints
* authentication
* authorization
* errors
* pagination
* rate limits
* versioning
* webhooks
* events

---

## 7.14 Security Engine

Handles:

* threat modeling
* authentication
* authorization
* permissions
* secrets
* encryption
* audit logging
* supply-chain security
* vulnerability management
* incident response

---

# 8. AI Engine

The AI Engine determines where AI belongs in a project.

It evaluates:

* AI usefulness
* AI workload
* model requirements
* inference patterns
* context requirements
* RAG
* embeddings
* agents
* tools
* memory
* evaluation
* AI cost
* provider selection

---

# 9. Agent Engine

The Agent Engine designs project-specific agents.

It defines:

* agent roles
* responsibilities
* capabilities
* tools
* skills
* permissions
* memory
* context
* state
* loops
* handoffs
* evaluation
* guardrails
* failure handling

Agent autonomy:

```text
L0 = No autonomy
L1 = Suggestions
L2 = Assisted execution
L3 = Supervised execution
L4 = High autonomy
L5 = Autonomous
```

---

# 10. Skills Engine

Skills are reusable procedures.

Examples:

```text
research
github-research
competitor-analysis
technology-research
architecture
database
security
cost-analysis
documentation
validation
```

A skill defines:

* purpose
* inputs
* procedure
* tools
* outputs
* constraints
* validation
* failure conditions

---

# 11. MCP Engine

The MCP Engine manages MCP requirements.

It determines:

* required MCP servers
* tools
* resources
* prompts
* permissions
* transport
* authentication
* security
* capability mapping

MCP should remain an integration mechanism, not the ProjectFounder core.

---

# 12. Documentation Engine

The Documentation Engine determines:

1. which documents are required
2. which are recommended
3. which are optional
4. which are unnecessary
5. which documents depend on others
6. which document is canonical
7. which documents can be derived

Document status:

```text
REQUIRED
RECOMMENDED
OPTIONAL
NOT_APPLICABLE
DEFER
GENERATE_LATER
```

---

# 13. Validation Engine

Validates:

* completeness
* consistency
* architecture
* requirements
* security
* budget
* documentation
* AI design
* agent design
* dependencies
* traceability
* implementation readiness

---

# 14. Budget Engine

The Budget Engine calculates:

* infrastructure
* hosting
* AI
* API usage
* database
* storage
* bandwidth
* email
* domains
* development
* maintenance
* operations
* security
* backup
* migration
* licensing
* human time

It supports:

```text
$0 / Free
MVP
Small
Medium
Large
Enterprise
```

And:

```text
Optimistic
Expected
Conservative
```

Commercial projects additionally calculate:

* MRR
* ARR
* ARPU
* CAC
* LTV
* gross margin
* break-even
* unit economics

---

# 15. Business Engine

Evaluates:

* business model
* pricing
* monetization
* market
* competition
* differentiation
* revenue scenarios
* cost structure
* unit economics
* go-to-market

---

# 16. Risk Engine

Tracks:

* technical risks
* security risks
* financial risks
* vendor risks
* legal risks
* operational risks
* AI risks
* dependency risks
* scalability risks
* project execution risks

---

# 17. Governance Engine

Controls:

* decisions
* approvals
* ownership
* permissions
* policies
* human review
* AI autonomy
* artifact locking
* change management

---

# 18. Roadmap Engine

Transforms validated requirements into:

```text
Vision
 ↓
Milestones
 ↓
Epics
 ↓
Features
 ↓
Tasks
```

---

# 19. Task Engine

Creates implementation tasks with:

* ID
* description
* dependencies
* priority
* estimate
* required skills
* required context
* acceptance criteria
* affected artifacts
* owner
* status

---

# 20. Workflow Engine

Controls execution.

Example:

```text
new-project
    ↓
classification
    ↓
discovery
    ↓
research
    ↓
specification
    ↓
architecture
    ↓
validation
    ↓
roadmap
    ↓
tasks
```

---

# 21. Change-Impact Engine

> See § 163.1 for the v0.1.1 delta-spec amendment (change-scoped artifacts instead of whole-project regeneration).

When something changes, ProjectFounder determines:

```text
What changed?
     ↓
What depends on it?
     ↓
What artifacts are affected?
     ↓
What decisions become invalid?
     ↓
What research is stale?
     ↓
What tasks must change?
```

---

# 22. Migration Engine

Handles:

* technology migrations
* provider migrations
* database migrations
* API migrations
* architecture migrations
* model migrations
* agent migrations

---

# 23. Memory Engine

> See § 163.6 for the v0.1.1 amendment adding MEMORY.md and a required session-bootstrap step.

Stores:

* project history
* decisions
* research
* previous versions
* assumptions
* user preferences
* implementation discoveries
* feedback
* lessons learned

---

# 24. Feedback Engine

> See § 163.7 for the v0.1.1 amendment wiring feedback into anti-drift detection.

Captures:

* user feedback
* implementation feedback
* test results
* production observations
* agent feedback
* research corrections

This feeds back into the intelligence loop.

---

# 25. Lifecycle Engine

ProjectFounder lifecycle:

```text
IDEA
 ↓
CAPTURED
 ↓
CLASSIFIED
 ↓
DISCOVERY
 ↓
RESEARCHING
 ↓
DESIGNING
 ↓
SPECIFYING
 ↓
VALIDATING
 ↓
READY
 ↓
BUILDING
 ↓
TESTING
 ↓
BETA
 ↓
PRODUCTION
 ↓
OPERATING
 ↓
EVOLVING
 ↓
ARCHIVED
```

---

# 26. Project Modes

A project may operate in:

```text
DISCOVERY
RESEARCH
ARCHITECTURE
IMPLEMENTATION
AUDIT
MIGRATION
OPTIMIZATION
SCALE
MAINTENANCE
```

---

# 27. Project Intent

> See § 163.2 for the v0.1.1 amendment adding an Explore step before Discovery for any non-`CREATE` intent.

Supported intents:

```text
CREATE
IMPROVE
REBUILD
CLONE
REVERSE_ENGINEER
MIGRATE
EXTEND
OPTIMIZE
COMPARE
RESEARCH
AUDIT
DOCUMENT
VALIDATE
SCALE
```

---

# 28. Project Classification

> See § 163.5 for the v0.1.1 amendment adding a free-text `other` escape hatch per dimension, for labels a real project needs that aren't enumerated below.

Classification is multidimensional.

## Product

```text
SaaS
B2B
B2C
Freemium
Open Source
Open Core
Enterprise
Internal
Marketplace
Platform
```

## Application

```text
Web
PWA
Mobile
Desktop
Browser Extension
CLI
API
```

## Technical

```text
Library
SDK
Framework
Database
Infrastructure
Protocol
Service
Platform
```

## AI

```text
AI SaaS
AI Agent
Multi-Agent
Agent Platform
MCP
RAG
AI API
AI Skill
```

## Deployment

```text
Cloud
Self-Hosted
Local-First
Offline-First
Hybrid
Edge
```

Multiple classifications may apply.

---

# 29. Project State

Project state is persistent and machine-readable.

Example:

```yaml
project:
  id: example-project
  lifecycle: SPECIFYING
  mode: ARCHITECTURE
  intent: CREATE
  readiness: R4
  quality_profile: STANDARD
  research_depth: L2
  documentation_depth: STANDARD
  complexity: MEDIUM
```

---

# 30. Readiness Levels

```text
R0 — IDEA
R1 — EXPLORED
R2 — RESEARCHED
R3 — SPECIFIED
R4 — ARCHITECTED
R5 — VALIDATED
R6 — IMPLEMENTATION READY
R7 — PRODUCTION READY
```

---

# 31. Scope Engine

Every requirement, feature, artifact, and task should have:

```text
IN_SCOPE
OUT_OF_SCOPE
DEFERRED
UNKNOWN
```

This prevents scope drift.

---

# 32. Goals

ProjectFounder supports:

```text
Vision
 ↓
Strategic Goals
 ↓
Product Goals
 ↓
Technical Goals
 ↓
Success Metrics
```

---

# 33. Success Metrics

Projects can define:

* adoption
* activation
* retention
* performance
* availability
* cost
* reliability
* security
* task completion
* AI accuracy
* agent success rate

---

# 34. Decision Engine

Every major decision records:

```yaml
decision:
  id:
  title:
  context:
  options:
  selected:
  rationale:
  evidence:
  confidence:
  reversibility:
  approval:
  dependencies:
  affected_artifacts:
```

Decision confidence:

```text
LOW
MEDIUM
HIGH
VERY_HIGH
```

Reversibility:

```text
EASY
MODERATE
DIFFICULT
IRREVERSIBLE
```

Approval:

```text
AUTO_APPROVE
RECOMMEND
REQUIRE_HUMAN_APPROVAL
BLOCKED
```

---

# 35. Decision Labels

General:

```text
KEEP
ADD
MERGE
REPLACE
REMOVE
DEFER
UNKNOWN
```

Reverse engineering:

```text
KEEP
MERGE
REIMPLEMENT
INSPIRE
FORK
REPLACE
REMOVE
IGNORE
```

---

# 36. Evidence Model

Evidence types:

```text
FACT
INFERENCE
ESTIMATE
RECOMMENDATION
UNKNOWN
```

Sources should track:

```yaml
source:
  title:
  url:
  publisher:
  accessed:
  published:
  confidence:
  authority:
  freshness:
  specificity:
  independence:
```

Evidence hierarchy:

```text
Official documentation/specification
        ↓
Official repository/maintainer source
        ↓
Technical papers
        ↓
Maintainer discussions
        ↓
Community sources
        ↓
Blogs/social media
```

Contradictions must be surfaced.

They must never be silently hidden.

---

# 37. Research Freshness

> See § 163.7 for the v0.1.1 amendment generalizing this freshness model into a `drift_status` on every canonical artifact, not just research facts.

Research-sensitive information must have freshness rules.

Examples:

* pricing
* API limits
* model capabilities
* framework versions
* hosting costs
* free tiers
* licensing
* provider availability

Research may be marked:

```text
FRESH
AGING
STALE
UNKNOWN
```

---

# 38. Resource Intelligence

Resource records are replaceable.

```yaml
resource:
  id:
  name:
  category:
  type:

  official:
    website:
    documentation:

  license:
    type:
    open_source:

  deployment:

  capabilities:

  compatibility:

  pricing:

  maturity:

  project_fit:

  verification:
    verified_at:
    sources:
```

---

# 39. Resource Selection

Resources are evaluated against:

* requirements fit
* performance
* cost
* free tier
* open-source status
* self-hosting
* maturity
* security
* ecosystem
* developer experience
* lock-in
* geography
* data residency
* scaling
* availability
* license compatibility

---

# 40. Architecture Quality

Architecture must consider:

* simplicity
* maintainability
* scalability
* reliability
* security
* performance
* observability
* portability
* cost

Architecture fitness functions should validate whether the architecture continues to satisfy its intended properties.

---

# 41. Reliability

Where applicable:

```text
SLI
SLO
SLA
Error Budget
Availability
Recovery Time Objective
Recovery Point Objective
```

---

# 42. Performance

Projects may define:

* latency budget
* response-time budget
* startup budget
* bundle-size budget
* database query budget
* AI latency budget
* infrastructure resource budget

---

# 43. Capacity Planning

ProjectFounder should estimate:

* users
* requests
* storage
* bandwidth
* database size
* jobs
* events
* AI tokens
* model calls

at different scales.

---

# 44. Security Architecture

Security planning includes:

```text
Threat Model
Authentication
Authorization
RBAC
Permissions
Secrets
Encryption
Data Protection
Audit Logging
Rate Limiting
Security Headers
Supply Chain Security
SBOM
Vulnerability Management
Incident Response
```

---

# 45. AI Security

AI projects additionally evaluate:

* prompt injection
* data leakage
* tool abuse
* excessive autonomy
* model manipulation
* unsafe tool execution
* memory poisoning
* retrieval poisoning
* untrusted content
* model supply-chain risk

---

# 46. AI Governance

AI governance defines:

* allowed models
* allowed providers
* allowed data
* retention
* logging
* human approval
* autonomy
* cost limits
* safety policies
* evaluation requirements

---

# 47. AI Provider Abstraction

The architecture should support:

```text
AI Provider Interface
       │
 ┌─────┼──────┬───────┐
 ▼     ▼      ▼       ▼
Model A Model B Model C Local
```

Changing providers should not require rewriting business logic.

---

# 48. AI Workload Classification

AI workloads may be classified as:

```text
CHAT
CLASSIFICATION
EXTRACTION
SUMMARIZATION
GENERATION
EMBEDDING
RERANKING
REASONING
CODING
AGENT
VISION
AUDIO
MULTIMODAL
```

---

# 49. AI Cost

AI cost must track:

* input tokens
* output tokens
* embeddings
* inference
* tool calls
* agent iterations
* retries
* caching
* model choice

AI budget should have hard limits where appropriate.

---

# 50. Agent Architecture

Agent specification:

```yaml
agent:
  id:
  name:
  purpose:
  role:
  autonomy:
  inputs:
  outputs:
  tools:
  skills:
  memory:
  context:
  permissions:
  guardrails:
  evaluation:
  failure_handling:
```

---

# 51. Agent Governance

Agents must have:

* identity
* role
* permissions
* allowed tools
* forbidden actions
* budget
* context limits
* escalation rules
* human approval requirements

---

# 52. Tool Governance

Tools should specify:

* purpose
* input schema
* output schema
* permission
* risk
* side effects
* rate limits
* authentication
* audit requirements

---

# 53. Agent Memory

Memory categories:

```text
Transient
Immediate
Medium
Episodic
Structural
```

Memory must have:

* provenance
* retention
* ownership
* deletion
* confidence
* access policy

---

# 54. Agent Evaluation

Agents must be evaluated on:

* correctness
* task completion
* tool selection
* safety
* efficiency
* cost
* hallucination
* recovery
* consistency

---

# 55. Human-in-the-Loop

Human approval should be required for high-impact actions such as:

* destructive changes
* production deployment
* secret changes
* financial commitments
* irreversible migrations
* major architecture changes
* high-risk AI actions

---

# 56. MCP Architecture

MCP definitions may include:

```text
MCP Servers
MCP Tools
MCP Resources
MCP Prompts
Permissions
Transport
Security
Authentication
```

ProjectFounder should maintain an MCP registry rather than hard-code individual servers.

---

# 57. Data Architecture

ProjectFounder must understand:

```text
Entities
Relationships
Schemas
Indexes
Migrations
Retention
Backups
Restoration
Data lineage
Data residency
Data quality
```

---

# 58. API Lifecycle

API design should support:

```text
Design
Version
Publish
Monitor
Deprecate
Migrate
Remove
```

---

# 59. Dependency Lifecycle

Dependencies should be tracked for:

* version
* license
* security
* compatibility
* maintenance
* end-of-life
* replacement

---

# 60. Supply Chain

Where relevant:

* SBOM
* dependency scanning
* artifact verification
* package provenance
* signing
* build integrity

---

# 61. Infrastructure

ProjectFounder may plan:

```text
Cloud
VPS
Containers
Kubernetes
Serverless
Edge
Self-hosted
Hybrid
Local
```

Technology selection remains replaceable.

---

# 62. Deployment

Deployment planning includes:

* environments
* development
* staging
* production
* CI/CD
* secrets
* DNS
* TLS
* backups
* rollback
* monitoring

---

# 63. Operations

Operations artifacts may include:

```text
RUNBOOK
MONITORING
OBSERVABILITY
LOGGING
METRICS
TRACING
ALERTING
INCIDENT RESPONSE
DISASTER RECOVERY
BUSINESS CONTINUITY
CAPACITY PLANNING
```

---

# 64. Disaster Recovery

ProjectFounder should plan:

```text
Backup
Restore
Rollback
Recovery
Failover
Data recovery
Service recovery
```

---

# 65. External Service Failure

External dependencies must have:

* timeout strategy
* retry strategy
* fallback
* circuit breaker
* degraded mode
* failure detection
* migration strategy

---

# 66. Accessibility

Where relevant:

* keyboard access
* screen readers
* semantic HTML
* contrast
* focus management
* reduced motion
* accessible forms

---

# 67. Internationalization

Where relevant:

* languages
* locale
* timezone
* currency
* date formats
* RTL
* translations

---

# 68. Geography

Projects should optionally track:

* target countries
* regions
* availability
* provider regions
* legal jurisdictions
* data residency
* latency

---

# 69. Legal / Regulatory

Where applicable:

* privacy
* terms
* licenses
* copyright
* trademarks
* data processing
* regulatory obligations
* content/IP
* ethical review

ProjectFounder should identify potential concerns, not pretend to provide legal advice.

---

# 70. Sustainability

Large systems may evaluate:

* compute
* storage
* network
* GPU use
* lifecycle
* resource efficiency

---

# 71. Business Model

Possible models:

```text
Free
Freemium
Subscription
Usage-based
One-time
Open Core
Enterprise
Marketplace
Advertising
Internal
```

---

# 72. Budget Architecture

Canonical budget structure:

```text
BUDGET
├── Infrastructure
├── AI
├── APIs
├── Database
├── Storage
├── Bandwidth
├── Hosting
├── Licensing
├── Development
├── Operations
├── Security
├── Backup
├── Migration
└── Human Time
```

ProjectFounder itself should also separately track:

```text
Project Cost
vs
ProjectFounder Operational Cost
```

---

# 73. TCO

Total Cost of Ownership:

```text
TCO =
Infrastructure
+ AI
+ APIs
+ Licensing
+ Development
+ Operations
+ Maintenance
+ Security
+ Migration
+ Human Cost
```

---

# 74. Currency

Budget calculations should support:

```text
USD
EUR
GBP
AED
MVR
and other currencies
```

Internally, one canonical calculation currency should be selected per project.

Exchange rates must have:

* date
* source
* confidence

---

# 75. Free / $0 Architecture

ProjectFounder should have a dedicated cost mode:

```text
ZERO_COST
```

It searches for:

* free tiers
* open-source alternatives
* self-hosted options
* local inference
* free APIs
* free storage
* free hosting
* low-cost VPS

It must also expose free-tier limits and future cost escalation.

---

# 76. Cost Escalation

A resource should not be labeled simply "free".

Instead:

```text
$0
 ↓
10 users
 ↓
100 users
 ↓
1,000 users
 ↓
10,000 users
 ↓
100,000 users
```

ProjectFounder estimates when cost begins to appear.

---

# 77. Product Analytics

Projects may define:

* activation
* conversion
* retention
* churn
* feature usage
* funnel
* performance
* errors

---

# 78. Experiment Engine

Experiments may include:

```text
Hypothesis
Metric
Variant
Duration
Result
Decision
```

---

# 79. User Research

User research may capture:

* interviews
* surveys
* observations
* feedback
* personas
* jobs-to-be-done
* usability findings

---

# 80. Documentation Architecture

Documentation has three categories.

## Canonical

The authoritative source.

Example:

```text
SPEC.md
```

## Derived

Generated from canonical information.

Example:

```text
README.md
```

## Reference

Supporting information.

Example:

```text
REFERENCES.md
```

This prevents conflicting documents.

---

# 81. Documentation Deduplication

ProjectFounder must avoid generating 20 documents that repeat the same information.

Each document should have:

```yaml
document:
  id:
  type:
  status:
  version:
  owner:
  source:
  generated_by:
  generated_at:
  confidence:
  dependencies:
  canonical:
  supersedes:
  superseded_by:
```

---

# 82. Documentation Graph

Example:

```text
PROJECT.yaml
     │
     ▼
SPEC.md
 ┌───┼───────────┐
 ▼   ▼           ▼
REQ FEATURES ARCHITECTURE
 │      │           │
 └──────┼───────────┘
        ▼
      TASKS
        │
        ▼
      ROADMAP
```

---

# 83. Required AI Documentation

For AI projects, ProjectFounder may generate:

```text
AI.md
AI-ARCHITECTURE.md
AI-AGENTS.md
AI-COST.md
AI-LIMITS.md
AI-THREAT-MODEL.md
AI-GOVERNANCE.md
AI-EVALUATION.md
AI-PROVIDER-ABSTRACTION.md
AI-MODEL-LIFECYCLE.md
AI-WORKLOADS.md
AI-DATA-POLICY.md
AI-MEMORY-GOVERNANCE.md
AI-AUDIT.md
AI-OBSERVABILITY.md
```

---

# 84. Agent Documentation

Potential artifacts:

```text
AGENT-ARCHITECTURE.md
AGENT-SPEC.md
AGENT-ROLES.md
AGENT-WORKFLOWS.md
AGENT-POLICY.md
AGENT-CAPABILITIES.md
AGENT-PERMISSIONS.md
AGENT-TOOLS.md
AGENT-SKILLS.md
AGENT-MEMORY.md
AGENT-CONTEXT.md
AGENT-LOOP.md
AGENT-STATE.md
AGENT-EVALUATION.md
AGENT-GUARDRAILS.md
AGENT-HANDOFF.md
AGENT-ERROR-HANDLING.md
```

---

# 85. MCP Documentation

Potential artifacts:

```text
MCP.md
MCP-SERVERS.md
MCP-TOOLS.md
MCP-RESOURCES.md
MCP-PROMPTS.md
MCP-PERMISSIONS.md
MCP-SECURITY.md
MCP-TRANSPORT.md
```

---

# 86. AI Supporting Documentation

Potential artifacts:

```text
TOOLS.md
TOOL-SPEC.md
SKILLS.md
SKILL-SPEC.md
PROMPTS.md
PROMPT-ARCHITECTURE.md
PROMPT-VERSIONING.md
PROMPT-REGISTRY.md
CONTEXT.md
CONTEXT-ENGINEERING.md
MEMORY.md
MEMORY-ARCHITECTURE.md
RAG.md
RAG-ARCHITECTURE.md
MODELS.md
MODEL-SELECTION.md
GUARDRAILS.md
HUMAN-IN-THE-LOOP.md
AI-SAFETY.md
AI-GOVERNANCE.md
EVALUATION.md
BENCHMARKS.md
```

---

# 87. Budget Documentation

Potential artifacts:

```text
BUDGET.md
COST.md
COST-ANALYSIS.md
COST-MODEL.md
COST-SCENARIOS.md
INFRASTRUCTURE-COST.md
AI-COST.md
API-COST.md
DATABASE-COST.md
STORAGE-COST.md
BANDWIDTH-COST.md
HOSTING-COST.md
DEVELOPMENT-COST.md
OPERATIONS-COST.md
TCO.md
UNIT-ECONOMICS.md
FINANCIAL-MODEL.md
REVENUE-MODEL.md
PRICING.md
FREE-TIER.md
ZERO-COST.md
```

---

# 88. Core Project Artifacts

> See § 163.6 for the v0.1.1 amendment adding `MEMORY.md` to this list.

Every ProjectFounder project should normally contain:

```text
idea.md
README.md
PROJECT.yaml
SPEC.md
REQUIREMENTS.md
FEATURES.md
ARCHITECTURE.md
TECH-STACK.md
ASSUMPTIONS.md
CONSTRAINTS.md
NON-GOALS.md
DECISIONS.md
RISKS.md
BUDGET.md
ROADMAP.md
TASKS.md
WORKFLOW.md
VALIDATION.md
OPEN-QUESTIONS.md
LIMITATIONS.md
REFERENCES.md
AGENTS.md
```

Additional documents are conditional.

---

# 89. Special Agent Files

## AGENT.md

The master operational contract for ProjectFounder.

Defines:

* identity
* mission
* operating rules
* reasoning process
* engine usage
* artifact rules
* safety
* approval
* completion criteria

## AGENTS.md

Project-wide agent instructions.

Defines:

* repository conventions
* implementation rules
* agent handoff
* coding expectations
* validation
* forbidden behavior

## CLAUDE.md

Claude Code-specific adapter.

It should translate the generic ProjectFounder contract into Claude Code conventions.

Future adapters may include:

```text
CODEX.md
GEMINI.md
CURSOR.md
COPILOT.md
OPENCODE.md
```

Only generate adapters actually required.

---

# 90. SPEC.md

`SPEC.md` is the canonical implementation specification.

It contains:

* project purpose
* scope
* requirements
* features
* architecture
* interfaces
* constraints
* acceptance criteria

---

# 91. TASKS.md

`TASKS.md` is the implementation backlog.

Every task should trace to:

```text
Goal
 ↓
Requirement
 ↓
Feature
 ↓
Architecture
 ↓
Task
```

---

# 92. ROADMAP.md

`ROADMAP.md` contains:

```text
Vision
Milestones
Epics
Releases
Future work
```

---

# 93. WORKFLOW.md

`WORKFLOW.md` defines how project work is executed.

Example:

```text
Research
 ↓
Review
 ↓
Approve
 ↓
Specify
 ↓
Architect
 ↓
Validate
 ↓
Task
 ↓
Build
 ↓
Test
 ↓
Release
```

---

# 94. Implementation Contract

The implementation contract is the boundary between ProjectFounder design and actual implementation.

## 94.1 Contract Rule

No implementation task should be considered ready unless it has enough context to execute without reconstructing the entire project.

Each task must contain:

```yaml
task:
  id:
  title:
  description:

  source:
    requirements:
    features:
    decisions:
    architecture:

  scope:
    included:
    excluded:

  dependencies:

  inputs:

  outputs:

  affected_files:

  required_context:

  implementation_notes:

  acceptance_criteria:

  tests:

  security_considerations:

  rollback:

  status:
```

---

# 95. Implementation Contract Levels

## Level 1 — Idea

Not implementation-ready.

## Level 2 — Explored

Enough information to discuss.

## Level 3 — Specified

Requirements exist.

## Level 4 — Architected

Technical design exists.

## Level 5 — Validated

Design has passed quality gates.

## Level 6 — Implementation Ready

Tasks are executable.

## Level 7 — Production Ready

Deployment and operations are defined.

---

# 96. Definition of Ready

A task is `READY` only when:

* scope is known
* requirements are known
* dependencies are known
* acceptance criteria exist
* required context exists
* affected artifacts are known
* security implications are understood
* testing expectations exist

---

# 97. Definition of Done

A task is `DONE` only when:

* implementation exists
* tests pass
* acceptance criteria pass
* documentation is updated
* relevant artifacts are synchronized
* validation passes
* no unresolved blocker remains

---

# 98. Build Context Package

Every implementation task can receive a compact context package:

```text
TASK
 ↓
REQUIREMENTS
 ↓
RELEVANT FEATURES
 ↓
RELEVANT ARCHITECTURE
 ↓
DECISIONS
 ↓
DEPENDENCIES
 ↓
CONSTRAINTS
 ↓
ACCEPTANCE CRITERIA
 ↓
TEST REQUIREMENTS
```

The agent should not receive the entire project unless necessary.

---

# 99. Handoff System

Agents can hand work to other agents.

Example:

```text
Research Agent
      ↓
Architecture Agent
      ↓
Security Agent
      ↓
Validation Agent
      ↓
Task Agent
```

Handoffs include:

* context
* outputs
* unresolved questions
* confidence
* blockers
* required next actions

---

# 100. Parallel Work

Independent work can execute in parallel.

Example:

```text
              ┌── Research
Idea ─────────┼── Competitor analysis
              ├── Technology research
              ├── Security discovery
              └── Cost research
```

Results are merged through controlled artifact updates.

---

# 101. Agent Conflict Resolution

When agents disagree:

```text
Agent A
Agent B
Agent C
   ↓
Evidence comparison
   ↓
Confidence comparison
   ↓
Decision Engine
   ↓
Human approval if required
```

No silent overwrite.

---

# 102. Agent Cost Optimization

Agent orchestration should minimize:

* redundant calls
* duplicate research
* excessive context
* repeated tool calls
* unnecessary model usage

Use:

```text
Caching
Context compression
Progressive disclosure
Task-specific context
Research reuse
Artifact reuse
```

---

# 103. Progressive Disclosure

Agents should receive only the context required for the current operation.

Example:

```text
HOT CONTEXT
~200 tokens

BRAIN CONTEXT
~500 tokens

INDEX
~300 tokens

FULL DOCUMENT
on demand
```

---

# 104. Traceability

Every major output should be traceable.

```text
Idea
 ↓
Goal
 ↓
Requirement
 ↓
Feature
 ↓
Decision
 ↓
Architecture
 ↓
Task
 ↓
Implementation
 ↓
Test
```

---

# 105. Artifact Ownership

Artifacts can be:

```text
SYSTEM_GENERATED
AGENT_GENERATED
HUMAN_AUTHORED
HUMAN_APPROVED
MIXED
```

---

# 106. Artifact Locking

Artifacts may be:

```text
LOCKED
UNLOCKED
DRAFT
APPROVED
DEPRECATED
```

A locked canonical artifact should not be silently modified.

---

# 107. Artifact Dependency Graph

ProjectFounder maintains relationships such as:

```text
SPEC
 ├── REQUIREMENTS
 ├── FEATURES
 └── ARCHITECTURE

FEATURES
 └── TASKS

ARCHITECTURE
 ├── DATABASE
 ├── API
 └── INFRASTRUCTURE

BUDGET
 └── RESOURCE SELECTION
```

---

# 108. Change Management

A change must produce:

```text
Change
 ↓
Impact Analysis
 ↓
Affected Decisions
 ↓
Affected Requirements
 ↓
Affected Architecture
 ↓
Affected Documents
 ↓
Affected Tasks
```

---

# 109. Migration and Rollback

Every significant technology decision should consider:

```text
Migration Path
Rollback Path
Exit Cost
Vendor Lock-in
Data Portability
```

---

# 110. Known Limitations

ProjectFounder must explicitly maintain:

```text
LIMITATIONS.md
```

Unknown limitations should not be hidden.

---

# 111. Open Questions

Unknown information should become:

```text
OPEN-QUESTIONS.md
```

Questions may block readiness.

---

# 112. Blocker Engine

Blockers should have:

```yaml
blocker:
  id:
  description:
  severity:
  owner:
  blocking:
  resolution:
  status:
```

---

# 113. Quality Profiles

ProjectFounder supports:

```text
MINIMAL
STANDARD
DETAILED
PRODUCTION
ENTERPRISE
RESEARCH
```

Quality profile controls depth, not correctness.

---

# 114. Research Depth

```text
L0 — Quick
L1 — Standard
L2 — Deep
L3 — Exhaustive
```

---

# 115. Documentation Depth

```text
MINIMAL
STANDARD
DETAILED
FULL
```

---

# 116. Complexity Estimation

Complexity:

```text
LOW
MEDIUM
HIGH
VERY_HIGH
```

Complexity influences:

* research depth
* architecture depth
* documentation
* validation
* testing
* agent involvement

---

# 117. Configuration Engine

ProjectFounder configuration controls:

* project types
* resource categories
* research depth
* scoring
* quality gates
* budget policies
* AI policies
* agent policies
* lifecycle

---

# 118. Policy Engine

Policies include:

```text
Research Policy
AI Policy
Agent Policy
Security Policy
Budget Policy
Documentation Policy
Approval Policy
Quality Policy
```

---

# 119. Schema Validation

Machine-readable outputs must validate against schemas.

Core schemas:

```text
project.schema.yaml
resource.schema.yaml
document.schema.yaml
research.schema.yaml
requirement.schema.yaml
feature.schema.yaml
decision.schema.yaml
risk.schema.yaml
budget.schema.yaml
task.schema.yaml
roadmap.schema.yaml
agent.schema.yaml
skill.schema.yaml
workflow.schema.yaml
```

---

# 120. Project Manifest

Every generated project should have:

```text
PROJECT.yaml
```

Example:

```yaml
project:
  id:
  name:
  version: 0.1
  status:
  lifecycle:
  mode:
  intent:
  types:
  complexity:
  readiness:
  quality_profile:
  research_depth:
  documentation_depth:
```

---

# 121. Machine-Readable Artifacts

ProjectFounder may generate:

```text
PROJECT.yaml
PROJECT.json
requirements.yaml
requirements.json
features.yaml
features.json
architecture.yaml
architecture.json
openapi.yaml
openapi.json
agent.yaml
agent.json
tools.yaml
tools.json
skills.yaml
skills.json
mcp.yaml
mcp.json
deployment.yaml
deployment.json
```

---

# 122. Project Output Structure

A generated project may look like:

```text
<project>/
├── idea.md
├── README.md
├── PROJECT.yaml
├── SPEC.md
├── REQUIREMENTS.md
├── FEATURES.md
├── ARCHITECTURE.md
├── TECH-STACK.md
├── ASSUMPTIONS.md
├── CONSTRAINTS.md
├── NON-GOALS.md
├── DECISIONS.md
├── RISKS.md
├── BUDGET.md
├── ROADMAP.md
├── TASKS.md
├── WORKFLOW.md
├── VALIDATION.md
├── OPEN-QUESTIONS.md
├── LIMITATIONS.md
├── REFERENCES.md
│
├── AI.md
├── AGENT-ARCHITECTURE.md
├── MCP.md
│
├── AGENTS.md
├── CLAUDE.md
│
├── research/
├── architecture/
├── diagrams/
├── schemas/
├── tasks/
├── decisions/
└── resources/
```

Only applicable artifacts are generated.

---

# 123. Concrete v0.1 User Journey

This is the canonical first-run experience.

## Step 1 — User Starts

User enters:

> "I want to build a free AI-powered bookmark manager with web app, PWA, browser extension, semantic search, and optional self-hosting."

---

## Step 2 — ProjectFounder Captures

System creates:

```text
project.id
project.name
raw_idea
created_at
```

State:

```text
CAPTURED
```

---

## Step 3 — Classification

ProjectFounder identifies:

```text
Product:
  SaaS
  Freemium
  Open Source candidate

Application:
  Web
  PWA
  Browser Extension

Technical:
  Search
  Data Platform

AI:
  AI
  RAG
  Semantic Search

Deployment:
  Cloud
  Self-Hosted
```

State:

```text
CLASSIFIED
```

---

## Step 4 — Discovery

ProjectFounder asks only critical questions.

Example:

```text
Who are the primary users?
Is self-hosting mandatory?
Should AI work locally?
Is browser extension required for MVP?
Is authentication required?
```

Unknown answers become assumptions/open questions rather than blocking everything.

---

## Step 5 — Brainstorm

ProjectFounder expands the idea into:

```text
Capture
Organization
Tags
Collections
Search
Semantic Search
AI Summaries
Browser Extension
PWA
Import
Export
Sharing
Authentication
Sync
Backup
Self-hosting
```

---

## Step 6 — Research

Research Engine investigates:

```text
Raindrop.io
Pocket
Omnivore
Linkwarden
Karakeep
browser bookmarking systems
semantic search implementations
open-source alternatives
AI search technologies
```

Research records evidence.

---

## Step 7 — Resource Discovery

Resource Engine evaluates:

```text
Frontend options
Backend options
Database options
Search options
Embedding options
AI providers
Self-hosting
Storage
Authentication
Deployment
```

No technology is permanently selected.

---

## Step 8 — Gap Analysis

ProjectFounder discovers missing concerns:

```text
Account deletion
Import/export
Bookmark deduplication
Broken links
Privacy
Search indexing
Backup
Data portability
Extension permissions
Rate limits
AI cost
AI privacy
```

---

## Step 9 — Feature Discovery

Features are categorized:

```text
MVP
V1
V2
Future
```

---

## Step 10 — Requirements

Each feature becomes requirements.

Example:

```text
REQ-001
The system SHALL allow users to save bookmarks.

REQ-002
The system SHALL allow users to search bookmarks.

REQ-003
The system SHOULD support semantic search.

REQ-004
The system SHALL support export.
```

---

## Step 11 — Architecture

Architecture Engine creates:

```text
System Context
Component Architecture
Data Model
API
Search Architecture
AI Architecture
Security Architecture
Deployment Architecture
```

---

## Step 12 — AI Design

AI Engine determines:

```text
Semantic search
Embeddings
Optional summarization
Optional classification
```

Agent Engine determines whether autonomous agents are actually necessary.

If not:

```text
NO AGENT REQUIRED
```

This is important.

ProjectFounder must not add AI agents merely because AI exists.

---

## Step 13 — Budget

Budget Engine generates:

```text
$0 architecture
MVP architecture
Growth architecture
```

Example:

```text
Scenario A — $0
Scenario B — Low Cost
Scenario C — Growth
```

---

## Step 14 — Security

Security Engine produces:

```text
Threat Model
Authentication
Authorization
Data Protection
Extension Security
AI Threat Model
```

---

## Step 15 — Documentation Selection

ProjectFounder determines:

```text
Required:
  SPEC.md
  REQUIREMENTS.md
  FEATURES.md
  ARCHITECTURE.md
  BUDGET.md
  TASKS.md
  ROADMAP.md

AI:
  AI.md
  AI-ARCHITECTURE.md

Extension:
  EXTENSION.md

Search:
  SEARCH.md

Security:
  SECURITY.md
  THREAT-MODEL.md
```

Unnecessary documents are not generated.

---

## Step 16 — Validation

Validation Engine checks:

```text
Requirements complete?
Features traceable?
Architecture supports requirements?
Budget consistent?
Security covered?
AI justified?
Tasks executable?
```

---

## Step 17 — Readiness

ProjectFounder may report:

```text
Readiness: R6
Implementation Ready
```

---

## Step 18 — Roadmap

Example:

```text
Milestone 1
  Project foundation

Milestone 2
  Authentication

Milestone 3
  Bookmark capture

Milestone 4
  Organization

Milestone 5
  Search

Milestone 6
  Browser extension

Milestone 7
  AI search

Milestone 8
  Deployment
```

---

## Step 19 — Tasks

Tasks are generated from requirements and architecture.

Each task has its own context package.

---

## Step 20 — Coding Agent Handoff

Claude Code / Codex / another coding agent receives:

```text
AGENTS.md
CLAUDE.md
SPEC.md
TASKS.md
relevant architecture
relevant requirements
task context
acceptance criteria
```

The coding agent does not need to rediscover the project.

---

# 124. Continuous Intelligence Loop

ProjectFounder does not stop after generating documents.

```text
              ┌──────────────────────────┐
              │                          │
              ▼                          │
IDEA → RESEARCH → SPEC → ARCHITECTURE    │
              ↓                          │
           BUDGET                        │
              ↓                          │
        DOCUMENTATION                    │
              ↓                          │
          ROADMAP                        │
              ↓                          │
           TASKS                         │
              ↓                          │
           BUILD                         │
              ↓                          │
           TEST                          │
              ↓                          │
          DEPLOY                         │
              ↓                          │
         OBSERVE                         │
              ↓                          │
         FEEDBACK                        │
              ↓                          │
        REASSESS ────────────────────────┘
```

---

# 125. ProjectFounder Observability

ProjectFounder itself should monitor:

* engine execution
* agent execution
* task execution
* research calls
* resource discovery
* validation failures
* token usage
* model usage
* execution cost
* latency
* errors
* artifact changes

---

# 126. ProjectFounder Cost

Separate:

```text
Project Cost
```

from:

```text
ProjectFounder Cost
```

ProjectFounder cost includes:

* AI inference
* web research
* storage
* compute
* API usage
* agent execution

---

# 127. Reproducibility

ProjectFounder should record enough information to reproduce important outputs:

```text
Project version
Engine version
Agent version
Skill version
Prompt version
Policy version
Resource snapshot
Research timestamp
Model
Configuration
```

---

# 128. Versioning

Version:

```text
Project
Artifacts
Schemas
Engines
Agents
Skills
Prompts
Policies
Resources
```

---

# 129. Prompt Management

Prompts should be treated as versioned assets.

Support:

```text
Prompt Registry
Prompt Version
Prompt Metadata
Prompt Evaluation
Prompt Deprecation
```

---

# 130. Skill Versioning

Skills should have:

```text
name
version
purpose
inputs
outputs
dependencies
compatibility
validation
```

---

# 131. Agent Versioning

Agents should have:

```text
agent_id
version
role
capabilities
permissions
tools
skills
model
policy
evaluation
```

---

# 132. Security Boundary

ProjectFounder must distinguish:

```text
Trusted Project Data
Untrusted Research Data
Untrusted Web Content
Agent Instructions
Tool Outputs
User Input
Generated Content
```

Untrusted content must never automatically become trusted instructions.

---

# 133. Sandbox

High-risk agent actions should execute inside controlled environments.

Potential isolation:

```text
Read-only
Sandbox
Container
Temporary workspace
Approval gate
Production
```

---

# 134. Failure Recovery

Failures should produce:

```text
Error
 ↓
Classification
 ↓
Retry?
 ↓
Fallback?
 ↓
Escalate?
 ↓
Recover?
```

Retries must have limits.

---

# 135. Final Quality Gates

Before `R6`, ProjectFounder checks:

### Product

* problem defined
* target user defined
* value proposition defined

### Research

* relevant research complete
* evidence recorded
* stale information identified

### Requirements

* requirements traceable
* scope defined
* acceptance criteria exist

### Architecture

* architecture supports requirements
* major failure modes considered
* dependencies identified

### Security

* threat model exists where needed
* authentication/authorization defined
* data handling understood

### AI

* AI use justified
* model requirements defined
* AI cost considered
* AI safety considered

### Budget

* costs estimated
* assumptions recorded
* free-tier limitations considered

### Documentation

* required docs generated
* duplicates removed
* canonical sources defined

### Implementation

* roadmap exists
* tasks exist
* task dependencies exist
* implementation contract satisfied

---

# 136. v0.1 Minimum Viable Definition

**Minimum Viable does NOT mean removing the architecture.**

It means implementing the smallest executable version of the architecture.

## v0.1 MUST include

### Core

```text
Project Engine
Discovery Engine
Brainstorm Engine
Research Engine
Resource Engine
Product Engine
Feature Discovery Engine
Gap Analysis Engine
Requirements Engine
Architecture Engine
Security Engine
AI Engine
Agent Engine
Documentation Engine
Validation Engine
Budget Engine
Risk Engine
Roadmap Engine
Task Engine
Workflow Engine
```

### Core state

```text
Project lifecycle
Project mode
Project intent
Project scope
Readiness
Complexity
Quality profile
Research depth
```

### Core artifacts

```text
idea.md
README.md
PROJECT.yaml
SPEC.md
REQUIREMENTS.md
FEATURES.md
ARCHITECTURE.md
TECH-STACK.md
ASSUMPTIONS.md
CONSTRAINTS.md
NON-GOALS.md
DECISIONS.md
RISKS.md
BUDGET.md
ROADMAP.md
TASKS.md
WORKFLOW.md
VALIDATION.md
OPEN-QUESTIONS.md
LIMITATIONS.md
REFERENCES.md
AGENTS.md
```

### AI/agent artifacts

At minimum:

```text
AI.md
AI-ARCHITECTURE.md
AGENT-ARCHITECTURE.md
AGENT-SPEC.md
TOOLS.md
SKILLS.md
MCP.md
```

Only if the project uses them.

### Machine-readable

```text
PROJECT.yaml
requirements.yaml
features.yaml
architecture.yaml
decision.yaml
budget.yaml
task.yaml
```

---

# 137. v0.1 SHOULD Include

```text
Research cache
Evidence scoring
Decision confidence
Artifact ownership
Artifact locking
Traceability
Change impact analysis
Basic migration planning
Basic rollback planning
Basic observability
Basic agent evaluation
Basic cost tracking
Basic schema validation
```

---

# 138. v0.1 MAY Defer

These remain architecturally supported but need not be fully implemented:

```text
Advanced multi-agent orchestration
Large-scale distributed execution
Enterprise governance
Advanced billing
Full marketplace
Advanced analytics
Complex experimentation
Advanced autonomous agents
Large-scale model evaluation
Advanced data lineage
Full compliance automation
Kubernetes optimization
```

They are **deferred implementation**, not removed from the architecture.

---

# 139. What v0.1 Must NOT Do

ProjectFounder v0.1 must not:

* hard-code one technology stack
* require one AI provider
* require one database
* assume every project needs agents
* assume every project needs MCP
* generate every possible document
* hide uncertainty
* silently overwrite decisions
* silently overwrite human-approved artifacts
* treat estimates as facts
* treat web research as automatically trustworthy
* claim production readiness without validation
* create unnecessary complexity

---

# 140. v0.1 Implementation Phases

## Phase 0 — Foundation

Implement:

```text
Project model
Project manifest
Schemas
Configuration
State
Lifecycle
```

---

## Phase 1 — Intelligence Core

Implement:

```text
Discovery
Brainstorm
Classification
Requirements
Feature discovery
Gap analysis
```

---

## Phase 2 — Research

Implement:

```text
Research Engine
Evidence model
Sources
Research cache
Freshness
Resource catalog
```

---

## Phase 3 — Architecture

Implement:

```text
Architecture Engine
Data model
API model
Security model
Infrastructure model
```

---

## Phase 4 — AI / Agents

Implement:

```text
AI Engine
Agent Engine
Skill model
Tool model
MCP model
AI policy
Agent policy
```

---

## Phase 5 — Budget / Business

Implement:

```text
Budget Engine
TCO
Cost scenarios
Free-tier analysis
Business model
```

---

## Phase 6 — Documentation

Implement:

```text
Documentation Engine
Document selection
Templates
Canonical documents
Derived documents
Deduplication
```

---

## Phase 7 — Validation

Implement:

```text
Validation Engine
Quality gates
Traceability
Readiness
```

---

## Phase 8 — Implementation Planning

Implement:

```text
Roadmap Engine
Task Engine
Workflow Engine
Build Context Package
Agent handoff
```

---

# 141. Initial Agent Set

ProjectFounder v0.1 may begin with:

```text
project-architect
research-agent
technology-agent
product-agent
architecture-agent
security-agent
ai-agent
documentation-agent
validation-agent
```

The orchestrator decides whether each agent is necessary.

---

# 142. Initial Skill Set

```text
brainstorm
research
competitor-analysis
github-research
technology-research
resource-discovery
requirements
feature-discovery
gap-analysis
architecture
ux-ui
database
api
security
ai-agent
infrastructure
cost-analysis
documentation
validation
```

---

# 143. Initial Workflows

```text
new-project
brainstorm
deep-research
existing-project
github-project
saas
webapp
pwa
mobile
desktop
cli
api
ai
agent
mcp
browser-extension
library
self-hosted
infrastructure
```

---

# 144. Initial Resource Catalog

```text
languages
frameworks
runtimes
databases
search
storage
apis
authentication
payments
email
messaging
ai-models
ai-platforms
agent-frameworks
mcp
hosting
cloud
vps
gpu
containers
devops
observability
security
testing
dns
cdn
analytics
```

---

# 145. Repository Structure

```text
ProjectFounder/
│
├── AGENT.md
├── AGENTS.md
├── CLAUDE.md
├── README.md
├── LICENSE
│
├── docs/                     # this repo's own § 88 instance (not project output, § 122)
│   ├── CHANGELOG.md          # this repo's own changelog (not a project artifact)
│   ├── TASKS.md              # this repo's own build backlog (not TASKS.md, § 91)
│   ├── DECISIONS.md          # this repo's own decision log (§ 34 record shape)
│   ├── ASSUMPTIONS.md        # unproven premises the design relies on
│   ├── CONSTRAINTS.md        # hard rules the design must not break
│   ├── NON-GOALS.md          # § 138–139, what v0.1 deliberately won't do
│   ├── OPEN-QUESTIONS.md     # § 111, unresolved questions that may block readiness
│   ├── LIMITATIONS.md        # § 110, what doesn't work yet
│   ├── REFERENCES.md         # index of external sources
│   └── research/             # meta-research about ProjectFounder itself
│
├── config/
│   ├── project-types.yaml
│   ├── document-types.yaml
│   ├── resource-types.yaml
│   ├── research-policy.yaml
│   ├── scoring.yaml
│   ├── quality-gates.yaml
│   ├── budget-policy.yaml
│   ├── ai-policy.yaml
│   ├── agent-policy.yaml
│   └── lifecycle.yaml
│
├── agents/
│   ├── project-architect.md
│   ├── research-agent.md
│   ├── technology-agent.md
│   ├── product-agent.md
│   ├── architecture-agent.md
│   ├── security-agent.md
│   ├── ai-agent.md
│   ├── documentation-agent.md
│   └── validation-agent.md
│
├── skills/
│   ├── brainstorm/
│   ├── research/
│   ├── competitor-analysis/
│   ├── github-research/
│   ├── technology-research/
│   ├── resource-discovery/
│   ├── requirements/
│   ├── feature-discovery/
│   ├── gap-analysis/
│   ├── architecture/
│   ├── ux-ui/
│   ├── database/
│   ├── api/
│   ├── security/
│   ├── ai-agent/
│   ├── infrastructure/
│   ├── cost-analysis/
│   ├── documentation/
│   └── validation/
│
├── workflows/
│
├── resources/
│
├── templates/
│   ├── core/
│   ├── product/
│   ├── research/
│   ├── architecture/
│   ├── frontend/
│   ├── backend/
│   ├── database/
│   ├── api/
│   ├── security/
│   ├── ai/
│   ├── infrastructure/
│   ├── business/
│   ├── engineering/
│   └── reference/
│
├── schemas/
│
├── checks/
│
├── commands/
│
├── examples/
│
└── output/
    └── <project>/
```

---

# 146. Engine Contract

Every engine should expose a predictable contract.

```yaml
engine:
  id:
  version:
  purpose:

  inputs:
    - type:

  outputs:
    - type:

  dependencies:

  policies:

  tools:

  artifacts_read:

  artifacts_write:

  validation:

  failure_modes:
```

---

# 147. Engine Rules

An engine:

1. must declare its inputs
2. must declare its outputs
3. must identify artifacts it reads
4. must identify artifacts it writes
5. must obey policies
6. must preserve provenance
7. must not silently overwrite locked artifacts
8. must report uncertainty
9. must be versioned
10. must be testable independently

---

# 148. Artifact Contract

Every artifact should have:

```yaml
artifact:
  id:
  type:
  version:
  status:
  ownership:
  canonical:
  source:
  generated_by:
  dependencies:
  confidence:
  created_at:
  updated_at:
```

---

# 149. Workflow Contract

Every workflow should define:

```yaml
workflow:
  id:
  purpose:
  trigger:
  inputs:
  steps:
  engines:
  agents:
  skills:
  artifacts:
  approvals:
  validation:
  failure_recovery:
  outputs:
```

---

# 150. Skill Contract

```yaml
skill:
  id:
  version:
  purpose:
  inputs:
  procedure:
  tools:
  outputs:
  validation:
  failure_conditions:
```

---

# 151. Agent Contract

```yaml
agent:
  id:
  version:
  role:
  purpose:
  autonomy:
  inputs:
  outputs:
  tools:
  skills:
  permissions:
  memory:
  context:
  policies:
  evaluation:
  escalation:
```

---

# 152. Resource Contract

```yaml
resource:
  id:
  name:
  category:
  type:
  capabilities:
  compatibility:
  pricing:
  license:
  deployment:
  maturity:
  risks:
  alternatives:
  verification:
```

---

# 153. Implementation Contract — Final Rule

The implementation layer may consume ProjectFounder artifacts but must never redefine their meaning.

```text
ProjectFounder
      │
      ▼
Canonical Project Knowledge
      │
      ▼
Implementation Contract
      │
      ▼
Coding Agent
      │
      ▼
Code
      │
      ▼
Tests
      │
      ▼
Validation
      │
      ▼
Updated Project Knowledge
```

Implementation discovers facts.

Those facts can feed back into ProjectFounder.

---

# 154. Build → Feedback Loop

After implementation:

```text
Code
 ↓
Tests
 ↓
Observations
 ↓
Implementation Feedback
 ↓
ProjectFounder
 ↓
Change Impact
 ↓
Updated Specification
 ↓
Updated Architecture
 ↓
Updated Tasks
```

This prevents documentation from becoming permanently stale.

---

# 155. Final v0.1 Definition

ProjectFounder v0.1 is a **project intelligence engine with persistent project artifacts**.

Its minimum successful behavior is:

```text
Given:
    A rough project idea

ProjectFounder MUST be able to:

1. classify the project
2. discover missing information
3. brainstorm possibilities
4. research relevant information
5. discover resources
6. identify gaps
7. discover features
8. define requirements
9. design architecture
10. evaluate security
11. determine AI/agent/MCP needs
12. estimate budget
13. identify risks
14. select required documentation
15. generate canonical artifacts
16. validate consistency
17. calculate readiness
18. produce a roadmap
19. produce executable tasks
20. provide an implementation context package
```

---

# 156. The Core Abstraction

The entire system can be reduced to:

```text
                    PROJECT
                       │
       ┌───────────────┼────────────────┐
       ▼               ▼                ▼
   KNOWLEDGE        ENGINES          ARTIFACTS
       │               │                │
       │               │                │
       ▼               ▼                ▼
 Research          Analysis          SPEC
 Resources         Decisions         ARCHITECTURE
 Requirements      Validation        TASKS
 Features          Planning          ROADMAP
 Decisions         Generation        BUDGET
 State             Orchestration      AI.md
```

The project is the source of truth.

Engines operate on project knowledge.

Artifacts persist the results.

Resources provide replaceable technology knowledge.

Policies control behavior.

Schemas enforce structure.

Agents execute workflows.

Skills provide reusable procedures.

---

# 157. ProjectFounder Final Architecture

```text
┌─────────────────────────────────────────────────────┐
│                     USER / AGENT                    │
└──────────────────────────┬──────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────┐
│                  ORCHESTRATION LAYER                │
│         Workflows / Agents / Skills / Tasks         │
└──────────────────────────┬──────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────┐
│                    ENGINE LAYER                     │
│                                                     │
│ Project     Research       Product      Features    │
│ Gap         Requirements   Architecture Security   │
│ AI          Agent          MCP          Budget      │
│ Business    Risk           Documentation           │
│ Validation  Roadmap        Tasks        Workflow    │
│ Change      Migration      Memory       Feedback    │
└──────────────────────────┬──────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────┐
│                 PROJECT KNOWLEDGE                   │
│                                                     │
│ State / Goals / Requirements / Features / Decisions │
│ Research / Resources / Risks / Constraints          │
└──────────────────────────┬──────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────┐
│                    ARTIFACT LAYER                   │
│                                                     │
│ Markdown / YAML / JSON / SQL / OpenAPI / Diagrams  │
└──────────────────────────┬──────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────┐
│                EXTERNAL RESOURCE LAYER              │
│                                                     │
│ GitHub / Web / APIs / Models / Cloud / Databases   │
│ Hosting / MCP / Open Source / Documentation        │
└─────────────────────────────────────────────────────┘
```

---

# 158. Final Principle

ProjectFounder should not try to predict the future technology stack.

It should build a **technology-independent project model** that can continuously evaluate the future technology stack.

Therefore:

```text
Project Knowledge = Durable
Technology Choice = Replaceable
Research = Refreshable
Architecture = Evolvable
Artifacts = Versioned
Decisions = Traceable
Agents = Replaceable
Skills = Reusable
Models = Replaceable
Providers = Replaceable
Implementation = Regeneratable
```

---

# 159. ProjectFounder v0.1 Success Criteria

v0.1 is successful when a user can start with:

> "I have an idea."

and end with:

```text
Project
├── Clearly defined purpose
├── Target users
├── Scope
├── Goals
├── Requirements
├── Features
├── Research
├── Evidence
├── Resource candidates
├── Architecture
├── Security model
├── AI design
├── Agent design
├── MCP design where applicable
├── Budget
├── Risks
├── Decisions
├── Documentation plan
├── Validation results
├── Roadmap
├── Tasks
└── Implementation Context
```

and a coding agent can begin implementation without having to rediscover the project's fundamental decisions.

---

# 160. Final Boundary of v0.1

**Included:**

```text
Full ProjectFounder conceptual architecture
Full engine model
Artifact model
Research model
Resource model
AI model
Agent model
Skill model
MCP model
Budget model
Security model
Documentation system
Decision system
Lifecycle
State
Traceability
Validation
Roadmap
Tasks
Implementation contract
Concrete user journey
```

**Deferred only at implementation depth:**

```text
Large-scale distributed execution
Enterprise-scale orchestration
Advanced autonomous agents
Marketplace
Advanced billing
Massive evaluation infrastructure
Advanced analytics
Complex compliance automation
```

These are **not removed from ProjectFounder**.

They are future implementation layers.

---

# 161. ProjectFounder Definition

> **ProjectFounder is an AI-native project intelligence system that transforms ideas into evidence-backed, requirement-complete, architecture-defined, security-aware, budgeted, documented, validated, and implementation-ready projects while keeping technology choices replaceable and project knowledge persistent.**

The v0.1 objective is therefore not:

> "Generate an idea.md."

It is:

> **"Create a trustworthy project model from which the entire project can be researched, designed, documented, implemented, validated, and continuously evolved."**

---

# 162. End State

```text
                         PROJECTFOUNDER
                               │
                               ▼
                           PROJECT
                               │
        ┌──────────────────────┼─────────────────────┐
        │                      │                     │
        ▼                      ▼                     ▼
    KNOWLEDGE                ENGINES              POLICIES
        │                      │                     │
        │                      ▼                     │
        │                 INTELLIGENCE              │
        │                      │                     │
        └──────────────────────┼─────────────────────┘
                               ▼
                           ARTIFACTS
                               │
                               ▼
                         IMPLEMENTATION
                               │
                               ▼
                              CODE
                               │
                               ▼
                           VALIDATION
                               │
                               ▼
                           PRODUCTION
                               │
                               ▼
                            FEEDBACK
                               │
                               └──────────────►
                                  PROJECTFOUNDER
```

**This is the v0.1 foundation.**

This version keeps the architecture broad while defining **exactly what is executable in v0.1**, and it establishes the implementation contract so ProjectFounder can later evolve without rewriting its core.

---

# 163. v0.1.1 Amendments — Research-Driven Additions

Added 2026-09-08, informed by `docs/research/2026-09-08-projectfounder-deep-research.md` (external evidence from spec-kit, OpenSpec, Martin Fowler/Thoughtworks, HN thread 45935763, and field practitioner critique). These are deliberate, called-out amendments per `AGENTS.md` — "the spec is canonical, updates are deliberate, never silent drift" — not a rewrite of the sections they amend. The base sections stay as the general case; each amendment below states exactly what it changes.

## 163.1 Delta-Spec / Change-Scoped Artifact Mode

Amends: § 21 Change-Impact Engine, § 90 SPEC.md, § 108 Change Management, § 122 Project Output Structure.

Problem: whole-project spec regeneration on every change is the field's #1 complaint — "illusion of work," monster specs, snowball complexity (spec-kit issue #75; HN thread).

ProjectFounder supports two artifact generation modes:

```text
full   — whole-project generation (existing behavior, § 123 user journey)
delta  — change-scoped: propose → explore → apply → sync → archive
```

A `delta` change is its own artifact set, not a rewrite of canonical artifacts:

```text
output/<project>/changes/<change-id>/
    PROPOSAL.md      — what/why, scoped to one change
    DESIGN.md        — optional, only if the change needs design decisions
    DELTA-SPEC.md    — requirement/behavior deltas only (add/modify/remove)
```

The Change-Impact Engine (§ 21) produces `DELTA-SPEC.md` from its existing "what changed → what depends on it → what's affected" pipeline. `archive` is a new terminal step: once a delta is approved, it merges into the canonical artifacts (`SPEC.md`, `ARCHITECTURE.md`, …). Canonical artifacts stay the single source of truth; `changes/` is a log of how they got there, not a parallel truth.

`full` mode remains the default for new projects (Levels 1–3, §§ 2508–2520); `delta` mode is the default once a project reaches Level 6+ (Implementation Ready, § 2528) or carries a non-`CREATE` intent (§ 27, see § 163.2).

Artifact Contract (§ 148) gains one field:

```yaml
artifact:
  # ...existing fields
  mode: full | delta   # delta artifacts also set `change_id`
```

## 163.2 Explore-Before-Design for Brownfield / Non-Greenfield Intent

Amends: § 27 Project Intent, § 123 Concrete v0.1 User Journey (Step 3 Classification → Step 4 Discovery).

Problem: the existing intent list (§ 27: IMPROVE / CLONE / REVERSE_ENGINEER / etc.) already anticipates non-greenfield projects, but the pipeline (Steps 4–11) is written greenfield-shaped — Discovery assumes there is no existing code to read. Field evidence (OpenSpec's Explore workflow; spec-kit discussion #155; HN practitioner reports) says this is exactly where SDD tools fail in practice.

When Project Intent (§ 27) is anything other than `CREATE`, an **Explore** step runs before Discovery:

```text
CLASSIFICATION (intent ≠ CREATE)
     ↓
EXPLORE            ← new: research the existing codebase and its own docs first
     ↓
DISCOVERY          ← now grounded in what Explore found, not a blank slate
     ↓
... (pipeline continues unchanged)
```

Explore is a mode of the Research Engine (§ 7.4), not a new engine: it points research at the existing repository (structure, dependencies, existing docs, existing tests) before pointing it outward at the web/market. Its output feeds Discovery and Gap Analysis (§ 401) the same way external research does, using `source: codebase` instead of `source: web` in the Evidence Model (§ 36).

## 163.3 Human-Readable Artifact Tier

Amends: § 80 Documentation Architecture, § 148 Artifact Contract.

Problem: generated specs are too technical for non-technical reviewers to approve (spec-kit discussion #4207), which blocks the human approval gates ProjectFounder already requires (`AGENT.md` § Operating rules).

Every canonical, human-approved artifact (`SPEC.md`, `ARCHITECTURE.md`, `BUDGET.md`, decisions) carries a short plain-language block before its technical body:

```markdown
> **In plain terms:** <= 5 sentences, no jargon. States what this document
> decides or contains and why it matters, for a reader outside this
> document's usual technical audience.
```

This is not a separate document — Documentation Deduplication (§ 81) still applies. It is a required leading section of the existing canonical artifact, written by whichever engine owns that artifact. Artifact Contract (§ 148) gains a field to track it:

```yaml
artifact:
  # ...existing fields
  has_plain_language_summary: true | false
```

## 163.4 Executable Validation Over LLM Judgment

Amends: § 13 Validation Engine, § 96 Definition of Ready, § 135 Final Quality Gates.

Problem: validation backed only by an LLM re-reading its own spec is not trusted by practitioners (spec-kit discussion #3674: "should compile to executable architecture tests, not rely on LLM review alone"). The concern is judgment with zero mechanical check, not that tests are a perfect proof.

Requirements (§ 7.9) already produce acceptance criteria; this amendment requires acceptance criteria to be written as Given/When/Then scenarios wherever a requirement is checkable mechanically:

```text
GIVEN <precondition>
WHEN  <action>
THEN  <observable outcome>
```

The Validation Engine (§ 13) classifies each acceptance criterion as `executable` (compiles to a check under `checks/` — a test or a fitness function) or `judged` (no mechanical check exists yet; LLM/human review is the only gate). Final Quality Gates (§ 135, Requirements subsection) and Definition of Ready (§ 96) both report the executable/judged ratio for a project's acceptance criteria, not just their existence — "acceptance criteria exist" (§ 135) becomes "acceptance criteria exist, `<n>` of which are executable."

## 163.5 Classification Escape Hatch

Amends: § 28 Project Classification.

Problem: found by dogfooding, not external research. Building `examples/bookmark-manager/` (this repo's own worked example) against § 123's own canonical classification showed that § 28's five taxonomies don't cover every real label a project might need — § 123 Step 3 itself uses "Search," "Data Platform," bare "AI," and "Semantic Search," none of which are enumerated values in § 28. Without an escape hatch, an agent classifying a project either drops real information (flattening "Semantic Search" into the nearest enumerated value, `RAG`) or silently invents a new taxonomy value (drifting from § 28 without a called-out amendment — forbidden by `AGENTS.md`).

Each of § 28's five dimensions (`product`, `application`, `technical`, `ai`, `deployment`) may additionally carry free-text labels that aren't in the enumerated list, under a sibling `other` object — not by extending the enumerated arrays themselves:

```yaml
project:
  types:
    product: [SaaS]        # only § 28 enumerated values
    technical: [Platform]
    ai: [RAG]
    other:
      technical: [Search, "Data Platform"]
      ai: [AI, "Semantic Search"]
```

This keeps § 28's canonical list exactly as specified — nothing is silently added to it — while not losing information a real idea actually contains. `other` entries are a signal, not noise: if the same free-text label recurs across multiple projects, that's evidence § 28 itself should gain an enumerated value, via a normal called-out spec amendment (see § 163's own pattern), not by the taxonomy growing unboundedly one label at a time.

Artifact Contract (§ 148) is unaffected; this only changes the shape of the `types` field already introduced for `PROJECT.yaml` (§ 120).

## 163.6 Session Context Persistence

Amends: § 23 Memory Engine, § 88 Core Project Artifacts, § 98 Build Context Package, § 99 Handoff System.

Problem: the field's loudest complaint isn't spec generation quality, it's context loss between sessions (spec-kit discussion #1482: "AI forgets everything between sessions"). § 23 already lists what the Memory Engine stores, and § 99 already closes with the right goal — "the coding agent does not need to rediscover the project" — but nothing says *when* memory is loaded, and most of § 23's categories already have a canonical home elsewhere (decisions → `DECISIONS.md`, assumptions → `ASSUMPTIONS.md`, research → `RESEARCH.md`/research cache § 114), which § 81 Documentation Deduplication says shouldn't be duplicated into a second file.

Two changes:

1. **`MEMORY.md`** joins § 88's Core Project Artifacts, scoped to exactly the § 23 categories that have no other canonical home: user preferences, implementation discoveries (facts learned while building that aren't decisions — "the free tier actually caps at 3 seats, not 5"), and lessons learned. Project history, decisions, research, assumptions, and feedback stay in their existing artifacts; `MEMORY.md` doesn't repeat them.
2. **Session bootstrap is a required, named step**, not an implicit assumption. At the start of any session working on a project, before any engine runs: read `PROJECT.yaml`, `MEMORY.md`, `DECISIONS.md`, and `OPEN-QUESTIONS.md`. This is distinct from the task-scoped Build Context Package (§ 98, which stays narrow on purpose) — bootstrap is session-scoped and always runs once; the Build Context Package is per-task and runs many times within a session.

```yaml
session_bootstrap:
  always_read: [PROJECT.yaml, MEMORY.md, DECISIONS.md, OPEN-QUESTIONS.md]
  purpose: "A new session starts with the project's durable state already loaded, not rediscovered from scratch."
```

## 163.7 Anti-Drift Detection Loop

Amends: § 21 Change-Impact Engine, § 24 Feedback Engine, § 37 Research Freshness, § 108 Change Management, § 135 Final Quality Gates.

Problem: spec-to-code drift is the same docs-vs-code-drift problem that's existed for 20 years, except it now makes agents ship wrong changes on top of stale assumptions, not just confuse human readers (DZone, "SDD Didn't Solve the Real Problem"; Focused Labs, "Documentation Drift Breaks Coding Agents"). § 108 Change Management already handles a *declared* change's impact, and § 37 already tracks freshness for research facts specifically — neither one detects *undeclared* drift: code that changed without the spec being told, or an artifact whose upstream dependency (§ 107 Artifact Dependency Graph) changed without anyone checking whether it still holds.

§ 37's freshness enum (`FRESH` / `AGING` / `STALE` / `UNKNOWN`) generalizes from research facts to every canonical artifact, as a new `drift_status` field on the Artifact Contract (§ 148):

```yaml
artifact:
  # ...existing fields
  drift_status: IN_SYNC | SUSPECT | DRIFTED | UNKNOWN
```

- `IN_SYNC` — nothing suggests divergence from what the artifact describes.
- `SUSPECT` — an upstream dependency (§ 107) changed since this artifact was last touched, but nobody has confirmed whether it still holds.
- `DRIFTED` — confirmed to no longer match reality (implementation feedback, a production observation, or a research re-check contradicts it).
- `UNKNOWN` — no signal either way (e.g. a freshly generated artifact with no dependents yet).

The Feedback Engine (§ 24) is the trigger: implementation feedback, production observations, or research corrections that contradict a canonical artifact flip its `drift_status` to `SUSPECT` or `DRIFTED` and propagate `SUSPECT` to its dependents via the Artifact Dependency Graph (§ 107) — the same propagation § 108 already does for a *declared* change, now also firing on an *observed* one. Final Quality Gates (§ 135, Documentation subsection) add one check: no canonical artifact the project depends on is `DRIFTED` at `R6`/`R7`. This makes "keep the spec true" a checked property (per § 163.4's own executable-over-judged principle) instead of a promise nobody verifies.
