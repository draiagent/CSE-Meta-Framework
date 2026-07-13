# 07 Skills Standard

> CSE Meta Framework — Skills Standard

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Execution Standard  
Source of Truth: Skills Standard  
Last Updated: 2026-07-11

Depends On:
- `04-repository-architecture.md`
- `06-core-methodology.md`
- `11-validation-standard.md`
- `13-security-standard.md`
- `14-glossary.md`

Required By:
- `08-template-standard.md`

---

# Purpose

本文件定義所有 CSE Framework 的 Skill 設計、封裝、命名、輸入輸出、驗證、測試、版本與跨平台適配標準。

Skill 的目的不是保存知識，而是將 Framework 的方法論轉換為 AI 可直接執行的能力。

本文件適用於：

- Codex Skills
- Claude Code Skills
- Gemini CLI Skills
- Cursor Rules / Skills
- Agent Skills
- Workflow Skills
- Validator Skills
- Reviewer Skills
- Router Skills
- 其他可重複使用的 AI 執行單元

---

# 1. Skill Definition

Skill 是一個具備明確責任、輸入、流程、輸出與驗證規則的可執行單元。

一個合格的 Skill 必須具備：

- Single Responsibility
- Explicit Inputs
- Deterministic Workflow
- Structured Outputs
- Validation Rules
- Error Handling
- Versioning
- Portability
- Testability
- Traceability

Skill 不應只是：

- 一段泛用提示詞
- 一篇教學文章
- 一份平台操作說明
- 一個沒有輸入輸出的工作流程
- 一組未驗證的範例

---

# 2. Skill Design Principles

所有 CSE Skill 必須遵循以下原則：

1. **One Skill, One Primary Responsibility**
2. **Methodology First**
3. **Docs Explain, Skills Execute**
4. **Model-Agnostic by Default**
5. **Configuration Over Hardcoding**
6. **Explicit Input and Output Contracts**
7. **Validation Is Mandatory**
8. **Fail Explicitly**
9. **Portable Core, Platform Adapters**
10. **Version Every Meaningful Change**

---

# 3. Skill Categories

CSE Skill 分為六類：

| Category | Purpose | Example |
|---|---|---|
| Router Skill | 任務分類與路由 | Task Complexity Router |
| Execution Skill | 執行特定任務 | Report Generator |
| Validation Skill | 驗證結果 | Output Validator |
| Review Skill | 獨立審查 | Risk Reviewer |
| Transformation Skill | 格式或內容轉換 | Markdown Converter |
| Orchestration Skill | 協調多個 Skill | Multi-Step Workflow |

不同類型 Skill 可以組合，但每個 Skill 仍必須保持單一主要責任。

---

# 4. Skill Package Structure

標準 Skill Package：

```text
skills/
└── skill-name/
    ├── skill.md
    ├── README.md
    ├── config.yaml
    ├── input.schema.json
    ├── output.schema.json
    ├── examples/
    │   ├── basic.md
    │   ├── advanced.md
    │   └── failure.md
    ├── tests/
    │   ├── smoke-test.md
    │   ├── scenario-test.md
    │   └── regression-test.md
    └── adapters/
        ├── codex.md
        ├── claude-code.md
        ├── gemini-cli.md
        └── cursor.md
```

對於小型 Skill，可使用精簡結構：

```text
skills/
└── skill-name/
    ├── skill.md
    ├── config.yaml
    └── tests.md
```

---

# 5. Skill Front Matter

每個 `skill.md` 必須包含 Front Matter。

標準格式：

```yaml
---
name: task-router
display_name: Task Router
description: Classify task complexity and select an execution path.
version: 1.0.0
status: Draft
owner: CSE
framework: CSE-TaskRouter
category: router
language: zh-TW
license: MIT
inputs:
  - task
outputs:
  - task_level
  - recommendation
requires:
  - core-methodology
supports:
  - codex
  - claude-code
  - gemini-cli
  - cursor
---
```

## 5.1 Required Fields

| Field | Required | Description |
|---|---:|---|
| name | Yes | Skill 唯一識別名稱 |
| display_name | Yes | 顯示名稱 |
| description | Yes | 一句話描述用途 |
| version | Yes | Semantic Version |
| status | Yes | Draft / Beta / Stable 等 |
| owner | Yes | 維護責任人 |
| framework | Yes | 所屬 Framework |
| category | Yes | Skill 類型 |
| inputs | Yes | 必要輸入 |
| outputs | Yes | 主要輸出 |
| license | Yes | 授權條款 |

## 5.2 Optional Fields

- language
- tags
- supports
- requires
- deprecated
- replaced_by
- risk_level
- human_review_required

---

# 6. Skill Naming Standard

Skill 名稱使用：

```text
kebab-case
```

例如：

```text
task-router
output-validator
risk-reviewer
context-builder
```

禁止：

- 空格
- 中文檔名
- 無意義縮寫
- `new-skill`
- `final-skill`
- `skill-v2`
- 名稱與責任不一致

名稱應反映動作與責任。

建議格式：

```text
<object>-<action>
```

或：

```text
<domain>-<responsibility>
```

---

# 7. Skill Document Structure

每個 `skill.md` 應包含：

1. Purpose
2. Scope
3. Non-Goals
4. Inputs
5. Preconditions
6. Workflow
7. Decision Rules
8. Outputs
9. Validation
10. Error Handling
11. Human Review
12. Examples
13. Limitations
14. Version Notes

---

# 8. Purpose and Scope

## 8.1 Purpose

Purpose 必須用一句話定義 Skill 的唯一目的。

範例：

```text
Classify a task into Quick, Standard, Deep, or Strategic.
```

## 8.2 Scope

Scope 應列出 Skill 負責事項。

範例：

```markdown
## Included

- Analyze task complexity
- Assign task level
- Recommend execution depth
```

## 8.3 Non-Goals

範例：

```markdown
## Non-Goals

- Does not execute the task
- Does not compare providers
- Does not select a commercial plan
```

---

# 9. Input Contract

所有 Skill 必須定義 Input Contract。

## 9.1 Input Fields

| Field | Type | Required | Default | Description |
|---|---|---:|---|---|
| task | string | Yes | — | 使用者任務 |
| context | object | No | `{}` | 補充背景 |
| constraints | array | No | `[]` | 限制條件 |
| risk_level | string | No | `unknown` | 風險等級 |

## 9.2 Input Rules

- 必填欄位缺失時不得執行
- 型別錯誤時應回傳明確錯誤
- 高風險任務不得以預設值取代關鍵資訊
- 未提供的可選欄位可使用明確預設值
- 不得偷偷推測敏感或高影響資訊

## 9.3 Input Schema

建議提供：

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Task Router Input",
  "type": "object",
  "required": ["task"],
  "properties": {
    "task": {
      "type": "string",
      "minLength": 1
    },
    "context": {
      "type": "object"
    },
    "constraints": {
      "type": "array",
      "items": {
        "type": "string"
      }
    }
  },
  "additionalProperties": false
}
```

---

# 10. Preconditions

Skill 執行前必須確認 Preconditions。

常見 Preconditions：

- Required Input 已提供
- 使用者具備必要權限
- 所需工具可用
- 所需文件可存取
- 外部資料來源已確認
- Config 已載入
- 風險等級已判斷

若 Preconditions 不成立：

```text
Stop
→ Return Error
→ Request Missing Input
```

不得繼續猜測執行。

---

# 11. Workflow Standard

每個 Skill 內部流程至少包含：

```text
Receive
   ↓
Validate Input
   ↓
Analyze
   ↓
Execute
   ↓
Validate Output
   ↓
Return
```

複雜 Skill 可增加：

- Plan
- Tool Selection
- Human Review
- Retry
- Escalation
- Logging

## 11.1 Core Methodology Mapping

Skill Workflow 必須能映射至 [Core Methodology](./06-core-methodology.md)：

| Skill Workflow | Core Methodology |
|---|---|
| Receive + Validate Input | Understand |
| Analyze | Analyze |
| Plan + Decision Rules | Design |
| Execute | Execute |
| Validate Output | Validate |
| Retry + Correction + Logging | Improve |

固定原則：

```text
Skill 可以簡化或內嵌六階段，
但不得省略必要的 Understand、Validate 與錯誤改善機制。
```

## 11.2 Workflow Rules

- Workflow 必須可重複
- 每一步有明確目的
- 每一步有輸入與輸出
- 每一步可被驗證
- 不得跳過 Output Validation
- 失敗時需回傳明確狀態

---

# 12. Decision Rules

Skill 中的決策應使用明確規則。

範例：

```text
IF risk_level = high
THEN human_review_required = true
```

或：

```yaml
decision_rules:
  - condition: missing_required_input
    action: stop
  - condition: high_risk
    action: escalate
  - condition: validation_failed
    action: retry_or_return
```

避免使用：

```text
視情況處理
適當判斷
必要時調整
```

若必須保留彈性，應定義判斷準則。

---

# 13. Output Contract

所有 Skill 必須定義 Output Contract。

## 13.1 Standard Output

```json
{
  "status": "success",
  "summary": "",
  "result": {},
  "warnings": [],
  "limitations": [],
  "validation": {
    "status": "pass"
  }
}
```

## 13.2 Required Output Fields

| Field | Required | Description |
|---|---:|---|
| status | Yes | success / failed / partial |
| summary | Yes | 簡要說明 |
| result | Yes | 主要結果 |
| warnings | Yes | 警告 |
| limitations | Yes | 限制 |
| validation | Yes | 驗證結果 |

## 13.3 Error Output

```json
{
  "status": "failed",
  "error_type": "missing_input",
  "message": "Required field 'task' is missing.",
  "failed_stage": "input_validation",
  "missing_information": ["task"],
  "retry_allowed": true
}
```

---

# 14. Validation Standard

每個 Skill 必須具備：

- Input Validation
- Process Validation
- Output Validation

本文件只定義 Skill 必須接受驗證，不重新定義完整 Validation Model。

最低要求：

- Required Input 缺失時停止
- Workflow 未完成時不得回傳成功
- Output 必須符合 Contract
- 高風險情境必須觸發 Human Review
- Failed Validation 必須回傳明確錯誤

完整驗證層級、Acceptance Criteria、Severity、Decision 與報告格式，統一由 [Validation Standard](./11-validation-standard.md) 定義。

# 15. Error Handling

Skill 必須明確定義錯誤類型。

建議分類：

| Error Type | Description |
|---|---|
| missing_input | 缺少必要輸入 |
| invalid_input | 輸入格式錯誤 |
| permission_denied | 權限不足 |
| tool_unavailable | 工具不可用 |
| validation_failed | 驗證失敗 |
| scope_violation | 超出 Skill 範圍 |
| unsafe_request | 無法安全執行 |
| internal_error | 非預期錯誤 |

每個錯誤至少回傳：

- Error Type
- Message
- Failed Stage
- Suggested Action
- Retry Allowed

---

# 16. Human Review

以下情況 Skill 必須要求人工審核：

- 高風險醫療、法律、財務內容
- 生產環境部署
- 權限變更
- 不可逆操作
- 對外正式發布
- 重大策略建議
- 高敏感資料處理
- 安全設定變更

Front Matter 可標示：

```yaml
human_review_required: true
```

或依條件動態決定。

---

# 17. Portability Standard

Skill Core 必須保持平台中立。

## 17.1 Portable Core

Portable Core 應包含：

- Purpose
- Scope
- Inputs
- Workflow
- Outputs
- Validation
- Error Handling

## 17.2 Platform Adapter

平台差異應放在：

```text
adapters/
```

例如：

```text
adapters/
├── codex.md
├── claude-code.md
├── gemini-cli.md
└── cursor.md
```

Adapter 可定義：

- 入口格式
- 平台特有工具
- 目錄位置
- 平台限制
- 呼叫方式

Adapter 不得改變核心方法論。

---

# 18. Configuration Standard

Skill 不得硬編碼：

- 模型名稱
- 模型版本
- Token 限制
- Provider
- 路由門檻
- 工具清單
- Timeout
- Retry Count

上述內容應放入 `config.yaml`。

範例：

```yaml
skill:
  name: task-router
  version: 1.0.0

runtime:
  max_retries: 2
  timeout_seconds: 120

validation:
  strict: true

routing:
  config_source: ../../configs/routing.yaml
```

---

# 19. Skill Dependencies

Skill 依賴必須明確記錄。

範例：

```yaml
requires:
  skills:
    - input-validator
    - output-validator
  frameworks:
    - CSE-Core-Methodology
  configs:
    - routing.yaml
```

## 19.1 Dependency Rules

- 禁止循環依賴
- 必要與選用依賴分開
- 版本需求需明確
- 外部依賴需標示
- 不可用時需有 Failover 或停止規則

---

# 20. Skill Composition

多個 Skill 可組合成 Workflow。

範例：

```text
Task Router
   ↓
Context Builder
   ↓
Executor
   ↓
Output Validator
   ↓
Risk Reviewer
```

組合時必須：

- 定義執行順序
- 定義資料傳遞契約
- 定義失敗處理
- 定義停止條件
- 定義最終責任 Skill

---

# 21. Skill Testing

每個 Skill 至少需要：

1. Smoke Test
2. Standard Scenario
3. Boundary Scenario
4. Failure Scenario
5. Incomplete Input Scenario
6. Regression Test

## 21.1 Test Case Structure

```yaml
test_case:
  id:
  name:
  input:
  expected_status:
  expected_output:
  validation_rules:
  notes:
```

## 21.2 Minimum Release Requirement

Stable Skill 必須：

- 所有 Smoke Test 通過
- 所有 Critical Scenario 通過
- Critical Error 為 0
- Regression Test 通過
- Known Limitations 已記錄

---

# 22. Skill Versioning

採用 Semantic Versioning：

```text
MAJOR.MINOR.PATCH
```

## 22.1 Version Impact

| Change | Version |
|---|---|
| 錯字、非功能修正 | Patch |
| 新增相容欄位 | Minor |
| 新增相容 Workflow | Minor |
| 修改 Input Contract | Major |
| 修改 Output Contract | Major |
| 修改核心責任 | Major |
| 移除舊功能 | Major |

---

# 23. Skill Status Lifecycle

```text
Draft
  ↓
Alpha
  ↓
Beta
  ↓
Release Candidate
  ↓
Stable
  ↓
Deprecated
  ↓
Archived
```

每次狀態變更必須：

- 更新 Front Matter
- 更新 CHANGELOG
- 完成對應測試
- 記錄 Known Limitations

---

# 24. Deprecation Rules

Skill 不得直接刪除。

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

Deprecated Skill 必須標示：

```yaml
deprecated: true
replaced_by: new-skill-name
```

並提供 Migration Guide。

---

# 25. Skill Documentation Boundary

`skill.md` 應保持可執行與精簡。

完整理論應放在：

```text
docs/
```

Skill 文件只保留：

- 執行所需規則
- 輸入輸出
- 流程
- 驗證
- 錯誤處理
- 簡短範例

禁止將完整 Framework 教材複製進 Skill。

---

# 26. Security and Safety

Skill 必須符合以下最低安全要求：

- 最小權限
- 資料最小化
- 敏感資訊遮罩
- 可回復性優先
- 高風險操作人工確認
- 外部操作有日誌
- 未授權操作停止

完整 Data Classification、Secret、Prompt Injection、Tool Allowlist、Supply Chain 與 Incident Response 規則，統一由 [Security Standard](./13-security-standard.md) 定義。

# 27. Traceability

重要 Skill 執行應記錄：

- Skill Name
- Skill Version
- Framework Version
- Config Version
- Input Summary
- Output Status
- Tools Used
- Validation Result
- Reviewer
- Timestamp

不得記錄不必要的敏感資料。

---

# 28. Skill Template

標準 `skill.md` 範本：

```markdown
---
name:
display_name:
description:
version:
status:
owner:
framework:
category:
license:
inputs:
outputs:
---

# Purpose

# Scope

## Included

## Non-Goals

# Inputs

# Preconditions

# Workflow

# Decision Rules

# Outputs

# Validation

# Error Handling

# Human Review

# Examples

# Limitations

# Version Notes
```

---

# 29. Skill Review Checklist

## Identity

- [ ] Name 唯一
- [ ] Responsibility 單一
- [ ] Category 正確
- [ ] Owner 明確

## Contract

- [ ] Inputs 完整
- [ ] Outputs 完整
- [ ] Schema 存在
- [ ] Error Output 已定義

## Workflow

- [ ] Workflow 可重複
- [ ] Decision Rules 明確
- [ ] Preconditions 已定義
- [ ] Stop Conditions 已定義

## Portability

- [ ] Core 不綁定平台
- [ ] Provider 資訊未硬編碼
- [ ] Adapter 已分離
- [ ] Config 已分離

## Validation

- [ ] Input Validation 存在
- [ ] Process Validation 存在
- [ ] Output Validation 存在
- [ ] Tests 完整
- [ ] Known Limitations 已記錄

## Governance

- [ ] Version 正確
- [ ] Status 正確
- [ ] CHANGELOG 已更新
- [ ] Deprecation 規則已定義
- [ ] Security 已檢查

---

# 30. Anti-Patterns

## 30.1 Prompt Disguised as Skill

只有一段提示詞，沒有輸入輸出與驗證。

修正：

- 建立完整 Skill Contract。

## 30.2 Knowledge Dump

將所有方法論塞進 `skill.md`。

修正：

- 理論移至 `docs/`
- Skill 保留執行規則

## 30.3 Hardcoded Provider

在 Skill 內寫死模型與平台。

修正：

- 移至 Config 或 Adapter

## 30.4 Hidden Preconditions

執行需要條件但未明確定義。

修正：

- 建立 Preconditions

## 30.5 Silent Failure

執行失敗但仍輸出結果。

修正：

- 使用 Error Output

## 30.6 Self-Validation Only

只有生成者自我宣告通過。

修正：

- 使用獨立 Validator 或 Human Review

## 30.7 Unversioned Contract Change

修改 Input / Output 但未升級版本。

修正：

- 提升 Major Version
- 提供 Migration Guide

---

# 31. Immediate Corrections

本版已修正舊版 `05-skills-standard.md` 的主要問題：

1. **從單一 Skill 文件升級為 Skill Package**
   - 加入 Config、Schema、Examples、Tests 與 Adapters。

2. **建立 Front Matter 完整規格**
   - 明確定義 Skill 身份、責任與相容平台。

3. **建立 Input / Output Contract**
   - 避免 Skill 只有提示詞、沒有可驗證介面。

4. **加入 Preconditions、Decision Rules 與 Error Handling**
   - 避免模糊執行與靜默失敗。

5. **建立 Portable Core 與 Platform Adapter 分離**
   - 核心 Skill 可跨 Codex、Claude Code、Gemini CLI、Cursor 使用。

6. **加入 Dependency、Composition 與 Testing**
   - 支援多 Skill 組合與回歸測試。

7. **加入 Security、Traceability 與 Human Review**
   - 符合企業級執行要求。

8. **加入 Deprecation 與 Migration**
   - 避免 Skill 被直接刪除或破壞相容性。

---

# 32. Definition of Done

本文件完成代表：

- 已定義 CSE Skill 的正式標準
- 已建立 Skill Package Structure
- 已建立 Front Matter 規格
- 已建立 Input / Output Contract
- 已建立 Workflow、Decision Rules 與 Error Handling
- 已建立 Validation 與 Testing 規則
- 已建立 Portable Core 與 Platform Adapter
- 已建立 Configuration 與 Dependency 規則
- 已建立 Versioning、Deprecation 與 Migration
- 已建立 Security、Human Review 與 Traceability
- 可供所有 CSE Framework 直接建立跨平台 Skill

---


# Related Documents

- [Repository Architecture](./04-repository-architecture.md)
- [Core Methodology](./06-core-methodology.md)
- [Template Standard](./08-template-standard.md)
- [Validation Standard](./11-validation-standard.md)
- [Security Standard](./13-security-standard.md)
- [Glossary](./14-glossary.md)

# Next Document

**08-template-standard.md**

下一份文件將定義：

- Framework Template
- README Template
- Skill Template
- Prompt Template
- Example Template
- ADR Template
- Release Template
- Validation Template
