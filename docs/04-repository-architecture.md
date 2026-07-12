# 04 Repository Architecture

> CSE Meta Framework — Repository Architecture

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Architecture Standard  
Source of Truth: Repository Architecture  
Last Updated: 2026-07-11

Depends On:
- `02-framework-blueprint.md`
- `03-design-principles.md`
- `14-glossary.md`

Required By:
- `05-document-standards.md`
- `07-skills-standard.md`
- `09-readme-standard.md`

---

# Purpose

本文件定義所有 CSE Framework Repository 的標準架構。

目標是讓不同 Framework 具備一致的：

- 目錄結構
- 模組責任
- 文件位置
- Skill 位置
- Config 與 Schema 管理方式
- Test 與 Validation 位置
- GitHub 開源治理結構

本文件處理的是 Repository 的結構與責任分配，不取代 Framework Blueprint、Core Methodology 或 Document Standards。

---

# 1. Architecture Objectives

每一個 CSE Repository 應同時達成以下目標：

| Objective | Description |
|---|---|
| Clarity | 使用者能快速理解每個目錄的用途 |
| Modularity | 模組可獨立維護與測試 |
| Reusability | Skill、Template、Schema 可重複使用 |
| Scalability | 可從小型專案擴充到企業級專案 |
| Traceability | 變更、版本與依賴可追蹤 |
| AI Readability | AI 能快速定位規則、範例與配置 |
| Human Readability | 人類可快速瀏覽與理解 |
| Governance | Repository 具備開源維護與發布能力 |

---

# 2. Repository Profiles

CSE 提供三種 Repository Profile：

```text
Small
Standard
Enterprise
```

所有新 Framework 預設採用 **Standard Profile**。

只有在需求明確時，才使用 Small 或 Enterprise。

---

## 2.1 Small Profile

適用：

- 單一小型 Skill
- 內部試驗
- 概念驗證
- 教學範例

標準結構：

```text
repository/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── docs/
│   └── framework.md
├── skills/
│   └── skill.md
├── examples/
│   └── basic.md
└── tests/
    └── smoke-test.md
```

限制：

- 不適合複雜 Framework
- 不適合多模組
- 不適合企業治理
- 不應長期維護大量內容

---

## 2.2 Standard Profile

適用：

- 一般 CSE Framework
- 公開 GitHub 專案
- 多份文件
- 多個 Skill
- 需要 Config、Schema 與 Test

標準結構：

```text
repository/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── ROADMAP.md
├── .gitignore
├── .github/
├── docs/
├── skills/
├── prompts/
├── templates/
├── schemas/
├── configs/
├── examples/
├── tests/
├── diagrams/
├── assets/
└── references/
```

---

## 2.3 Enterprise Profile

適用：

- 企業級 Framework
- 多團隊協作
- 多 Provider 整合
- 自動化測試
- 合規與治理要求
- 長期版本維護

標準結構：

```text
repository/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── GOVERNANCE.md
├── SUPPORT.md
├── ROADMAP.md
├── RELEASE.md
├── .github/
├── docs/
├── skills/
├── prompts/
├── templates/
├── schemas/
├── configs/
├── adapters/
├── integrations/
├── examples/
├── tests/
├── benchmarks/
├── diagrams/
├── assets/
├── references/
├── scripts/
└── tools/
```

---

# 3. Standard Repository Structure

以下為 CSE Standard Profile 的完整標準結構：

```text
CSE-Framework-Name/
│
├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── ROADMAP.md
├── .gitignore
│
├── .github/
│   ├── ISSUE_TEMPLATE/
│   ├── PULL_REQUEST_TEMPLATE.md
│   ├── DISCUSSION_TEMPLATE/
│   └── workflows/
│
├── docs/
│   ├── 00-framework-definition.md
│   ├── 01-design-principles.md
│   ├── 02-architecture.md
│   ├── 03-core-methodology.md
│   ├── 04-workflow.md
│   ├── 05-validation.md
│   ├── 06-governance.md
│   ├── glossary.md
│   └── decisions/
│
├── skills/
│   ├── skill.md
│   ├── router.md
│   ├── validator.md
│   └── reviewers/
│
├── prompts/
│   ├── system/
│   ├── task/
│   ├── review/
│   └── examples/
│
├── templates/
│   ├── framework.template.md
│   ├── skill.template.md
│   ├── prompt.template.md
│   ├── example.template.md
│   └── release.template.md
│
├── schemas/
│   ├── input.schema.json
│   ├── output.schema.json
│   ├── config.schema.json
│   └── validation.schema.json
│
├── configs/
│   ├── framework.yaml
│   ├── routing.yaml
│   ├── models.yaml
│   └── validation.yaml
│
├── examples/
│   ├── beginner/
│   ├── standard/
│   ├── advanced/
│   └── enterprise/
│
├── tests/
│   ├── structural/
│   ├── functional/
│   ├── scenario/
│   └── regression/
│
├── diagrams/
│   ├── architecture.mmd
│   ├── workflow.mmd
│   └── lifecycle.mmd
│
├── assets/
│   ├── images/
│   ├── logos/
│   └── exports/
│
└── references/
    ├── official/
    ├── research/
    └── provider-guides/
```

---

# 4. Root Files

Root Files 提供 Repository 的入口、治理與版本資訊。

---

## 4.1 README.md

責任：

- 說明 Framework 是什麼
- 提供快速開始
- 引導至核心文件
- 顯示目前版本與狀態
- 提供安裝或使用入口

README 不應包含：

- 完整方法論
- 所有案例
- 所有 Skill 內容
- 大量動態資料

---

## 4.2 LICENSE

每個公開 Repository 必須有 License。

若未指定，預設建議：

```text
MIT License
```

企業內部 Repository 可依公司政策調整。

---

## 4.3 CHANGELOG.md

必須記錄：

- Added
- Changed
- Deprecated
- Removed
- Fixed
- Security

不得只寫模糊描述，例如：

```text
更新內容
改善文件
```

---

## 4.4 CONTRIBUTING.md

應定義：

- 如何提交 Issue
- 如何提交 Pull Request
- Branch 規則
- Commit 規則
- Review 流程
- 測試要求

---

## 4.5 CODE_OF_CONDUCT.md

公開開源專案建議必備。

---

## 4.6 SECURITY.md

至少包含：

- 如何回報安全問題
- 不應公開揭露的內容
- 支援版本
- 回應流程

---

## 4.7 ROADMAP.md

記錄：

- Current
- Next
- Later
- Out of Scope

避免以 Roadmap 作為承諾保證。

---

# 5. `.github/` Structure

`.github/` 用於開源協作與自動化。

```text
.github/
├── ISSUE_TEMPLATE/
│   ├── bug_report.md
│   ├── feature_request.md
│   ├── framework_change.md
│   └── documentation_issue.md
├── PULL_REQUEST_TEMPLATE.md
├── DISCUSSION_TEMPLATE/
└── workflows/
    ├── markdown-lint.yml
    ├── link-check.yml
    ├── schema-validation.yml
    └── release-check.yml
```

規則：

- 所有 Issue Template 必須要求版本與重現步驟
- 所有 Pull Request 必須標示影響範圍
- 核心變更必須附 Validation Result
- Workflow 不得依賴未記錄的 Secret 或外部服務

---

# 6. `docs/` Structure

`docs/` 是 Framework 的知識與規格來源。

以下結構適用於**一般子 Framework Repository**：

```text
docs/
├── 00-framework-definition.md
├── 01-design-principles.md
├── 02-architecture.md
├── 03-core-methodology.md
├── 04-workflow.md
├── 05-validation.md
├── 06-governance.md
├── glossary.md
└── decisions/
```

責任：

- 保存穩定方法論
- 保存設計決策
- 保存規則與邊界
- 保存正式術語

禁止：

- 放模型版本清單
- 放大量可變動設定
- 放單次案例
- 放未整理的草稿

---

## 6.1 `docs/decisions/`

用於保存 Architecture Decision Record。

建議格式：

```text
ADR-001-framework-boundary.md
ADR-002-config-separation.md
ADR-003-skill-versioning.md
```

每份 ADR 至少包含：

- Context
- Decision
- Alternatives
- Consequences
- Status
- Date
- Owner

---

# 7. `skills/` Structure

`skills/` 儲存可直接被 AI 使用的 Skill。

```text
skills/
├── skill.md
├── router.md
├── validator.md
└── reviewers/
```

本文件只定義位置與責任：

```text
docs/   → 說明方法論
skills/ → 執行方法論
```

Skill Package、Front Matter、Input / Output Contract、Validation、Versioning 與 Platform Adapter，統一由 [Skills Standard](./07-skills-standard.md) 定義。

# 8. `prompts/` Structure

`prompts/` 儲存 Prompt Pattern，不儲存完整 Framework 規格。

```text
prompts/
├── system/
├── task/
├── review/
└── examples/
```

分類：

| Folder | Purpose |
|---|---|
| system | 系統級提示詞 |
| task | 任務級提示詞 |
| review | 驗證與審查提示詞 |
| examples | Prompt 使用範例 |

規則：

- Prompt 應可獨立引用
- Prompt 不得與 Skill 重複
- Prompt 版本需可追蹤
- Prompt 內不得放動態模型名稱

---

# 9. `templates/` Structure

`templates/` 儲存可重複使用的文件模板。

```text
templates/
├── framework.template.md
├── skill.template.md
├── prompt.template.md
├── example.template.md
└── release.template.md
```

規則：

- Template 不包含特定案例內容
- Placeholder 必須明確
- Template 必須可直接複製
- Template 變更應更新版本

---

# 10. `schemas/` Structure

`schemas/` 定義結構化資料契約。

```text
schemas/
├── input.schema.json
├── output.schema.json
├── config.schema.json
└── validation.schema.json
```

用途：

- 結構化輸入
- 結構化輸出
- Config 驗證
- API 整合
- 自動化測試

規則：

- Schema 需有 `$schema`
- Schema 需有 version
- Required 欄位必須明確
- 不相容變更需提升 Major Version

---

# 11. `configs/` Structure

`configs/` 儲存可變動設定。

```text
configs/
├── framework.yaml
├── routing.yaml
├── models.yaml
└── validation.yaml
```

應放入：

- 模型名稱
- 模型版本
- Provider 設定
- 路由門檻
- Feature Flags
- 驗證門檻
- 預設參數

不應放入：

- 核心哲學
- 核心方法論
- 長篇說明
- 一次性案例

固定原則：

```text
Core is stable.
Config is changeable.
```

---

# 12. `examples/` Structure

`examples/` 用於展示 Framework 的實際使用。

```text
examples/
├── beginner/
├── standard/
├── advanced/
└── enterprise/
```

每個 Example 至少包含：

1. Problem
2. Context
3. Input
4. Workflow
5. Output
6. Validation
7. Lessons Learned

禁止：

- 只有 Prompt
- 只有最終答案
- 未標示使用條件
- 使用未驗證輸出作為規格來源

---

# 13. `tests/` Structure

`tests/` 用於保存可重複執行的驗證案例。

```text
tests/
├── structural/
├── functional/
├── scenario/
└── regression/
```

本文件只定義測試位置與分類。Validation Levels、Acceptance Criteria、Severity、Decision 與報告格式，統一由 [Validation Standard](./11-validation-standard.md) 定義。

# 14. `diagrams/` Structure

`diagrams/` 保存圖表原始檔。

```text
diagrams/
├── architecture.mmd
├── workflow.mmd
└── lifecycle.mmd
```

規則：

- Mermaid `.mmd` 為唯一原始來源
- PNG / SVG 只作展示
- 圖表內容必須與 docs 一致
- 不得只保留圖片而失去可編輯來源

---

# 15. `assets/` Structure

`assets/` 儲存非核心知識資產。

```text
assets/
├── images/
├── logos/
└── exports/
```

可放：

- Logo
- Banner
- 圖片
- 匯出 PNG
- 匯出 SVG

禁止：

- 核心方法論
- 主要規格
- Skill
- Config
- Schema

---

# 16. `references/` Structure

`references/` 保存外部參考資料與平台說明。

```text
references/
├── official/
├── research/
└── provider-guides/
```

分類：

- `official/`：官方文件摘要或連結
- `research/`：論文與研究來源
- `provider-guides/`：特定平台整合說明

規則：

- 外部資料不得取代核心方法論
- 需標示來源與更新日期
- 易變資訊必須獨立管理
- 過時內容需標示 Deprecated

---

# 17. Optional Enterprise Folders

Enterprise Profile 可增加：

```text
adapters/
integrations/
benchmarks/
scripts/
tools/
```

---

## 17.1 `adapters/`

用於平台或 Provider 適配。

例如：

```text
adapters/
├── openai/
├── anthropic/
├── google/
└── xai/
```

Adapter 不得修改核心方法論。

---

## 17.2 `integrations/`

用於外部系統整合。

例如：

```text
integrations/
├── github/
├── slack/
├── notion/
└── mcp/
```

---

## 17.3 `benchmarks/`

用於正式效能比較與品質評估。

至少記錄：

- Benchmark Version
- Test Dataset
- Environment
- Result
- Limitations

---

## 17.4 `scripts/`

儲存 Repository 維護腳本。

例如：

- 連結檢查
- Schema 驗證
- 版本同步
- Release 打包

---

## 17.5 `tools/`

儲存輔助工具，不應與 Skill 混用。

---

# 18. Dependency Rules

所有依賴必須明確。

## 18.1 Internal Dependency

建議方向：

```text
docs
  ↓
skills
  ↓
examples
  ↓
tests
```

不可反向依賴：

```text
docs 不應依賴 examples 才能成立
core methodology 不應依賴特定 Skill
```

---

## 18.2 Cross-Framework Dependency

依賴其他 CSE Framework 時，必須記錄：

```yaml
dependency:
  framework:
  version:
  component:
  required:
  reason:
```

---

## 18.3 Dependency Principles

- 避免循環依賴
- 避免未記錄依賴
- 避免將 Provider 當核心依賴
- 依賴版本應可追蹤
- 非必要依賴應標示 Optional

---

# 19. Required and Optional Components

| Component | Small | Standard | Enterprise |
|---|---:|---:|---:|
| README | Required | Required | Required |
| LICENSE | Required | Required | Required |
| CHANGELOG | Required | Required | Required |
| docs | Required | Required | Required |
| skills | Required | Required | Required |
| examples | Required | Required | Required |
| tests | Required | Required | Required |
| prompts | Optional | Required | Required |
| templates | Optional | Required | Required |
| schemas | Optional | Required | Required |
| configs | Optional | Required | Required |
| diagrams | Optional | Required | Required |
| references | Optional | Required | Required |
| adapters | No | Optional | Required when multi-provider |
| integrations | No | Optional | Optional / Required |
| benchmarks | No | Optional | Required for formal comparison |
| scripts | Optional | Optional | Recommended |

---

# 20. Repository Naming Rules

Repository：

```text
CSE-<Framework-Name>
```

Folder：

```text
kebab-case
```

Markdown：

```text
00-framework-definition.md
01-design-principles.md
```

Schema：

```text
input.schema.json
output.schema.json
```

Config：

```text
framework.yaml
routing.yaml
```

Mermaid：

```text
architecture.mmd
workflow.mmd
```

禁止：

- 空格
- 中文檔名
- 無意義縮寫
- 同時使用 snake_case 與 kebab-case
- 目錄名稱與責任不一致

---

# 21. Repository Creation Sequence

建立新 Repository 時，依序執行：

```text
1. Confirm Profile
2. Create Root Files
3. Create docs/
4. Create configs/ and schemas/
5. Create skills/
6. Create prompts/
7. Create templates/
8. Create examples/
9. Create tests/
10. Create diagrams/
11. Write README
12. Run Validation
```

README 在核心內容完成後建立。

---

# 22. Architecture Validation Checklist

## Profile

- [ ] 已選擇 Small、Standard 或 Enterprise
- [ ] Profile 與實際需求一致

## Root

- [ ] README 存在
- [ ] LICENSE 存在
- [ ] CHANGELOG 存在
- [ ] SECURITY 存在
- [ ] CONTRIBUTING 存在

## Core Folders

- [ ] docs 存在
- [ ] skills 存在
- [ ] examples 存在
- [ ] tests 存在
- [ ] configs 與 schemas 已依需求建立

## Responsibilities

- [ ] 每個目錄責任唯一
- [ ] 無重複存放核心規則
- [ ] Dynamic Data 已放入 configs
- [ ] External References 已放入 references
- [ ] Skill 與 Knowledge 已分離

## Dependencies

- [ ] 內部依賴方向正確
- [ ] 無循環依賴
- [ ] Cross-Framework Dependency 已記錄
- [ ] Provider Dependency 未進入 Stable Core

## Validation

- [ ] Structural Test 存在
- [ ] Functional Test 存在
- [ ] Scenario Test 存在
- [ ] Diagram 原始檔存在

---

# 23. Immediate Corrections

本版已修正舊版 `02-repository-architecture.md` 的主要問題：

1. **新增 Small、Standard、Enterprise 三種 Profile**
   - 避免所有專案被迫使用相同規模。

2. **將必要與選用目錄分開**
   - 降低小型 Framework 的不必要負擔。

3. **新增 Root Governance Files**
   - 包含 SECURITY、CONTRIBUTING、CODE_OF_CONDUCT 與 ROADMAP。

4. **加入 Dependency Rules**
   - 明確規範模組與跨 Framework 依賴。

5. **加入 `references/`**
   - 外部官方資料與核心方法論分離。

6. **加入 Enterprise 擴充層**
   - adapters、integrations、benchmarks、scripts、tools。

7. **固定 README 最後撰寫**
   - 避免 README 與實際 Framework 不一致。

8. **建立 Required / Optional Matrix**
   - 讓不同規模的 Repository 能正確選擇架構。

---

# 24. Definition of Done

本文件完成代表：

- 已建立三種 Repository Profile
- 已定義 Standard Profile 完整架構
- 已定義每個目錄與 Root File 的責任
- 已建立 Config、Schema、Skill、Example 與 Test 的位置
- 已定義 Dependency Rules
- 已定義 Enterprise 擴充目錄
- 已建立 Required / Optional Matrix
- 已建立 Repository Creation Sequence
- 已建立 Architecture Validation Checklist
- 可作為所有 CSE Framework Repository 的結構標準

---


# Related Documents

- [Design Principles](./03-design-principles.md)
- [Document Standards](./05-document-standards.md)
- [Skills Standard](./07-skills-standard.md)
- [Validation Standard](./11-validation-standard.md)
- [Security Standard](./13-security-standard.md)
- [Glossary](./14-glossary.md)

# Next Document

**05-document-standards.md**

下一份文件將重新定義：

- Metadata Standard
- Markdown Structure
- Heading Rules
- Terminology Rules
- Tables and Code Blocks
- Cross-Reference Rules
- Dynamic Information Handling
- AI Readability
- Documentation Validation
