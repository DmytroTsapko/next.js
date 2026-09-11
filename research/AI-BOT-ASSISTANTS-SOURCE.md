# AI BOT / ASSISTANTS — SOURCE

Дата: 2026-09-11
Владелец исследовательского контура: DmytroTsapko

## Назначение

Каталог открытых GitHub-проектов, относящихся к AI-ассистентам, LLM-агентам, автономным агентам, chatbot-системам, tool-calling, памяти, MCP, multi-agent orchestration и локальным AI-системам.

Цель — использовать репозитории как источники для архитектурного анализа. Наличие слова AI/agent в README само по себе не считается доказательством конкретной реализации: код и структура проекта проверяются отдельно.

## Классификация доказательств

- CONFIRMED — функциональность подтверждается кодом/структурой репозитория.
- CLAIMED — заявлена в README/описании, но код ещё не проверен.
- REFERENCE — каталог/список, полезный для обнаружения проектов; не доказательство реализации конкретного проекта.

## Основной контур

### 1. AI assistants / chatbots

- iOfficeAI/AionUi — AI assistant application.
- AstrBotDevs/AstrBot — bot/assistant platform.
- sigoden/aichat — terminal AI chat/assistant.
- agentscope-ai/QwenPaw — personal AI assistant.
- libraryofcelsus/Aetherius_AI_Assistant — personal AI assistant.
- hoangsonww/AI-RAG-Assistant-Chatbot — RAG assistant/chatbot.
- aws-samples/sample-ai-assistant-on-agentcore — reference implementation of an AI assistant.

Status: CLAIMED until repository code is inspected for the specific capability being studied.

### 2. Autonomous / LLM agents

- Significant-Gravitas/AutoGPT — autonomous-agent framework/project.
- ruvnet/ruflo — multi-agent/agent orchestration framework.
- HKUDS/nanobot — lightweight personal AI agent framework with tools, memory, MCP and multi-agent workflows.
- Fosowl/agenticSeek — local autonomous agent.
- agentscope-ai/agentscope — agent framework with multi-agent and MCP capabilities.
- microsoft/autogen — framework for agentic AI.

### 3. Local AI / self-hosted assistants

Relevant projects include nanobot, QwenPaw, agenticSeek and other repositories tagged with local-llm, llm-agents and personal-ai-assistant.

### 4. Agent infrastructure

Important architectural areas to extract from source code:

- model adapters
- tool/function calling
- planning and task decomposition
- memory/state
- RAG/vector retrieval
- MCP/tool servers
- browser/computer interaction
- multi-agent coordination
- permissions and execution boundaries
- logging/evaluation
- configuration and model routing

## Independent discovery sources

- GitHub topic: autonomous-agents — thousands of public repositories.
- GitHub topic: llm-agents — thousands of public repositories.
- GitHub topic: personal-ai-assistant — dozens of focused repositories.
- xufei547/awesome-ai-assistants — curated list of AI personal assistants and autonomous agents.
- KORAYTEACHER/awesome-agents — curated agent ecosystem list.
- GagnDeep/awesome-best-open-source-ai-agents-2026 — 2026 GitHub-first agent catalog.

These lists are discovery indexes, not proof that every listed capability exists in executable code.

## Research extraction schema

For every candidate repository, record:

1. Repository
2. URL
3. Default branch
4. License
5. Primary language
6. Last update
7. Claimed purpose
8. Confirmed model providers
9. Confirmed agent loop
10. Confirmed tools/actions
11. Confirmed memory/state
12. Confirmed RAG
13. Confirmed MCP
14. Confirmed multi-agent architecture
15. Confirmed automation/browser/device control
16. Relevant source files
17. Evidence excerpts
18. CLAIMED vs CONFIRMED classification
19. Security/permission boundaries
20. Relevance to our architecture

## Important separation

Do not infer AI capability from names such as `ai`, `model`, `agent`, `strategy`, `predict`, `ml`, `neural` or `gpt`. Each claim must be tied to source evidence.

Do not treat a repository README, star count, topic tag or marketing statement as proof of a hidden algorithm, neural model, autonomous decision system or production capability.

## Scope restriction

This source is intentionally focused on general AI assistants and agent architectures. It does not provide operational instructions for gambling, betting or other age-restricted financial-risk activities.

## Next research pass

For each high-priority repository, inspect:

- repository tree
- README
- package/dependency manifests
- agent/core directories
- model/provider adapters
- tool definitions
- memory/state implementation
- orchestration loop
- tests
- configuration
- security/permission controls

Then upgrade individual entries from CLAIMED to CONFIRMED only where source evidence supports the claim.

## Initial evidence basis

The initial shortlist was discovered through GitHub repository search and current public GitHub topic/catalog pages on 2026-09-11. Repository names and descriptions are discovery evidence; implementation status requires direct code inspection.
