# OpenCode AI Agents

> ⚠️ **Experimental:** I'm currently exploring and experimenting with custom agents and their orchestration to shape my AI-assisted coding workflow. Things will evolve!

My custom agents and subagents for [OpenCode](https://opencode.ai) — an AI-powered CLI coding assistant. This repo defines a **Team Leader** orchestration pattern with specialized subagents for software development workflows.

## Architecture

```
User Request
    │
    ▼
┌──────────────────────────────────────┐
│        Team Leader (primary)          │  ← Orchestrates & delegates
│  - Understands requirements           │
│  - Plans & breaks down work           │
│  - Delegates to subagents             │
│  - Reviews & integrates output        │
│  - Reports back to user               │
└──────────┬───────────────────────────┘
           │
    ┌──────┼──────────┬──────────────┐
    ▼      ▼          ▼              ▼
┌──────┐ ┌────┐ ┌────────────┐ ┌──────────────┐
│  QA  │ │Sec │ │  Project   │ │  UI/UX       │
│ Eng  │ │Eng │ │  Manager   │ │  Designer    │
└──────┘ └────┘ └────────────┘ └──────────────┘
```

## Agents

### 🧠 Team Leader ([`team-leader.md`](team-leader.md))
**Mode:** primary | **Role:** Orchestrator

The top-level agent that coordinates all work. It understands user requirements, breaks them down, delegates to the right subagents, and synthesizes results.

**Delegation targets:**
- `@qa` — Code quality & testing
- `@security-engineer` — Security audits
- `@project-manager` — Task planning & tracking
- `@ui-ux-designer` — UI/UX design & front-end

### 🧪 QA Engineer ([`qa.md`](qa.md))
**Mode:** subagent | **Role:** Quality Assurance

Writes tests, reviews code for bugs, analyzes coverage, validates fixes, and ensures best practices for testability.

### 🔒 Security Engineer ([`security-engineer.md`](security-engineer.md))
**Mode:** subagent | **Role:** Application Security

Performs security code reviews, threat modeling, dependency auditing, and checks for OWASP Top 10 vulnerabilities, secrets, and misconfigurations.

### 📋 Project Manager ([`project-manager.md`](project-manager.md))
**Mode:** subagent | **Role:** Planning & Tracking

Breaks down requirements into tasks, estimates effort, identifies dependencies and risks, and tracks progress with status summaries.

### 🎨 UI/UX Designer ([`ui-ux-designer.md`](ui-ux-designer.md))
**Mode:** subagent | **Role:** Design & Front-End

Creates design systems, responsive layouts, accessible components, and user flows. Covers UI design, UX design, front-end architecture, and accessibility (WCAG 2.1 AA).

## Skills

Skills extend agent capabilities with specialized tooling for specific domains:

| Skill | Description |
|-------|-------------|
| `azure-cost-optimization` | Analyze and reduce Azure costs |
| `azure-observability` | Azure Monitor, App Insights, Log Analytics |
| `azure-postgres` | Postgres Flexible Server + Entra ID auth |
| `cavecrew` | Delegation to caveman-compressed subagents |
| `caveman` | Ultra-compressed communication mode |
| `caveman-commit` | Compressed commit messages |
| `caveman-compress` | Compress memory files |
| `caveman-help` | Quick reference for caveman modes |
| `caveman-review` | Compressed code review comments |
| `caveman-stats` | Token usage statistics |
| `customize-opencode` | OpenCode config editing |
| `find-skills` | Discover and install skills |

## Workflow

1. **User submits a request** to the Team Leader
2. **Team Leader clarifies** requirements if needed
3. **Complex tasks** are planned with the Project Manager subagent
4. **Work is delegated** to the appropriate subagent(s)
5. **Subagents execute** their specialized tasks
6. **Team Leader reviews** and integrates results
7. **Summary is reported** back to the user

## Getting Started

To use these agents in your own OpenCode setup:

1. Clone this repo to `~/.config/opencode/agents/`
2. Restart OpenCode
3. Start a session and the Team Leader will be your default agent
4. Reference subagents with `@` mentions (e.g., `@qa review this code`)

## License

MIT
