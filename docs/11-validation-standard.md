# 11 Validation Standard

> CSE Meta Framework — Validation Standard

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Quality Standard  
Source of Truth: Validation Standard  
Last Updated: 2026-07-11

Depends On:
- `06-core-methodology.md`
- `10-release-standard.md`
- `12-governance-standard.md`
- `13-security-standard.md`
- `14-glossary.md`

Required By:
- `06-core-methodology.md`
- `07-skills-standard.md`
- `08-template-standard.md`
- `10-release-standard.md`
- `12-governance-standard.md`
- `13-security-standard.md`
- `15-roadmap.md`

---

# Purpose

本文件定義所有 CSE Framework、Skill、Template、Prompt、Config、Schema、Example、Documentation 與 Release 的驗證標準。

Validation 的目的不是確認內容「看起來合理」，而是建立一套可重複、可追蹤、可審查的品質判定機制。

任何未通過必要驗證的 Artifact，不得標示為 Stable，也不得進入正式 Release。

---

# 1. Validation Principles

所有 CSE Validation 必須遵循以下原則：

1. **Validation Is Mandatory**
2. **Validation Must Be Designed Early**
3. **Independent Review Is Preferred**
4. **Critical Errors Block Release**
5. **Evidence Must Be Traceable**
6. **Acceptance Criteria Must Be Explicit**
7. **Failure Cases Must Be Tested**
8. **Regression Must Be Prevented**
9. **Human Review Is Required for High-Risk Work**
10. **Validation Results Must Be Recorded**

---

# 2. Validation Scope

本標準適用於：

- Framework Definition
- Framework Blueprint
- Core Methodology
- Repository Structure
- Documentation
- Skills
- Prompts
- Templates
- Configs
- Schemas
- Examples
- Diagrams
- Integrations
- Adapters
- Benchmarks
- Releases

---

# 3. Validation Levels

CSE Validation 分為七個層級：

| Level | Name | Purpose |
|---|---|---|
| L1 | Structural Validation | 驗證結構、命名、Metadata 與必要檔案 |
| L2 | Content Validation | 驗證內容正確性、完整性與一致性 |
| L3 | Functional Validation | 驗證 Skill、Template、Schema、Config 是否可運作 |
| L4 | Scenario Validation | 使用實際情境測試 |
| L5 | Regression Validation | 確保新版未破壞既有功能 |
| L6 | Security and Safety Validation | 驗證權限、資料、風險與安全 |
| L7 | Human Review | 高風險與策略內容的人工審查 |

不同 Artifact 可使用不同深度，但不得省略其必要層級。

---

# 4. Validation Lifecycle

標準流程：

```text
Plan
  ↓
Prepare
  ↓
Execute
  ↓
Record
  ↓
Review
  ↓
Decide
  ↓
Improve
```

每次 Validation 必須產生可追蹤結果。

---

# 5. Stage 1 — Validation Plan

## 5.1 Objective

在執行驗證前，先定義驗證範圍、方法與通過條件。

## 5.2 Required Fields

Validation Plan 至少包含：

- Artifact Name
- Artifact Version
- Validation Scope
- Validation Levels
- Test Cases
- Test Environment
- Acceptance Criteria
- Critical Error Definition
- Reviewer
- Human Review Requirement
- Expected Completion Date

## 5.3 Validation Plan Template

```yaml
validation_plan:
  artifact:
  version:
  scope:
  levels:
  test_cases:
  environment:
  acceptance_criteria:
  critical_error_definition:
  reviewer:
  human_review_required:
```

## 5.4 Stage Gate

- [ ] Artifact 與 Version 已確認
- [ ] Scope 已定義
- [ ] Validation Levels 已選擇
- [ ] Acceptance Criteria 已建立
- [ ] Critical Error 已定義
- [ ] Reviewer 已指定

---

# 6. Level 1 — Structural Validation

## 6.1 Objective

確認 Artifact 的結構符合 CSE 標準。

## 6.2 Checks

### Repository

- 必要 Root Files 是否存在
- 必要目錄是否存在
- Profile 是否正確
- 命名是否符合規範
- 無不應存在的重複檔案

### Document

- Metadata 是否完整
- Heading 是否正確
- File Name 是否正確
- Required Sections 是否存在
- Link 是否有效
- Code Block 是否標示語言

### Skill

- Front Matter 是否完整
- Input / Output Contract 是否存在
- Validation 是否存在
- Error Handling 是否存在
- Version 是否存在

### Template

- Metadata 是否完整
- Placeholder 是否正確
- Source Standard 是否存在
- Required Placeholder 是否齊全

### Schema

- `$schema` 是否存在
- Required Fields 是否明確
- Version 是否存在
- JSON 是否有效

## 6.3 Structural Result

```yaml
structural_validation:
  status:
  missing_files:
  naming_errors:
  metadata_errors:
  link_errors:
  schema_errors:
```

---

# 7. Level 2 — Content Validation

## 7.1 Objective

確認內容正確、完整、一致，且符合 Scope。

## 7.2 Validation Dimensions

| Dimension | Question |
|---|---|
| Accuracy | 內容是否正確？ |
| Completeness | 必要內容是否完整？ |
| Consistency | 是否前後一致？ |
| Scope Alignment | 是否符合 Framework 邊界？ |
| Terminology | 術語是否一致？ |
| Evidence | 重要判斷是否有依據？ |
| Traceability | 來源與變更是否可追蹤？ |
| Readability | 人與 AI 是否容易理解？ |

## 7.3 Content Checks

- 是否與 Philosophy 一致
- 是否與 Blueprint 一致
- 是否與 Core Methodology 一致
- 是否存在 Scope Expansion
- 是否有互相矛盾規則
- 是否有未定義術語
- 是否重複建立 Source of Truth
- 是否混入過時動態資訊
- 是否標示 Known Limitations
- 是否明確揭露假設

## 7.4 Evidence Rules

可接受證據：

- 官方文件
- 可重現測試
- 實際案例
- Benchmark
- Issue Record
- ADR
- 使用者回饋
- 研究資料

不可接受：

- 個人偏好
- 無來源推測
- 單一成功案例
- 未驗證網路內容
- 行銷宣稱

---

# 8. Level 3 — Functional Validation

## 8.1 Objective

確認 Artifact 實際可執行或可使用。

## 8.2 Skill Validation

檢查：

- Input 是否可被接受
- Required Input 缺失時是否停止
- Workflow 是否完整
- Decision Rules 是否正確
- Output 是否符合 Schema
- Error Handling 是否正常
- Human Review 是否正確觸發

## 8.3 Template Validation

檢查：

- Template 可否 Render
- Required Placeholder 是否能完整填入
- 是否有殘留 Placeholder
- 輸出格式是否正確
- 是否符合 Source Standard

## 8.4 Config Validation

檢查：

- YAML / JSON 是否可解析
- Required Settings 是否存在
- Default Value 是否安全
- 動態設定是否可更新
- Config 是否與 Schema 一致

## 8.5 Schema Validation

檢查：

- Valid Input 是否通過
- Invalid Input 是否失敗
- Required Field 是否正確
- Additional Properties 是否合理
- Error Message 是否明確

---

# 9. Level 4 — Scenario Validation

## 9.1 Objective

以實際情境驗證 Framework 是否可用。

每個 Stable Artifact 至少需要以下案例：

1. Standard Case
2. Complex Case
3. Boundary Case
4. Failure Case
5. Incomplete Input Case
6. High-Risk Case（如適用）
7. Cross-Framework Case（如適用）

## 9.2 Scenario Test Structure

```yaml
scenario:
  id:
  name:
  purpose:
  preconditions:
  input:
  expected_process:
  expected_output:
  expected_warnings:
  acceptance_criteria:
```

## 9.3 Scenario Rules

- 測試案例應可重現
- Expected Output 必須明確
- 不得只測試成功案例
- 邊界與失敗案例必須存在
- 測試資料不得含敏感資訊
- 高風險情境必須有人工審核

---

# 10. Level 5 — Regression Validation

## 10.1 Objective

確保新版本未破壞既有能力。

## 10.2 Regression Scope

至少包含：

- 舊 Skill
- 舊 Template
- 舊 Config
- 舊 Schema
- 舊 Example
- 舊 Quick Start
- 舊 Adapter
- 舊 Integration

## 10.3 Regression Rules

- Stable Release 必須執行 Regression Test
- Breaking Change 必須明確標示
- 失敗案例應轉為 Regression Test
- Hotfix 必須補充 Regression Test
- Deprecated 功能仍在支援期內時必須持續測試

---

# 11. Level 6 — Security and Safety Validation

## 11.1 Objective

確認 Artifact 不會引入不可接受的資料、權限、執行或治理風險。

## 11.2 Security Checks

- 是否包含 API Key、Token、密碼
- 是否包含個資或敏感資料
- 是否要求過高權限
- 是否執行不可逆操作
- 是否有未授權外部呼叫
- 是否有危險預設值
- 是否有 Prompt Injection 風險
- 是否有資料外洩風險
- 是否有日誌過度記錄
- 是否有未驗證第三方依賴

## 11.3 Safety Controls

必要控制包括：

- 最小權限
- 資料最小化
- 人工確認
- 可回復性
- 操作日誌
- 失敗停止
- 敏感資訊遮罩
- 安全預設值

## 11.4 Security Result

```yaml
security_validation:
  status:
  findings:
  severity:
  affected_components:
  mitigation:
  release_blocking:
```

---

# 12. Level 7 — Human Review

## 12.1 Objective

對高風險、策略性或重大影響內容進行獨立人工審核。

## 12.2 Mandatory Human Review

以下情況必須人工審核：

- 醫療、法律、財務重大決策
- 企業正式發布
- 生產環境部署
- 權限變更
- 不可逆操作
- 高金額決策
- 敏感資料處理
- 重大策略建議
- 安全政策變更
- Breaking Change

## 12.3 Reviewer Independence

重大 Artifact 應由非原始作者審查。

同一 AI 或同一生成流程的自我檢查，不應被視為完整獨立 Review。

---

# 13. Acceptance Criteria

Acceptance Criteria 必須：

- 明確
- 可衡量
- 可重現
- 與 Scope 一致
- 與風險相符

## 13.1 Example

```yaml
acceptance_criteria:
  structural_errors: 0
  critical_errors: 0
  scenario_pass_rate: ">= 90%"
  regression_pass_rate: "100%"
  security_blockers: 0
  required_sections_present: true
  human_review_approved: true
```

## 13.2 Prohibited Criteria

避免：

```text
看起來合理
品質不錯
大致完成
應該可以使用
```

---

# 14. Severity Classification

Validation Finding 分為四級：

| Severity | Meaning | Release Impact |
|---|---|---|
| Critical | 造成安全、資料、核心功能或重大錯誤 | 阻止 Release |
| Major | 影響主要功能或相容性 | 必須修正或明確接受 |
| Minor | 非核心問題 | 可延後修正 |
| Informational | 改善建議 | 不阻止 Release |

---

# 15. Validation Decision

Validation 最終狀態：

```text
Pass
Conditional Pass
Fail
```

## 15.1 Pass

條件：

- Critical = 0
- 必要測試通過
- 安全驗證通過
- Human Review 通過（如適用）

## 15.2 Conditional Pass

條件：

- 無 Critical
- 存在可接受 Minor / Major
- Known Limitations 已揭露
- 有明確修正計畫
- Owner 已接受風險

## 15.3 Fail

條件：

- 存在 Critical
- Regression 失敗
- 安全風險未控制
- 核心 Scope 不一致
- 必要 Human Review 未完成

---

# 16. Validation Report

每次正式 Validation 必須建立報告。

標準結構：

```markdown
# Validation Report

## Artifact

## Version

## Scope

## Environment

## Validation Levels

## Test Cases

## Passed Items

## Failed Items

## Findings

## Severity

## Security Results

## Compatibility Results

## Known Limitations

## Required Fixes

## Human Review

## Final Decision

## Release Recommendation
```

---

# 17. Traceability

Validation 必須記錄：

- Artifact Name
- Artifact Version
- Framework Version
- Skill Version
- Config Version
- Schema Version
- Test Case Version
- Test Environment
- Reviewer
- Validation Date
- Final Decision

---

# 18. Validation Evidence Storage

建議位置：

```text
tests/
validation/
reports/
```

例如：

```text
validation/
├── plans/
├── reports/
├── evidence/
└── history/
```

禁止只在對話中保存驗證結果。

---

# 19. Validation Automation

可自動化項目：

- Markdown Lint
- Broken Link Check
- Schema Validation
- YAML Parsing
- Placeholder Check
- File Structure Check
- Version Consistency Check
- Regression Test
- Secret Scan

不可完全自動化：

- 商業合理性
- 高風險決策
- 法律與醫療最終判斷
- 重大架構取捨
- 企業治理風險
- 使用者可理解性

---

# 20. Validation Ownership

| Role | Responsibility |
|---|---|
| Validation Owner | 負責整體驗證 |
| Test Author | 建立測試案例 |
| Reviewer | 獨立審查 |
| Security Reviewer | 安全與風險審查 |
| Framework Owner | 接受或拒絕結果 |
| Maintainer | 修正與版本更新 |

---

# 21. Validation Matrix

| Artifact | Structural | Content | Functional | Scenario | Regression | Security | Human |
|---|---:|---:|---:|---:|---:|---:|---:|
| Core Document | Required | Required | Optional | Recommended | Required | Optional | Recommended |
| Skill | Required | Required | Required | Required | Required | Required | Risk-based |
| Template | Required | Required | Required | Required | Required | Recommended | Optional |
| Config | Required | Required | Required | Required | Required | Required | Optional |
| Schema | Required | Required | Required | Required | Required | Recommended | Optional |
| Example | Required | Required | Required | Required | Optional | Recommended | Optional |
| Release | Required | Required | Required | Required | Required | Required | Required |

---

# 22. Validation Checklist

## Plan

- [ ] Artifact 與 Version 已確認
- [ ] Scope 已定義
- [ ] Acceptance Criteria 已建立
- [ ] Reviewer 已指定
- [ ] Critical Error 已定義

## Structural

- [ ] Files 完整
- [ ] Metadata 完整
- [ ] Naming 正確
- [ ] Links 有效
- [ ] Schema 有效

## Content

- [ ] Accuracy 通過
- [ ] Completeness 通過
- [ ] Consistency 通過
- [ ] Scope Alignment 通過
- [ ] Terminology 一致
- [ ] Known Limitations 已揭露

## Functional

- [ ] Skill 可執行
- [ ] Template 可 Render
- [ ] Config 可載入
- [ ] Schema 可驗證
- [ ] Error Handling 正常

## Scenario

- [ ] Standard Case 通過
- [ ] Complex Case 通過
- [ ] Boundary Case 通過
- [ ] Failure Case 通過
- [ ] Incomplete Input Case 通過

## Regression

- [ ] 舊案例通過
- [ ] 舊 Skill 未被破壞
- [ ] 舊 Config 相容
- [ ] 舊 Schema 相容

## Security

- [ ] 無敏感資訊
- [ ] 權限合理
- [ ] 無危險預設
- [ ] 不可逆操作有確認
- [ ] 安全 Review 完成

## Decision

- [ ] Findings 已分級
- [ ] Required Fixes 已完成
- [ ] Human Review 已完成
- [ ] Final Decision 已記錄
- [ ] Release Recommendation 已完成

---

# 23. Anti-Patterns

## 23.1 Self-Approval

作者自行宣告通過。

修正：

- 使用獨立 Reviewer。

## 23.2 Success-Only Testing

只測試成功案例。

修正：

- 加入 Boundary、Failure 與 Incomplete Input。

## 23.3 Validation After Release

發布後才開始測試。

修正：

- Validation 必須進入 Release Gate。

## 23.4 Undefined Acceptance Criteria

沒有明確通過條件。

修正：

- 先建立可衡量 Criteria。

## 23.5 Hidden Critical Issue

已知重大問題未揭露。

修正：

- Critical Issue 阻止 Release。

## 23.6 Regression Ignored

新版通過，但舊功能失效。

修正：

- Stable Release 必須執行 Regression。

## 23.7 Security as Optional

安全檢查被視為附加項。

修正：

- Skill、Config、Integration 與 Release 必須安全驗證。

---

# 24. Immediate Corrections

本版已建立並修正以下核心要求：

1. **Validation 從單一檢查升級為七層模型**
   - Structural、Content、Functional、Scenario、Regression、Security、Human。

2. **建立 Acceptance Criteria**
   - 不再使用模糊判斷。

3. **建立 Severity Classification**
   - Critical、Major、Minor、Informational。

4. **建立 Validation Decision**
   - Pass、Conditional Pass、Fail。

5. **建立 Validation Matrix**
   - 不同 Artifact 有不同必要驗證層級。

6. **加入 Traceability 與 Evidence Storage**
   - 驗證結果不得只存在對話中。

7. **加入 Automation Boundary**
   - 可自動化與不可完全自動化項目明確分開。

8. **加入 Human Review Independence**
   - 高風險工作不得只依賴自我檢查。

---

# 25. Definition of Done

本文件完成代表：

- 已建立 CSE Validation 的正式標準
- 已建立七層 Validation Model
- 已定義 Validation Lifecycle
- 已建立 Acceptance Criteria 與 Severity
- 已建立 Pass、Conditional Pass、Fail 決策
- 已建立 Validation Report
- 已建立 Traceability 與 Evidence Storage
- 已建立 Automation Boundary
- 已建立 Validation Ownership
- 已建立 Artifact Validation Matrix
- 已建立完整 Validation Checklist
- 可供所有 CSE Framework 執行一致、可追蹤與可審核的驗證

---


# Related Documents

- [Core Methodology](./06-core-methodology.md)
- [Release Standard](./10-release-standard.md)
- [Governance Standard](./12-governance-standard.md)
- [Security Standard](./13-security-standard.md)
- [Glossary](./14-glossary.md)

# Next Document

**12-governance-standard.md**

下一份文件將定義：

- Ownership
- Decision Rights
- Change Control
- ADR
- Review and Approval
- Maintainer Roles
- Contribution Governance
- Conflict Resolution
- Deprecation Governance
- Audit and Traceability
