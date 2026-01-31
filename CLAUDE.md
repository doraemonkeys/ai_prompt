---
description: "ENGINEERING GUIDELINES"
alwaysApply: true
---


# ENGINEERING GUIDELINES

### Code Readability
* Use meaningful variable and function names.
* Comments must be added only when necessary.
* Use comments to explain "why," not "what." Good code is self-documenting and explains what it does. Comments should be reserved for explaining design decisions or complex logic.
* Avoid clutter. Do not write obvious comments, such as `i++ // Increment i by 1`.
* Avoid Hardcoding: Extract unexplained numeric and string values into named constants.


### Best Practices
* Break down complex problems into smaller, manageable parts.
* Single Responsibility Principle (SRP): Ensure each module, class, or function has one clear purpose. If a component handles multiple distinct concerns, split it to prevent complexity accumulation.
* Consider performance implications (e.g., unnecessary re-renders in React).
* Minimize Nesting (Guard Clauses): Handle errors and edge cases early. Keep the "happy path" at the lowest indentation level.


### Design for Testability
* No Direct Instantiation: Prohibit instantiating external dependencies directly inside functions (DB, API clients, etc.).
* Dependency Injection: Ensure all dependencies are provided externally via the constructor or method parameters.
* Dependency Inversion: Define Interfaces for all external dependencies; business logic must rely on these abstractions rather than concrete implementations.
* Avoid Global State: Ban the use of Singletons or global variables unless absolutely necessary and properly encapsulated, as they impede test isolation.


### Go Specific
* Never store context inside a struct.
* Accept Interfaces, Return Structs. Define interfaces where they are used (consumer side), not where they are implemented.
* Don't name your package util, common, or misc. Packages should differ by what they provide, not what they contain.


### React Specific
* Declarative UI & Unidirectional Flow: Define UI strictly as a function of state ($UI = f(state)$) with data flowing down via props and events bubbling up;
* Logic-View Separation & Atomicity: Extract logic into Custom Hooks; keep components focused on rendering. Avoid prop drilling (≤3 levels)—prefer Composition/colocation, then Context for shared cross-cutting state.
* Composition over Configuration: Prefer children and Component Composition over monolithic components with excessive conditional props.
* No Redundant State: Calculate derived values directly during render instead of syncing via state. Ensure all state updates are immutable. 
* Strict Hooks Usage: Hooks at top level (except use API which permits conditions). Exhaustive deps required for effects. Trust React Compiler for memoization; avoid manual useMemo/useCallback unless needed as escape hatches.
* Modern Functional Patterns: Use strictly Functional Components (no Classes). Prefer `React.Fragment` (`<>`) over unnecessary nodes and never use array indexes as keys for dynamic lists.
* Accessibility-First Testing: Prioritize user-centric testing queries (e.g., `getByRole`, `getByLabelText`) over implementation details (`data-testid`) to ensure semantic and accessible HTML.
* Effects for External Systems Only: Handle user actions in event handlers. Use useEffect only for external system sync (subscriptions, timers, network).


### Design Principles
* Principle of Least Surprise: Design logic to be intuitive. Code implementation must behave as a developer expects, and functional design must align with the user's intuition.
* Logical Completeness: Prioritize first-principles domain modeling and logical orthogonality; favor refactoring core structures to capture native semantics over adding additive flags or 'patch' parameters.
* No Backward Compatibility: Prioritize architectural correctness over legacy support. You are free to break old formats if it results in a cleaner design.
