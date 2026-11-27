# AI Engineering Toolkit — AI Agents, MCP, RAG & LLM Tools

[![Awesome](https://awesome.re/badge.svg)](https://github.com/sindresorhus/awesome)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: CC0-1.0](https://img.shields.io/badge/license-CC0--1.0-lightgrey.svg)](LICENSE)

Open-source tools I'd reach for when building and shipping AI applications: AI agents, MCP servers, RAG, model serving, evaluations, backend APIs and AWS deployment.

This isn't a dump of every repo with "LLM" in the description. It's a short list, grouped by the job you're trying to get done, with a line on when each project is the right pick. Licences come from GitHub. "See repository" means GitHub couldn't classify the licence file, so read it before you adopt the project. Anything that needs a hosted service or has unusual licence terms says so.

## Contents

- [Start here](#start-here)
- [AI agent frameworks and MCP](#ai-agent-frameworks--mcp)
- [RAG, vector search and agent memory](#rag-vector-search--agent-memory)
- [Local LLMs and model serving](#local-llms--model-serving)
- [LLM evaluation and observability](#llm-evaluation--observability)
- [AI coding agents and developer workflows](#ai-coding-agents--developer-workflows)
- [Backend APIs and full-stack integration](#backend-apis--full-stack-integration)
- [AWS, Docker and production deployment](#aws-docker--production-deployment)
- [Contributing](#contributing)
- [Related lists](#related-lists)

## Start here

Three common paths, depending on where you are.

| You want to | Try this |
|---|---|
| Build your first agent | Pick a framework from [Agent frameworks](#agent-frameworks), give it one tool through an [MCP SDK](#mcp-sdks-and-servers), and run the model locally with [Ollama](https://github.com/ollama/ollama) while you iterate. |
| Add retrieval | If you already run PostgreSQL, start with [pgvector](https://github.com/pgvector/pgvector). Convert your documents with [MarkItDown](https://github.com/microsoft/markitdown). Move to a dedicated engine like [Qdrant](https://github.com/qdrant/qdrant) once retrieval needs its own service. |
| Test and trace in production | Trace calls with [Langfuse](https://github.com/langfuse/langfuse) or [Phoenix](https://github.com/Arize-ai/phoenix), then catch prompt regressions in CI with [Promptfoo](https://github.com/promptfoo/promptfoo). |

## AI agent frameworks & MCP

### Agent frameworks

- [Pydantic AI](https://github.com/pydantic/pydantic-ai) — Typed Python agents. A natural fit if your services already use Pydantic and FastAPI. MIT.
- [LangGraph](https://github.com/langchain-ai/langgraph) — For agents that need real control flow: branches, retries, and a human approving a step. MIT.
- [OpenAI Agents SDK](https://github.com/openai/openai-agents-python) — A small Python SDK built around handoffs between agents and guardrails on their inputs and outputs. MIT.
- [CrewAI](https://github.com/crewAIInc/crewAI) — Model a task as a team of role-based agents without writing the orchestration yourself. MIT.
- [Agno](https://github.com/agno-agi/agno) — Agents with memory and tools that you run as a service, not a script. Apache-2.0.
- [Inngest](https://github.com/inngest/inngest) — Durable workflows, so an agent's steps survive crashes and retries. Licence: see repository.

### MCP SDKs and servers

MCP (Model Context Protocol) is the open protocol that lets an agent call outside tools and read outside data through one standard interface.

- [MCP Python SDK](https://github.com/modelcontextprotocol/python-sdk) — The official way to write MCP servers and clients in Python. MIT.
- [MCP TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) — The same thing for Node.js and TypeScript. Licence: see repository.
- [FastMCP](https://github.com/PrefectHQ/fastmcp) — A decorator-style layer on top of the Python SDK. Less boilerplate for servers and clients. Apache-2.0.
- [MCP Inspector](https://github.com/modelcontextprotocol/inspector) — Poke at an MCP server by hand before you let an agent loose on it. Licence: see repository.
- [MCP reference servers](https://github.com/modelcontextprotocol/servers) — Working examples worth reading before you write your own. Licence: see repository.
- [MongoDB MCP Server](https://github.com/mongodb-js/mongodb-mcp-server) — Lets an agent query and inspect MongoDB or Atlas. Apache-2.0.

## RAG, vector search & agent memory

- [MarkItDown](https://github.com/microsoft/markitdown) — Turns Office files, PDFs and other documents into Markdown before you chunk and index them. MIT.
- [Firecrawl](https://github.com/firecrawl/firecrawl) — Crawls websites into clean text for ingestion. The repo is AGPL-3.0, and there is also a hosted API. AGPL-3.0.
- [LlamaIndex](https://github.com/run-llama/llama_index) — Data connectors and retrieval pipelines for a lot of different document sources. MIT.
- [pgvector](https://github.com/pgvector/pgvector) — Vector similarity search inside an existing PostgreSQL database. Licence: see repository.
- [Qdrant](https://github.com/qdrant/qdrant) — A dedicated vector engine with payload filtering, run as its own service. Apache-2.0.
- [Weaviate](https://github.com/weaviate/weaviate) — Stores objects and vectors together and supports hybrid search. Licence: see repository.
- [Milvus](https://github.com/milvus-io/milvus) — A distributed engine for very large vector collections. Apache-2.0.
- [Cognee](https://github.com/topoteretes/cognee) — Long-term memory for agents, built as a knowledge graph over your documents. Apache-2.0.

## Local LLMs & model serving

- [Ollama](https://github.com/ollama/ollama) — Run open models on a laptop with one command and a local API. MIT.
- [llama.cpp](https://github.com/ggml-org/llama.cpp) — Quantised inference on modest hardware, including CPU-only machines. MIT.
- [vLLM](https://github.com/vllm-project/vllm) — Serve LLMs to many users at once when throughput matters. Apache-2.0.
- [Unsloth](https://github.com/unslothai/unsloth) — Fine-tune open models faster and with less GPU memory. Apache-2.0.
- [Open WebUI](https://github.com/open-webui/open-webui) — A self-hosted chat interface for Ollama or any OpenAI-compatible API. Check the licence terms before rebranding it. Licence: see repository.

## LLM evaluation & observability

- [Langfuse](https://github.com/langfuse/langfuse) — Trace model calls and agent steps, then turn those traces into evaluation datasets. Self-hosted or cloud. Licence: see repository.
- [Phoenix](https://github.com/Arize-ai/phoenix) — Inspect traces and evaluate retrieval and model behaviour from a notebook or a service. Licence: see repository.
- [Promptfoo](https://github.com/promptfoo/promptfoo) — Repeatable prompt and agent regression checks, including in CI. MIT.
- [Ragas](https://github.com/vibrantlabsai/ragas) — Metrics for scoring retrieval-augmented generation pipelines. Apache-2.0.

## AI coding agents & developer workflows

- [Claude Code plugins (official)](https://github.com/anthropics/claude-plugins-official) — The plugins Anthropic maintains for Claude Code, and a good template for writing your own. Apache-2.0.
- [claude-mem](https://github.com/thedotmack/claude-mem) — Keeps context between Claude Code sessions so you stop re-explaining the project. Apache-2.0.
- [Context Mode](https://github.com/mksglu/context-mode) — Keeps bulky tool output out of a coding agent's context window. Licence: see repository.
- [Herdr](https://github.com/herdrdev/herdr) — A runtime for running several coding agents side by side. Apache-2.0.

## Backend APIs & full-stack integration

- [FastAPI](https://github.com/fastapi/fastapi) — Typed Python APIs for serving models, agents and streaming responses. MIT.
- [NestJS](https://github.com/nestjs/nest) — Structured Node.js services that put model calls behind injectable providers. MIT.
- [Vercel AI SDK](https://github.com/vercel/ai) — Streaming, tool calling and a provider-agnostic API for TypeScript and React apps. Licence: see repository.

## AWS, Docker & production deployment

- [SST](https://github.com/anomalyco/sst) — Define and deploy full-stack apps on your own AWS account from TypeScript. MIT.
- [AWS CDK](https://github.com/aws/aws-cdk) — Describe AWS infrastructure in TypeScript or Python instead of YAML. Apache-2.0.
- [act](https://github.com/nektos/act) — Run GitHub Actions workflows locally before you push. MIT.
- [SigNoz](https://github.com/SigNoz/signoz) — OpenTelemetry-native traces, logs and metrics in one self-hosted tool. Licence: see repository.

## Contributing

Suggestions are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) first; it's short. The rule of thumb is one project per pull request, a public repository, and one honest sentence about when someone should pick it.

## Related lists

- [Awesome](https://github.com/sindresorhus/awesome) — the index of awesome lists this one follows.
- [Awesome AWS AI Engineering](https://github.com/arslanramay/awesome-aws-ai-engineering) — the AWS-focused companion list: Bedrock, AgentCore, Strands, SageMaker and CDK.
- [Awesome LLM Apps](https://github.com/Shubhamsaboo/awesome-llm-apps) — runnable LLM, agent and RAG apps to learn from.
