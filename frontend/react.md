# React (Senior Engineer Notes)

## Rendering and Performance
- Identify render boundaries; use memoization only when measured.
- Avoid prop drilling for high-churn state; use context sparingly.
- Use `useMemo` and `useCallback` to stabilize expensive computations, not as defaults.

## State Management
- Separate server state (React Query/SWR) from UI state.
- Co-locate state near usage to reduce rerenders.
- Prefer state machines for complex UI flows.

## Effects and Data Fetching
- Keep effects idempotent; guard with dependencies.
- Cancel in-flight requests on unmount or param change.
- Handle partial failures with retry budgets and fallback UI.

## Component Architecture
- Build presentational vs container components to isolate data concerns.
- Prefer composition over inheritance.
- Keep shared components in a design system with stable APIs.

## Accessibility
- Always support keyboard navigation and focus states.
- Use ARIA only when semantics are missing.
- Test with screen readers for critical flows.

## Performance at Scale
- Use virtualization for long lists.
- Defer non-critical work (lazy loading, code splitting).
- Monitor Web Vitals; optimize LCP and INP.

## Testing
- Test user behavior with `@testing-library/react`.
- Keep snapshot tests minimal; focus on interactions.
- Add visual regression tests for critical views.

## Real-World Patterns
- Progressive rendering with skeletons to reduce perceived latency.
- Feature flags for staged rollouts.
- Error boundaries around risky components.
