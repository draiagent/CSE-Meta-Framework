# Security Policy

## Supported Versions

| Version | Supported |
|---|---|
| 1.0.x Draft / Release Candidate | Yes |
| Earlier experimental versions | No |

## Reporting a Vulnerability

Do not disclose security vulnerabilities in public Issues, Discussions, or Pull Requests.

Report privately to the Repository owner or designated security contact. Include:

- Affected version
- Affected component
- Risk description
- Reproduction steps
- Potential impact
- Suggested mitigation, if available

## Response Process

```text
Receive
  ↓
Acknowledge
  ↓
Assess
  ↓
Contain
  ↓
Fix
  ↓
Validate
  ↓
Release
  ↓
Review
```

## Security Scope

Security reports may include:

- Secret exposure
- Excessive permissions
- Unsafe defaults
- Prompt injection risk
- External tool misuse
- Data leakage
- Dependency or supply-chain risk
- Irreversible action without confirmation
- Logging of confidential or restricted data

## Security Requirements

- Secrets must not be committed to the Repository.
- External operations must use least privilege.
- High-risk or irreversible actions require human review.
- Security findings classified as Critical block release.
- Security fixes require validation and CHANGELOG updates.

See [Security Standard](./docs/13-security-standard.md).

## Disclosure

Security details may be limited until a fix or mitigation is available.
