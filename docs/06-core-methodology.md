# 06 Core Methodology

> CSE Meta Framework — Core Execution Methodology

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Core Execution Standard  
Source of Truth: Core Execution Methodology  
Last Updated: 2026-07-11

Depends On:
- `00-philosophy.md`
- `01-framework-lifecycle.md`
- `02-framework-blueprint.md`
- `11-validation-standard.md`
- `13-security-standard.md`
- `14-glossary.md`

Required By:
- `07-skills-standard.md`
- `11-validation-standard.md`

---

# Purpose

本文件定義所有 CSE Framework 共用的核心執行方法論。

此方法論處理的是：

> 一個具體任務如何被理解、分析、設計、執行、驗證與改善。

它不同於 `01-framework-lifecycle.md`。

- `Framework Lifecycle`：定義一個 Framework 如何誕生、發布與演進。
- `Core Methodology`：定義一個任務如何被處理與完成。

兩者不得混用。

---

# 1. Methodology Overview

所有 CSE Framework 的任務執行流程統一為：

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

六個階段的目的如下：

| Stage | Core Question | Primary Output |
|---|---|---|
| Understand | 使用者真正要解決什麼？ | Requirement Definition |
| Analyze | 問題的本質、限制與風險是什麼？ | Analysis |
| Design | 應採用什麼方案與流程？ | Execution Plan |
| Execute | 如何依計畫完成任務？ | Deliverable |
| Validate | 結果是否正確、完整、可用？ | Validation Result |
| Improve | 如何修正並避免問題重複發生？ | Improvement Record |

---

# 2. Governing Rules

所有 CSE Framework 執行任務時，必須遵循以下規則：

1. **Understand Before Execute**
   - 未確認需求，不得直接產出最終結果。

2. **Analyze Before Design**
   - 未理解限制、風險與依賴，不得直接選擇方案。

3. **Design Before Execute**
   - 複雜任務必須先建立執行計畫。

4. **Validate Before Release**
   - 未驗證的輸出不得視為完成。

5. **Improve Through Evidence**
   - 改善應依據錯誤、測試與回饋，而非直覺。

6. **Stop When Critical Information Is Missing**
   - 缺少會影響安全、正確性或決策品質的資訊時，必須停止並要求補充。

7. **Use the Smallest Sufficient Process**
   - 簡單任務可縮短流程，但不得省略必要驗證。

---

# 3. Stage 1 — Understand

## 3.1 Objective

確認任務真正目標，而不是只接受表面描述。

Understand 階段需要將模糊需求轉換成可執行的 Requirement。

## 3.2 Required Questions

至少確認：

- 目標是什麼？
- 預期輸出是什麼？
- 使用者是誰？
- 成功標準是什麼？
- 有哪些限制？
- 有哪些已知資訊？
- 缺少哪些資訊？
- 是否涉及高風險情境？
- 是否需要使用工具、文件或外部資料？

## 3.3 Input Types

可能輸入包括：

- User Request
- Context
- Files
- Data
- Constraints
- Existing Framework
- Prior Decisions
- External References

## 3.4 Required Output

```text
Requirement Definition
```

建議格式：

```yaml
goal:
primary_output:
target_user:
constraints:
success_criteria:
known_information:
missing_information:
risk_level:
required_tools:
```

## 3.5 Clarification Rules

需要立即澄清的情況：

- 目標互相衝突
- 輸出格式不明
- 重要限制缺失
- 涉及高風險決策
- 要修改正式系統
- 要代表使用者對外發布
- 要執行不可逆操作

不需澄清的情況：

- 可做低風險合理假設
- 使用者已提供足夠上下文
- 只需格式轉換或單純摘要

合理假設必須明確標示。

## 3.6 Stage Gate

- [ ] 目標已明確
- [ ] 輸出已明確
- [ ] 成功標準已明確
- [ ] 限制已確認
- [ ] 關鍵缺口已處理
- [ ] 風險等級已判斷

---

# 4. Stage 2 — Analyze

## 4.1 Objective

拆解問題並判斷應採用的處理方式。

Analyze 階段不產生最終成果，而是建立足夠的問題理解。

## 4.2 Analysis Dimensions

至少評估：

| Dimension | Question |
|---|---|
| Complexity | 任務複雜度多高？ |
| Scope | 涉及多少模組、文件或角色？ |
| Dependencies | 有哪些相依條件？ |
| Risk | 錯誤會造成什麼影響？ |
| Evidence | 需要哪些資料或來源？ |
| Tools | 需要哪些工具或能力？ |
| Time Horizon | 是單次任務還是多階段任務？ |
| Reversibility | 結果是否可回復？ |

## 4.3 Problem Decomposition

複雜任務應拆分為：

```text
Main Problem
├── Subproblem A
├── Subproblem B
├── Subproblem C
└── Validation Problem
```

每個子問題需定義：

- Input
- Output
- Owner
- Dependency
- Risk
- Completion Condition

## 4.4 Assumption Management

所有重要假設必須記錄：

```yaml
assumptions:
  - statement:
    reason:
    risk_if_wrong:
    validation_method:
```

禁止隱藏假設。

## 4.5 Analysis Output

```text
Analysis
```

至少包含：

- Problem Definition
- Complexity
- Constraints
- Dependencies
- Risks
- Assumptions
- Required Evidence
- Recommended Processing Level

## 4.6 Stage Gate

- [ ] 問題已拆解
- [ ] 複雜度已判斷
- [ ] 風險已辨識
- [ ] 相依關係已記錄
- [ ] 假設已標示
- [ ] 所需工具與證據已確認

---

# 5. Stage 3 — Design

## 5.1 Objective

根據 Requirement 與 Analysis 建立可執行方案。

Design 階段必須回答：

- 採用哪一種方法？
- 執行順序是什麼？
- 使用哪些工具？
- 哪些步驟需要人工審核？
- 如何驗證結果？
- 失敗時如何處理？

## 5.2 Design Components

一個完整 Execution Plan 至少包含：

1. Approach
2. Steps
3. Inputs
4. Outputs
5. Tools
6. Decision Points
7. Validation Rules
8. Human Review Points
9. Failure Handling
10. Task Completion Criteria

## 5.3 Option Design

中高複雜度任務應比較至少兩種方案。

建議格式：

| Option | Benefits | Risks | Cost | Fit |
|---|---|---|---|---|
| A |  |  |  |  |
| B |  |  |  |  |

若只有一種合理方案，需說明原因。

## 5.4 Decision Logic

決策順序：

```text
Requirement Fit
   ↓
Safety
   ↓
Correctness
   ↓
Maintainability
   ↓
Cost
   ↓
Speed
```

不得只以速度或模型能力決定方案。

## 5.5 Design Output

```text
Execution Plan
```

建議格式：

```yaml
approach:
steps:
  - id:
    action:
    input:
    output:
    tool:
    validation:
decision_points:
human_review:
failure_handling:
completion_criteria:
```

## 5.6 Stage Gate

- [ ] 方案與需求一致
- [ ] 步驟可執行
- [ ] 工具已確認
- [ ] 驗證規則已定義
- [ ] 失敗處理已定義
- [ ] Task Completion Criteria 已明確

---

# 6. Stage 4 — Execute

## 6.1 Objective

依 Execution Plan 完成任務。

Execute 階段不應重新改變 Scope 或核心方向。

若執行中發現設計錯誤，應返回 Analyze 或 Design。

## 6.2 Execution Rules

- 依計畫順序執行
- 記錄重要決策
- 不跳過必要步驟
- 不擴大未授權範圍
- 不自行修改成功標準
- 不隱藏錯誤
- 不將未驗證結果標示為完成

## 6.3 Execution Modes

### Direct Execution

適用：

- Quick Task
- 低風險
- 單一輸出
- 不需多工具

### Staged Execution

適用：

- Standard Task
- 多個步驟
- 有中間成果
- 需要局部驗證

### Orchestrated Execution

適用：

- Deep / Strategic Task
- 多工具
- 多文件
- 多 Agent
- 多角色協作
- 高風險

## 6.4 Execution Record

重要任務應記錄：

```yaml
execution:
  version:
  started_at:
  steps_completed:
  tools_used:
  deviations:
  warnings:
  intermediate_outputs:
```

## 6.5 Deviation Rules

若執行偏離原計畫：

1. 記錄偏離原因。
2. 評估風險。
3. 確認是否仍符合 Scope。
4. 必要時回到 Design。
5. 更新 Execution Plan。
6. 不得靜默變更。

## 6.6 Stage Gate

- [ ] 所有必要步驟已完成
- [ ] 未授權 Scope 未擴張
- [ ] 中間錯誤已記錄
- [ ] Deliverable 已產生
- [ ] 可進入 Validation

---

# 7. Stage 5 — Validate

## 7.1 Objective

確認 Deliverable 是否符合 Requirement、Execution Plan 與最低品質要求。

Core Methodology 只定義任務執行中的 Validate Stage，不重複定義完整 Validation Model。

## 7.2 Minimum Validation Questions

- 是否符合 Requirement？
- 是否完整？
- 是否前後一致？
- 是否符合限制？
- 是否可安全使用？
- 是否需人工審核？

## 7.3 Required Output

```yaml
validation:
  status: pass | conditional_pass | fail
  warnings:
  limitations:
  required_fixes:
```

## 7.4 Decision

```text
Pass              → Deliver
Conditional Pass  → Deliver with Warnings
Fail              → Return to Analyze, Design, or Execute
```

完整 Validation Levels、Acceptance Criteria、Severity 與 Human Review 規則，統一由 [Validation Standard](./11-validation-standard.md) 定義。

# 8. Stage 6 — Improve

## 8.1 Objective

根據 Validation、錯誤與回饋改善結果與 Framework。

Improve 不只是修正一次輸出，也應改善未來執行品質。

## 8.2 Improvement Levels

### Level 1 — Output Fix

修正單次 Deliverable。

### Level 2 — Prompt or Skill Fix

修正執行方法。

### Level 3 — Template or Config Fix

修正可重複元件。

### Level 4 — Methodology Fix

修正核心流程。

### Level 5 — Governance Fix

修正審查、版本或責任機制。

## 8.3 Root Cause Analysis

問題修正前應判斷根因：

```text
Symptom
   ↓
Immediate Cause
   ↓
Process Cause
   ↓
System Cause
```

常見根因：

- Requirement 不完整
- Analysis 不足
- Design 錯誤
- Tool 使用錯誤
- Validation 缺失
- Config 過時
- Skill 邊界不清
- Scope 擴張

## 8.4 Improvement Record

```yaml
improvement:
  issue:
  root_cause:
  immediate_fix:
  permanent_fix:
  affected_components:
  test_added:
  version_impact:
```

## 8.5 Improvement Rule

每次發現可重複問題時，至少評估是否需要更新：

- Core Rule
- Skill
- Prompt
- Template
- Config
- Example
- Test
- Documentation
- CHANGELOG

## 8.6 Stage Gate

- [ ] Root Cause 已確認
- [ ] Immediate Fix 已完成
- [ ] Permanent Fix 已評估
- [ ] 必要測試已新增
- [ ] 變更已記錄
- [ ] 版本影響已確認

---

# 9. Task Complexity Adaptation

六階段方法論可依任務複雜度調整深度，但不能失去核心控制點。

| Task Level | Understand | Analyze | Design | Execute | Validate | Improve |
|---|---|---|---|---|---|---|
| Quick | 簡化 | 簡化 | 可內嵌 | 直接 | 必須 | 視需要 |
| Standard | 完整 | 基本 | 基本 | 分階段 | 必須 | 視需要 |
| Deep | 完整 | 深入 | 完整 | 分階段 | 多層 | 必須 |
| Strategic | 完整 | 深入 | 多方案 | 編排式 | 多層＋人工 | 必須 |

固定規則：

```text
流程深度可以調整，
Validation 不得省略。
```

---

# 10. Framework Mapping

所有子 Framework 都必須映射到六階段方法論。

| Framework | Primary Contribution |
|---|---|
| TaskRouter | Analyze |
| Prompt Engineering | Design / Execute |
| Context Engineering | Understand / Analyze |
| Workflow Engineering | Design / Execute |
| Agent Framework | Execute |
| MCP Framework | Execute / Integration |
| Validation Framework | Validate |
| Governance Framework | Validate / Improve |

子 Framework 可強化特定階段，但不得改寫整體順序。

---

# 11. Input and Output Contract

## 11.1 Universal Input

```yaml
task:
context:
constraints:
success_criteria:
risk_level:
available_tools:
```

## 11.2 Universal Output

```yaml
status:
summary:
result:
validation:
warnings:
limitations:
next_actions:
```

## 11.3 Error Output

```yaml
status: failed
error_type:
failed_stage:
reason:
missing_information:
recommended_action:
retry_allowed:
```

---

# 12. Stop Conditions

遇到以下情況，流程必須停止：

- 缺少高風險決策所需資訊
- 使用者要求超出授權範圍
- 工具不可用
- 來源無法驗證
- Scope 衝突
- 需求互相矛盾
- 無法安全執行
- 不可逆操作未獲確認
- Validation 出現 Critical Error

停止時必須輸出：

- 停止原因
- 停止階段
- 缺少資訊
- 建議下一步

---

# 13. Human Review Rules

以下情況必須人工審核：

- 醫療、法律、財務重大決策
- 企業正式對外發布
- 生產系統部署
- 不可逆操作
- 高金額決策
- 高敏感資料
- 重大策略建議
- 權限變更
- 安全設定變更

人工審核不得被模型自我驗證取代。

---

# 14. Traceability Requirements

重要任務至少記錄：

- Requirement Version
- Methodology Version
- Skill Version
- Config Version
- Model / Provider
- Tools Used
- Validation Result
- Reviewer
- Final Status

目的：

- 可重現
- 可追蹤
- 可審查
- 可回復

---

# 15. Anti-Patterns

## 15.1 Execute First

未確認需求就直接產出。

修正：

- 返回 Understand。

## 15.2 Hidden Analysis

重要假設與限制未記錄。

修正：

- 在 Analysis 中明確標示。

## 15.3 Plan Without Validation

有計畫但沒有驗證條件。

修正：

- 在 Design 階段先定義 Validation。

## 15.4 Silent Deviation

執行中改變方向但未記錄。

修正：

- 建立 Deviation Record。

## 15.5 Self-Approval

生成者自行宣告結果通過。

修正：

- 使用獨立 Validation 或人工 Review。

## 15.6 Fix Only the Output

只修正單次錯誤，不修正根因。

修正：

- 進入 Improve，更新 Skill、Template 或 Test。

## 15.7 Over-Processing

簡單任務使用完整策略流程。

修正：

- 使用最小充分流程。

---

# 16. Core Methodology Checklist

## Understand

- [ ] Goal 明確
- [ ] Output 明確
- [ ] Constraints 明確
- [ ] Success Criteria 明確
- [ ] Missing Information 已處理

## Analyze

- [ ] Complexity 已判斷
- [ ] Risks 已辨識
- [ ] Dependencies 已記錄
- [ ] Assumptions 已標示

## Design

- [ ] Approach 已選擇
- [ ] Steps 已定義
- [ ] Tools 已確認
- [ ] Validation 已設計
- [ ] Failure Handling 已定義

## Execute

- [ ] 按 Plan 執行
- [ ] Deviations 已記錄
- [ ] Scope 未擴張
- [ ] Deliverable 已完成

## Validate

- [ ] Accuracy 通過
- [ ] Completeness 通過
- [ ] Consistency 通過
- [ ] Safety 通過
- [ ] Limitations 已揭露

## Improve

- [ ] Root Cause 已確認
- [ ] Fix 已完成
- [ ] Test 已補充
- [ ] 變更已記錄

---

# 17. Immediate Corrections

本版已修正舊版 `04-core-methodology.md` 的主要問題：

1. **明確區分 Core Methodology 與 Framework Lifecycle**
   - Lifecycle 處理 Framework 的建立與發布。
   - Core Methodology 處理任務執行。

2. **為每個階段加入 Input、Output 與 Stage Gate**
   - 避免流程只有概念，無法執行。

3. **加入 Stop Conditions**
   - 高風險或資訊不足時不得硬做。

4. **加入 Human Review Rules**
   - 高風險任務不得只依賴模型自我驗證。

5. **加入 Traceability Requirements**
   - 重要任務必須記錄版本、工具與驗證結果。

6. **加入 Task Complexity Adaptation**
   - 流程深度可調整，但 Validation 不可省略。

7. **加入 Universal Input / Output Contract**
   - 讓不同 Framework 能共用一致介面。

8. **加入 Root Cause Improvement**
   - 不只修正結果，也修正流程與系統。

---

# 18. Definition of Done

本文件完成代表：

- 已建立所有 CSE Framework 共用的六階段執行方法
- 已明確區分 Core Methodology 與 Framework Lifecycle
- 已定義每個階段的目標、輸入、輸出與 Gate
- 已建立 Stop Conditions 與 Human Review 規則
- 已建立 Validation 與 Improvement 機制
- 已建立 Universal Input / Output Contract
- 已建立 Task Complexity Adaptation
- 已建立 Traceability Requirements
- 可供所有 CSE Framework 直接映射與擴充

---


# Related Documents

- [Framework Lifecycle](./01-framework-lifecycle.md)
- [Framework Blueprint](./02-framework-blueprint.md)
- [Skills Standard](./07-skills-standard.md)
- [Validation Standard](./11-validation-standard.md)
- [Security Standard](./13-security-standard.md)
- [Glossary](./14-glossary.md)

# Next Document

**07-skills-standard.md**

下一份文件將重新定義：

- Skill Definition
- Skill Package Structure
- Front Matter
- Inputs and Outputs
- Workflow
- Validation
- Portability
- Versioning
- Testing
- Platform Adapters
