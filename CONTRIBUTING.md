# Contributing to API Endpoints Plugin

## Development Setup

```bash
git clone https://github.com/markus-michalski/osticket-api-endpoints.git
cd osticket-api-endpoints
composer install
```

## Requirements

- PHP 8.1+
- osTicket 1.18.x (for integration testing)
- Composer

## Code Style

- **Language:** PHP 8.1+
- **Standard:** PSR-12
- **Comments:** English
- **Testing:** PHPUnit 10/11 with PHP 8 attributes (`#[Test]`, `#[CoversClass]`, `#[DataProvider]`)

## Architecture

Signal-based plugin architecture — no core modifications required:

```
plugin.php              # Plugin metadata
class.*.php             # Plugin classes
api/                    # API endpoint handlers
tests/                  # PHPUnit tests
```

### Adding a New API Endpoint

1. Create the endpoint handler in `api/`
2. Register the route via osTicket's signal system
3. Add granular API key permission if needed
4. Write tests (TDD preferred, 168 existing tests)

## Testing

```bash
# Run all tests
./vendor/bin/phpunit

# Run specific test file
./vendor/bin/phpunit tests/Unit/SomeTest.php

# With coverage
./vendor/bin/phpunit --coverage-text
```

## CI

GitHub Actions on push/PR to main: PHPUnit tests.

## Commits

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add new API endpoint
fix: correct a bug
docs: update documentation
refactor: restructure code
test: add or modify tests
```

## Pull Requests

1. Create a feature branch from `main`
2. Make your changes
3. Ensure all tests pass
4. Open a PR with a clear description

## License

GPL-2.0, compatible with osTicket core.
