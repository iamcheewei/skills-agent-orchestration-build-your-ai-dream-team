# Agent team

I will use GitHub Copilot CLI in a Codespace to orchestrate the work of this custom agent team to build Mona's Project Pulse dashboard.

| Agent | Target model | Responsibility | Definition |
| --- | --- | --- | --- |
| Orchestrator | Claude Opus 5.5 (copilot) | Breaks the request into phases, delegates work to specialists with clear file ownership, coordinates dependencies and validation, and confirms the final integration. | `.github/agents/orchestrator.agent.md` |
| Planner | Claude Opus 5.5 (copilot) | Researches the repo and requirements, identifies edge cases, and produces the implementation plan with phases, dependencies, and validation expectations. | `.github/agents/planner.agent.md` |
| Designer | Gemini 3.7 Flash (copilot) | Defines the dashboard experience, visual hierarchy, accessibility, and polished card-based frontend styling. | `.github/agents/designer.agent.md` |
| Coder | GPT-5.5 (copilot) | Implements the app files and launch configuration, then validates the static dashboard behavior. | `.github/agents/coder.agent.md` |

The team works together in sequence: the Orchestrator sets the scope and delegates tasks, the Planner creates a concrete implementation plan, the Designer shapes the UI and accessibility approach, and the Coder builds the project files and runnable dashboard. Once the app files and launch configuration are in place, the Orchestrator verifies the integration, checks the relevant paths, and confirms the dashboard is ready for Mona's team.
