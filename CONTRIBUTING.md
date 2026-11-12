# Contributing

Pentarix Base Component is a generic PHP project template focused on test-driven development and a small, explicit quality baseline.

## Development environment

Requirements:

- PHP 8.2+
- Composer 2.x

Install dependencies:

```bash
composer install
```

## Development workflow

For behaviour changes, prefer a test-first workflow:

1. Describe the required behaviour with a test.
2. Run the test and confirm that it fails for the expected reason.
3. Implement the smallest change needed to make it pass.
4. Refactor without changing the behaviour.
5. Run the complete quality gate.

The aim is to make tests describe expected behaviour rather than coupling them unnecessarily to implementation details.

## Verification

Run the complete local check:

```bash
composer check-all
```

This verifies formatting, PHPStan, Psalm, and PHPUnit.

Individual checks are available:

```bash
composer test
composer analyze:phpstan
composer analyze:psalm
composer format:check
```

Apply PHP CS Fixer formatting with:

```bash
composer format
```

After formatting, run `composer check-all` again.

## Tests

Production code belongs in `src/`; tests belong in `tests/`.

Use PHPUnit for automated tests. Keep tests deterministic and focused on observable behaviour. Prefer small tests with clear assertions, explicit inputs and outputs, and isolated unit tests where practical. Use integration tests when integration itself is the behaviour being verified.

Coverage can help identify untested areas, but a percentage is not a substitute for test quality.

## Static analysis

Both PHPStan and Psalm are part of the baseline. New production code should pass both analysers.

Do not add broad suppressions merely to make checks pass. Prefer fixing the underlying typing or design issue. If a suppression is genuinely necessary, keep it narrow and explain why it is required.

## Formatting

PHP CS Fixer is the formatting tool for this repository.

- Run `composer format` to apply formatting.
- Run `composer format:check` to verify formatting without modifying files.

Avoid unrelated formatting changes in a functional change.

## Project structure

Keep the top-level structure conventional:

```text
src/       production PHP
tests/     automated tests
```

Start with `tests/Unit/` when unit tests are appropriate. Add other test categories only when the project needs them.

Do not introduce framework-specific directories or infrastructure into the template itself.

## Dependencies and tooling

The baseline intentionally includes PHPUnit, PHPStan, Psalm, and PHP CS Fixer. Do not add another testing or analysis tool merely because it is popular; add infrastructure when the project has a demonstrated need for it.

Keep the template independent of frameworks and content-management systems. In particular, do not introduce WordPress-specific dependencies or assumptions into this generic PHP template.

## Pull requests

A good change should:

- solve one coherent problem;
- keep the change as small as practical;
- include or update tests when behaviour changes;
- preserve compatibility unless a breaking change is intentional;
- keep the template generic;
- update documentation when the development workflow changes.

Before opening a pull request, run:

```bash
composer check-all
```

Review the final diff for generated files, accidental dependencies, and unrelated changes.
