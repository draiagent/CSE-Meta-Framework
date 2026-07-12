# Contributing

Thank you for contributing to CSE Meta Framework.

## Contribution Scope

Accepted contributions include:

- Corrections to core documents
- Cross-reference and terminology fixes
- Validation cases
- Templates
- Examples
- Security improvements
- Release and migration improvements

Changes that expand the framework scope must follow the governance process.

## Before You Start

1. Read [Philosophy](./docs/00-philosophy.md).
2. Read [Design Principles](./docs/03-design-principles.md).
3. Read [Document Standards](./docs/05-document-standards.md).
4. Read [Governance Standard](./docs/12-governance-standard.md).
5. Open or reference an Issue for significant changes.

## Contribution Process

```text
Issue
  ↓
Proposal
  ↓
Change
  ↓
Validation
  ↓
Review
  ↓
Merge
```

## Pull Request Requirements

A Pull Request should include:

- Summary
- Change type
- Related Issue
- Affected files
- Scope impact
- Compatibility impact
- Security impact
- Validation result
- Migration notes, if required

## Change Classification

| Level | Type | Examples |
|---|---|---|
| 1 | Editorial | Typo, formatting, broken link |
| 2 | Compatible | New example, optional field, compatible template |
| 3 | Significant | New skill, architecture adjustment |
| 4 | Breaking / Critical | Scope, methodology, contract, or security change |

Level 3 and Level 4 changes require formal review. Level 4 changes may require an ADR and a Major version update.

## Documentation Rules

- Use Traditional Chinese or English consistently within a document.
- Use official terminology from [Glossary](./docs/14-glossary.md).
- Use relative links for internal references.
- Do not duplicate a Source of Truth.
- Keep dynamic provider information outside stable core documents.

## Validation Requirements

Before requesting merge:

- Confirm Markdown structure
- Confirm links
- Confirm terminology
- Confirm Source of Truth alignment
- Confirm no secrets or sensitive data
- Add or update tests when behavior changes

See [Validation Standard](./docs/11-validation-standard.md).

## Security

Do not report vulnerabilities in public Issues. Follow [SECURITY.md](./SECURITY.md).

## License

By contributing, you agree that your contribution will be licensed under the MIT License.
