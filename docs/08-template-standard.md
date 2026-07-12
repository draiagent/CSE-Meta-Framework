# 08 Template Standard

> CSE Meta Framework — Template Standard

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Template Standard  
Source of Truth: Template Standard  
Last Updated: 2026-07-11

Depends On:
- `05-document-standards.md`
- `07-skills-standard.md`
- `09-readme-standard.md`
- `10-release-standard.md`
- `11-validation-standard.md`
- `14-glossary.md`

Required By:
- `09-readme-standard.md`
- `15-roadmap.md`

---

# Purpose

本文件定義所有 CSE Framework 的 Template 設計、命名、結構、版本、驗證與維護標準。

Template 的目的，是把已驗證的 Framework 規則轉換成可重複使用的起始結構，降低建立新 Repository、文件、Skill、Prompt、Example、ADR、Validation 與 Release Artifact 的成本。

Template 不取代 Framework 方法論，也不得成為規則的唯一來源。

---

# 1. Template Definition

Template 是一個可重複使用的標準骨架。

一個合格的 Template 必須具備：

- 明確用途
- 固定結構
- 清楚 Placeholder
- 可直接複製
- 可被驗證
- 可版本管理
- 不含特定專案內容
- 不硬編碼動態資訊
- 與 Source of Truth 保持一致

Template 不應只是：

- 空白 Markdown
- 範例文件
- 一次性草稿
- 平台專屬說明
- 未經驗證的格式集合

---

# 2. Template Principles

所有 CSE Template 必須遵循：

1. **Template Follows Standard**
2. **One Template, One Primary Purpose**
3. **Minimal but Complete**
4. **Explicit Placeholders**
5. **No Hidden Assumptions**
6. **No Dynamic Data Hardcoding**
7. **Reusable by Default**
8. **Validation Before Release**
9. **Versioned and Traceable**
10. **Backward Compatible by Default**

---

# 3. Template Categories

CSE Template 分為九類：

| Category | Purpose | Typical File |
|---|---|---|
| Framework Template | 建立新 Framework 定義 | `framework.template.md` |
| README Template | 建立 Repository 首頁 | `readme.template.md` |
| Skill Template | 建立新 Skill | `skill.template.md` |
| Prompt Template | 建立 Prompt Pattern | `prompt.template.md` |
| Example Template | 建立案例 | `example.template.md` |
| ADR Template | 建立設計決策紀錄 | `adr.template.md` |
| Validation Template | 建立驗證報告 | `validation.template.md` |
| Release Template | 建立發布說明 | `release.template.md` |
| Migration Template | 建立版本遷移指南 | `migration.template.md` |

---

# 4. Template Package Structure

標準 Template 目錄：

```text
templates/
├── framework/
│   ├── framework-definition.template.md
│   ├── blueprint.template.md
│   └── methodology.template.md
├── repository/
│   ├── readme.template.md
│   ├── contributing.template.md
│   ├── security.template.md
│   └── roadmap.template.md
├── skills/
│   ├── skill.template.md
│   ├── adapter.template.md
│   └── skill-test.template.md
├── prompts/
│   ├── system-prompt.template.md
│   ├── task-prompt.template.md
│   └── review-prompt.template.md
├── examples/
│   └── example.template.md
├── decisions/
│   └── adr.template.md
├── validation/
│   ├── validation-plan.template.md
│   └── validation-report.template.md
├── release/
│   ├── release-notes.template.md
│   └── migration-guide.template.md
└── template-registry.yaml
```

---

# 5. Template Metadata

每個 Template 必須包含 Metadata。

標準格式：

```yaml
---
template_name: skill-template
display_name: Skill Template
version: 1.0.0
status: stable
owner: CSE
category: skill
source_standard: 07-skills-standard.md
last_updated: 2026-07-11
placeholders:
  - SKILL_NAME
  - SKILL_PURPOSE
  - SKILL_VERSION
---
```

## 5.1 Required Fields

| Field | Required | Description |
|---|---:|---|
| template_name | Yes | Template 唯一名稱 |
| display_name | Yes | 顯示名稱 |
| version | Yes | Template 版本 |
| status | Yes | Draft / Stable 等 |
| owner | Yes | 維護責任人 |
| category | Yes | Template 類型 |
| source_standard | Yes | 對應規格來源 |
| last_updated | Yes | 最後更新日期 |
| placeholders | Yes | Placeholder 清單 |

---

# 6. Template Naming Standard

檔名使用：

```text
<object>.template.md
```

範例：

```text
skill.template.md
example.template.md
validation-report.template.md
migration-guide.template.md
```

禁止：

- `template1.md`
- `new-template.md`
- `final-template.md`
- `template-v2.md`
- 中文檔名
- 空格
- 無法辨識用途的名稱

Template 版本由 Metadata 與 Git 管理，不寫入檔名。

---

# 7. Placeholder Standard

Placeholder 必須使用大寫蛇形命名：

```text
{{FRAMEWORK_NAME}}
{{SKILL_NAME}}
{{VERSION}}
{{OWNER}}
{{PURPOSE}}
```

## 7.1 Placeholder Rules

- 必須具描述性
- 不得使用 `XXX`
- 不得使用 `TBD` 作為永久 Placeholder
- 同一 Placeholder 必須保持一致
- Required 與 Optional Placeholder 必須分開
- Placeholder 不得包含真實敏感資料

## 7.2 Required and Optional Placeholders

範例：

```yaml
required_placeholders:
  - FRAMEWORK_NAME
  - PURPOSE
  - VERSION

optional_placeholders:
  - REVIEWERS
  - RELATED_DOCUMENTS
```

## 7.3 Default Values

只有低風險且穩定欄位可提供預設值。

範例：

```yaml
defaults:
  STATUS: draft
  LICENSE: MIT
  LANGUAGE: zh-TW
```

模型名稱、價格、API、Provider 不得設為固定預設值。

---

# 8. Template Content Rules

Template 內容必須：

- 保留必要章節
- 提供最小可用結構
- 不複製過多教學文字
- 不嵌入特定案例
- 不寫死動態資訊
- 不隱藏必要欄位
- 可被人與 AI 直接填寫

Template 中的說明應使用 HTML Comment：

```markdown
<!-- Describe the Framework purpose in one sentence. -->
```

使用後可刪除，不污染正式輸出。

---

# 9. Framework Template

以下為**一般子 Framework** 的標準 Framework Definition Template：

```markdown
---
template_name: framework-definition-template
version: 1.0.0
status: stable
owner: CSE
category: framework
source_standard: 02-framework-blueprint.md
---

# {{FRAMEWORK_NAME}}

Version: {{VERSION}}
Status: {{STATUS}}
Owner: {{OWNER}}
Last Updated: {{LAST_UPDATED}}

## Purpose

{{PURPOSE}}

## Problem Definition

{{PROBLEM_DEFINITION}}

## Target Users

{{TARGET_USERS}}

## Scope

### Included

{{INCLUDED_SCOPE}}

### Excluded

{{EXCLUDED_SCOPE}}

## Non-Goals

{{NON_GOALS}}

## Value Proposition

{{VALUE_PROPOSITION}}

## Core Methodology

{{CORE_METHODOLOGY}}

## Success Criteria

{{SUCCESS_CRITERIA}}

## Definition of Done

{{DEFINITION_OF_DONE}}
```

---

# 10. README Template

README Template 應提供入口，不承載全部方法論。

標準結構：

```markdown
# {{FRAMEWORK_NAME}}

> {{TAGLINE}}

{{BADGES}}

## Overview

{{OVERVIEW}}

## Why This Framework

{{WHY}}

## Core Methodology

{{METHODOLOGY_SUMMARY}}

## Architecture

{{ARCHITECTURE_SUMMARY}}

## Quick Start

{{QUICK_START}}

## Skills

{{SKILLS_INDEX}}

## Examples

{{EXAMPLES_INDEX}}

## Documentation

{{DOCUMENTATION_INDEX}}

## Version

{{VERSION}}

## License

{{LICENSE}}
```

禁止在 README Template 中放入：

- 全部方法論
- 完整 API Reference
- 大量平台比較
- 動態模型清單
- 所有案例內容

---

# 11. Skill Template

Skill Template 必須符合 `07-skills-standard.md`。

```markdown
---
name: {{SKILL_NAME}}
display_name: {{DISPLAY_NAME}}
description: {{DESCRIPTION}}
version: {{VERSION}}
status: {{STATUS}}
owner: {{OWNER}}
framework: {{FRAMEWORK}}
category: {{CATEGORY}}
license: {{LICENSE}}
inputs:
  - {{INPUT_FIELD}}
outputs:
  - {{OUTPUT_FIELD}}
---

# Purpose

{{PURPOSE}}

# Scope

## Included

{{INCLUDED_SCOPE}}

## Non-Goals

{{NON_GOALS}}

# Inputs

{{INPUT_CONTRACT}}

# Preconditions

{{PRECONDITIONS}}

# Workflow

{{WORKFLOW}}

# Decision Rules

{{DECISION_RULES}}

# Outputs

{{OUTPUT_CONTRACT}}

# Validation

{{VALIDATION_RULES}}

# Error Handling

{{ERROR_HANDLING}}

# Human Review

{{HUMAN_REVIEW_RULES}}

# Examples

{{EXAMPLES}}

# Limitations

{{LIMITATIONS}}

# Version Notes

{{VERSION_NOTES}}
```

---

# 12. Prompt Template

Prompt Template 應區分：

- Role
- Context
- Task
- Constraints
- Process
- Output
- Validation

標準格式：

```markdown
# Role

{{ROLE}}

# Context

{{CONTEXT}}

# Task

{{TASK}}

# Constraints

{{CONSTRAINTS}}

# Process

{{PROCESS}}

# Output Format

{{OUTPUT_FORMAT}}

# Validation

{{VALIDATION_RULES}}
```

Prompt Template 不得：

- 指定過時模型名稱
- 混入完整方法論
- 缺少輸出格式
- 缺少限制條件
- 只描述角色，不描述任務

---

# 13. Example Template

```markdown
# {{EXAMPLE_TITLE}}

Version: {{VERSION}}
Status: {{STATUS}}

## Problem

{{PROBLEM}}

## Context

{{CONTEXT}}

## Input

{{INPUT}}

## Workflow

{{WORKFLOW}}

## Output

{{OUTPUT}}

## Validation

{{VALIDATION}}

## Lessons Learned

{{LESSONS_LEARNED}}

## Limitations

{{LIMITATIONS}}
```

每個 Example 必須可重現。

---

# 14. ADR Template

```markdown
# ADR-{{ADR_NUMBER}} {{DECISION_TITLE}}

Status: {{STATUS}}
Date: {{DATE}}
Owner: {{OWNER}}

## Context

{{CONTEXT}}

## Decision

{{DECISION}}

## Alternatives

{{ALTERNATIVES}}

## Consequences

{{CONSEQUENCES}}

## Validation

{{VALIDATION}}

## Related Documents

{{RELATED_DOCUMENTS}}
```

ADR 不得在既有決策改變後直接覆寫。

應建立新的 ADR，並標示取代關係。

---

# 15. Validation Template

## 15.1 Validation Plan

```markdown
# Validation Plan

## Scope

{{VALIDATION_SCOPE}}

## Version Under Test

{{VERSION}}

## Test Levels

{{TEST_LEVELS}}

## Test Cases

{{TEST_CASES}}

## Acceptance Criteria

{{ACCEPTANCE_CRITERIA}}

## Human Review

{{HUMAN_REVIEW}}

## Risks

{{RISKS}}
```

## 15.2 Validation Report

```markdown
# Validation Report

## Tested Version

{{VERSION}}

## Test Scope

{{TEST_SCOPE}}

## Passed Items

{{PASSED_ITEMS}}

## Failed Items

{{FAILED_ITEMS}}

## Warnings

{{WARNINGS}}

## Known Limitations

{{KNOWN_LIMITATIONS}}

## Required Fixes

{{REQUIRED_FIXES}}

## Release Recommendation

{{RELEASE_RECOMMENDATION}}
```

---

# 16. Release Template

```markdown
# Release {{VERSION}}

Release Date: {{RELEASE_DATE}}
Status: {{STATUS}}

## Summary

{{SUMMARY}}

## Added

{{ADDED}}

## Changed

{{CHANGED}}

## Fixed

{{FIXED}}

## Deprecated

{{DEPRECATED}}

## Removed

{{REMOVED}}

## Security

{{SECURITY}}

## Known Limitations

{{KNOWN_LIMITATIONS}}

## Migration Notes

{{MIGRATION_NOTES}}
```

---

# 17. Migration Template

```markdown
# Migration Guide

From: {{FROM_VERSION}}
To: {{TO_VERSION}}

## Why Migration Is Required

{{WHY}}

## Breaking Changes

{{BREAKING_CHANGES}}

## Before Migration

{{PRE_MIGRATION_CHECKLIST}}

## Migration Steps

{{MIGRATION_STEPS}}

## Validation

{{VALIDATION_STEPS}}

## Rollback

{{ROLLBACK_PLAN}}

## Known Issues

{{KNOWN_ISSUES}}
```

---

# 18. Template Registry

所有 Template 應登錄於：

```text
templates/template-registry.yaml
```

範例：

```yaml
templates:
  - name: skill-template
    file: skills/skill.template.md
    version: 1.0.0
    status: stable
    source_standard: docs/07-skills-standard.md

  - name: readme-template
    file: repository/readme.template.md
    version: 1.0.0
    status: draft
    source_standard: docs/09-readme-standard.md
```

Registry 用於：

- 追蹤版本
- 找出 Source Standard
- 自動化檢查
- Template Discovery
- Deprecated 管理

---

# 19. Template Validation

每個 Template 必須完成以下最低驗證：

1. Structural Validation
2. Placeholder Validation
3. Render Validation
4. Source Standard Alignment

本文件只定義 Template 特有驗證要求。

完整 Validation Lifecycle、Acceptance Criteria、Severity 與 Decision，統一由 [Validation Standard](./11-validation-standard.md) 定義。

# 20. Template Testing

每個 Stable Template 至少需要：

1. Empty Input Test
2. Minimum Input Test
3. Full Input Test
4. Invalid Placeholder Test
5. Render Test
6. Regression Test

測試案例範例：

```yaml
test_case:
  id: template-001
  template: skill-template
  input:
    SKILL_NAME: task-router
    VERSION: 1.0.0
  expected:
    unresolved_placeholders: 0
    required_sections_present: true
    markdown_valid: true
```

---

# 21. Template Versioning

Template 使用 Semantic Versioning：

```text
MAJOR.MINOR.PATCH
```

| Change | Version Impact |
|---|---|
| 修正錯字 | Patch |
| 新增 Optional Placeholder | Minor |
| 新增相容章節 | Minor |
| 移除 Required Placeholder | Major |
| 修改必要章節 | Major |
| 修改 Render Contract | Major |

Template 版本不必與 Framework 版本完全一致，但必須記錄相容範圍。

---

# 22. Compatibility

Template 應標示相容版本：

```yaml
compatibility:
  framework_standard: ">=1.0.0 <2.0.0"
  skill_standard: ">=1.0.0 <2.0.0"
```

Breaking Change 時，應：

- 提升 Major Version
- 更新 Registry
- 提供 Migration Guide
- 標示 Deprecated Template
- 保留過渡期

---

# 23. Deprecation

Template 不得直接刪除。

標準流程：

```text
Stable
  ↓
Deprecated
  ↓
Migration Period
  ↓
Archived
```

Deprecated Metadata：

```yaml
status: deprecated
deprecated: true
replaced_by: skill-template-v2
```

---

# 24. Template Ownership

每個 Template 必須有 Owner。

Owner 負責：

- 與 Source Standard 同步
- 版本管理
- 測試
- Deprecated 管理
- Registry 更新
- Issue 回應

無 Owner 的 Template 不得標示 Stable。

---

# 25. Security Rules

Template 不得包含：

- 真實密碼
- API Key
- Token
- 個資
- 私有 URL
- 內部帳號
- 生產環境 ID
- 未遮罩範例資料

敏感欄位應使用：

```text
{{SECRET_REFERENCE}}
```

而不是填入真實值。

---

# 26. Localization

多語言 Template 必須：

- 指定主要版本
- 保持 Placeholder 一致
- 保持章節一致
- 同步版本
- 不改變執行契約

命名建議：

```text
skill.template.md
skill.template.zh-TW.md
skill.template.en.md
```

---

# 27. Template Usage Workflow

```text
Select Template
   ↓
Check Compatibility
   ↓
Copy Template
   ↓
Fill Required Placeholders
   ↓
Fill Optional Placeholders
   ↓
Render
   ↓
Validate
   ↓
Review
   ↓
Commit
```

禁止直接修改中央 Template 來完成單一專案。

---

# 28. Template Review Checklist

## Identity

- [ ] Template Name 唯一
- [ ] Category 正確
- [ ] Owner 明確
- [ ] Source Standard 已指定

## Structure

- [ ] 必要章節完整
- [ ] 一個 Template 一個主要用途
- [ ] 沒有特定專案內容
- [ ] 沒有重複規則

## Placeholder

- [ ] Required Placeholder 完整
- [ ] Optional Placeholder 已分離
- [ ] Placeholder 命名一致
- [ ] 沒有 `XXX` 或永久 `TBD`
- [ ] 沒有敏感資料

## Validation

- [ ] Structural Test 通過
- [ ] Render Test 通過
- [ ] Regression Test 通過
- [ ] 無殘留 Placeholder
- [ ] 與 Source Standard 一致

## Governance

- [ ] Version 正確
- [ ] Registry 已更新
- [ ] Compatibility 已定義
- [ ] CHANGELOG 已更新
- [ ] Deprecated 規則已確認

---

# 29. Anti-Patterns

## 29.1 Blank Skeleton

Template 只有標題，沒有必要欄位。

修正：

- 加入最小可用結構。

## 29.2 Example Disguised as Template

Template 內含特定公司、人名或案例。

修正：

- 改用 Placeholder。

## 29.3 Hidden Required Fields

必要資訊未標示 Required。

修正：

- 建立 Required Placeholder 清單。

## 29.4 Hardcoded Dynamic Data

Template 內寫死模型、價格或 API。

修正：

- 改用 Config Reference。

## 29.5 Template Becomes Source of Truth

規則只存在 Template，標準文件沒有定義。

修正：

- 規則回到 Source Standard。

## 29.6 Unvalidated Template

未測試就標示 Stable。

修正：

- 執行 Render 與 Regression Test。

## 29.7 Central Template Edited for One Project

為了單一案例修改共用 Template。

修正：

- 複製 Template 後再填寫。

---

# 30. Immediate Corrections

本版已建立並修正以下核心要求：

1. **Template 與 Standard 分離**
   - Standard 是規則來源。
   - Template 是規則的可重複實作。

2. **新增 Template Registry**
   - 統一追蹤版本、狀態與 Source Standard。

3. **建立 Placeholder 正式規範**
   - Required、Optional、Default 分開管理。

4. **加入 Render Validation**
   - Template 必須實際填入測試資料驗證。

5. **加入 Compatibility 與 Migration**
   - Template 更新不得破壞既有 Framework。

6. **加入 Security 與 Localization**
   - 防止敏感資料進入 Template，並支援多語言一致性。

7. **建立九種核心 Template**
   - Framework、README、Skill、Prompt、Example、ADR、Validation、Release、Migration。

---

# 31. Definition of Done

本文件完成代表：

- 已定義 CSE Template 的正式標準
- 已建立 Template Categories 與 Package Structure
- 已建立 Metadata、Naming 與 Placeholder 規範
- 已建立 Framework、README、Skill、Prompt、Example、ADR、Validation、Release 與 Migration Template
- 已建立 Template Registry
- 已建立 Validation、Testing、Versioning 與 Compatibility
- 已建立 Deprecation、Ownership、Security 與 Localization
- 已建立 Template Usage Workflow 與 Review Checklist
- 可供所有 CSE Framework 建立一致且可重複使用的模板

---


# Related Documents

- [Document Standards](./05-document-standards.md)
- [Skills Standard](./07-skills-standard.md)
- [README Standard](./09-readme-standard.md)
- [Release Standard](./10-release-standard.md)
- [Validation Standard](./11-validation-standard.md)
- [Glossary](./14-glossary.md)

# Next Document

**09-readme-standard.md**

下一份文件將定義：

- README 的責任與邊界
- GitHub 首頁資訊架構
- Quick Start
- Architecture Summary
- Documentation Navigation
- Badges
- Version and Status
- README Validation
