# 15 Roadmap

> CSE Meta Framework — Roadmap

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Last Updated: 2026-07-11

---

# Purpose

本文件定義 **CSE Meta Framework** 的建設順序、版本目標、里程碑、優先級與明確排除範圍。

Roadmap 的目的，是讓 CSE Meta Framework 依照一致節奏持續完成，而不是同時展開過多文件、Skill、Template、Automation 與子 Framework。

本文件不構成時間承諾。

Roadmap 只代表目前優先順序，實際進度需依：

- Validation 結果
- 資源
- 風險
- 依賴
- 使用者回饋
- Release Readiness

進行調整。

---

# 1. Roadmap Principles

所有 Roadmap 決策必須遵循：

1. **Foundation Before Expansion**
2. **Core Before Automation**
3. **Validation Before Scale**
4. **Templates Before Repetition**
5. **One Milestone at a Time**
6. **No Feature Without Owner**
7. **No Release Without Evidence**
8. **Out of Scope Must Stay Visible**
9. **Roadmap Is Prioritization, Not Promise**
10. **Every Milestone Must Have Exit Criteria**

---

# 2. Roadmap Structure

CSE Roadmap 採用四層時間視角：

```text
Current
  ↓
Next
  ↓
Later
  ↓
Future
```

| Horizon | Meaning |
|---|---|
| Current | 正在完成，直接影響 v1.0 |
| Next | v1.0 完成後優先處理 |
| Later | 核心穩定後再擴充 |
| Future | 方向性規劃，尚未承諾 |

---

# 3. Current — Complete CSE Meta Framework v1.0

目前最重要目標：

> 完成 CSE Meta Framework v1.0 的核心文件、模板、驗證與發布基礎。

---

## 3.1 Core Documents

目前核心文件清單：

- [x] `00-philosophy.md`
- [x] `01-framework-lifecycle.md`
- [x] `02-framework-blueprint.md`
- [x] `03-design-principles.md`
- [x] `04-repository-architecture.md`
- [x] `05-document-standards.md`
- [x] `06-core-methodology.md`
- [x] `07-skills-standard.md`
- [x] `08-template-standard.md`
- [x] `09-readme-standard.md`
- [x] `10-release-standard.md`
- [x] `11-validation-standard.md`
- [x] `12-governance-standard.md`
- [x] `13-security-standard.md`
- [x] `14-glossary.md`
- [x] `15-roadmap.md`

## 3.2 Remaining v1.0 Foundation Work

v1.0 尚需完成：

- [ ] 核心文件一致性審查
- [ ] 交叉連結
- [ ] 版本同步
- [ ] Metadata 檢查
- [ ] 術語一致性檢查
- [ ] 重複內容檢查
- [ ] Scope 衝突檢查
- [ ] Validation Report
- [ ] README.md
- [ ] LICENSE
- [ ] CHANGELOG.md
- [ ] CONTRIBUTING.md
- [ ] CODE_OF_CONDUCT.md
- [ ] SECURITY.md
- [ ] RELEASE.md
- [ ] GitHub Repository 結構
- [ ] Release Candidate

---

# 4. v1.0 Release Scope

CSE Meta Framework v1.0 必須提供：

## 4.1 Required Core

- Philosophy
- Framework Lifecycle
- Framework Blueprint
- Design Principles
- Repository Architecture
- Document Standards
- Core Methodology
- Skills Standard
- Template Standard
- README Standard
- Release Standard
- Validation Standard
- Governance Standard
- Security Standard
- Glossary
- Roadmap

## 4.2 Required Repository Files

- README.md
- LICENSE
- CHANGELOG.md
- CONTRIBUTING.md
- CODE_OF_CONDUCT.md
- SECURITY.md
- ROADMAP.md
- RELEASE.md

## 4.3 Required Templates

- Framework Definition Template
- Framework Blueprint Template
- README Template
- Skill Template
- Prompt Template
- Example Template
- ADR Template
- Validation Plan Template
- Validation Report Template
- Release Notes Template
- Migration Guide Template

## 4.4 Required Validation

- Structural Validation
- Content Validation
- Terminology Validation
- Cross-Link Validation
- Template Render Validation
- Security Review
- Release Readiness Review

---

# 5. v1.0 Milestones

---

## Milestone 1 — Core Documents Complete

### Objective

完成所有 00–15 核心文件。

### Deliverables

- 16 份核心文件
- 統一 Metadata
- 統一術語
- 明確 Next Document

### Exit Criteria

- [ ] 所有文件存在
- [ ] 無缺漏章節
- [ ] 無明顯 Scope 衝突
- [ ] Glossary 可涵蓋核心術語
- [ ] 文件順序合理

### Status

```text
Current
```

---

## Milestone 2 — Core Consistency Review

### Objective

驗證所有核心文件彼此一致。

### Checks

- Philosophy Alignment
- Lifecycle Alignment
- Blueprint Alignment
- Terminology Alignment
- Repository Alignment
- Skill Alignment
- Validation Alignment
- Security Alignment
- Governance Alignment

### Exit Criteria

- [ ] 核心術語一致
- [ ] 文件角色不重疊
- [ ] Source of Truth 清楚
- [ ] Cross-References 完整
- [ ] 重複內容已移除
- [ ] 衝突規則已修正

### Status

```text
Next
```

---

## Milestone 3 — Template Package

### Objective

將標準轉換為可直接使用的 Template。

### Deliverables

```text
templates/
├── framework/
├── repository/
├── skills/
├── prompts/
├── examples/
├── decisions/
├── validation/
└── release/
```

### Exit Criteria

- [ ] Template Registry 完成
- [ ] Required Placeholder 完整
- [ ] Render Test 通過
- [ ] 無殘留 Placeholder
- [ ] 與 Source Standard 一致

### Status

```text
Next
```

---

## Milestone 4 — Validation Package

### Objective

建立可重複的 Validation Artifact。

### Deliverables

- Validation Plan
- Validation Report
- Structural Checklist
- Content Checklist
- Security Checklist
- Release Checklist
- Regression Test Plan

### Exit Criteria

- [ ] Validation Matrix 完成
- [ ] Acceptance Criteria 明確
- [ ] Critical Error 定義完成
- [ ] 報告模板可使用
- [ ] Evidence Storage 結構完成

### Status

```text
Next
```

---

## Milestone 5 — Repository Governance Files

### Objective

完成正式開源 Repository 所需治理文件。

### Deliverables

- README.md
- LICENSE
- CHANGELOG.md
- CONTRIBUTING.md
- CODE_OF_CONDUCT.md
- SECURITY.md
- RELEASE.md
- SUPPORT.md（如適用）

### Exit Criteria

- [ ] Root Files 完整
- [ ] 所有連結有效
- [ ] Version 一致
- [ ] Security Contact 流程明確
- [ ] Contribution Flow 明確

### Status

```text
Next
```

---

## Milestone 6 — Release Candidate

### Objective

建立 `v1.0.0-rc.1`。

### Required Actions

- Freeze Scope
- Freeze Core Structure
- Run Validation
- Fix Critical Issues
- Publish RC
- Collect Review

### Exit Criteria

- [ ] Critical Error = 0
- [ ] Major Issues 已處理
- [ ] README 完成
- [ ] Validation Report 完成
- [ ] Release Notes 完成
- [ ] Owner Approval 完成

### Status

```text
Later
```

---

## Milestone 7 — Stable v1.0.0

### Objective

正式發布 CSE Meta Framework v1.0.0。

### Exit Criteria

- [ ] RC 通過
- [ ] Git Tag 建立
- [ ] GitHub Release 建立
- [ ] Release Notes 完整
- [ ] Validation Report 通過
- [ ] Post-Release Review 已排定

### Status

```text
Later
```

---

# 6. Next — Build the First Reference Framework

CSE Meta Framework v1.0 完成後，下一步不是同時建立所有子 Framework。

應先建立一個 Reference Implementation，驗證 Meta Framework 是否真的可用。

建議第一個 Reference Framework：

```text
CSE-TaskRouter
```

理由：

- Scope 清楚
- 方法論明確
- 可直接驗證 Blueprint
- 可驗證 Skill Standard
- 可驗證 Config 與 Schema
- 可驗證 README 與 Release Standard
- 可作為其他 Framework 的參考樣板

---

# 7. CSE-TaskRouter Reference Milestones

## Milestone A — Discover and Define

- Problem Brief
- Framework Definition
- Scope
- Non-Goals
- Target Users
- Success Criteria

## Milestone B — Blueprint

- Core Methodology
- Architecture
- Inputs / Outputs
- Validation Design
- Governance
- Release Criteria

## Milestone C — Repository

- docs
- skills
- configs
- schemas
- examples
- tests
- templates

## Milestone D — Validation

- Quick Task
- Standard Task
- Deep Task
- Strategic Task
- Boundary Cases
- Failure Cases

## Milestone E — Release

- v0.1.0 Alpha
- v0.5.0 Beta
- v1.0.0 Stable

---

# 8. Later — Expand the CSE Framework Family

只有在 CSE-TaskRouter 通過實際驗證後，才進入下一批 Framework。

建議順序：

1. CSE Prompt Engineering
2. CSE Context Engineering
3. CSE Workflow Engineering
4. CSE Agent Framework
5. CSE MCP Framework
6. CSE Validation Framework
7. CSE Governance Framework

順序原則：

```text
Prompt
  ↓
Context
  ↓
Workflow
  ↓
Agent
  ↓
MCP
```

不得同時大量建立所有 Framework。

---

# 9. Later — Automation

Automation 應在核心文件、模板與 Reference Framework 穩定後才建立。

建議項目：

- Repository Generator
- Metadata Validator
- Link Checker
- Markdown Linter
- Template Renderer
- Placeholder Checker
- Version Synchronizer
- Schema Validator
- Secret Scanner
- Release Readiness Checker
- Framework Compliance Checker

Automation 不得成為 v1.0 核心發布的阻塞條件，除非影響安全或一致性。

---

# 10. Future — CSE Tooling Ecosystem

Future 項目僅為方向性規劃。

可能包含：

- CLI
- Web-based Framework Builder
- VS Code Extension
- GitHub App
- Automated ADR Generator
- Automated Validation Dashboard
- Framework Registry
- Skill Registry
- Provider Adapter Registry
- Enterprise Compliance Pack
- Training and Certification Materials

這些項目目前不屬於 v1.0 Scope。

---

# 11. Priority Model

所有 Roadmap 項目使用以下優先級：

| Priority | Meaning |
|---|---|
| P0 | 阻止核心發布，必須立即處理 |
| P1 | v1.0 必須完成 |
| P2 | v1.0 後優先處理 |
| P3 | 可延後 |
| P4 | Future / Research |

## 11.1 Priority Rules

P0：

- Critical Security Issue
- Core Contradiction
- Missing Release Requirement
- Broken Validation
- Data Exposure Risk

P1：

- Core Documents
- Templates
- Validation
- README
- Governance Files
- Release Candidate

P2：

- Reference Framework
- Automation Foundation
- Additional Examples

P3：

- Extended Adapters
- Optional Integrations
- Advanced Benchmarks

P4：

- CLI
- Web Platform
- Certification
- Ecosystem Marketplace

---

# 12. Dependency Map

```text
Core Documents
      ↓
Consistency Review
      ↓
Templates
      ↓
Validation Package
      ↓
Repository Governance Files
      ↓
Release Candidate
      ↓
Stable v1.0
      ↓
CSE-TaskRouter
      ↓
Other CSE Frameworks
      ↓
Automation and Ecosystem
```

任何後續項目不得跳過其前置依賴。

---

# 13. Roadmap Entry Requirements

任何新 Roadmap 項目必須包含：

```yaml
roadmap_item:
  id:
  title:
  objective:
  reason:
  owner:
  priority:
  dependencies:
  deliverables:
  exit_criteria:
  risks:
  status:
```

沒有 Owner 或 Exit Criteria 的項目不得加入正式 Roadmap。

---

# 14. Roadmap Status

允許狀態：

```text
Proposed
Approved
Current
Blocked
Deferred
Completed
Cancelled
```

不得使用模糊狀態：

```text
Doing
Soon
Maybe
Almost Done
```

---

# 15. Exit Criteria

每個 Milestone 都必須有 Exit Criteria。

良好 Exit Criteria：

```text
Validation Report 通過
Critical Error = 0
所有 Required Files 存在
```

不良 Exit Criteria：

```text
大致完成
內容很多
看起來可用
```

---

# 16. Roadmap Review

Roadmap 應在以下時點 Review：

- 每個 Milestone 完成後
- 每次 Major Release 前
- 出現 Critical Issue 時
- Scope 變更時
- 核心依賴失效時
- 每季一次（Enterprise Profile）

Review 內容：

- Priority 是否仍合理
- Dependencies 是否變更
- Risks 是否增加
- Owner 是否仍有效
- Exit Criteria 是否可達成
- Out of Scope 是否被突破

---

# 17. Out of Scope for v1.0

CSE Meta Framework v1.0 明確不包含：

- 完整 CLI
- Web App
- GitHub App
- Provider Marketplace
- Skill Marketplace
- 自動化部署平台
- 商業認證
- 完整課程教材
- 所有子 Framework
- 所有平台 Adapter
- 模型 Benchmark 系統
- 企業合規認證套件

若這些項目提前出現，應移至 Future，不得影響 v1.0 核心發布。

---

# 18. Risks

## 18.1 Scope Expansion

風險：

持續新增文件，導致 v1.0 無法完成。

控制：

- 凍結 v1.0 Scope
- 新需求移至 Next / Later
- 使用 Change Control

## 18.2 Documentation Drift

風險：

文件彼此矛盾。

控制：

- Consistency Review
- Glossary
- Source of Truth
- Cross-Link Validation

## 18.3 Over-Engineering

風險：

在實際驗證前建立過多自動化與工具。

控制：

- 先完成 Reference Framework
- Automation 延後

## 18.4 Owner Bottleneck

風險：

所有決策集中單一 Owner。

控制：

- 分配 Maintainer、Architect、Reviewer
- 建立 RACI

## 18.5 Unvalidated Standard

風險：

標準看似完整，但沒有實際 Framework 驗證。

控制：

- 建立 CSE-TaskRouter Reference Implementation

---

# 19. Roadmap Metrics

建議追蹤：

| Metric | Target |
|---|---|
| Core Documents Completed | 16 / 16 |
| Critical Contradictions | 0 |
| Broken Internal Links | 0 |
| Stable Templates | >= 8 |
| Validation Coverage | 100% Core Files |
| Critical Security Findings | 0 |
| Release Readiness | Pass |
| Reference Framework | 1 Completed |

---

# 20. Current Priority Board

| Priority | Work Item | Status |
|---|---|---|
| P0 | Core contradiction review | Proposed |
| P1 | Complete core documents | Current |
| P1 | Cross-reference and metadata review | Next |
| P1 | Build template package | Next |
| P1 | Build validation package | Next |
| P1 | Create README and governance files | Next |
| P1 | Release Candidate | Later |
| P2 | Build CSE-TaskRouter | Later |
| P3 | Build automation scripts | Deferred |
| P4 | Build CLI / Web tools | Future |

---

# 21. Roadmap Checklist

## Scope

- [ ] v1.0 Scope 明確
- [ ] Out of Scope 明確
- [ ] 新需求未直接擴張 Scope

## Milestones

- [ ] 每個 Milestone 有 Objective
- [ ] 每個 Milestone 有 Deliverables
- [ ] 每個 Milestone 有 Exit Criteria
- [ ] 每個 Milestone 有 Status

## Priority

- [ ] P0 / P1 已明確
- [ ] Owner 已指定
- [ ] Dependencies 已記錄
- [ ] Risks 已記錄

## Release

- [ ] RC 路徑清楚
- [ ] Stable Release 條件清楚
- [ ] Validation 為必要條件
- [ ] Post-Release Review 已納入

---

# 22. Anti-Patterns

## 22.1 Everything Is Current

所有項目同時進行。

修正：

- 僅保留少量 Current 項目。

## 22.2 Roadmap Without Exit Criteria

只有項目名稱，沒有完成定義。

修正：

- 每個 Milestone 都需 Exit Criteria。

## 22.3 Tooling Before Core

先開發 CLI、App、Automation。

修正：

- 先完成核心文件與 Reference Framework。

## 22.4 Hidden Scope Expansion

需求直接加入 Current。

修正：

- 經 Change Control 後放入 Next、Later 或 Future。

## 22.5 Roadmap as Promise

把 Roadmap 當成固定交期承諾。

修正：

- Roadmap 只代表優先順序。

## 22.6 No Reference Implementation

只有 Meta Standard，沒有實際 Framework 驗證。

修正：

- CSE-TaskRouter 作為第一個 Reference Framework。

---

# 23. Immediate Corrections

本版已建立並修正以下核心要求：

1. **Roadmap 不再只是待辦清單**
   - 加入 Priority、Dependencies、Milestones 與 Exit Criteria。

2. **v1.0 Scope 明確凍結**
   - 先完成 Meta Framework，不提前展開工具生態。

3. **將 CSE-TaskRouter 定義為第一個 Reference Framework**
   - 用實際專案驗證 Meta Framework。

4. **Automation 延後**
   - 核心與 Template 穩定後再建立。

5. **建立 Current、Next、Later、Future**
   - 避免所有工作同時進行。

6. **加入 Risk、Metrics 與 Review**
   - Roadmap 可追蹤、可調整、可治理。

7. **明確列出 v1.0 Out of Scope**
   - 防止無限擴張。

---

# 24. Definition of Done

本文件完成代表：

- 已定義 CSE Meta Framework 的 Roadmap 結構
- 已建立 Current、Next、Later、Future
- 已定義 v1.0 Release Scope
- 已建立七個主要 Milestone
- 已定義 CSE-TaskRouter 為第一個 Reference Framework
- 已建立後續 Framework 建設順序
- 已定義 Automation 與 Future Ecosystem
- 已建立 Priority Model、Dependency Map 與 Exit Criteria
- 已建立 Risks、Metrics 與 Review 規則
- 已明確列出 v1.0 Out of Scope
- 可作為 CSE Meta Framework 後續開發與發布的正式優先級依據

---

# Next Step

核心文件 `00` 至 `15` 已完成初稿。

下一步最重要的工作是：

```text
Core Consistency Review
```

應依序執行：

1. Metadata Review
2. Terminology Review
3. Scope Conflict Review
4. Source of Truth Review
5. Cross-Reference Review
6. Duplicate Content Review
7. Release Readiness Gap Review
