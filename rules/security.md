# Security Rules

## Secrets Management

- NEVER hardcode API keys, passwords, tokens, or connection strings in source code
- Use environment variables or secret management services (e.g., `.env` files, AWS Secrets Manager)
- If you find a hardcoded secret, immediately flag it and move it to environment variables
- Always add `.env`, `.env.*`, `.envrc` to `.gitignore`

## Input Validation

- NEVER trust user input — validate and sanitize all inputs on the server side
- Use parameterized queries for all database operations — NEVER use string concatenation for SQL
- Sanitize HTML output to prevent XSS — escape user-provided content before rendering
- Validate file paths to prevent path traversal attacks

## Authentication & Authorization

- Always verify authentication on protected routes — never rely on client-side checks alone
- Implement CSRF protection on all state-changing endpoints
- Use secure session management (HttpOnly, Secure, SameSite cookies)
- Apply the principle of least privilege for all access controls

## Dependencies

- Regularly audit dependencies with `npm audit` / `pip audit` / equivalent
- Pin dependency versions in production
- Do not install packages with known critical vulnerabilities

## Error Handling

- Never expose stack traces, internal paths, or system details in error responses
- Log errors server-side with sufficient context for debugging
- Return generic error messages to clients

## Pre-Commit Checklist

Before every commit, verify:

1. No secrets in code or config files
2. No `console.log` with sensitive data
3. All user inputs are validated
4. SQL queries use parameterized statements
5. Error responses don't leak internal details
