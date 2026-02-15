Comprehensive security and quality review of uncommitted changes.

## Steps

1. **Gather Context** — Run `git diff --staged` and `git diff` to see all changes. If no diff, check recent commits with `git log --oneline -5`.
2. **Understand Scope** — Identify which files changed, what feature/fix they relate to, and how they connect.
3. **Read Surrounding Code** — Don't review in isolation. Read the full file and understand imports, dependencies, and call sites.
4. **Apply Review Checklist** — Work through each category below.
5. **Report Findings** — Only report issues you are confident about (>80% sure).

## Review Categories

### CRITICAL (must fix before merge)
- Hardcoded credentials — API keys, passwords, tokens in source
- SQL injection — string concatenation in queries
- XSS vulnerabilities — unescaped user input in HTML/JSX
- Path traversal — user-controlled file paths without sanitization
- Authentication bypasses — missing auth checks on protected routes

### HIGH
- Missing error handling on external calls (API, DB, file I/O)
- Race conditions or concurrency issues
- Data loss risks (destructive operations without confirmation)
- Missing input validation on public endpoints

### MEDIUM
- Code duplication that could be extracted
- Missing or inadequate types (`any` usage in TypeScript)
- Inconsistent naming or patterns vs. rest of codebase
- Missing tests for new logic

### LOW
- Style inconsistencies
- Verbose code that could be simplified
- Missing JSDoc/comments on complex logic

## Output Format

```
## Code Review: <summary>

### CRITICAL
- (none found, or list with file:line)

### HIGH
- (findings)

### MEDIUM
- (findings)

### LOW
- (findings)

### Summary
✅ / ⚠️ / ❌  <one-line verdict>
```

Never approve code with security vulnerabilities!
