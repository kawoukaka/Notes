# Search and Recommendations

## Search Systems
- Index pipeline: ingest -> normalize -> index.
- Query pipeline: parse -> retrieve -> rank -> highlight.

## Ranking
- Combine lexical match (BM25) with business signals.
- Use learning-to-rank for large catalogs.

## Recommendations
- Collaborative filtering: user-item interactions.
- Content-based: metadata similarity.
- Hybrid: combine both with business rules.

## Real-World Examples
- Product search with filters and facets.
- News feed ranking with freshness and diversity.
- Personalized recommendations with cold-start handling.

## Senior Notes
- Maintain separate offline evaluation and online A/B testing.
- Keep explainability for user trust and debugging.
- Index rebuilds should be incremental to avoid downtime.
