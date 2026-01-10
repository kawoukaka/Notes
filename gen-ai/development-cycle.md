# GenAI Development Cycle

## 1. Problem Framing
- Define task scope, failure tolerance, and acceptable error rates.
- Select evaluation metrics (accuracy, usefulness, latency, cost).

## 2. Data and Context Strategy
- Identify sources for retrieval (docs, DBs, APIs).
- Decide on chunking, embedding strategy, and re-ranking.
- Define freshness and update cadence.

## 3. Prompt and Tool Design
- Create prompt templates with clear instructions and examples.
- Define tool schemas with strict validation and error handling.
- Use system prompts for global behavior; keep user prompts minimal.

## 4. Prototyping and Evaluation
- Build a minimal pipeline (prompt + retrieval + model).
- Run offline evals with golden datasets.
- Use human review for subjective metrics.

## 5. Hardening for Production
- Add guardrails (PII checks, safety filters, rate limits).
- Introduce caching and timeouts.
- Implement fallback strategies and retries.

## 6. Launch and Monitoring
- Track quality metrics (helpfulness, accuracy, refusal rate).
- Monitor drift in retrieval and model outputs.
- Capture feedback signals and retrain or re-tune.

## 7. Iteration
- Update prompts and retrieval sources based on evals.
- Rebalance latency vs accuracy with model routing.
- Automate regression tests for new prompts.
