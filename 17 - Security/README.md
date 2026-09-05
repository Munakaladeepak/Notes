# Security Fundamentals

**Priority:** High · **Prerequisite:** [[11 - REST and HTTP/README|REST and HTTP]] · **Related:** [[05 - MySQL and SQL/README|SQL]], [[04 - PHP/README|PHP]]

## Security model

Authentication verifies identity. Authorization checks permissions. Accounting/auditing records relevant actions. Role-based access control groups permissions by role. Least privilege limits damage. Defense in depth uses multiple independent controls.

## Input and output

All client input is untrusted, including hidden fields and frontend validation. Validate type, length, format, range, ownership, and business rules server-side. Use parameterized SQL. Contextually escape output for HTML, JavaScript, CSS, or URLs. Sanitization is context-dependent, not a universal substitute for validation.

## Common vulnerabilities

**SQL injection** changes database commands through input; use prepared statements. **XSS** executes attacker-controlled script in a victim’s browser; encode output and use safe rendering. **CSRF** tricks a browser with existing credentials into an unwanted action; use same-site cookies and anti-CSRF controls where applicable. **Broken access control** occurs when a user accesses another user’s record by changing an ID; always enforce ownership/permission on the server.

## Identity and secrets

Hash passwords with a slow adaptive password-hashing algorithm. HTTPS protects data in transit. Secure, HttpOnly, and SameSite cookie flags reduce common session risks. JWT is a signed token format and must still be protected, expired, scoped, and revoked/rotated according to risk. Keep API keys and cloud credentials in secret managers.

## API and operational security

Use rate limiting, request-size limits, secure headers, narrow CORS, dependency updates, audit logs, alerting, and safe error responses. Do not log passwords, access tokens, or unnecessary personal data. Rotate secrets after exposure. Apply patches and review permissions regularly.

## Threat-thinking checklist

For every feature ask: What assets are protected? Who is the actor? What input is controlled by them? What authorization is required? What happens if the request is repeated? What gets logged? What is the failure mode? What is the recovery path?

## Checklist

- [ ] Authentication, authorization, RBAC, least privilege
- [ ] Server-side validation and output encoding
- [ ] SQL injection and prepared statements
- [ ] XSS and CSRF
- [ ] Broken access control and IDOR
- [ ] Password hashing and secure sessions
- [ ] HTTPS, JWT/session awareness
- [ ] CORS, rate limiting, secure headers
- [ ] Secret handling, logging, patching
