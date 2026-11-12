# Pentarix Base Component

Pentarix Base Component is a **generic PHP project template for test-driven development (TDD)**.

It provides a conventional starting structure and an essential development-quality toolchain, so a new PHP project can begin with tests, static analysis, and consistent formatting from its first commit.

This template is intentionally independent of any framework, CMS, or frontend stack. It has no WordPress integration and introduces no application architecture.

## What you get

The baseline includes four development tools:

- **PHPUnit** — automated tests.
- **PHPStan** — static analysis.
- **Psalm** — an independent static-analysis pass.
- **PHP CS Fixer** — consistent PHP formatting.

The tools are integrated with Composer scripts:

```bash
composer install
composer check-all
```

## Requirements

- PHP 8.2 or newer.
- Composer 2.x.
- For HTML coverage reports: **Xdebug** or **PCOV** enabled in the PHP environment.

## Create a project from this template

Use GitHub's **Use this template** action to create a repository, then clone your new repository.

After creating the project, review the following items before starting development:

1. **Project identity:** update the Composer package name, description, keywords, homepage, and support links in `composer.json`.
2. **Namespaces:** replace the placeholder `App\` and `Tests\` PSR-4 namespaces with the namespaces used by your project. Update directory names if required.
3. **PHP support:** review the `php` constraint in `composer.json` and the PHP version matrix in `.github/workflows/ci.yml`. Keep them aligned with the versions you intend to support.
4. **Dependencies:** add only the runtime and development dependencies your project needs.
5. **Install dependencies:** run `composer install`.
6. **Example code:** replace or remove `src/Example.php` and `tests/Unit/ExampleTest.php`.
7. **Tool configuration:** review `phpunit.xml`, `phpstan.neon`, `psalm.xml`, and `.php-cs-fixer.dist.php`.
8. **Verification:** run `composer check-all` and review the CI workflow for your project.

Keep `"type": "project"` in Composer for an application or project repository. Change it only if you deliberately turn the repository into a distributable Composer package.

## Development workflow

The template supports a simple TDD loop:

1. Write a test describing the required behaviour.
2. Run it and confirm that it fails for the expected reason.
3. Implement the smallest change that makes it pass.
4. Refactor while keeping the tests green.
5. Run static analysis and formatting checks.

The template provides the development foundation; the project remains responsible for its own domain model and architecture.

## Composer commands

| Command | Purpose |
| --- | --- |
| `composer test` | Run the PHPUnit test suite. |
| `composer test:coverage` | Generate an HTML coverage report under `build/coverage/`. |
| `composer analyze:phpstan` | Run PHPStan. |
| `composer analyze:psalm` | Run Psalm. |
| `composer format` | Apply PHP CS Fixer formatting. |
| `composer format:check` | Check formatting without changing files. |
| `composer check-all` | Run formatting verification, PHPStan, Psalm, and PHPUnit. |
| `composer audit` | Check installed dependencies against known security advisories. |

### Code coverage

The coverage command requires a code-coverage driver. Install and enable [Xdebug](https://xdebug.org/docs/install) or [PCOV](https://github.com/krakjoe/pcov).

Coverage is a diagnostic tool, not a substitute for meaningful tests. The template does not impose an arbitrary coverage percentage.

### Dependency lock file

This repository intentionally does not include `composer.lock`, because it is a reusable project template. Once you create a real project, run `composer install` and commit the generated lock file to make dependency resolution reproducible for that project.

## Configuration

| Area | File | Baseline |
| --- | --- | --- |
| Composer identity and dependencies | `composer.json` | PHP 8.2+, PSR-4 autoloading, development tools, and quality scripts. |
| PHPUnit | `phpunit.xml` | Discovers tests under `tests/` and measures source under `src/`. |
| PHPStan | `phpstan.neon` | Level 8 analysis of production source. |
| Psalm | `psalm.xml` | Analyses production and test code. |
| PHP CS Fixer | `.php-cs-fixer.dist.php` | Repository formatting rules. |
| CI | `.github/workflows/ci.yml` | PHPUnit across the configured PHP matrix, plus quality checks. |

Adjust these settings to suit the actual project. Prefer fixing underlying typing or design issues over introducing broad static-analysis suppressions.

## Project structure

```text
.
├── src/
│   └── Example.php
├── tests/
│   └── Unit/
│       └── ExampleTest.php
├── .github/
│   └── workflows/
│       └── ci.yml
├── .editorconfig
├── .gitignore
├── .php-cs-fixer.dist.php
├── composer.json
├── phpstan.neon
├── phpunit.xml
├── psalm.xml
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

Production code belongs under `src/`; automated tests belong under `tests/`. Add integration or functional test directories only when the project has a real need for them.

## Design principles

- **Generic PHP:** no framework, CMS, or WordPress dependency.
- **No prescribed application architecture:** choose structures that fit the actual domain.
- **Small development baseline:** use tools with clear, distinct responsibilities.
- **Test-first development:** make behaviour explicit through tests.
- **Maintainability:** favour clear code, explicit checks, and narrow configuration.
- **No unnecessary runtime dependencies:** the template should not dictate the dependencies of the project built from it.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for development and verification guidance.

## Licence

This project is licensed under the MIT Licence. See [LICENSE](LICENSE).
