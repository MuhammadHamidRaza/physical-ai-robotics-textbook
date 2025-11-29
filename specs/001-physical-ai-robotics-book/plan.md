# Implementation Plan: Physical AI & Humanoid Robotics Textbook

**Branch**: `001-physical-ai-robotics-book` | **Date**: 2025-11-29 | **Spec**: specs/001-physical-ai-robotics-book/spec.md
**Input**: Feature specification from `/specs/001-physical-ai-robotics-book/spec.md`

**Note**: This template is filled in by the `/sp.plan` command. See `.specify/templates/commands/plan.md` for the execution workflow.

## Summary

The primary objective is to create an AI/Spec-Driven textbook on Physical AI & Humanoid Robotics using Docusaurus, deployed on GitHub Pages. This includes an integrated RAG chatbot, user authentication with Better-Auth, and features for content personalization and Urdu translation. The technical approach involves a Docusaurus frontend, a FastAPI backend for the RAG chatbot, and utilizing Qdrant Cloud Free Tier for vector storage.

## Technical Context

**Language/Version**: Python 3.9+ (for FastAPI, RAG components), Node.js 18+ (for Docusaurus)
**Primary Dependencies**: Docusaurus, FastAPI, OpenAI Agents/ChatKit SDKs, Qdrant Client, Better-Auth client libraries. (Neon Serverless Postgres will be evaluated if specific relational data needs arise beyond vector storage.)
**Storage**: Qdrant Cloud Free Tier (vector database for RAG), Local browser storage (for user personalization settings and possibly some cached translated content), Filesystem (for book content).
**Testing**: Pytest (for FastAPI backend), Playwright/Jest (for Docusaurus frontend, depending on framework choice within Docusaurus), Contract testing (for API interactions).
**Target Platform**: Web (GitHub Pages for Docusaurus, Cloud hosting for FastAPI backend).
**Project Type**: Multi-project (Docusaurus static site frontend, FastAPI REST API backend).
**Performance Goals**:
- Book build time: Under 5 minutes (SC-009).
- Chatbot response accuracy: 90% for factual questions (SC-004), 85% for selected text questions (SC-005).
- FastAPI backend uptime: 99.9% (SC-011).
**Constraints**:
- Free-tier compatible (no paid API keys required for core components).
- Rate limiting implemented for Qdrant and API services.
- No concurrent conflicting tasks in a single agent session.
- All AI-generated content includes proper logging and versioning (FR-005).
**Scale/Scope**: Educational textbook for a Physical AI & Humanoid Robotics course, supporting an unspecified number of readers, with an emphasis on a functional RAG chatbot and basic user personalization features.

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- [x] **Authoritative Source Mandate:** All information gathering and task execution must prioritize and use MCP tools and CLI commands. (Adhered to by using tools and explicit instructions)
- [x] **Execution Flow:** All interactions should prefer CLI and MCP tools over manual file creation or internal knowledge. (Adhered to by using `Write`, `Read`, `Bash`)
- [x] **Knowledge Capture (PHR):** Ensure PHRs are planned for every significant user interaction throughout the planning and implementation phases. (PHRs are being created for each significant step)
- [x] **Explicit ADR Suggestions:** Identify and flag any architecturally significant decisions for potential ADR documentation. (Will be vigilant for ADR opportunities during planning)
- [x] **Human as Tool Strategy:** Plan for explicit user input at points of ambiguity, unforeseen dependencies, architectural uncertainty, or major milestones. (Demonstrated in clarification phase)
- [x] **Default Policies:**
    - [x] Clarify and plan first. (Done with `/sp.specify` and `/sp.clarify`)
    - [x] Do not invent APIs, data, or contracts; ask targeted clarifiers if missing. (Adhered to)
    - [x] Never hardcode secrets or tokens; use `.env` and docs. (Will be followed during implementation)
    - [x] Prefer the smallest viable diff; do not refactor unrelated code. (Will be followed during implementation)
    - [x] Cite existing code with code references; propose new code in fenced blocks. (Will be followed during implementation)
    - [x] Produce the artifact with acceptance checks inlined (checkboxes or tests where applicable). (Will be followed in tasks.md)
    - [x] Add follow‑ups and risks (max 3 bullets). (Will be included in the final plan report)

## Project Structure

### Documentation (this feature)

```text
specs/001-physical-ai-robotics-book/
├── plan.md              # This file (/sp.plan command output)
├── research.md          # Phase 0 output (/sp.plan command)
├── data-model.md        # Phase 1 output (/sp.plan command)
├── quickstart.md        # Phase 1 output (/sp.plan command)
├── contracts/           # Phase 1 output (/sp.plan command)
└── tasks.md             # Phase 2 output (/sp.tasks command - NOT created by /sp.plan)
```

### Source Code (repository root)

```text
docusaurus-book/
├── src/
│   ├── components/      # React components for Docusaurus
│   ├── pages/           # Docusaurus pages (e.g., chatbot integration)
│   └── theme/           # Custom Docusaurus theme overrides
├── docs/                # Markdown content for the textbook
├── static/              # Static assets (images, CSS)
└── docusaurus.config.js # Docusaurus configuration

fastapi-backend/
├── src/
│   ├── models/          # Pydantic models for data (e.g., user profiles, query requests)
│   ├── services/        # Business logic for RAG, personalization, translation
│   ├── api/             # FastAPI endpoints
│   └── data/            # Local data management for user profiles, Qdrant client
└── tests/
    ├── api/
    ├── unit/
    └── integration/

.github/workflows/       # GitHub Actions for CI/CD (Docusaurus deploy, FastAPI deploy)
```

**Structure Decision**: A monorepo-like structure with `docusaurus-book/` for the frontend and `fastapi-backend/` for the backend, co-located at the repository root. This aligns with the Node.js + Python environment requirement and provides clear separation of concerns while allowing for integrated deployment. The `data` directory in the FastAPI backend will manage local user profiles for personalization, as per clarification. CI/CD workflows will be defined in `.github/workflows/`.

## Complexity Tracking

No justified violations of the Constitution Check at this planning stage. All policies are adhered to.
