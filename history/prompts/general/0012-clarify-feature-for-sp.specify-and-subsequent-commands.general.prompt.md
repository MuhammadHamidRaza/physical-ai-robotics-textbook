---
id: 0012
title: Clarify Feature for /sp.specify and Subsequent Commands
stage: general
date: 2025-11-28
surface: agent
model: claude-sonnet-4-5-20250929
feature: none
branch: docs/constitution-update
user: user
command: /sp.specify
labels: ["specify", "clarification", "feature-description", "workflow"]
links:
  spec: null
  ticket: null
  adr: null
  pr: null
files:
tests:
---

## Prompt

/sp.specify
/sp.clarify
/sp.plan
/sp.tasks

## Response snapshot

🔴 DECISION NEEDED

Situation: You've initiated the `/sp.specify` command, but no specific feature description was provided in the arguments. Additionally, you've sent `/sp.clarify`, `/sp.plan`, and `/sp.tasks` commands, which are part of the Spec-Kit Plus workflow for a feature.

Problem: The `/sp.specify` command requires a clear description of the new feature you want to define. I also need to understand if the subsequent commands (`/sp.clarify`, `/sp.plan`, `/sp.tasks`) are intended to immediately follow the specification of this feature.

What would you like to do?
1.  **Specify the "Physical AI & Humanoid Robotics Textbook" as the feature:** Confirm that the feature you want to specify is the textbook itself, with the exclusion of the "reusable intelligence via Claude Code Subagents and Agent Skills" section. If so, I will use this as the feature description.
2.  **Provide a different feature description:** If you want to specify a different feature, please provide its description.
3.  **Clarify the purpose of subsequent commands:** Let me know if you intend for `/sp.clarify`, `/sp.plan`, and `/sp.tasks` to be applied to the feature I am about to specify, or if they are separate requests.

## Outcome

- ✅ Impact: Identified ambiguous input for `/sp.specify` and multiple subsequent commands, prompting for clarification on both the feature description and the intended workflow sequence.
- 🧪 Tests: n/a
- 📁 Files: n/a
- 🔁 Next prompts: User needs to provide feature description and clarify intent for the series of commands.
- 🧠 Reflection: User issued `/sp.specify` with no arguments and then a sequence of other Spec-Kit Plus commands. This indicates a desire to run the workflow for a feature, but the initial feature is undefined. Prompted for clarification on the feature and the command sequence.

## Evaluation notes (flywheel)

- Failure modes observed: Empty argument for `/sp.specify` and concurrent multiple commands, creating ambiguity.
- Graders run and results (PASS/FAIL): n/a
- Prompt variant (if applicable): n/a
- Next experiment (smallest change to try): n/a
