<div align="center">

# NovaCortex OS

### A Complete Open-Source AI-Native Operating System Built From Scratch

NovaCortex OS is an operating system in which a project-owned system AI understands the machine, turns user goals into safe actions, explains its work, and helps maintain the OS itself.

![Status](https://img.shields.io/badge/status-planning-yellow)
![AI](https://img.shields.io/badge/AI-built%20from%20scratch-purple)
![Kernel](https://img.shields.io/badge/kernel-NovaKernel-blue)
![Architecture](https://img.shields.io/badge/architecture-x86__64-lightgrey)
![License](https://img.shields.io/badge/license-MIT-green)

</div>

---

## Project Status

NovaCortex OS is in the research, specification, and architecture phase. It is not yet ready for production use.

The project is intentionally ambitious: both the operating system and its central AI are being developed as original, open-source systems. Early releases will focus on verifiable foundations rather than broad autonomy.

---

## Vision

NovaCortex OS is not a conventional operating system with a chatbot attached to it. The system AI is a first-class part of the operating environment.

A user should be able to describe an outcome, such as preparing a development workspace, diagnosing a slow system, organizing files, or configuring an application. The AI will inspect structured system state, create a constrained plan, request authorization when needed, execute actions through controlled OS interfaces, verify the result, and explain what happened.

The long-term goal is an operating system that can:

- Understand its services, applications, files, processes, devices, policies, and codebase
- Communicate through text, voice, and graphical interfaces
- Perform multi-step system work for the user
- Explain its current actions, decisions, uncertainty, failures, and results
- Diagnose problems and coordinate safe recovery
- Help maintain the NovaCortex OS codebase through reviewable changes
- Remain usable in a deterministic safe mode when the AI is unavailable

---

## Foundational Rule: The AI Is Built From Scratch

NovaCortex OS will not use an existing AI product as its system intelligence.

The project's AI commitment means:

- No OpenAI, Anthropic, Google, or other cloud AI API will provide the OS intelligence
- No pretrained language model, foundation model, or externally trained checkpoint will be used as the core or fallback intelligence
- Model architecture and initial weights will be owned and produced by this project
- Language and system representations, tokenization, training pipelines, memory, reasoning, planning, decision-making, and conversation systems will be designed and developed within the project
- Training data must have documented provenance, licensing, filtering, and evaluation
- Model behaviour must be reproducible, inspectable, testable, and replaceable
- AI research decisions and limitations will be documented openly

General-purpose compilers, programming-language runtimes, system libraries, testing tools, and other non-AI infrastructure may be used when approved and documented. They are implementation tools, not a substitute for the project-owned AI.

This rule is an architectural boundary, not a marketing claim. A feature that depends on a proprietary model, remote inference service, or pretrained checkpoint is not part of the NovaCortex OS core.

---

## Kernel: NovaKernel

NovaCortex OS uses [NovaKernel](https://github.com/dev-collaboration-hub/NovaKernel) as its kernel.

NovaKernel is a separate, from-scratch, modular, AI-aware kernel. It provides deterministic, low-level mechanisms and enforces safety boundaries. The kernel does not contain the central AI.

### NovaKernel Owns

- Boot and hardware initialization
- Interrupt and exception handling
- Physical and virtual memory management
- Processes, threads, scheduling, and context switching
- System calls and privilege separation
- Kernel-level device drivers
- Filesystem and networking mechanisms
- Security enforcement
- Structured kernel events and telemetry
- Validated interfaces for AI-requested operations
- Kernel recovery and safe fallback mechanisms

### NovaCortex OS Owns

- The complete user-space operating environment
- The from-scratch AI architecture and runtime
- Data preparation, model training, evaluation, and versioning
- System understanding, memory, reasoning, and planning
- Conversation and action explanation
- Permission, policy, audit, verification, and rollback coordination
- System services, desktop, shell, and applications
- Diagnostics and recovery orchestration
- Codebase understanding and maintenance assistance
- NovaKernel integration
- Bootable image assembly and end-to-end releases

Kernel source code is not developed or duplicated in this repository. NovaCortex OS consumes a tested NovaKernel release or pinned commit through a documented compatibility contract.

> The NovaCortex AI understands, plans, coordinates, and explains. NovaKernel validates and executes low-level operations.

---

## How the System AI Works

The AI operates on structured state and declared capabilities instead of receiving unrestricted machine access.

1. **Observe** — Read relevant, permission-filtered system state.
2. **Understand** — Interpret the goal, context, constraints, and uncertainty.
3. **Plan** — Produce an inspectable task graph with preconditions and expected results.
4. **Authorize** — Apply capability, policy, risk, and user-approval checks.
5. **Execute** — Call NovaCortex OS services and validated NovaKernel interfaces.
6. **Verify** — Compare real outcomes with expected postconditions.
7. **Explain** — Report actions, evidence, failures, recovery, and final state.

The AI cannot declare success without verification, and its output is never treated as kernel authority.

---

## Core AI Subsystems

### Learning Core

Project-owned model architecture, parameter initialization, optimization, training, checkpointing, and inference.

### System Understanding

A structured representation of processes, services, files, applications, devices, resources, policies, events, source modules, and kernel interfaces.

### Memory and Context

Permission-aware short-term and persistent memory with provenance, retention, invalidation, and user-control rules.

### Goal Understanding and Planning

Conversion of user requests into constrained goals, task graphs, dependencies, preconditions, postconditions, and recovery paths.

### Action Engine

Execution of typed system actions through capability-controlled services, with cancellation, audit, verification, and rollback.

### Conversation and Explanation

Text and voice interaction, clarification, confirmation, progress narration, uncertainty reporting, and evidence-based explanations.

### Diagnostics and Maintenance

Failure correlation, recovery planning, codebase mapping, dependency analysis, isolated builds, test execution, and reviewable maintenance proposals.

---

## System Architecture

```text
User
  |
  v
Text, Voice, and Graphical Interfaces
  |
  v
NovaCortex AI
  |- Learning and Inference
  |- System Understanding and Memory
  |- Goal Reasoning and Planning
  |- Conversation and Explanation
  |- Diagnostics and Codebase Maintenance
  |
  v
AI Control and Safety Layer
  |- Capability Registry
  |- Permission and Policy Engine
  |- Risk Classification and Approval
  |- Audit, Verification, and Rollback
  |
  v
NovaCortex OS Services
  |- Applications, Files, Processes, and Sessions
  |- Devices, Networking, Settings, and Updates
  |- Desktop, Shell, Notifications, and Recovery
  |
  v
NovaKernel Integration Layer
  |
  v
NovaKernel
  |
  v
Hardware
```

---

## Safety Principles

- The AI has no unrestricted access to kernel memory, hardware, credentials, or user data
- Every system operation is represented as a typed, inspectable action
- Privileged actions pass through capability and policy checks
- Destructive and security-critical actions require explicit authorization
- Sensitive operations produce tamper-evident audit records
- Reversible operations use checkpoints or rollback data where possible
- Users can inspect, interrupt, limit, or disable AI-controlled work
- AI failures are isolated from the kernel and critical services
- The OS provides deterministic manual and safe-mode operation
- AI-proposed code changes are built and tested in isolation
- Trusted system components cannot be silently replaced by the AI

---

## Repository Scope

### In Scope

- From-scratch AI research, architecture, training, inference, and evaluation
- Training-data governance and reproducible dataset pipelines
- Conversation, memory, system understanding, reasoning, and planning
- Capability registry, action engine, policy, audit, and recovery
- User-space runtime, init, services, sessions, and configuration
- Desktop environment, shell, applications, and developer SDK
- Diagnostics and codebase-maintenance systems
- NovaKernel integration contracts and compatibility tests
- Bootable OS images, updates, releases, and end-to-end tests
- Architecture, security, research, and contributor documentation

### Out of Scope

- NovaKernel implementation
- Kernel scheduler, memory manager, drivers, interrupts, networking, or filesystem internals
- Direct AI inference inside critical kernel execution paths
- Proprietary or cloud-hosted AI as system intelligence
- Pretrained third-party models or checkpoints as core or fallback intelligence
- Silent autonomous deployment of changes to trusted components

Kernel work belongs in the [NovaKernel repository](https://github.com/dev-collaboration-hub/NovaKernel).

---

## Planned Repository Structure

```text
NovaCortex-OS/
├── ai/
│   ├── architecture/
│   ├── representations/
│   ├── learning/
│   ├── inference/
│   ├── memory/
│   ├── understanding/
│   ├── planning/
│   ├── conversation/
│   ├── diagnostics/
│   └── maintenance/
├── data/
│   ├── specifications/
│   ├── pipelines/
│   ├── provenance/
│   └── validation/
├── training/
│   ├── experiments/
│   ├── checkpoints/
│   ├── evaluation/
│   └── reproducibility/
├── control/
│   ├── capabilities/
│   ├── permissions/
│   ├── policies/
│   ├── audit/
│   └── recovery/
├── system/
│   ├── runtime/
│   ├── init/
│   ├── services/
│   ├── session/
│   └── configuration/
├── services/
├── shell/
├── desktop/
├── apps/
├── sdk/
├── integration/novakernel/
├── image/
├── tests/
├── tools/
├── docs/
└── scripts/
```

The structure will evolve through architecture decision records and milestone reviews.

---

## Development Strategy

Development is organized around evidence-based gates:

1. Define project boundaries, safety invariants, and the NovaKernel contract.
2. Boot a deterministic minimal user space before introducing AI control.
3. Build structured system state, capabilities, permissions, audit, and recovery.
4. Establish reproducible data, training, and evaluation infrastructure.
5. Train the first project-owned model from project-owned initial weights.
6. Add memory, system understanding, conversation, and constrained planning.
7. Expand AI-controlled operations only after safety and correctness evaluations pass.
8. Build the desktop, application platform, diagnostics, and maintenance intelligence.
9. Integrate, harden, test, and release the complete OS.

No milestone is complete only because a demo works. Each milestone requires documented interfaces, tests, failure behaviour, and acceptance evidence.

---

## Documentation

- [Detailed Documentation Roadmap](docs/documentation-roadmap.md)
- [Engineering Milestones](docs/milestones.md)

The roadmap defines what must be specified. The milestones define the order in which validated system capabilities will be delivered.

---

## Immediate Priorities

1. Approve the project vision, scope, terminology, and non-goals.
2. Define the NovaCortex OS–NovaKernel integration contract.
3. Define the from-scratch AI research charter and reproducibility rules.
4. Define the permission, action, audit, verification, rollback, and safe-mode models.
5. Design the minimal deterministic user-space runtime.
6. Establish measurable acceptance criteria for the first AI learning experiments.

---

## Contributing

NovaCortex OS welcomes contributors in operating systems, machine learning research, security, compilers, user interfaces, developer tooling, testing, data governance, and technical documentation.

Before contributing:

1. Read the scope, roadmap, and relevant architecture documents.
2. Check open issues and active milestones.
3. Discuss major architectural or research changes before implementation.
4. Keep kernel implementation in NovaKernel.
5. Do not introduce pretrained models or external AI-service dependencies.
6. Include tests, evaluation results, and documentation with system-level changes.
7. Preserve permission, audit, verification, recovery, and reproducibility guarantees.

---

## Related Project

- [NovaKernel](https://github.com/dev-collaboration-hub/NovaKernel) — the from-scratch, modular, AI-aware kernel used by NovaCortex OS.

---

## License

NovaCortex OS is released under the MIT License.

---

<div align="center">

Built by the Dev Collaboration Hub open-source community.

</div>
