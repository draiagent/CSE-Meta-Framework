# 14 Glossary

> CSE Meta Framework — Glossary

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Terminology Standard  
Source of Truth: Glossary  
Last Updated: 2026-07-11

Depends On:
- `00-philosophy.md`

Required By:
- `01-framework-lifecycle.md`
- `02-framework-blueprint.md`
- `03-design-principles.md`
- `04-repository-architecture.md`
- `05-document-standards.md`
- `06-core-methodology.md`
- `07-skills-standard.md`
- `08-template-standard.md`
- `09-readme-standard.md`
- `10-release-standard.md`
- `11-validation-standard.md`
- `12-governance-standard.md`
- `13-security-standard.md`
- `15-roadmap.md`

---

# Purpose

本文件定義 **CSE Meta Framework** 與所有子 Framework 共用的正式術語。

目標是避免同一概念被不同名稱混用，確保：

- 文件一致
- Skill 一致
- Prompt 一致
- Template 一致
- AI 可正確解析
- 人類可快速理解
- 跨 Framework 溝通一致

本文件是 CSE 正式術語的 **Single Source of Truth**。

若其他文件中的術語與本文件衝突，應優先修正其他文件。

---

# 1. Terminology Rules

所有 CSE 文件必須遵循以下規則：

1. 同一概念只使用一個正式名稱。
2. 英文術語首次出現時可附繁體中文。
3. 後續使用應保持一致。
4. 不使用未定義縮寫。
5. 不以產品名稱取代能力名稱。
6. 不將 Framework、Skill、Prompt、Tool、Workflow 混用。
7. 新術語進入核心文件前，必須先加入本 Glossary。
8. Deprecated Term 不得出現在新文件中。

---

# 2. Term Status

每個術語可使用以下狀態：

| Status | Meaning |
|---|---|
| Preferred | 正式建議用詞 |
| Allowed | 可使用，但需符合語境 |
| Deprecated | 不建議新文件使用 |
| Prohibited | 禁止使用 |
| Provider-Specific | 僅限特定平台語境 |

---

# 3. Core Framework Terms

## 3.1 CSE

**English:** CSE  
**Chinese:** CSE 系列框架  
**Status:** Preferred

定義：

CSE 是一組以統一哲學、生命週期、設計、文件、Skill、驗證、治理與安全標準建立的 AI Framework 系列。

使用原則：

- 作為整個 Framework 家族的總稱。
- 不應隨意展開成未正式定義的其他名稱。
- 若需正式全名，應由專案 Owner 統一定義。

---

## 3.2 CSE Meta Framework

**Chinese:** CSE 母框架  
**Status:** Preferred

定義：

所有 CSE 子 Framework 的最高層母框架，負責定義 Philosophy、Lifecycle、Blueprint、Standards、Governance 與 Security。

不包含：

- 特定 Prompt 方法論
- 特定 Agent 設計
- 特定模型操作
- 特定供應商功能教學

---

## 3.3 Framework

**Chinese:** 框架  
**Status:** Preferred

定義：

一套可重複、可教學、可驗證、可維護的方法、架構、規則與實作組合，用來持續解決一類重複性問題。

Framework 必須具備：

- Problem
- Scope
- Non-Goals
- Core Methodology
- Architecture
- Validation
- Governance
- Release

禁止混用：

- System
- Tool
- Skill
- Workflow
- Prompt

---

## 3.4 Meta Framework

**Chinese:** 母框架  
**Status:** Preferred

定義：

用來建立、規範與治理其他 Framework 的上層 Framework。

---

## 3.5 Sub-Framework

**Chinese:** 子框架  
**Status:** Allowed

定義：

依循 CSE Meta Framework 所建立的獨立專業 Framework。

範例：

- CSE TaskRouter
- CSE Prompt Engineering
- CSE Context Engineering
- CSE Agent Framework

---

## 3.6 Framework Family

**Chinese:** 框架家族  
**Status:** Preferred

定義：

具有共同哲學、標準、生命週期與治理規則的一組 Framework。

---

# 4. Framework Lifecycle Terms

## 4.1 Framework Lifecycle

**Chinese:** 框架生命週期  
**Status:** Preferred

定義：

Framework 從需求發現到發布與演進的完整流程。

標準階段：

```text
Discover
Define
Design
Develop
Validate
Release
Evolve
```

不得與 Core Methodology 混用。

---

## 4.2 Discover

**Chinese:** 探索  
**Status:** Preferred

定義：

確認問題是否真實、重複、值得建立 Framework 解決的階段。

主要產出：

```text
Problem Brief
```

---

## 4.3 Define

**Chinese:** 定義  
**Status:** Preferred

定義：

確認 Framework 名稱、目的、使用者、範圍、邊界與成功條件的階段。

---

## 4.4 Design

**Chinese:** 設計  
**Status:** Preferred

定義：

建立 Core Methodology、Architecture、Workflow、Input、Output、Validation 與 Governance 的階段。

---

## 4.5 Develop

**Chinese:** 開發  
**Status:** Preferred

定義：

將已確認的設計轉化為 Repository、文件、Skill、Template、Config、Schema、Example 與 Test 的階段。

---

## 4.6 Validate

**Chinese:** 驗證  
**Status:** Preferred

定義：

以明確 Acceptance Criteria 判斷 Artifact 是否正確、完整、可用與安全的階段。

---

## 4.7 Release

**Chinese:** 發布  
**Status:** Preferred

定義：

將通過驗證的版本以可追蹤、可取得、可回復的方式正式對外或對內發布。

---

## 4.8 Evolve

**Chinese:** 演進  
**Status:** Preferred

定義：

根據證據、回饋、Issue、測試與環境變化持續改善 Framework 的階段。

---

## 4.9 Stage Gate

**Chinese:** 階段閘門  
**Status:** Preferred

定義：

每一 Lifecycle Stage 在進入下一階段前必須通過的完成條件。

---

# 5. Framework Definition Terms

## 5.1 Philosophy

**Chinese:** 核心哲學  
**Status:** Preferred

定義：

Framework 最高層的價值、方向與決策基準。

---

## 5.2 Vision

**Chinese:** 願景  
**Status:** Preferred

定義：

Framework 長期希望達成的未來狀態。

---

## 5.3 Mission

**Chinese:** 使命  
**Status:** Preferred

定義：

Framework 為實現 Vision 所採取的核心責任與行動方向。

---

## 5.4 Problem Statement

**Chinese:** 問題敘述  
**Status:** Preferred

定義：

清楚描述目前問題、根因、影響與 Framework 預計解決方式的正式敘述。

---

## 5.5 Scope

**Chinese:** 範圍  
**Status:** Preferred

定義：

Framework 明確負責的能力、任務與內容。

---

## 5.6 Excluded Scope

**Chinese:** 排除範圍  
**Status:** Preferred

定義：

與 Framework 有關，但明確不由此 Repository 負責的內容。

---

## 5.7 Non-Goals

**Chinese:** 非目標  
**Status:** Preferred

定義：

Framework 明確不追求、不處理或不承諾的事項。

Scope 與 Non-Goals 不得混為一談。

---

## 5.8 Boundary

**Chinese:** 邊界  
**Status:** Preferred

定義：

Framework 與其他 Framework、Repository、角色或系統之間的責任分界。

---

## 5.9 Success Criteria

**Chinese:** 成功條件  
**Status:** Preferred

定義：

判斷 Framework 是否達成預期價值的可衡量條件。

---

## 5.10 Definition of Done

**Chinese:** 完成定義  
**Status:** Preferred

定義：

判斷某份文件、Skill、Template、Release 或 Framework 是否可視為完成的具體清單。

---

# 6. Blueprint Terms

## 6.1 Framework Blueprint

**Chinese:** 框架藍圖  
**Status:** Preferred

定義：

將 Framework Definition 轉換為可開發設計的標準文件。

Blueprint 至少包含：

- Identity
- Problem
- Users
- Scope
- Non-Goals
- Value
- Methodology
- Architecture
- Inputs and Outputs
- Validation
- Governance
- Release

---

## 6.2 Identity

**Chinese:** 身份定義  
**Status:** Preferred

定義：

Framework 的正式名稱、Repository 名稱、版本、Owner、Category 與 License 等基本資訊。

---

## 6.3 Value Proposition

**Chinese:** 價值主張  
**Status:** Preferred

定義：

Framework 對使用者、組織、技術與治理所提供的可驗證價值。

---

## 6.4 Target User

**Chinese:** 目標使用者  
**Status:** Preferred

定義：

Framework 主要服務的明確角色或群體。

不建議用詞：

```text
所有人
所有企業
所有 AI 使用者
```

---

## 6.5 Architecture

**Chinese:** 架構  
**Status:** Preferred

定義：

Framework、Repository 或系統中，各組件、責任、介面、依賴與結構關係的整體安排。

Architecture 描述「各部分如何組成與互動」，不等同於 Framework Blueprint、Design 或 Template。

---

## 6.6 Design

**Chinese:** 設計  
**Status:** Preferred

定義：

依據已確認的 Framework Definition、Blueprint 與 Design Principles，形成可實作結構、規則、介面與行為方案的活動與成果。

Design 是將 Blueprint 具體化的過程，不應直接用來取代 Blueprint、Architecture 或 Template。

---

## 6.7 Template

**Chinese:** 範本  
**Status:** Preferred

定義：

依據正式 Standard 或已驗證規則建立，可重複複製、填寫與驗證的標準骨架。

Template 提供起始結構，但不是 Blueprint、Design、Architecture 或 Source of Truth。

---

# 7. Core Methodology Terms

## 7.1 Core Methodology

**Chinese:** 核心方法論  
**Status:** Preferred

定義：

Framework 將輸入轉換為輸出的主要可重複流程。

每個 Framework 只允許一個主要 Core Methodology。

---

## 7.2 Core Execution Methodology

**Chinese:** 核心執行方法  
**Status:** Preferred

定義：

所有 CSE Framework 共用的任務執行流程：

```text
Understand
Analyze
Design
Execute
Validate
Improve
```

不得與 Framework Lifecycle 混用。

---

## 7.3 Understand

**Chinese:** 理解  
**Status:** Preferred

定義：

確認使用者目標、輸出、限制、成功條件與資訊缺口。

---

## 7.4 Analyze

**Chinese:** 分析  
**Status:** Preferred

定義：

拆解問題、判斷複雜度、風險、依賴與假設。

---

## 7.5 Execute

**Chinese:** 執行  
**Status:** Preferred

定義：

依已確認計畫完成任務並產出 Deliverable。

---

## 7.6 Improve

**Chinese:** 改善  
**Status:** Preferred

定義：

根據驗證結果與根因分析，修正 Output、Skill、Template、Config、Test 或 Methodology。

---

## 7.7 Workflow

**Chinese:** 工作流程  
**Status:** Preferred

定義：

一組有順序、輸入、輸出、決策點與完成條件的執行步驟。

Workflow 不等於 Framework。

---

## 7.8 Process

**Chinese:** 流程  
**Status:** Preferred

定義：

為達成特定治理、驗證、發布或營運目標而建立的正式階段與活動順序。

Process 通常描述「必須經過哪些階段」，不等同於單次任務的 Workflow，也不等同於 Framework 的 Core Methodology。

---

## 7.9 Pipeline

**Chinese:** 處理管線  
**Status:** Preferred

定義：

將資料、Artifact、驗證或自動化工作依固定順序串接處理的技術執行鏈。

Pipeline 通常強調系統化、自動化與前後階段輸出傳遞，不應用來取代 Methodology、Process 或 Workflow。

---

## 7.10 Decision Point

**Chinese:** 決策點  
**Status:** Preferred

定義：

流程中根據明確條件選擇不同路徑的位置。

---

## 7.11 Feedback Loop

**Chinese:** 回饋迴路  
**Status:** Preferred

定義：

執行結果回到前一階段，用於修正、重新設計或改善的循環機制。

---

## 7.12 Stop Condition

**Chinese:** 停止條件  
**Status:** Preferred

定義：

當資訊不足、權限不明、安全條件不成立或驗證失敗時，必須停止執行的明確規則。

---

# 8. Repository Terms

## 8.1 Repository

**Chinese:** 程式庫／專案儲存庫  
**Status:** Preferred

定義：

保存 Framework 文件、Skill、Template、Config、Schema、Example、Test 與治理檔案的版本控制空間。

正式文件不建議使用：

```text
Repo
```

---

## 8.2 Root File

**Chinese:** 根目錄文件  
**Status:** Preferred

定義：

位於 Repository 最上層的治理或入口文件。

範例：

- README.md
- LICENSE
- CHANGELOG.md
- CONTRIBUTING.md
- SECURITY.md

---

## 8.3 Repository Profile

**Chinese:** 儲存庫規模設定  
**Status:** Preferred

定義：

依專案複雜度選擇的標準 Repository 結構。

標準類型：

- Small
- Standard
- Enterprise

---

## 8.4 Module

**Chinese:** 模組  
**Status:** Preferred

定義：

具有單一責任、明確介面與可獨立維護能力的 Framework 組件。

---

## 8.5 Component

**Chinese:** 組件  
**Status:** Preferred

定義：

Framework 中可辨識的結構單位。

Module 通常比 Component 更強調獨立責任與介面。

---

## 8.6 Package

**Chinese:** 套件  
**Status:** Preferred

定義：

為特定用途而組合、版本化、發布或交付的一組相關 Module、Component、文件、Config、Schema、Template、Example 或 Test。

Package 強調「可封裝、可版本化與可交付」，但不必然具備 Module 的單一責任與獨立介面。

Package 不等同於 Repository；一個 Repository 可以包含多個 Package，一個 Package 也可以由多個 Module 或 Component 組成。

---

## 8.7 Dependency

**Chinese:** 依賴  
**Status:** Preferred

定義：

一個 Module、Skill 或 Framework 正常運作所需要的其他元件、版本或服務。

---

## 8.8 Adapter

**Chinese:** 適配器  
**Status:** Preferred

定義：

將平台或 Provider 特有行為轉換成 Core Framework 可使用介面的外圍模組。

Adapter 不得修改核心方法論。

---

## 8.9 Integration

**Chinese:** 整合  
**Status:** Preferred

定義：

Framework 與外部系統、工具、平台或服務之間的連接實作。

---

# 9. Skill Terms

## 9.1 Skill

**Chinese:** 技能  
**Status:** Preferred

定義：

具備明確責任、輸入、流程、輸出、驗證與錯誤處理的 AI 可執行單元。

Skill 不等於 Prompt。

---

## 9.2 Skill Package

**Chinese:** 技能套件  
**Status:** Preferred

定義：

包含 `skill.md`、Config、Schema、Examples、Tests 與 Platform Adapters 的完整 Skill 結構。

---

## 9.3 Skill Core

**Chinese:** 技能核心  
**Status:** Preferred

定義：

不依賴特定平台的 Skill Purpose、Scope、Input、Workflow、Output、Validation 與 Error Handling。

---

## 9.4 Router Skill

**Chinese:** 路由技能  
**Status:** Preferred

定義：

根據任務特徵、複雜度、風險或條件選擇處理路徑的 Skill。

---

## 9.5 Execution Skill

**Chinese:** 執行技能  
**Status:** Preferred

定義：

完成特定任務並產出結果的 Skill。

---

## 9.6 Validation Skill

**Chinese:** 驗證技能  
**Status:** Preferred

定義：

依明確規則檢查 Input、Process 或 Output 的 Skill。

---

## 9.7 Review Skill

**Chinese:** 審查技能  
**Status:** Preferred

定義：

從獨立角度檢查邏輯、風險、品質或政策一致性的 Skill。

---

## 9.8 Orchestration Skill

**Chinese:** 編排技能  
**Status:** Preferred

定義：

協調多個 Skill、Tool 或 Workflow 執行順序與資料傳遞的 Skill。

---

# 10. Tool and Agent Terms

## 10.1 Tool

**Chinese:** 工具  
**Status:** Preferred

定義：

由 Skill、Workflow 或 Agent 呼叫，用來取得外部資料、執行操作、存取服務或改變外部狀態的功能介面。

Tool 提供能力，但不負責完整任務方法、流程治理或自主決策。

Tool 不等同於 Skill、Prompt 或 Agent。

---

## 10.2 Agent

**Chinese:** 智能代理  
**Status:** Preferred

定義：

依據目標、狀態、規則與回饋，選擇 Prompt、Skill、Tool 或 Workflow，並持續執行、判斷與調整任務的自主執行角色。

Agent 可以調用多個 Skill 與 Tool，但 Agent 本身不等同於單一 Skill、Tool、Prompt 或 Workflow。

Agent 必須受到 Scope、Permission、Stop Condition、Validation 與 Governance 約束。

---

# 11. Prompt Terms

## 11.1 Prompt

**Chinese:** 提示詞  
**Status:** Preferred

定義：

提供給 AI 模型的任務指令、背景、限制、輸出格式與執行要求。

Prompt 不是 Skill。

---

## 11.2 System Prompt

**Chinese:** 系統提示詞  
**Status:** Preferred

定義：

位於最高指令層級，用來定義 AI 角色、行為邊界與全域規則的 Prompt。

---

## 11.3 Task Prompt

**Chinese:** 任務提示詞  
**Status:** Preferred

定義：

描述單次任務、輸入、限制與輸出要求的 Prompt。

---

## 11.4 Review Prompt

**Chinese:** 審查提示詞  
**Status:** Preferred

定義：

用於驗證、審查、反駁或風險檢查的 Prompt。

---

## 11.5 Prompt Pattern

**Chinese:** 提示詞模式  
**Status:** Preferred

定義：

可重複使用的 Prompt 結構。

---

# 12. Template Terms

## 12.1 Template

**Chinese:** 模板  
**Status:** Preferred

定義：

將已驗證規則轉換為可重複使用的標準骨架。

Template 不得取代 Source Standard。

---

## 12.2 Placeholder

**Chinese:** 佔位符  
**Status:** Preferred

定義：

Template 中等待使用者或系統填入的命名欄位。

標準格式：

```text
{{FRAMEWORK_NAME}}
```

---

## 12.3 Template Registry

**Chinese:** 模板登錄表  
**Status:** Preferred

定義：

集中記錄 Template 名稱、版本、狀態、路徑與 Source Standard 的 Registry。

---

## 12.4 Registry

**Chinese:** 登錄表／登錄機制  
**Status:** Preferred

定義：

集中記錄並管理 Artifact、Template、Skill、Package 或其他受治理項目的名稱、版本、狀態、路徑、Owner 與 Metadata 的正式機制。

Registry 用於索引、追蹤與治理，不保存完整實作內容，也不等同於 Repository、Directory 或一般清單。

---

## 12.5 Render

**Chinese:** 渲染／套用模板  
**Status:** Preferred

定義：

將 Placeholder 替換為實際資料並產生正式 Artifact 的過程。

---

# 13. Configuration and Schema Terms

## 13.1 Configuration

**Chinese:** 配置  
**Status:** Preferred

定義：

可變動但不應寫死於核心方法論的設定。

範例：

- Model Name
- Routing Threshold
- Timeout
- Retry
- Feature Flag

正式定義中不建議用：

```text
Setting
Config
```

但檔名可使用 `config.yaml`。

---

## 13.2 Config

**Chinese:** 配置檔  
**Status:** Allowed

定義：

Configuration 的實際檔案或簡稱。

建議用於檔名或技術語境。

---

## 13.3 Schema

**Chinese:** 結構描述  
**Status:** Preferred

定義：

用來定義資料欄位、型別、必要性與驗證規則的正式契約。

---

## 13.4 Contract

**Chinese:** 契約  
**Status:** Preferred

定義：

對 Input、Output、Interface、行為、責任、限制與錯誤處理所建立的正式約定。

Contract 定義「各方必須遵守什麼」；Schema 定義「資料必須具有什麼結構」。

Contract 可以引用 Schema，但不得與 Schema、Configuration 或 Template 混用。

---

## 13.5 Input Contract

**Chinese:** 輸入契約  
**Status:** Preferred

定義：

對輸入欄位、型別、Required、Default、Constraint 與錯誤行為的正式規範。

---

## 13.6 Output Contract

**Chinese:** 輸出契約  
**Status:** Preferred

定義：

對輸出結構、Required Fields、狀態、警告、限制與錯誤格式的正式規範。

---

## 13.7 Interface

**Chinese:** 介面  
**Status:** Preferred

定義：

兩個 Module、Skill 或 Framework 交換資料與行為的契約。

---

# 14. Output and Artifact Terms

## 14.1 Output

**Chinese:** 輸出  
**Status:** Preferred

定義：

單次 Task、Workflow、Skill 或 Process 執行後直接產生的內容、資料或狀態。

Output 可能尚未完成 Validation、Review 或 Approval，因此不必然構成正式 Deliverable 或 Artifact。

---

## 14.2 Result

**Chinese:** 結果  
**Status:** Preferred

定義：

Task、Workflow、Validation、Verification、Review 或 Audit 執行後所得到的判定、狀態或結論。

Result 可為 Pass、Fail、Warning、Approved、Rejected 或其他明確狀態，不應用來指稱文件、檔案或正式產出物。

---

## 14.3 Artifact

**Chinese:** 正式產出物  
**Status:** Preferred

定義：

具備明確內容、版本、Owner、可追蹤性與可驗證性的正式產出物。

Artifact 可包含文件、Skill、Template、Config、Schema、Report、Release Notes 或其他可保存與治理的成果。

Artifact 不等同於單次 Output 或狀態型 Result。

---

## 14.4 Deliverable

**Chinese:** 交付成果  
**Status:** Preferred

定義：

依 Scope、Milestone、Contract 或 Acceptance Criteria，正式交付給使用者、Owner、Reviewer 或專案的成果。

Deliverable 可由一個或多個 Artifact 組成，且應具備明確交付對象與完成條件。

Deliverable 不等同於所有 Output，也不應直接與單一 Artifact 混用。

---

# 15. Validation Terms

## 15.1 Validation

**Chinese:** 驗證  
**Status:** Preferred

定義：

依預先定義的 Acceptance Criteria，判斷 Artifact 是否符合結構、內容、功能、情境、回歸、安全與人工審查要求。

---

## 15.2 Verification

**Chinese:** 確認／符合性確認  
**Status:** Preferred

定義：

依據既定 Specification、Blueprint、Standard、Schema 或 Contract，確認 Artifact 的實作是否與原先定義一致。

Verification 回答「是否按照規格正確建立」；Validation 回答「是否符合預期需求與 Acceptance Criteria」。

Verification 不得與 Validation、Review 或 Audit 混用。

---

## 15.3 Review

**Chinese:** 審查  
**Status:** Preferred

定義：

由人類或獨立 Reviewer 檢查設計、內容、風險或品質的過程。

Validation 與 Review 不得混用：

- Validation：依規則判定
- Review：由 Reviewer 進行判斷

---

## 15.4 Structural Validation

**Chinese:** 結構驗證  
**Status:** Preferred

定義：

檢查檔案、命名、Metadata、Heading、Link、Schema 與必要章節。

---

## 15.5 Content Validation

**Chinese:** 內容驗證  
**Status:** Preferred

定義：

檢查正確性、完整性、一致性、術語與 Scope Alignment。

---

## 15.6 Functional Validation

**Chinese:** 功能驗證  
**Status:** Preferred

定義：

確認 Skill、Template、Config、Schema 或 Workflow 是否實際可運作。

---

## 15.7 Scenario Validation

**Chinese:** 情境驗證  
**Status:** Preferred

定義：

使用 Standard、Complex、Boundary、Failure 與 Incomplete Input Case 進行實際測試。

---

## 15.8 Regression Validation

**Chinese:** 回歸驗證  
**Status:** Preferred

定義：

確認新版本沒有破壞既有功能與相容性。

---

## 15.9 Security Validation

**Chinese:** 安全驗證  
**Status:** Preferred

定義：

檢查 Secret、權限、資料、工具、Prompt Injection、依賴與不可逆操作風險。

---

## 15.10 Acceptance Criteria

**Chinese:** 驗收標準  
**Status:** Preferred

定義：

判斷 Validation 通過或失敗的明確、可衡量條件。

---

## 15.11 Validation Report

**Chinese:** 驗證報告  
**Status:** Preferred

定義：

記錄 Validation Scope、Test Cases、Findings、Severity、Decision 與 Release Recommendation 的正式 Artifact。

---

## 15.12 Finding

**Chinese:** 驗證發現  
**Status:** Preferred

定義：

Validation 過程中識別出的問題、風險、差異或改善事項。

---

## 15.13 Severity

**Chinese:** 嚴重程度  
**Status:** Preferred

標準分類：

- Critical
- Major
- Minor
- Informational

---

# 16. Governance Terms

## 16.1 Governance

**Chinese:** 治理  
**Status:** Preferred

定義：

用來管理 Ownership、Decision Rights、Change Control、Review、Approval、Release、Deprecation、Conflict 與 Audit 的制度。

---

## 16.2 Owner

**Chinese:** 負責人  
**Status:** Preferred

定義：

對 Framework 或 Artifact 的方向、Scope 與最終決策負責的人或團隊。

---

## 16.3 Maintainer

**Chinese:** 維護者  
**Status:** Preferred

定義：

負責 Repository、Issue、Pull Request、版本、文件與日常維護的人。

---

## 16.4 Architect

**Chinese:** 架構負責人  
**Status:** Preferred

定義：

負責 Core Methodology、Architecture、Interface、Dependency 與 Compatibility 的角色。

---

## 16.5 Reviewer

**Chinese:** 審查者  
**Status:** Preferred

定義：

獨立檢查 Artifact 品質、邏輯、風險或一致性的角色。

---

## 16.6 Decision Rights

**Chinese:** 決策權責  
**Status:** Preferred

定義：

不同類型決策由誰提出、審查、核准與負責的正式規則。

---

## 16.7 RACI

**Chinese:** RACI 權責矩陣  
**Status:** Preferred

定義：

- Responsible
- Accountable
- Consulted
- Informed

---

## 16.8 Change Control

**Chinese:** 變更控制  
**Status:** Preferred

定義：

從 Proposal、Impact Analysis、Review、Validation 到 Approval 與 Release 的完整變更流程。

---

## 16.9 ADR

**English:** Architecture Decision Record  
**Chinese:** 架構決策紀錄  
**Status:** Preferred

定義：

記錄重大架構決策的 Context、Decision、Alternatives、Consequences 與 Status。

---

## 16.10 Audit

**Chinese:** 稽核／審計  
**Status:** Preferred

定義：

檢查決策、版本、權限、變更與 Release 是否有完整紀錄並符合治理規則。

---

# 17. Release Terms

## 17.1 Release

**Chinese:** 發布  
**Status:** Preferred

定義：

將通過驗證的 Artifact 以正式版本、Tag、Release Notes 與可追蹤紀錄提供使用。

---

## 17.2 Release Candidate

**Chinese:** 候選發布版  
**Status:** Preferred

定義：

已功能凍結並通過主要驗證，等待最終核准的版本。

格式：

```text
1.0.0-rc.1
```

---

## 17.3 Stable

**Chinese:** 穩定版  
**Status:** Preferred

定義：

已通過必要驗證並正式支援的版本狀態。

---

## 17.4 Semantic Versioning

**Chinese:** 語意化版本  
**Status:** Preferred

定義：

使用：

```text
MAJOR.MINOR.PATCH
```

管理版本影響。

---

## 17.5 Breaking Change

**Chinese:** 破壞性變更  
**Status:** Preferred

定義：

會造成既有使用方式、Contract、Skill、Schema 或相容性失效的變更。

---

## 17.6 Migration Guide

**Chinese:** 遷移指南  
**Status:** Preferred

定義：

說明從舊版本轉移到新版本的步驟、驗證、風險與 Rollback。

---

## 17.7 Rollback

**Chinese:** 回復／回滾  
**Status:** Preferred

定義：

在 Release 失敗時恢復到前一個穩定狀態的流程。

---

## 17.8 Deprecation

**Chinese:** 淘汰標示  
**Status:** Preferred

定義：

宣告某項功能仍暫時存在，但不建議新使用，並將在未來版本移除。

---

## 17.9 Archive

**Chinese:** 封存  
**Status:** Preferred

定義：

停止主動維護，但保留歷史內容與紀錄。

---

# 18. Security Terms

## 18.1 Security by Design

**Chinese:** 安全內建設計  
**Status:** Preferred

定義：

在 Blueprint 與 Design 階段就納入安全，而不是發布前才補做。

---

## 18.2 Least Privilege

**Chinese:** 最小權限  
**Status:** Preferred

定義：

只授予完成任務所需的最小權限。

---

## 18.3 Data Minimization

**Chinese:** 資料最小化  
**Status:** Preferred

定義：

只收集、傳遞與保存任務真正需要的資料。

---

## 18.4 Secure Default

**Chinese:** 安全預設值  
**Status:** Preferred

定義：

預設禁止高風險操作，只有明確授權後才啟用。

---

## 18.5 Fail Closed

**Chinese:** 安全失敗  
**Status:** Preferred

定義：

當安全條件不明或驗證失敗時停止執行，而不是繼續猜測。

---

## 18.6 Secret

**Chinese:** 機密憑證  
**Status:** Preferred

定義：

API Key、Token、Password、Private Key 或其他授權憑證。

---

## 18.7 Prompt Injection

**Chinese:** 提示詞注入  
**Status:** Preferred

定義：

外部內容試圖改變原始指令層級、洩漏資訊或誘導未授權操作的攻擊方式。

---

## 18.8 Tool Allowlist

**Chinese:** 工具允許清單  
**Status:** Preferred

定義：

明確列出可使用工具與其允許權限的安全控制。

---

## 18.9 Irreversible Action

**Chinese:** 不可逆操作  
**Status:** Preferred

定義：

無法簡單回復、可能造成正式資料、權限、發布或系統狀態重大改變的操作。

---

## 18.10 Incident Response

**Chinese:** 安全事件處理  
**Status:** Preferred

定義：

從 Detect、Contain、Assess、Mitigate、Recover 到 Review 的事件應變流程。

---

# 19. Data Classification Terms

## 19.1 Public

**Chinese:** 公開資料  
**Status:** Preferred

定義：

可公開傳播、不具明顯敏感性的資料。

---

## 19.2 Internal

**Chinese:** 內部資料  
**Status:** Preferred

定義：

僅供組織內部使用，不應任意公開的資料。

---

## 19.3 Confidential

**Chinese:** 機密資料  
**Status:** Preferred

定義：

包含商業、客戶、策略或未公開資訊，需要嚴格存取控制的資料。

---

## 19.4 Restricted

**Chinese:** 高度限制資料  
**Status:** Preferred

定義：

個資、憑證、醫療、法律、財務或其他高敏感資料。

---

# 20. Documentation Terms

## 20.1 Documentation

**Chinese:** 文件體系  
**Status:** Preferred

定義：

描述 Framework 哲學、方法論、架構、規則、案例與治理的正式文件集合。

---

## 20.2 Source of Truth

**Chinese:** 單一真實來源  
**Status:** Preferred

定義：

某項核心規則唯一且正式的主要來源文件。

---

## 20.3 Cross-Reference

**Chinese:** 交叉引用  
**Status:** Preferred

定義：

透過相對連結引用其他文件，而不是複製相同內容。

---

## 20.4 Metadata

**Chinese:** 文件中繼資料  
**Status:** Preferred

定義：

描述 Version、Status、Owner、Last Updated 等文件身份資訊。

---

## 20.5 README

**Chinese:** 專案首頁  
**Status:** Preferred

定義：

Repository 的入口文件，用於 Overview、Quick Start、Navigation、Version 與 License。

README 不等於完整文件系統。

---

## 20.6 CHANGELOG

**Chinese:** 變更紀錄  
**Status:** Preferred

定義：

依版本記錄 Added、Changed、Deprecated、Removed、Fixed 與 Security 的文件。

---

# 21. AI and Model Terms

## 21.1 Model

**Chinese:** 模型  
**Status:** Preferred

定義：

實際執行生成、推理、分類或工具呼叫的 AI 模型。

Model 不等於 Platform、Tool 或 Workflow。

---

## 21.2 Provider

**Chinese:** 模型供應商  
**Status:** Preferred

定義：

提供 AI 模型、API 或平台服務的組織。

---

## 21.3 Platform

**Chinese:** 平台  
**Status:** Preferred

定義：

整合模型、工具、介面、工作區或代理功能的產品環境。

---

## 21.4 Tool

**Chinese:** 工具  
**Status:** Preferred

定義：

AI 可呼叫以取得資料、執行操作或產生 Artifact 的外部能力。

Tool 不等於 Skill。

---

## 21.5 Agent

**Chinese:** 代理  
**Status:** Preferred

定義：

能根據目標規劃、使用工具、執行多步任務、驗證結果並調整行動的執行單元。

---

## 21.6 Multi-Agent

**Chinese:** 多代理協作  
**Status:** Preferred

定義：

多個 Agent 依角色、責任或流程共同完成任務的協作模式。

---

## 21.7 Model Routing

**Chinese:** 模型路由  
**Status:** Preferred

定義：

根據任務複雜度、風險、成本、延遲與能力需求選擇模型的過程。

---

## 21.8 Task Routing

**Chinese:** 任務路由  
**Status:** Preferred

定義：

將任務分類並指派到適當 Workflow、Skill、Model 或 Human Review 路徑的過程。

---

# 22. Quality Terms

## 22.1 Accuracy

**Chinese:** 正確性  
**Status:** Preferred

定義：

內容、邏輯或結果是否符合事實、規格與預期。

---

## 22.2 Completeness

**Chinese:** 完整性  
**Status:** Preferred

定義：

是否涵蓋所有必要要求與輸出。

---

## 22.3 Consistency

**Chinese:** 一致性  
**Status:** Preferred

定義：

不同文件、Skill、Config、Schema 與版本之間是否沒有衝突。

---

## 22.4 Reusability

**Chinese:** 可重複使用性  
**Status:** Preferred

定義：

Artifact 是否可套用到多個相似情境，而非只適用一次。

---

## 22.5 Maintainability

**Chinese:** 可維護性  
**Status:** Preferred

定義：

Artifact 是否容易理解、修改、測試、版本化與修正。

---

## 22.6 Traceability

**Chinese:** 可追蹤性  
**Status:** Preferred

定義：

是否能追蹤輸入、版本、決策、變更、驗證與責任人。

---

## 22.7 Portability

**Chinese:** 可攜性  
**Status:** Preferred

定義：

Skill 或 Framework 是否能在不同平台、模型或工具環境中重複使用。

---

## 22.8 Compatibility

**Chinese:** 相容性  
**Status:** Preferred

定義：

不同版本、Skill、Config、Schema、Adapter 或 Framework 是否能正常協作。

---

# 23. Recommended and Prohibited Usage

| Preferred | Avoid | Reason |
|---|---|---|
| Framework | System（泛稱） | 避免與完整系統混淆 |
| Skill | Tool / Plugin | Skill 是可執行方法，不一定是工具 |
| Prompt | Command / 咒語 | 保持專業術語 |
| Validation | Check | Validation 有正式標準 |
| Review | Validation | Review 是人工或獨立審查 |
| Repository | Repo | 正式文件保持一致 |
| Configuration | Setting | 正式定義使用一致名稱 |
| Provider | Platform | 供應商與平台不同 |
| Blueprint | Plan | Blueprint 是正式設計藍圖 |
| Lifecycle | Workflow | Lifecycle 與任務工作流不同 |

---

# 24. Deprecated Terms

以下用詞不建議在新文件中使用：

| Deprecated Term | Replace With |
|---|---|
| AI Tool Framework | 依實際責任改為 Framework、Tool 或 Skill |
| Super Skill | Skill |
| Smart Prompt | Prompt Pattern |
| Final Version | Stable Release |
| Latest Model | Model Registry 中的 Current Model |
| Best Model | Appropriate Model |
| One-Click AI | 明確描述 Workflow 或 Automation |
| Repo | Repository |
| Check | Validation 或 Review |
| Plugin | Adapter、Integration 或 Skill |

---

# 25. Abbreviation Rules

縮寫首次出現時必須展開。

範例：

```text
Architecture Decision Record (ADR)
```

後續可使用：

```text
ADR
```

禁止：

- 未定義縮寫
- 同一縮寫代表多個概念
- 自創但未加入 Glossary 的縮寫
- 以縮寫取代可理解名稱

---

# 26. Bilingual Usage

中英文文件應保持概念一致。

建議格式：

```text
Framework Lifecycle（框架生命週期）
```

或：

```text
框架生命週期（Framework Lifecycle）
```

同一文件內應固定一種順序。

正式英文術語不得被隨意翻譯成多種中文名稱。

---

# 27. New Term Proposal

新增術語時，應提供：

```yaml
term:
english:
chinese:
status:
definition:
scope:
related_terms:
avoid:
example:
owner:
```

新增流程：

```text
Propose
  ↓
Review
  ↓
Check Conflict
  ↓
Approve
  ↓
Add to Glossary
  ↓
Update Related Documents
```

---

# 28. Glossary Governance

本 Glossary 的重大變更需：

- 建立 Issue
- 說明新增或修改原因
- 檢查既有文件影響
- 由 Documentation Reviewer 審查
- 更新 CHANGELOG
- 更新受影響文件

若修改正式術語，需評估是否為 Breaking Change。

---

# 29. Glossary Validation Checklist

## Definition

- [ ] 術語只有一個主要定義
- [ ] 中文與英文一致
- [ ] Scope 清楚
- [ ] Related Terms 已區分

## Consistency

- [ ] 未與既有術語重疊
- [ ] 未使用未定義縮寫
- [ ] 未出現同義詞混用
- [ ] Deprecated Term 已標示

## Documentation

- [ ] 受影響文件已更新
- [ ] Cross-Reference 已建立
- [ ] CHANGELOG 已更新
- [ ] Version 已確認

---

# 30. Anti-Patterns

## 30.1 Synonym Drift

同一概念在不同文件使用不同名稱。

修正：

- 回到 Glossary 統一正式名稱。

## 30.2 Product Name as Methodology

以某平台產品名稱取代能力或方法。

修正：

- 核心文件使用能力名稱，產品名稱放在 Adapter 或 Reference。

## 30.3 Undefined Acronym

使用者無法理解縮寫。

修正：

- 首次展開並加入 Glossary。

## 30.4 Translation Drift

中英文版本定義不同。

修正：

- 指定主要語言與正式對照。

## 30.5 Glossary as Encyclopedia

收錄與 Framework 無關的一般 AI 名詞。

修正：

- 只保留影響 CSE 設計、執行、治理與安全的術語。

---

# 31. Immediate Corrections

本版已建立並修正以下核心要求：

1. **Glossary 成為術語的 Single Source of Truth**
   - 其他文件不得自行重新定義正式術語。

2. **明確區分 Framework、Lifecycle、Core Methodology 與 Workflow**
   - 避免前面文件最容易發生的概念混用。

3. **明確區分 Skill、Prompt、Tool、Agent 與 Adapter**
   - 避免平台用語影響核心架構。

4. **加入 Preferred、Allowed、Deprecated、Prohibited 狀態**
   - 便於未來管理詞彙演進。

5. **加入正式中英文對照**
   - 支援雙語文件與跨平台溝通。

6. **加入 Deprecated Terms 與替代詞**
   - 防止舊文件持續使用模糊名稱。

7. **加入 New Term Proposal 與 Glossary Governance**
   - 新術語不得未經審查直接進入核心文件。

---

# 32. Definition of Done

本文件完成代表：

- 已建立 CSE 核心術語的正式定義
- 已建立中英文對照
- 已定義 Preferred、Allowed、Deprecated 與 Prohibited 狀態
- 已區分 Framework、Lifecycle、Methodology、Workflow、Skill、Prompt、Tool、Agent 與 Adapter
- 已建立 Validation、Governance、Release 與 Security 術語
- 已建立 Recommended、Deprecated 與 Prohibited Usage
- 已建立 Abbreviation、Bilingual 與 New Term Proposal 規則
- 已建立 Glossary Governance 與 Validation Checklist
- 可作為所有 CSE Framework 文件的術語 Single Source of Truth

---

# Related Documents

- [Philosophy](./00-philosophy.md)
- [Document Standards](./05-document-standards.md)
- [Core Methodology](./06-core-methodology.md)
- [Governance Standard](./12-governance-standard.md)
- [Security Standard](./13-security-standard.md)

---

# Next Document

**15-roadmap.md**

下一份文件將定義：

- CSE Meta Framework 的 Current、Next、Later
- v1.0 發布範圍
- 後續 Template、Example、Test 與 Automation 建設順序
- Out of Scope
- Milestones
