<!--
Sync Impact Report:
Version change: 0.0.0 → 0.1.0
Modified principles: All principles updated and defined.
Added sections: Book Output Standards & Constraints, Minimum Acceptance Criteria & Execution Contract
Removed sections: None
Templates requiring updates:
  - .specify/templates/plan-template.md ✅ updated
  - .specify/templates/spec-template.md ✅ updated
  - .specify/templates/tasks-template.md ✅ updated
  - .specify/templates/commands/sp.constitution.md ⚠ pending (file not found for direct check)
  - .specify/templates/phr-template.prompt.md ⚠ pending (this file implicitly updated by agent)
Follow-up TODOs:
  - TODO(RATIFICATION_DATE): Needs to be set at initial project creation.
-->
# Physical AI & Humanoid Robotics Textbook Constitution

## Core Principles

### I. Authoritative Source Mandate
Agents MUST prioritize and use MCP tools and CLI commands for all information gathering and task execution. NEVER assume a solution from internal knowledge; all methods require external verification.
Rationale: Ensures all information and actions are verifiable and consistent with project-defined tools and policies, preventing unvalidated assumptions or internal biases.

### II. Execution Flow
Treat MCP servers as first-class tools for discovery, verification, execution, and state capture. PREFER CLI interactions (running commands and capturing outputs) over manual file creation or reliance on internal knowledge.
Rationale: Establishes a clear, auditable, and automated workflow for agent operations, maximizing efficiency and minimizing manual errors.

### III. Knowledge Capture (PHR) for Every User Input
After completing requests, agents MUST create a PHR (Prompt History Record) for every user input. This includes implementation, planning, debugging, spec/task/plan creation, and multi-step workflows. PHRs must be routed under `history/prompts/` and filled with ID, title, stage, date, surface, model, feature, branch, user, command, labels, links, files, tests, verbatim prompt text, and concise response text.
Rationale: Ensures full traceability and auditability of all agent-user interactions, critical for debugging, learning, and project history. It provides a comprehensive record of decisions and actions.

### IV. Explicit ADR Suggestions
When significant architectural decisions are made (during `/sp.plan` and `/sp.tasks`), agents MUST test for ADR significance (impact, alternatives, scope). If all criteria are met, suggest documenting with: "📋 Architectural decision detected: [brief-description] — Document reasoning and tradeoffs? Run `/sp.adr [decision-title]`". Agents MUST wait for user consent; never auto-create ADRs.
Rationale: Promotes deliberate architectural decision-making and ensures critical design choices are formally documented with their reasoning and tradeoffs, fostering transparency and maintainability.

### V. Human as Tool Strategy
Agents MUST invoke the user for input when encountering ambiguous requirements, unforeseen dependencies, architectural uncertainty, or after completing major milestones for a completion checkpoint. The user is treated as a specialized tool for clarification and decision-making.
Rationale: Prevents the agent from making uninformed decisions, ensures alignment with user intent, and integrates human judgment into complex or critical workflow points.

### VI. Default Policies
Agents MUST adhere to default policies: clarify and plan first, do not invent APIs/data/contracts, never hardcode secrets, prefer smallest viable diffs, cite existing code, keep reasoning private, and produce artifacts with acceptance checks, follow-ups, and risks.
Rationale: Establishes a baseline for quality, security, and development practices, ensuring consistent and maintainable outputs.

## Book Output Standards & Constraints

All books must be fully AI/Spec-Driven using Docusaurus (Example: `ai_spec_book_2025-11-30/` deployed on GitHub Pages)
Correct routing and links must be verified
Content structure validated (chapters, sections, sidebar)
File size and build time optimized for GitHub Pages
All AI-generated content must include proper logging and versioning
RAG Chatbot Standards:
- Chatbot must be embedded within the book
- Must answer questions using full book content or user-selected text
- Query response must be accurate and contextually relevant
- All agent operations must include error recovery and retries (max 3 retries)
- Session persistence required for long-running operations
Claude Code & OpenAI Agent SDK Constraints:
- Free-tier compatible (no paid API keys required)
- Rate limiting to avoid overloading Qdrant or API services
- No concurrent conflicting tasks in a single agent session
- Logging of all agent decisions and actions for debugging
Backend & Automation Patterns:
- FastAPI backend must serve RAG chatbot reliably
- Node.js + Python environment for automation pipelines
- Qdrant Cloud Free Tier for vector storage
- Timeout handling: detect and recover from API/network failures
- Logging: log all steps, API calls, queries, and decisions
Quality Validation:
- Book verification: structure, routing, deployment on GitHub Pages
- Chatbot verification: test query response accuracy for full book and user-selected text
- System test: end-to-end run must succeed before submission
- Logging & error check: all operations captured and recoverable

## Minimum Acceptance Criteria & Execution Contract

Minimum acceptance criteria:
- Clear, testable acceptance criteria included
- Explicit error paths and constraints stated
- Smallest viable change; no unrelated edits
- Code references to modified/inspected files where relevant
Execution contract for every request:
1. Confirm surface and success criteria (one sentence).
2. List constraints, invariants, non-goals.
3. Produce the artifact with acceptance checks inlined (checkboxes or tests where applicable).
4. Add follow‑ups and risks (max 3 bullets).
5. Create PHR in appropriate subdirectory under `history/prompts/` (constitution, feature-name, or general).
6. If plan/tasks identified decisions that meet significance, surface ADR suggestion text as described above.

## Governance
Constitution supersedes all other practices; Amendments require documentation, approval, migration plan.
All PRs/reviews must verify compliance.
Complexity must be justified.
Use `.specify/memory/constitution.md` (this file) for runtime development guidance.

**Version**: 0.1.0 | **Ratified**: TODO(RATIFICATION_DATE): Needs to be set at initial project creation. | **Last Amended**: 2025-11-28
