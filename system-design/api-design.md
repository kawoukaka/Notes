# API Design: REST, GraphQL, gRPC

## REST
- Architecture: resource-oriented, stateless, HTTP verbs represent actions.
- Data format: typically JSON; can be XML or others.
- Structure:
  - GET /users/123
  - POST /users
  - PUT /users/123
- Tradeoffs:
  - Simple and cache-friendly, but can over/under-fetch.
  - Versioning can be hard (URI vs header).
- Real-world usage:
  - Public APIs and CRUD services with broad client support.

## GraphQL
- Architecture: schema-driven query language with a single endpoint.
- Data format: JSON responses shaped by queries.
- Structure:
  - POST /graphql
  - Query includes fields and nested relationships.
- Tradeoffs:
  - Solves over/under-fetching but adds complexity.
  - Requires query cost controls and caching strategies.
- Real-world usage:
  - Client-driven data needs (mobile apps, complex UIs).

## gRPC
- Architecture: RPC over HTTP/2 with protobuf schemas.
- Data format: Protocol Buffers (binary).
- Structure:
  - Service definitions in .proto files.
  - Methods like GetUser, UpdateUser.
- Tradeoffs:
  - High performance and strong typing, but less browser-friendly.
  - Requires schema compilation and tooling.
- Real-world usage:
  - Internal microservices and latency-sensitive systems.
