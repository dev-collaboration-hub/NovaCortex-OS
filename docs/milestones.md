# NovaCortex OS — Engineering Milestones

These milestones define the delivery order for NovaCortex OS. They intentionally do not contain calendar promises. Dates should be assigned only after the architecture, people, compute, hardware, and funding constraints are known.

Each milestone must produce reviewable documentation, code, tests, failure behaviour, and acceptance evidence. A demonstration alone does not complete a milestone.

## Project-Wide Completion Rules

Every milestone must preserve these invariants:

- The central AI is built and trained by the project from project-owned architecture and initial weights
- No cloud AI API, pretrained model, or externally trained checkpoint provides core or fallback intelligence
- AI actions are typed, permission-controlled, auditable, interruptible, and verified
- NovaKernel remains a separate repository and deterministic kernel boundary
- The OS remains operable when the AI is unavailable
- Model, data, code, configuration, and evaluation versions are traceable
- Trusted components cannot be silently modified or deployed by the AI

---

## M0 — Project Definition

**Goal:** Establish one unambiguous definition of NovaCortex OS.

**Deliverables:**

- Vision, scope, non-goals, terminology, and repository boundaries
- Definition of AI-native and built from scratch
- Definition of the minimum usable system
- Initial architecture decision record process

**Exit criteria:**

- NovaCortex OS and NovaKernel responsibilities do not overlap
- Prohibited AI dependencies are explicit
- Project goals are measurable

---

## M1 — Architecture and Safety Baseline

**Goal:** Define the complete system and its trust boundaries before privileged AI control exists.

**Deliverables:**

- Layered system architecture
- Component and dependency maps
- Capability, permission, policy, audit, interruption, rollback, and safe-mode specifications
- Threat model and failure-containment plan

**Exit criteria:**

- No planned action path bypasses authorization
- Critical startup, failure, shutdown, and recovery paths are specified
- Security invariants have planned tests

---

## M2 — NovaKernel Integration Contract

**Goal:** Establish the versioned boundary between the complete OS and NovaKernel.

**Deliverables:**

- System-call and user-space ABI requirements
- Kernel capability, event, and telemetry schemas
- AI action request protocol
- Compatibility, timeout, cancellation, and fallback rules
- Contract-test harness design

**Exit criteria:**

- Every kernel dependency is explicit and testable
- Privileged operations have authorization paths
- Unsupported or failed kernel features produce deterministic outcomes

---

## M3 — Minimal Deterministic User Space

**Goal:** Boot a usable non-AI user-space foundation on NovaKernel.

**Deliverables:**

- Initial runtime and first user-space process
- Init system and service manager
- IPC, configuration, session, shutdown, and restart foundations
- Minimal manual shell and diagnostic output
- Automated virtual-machine boot test

**Exit criteria:**

- NovaCortex OS boots to a stable user-space environment
- Services are supervised and shut down cleanly
- Basic operation does not require AI

---

## M4 — Core Control and Safety Layer

**Goal:** Implement the boundary through which all future AI actions must pass.

**Deliverables:**

- Capability registry
- Permission and policy engine
- Typed action schema
- Risk classification and approval flow
- Audit log, cancellation, verification, rollback, and safe mode

**Exit criteria:**

- Unauthorized actions fail closed
- Destructive actions cannot skip approval
- Actions can be traced, interrupted, and verified
- Safe mode works without the AI runtime

---

## M5 — Structured System State

**Goal:** Give the future AI an inspectable, permission-filtered model of the OS.

**Deliverables:**

- Resource and relationship graph
- Structured process, service, file, application, device, network, and user state
- Event model and state synchronization
- Sensitive-data filters
- Query and subscription interfaces

**Exit criteria:**

- Controllable components expose typed state and capabilities
- State changes produce structured events
- Stale, conflicting, or unauthorized context is detected

---

## M6 — From-Scratch AI Research Foundation

**Goal:** Make the project's AI rules technically enforceable and reproducible.

**Deliverables:**

- AI research charter and non-dependency policy
- Model and experiment versioning
- Reproducible environment and artifact format
- Baseline tasks, metrics, and immutable evaluation sets
- Compute and experiment budgeting policy

**Exit criteria:**

- Experiments start from project-owned architecture and initialization
- Runs record code, data, configuration, seed, environment, and results
- Dependency checks can detect prohibited AI artifacts and services

---

## M7 — Data and Representation Pipeline

**Goal:** Produce traceable training and evaluation inputs for a project-owned model.

**Deliverables:**

- Dataset specification and provenance ledger
- Licensed collection and synthetic-generation pipelines
- Privacy, secret, quality, filtering, and deduplication checks
- Project-owned tokenization or alternative representation system
- Versioned train, validation, and test splits
- System-state, action, language, conversation, and code representations

**Exit criteria:**

- Every accepted item has provenance and policy status
- Evaluation data is isolated from training
- Dataset and representation builds are reproducible

---

## M8 — First Project-Trained Learning Core

**Goal:** Train and run the first original NovaCortex model from project-owned initial weights.

**Deliverables:**

- Initial model architecture
- Parameter initialization and learning objectives
- Training, checkpointing, inference, and experiment-tracking tools
- Small-scale capability and failure evaluations
- Model card and limitation report

**Exit criteria:**

- The model runs locally without an external AI service
- Architecture, initialization, data, training, and evaluation are traceable
- Results beat documented non-intelligent or statistical baselines on selected tasks
- Failure modes are reported without overstating capability

---

## M9 — System Grounding and Memory

**Goal:** Connect the learning core to current OS state without granting action authority.

**Deliverables:**

- Permission-aware context assembly
- Short-term and persistent memory
- Memory provenance, correction, expiry, and deletion
- Structured system-state grounding
- Confidence, uncertainty, and stale-context detection

**Exit criteria:**

- The AI answers bounded system questions using current evidence
- Memory access obeys user and capability permissions
- Unsupported or uncertain claims are surfaced
- This milestone remains read-only

---

## M10 — Goal Understanding and Planning

**Goal:** Convert user goals into inspectable, constrained task graphs.

**Deliverables:**

- Goal and constraint representation
- Task decomposition and dependency planning
- Preconditions, postconditions, risk, and evidence requirements
- Replanning and cancellation logic
- Planner evaluation suite

**Exit criteria:**

- Plans use only registered capabilities
- Every planned action has explicit authorization and verification requirements
- Unsafe, impossible, or ambiguous goals are rejected or clarified
- Planning is evaluated without executing real changes

---

## M11 — Sandboxed Action Engine

**Goal:** Execute low-risk plans through the control layer in a contained environment.

**Deliverables:**

- Action executor and state machine
- Simulation and dry-run modes
- Result verification
- Failure compensation and bounded replanning
- End-to-end audit records

**Exit criteria:**

- Read-only and reversible multi-step tasks complete in a sandbox
- False success is detected
- Cancellation and rollback pass failure-injection tests
- The AI cannot bypass the action engine

---

## M12 — Conversational and Explanation System

**Goal:** Let the OS communicate goals, plans, progress, uncertainty, and outcomes.

**Deliverables:**

- Project-owned local text conversation pipeline
- Clarification and confirmation flows
- Action narration and progress reporting
- Evidence-based result and error explanations
- Initial project-owned voice pipeline research

**Exit criteria:**

- Bounded conversations run without a cloud AI service or pretrained model
- Required confirmations cannot be skipped
- Narration matches actual execution state
- Errors and uncertainty are clearly communicated

---

## M13 — Core System Services

**Goal:** Provide stable typed services for meaningful OS operation.

**Deliverables:**

- File, application, process, device, network, storage, settings, update, notification, and identity services
- Service capability schemas
- Permission and recovery integration
- Service contract and integration tests

**Exit criteria:**

- Services work manually and through typed actions
- Failures are isolated and observable
- Cross-service workflows are versioned and testable

---

## M14 — AI-Controlled System Operations

**Goal:** Safely perform useful multi-step OS work on real system services.

**Deliverables:**

- File organization and search workflows
- Application and service lifecycle workflows
- Settings and device workflows
- Resource diagnosis and approved optimization
- User policies for bounded automation

**Exit criteria:**

- Selected goals complete with authorization, audit, and verification
- Destructive, adversarial, and ambiguous cases fail safely
- Users can inspect and interrupt every active task

---

## M15 — Desktop, Shell, and Application Platform

**Goal:** Deliver a complete interactive operating environment.

**Deliverables:**

- Desktop and window/session environment
- Manual system shell
- AI conversation and activity surfaces
- Permission, audit, diagnostics, and recovery interfaces
- Application model, packaging, isolation, and SDK

**Exit criteria:**

- The system is usable with or without AI assistance
- AI work is visible and interruptible
- Applications declare capabilities and follow a secure lifecycle

---

## M16 — Intelligent Diagnostics and Recovery

**Goal:** Diagnose and recover from system failures using structured evidence.

**Deliverables:**

- Health monitoring and failure correlation
- Diagnostic evidence model
- Recovery planner and orchestrator
- Checkpoints, rollback, service recovery, and safe boot
- Recovery evaluation and failure injection

**Exit criteria:**

- Diagnoses reference observable evidence
- Recovery actions are risk-classified and verified
- Failed recovery preserves the original failure information
- Critical services have deterministic fallback behaviour

---

## M17 — AI-Assisted Codebase Maintenance

**Goal:** Let the AI understand and help maintain NovaCortex OS without granting silent deployment authority.

**Deliverables:**

- Codebase and dependency graph
- Interface and change-impact analysis
- Failure localization
- Reviewable patch proposals
- Isolated builds, tests, compatibility checks, and rollback plans

**Exit criteria:**

- Proposed changes include evidence and affected modules
- Changes build and test in isolation
- Trusted updates require explicit human approval
- The AI cannot directly rewrite the running trusted system

---

## M18 — Build, Image, and Update Infrastructure

**Goal:** Reproducibly assemble and update the complete OS.

**Deliverables:**

- Pinned NovaKernel integration
- User-space and model artifact builds
- Filesystem and bootable image assembly
- Signed update, rollback, and recovery path
- Software bill of materials
- Automated virtual-machine test matrix

**Exit criteria:**

- Builds reproduce from recorded inputs
- Kernel, model, data, and user-space identities are visible
- Failed updates recover to a known-good version
- Release images pass automated boot and integrity tests

---

## M19 — Security and Reliability Hardening

**Goal:** Validate the whole system under malicious input, component failure, and resource pressure.

**Deliverables:**

- Threat-model validation
- Permission and policy adversarial tests
- Prompt/action injection and confused-deputy tests
- Privacy, model, data, and supply-chain tests
- Failure injection, long-running stability, and performance benchmarks
- Independent review findings and remediation

**Exit criteria:**

- No open release-blocking security finding
- Safety, recovery, and safe-mode gates pass
- Known limitations are documented
- Performance meets approved minimum budgets

---

## M20 — Developer Preview

**Goal:** Release the first complete system for developers and researchers.

**Deliverables:**

- Versioned bootable image
- Supported virtual-machine or hardware target
- Installer or documented image setup
- Contributor, research, debugging, and recovery guides
- Model card, dataset cards, evaluation report, and release notes

**Exit criteria:**

- A new contributor can reproduce, boot, inspect, and test the release
- Core demos operate without external AI or pretrained models
- Safety and rollback paths are documented and verified
- The release is clearly labeled experimental

---

## M21 — NovaCortex OS 1.0

**Goal:** Deliver a stable, supportable AI-native operating system release.

**Deliverables:**

- Stable user-space, service, application, AI, and NovaKernel contracts
- Supported hardware and compatibility policy
- Signed reproducible releases and updates
- Published security, reliability, AI capability, and limitation reports
- Long-term maintenance and governance process

**Exit criteria:**

- All 1.0 release gates pass
- Recovery and safe-mode operation are dependable
- AI behaviour stays within published capability and safety limits
- The project can maintain the release without proprietary AI dependencies

---

## Milestone Dependency Chain

The expected dependency order is:

`M0 → M1 → M2 → M3 → M4 → M5 → M6 → M7 → M8 → M9 → M10 → M11 → M12 → M13 → M14 → M15 → M16 → M17 → M18 → M19 → M20 → M21`

Some research and documentation work may run in parallel, but privileged AI-controlled operation must not begin before M4, grounding must not begin before M5, and system action execution must not begin before the planner and sandbox gates pass.
