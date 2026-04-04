# Security Hardening Notes

## Configuration

- keep checked-in settings placeholder-based
- move machine-specific values to environment variables or local-only overrides
- never commit live passwords, tokens, or signed URLs

## Development

- avoid logging secrets or connection strings
- keep Swagger and debug endpoints limited to development scenarios
- review sample payloads before publishing them

## Repository Hygiene

- scan for secrets before pushing
- prefer short-lived local credentials
- remove accidental leaks from history, not only from the current tree
