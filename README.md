
# CoPilot instructions

Include in .github folder with each project and CoPilot will include with prompts to drive consistency, maintainability and correctness of the code genereated.
Standards being enforced explained below...

## Java Code Layout

final on method parameters: Makes method contracts clearer by preventing reassignment inside the method.

No final on locals: Avoids clutter—local immutability is usually obvious.

Use var for locals (Java 10+): Improves readability by reducing type verbosity.

Annotations (@Override, @Serial): Enforce correctness (avoiding silent errors in overrides, ensuring proper serialization).

serialVersionUID in serializable classes: Ensures compatibility across versions.

No wildcard imports: Avoids ambiguity and reduces unintended dependencies.

No Lombok: Prevents hidden complexity and build tool coupling.

Formatting rules (line length, indentation, spacing, braces, import ordering): Improve readability and prevent “style wars.”

Qualified imports instead of inline fully qualified names: Keeps code cleaner while avoiding excessive verbosity.

## Logging

Use SLF4J: Standardized, flexible, and decoupled from the logging backend.

Parameterized logging: Improves performance and readability.

Log levels: Enforce discipline in what gets logged (debug for flow, info for events, warn for recoverable issues, error for failures).

No sensitive data in logs: Protects security and compliance.

## Method Parameter Ordering

Standard ordering (data → properties → helpers → context): Improves predictability and readability.

Copy-type methods use from–to order: Matches natural language and common conventions.

## Spring

Constructor injection only: Easier to test, promotes immutability, avoids hidden dependencies.

Configuration via constructor parameters (@Value): Keeps dependencies explicit and testable.

## Testing
### Frameworks and Conventions

JUnit 5: Modern, flexible, and widely adopted.

AssertJ for assertions: Fluent, readable assertions.

Parameterized tests: Encourage broader test coverage without code duplication.

Naming: CamelCase + test prefix improves discoverability.

@DisplayName: Makes test reports more readable.

### Coverage

All public methods tested: Encourages full API coverage.

Edge and typical cases: Ensures robustness.

No private method testing: Tests should verify behavior, not implementation details.

### Mocking

Mockito (BDDMockito, MockConstruction, MockStatic): Enables clean, isolated unit testing.

Field-based @Mock / @InjectMocks: Standardized and concise.

Avoid MockitoAnnotations and JUnit 4 runners: Outdated practices.

Exception testing with assertThatExceptionOfType: Clearer, more readable.

### Cucumber

JUnit Platform (@Suite) instead of old runners: Keeps tests aligned with modern JUnit 5 practices.

Externalize config in junit-application.properties: Centralizes test configuration, avoids duplication.

Standard reporting plugins: Ensures consistent test reports across environments.

## SQL
### Code Layout

Keyword alignment: Improves readability of complex queries.

Lowercase keywords, tables, columns: Consistency, avoids case-sensitivity pitfalls.

String literals unchanged: Prevents unintended data corruption.

as for column aliases, but not table aliases: Matches SQL style conventions.

Consistent join syntax (Oracle vs ANSI): Prevents optimizer inconsistencies.

Hints respected (/*+ ... */): Ensures performance tuning is not lost.

Parentheses around OR conditions: Avoids logical errors due to operator precedence.

from dual for table-less selects: Required by Oracle.

## Why These Rules Exist

Many rules are not just about “style”:

Consistency across teams → Easier onboarding, fewer merge conflicts.

Predictable Copilot output → AI-generated code follows standards automatically.

Readability & maintainability → Developers spend less time interpreting style, more on logic.

Correctness & safety → Prevents subtle bugs (e.g., missed @Override, wrong operator precedence in SQL).

Security & compliance → Prevents sensitive data leaks and enforces disciplined logging.