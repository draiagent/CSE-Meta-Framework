# CSE Meta Framework

> A vendor-neutral meta framework for designing, developing, validating, governing, securing, and releasing reusable AI frameworks.

![Version](https://img.shields.io/badge/version-1.0.0--rc.1-blue)
![Status](https://img.shields.io/badge/status-release%20candidate-orange)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

## Overview

CSE Meta Framework defines how an AI framework should be discovered, defined, designed, developed, validated, released, governed, secured, and continuously improved.

It is not a model comparison guide, prompt collection, or platform-specific toolkit. It is the parent standard used to create consistent CSE child frameworks such as TaskRouter, Prompt Engineering, Context Engineering, Workflow Engineering, Agent Framework, and MCP Framework.

## Why This Framework

AI framework projects often fail because their scope, terminology, repository structure, validation rules, and release process are inconsistent.

CSE Meta Framework provides a shared foundation for:

- Framework philosophy and boundaries
- Framework lifecycle and blueprint
- Repository and documentation architecture
- Core execution methodology
- Skill and template standards
- Validation, governance, security, and release controls

## Framework Lifecycle

```text
Discover
   ↓
Define
   ↓
Design
   ↓
Develop
   ↓
Validate
   ↓
Release
   ↓
Evolve
```

See [Framework Lifecycle](./docs/01-framework-lifecycle.md).

## Core Methodology

```text
Understand
   ↓
Analyze
   ↓
Design
   ↓
Execute
   ↓
Validate
   ↓
Improve
```

See [Core Methodology](./docs/06-core-methodology.md).

## Architecture

```text
CSE Meta Framework
├── Philosophy
├── Framework Lifecycle
├── Framework Blueprint
├── Design Principles
├── Repository Architecture
├── Document Standards
├── Core Methodology
├── Skills Standard
├── Template Standard
├── README Standard
├── Release Standard
├── Validation Standard
├── Governance Standard
├── Security Standard
├── Glossary
└── Roadmap
```

## Quick Start

### 1. Read the philosophy

Start with [00-philosophy.md](./docs/00-philosophy.md).

### 2. Follow the lifecycle

Use [01-framework-lifecycle.md](./docs/01-framework-lifecycle.md) to determine how a new framework should be created.

### 3. Complete the blueprint

Use [02-framework-blueprint.md](./docs/02-framework-blueprint.md) before creating large numbers of documents, skills, or templates.

### 4. Apply the standards

Use the relevant standards for repository structure, documentation, skills, templates, validation, governance, security, and release.

### 5. Validate before release

Do not mark a framework as Stable until it passes the requirements in [11-validation-standard.md](./docs/11-validation-standard.md).

## Documentation

| Document | Purpose |
|---|---|
| [Philosophy](./docs/00-philosophy.md) | Vision, mission, values, scope, and non-goals |
| [Framework Lifecycle](./docs/01-framework-lifecycle.md) | How a framework is created and evolved |
| [Framework Blueprint](./docs/02-framework-blueprint.md) | Required design blueprint |
| [Design Principles](./docs/03-design-principles.md) | Foundation, architecture, quality, and governance principles |
| [Repository Architecture](./docs/04-repository-architecture.md) | Standard repository profiles and structure |
| [Document Standards](./docs/05-document-standards.md) | Markdown, metadata, terminology, and reference rules |
| [Core Methodology](./docs/06-core-methodology.md) | Shared task execution method |
| [Skills Standard](./docs/07-skills-standard.md) | Skill package, contracts, portability, and testing |
| [Template Standard](./docs/08-template-standard.md) | Template categories, placeholders, registry, and validation |
| [README Standard](./docs/09-readme-standard.md) | GitHub repository entry-page standard |
| [Release Standard](./docs/10-release-standard.md) | Versioning, release candidate, migration, and rollback |
| [Validation Standard](./docs/11-validation-standard.md) | Validation levels, acceptance criteria, and reporting |
| [Governance Standard](./docs/12-governance-standard.md) | Ownership, decision rights, change control, and audit |
| [Security Standard](./docs/13-security-standard.md) | Data, access, execution, integration, and supply-chain security |
| [Glossary](./docs/14-glossary.md) | Official terminology |
| [Roadmap](./docs/15-roadmap.md) | Current priorities, milestones, and out-of-scope items |

## Current Status

- Version: `1.0.0-rc.1`
- Status: `Release Candidate`
- Core Consistency Review: `Pass`
- Next Phase: `Release Candidate Review and Approval`

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).

## Security

See [SECURITY.md](./SECURITY.md).

## Code of Conduct

See [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md).

## License

This project is licensed under the [MIT License](./LICENSE).
