# Refactoring with Patterns (Senior Mindset)

## When to Consider a Pattern
- Repeated conditionals indicate Strategy or State.
- Large constructors with many optional params suggest Builder.
- Tight coupling to external APIs suggests Adapter or Facade.
- Direct object creation in many places suggests Factory Method.
- Cross-cutting features suggest Decorator or Chain of Responsibility.

## How to Refactor Safely
- Start with tests around current behavior.
- Extract interfaces for volatility (payment provider, storage client).
- Refactor incrementally: replace one call path at a time.
- Avoid over-engineering: patterns should reduce complexity, not add it.

## Example Refactor Paths
- Switch statements on type -> Strategy with a registry map.
- State-based if/else -> State pattern with explicit transitions.
- Deep object graph calls -> Facade to simplify API.
- Duplicated construction logic -> Builder or Abstract Factory.

## Risk Signals
- Pattern explosion: too many layers for simple cases.
- Premature abstraction without clear extension points.
- Overuse of inheritance when composition is simpler.
