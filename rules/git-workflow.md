# Git Workflow Rules

## Commit Messages

Use Conventional Commits format:

```
<type>(<scope>): <description>

[optional body]
```

Types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`, `perf`, `ci`

Examples:
- `feat(auth): add OAuth login flow`
- `fix(api): handle null response from payment service`
- `refactor(db): extract query builder into utility`

Rules:
- Subject line: imperative mood, max 72 characters, no period
- Body: explain *what* and *why*, not *how*
- One logical change per commit — don't bundle unrelated changes

## Branching

- `main` — production-ready code, always deployable
- `feat/<name>` — new features
- `fix/<name>` — bug fixes
- `refactor/<name>` — code improvements without behavior change

## Pull Requests

Before creating a PR:

1. Run all tests and confirm they pass
2. Run the linter and fix any issues
3. Self-review the diff — remove debug code, console.logs, commented-out code
4. Write a clear PR description: what changed, why, and how to test

## Pre-Push Checklist

1. `git diff --staged` — review what you're committing
2. No `.env` files, secrets, or credentials in the diff
3. No unrelated changes mixed in
4. Tests pass locally
5. Commit message follows convention
