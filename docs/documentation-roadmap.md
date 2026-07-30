# NovaCortex OS — Detailed Documentation Roadmap

This roadmap defines the documents required to design, build, validate, and maintain NovaCortex OS as a complete AI-native operating system with a project-owned AI built from scratch.

NovaKernel internals are not duplicated here. This repository documents only the contracts by which NovaCortex OS uses NovaKernel.

## Non-Negotiable Documentation Rules

Every relevant document must preserve these rules:

1. The central AI is designed, trained, evaluated, and versioned by the project.
2. No cloud AI API, pretrained model, or externally trained checkpoint provides core or fallback intelligence.
3. General non-AI tooling may be used only as documented implementation infrastructure.
4. AI output is a proposal to the control layer, never kernel authority.
5. System actions are typed, permission-checked, auditable, interruptible, and verifiable.
6. The OS remains operable through deterministic manual and safe-mode paths.
7. NovaKernel is developed separately and consumed through a versioned contract.

---

## D0 — Vision, Scope, and Terminology

### Documents

- `vision-and-scope.md`
- `system-responsibilities.md`
- `system-boundaries.md`
- `non-goals.md`
- `terminology.md`
- `novacortex-vs-novakernel.md`
- `definition-of-usable-system.md`

### Required Decisions

- Product vision and measurable goals
- NovaCortex OS and NovaKernel ownership boundaries
- Meaning of AI-native, autonomous, from scratch, safe mode, and system understanding
- Minimum usable system and minimum developer preview
- Explicit non-goals and prohibited dependencies

### Exit Criteria

- Responsibilities do not overlap
- Goals and non-goals are testable
- From-scratch AI requirements are unambiguous
- Major terms have one approved definition

---

## D1 — System Architecture and Trust Boundaries

### Documents

- `system-architecture.md`
- `layered-architecture.md`
- `component-map.md`
- `runtime-dependency-graph.md`
- `system-data-flow.md`
- `boot-to-ai-lifecycle.md`
- `trust-boundaries.md`
- `failure-propagation.md`

### Required Decisions

- Ownership and allowed communication paths for every layer
- Startup, shutdown, degradation, and recovery order
- Trusted, privileged, isolated, and untrusted components
- Stable interfaces and versioning rules
- Behaviour before the AI starts and after it fails

### Exit Criteria

- Every component belongs to one layer
- No path bypasses permission and policy enforcement
- Boot and shutdown are deterministic
- Critical failure paths have defined containment

---

## D2 — NovaKernel Integration

### Documents

- `kernel-integration-overview.md`
- `kernel-interface-contract.md`
- `system-call-dependencies.md`
- `kernel-capability-contract.md`
- `kernel-telemetry-contract.md`
- `kernel-event-format.md`
- `ai-action-request-protocol.md`
- `version-compatibility.md`
- `kernel-failure-handling.md`

### Required Decisions

- Required system calls, capabilities, events, and telemetry
- Request, response, timeout, cancellation, and error formats
- Permission-enforcement ownership
- Version negotiation and compatibility
- Behaviour when a kernel capability is missing
- Test doubles and contract-test strategy

### Boundary Rule

These documents describe the public integration contract. They must not reproduce NovaKernel scheduler, memory, driver, interrupt, networking, or filesystem implementations.

### Exit Criteria

- Every privileged operation has an authorization path
- Every dependency is versioned and testable
- Failure and fallback behaviour is deterministic
- NovaKernel can evolve without undocumented coupling

---

## D3 — Deterministic User-Space Foundation

### Documents

- `userspace-runtime.md`
- `init-system.md`
- `service-manager.md`
- `process-model.md`
- `ipc-model.md`
- `session-management.md`
- `configuration-system.md`
- `shutdown-and-restart.md`
- `manual-operation-mode.md`

### Required Decisions

- First user-space process and startup sequence
- Service registration, dependencies, supervision, and restart policy
- IPC transport and message schemas
- Session and configuration ownership
- Manual operation without the AI
- Graceful shutdown and forced recovery

### Exit Criteria

- A minimal user space boots on NovaKernel
- Services start and stop deterministically
- IPC contracts are versioned
- The base OS remains usable without AI

---

## D4 — Capability, Permission, Policy, and Audit Model

### Documents

- `capability-security.md`
- `permission-model.md`
- `policy-engine.md`
- `action-risk-classification.md`
- `authorization-flow.md`
- `user-approval-system.md`
- `audit-log.md`
- `action-interruption.md`
- `rollback-model.md`
- `safe-mode.md`

### Required Decisions

- Capability issuance, scope, delegation, expiry, and revocation
- Read-only, reversible, privileged, destructive, and security-critical risk levels
- Policy precedence and user approval rules
- Audit integrity, redaction, and retention
- Emergency interruption and rollback eligibility
- Safe-mode capabilities and restrictions

### Exit Criteria

- The AI has no ambient kernel or hardware authority
- Destructive operations cannot bypass approval
- Sensitive operations are auditable
- Actions can be interrupted and the OS can enter safe mode

---

## D5 — Structured System State and Capability Graph

### Documents

- `system-state-model.md`
- `resource-graph.md`
- `capability-registry.md`
- `system-event-model.md`
- `application-capability-model.md`
- `device-capability-model.md`
- `system-context-store.md`
- `state-synchronization.md`
- `sensitive-data-filtering.md`

### Required Decisions

- Identity and relationships for files, processes, services, devices, applications, and users
- Capability discovery and schema evolution
- Event ordering, retention, provenance, and replay
- Current versus historical state
- Stale-state detection and repair
- Information visible to each AI subsystem

### Exit Criteria

- AI operation does not depend on parsing unstructured terminal output
- Every controllable component exposes typed capabilities
- State changes generate structured events
- Stale or unauthorized context is detectable

---

## D6 — From-Scratch AI Research Charter

### Documents

- `ai-research-charter.md`
- `from-scratch-definition.md`
- `ai-non-dependency-policy.md`
- `research-objectives.md`
- `baseline-strategy.md`
- `experiment-governance.md`
- `reproducibility-policy.md`
- `model-versioning.md`
- `responsible-research.md`

### Required Decisions

- What must be original and project-owned
- Prohibited models, checkpoints, APIs, and fallback paths
- Allowed non-AI research and engineering tools
- Initial capability targets and measurable baselines
- Experiment metadata, seed, environment, and artifact requirements
- Model identity, lineage, compatibility, and retirement
- Publication and review standards

### Exit Criteria

- A contributor can determine whether a dependency violates the scratch-built rule
- Every experiment can be reproduced from recorded inputs
- Model lineage begins with project-owned architecture and initialization
- Research claims require recorded evaluation evidence

---

## D7 — Data, Representation, and Tokenization

### Documents

- `data-governance.md`
- `dataset-specification.md`
- `data-provenance.md`
- `licensing-and-consent.md`
- `collection-and-generation.md`
- `filtering-and-deduplication.md`
- `system-action-corpus.md`
- `representation-design.md`
- `tokenizer-design.md`
- `train-validation-test-splits.md`
- `data-versioning.md`

### Required Decisions

- Permitted sources and licenses
- Collection, synthetic generation, filtering, and removal procedures
- Privacy, secret, and personal-data handling
- Language, system-state, action, code, and conversation representations
- Tokenizer or alternative representation training
- Leakage prevention and immutable evaluation sets
- Dataset versioning and reproducibility

### Exit Criteria

- Every training item has traceable provenance
- The first representation system is trained or constructed by the project
- Evaluation data is isolated from training
- Dataset builds are repeatable and policy-compliant

---

## D8 — Training and Experiment Infrastructure

### Documents

- `training-architecture.md`
- `optimization-strategy.md`
- `distributed-training.md`
- `checkpoint-format.md`
- `experiment-tracking.md`
- `resource-budgeting.md`
- `determinism-and-seeding.md`
- `failure-recovery.md`
- `artifact-integrity.md`
- `training-security.md`

### Required Decisions

- Training stages, objectives, optimizers, schedules, and stopping rules
- Hardware abstraction and scaling strategy
- Checkpoint content, integrity, and compatibility
- Resource budgets and experiment approval
- Reproducibility requirements
- Failure recovery and corrupted-artifact detection

### Exit Criteria

- A small model can be trained from project-owned initial weights
- A run produces traceable data, configuration, metrics, and artifacts
- Interrupted runs recover without ambiguous lineage
- Checkpoints are integrity-checked and versioned

---

## D9 — Core Model and Inference Runtime

### Documents

- `model-architecture.md`
- `learning-objectives.md`
- `parameter-initialization.md`
- `inference-runtime.md`
- `context-engine.md`
- `confidence-and-uncertainty.md`
- `resource-limits.md`
- `runtime-lifecycle.md`
- `model-loading-and-rollback.md`
- `ai-failure-isolation.md`

### Required Decisions

- Architecture, parameterization, initialization, and learning objectives
- Training and inference numerical formats
- Context limits and resource budgets
- Confidence and uncertainty representation
- Model loading, compatibility, update, rollback, and quarantine
- Behaviour when inference is unavailable or incorrect

### Exit Criteria

- The first project-trained model runs locally
- Its architecture, weights, data version, and evaluation are traceable
- Runtime failure cannot crash NovaKernel or critical services
- Model updates can be rejected or rolled back

---

## D10 — Memory and System Understanding

### Documents

- `system-perception.md`
- `context-assembly.md`
- `short-term-memory.md`
- `persistent-memory.md`
- `memory-provenance.md`
- `memory-permissions.md`
- `memory-retention-and-deletion.md`
- `goal-understanding.md`
- `state-grounding.md`
- `uncertainty-resolution.md`

### Required Decisions

- How structured state becomes model context
- Short-term and persistent memory formats
- Provenance, ownership, expiry, correction, and deletion
- Goal, constraint, and ambiguity representation
- Grounding and stale-context checks
- Clarification thresholds

### Exit Criteria

- The AI can answer bounded questions about current system state
- Memory cannot bypass data permissions
- Claims about the machine cite current structured evidence
- Stale, conflicting, and uncertain context is surfaced

---

## D11 — Goal Planner and Action Engine

### Documents

- `goal-representation.md`
- `task-planner.md`
- `task-graph.md`
- `action-schema.md`
- `action-executor.md`
- `preconditions-and-postconditions.md`
- `result-verification.md`
- `failure-replanning.md`
- `task-cancellation.md`
- `multi-step-execution.md`

### Required Decisions

- Goal decomposition and task ordering
- Typed actions and capability bindings
- Preconditions, postconditions, and evidence
- Authorization checkpoints
- Execution state machine
- Cancellation, compensation, rollback, and replanning limits

### Exit Criteria

- Every action has explicit inputs, permissions, risk, and expected results
- Multi-step tasks can be inspected and interrupted
- Failed actions cannot be reported as successful
- Goal completion is verified against actual state

---

## D12 — Conversation, Voice, and Explanation

### Documents

- `conversation-engine.md`
- `text-interface.md`
- `voice-pipeline.md`
- `conversation-state.md`
- `intent-clarification.md`
- `confirmation-system.md`
- `action-narration.md`
- `progress-reporting.md`
- `error-and-uncertainty-explanation.md`
- `sensitive-information-redaction.md`

### Required Decisions

- Project-owned language and voice components
- Conversation lifecycle and state
- Clarification and confirmation rules
- Progress-event representation
- Explanation evidence and detail levels
- Redaction and accessibility requirements

### Exit Criteria

- The AI can hold a bounded local conversation without an external AI service
- Narration matches real execution state
- Required confirmations cannot be skipped
- Errors and uncertainty include actionable recovery information

---

## D13 — Core System Services

### Documents

- `file-service.md`
- `application-service.md`
- `process-service.md`
- `device-service.md`
- `network-service.md`
- `storage-service.md`
- `settings-service.md`
- `update-service.md`
- `notification-service.md`
- `identity-and-user-service.md`

### Required Content for Every Service

- Responsibilities and non-responsibilities
- Typed public interfaces
- State, dependencies, and lifecycle
- Kernel capabilities and permissions
- Failure, recovery, and safe-mode behaviour
- Test and acceptance requirements

### Exit Criteria

- Each service has one clear owner
- Cross-service dependencies are documented
- AI-accessible operations use typed capabilities
- Service failures remain contained

---

## D14 — Desktop, Shell, Applications, and SDK

### Documents

- `desktop-architecture.md`
- `system-shell.md`
- `window-management.md`
- `application-model.md`
- `application-lifecycle.md`
- `application-sdk.md`
- `settings-interface.md`
- `ai-activity-center.md`
- `permission-interface.md`
- `accessibility.md`

### Required Decisions

- Desktop, shell, compositor, and session ownership
- Application packaging, isolation, lifecycle, and capability declaration
- AI interaction surfaces and activity history
- Permission, interruption, and recovery interfaces
- Developer SDK compatibility and security

### Exit Criteria

- Users can operate the OS with or without AI
- AI activity is visible and interruptible
- Applications have a documented secure lifecycle
- Third-party applications can expose safe capabilities

---

## D15 — Diagnostics, Recovery, and Codebase Maintenance

### Documents

- `system-health-monitor.md`
- `diagnostic-engine.md`
- `failure-correlation.md`
- `recovery-orchestrator.md`
- `checkpoint-and-rollback.md`
- `safe-boot.md`
- `codebase-knowledge-model.md`
- `module-dependency-graph.md`
- `change-impact-analysis.md`
- `failure-localization.md`
- `isolated-build-and-test.md`
- `maintenance-approval-flow.md`

### Required Decisions

- Health signals and failure classification
- Automatic versus approved recovery
- Evidence required for diagnosis
- Codebase indexing and dependency tracking
- Patch proposal and impact format
- Isolation, review, deployment, and rollback rules

### Exit Criteria

- Recovery is risk-classified, auditable, and verified
- Proposed code changes include evidence and affected modules
- Changes are built and tested in isolation
- Trusted components cannot be silently updated

---

## D16 — Build, Image, Update, and Release Engineering

### Documents

- `build-system.md`
- `novakernel-import.md`
- `userspace-build.md`
- `model-artifact-integration.md`
- `filesystem-image.md`
- `bootable-image-assembly.md`
- `qemu-testing.md`
- `hardware-support-policy.md`
- `update-and-rollback.md`
- `release-process.md`
- `versioning.md`
- `software-bill-of-materials.md`

### Required Decisions

- Reproducible build stages and outputs
- NovaKernel and AI model pinning
- Filesystem and boot-image layouts
- Debug, research, evaluation, and release profiles
- Signed update, compatibility, rollback, and recovery rules
- Initial virtual-machine and hardware targets

### Exit Criteria

- Complete images are reproducible
- Kernel, model, data, and user-space versions are traceable
- Images boot in automated tests
- Failed updates recover to a known-good system

---

## D17 — Testing, AI Evaluation, Security, and Reliability

### Documents

- `testing-strategy.md`
- `kernel-contract-testing.md`
- `service-integration-testing.md`
- `end-to-end-testing.md`
- `ai-capability-evaluation.md`
- `planning-and-action-evaluation.md`
- `conversation-evaluation.md`
- `safety-evaluation.md`
- `security-testing.md`
- `failure-injection.md`
- `recovery-testing.md`
- `performance-benchmarks.md`
- `release-gates.md`

### Required Decisions

- Test ownership and required levels
- Immutable evaluation suites and contamination checks
- AI correctness, grounding, uncertainty, and safety metrics
- Action success, false-success, and unsafe-action rates
- Adversarial, permission, privacy, and supply-chain tests
- Performance budgets and release-blocking failures

### Exit Criteria

- Every module has acceptance tests
- Model and planner releases pass versioned evaluation suites
- Permission and recovery paths pass failure injection
- Release evidence is published with limitations

---

## D18 — Contributor, Research, and Governance Documentation

### Documents

- `getting-started.md`
- `development-environment.md`
- `repository-structure.md`
- `coding-standards.md`
- `research-contribution-guide.md`
- `data-contribution-guide.md`
- `issue-and-pull-request-guide.md`
- `architecture-decision-records.md`
- `model-and-dataset-cards.md`
- `security-policy.md`
- `release-governance.md`
- `glossary.md`

### Required Decisions

- Engineering and research review workflows
- Data, model, code, and documentation contribution requirements
- Architecture decision ownership
- Security reporting and embargo handling
- Model and dataset documentation standards
- Definition of done and release authority

### Exit Criteria

- New contributors can reproduce the development environment
- Research results have traceable evidence
- Security-sensitive work follows a dedicated process
- Architecture and release decisions are recorded

---

## Standard Structure for Module Documents

Every system module document must include:

1. Purpose
2. Responsibilities
3. Non-responsibilities
4. Inputs, outputs, and schemas
5. Public interfaces
6. Internal components
7. State and lifecycle
8. Dependencies
9. Permissions and security
10. Failure and recovery behaviour
11. Observability
12. Testing and evaluation
13. Acceptance criteria
14. Open questions

Every AI research document must additionally record:

1. Hypothesis
2. Baseline
3. Data and artifact versions
4. Architecture and initialization
5. Training or evaluation configuration
6. Reproducibility environment
7. Metrics and failure analysis
8. Safety and limitation analysis

---

## Documentation Execution Order

Documentation should proceed in dependency order:

1. D0 — Vision, Scope, and Terminology
2. D1 — System Architecture and Trust Boundaries
3. D2 — NovaKernel Integration
4. D3 — Deterministic User-Space Foundation
5. D4 — Capability, Permission, Policy, and Audit Model
6. D6 — From-Scratch AI Research Charter
7. D5 — Structured System State and Capability Graph
8. D7 — Data, Representation, and Tokenization
9. D8 — Training and Experiment Infrastructure
10. D9 — Core Model and Inference Runtime
11. D10 — Memory and System Understanding
12. D11 — Goal Planner and Action Engine
13. D12 — Conversation, Voice, and Explanation
14. D13 — Core System Services
15. D14 — Desktop, Shell, Applications, and SDK
16. D15 — Diagnostics, Recovery, and Codebase Maintenance
17. D16 — Build, Image, Update, and Release Engineering
18. D17 — Testing, AI Evaluation, Security, and Reliability
19. D18 — Contributor, Research, and Governance Documentation

Implementation experiments may begin early, but no subsystem becomes a trusted OS component until its boundaries, safety rules, tests, and acceptance criteria are approved.

---

## Immediate Documentation Set

The first approved documentation package should contain:

1. `vision-and-scope.md`
2. `system-responsibilities.md`
3. `system-boundaries.md`
4. `non-goals.md`
5. `terminology.md`
6. `novacortex-vs-novakernel.md`
7. `from-scratch-definition.md`
8. `ai-non-dependency-policy.md`
9. `trust-boundaries.md`
10. `definition-of-usable-system.md`
