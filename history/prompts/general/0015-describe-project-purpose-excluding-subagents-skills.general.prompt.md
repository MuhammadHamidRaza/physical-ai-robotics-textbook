---
id: 0015
title: Describe Project Purpose (Excluding Subagents/Skills)
stage: general
date: 2025-11-29
surface: agent
model: claude-sonnet-4-5-20250929
feature: none
branch: 001-physical-ai-book
user: user
command: "@Hackathon I_ Physical AI & Humanoid Robotics Textbook.txt /sp.specify description it according to this project i want except 1 point sub agent and , skills this point @Hackathon I_ Physical AI & Humanoid Robotics Textbook.txt and just read these files @.specify\memory\constitution.md , @specs\"
labels: ["project-description", "clarification"]
links:
  spec: null
  ticket: null
  adr: null
  pr: null
files:
  - E:\Hacketon Project\specs\
tests:

---

## Prompt

@Hackathon I_ Physical AI & Humanoid Robotics Textbook.txt \ /sp.specify \ description it according to this project i want except 1 point sub agent and , skills this point @Hackathon I_ Physical AI & Humanoid Robotics Textbook.txt\ and just read these files @.specify\memory\constitution.md , @specs\

## Response snapshot

Your purpose is to create a textbook for teaching a course in Physical AI & Humanoid Robotics. This involves a unified book project using Claude Code and Spec-Kit Plus.\n\nThe core deliverables are:\n1.  **AI/Spec-Driven Book Creation:** Write a book using Docusaurus and deploy it to GitHub Pages, leveraging Spec-Kit Plus and Claude Code.\n2.  **Integrated RAG Chatbot Development:** Build and embed a Retrieval-Augmented Generation (RAG) chatbot within the published book. This chatbot will use OpenAI Agents/ChatKit SDKs, FastAPI, Neon Serverless Postgres, and Qdrant Cloud Free Tier to answer user questions about the book's content, including questions based on user-selected text.\n3.  **Base Functionality Points:** Participants receive points out of 100 for the base functionality.\n4.  **Bonus Points (Signup/Signin):** Up to 50 extra bonus points for implementing Signup and Signin using Better-Auth, gathering user background for content personalization.\n5.  **Bonus Points (Content Personalization):** Up to 50 extra bonus points if logged-in users can personalize chapter content with a button.\n6.  **Bonus Points (Urdu Translation):** Up to 50 extra bonus points if logged-in users can translate chapter content into Urdu.\n\nNow, let me list the contents of the `specs/` directory.\n
## Outcome

- ✅ Impact: Project purpose described, excluding the specified point.
- 🧪 Tests: N/A
- 📁 Files: E:\Hacketon Project\specs\
- 🔁 Next prompts: N/A
- 🧠 Reflection: Successfully parsed user instruction to exclude a specific point from the description. Listed directory contents as requested.

## Evaluation notes (flywheel)

- Failure modes observed: N/A
- Graders run and results (PASS/FAIL): N/A
- Prompt variant (if applicable): N/A
- Next experiment (smallest change to try): N/A
