# AWS AI/LLM Services

## Amazon Bedrock
- Usage: managed access to foundation models with tooling and guardrails.
- Real-world: build RAG apps and chatbots without managing model servers.
- Limits: model availability and throughput are region- and quota-limited.

## SageMaker (Training and Inference)
- Usage: custom model training, batch inference, real-time endpoints.
- Real-world: ML pipelines with managed training jobs and endpoints.
- Limits: instance quotas, endpoint concurrency, and payload sizes vary by instance type.

## Amazon Comprehend
- Usage: NLP for entity extraction, sentiment, PII detection.
- Real-world: support ticket triage and compliance scanning.
- Limits: document size and batch size limits apply; check service quotas.

## Amazon Textract
- Usage: OCR and structured data extraction from documents.
- Real-world: invoice and form processing.
- Limits: page count and document size limits apply per API.

## Amazon Rekognition
- Usage: image/video analysis (labels, faces, moderation).
- Real-world: content moderation pipelines.
- Limits: max file size and rate limits depend on API.

## Amazon Polly
- Usage: text-to-speech.
- Real-world: voice assistants and accessibility.
- Limits: text size limits per request.

## Amazon Transcribe
- Usage: speech-to-text.
- Real-world: call center analytics and meeting transcription.
- Limits: media length and format limits apply.

## Amazon Translate
- Usage: machine translation.
- Real-world: multilingual support and localization.
- Limits: text size limits per request.

## Amazon Kendra
- Usage: enterprise search and semantic retrieval.
- Real-world: internal knowledge base search for RAG.
- Limits: index size and query throughput quotas apply.

## Amazon OpenSearch (Vector Search)
- Usage: vector similarity search for embeddings.
- Real-world: semantic search and RAG retrieval.
- Limits: shard and memory limits; tune for vector workloads.
