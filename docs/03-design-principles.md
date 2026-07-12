# 03 Design Principles

> CSE Meta Framework — Design Principles

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Core Design Standard  
Source of Truth: Design Principles  
Last Updated: 2026-07-11

Depends On:
- `00-philosophy.md`
- `02-framework-blueprint.md`
- `14-glossary.md`

Required By:
- `02-framework-blueprint.md`
- `04-repository-architecture.md`
- `05-document-standards.md`

---

# Purpose

本文件定義 **CSE Meta Framework** 與所有子 Framework 必須遵循的設計原則。

這些原則用來約束：

- Framework Definition
- Framework Blueprint
- Repository Architecture
- Core Methodology
- Documentation
- Skills
- Templates
- Validation
- Governance
- Release

任何設計若與本文件衝突，必須先修正設計，而不是直接實作。

---

# 1. Principle Hierarchy

CSE Design Principles 分為五個層級：

```text
Foundation Principles
        ↓
Architecture Principles
        ↓
Quality Principles
        ↓
Governance Principles
        ↓
Documentation Principles
```

五個層級的優先順序由上而下。

若原則之間發生衝突，優先順序如下：

1. Foundation
2. Architecture
3. Quality
4. Governance
5. Documentation

Documentation 不得凌駕 Framework 的邊界、架構與品質要求。

---

# 2. Foundation Principles

Foundation Principles 定義所有 CSE Framework 的根本設計方向。

---

## 2.1 One Framework, One Core Problem

每個 Framework 只解決一個核心問題。

正確：

```text
CSE TaskRouter
→ 解決任務複雜度分類與模型路由
```

錯誤：

```text
CSE TaskRouter
→ 同時處理提示詞、RAG、Agent、MCP 與程式開發
```

判斷規則：

- 是否能用一句話描述核心問題？
- 是否只有一個主要方法論？
- 是否有清楚的 Repository Boundary？
- 是否需要拆分成多個 Framework？

檢查清單：

- [ ] 核心問題唯一
- [ ] 核心方法論唯一
- [ ] Scope 可清楚描述
- [ ] Non-Goals 已定義
- [ ] 不與其他 Framework 重疊

---

## 2.2 Framework Before Content

先定義 Framework，再產生內容。

正確順序：

```text
Problem
   ↓
Scope
   ↓
Blueprint
   ↓
Methodology
   ↓
Architecture
   ↓
Documentation
   ↓
Skills
   ↓
Examples
```

禁止：

- 未完成 Blueprint 就大量建立文件
- 未定義 Scope 就撰寫 README
- 未完成方法論就建立 Skill
- 用內容數量取代 Framework 設計

---

## 2.3 Task-Driven Design

Framework 應由任務需求驅動，而不是由模型、工具或平台驅動。

應優先描述：

- 任務
- 能力
- 流程
- 輸入
- 輸出
- 驗證

不應優先描述：

- 特定模型名稱
- 特定供應商
- 單一工具介面
- 暫時性的產品功能

固定規則：

```text
Stable Methodology
        +
Dynamic Configuration
```

方法論保持穩定；模型與工具由 `configs/` 管理。

---

## 2.4 Simplicity Before Expansion

優先選擇能解決問題的最簡單結構。

新增模組前，必須回答：

1. 是否真的需要？
2. 是否可由既有模組處理？
3. 是否會增加重複責任？
4. 是否會提高維護成本？
5. 是否能被測試與驗證？

禁止因「看起來完整」而增加無實際用途的文件、目錄或模組。

---

## 2.5 Reusable by Default

所有核心成果應優先設計為可重複使用。

包括：

- Methodology
- Skill
- Prompt
- Template
- Schema
- Config
- Example Pattern
- Validation Rule
- Diagram

一次性內容應放在案例或專案層，不應進入核心標準。

---

## 2.6 Vendor Neutral by Default

核心 Framework 不得綁定單一供應商。

正確：

```text
Reasoning Model
Fast Model
Tool Calling
Structured Output
```

不穩定：

```text
固定依賴某一個產品名稱或版本
```

例外：

- Provider Adapter
- Model Registry
- Platform-specific Example
- Integration Guide

例外內容必須與核心方法論分離。

---

## 2.7 Human Readable and AI Readable

所有內容必須同時方便人類與 AI 使用。

人類可讀性要求：

- 清楚標題
- 短段落
- 結構一致
- 範例明確
- 可快速掃描

AI 可讀性要求：

- 名詞一致
- 邊界明確
- Input / Output 清楚
- 不使用模糊代名詞
- 不依賴隱含上下文
- 規則可被拆解與引用

---

# 3. Architecture Principles

Architecture Principles 定義 Framework 如何被拆分、組合與維護。

---

## 3.1 Single Responsibility

每個模組、資料夾與文件只負責一件事。

範例：

| Component | Responsibility |
|---|---|
| `docs/` | 方法論與規格 |
| `skills/` | 可執行 Skill |
| `prompts/` | Prompt Pattern |
| `configs/` | 可變動設定 |
| `schemas/` | 結構化資料契約 |
| `examples/` | 實際使用案例 |
| `tests/` | 驗證案例 |

禁止：

- Skill 同時存放完整理論
- README 取代全部文件
- Config 混入方法論
- Example 變成核心規則來源

---

## 3.2 Modular Architecture

Framework 必須可拆分成獨立模組。

模組應具備：

- 明確責任
- 明確介面
- 明確輸入
- 明確輸出
- 明確依賴
- 可獨立測試
- 可獨立更新

基本架構：

```text
Core
├── Methodology
├── Architecture
├── Skills
├── Templates
├── Configs
├── Examples
└── Validation
```

---

## 3.3 Low Coupling, High Cohesion

每個模組內部應高度一致，模組之間應降低相依。

高 Cohesion：

```text
所有路由規則集中於 routing 模組
```

低 Coupling：

```text
模型名稱更新不應要求修改所有 Skill
```

實作要求：

- 動態資料集中配置
- 不跨模組複製規則
- 共用內容採引用
- 模組間使用明確契約

---

## 3.4 Stable Core, Flexible Edge

核心方法論應穩定，外圍整合可以快速變動。

```text
Stable Core
├── Philosophy
├── Lifecycle
├── Blueprint
└── Methodology

Flexible Edge
├── Model Registry
├── Provider Adapter
├── Tool Integration
├── Platform Example
└── UI
```

重大平台更新不得迫使核心方法論頻繁重寫。

---

## 3.5 Configuration Over Hardcoding

所有可能變動的內容應優先配置化。

應放入 `configs/`：

- 模型名稱
- 模型版本
- 路由門檻
- Provider 設定
- 工具清單
- Feature Flag
- 預設參數

不應寫死於：

- Skill
- Core Methodology
- Blueprint
- README

---

## 3.6 Explicit Interfaces

模組之間必須有明確介面。

至少定義：

- Input
- Output
- Required Fields
- Optional Fields
- Error States
- Validation Rules
- Compatibility

建議使用：

- JSON Schema
- YAML Schema
- Markdown Contract
- Interface Table

---

## 3.7 Extensibility Without Core Breakage

新增功能不得破壞既有核心。

擴充應優先採用：

- Adapter
- Plugin
- Extension
- Config
- New Example
- New Skill

只有在核心假設失效時，才允許修改 Core Methodology。

---

## 3.8 Traceable Dependencies

所有跨模組與跨 Framework 依賴必須可追蹤。

依賴應記錄：

```yaml
depends_on:
  - framework:
  - version:
  - component:
  - reason:
```

禁止隱性依賴。

---

# 4. Documentation Principles

Documentation Principles 定義所有 CSE 文件如何保持一致與可維護。

---

## 4.1 One Document, One Topic

一份文件只討論一個主要主題。

文件過大時，應拆分為：

- Core Document
- Reference
- Example
- Appendix

禁止：

- 在同一文件混合方法論、範例、變更紀錄與操作手冊
- 用超長 README 容納全部知識

---

## 4.2 Progressive Disclosure

資訊應由淺入深呈現。

建議順序：

```text
Summary
   ↓
Core Concept
   ↓
Rules
   ↓
Workflow
   ↓
Examples
   ↓
Reference
```

README 只提供入口，不應承載全部細節。

---

## 4.3 Consistent Terminology

同一概念只能使用一個正式名稱。

例如：

| Preferred Term | Avoid |
|---|---|
| Framework | 架構、框架、系統混用 |
| Repository | Repo 混用於正式文件 |
| Skill | Tool、Plugin 混用 |
| Validation | Review、Check 無區分使用 |
| Blueprint | Plan、Spec 混用 |

正式術語由 Glossary 管理。

---

## 4.4 Explicit Structure

每份核心文件至少應包含：

1. Purpose
2. Core Rules
3. Architecture or Workflow
4. Checklist
5. Definition of Done

依主題需要可增加：

- Examples
- Failure Modes
- References
- Migration Notes

---

## 4.5 Example-Backed Explanation

重要規則至少提供一個：

- 正確範例
- 錯誤範例
- 使用案例
- 邊界案例

沒有範例的抽象規則，難以驗證與教學。

---

## 4.6 No Uncontrolled Duplication

核心規則只允許存在一個主要來源。

其他文件應使用相對連結引用。

禁止：

- 複製相同方法論到多個檔案
- 不同步的多版本文字
- README、Skill、Docs 各自定義不同規則

---

## 4.7 Dynamic Information Separation

高變動資訊不得與穩定方法論混合。

高變動資訊包括：

- 模型版本
- 價格
- API 名稱
- 功能可用性
- 平台限制

這些資訊應放在：

```text
configs/
references/
provider-guides/
```

---

# 5. Quality Principles

Quality Principles 定義 Framework 如何確保正確、完整與可使用。

---

## 5.1 Validation Is Mandatory

任何 Framework、Skill、Template 或 Release 都必須驗證。

最低要求：

- Structural Validation
- Functional Validation
- Scenario Validation
- Review Validation

未驗證內容只能標示為 Draft 或 Alpha。

---

## 5.2 Evidence-Driven Decisions

重大設計決策應基於證據。

可接受證據：

- 官方文件
- 實際測試
- 可重現案例
- 使用者回饋
- Benchmark
- Failure Analysis
- Issue Records

不可只用：

- 個人偏好
- 流行趨勢
- 未驗證推測
- 單一成功案例

---

## 5.3 Testable by Design

設計階段就必須定義如何測試。

每個核心能力至少需要：

- Standard Case
- Complex Case
- Boundary Case
- Failure Case
- Incomplete Input Case

若無法測試，代表設計尚未完整。

---

## 5.4 Fail Explicitly

Framework 遇到錯誤時，應明確失敗，而不是靜默猜測。

錯誤輸出至少包含：

- Error Type
- Error Message
- Failed Stage
- Missing Input
- Suggested Correction
- Retry Condition

---

## 5.5 Reproducibility

相同輸入與相同版本下，應能得到可比較的結果。

為提高可重現性，需記錄：

- Framework Version
- Skill Version
- Config Version
- Model / Provider
- Input
- Validation Result

---

## 5.6 Known Limitations Are Required

每個 Stable Release 必須列出：

- 不適用情境
- 已知限制
- 未解決問題
- 風險
- 相容性限制

不應將限制隱藏於細節。

---

## 5.7 Quality Over Volume

完整度不以檔案數量或字數衡量。

品質指標包括：

- 邊界是否清楚
- 方法論是否可用
- Skill 是否可執行
- Example 是否可重現
- Validation 是否通過
- 文件是否一致

---

## 5.8 Continuous Improvement

每次發現問題時，不只修正單一輸出，也應評估：

- 是否需要更新 Rule
- 是否需要更新 Template
- 是否需要新增 Test
- 是否需要更新 Example
- 是否需要修改 Config
- 是否需要建立 Migration Note

---

# 6. Governance Principles

Governance Principles 定義 Framework 如何被管理、變更與發布。

---

## 6.1 Clear Ownership

每個 Framework 必須有明確 Owner。

Owner 負責：

- Scope
- Direction
- Major Decisions
- Release Approval
- Deprecation Approval

不得存在無人負責的核心 Framework。

---

## 6.2 Version Every Meaningful Change

有意義的變更必須版本化。

至少更新：

- Version
- CHANGELOG
- Last Updated
- Impact
- Migration Notes（如適用）

---

## 6.3 Backward Compatibility by Default

Minor 與 Patch 更新應維持向下相容。

破壞性變更必須：

- 提升 Major Version
- 提供 Migration Guide
- 標示 Deprecated Components
- 設定過渡期
- 說明影響範圍

---

## 6.4 Review Before Merge

核心變更不得直接合併。

重大變更至少需要：

1. Issue
2. Proposal
3. Impact Analysis
4. Review
5. Validation
6. CHANGELOG Update
7. Version Decision

---

## 6.5 Transparent Decision Records

重大決策應保留紀錄。

建議使用：

```text
docs/decisions/
```

每份 Decision Record 至少包含：

- Context
- Decision
- Alternatives
- Consequences
- Status
- Date
- Owner

---

## 6.6 Deprecate Before Remove

核心功能不得直接刪除。

標準流程：

```text
Active
   ↓
Deprecated
   ↓
Migration Period
   ↓
Removed
```

---

## 6.7 Security and Safety by Design

涉及資料、工具、執行或外部系統時，必須考量：

- 最小權限
- 資料最小化
- 可回復性
- 人工審核
- 日誌紀錄
- 失敗停止
- 未授權操作阻擋

---

# 7. Principle Conflict Resolution

當原則衝突時，依下列順序處理：

```text
Safety
  ↓
Scope and Philosophy
  ↓
Correctness
  ↓
Architecture Integrity
  ↓
Maintainability
  ↓
Usability
  ↓
Convenience
```

範例：

若自動化可提高效率，但會降低安全與可追蹤性，應優先保留人工審核與紀錄。

---

# 8. Design Decision Test

任何重大設計決策都應通過以下八個問題：

1. 是否符合 Philosophy？
2. 是否在 Scope 內？
3. 是否解決核心問題？
4. 是否增加不必要複雜度？
5. 是否可重複使用？
6. 是否可驗證？
7. 是否容易維護？
8. 是否需要版本或遷移處理？

若其中任一關鍵問題答案為否，應停止實作並重新設計。

---

# 9. Anti-Patterns

以下為 CSE Framework 禁止的常見設計模式。

## 9.1 God Framework

一個 Framework 試圖處理所有 AI 問題。

修正：

- 縮小 Scope
- 拆分 Repository
- 建立明確依賴

---

## 9.2 Tool-First Framework

先選工具，再創造問題。

修正：

- 回到 Problem Definition
- 重新確認 Framework Necessity
- 將工具降為 Adapter

---

## 9.3 Documentation-Only Framework

只有文章，沒有方法、Skill、Example 或 Validation。

修正：

- 建立 Core Methodology
- 建立可執行 Skill
- 建立測試案例

---

## 9.4 Hardcoded Framework

模型、版本、參數與流程全部寫死。

修正：

- 將動態資訊移至 `configs/`
- 建立 Adapter
- 定義 Interface

---

## 9.5 Copy-Paste Governance

多份文件各自保存相同規則。

修正：

- 建立 Single Source of Truth
- 改用相對引用
- 增加一致性測試

---

## 9.6 Example as Specification

以單一案例取代正式規則。

修正：

- 先建立 Methodology 與 Contract
- Example 只負責展示

---

## 9.7 Validation After Release

先發布，再決定如何測試。

修正：

- 在 Blueprint 階段定義 Validation
- Release Gate 必須要求 Validation Report

---

# 10. Design Review Checklist

## Foundation

- [ ] 核心問題唯一
- [ ] 核心方法論唯一
- [ ] Scope 與 Non-Goals 清楚
- [ ] 不綁定單一供應商
- [ ] 未增加不必要複雜度

## Architecture

- [ ] 模組責任單一
- [ ] 模組低耦合
- [ ] Config 與 Core 分離
- [ ] Interface 明確
- [ ] 可擴充而不破壞核心
- [ ] 依賴可追蹤

## Documentation

- [ ] 一份文件一個主題
- [ ] 術語一致
- [ ] 沒有失控重複
- [ ] 動態資訊已分離
- [ ] 重要規則有範例

## Quality

- [ ] Validation 已設計
- [ ] Failure Case 已定義
- [ ] Known Limitations 已記錄
- [ ] 核心內容可測試
- [ ] 重大決策有證據支持

## Governance

- [ ] Owner 明確
- [ ] 版本規則清楚
- [ ] Review 流程存在
- [ ] Breaking Change 有遷移規則
- [ ] 安全與可追蹤性已考量

---

# 11. Immediate Corrections

本版已修正舊版 `01-design-principles.md` 的主要問題：

1. **將平面的原則清單改為五層原則架構**
   - Foundation
   - Architecture
   - Documentation
   - Quality
   - Governance

2. **加入原則衝突優先順序**
   - 避免不同規則互相矛盾時無法決策。

3. **加入 Anti-Patterns**
   - 讓設計者能辨識常見錯誤，而不只看到抽象原則。

4. **加入 Design Decision Test**
   - 重大變更可用固定問題快速審查。

5. **將安全、版本與相容性納入設計原則**
   - 避免只重視文件與模組化，忽略企業級治理要求。

---

# 12. Definition of Done

本文件完成代表：

- 已建立 CSE Meta Framework 的五層設計原則
- 已定義 Foundation、Architecture、Documentation、Quality 與 Governance 原則
- 已建立原則衝突處理順序
- 已建立 Design Decision Test
- 已建立 Anti-Patterns
- 已建立完整 Design Review Checklist
- 可作為所有 CSE Framework 的設計審查依據

---

# Related Documents

- [Philosophy](./00-philosophy.md)
- [Framework Blueprint](./02-framework-blueprint.md)
- [Repository Architecture](./04-repository-architecture.md)
- [Glossary](./14-glossary.md)

# Next Document

**04-repository-architecture.md**

下一份文件將重新定義：

- Repository 標準結構
- 必要與選用目錄
- 模組責任
- Dependency Rules
- Config、Schema 與 Test 的位置
- Small、Standard、Enterprise 三種 Repository Profile
