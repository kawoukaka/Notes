# GenAI Glossary and Real-World Usage

## MCP (Model Context Protocol)
- Definition: standard protocol for tools/resources provided to models.
- Usage: integrate filesystem, databases, and APIs as model tools.
- Example: IDE copilots using MCP to access project files for code changes.

## A2A (Agent-to-Agent)
- Definition: agents collaborating with each other via explicit protocols.
- Usage: delegate research, planning, and execution across specialized agents.
- Example: one agent gathers requirements, another generates code, a third reviews.

## RAG (Retrieval-Augmented Generation)
- Definition: combine retrieval with generation for grounded answers.
- Usage: knowledge bases, support docs, internal tooling.
- Example: customer support assistant retrieving policy docs before responding.

## Multi-Modal
- Definition: models that accept multiple input types (text, images, audio).
- Usage: document understanding, image QA, OCR + reasoning.
- Example: invoice processing where model reads scanned documents.

## Tool Calling / Function Calling
- Definition: model invokes structured tools with validated inputs.
- Usage: database queries, API calls, workflows.
- Example: ops assistant that calls a deployment API.

## Prompt Engineering
- Definition: crafting prompts to steer model behavior.
- Usage: improve task reliability and format adherence.
- Example: structured JSON outputs for downstream parsers.

## Embeddings
- Definition: vector representations for semantic similarity.
- Usage: search, clustering, deduplication.
- Example: semantic search over product catalogs.

## Vector Database
- Definition: database optimized for vector similarity search.
- Usage: semantic retrieval at scale.
- Example: RAG over internal documents with hybrid search.

## Re-Ranking
- Definition: reorder retrieved results using a stronger model.
- Usage: improve answer accuracy in RAG.
- Example: re-rank top 50 documents to the best 5.

## Guardrails
- Definition: safety and policy constraints around model outputs.
- Usage: PII redaction, toxicity filtering, schema validation.
- Example: block or redact sensitive data before returning responses.

## Hallucination
- Definition: model outputs content not grounded in source data.
- Usage: mitigated via RAG, verification, or citations.
- Example: require citations for factual claims.

## RLHF / RLAIF
- Definition: alignment via human or AI feedback loops.
- Usage: steer behavior toward helpfulness and safety.
- Example: fine-tune a support bot with human-rated conversations.

## Agents
- Definition: LLMs that plan, call tools, and iterate on tasks.
- Usage: multi-step workflows and automation.
- Example: report generation that queries DB, writes summary, and sends email.
