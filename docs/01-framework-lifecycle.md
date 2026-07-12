# 01 Framework Lifecycle

> CSE Meta Framework — Framework Development Lifecycle

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Core Lifecycle  
Source of Truth: Framework Lifecycle  
Last Updated: 2026-07-11

Depends On:
- `00-philosophy.md`
- `14-glossary.md`

Required By:
- `02-framework-blueprint.md`
- `06-core-methodology.md`
- `15-roadmap.md`

---

# Purpose

本文件定義所有 CSE Framework 共用的母方法論：

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

這套 Lifecycle 用來規範一個 Framework 如何從概念形成、完成設計、被實作、通過驗證、正式發布，並持續演進。

任何 CSE Framework 都必須依循本 Lifecycle，不得直接跳過關鍵階段。

---

# 1. Lifecycle Overview

CSE Framework Lifecycle 包含七個階段：

| Stage | Core Question | Primary Output |
|---|---|---|
| Discover | 這個 Framework 是否真的需要存在？ | Problem Brief |
| Define | 這個 Framework 要解決什麼、邊界在哪裡？ | Framework Definition |
| Design | 這個 Framework 應如何運作與組成？ | Architecture and Methodology |
| Develop | 如何把設計轉成文件、Skill、Template 與範例？ | Working Repository |
| Validate | Framework 是否正確、完整、可用？ | Validation Report |
| Release | Framework 是否符合發布條件？ | Versioned Release |
| Evolve | Framework 如何根據證據持續改進？ | Roadmap and New Versions |

---

# 2. Lifecycle Governing Principles

所有階段遵循以下規則：

1. **Stage Gate**
   - 每個階段都有完成條件。
   - 未通過 Gate，不得進入下一階段。

2. **Evidence Before Assumption**
   - 關鍵決策應有需求、測試、官方資料或使用案例支持。

3. **Boundary Before Expansion**
   - 先定義不做什麼，再擴充功能。

4. **Design Before Development**
   - 未完成架構與方法論設計，不得大量產生文件或 Skill。

5. **Validation Before Release**
   - 未驗證內容不得標示為 Stable。

6. **Evolution Through Versioning**
   - 重大變更必須留下版本與 CHANGELOG 紀錄。

---

# 3. Stage 1 — Discover

## 3.1 Objective

確認問題是否值得建立一個新的 Framework 解決。

Discover 的重點不是提出解法，而是確認問題真實存在、具有重複性，且無法由既有 Framework 有效處理。

## 3.2 Key Questions

- 目前存在什麼問題？
- 問題出現頻率多高？
- 問題影響哪些人或流程？
- 現有方法為何不足？
- 是否真的需要建立新 Framework？
- 能否擴充既有 Framework 解決？
- 建立新 Framework 的價值是否高於維護成本？

## 3.3 Required Inputs

- 使用者需求
- 實際案例
- 現有工具或 Framework
- 問題紀錄
- 錯誤或失敗案例
- 預期使用情境

## 3.4 Required Outputs

```text
Problem Brief
```

Problem Brief 至少包含：

- Problem Statement
- Target Users
- Current Pain Points
- Existing Alternatives
- Framework Necessity
- Expected Value
- Initial Risks

## 3.5 Stage Gate

只有符合以下條件才可進入 Define：

- [ ] 問題可清楚描述
- [ ] 問題具有重複性
- [ ] 目標使用者明確
- [ ] 現有方案不足
- [ ] 建立 Framework 具有合理價值
- [ ] 沒有明顯重複建立既有功能

## 3.6 Stop Conditions

遇到以下情況應停止建立新 Framework：

- 問題只發生一次
- 問題可由單一 Prompt 解決
- 既有 Framework 已完整涵蓋
- 需求過度模糊
- 維護成本高於預期價值
- 僅因模型或工具流行而建立

---

# 4. Stage 2 — Define

## 4.1 Objective

定義 Framework 的身份、目標、邊界與成功條件。

Define 階段回答：

> 這個 Framework 是什麼？不是什麼？

## 4.2 Required Definitions

每個 Framework 必須定義：

- Name
- Vision
- Mission
- Problem
- Target Users
- Scope
- Excluded Scope
- Core Philosophy
- Success Criteria
- Non-Goals
- Repository Boundary

## 4.3 Required Output

```text
00-framework-definition.md
```

子 Framework 的定義文件應遵循 CSE Meta Framework 的 Philosophy。

## 4.4 Stage Gate

- [ ] 名稱清楚且不與既有 Framework 衝突
- [ ] Vision 與 Mission 明確
- [ ] Scope 與 Excluded Scope 完整
- [ ] Target Users 已定義
- [ ] Success Criteria 可衡量
- [ ] Non-Goals 已列出
- [ ] Repository Boundary 清楚
- [ ] 不綁定單一供應商

## 4.5 Common Failure

常見錯誤：

- Scope 過大
- 名稱太抽象
- 目標使用者過多
- 未定義 Non-Goals
- 將工具功能誤認為 Framework
- 同一 Repository 混入多個核心問題

---

# 5. Stage 3 — Design

## 5.1 Objective

將定義轉成完整且可執行的 Framework 設計。

Design 階段必須先完成方法論與架構，再開始大量內容製作。

## 5.2 Design Components

每個 Framework 至少需要：

1. Core Methodology
2. Architecture
3. Workflow
4. Decision Logic
5. Input and Output Model
6. Skill Design
7. Configuration Model
8. Validation Model
9. Example Strategy
10. Governance Rules

## 5.3 Required Outputs

建議輸出：

```text
01-design-principles.md
02-architecture.md
03-core-methodology.md
04-workflow.md
05-validation-design.md
```

實際檔名可依 Framework 規模調整，但不得省略核心設計內容。

## 5.4 Design Review Questions

- 方法論是否解決原始問題？
- 流程是否可重複？
- 模組是否能獨立維護？
- 是否存在重複責任？
- 是否能被 AI 與人類理解？
- 是否能透過配置而非硬編碼擴充？
- 是否有明確失敗處理方式？
- 是否有驗證機制？

## 5.5 Stage Gate

- [ ] Core Methodology 完整
- [ ] Repository Architecture 已定義
- [ ] Workflow 清楚
- [ ] Input / Output 已定義
- [ ] Skill 邊界清楚
- [ ] Validation 規則存在
- [ ] Configuration 與核心方法分離
- [ ] 設計符合 CSE Meta Framework

---

# 6. Stage 4 — Develop

## 6.1 Objective

將 Framework 設計轉化為可使用的 Repository。

Develop 的重點是實作，不是重新定義方向。

## 6.2 Development Components

應依設計建立：

- Core Documents
- Skills
- Prompts
- Templates
- Schemas
- Configs
- Examples
- Diagrams
- Tests
- Governance Files

## 6.3 Development Order

建議順序：

```text
Core Documents
      ↓
Schemas and Configs
      ↓
Skills
      ↓
Prompts
      ↓
Templates
      ↓
Examples
      ↓
Tests
      ↓
README
```

README 應在核心內容穩定後撰寫，避免首頁內容與實際 Framework 不一致。

## 6.4 Development Rules

- 不得違反 Define 階段的 Scope
- 不得在 Skill 內硬編碼動態模型名稱
- 不得重複複製核心方法論
- 不得以 README 取代完整文件
- 不得跳過 Examples 與 Tests
- 所有新增檔案需符合 Document Standards

## 6.5 Stage Gate

- [ ] Repository 結構完整
- [ ] 核心文件可獨立閱讀
- [ ] Skill 可直接執行
- [ ] Template 可重複使用
- [ ] Config 與核心邏輯分離
- [ ] 至少有一個完整案例
- [ ] 至少有一組測試
- [ ] README 與實際內容一致

---

# 7. Stage 5 — Validate

## 7.1 Objective

確認 Framework 是否符合其 Scope、Blueprint、Architecture 與品質要求。

本階段只定義 Lifecycle 所需的最低 Gate。完整驗證模型、Acceptance Criteria、Severity、Decision 與 Validation Report，統一由 [Validation Standard](./11-validation-standard.md) 定義。

## 7.2 Required Output

```text
Validation Report
```

## 7.3 Minimum Stage Gate

- [ ] 必要 Structural Validation 已完成
- [ ] 必要 Functional Validation 已完成
- [ ] 主要 Scenario Validation 已完成
- [ ] Critical Error 為 0
- [ ] Known Limitations 已記錄
- [ ] Release Recommendation 已形成

# 8. Stage 6 — Release

## 8.1 Objective

將通過驗證的 Framework 以可追蹤、可取得、可回復的方式正式發布。

本階段只定義 Lifecycle 所需的最低 Gate。完整版本、Release Candidate、Migration、Rollback、Deprecation 與 Post-Release Review，統一由 [Release Standard](./10-release-standard.md) 定義。

## 8.2 Required Output

```text
Versioned Release
```

## 8.3 Minimum Stage Gate

- [ ] Version 已確認
- [ ] CHANGELOG 已更新
- [ ] Release Notes 已完成
- [ ] Validation Report 已通過
- [ ] License 已確認
- [ ] Git Tag 已建立
- [ ] README 與版本一致

# 9. Stage 7 — Evolve

## 9.1 Objective

根據證據與實際使用持續改進 Framework。

Evolve 不等於無限制增加功能，而是有控制地改善價值、品質與可維護性。

## 9.2 Evidence Sources

- GitHub Issues
- Pull Requests
- 使用者回饋
- 測試結果
- 失敗案例
- 官方平台變更
- 安全問題
- 維護成本
- 企業導入經驗

## 9.3 Evolution Activities

- 修正錯誤
- 優化方法論
- 更新 Template
- 更新 Skill
- 新增案例
- 強化測試
- 改善文件
- 移除過時內容
- 提供 Migration Guide
- 規劃下一版本

## 9.4 Change Classification

| Change Type | Example | Version Impact |
|---|---|---|
| Correction | 錯字、失效連結 | Patch |
| Improvement | 增加案例或說明 | Patch / Minor |
| Feature | 新增 Skill 或模組 | Minor |
| Breaking Change | 修改核心流程 | Major |
| Deprecation | 淘汰舊模組 | Minor / Major |
| Security Fix | 修補高風險問題 | Patch / Immediate |

## 9.5 Stage Gate

Evolve 沒有終點，但每次變更必須：

- [ ] 有明確理由
- [ ] 有 Issue 或變更紀錄
- [ ] 經過 Review
- [ ] 通過必要測試
- [ ] 更新 CHANGELOG
- [ ] 依影響調整版本
- [ ] 不違反 Philosophy

---

# 10. Lifecycle State Model

```text
Idea
  ↓
Discovery
  ↓
Defined
  ↓
Designed
  ↓
Developed
  ↓
Validated
  ↓
Released
  ↓
Maintained
  ↓
Deprecated / Archived
```

---

# 11. Lifecycle Roles

同一人可兼任多個角色，但責任必須清楚。

| Role | Responsibility |
|---|---|
| Sponsor | 確認 Framework 價值與方向 |
| Architect | 負責方法論與架構 |
| Maintainer | 維護 Repository 與版本 |
| Contributor | 提交文件、Skill、案例或程式 |
| Reviewer | 獨立檢查品質與一致性 |
| User | 實際使用並提供回饋 |

---

# 12. Lifecycle Artifacts

每個階段應產生可追蹤的 Artifact。

| Stage | Minimum Artifact |
|---|---|
| Discover | Problem Brief |
| Define | Framework Definition |
| Design | Architecture and Methodology |
| Develop | Working Repository |
| Validate | Validation Report |
| Release | Versioned Release |
| Evolve | Roadmap and CHANGELOG |

---

# 13. Exception Handling

若需要跳過或合併階段，必須符合：

1. 明確記錄原因。
2. 說明風險。
3. 指定責任人。
4. 保留補做計畫。
5. 不得跳過 Validate。
6. 不得跳過 Release Versioning。

緊急修正可縮短流程，但仍需事後補齊紀錄。

---

# 14. Quality Checklist

- [ ] Discover 已確認 Framework 必要性
- [ ] Define 已定義邊界與成功條件
- [ ] Design 已建立方法論與架構
- [ ] Develop 已完成可用 Repository
- [ ] Validate 已完成結構、功能與案例驗證
- [ ] Release 已完成版本與發布文件
- [ ] Evolve 已建立回饋與維護機制
- [ ] 所有 Stage Gate 均有紀錄
- [ ] 所有重大變更可追蹤

---

# 15. Definition of Done

本文件完成代表：

- 已建立 CSE Framework 的母方法論
- 已定義七階段 Lifecycle
- 已定義每一階段的目標、輸入、輸出與 Gate
- 已建立 Lifecycle Roles 與 Artifacts
- 已建立例外處理與版本演進規則
- 可供所有後續 CSE Framework 直接套用

---


# Related Documents

- [Philosophy](./00-philosophy.md)
- [Framework Blueprint](./02-framework-blueprint.md)
- [Release Standard](./10-release-standard.md)
- [Validation Standard](./11-validation-standard.md)
- [Glossary](./14-glossary.md)

# Next Document

**02-framework-blueprint.md**

下一份文件將定義每一個 CSE Framework 必須具備的設計藍圖與必要組件。
