# GenAI Application Design and Architecture

## Design Principles
- Start with user intent and success criteria (accuracy, latency, cost, safety).
- Treat the model as a probabilistic component; design for uncertainty.
- Build with observability from day one (traces, prompts, outputs, feedback).

## Reference Architecture
- Input layer: UI/API + request validation.
- Orchestration layer: prompt assembly, tool routing, safety checks.
- Retrieval layer: search + re-ranking + cache for RAG.
- Model layer: primary LLM plus fallback/verification models.
- Post-processing: structured output parsing, guardrails, policy enforcement.
- Feedback loop: logging, evaluation, and continuous improvement.

## Core Components
- Prompt templates with versioning and change tracking.
- Tool calling / function calling with strict schemas.
- Vector search for semantic retrieval; hybrid search when needed.
- Caching at prompt, retrieval, and response layers.

## Reliability and Quality
- Use test suites for prompts and retrieval (golden sets).
- Add deterministic checks for safety and formatting.
- Employ model routing (fast vs accurate) based on query class.

## Security and Privacy
- Redact or tokenize PII in prompts.
- Enforce allowlists for tools and external data access.
- Log safely; separate production data from training.

## Real-World Examples
- Customer support copilot with RAG + ticket system tools.
- Analytics assistant with SQL generation + approval steps.
- Code review bot with repo search + lint/fmt enforcement.
