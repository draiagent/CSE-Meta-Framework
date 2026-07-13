# 13 Security Standard

> CSE Meta Framework — Security Standard

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Security Standard  
Source of Truth: Security Standard  
Last Updated: 2026-07-11

Depends On:
- `12-governance-standard.md`
- `14-glossary.md`

Required By:
- `06-core-methodology.md`
- `07-skills-standard.md`
- `10-release-standard.md`
- `11-validation-standard.md`
- `15-roadmap.md`

---

# Purpose

本文件定義所有 CSE Framework、Repository、Skill、Prompt、Config、Schema、Adapter、Integration、Tool、Workflow 與 Release 的安全標準。

Security 的目的，是在不犧牲可用性的前提下，建立最小但足夠的控制，保護：

- 使用者資料
- 敏感資訊
- Repository
- 執行權限
- 外部工具
- 模型輸入與輸出
- 供應鏈依賴
- Release 流程
- 企業系統
- 審計紀錄

任何高風險功能、外部操作、不可逆動作或敏感資料處理，都必須在設計階段納入安全控制，而不是等發布前才補做。

---

# 1. Security Principles

所有 CSE Security 設計必須遵循：

1. **Security by Design**
2. **Least Privilege**
3. **Data Minimization**
4. **Secure Defaults**
5. **Explicit Authorization**
6. **Human Review for High-Risk Actions**
7. **Fail Closed**
8. **Reversible Before Irreversible**
9. **Secrets Never in Source**
10. **Auditability by Default**
11. **Dependency Trust Must Be Verified**
12. **Security Overrides Convenience**

---

# 2. Security Scope

本標準適用於：

- Framework Definition
- Framework Blueprint
- Repository
- Documentation
- Skills
- Prompts
- Templates
- Configs
- Schemas
- Adapters
- Integrations
- Tools
- Agents
- Workflows
- External APIs
- File Operations
- GitHub Actions
- Releases
- Logs
- Security Incidents

---

# 3. Security Model

CSE Security 採用六層模型：

```text
Data Security
   ↓
Identity and Access
   ↓
Execution Safety
   ↓
Integration Security
   ↓
Supply Chain Security
   ↓
Monitoring and Response
```

---

# 4. Risk Classification

每個 Artifact、Skill 或 Workflow 應先分類風險。

| Risk Level | Description | Example |
|---|---|---|
| Low | 不涉及敏感資料或外部操作 | 文字摘要 |
| Medium | 涉及內部文件或有限工具 | 文件分析 |
| High | 涉及權限、外部寫入或重要決策 | GitHub 寫入、寄信 |
| Critical | 涉及不可逆操作、敏感資料或生產系統 | 刪除資料、部署、生產變更 |

## 4.1 Mandatory Controls

| Risk Level | Human Review | Logging | Rollback | Security Review |
|---|---:|---:|---:|---:|
| Low | Optional | Minimal | Optional | Optional |
| Medium | Recommended | Required | Recommended | Recommended |
| High | Required | Required | Required | Required |
| Critical | Required | Required | Mandatory | Mandatory |

---

# 5. Data Classification

所有資料應分類後再決定處理方式。

| Classification | Description | Handling |
|---|---|---|
| Public | 可公開資訊 | 可正常處理 |
| Internal | 組織內部資訊 | 限制分享 |
| Confidential | 商業、客戶、未公開資訊 | 嚴格存取控制 |
| Restricted | 個資、憑證、法律、醫療、財務敏感資料 | 最小化、遮罩、人工審核 |

## 5.1 Data Classification Rules

- 不確定時，採較高等級
- Restricted 資料不得進入公開 Repository
- Confidential 與 Restricted 資料不得放入 Example
- 真實資料應以匿名或合成資料取代
- 不得為了方便而降低分類

---

# 6. Data Minimization

只收集與任務必要的資料。

執行前應確認：

- 是否真的需要這個欄位？
- 是否可使用摘要？
- 是否可遮罩？
- 是否可匿名化？
- 是否可使用合成資料？
- 是否可縮短保留時間？

禁止：

- 收集與任務無關的個資
- 將完整文件傳給不需要的工具
- 保存不必要的 Prompt、Input 或 Output
- 在 Log 中記錄完整敏感內容

---

# 7. Secret Management

Secret 包括：

- API Key
- Token
- Password
- Private Key
- OAuth Credential
- Internal Endpoint
- Service Account Credential
- Signing Key

## 7.1 Secret Rules

不得將 Secret 放入：

- Markdown
- Config Example
- Source Code
- Prompt
- Template
- README
- Commit History
- Issue
- Pull Request
- Log

應使用：

- Environment Variables
- Secret Manager
- GitHub Secrets
- External Vault
- Runtime Injection

範例：

```yaml
api_key_env: OPENAI_API_KEY
```

禁止：

```yaml
api_key: sk-xxxxxxxx
```

---

# 8. Identity and Access Control

所有外部操作必須有明確身份與權限。

## 8.1 Least Privilege

每個 Skill、Tool、Agent 只能取得完成任務所需的最小權限。

例如：

- 只讀需求不授予寫入權限
- 只需單一 Repository 不授予整個 Organization
- 只需建立 Draft 不授予直接發布權限

## 8.2 Access Rules

- 權限需明確授權
- 高權限操作需人工確認
- 權限變更需記錄
- Token 應限制 Scope
- Token 應有到期時間
- 不共用個人 Credential
- 不使用長期有效的高權限金鑰

---

# 9. Authorization Before Action

外部寫入、刪除、發布、部署或通知前，必須確認：

1. 使用者意圖
2. 目標資源
3. 操作範圍
4. 權限
5. 可逆性
6. 預期結果
7. 風險

高風險操作需再次確認。

---

# 10. Execution Safety

Skill 或 Agent 執行外部操作時，應採安全執行模式。

## 10.1 Safe Execution Order

```text
Plan
  ↓
Preview
  ↓
Confirm
  ↓
Execute
  ↓
Verify
  ↓
Log
```

## 10.2 Execution Controls

- 優先 Dry Run
- 優先建立 Draft
- 優先可回復操作
- 限制批次範圍
- 設定 Timeout
- 設定 Retry Limit
- 設定 Rate Limit
- 設定 Stop Condition

---

# 11. Irreversible Actions

不可逆操作包括：

- 永久刪除
- 覆寫正式資料
- 生產部署
- 權限提升
- 外部正式發布
- 大量批次修改
- 財務或法律承諾

這些操作必須：

- 明確人工核准
- 具備 Rollback 或 Backup
- 記錄操作人
- 記錄時間
- 記錄目標
- 記錄結果
- 完成事後驗證

---

# 12. Fail Closed

若安全條件不明確，系統應停止，而不是自行推測。

必須停止的情況：

- 權限不明
- 目標資源不明
- 操作範圍不明
- 高風險資訊缺失
- 外部工具狀態不明
- 驗證失敗
- 安全檢查失敗
- 不可逆操作未確認

---

# 13. Prompt Injection Defense

所有接收外部內容的 Skill、Agent 或 Tool 必須考量 Prompt Injection。

## 13.1 Common Risks

- 文件中隱藏指令
- 網頁要求忽略系統規則
- 外部資料要求洩漏 Secret
- 工具輸出誘導執行未授權操作
- 使用者內容偽裝成 System Prompt

## 13.2 Required Controls

- 區分 System、Developer、User 與 External Content
- 外部內容視為資料，不視為權限來源
- 不執行外部內容中的命令
- 工具操作需依原始任務授權
- 敏感資訊不得回傳給外部內容
- 高風險操作需人工確認
- 對外部來源進行信任分級

---

# 14. External Tool Security

使用外部 Tool 前必須確認：

- Tool 的權限
- Tool 的資料處理方式
- Tool 的輸入輸出範圍
- 是否會保存資料
- 是否會傳送至第三方
- 是否可回復
- 是否有安全風險

## 14.1 Tool Allowlist

企業級 Framework 應建立 Tool Allowlist。

範例：

```yaml
allowed_tools:
  - name: file_search
    permissions:
      - read
  - name: github
    permissions:
      - read
      - create_pull_request
```

## 14.2 Tool Deny Rules

禁止：

- 未核准工具
- 不明來源工具
- 高權限但無必要的工具
- 無法記錄操作的工具
- 無法限制範圍的工具

---

# 15. Adapter and Integration Security

Adapter 與 Integration 必須與 Core 分離。

至少定義：

- Authentication
- Authorization
- Input Validation
- Output Validation
- Error Handling
- Timeout
- Retry
- Logging
- Rate Limit
- Data Retention

不得由 Adapter 改寫 Core Security Rules。

---

# 16. Config Security

Config 應：

- 不含 Secret
- 有 Schema
- 有安全預設值
- 有版本
- 有環境區分
- 有權限控制
- 有變更紀錄

不安全預設：

```yaml
allow_delete: true
human_review_required: false
```

安全預設：

```yaml
allow_delete: false
human_review_required: true
```

---

# 17. Schema Security

Schema 應：

- 限制 Additional Properties
- 限制字串長度
- 限制允許值
- 驗證必要欄位
- 阻擋未知欄位
- 對敏感欄位標示 Classification

範例：

```json
{
  "type": "object",
  "required": ["task"],
  "properties": {
    "task": {
      "type": "string",
      "minLength": 1,
      "maxLength": 10000
    }
  },
  "additionalProperties": false
}
```

---

# 18. Logging Standard

重要操作應記錄：

- Actor
- Skill
- Version
- Action
- Target
- Timestamp
- Result
- Validation
- Reviewer

不得記錄：

- Secret
- 完整 Credential
- 不必要個資
- 完整敏感文件內容
- 高風險 Prompt 原文（若非必要）

## 18.1 Log Retention

Log 應有：

- Retention Period
- Access Control
- Redaction
- Deletion Policy
- Audit Policy

---

# 19. Privacy Protection

涉及個資時，必須：

- 明確目的
- 最小化資料
- 限制存取
- 限制保留
- 提供刪除機制
- 避免二次使用
- 避免公開傳輸
- 使用匿名化或遮罩

---

# 20. Supply Chain Security

供應鏈包括：

- Third-Party Libraries
- GitHub Actions
- External Skills
- MCP Servers
- Models
- APIs
- Containers
- Packages

## 20.1 Supply Chain Controls

- 固定版本
- 驗證來源
- 檢查 License
- 掃描漏洞
- 限制權限
- 記錄更新
- 不直接信任不明 Repository
- 不使用未維護依賴

---

# 21. GitHub Security

Repository 至少應：

- 啟用 Branch Protection
- 禁止 Secret Commit
- 啟用 Dependency Alerts
- 啟用 Code Review
- 限制 GitHub Actions 權限
- 使用 Pin Version
- 保護 Release Tag
- 使用 SECURITY.md

---

# 22. Security Validation

Security Standard 定義安全控制與安全檢查範圍，但不重複建立完整 Validation Model。

Security Validation 至少應涵蓋：

- Secret Scan
- Permission Review
- Data Flow Review
- Prompt Injection Review
- External Tool Review
- Logging Review
- Irreversible Action Review
- Supply Chain Review

Validation Plan、Acceptance Criteria、Severity Mapping、Decision 與正式報告，統一由 [Validation Standard](./11-validation-standard.md) 定義。

# 23. Security Severity

安全 Finding 使用以下等級：

| Severity | Release Impact |
|---|---|
| Critical | 立即阻止 Release |
| High | 發布前必須修正 |
| Medium | 建立修正計畫 |
| Low | 可延後改善 |
| Informational | 建議事項 |

正式 Finding、Decision 與 Release Recommendation 仍依 [Validation Standard](./11-validation-standard.md) 管理。
## 23.1 Validation Severity Mapping

| Security Severity | Validation Severity | Release Impact |
|---|---|---|
| Critical | Critical | 阻止 Release |
| High | Major | 發布前必須修正 |
| Medium | Major | 必須修正，或由 Owner 明確接受風險 |
| Low | Minor | 可納入改善計畫 |
| Informational | Informational | 不阻止 Release |

Security Finding 應保留原始 Security Severity；進入正式 Validation Report 時，必須同步映射為 Validation Severity。

# 24. Incident Response

標準流程：

```text
Detect
  ↓
Contain
  ↓
Assess
  ↓
Mitigate
  ↓
Recover
  ↓
Review
```

## 24.1 Incident Record

至少包含：

- Incident ID
- Detected At
- Affected Components
- Severity
- Impact
- Immediate Action
- Root Cause
- Fix
- Validation
- Owner
- Post-Incident Review

---

# 25. Security Release

安全修正應：

- 優先處理
- 限制公開細節
- 標示受影響版本
- 提供修復版本
- 提供緩解措施
- 更新 CHANGELOG
- 建立 Post-Incident Review
- 補充 Regression Test

---

# 26. Security Review Triggers

以下變更必須 Security Review：

- 新增外部 Tool
- 新增外部 Integration
- 新增高權限操作
- 新增資料儲存
- 新增 Secret
- 新增生產部署
- 修改權限
- 新增自動刪除
- 修改 Log
- 新增第三方依賴
- Breaking Change

---

# 27. Human Review

以下操作必須人工審核：

- 不可逆操作
- 權限提升
- 生產環境修改
- 敏感資料外傳
- 對外正式發布
- 高金額或法律承諾
- 重大安全設定
- Critical Risk Workflow

人工審核不得被模型自我檢查取代。

---

# 28. Security Checklist

## Data

- [ ] Data Classification 已完成
- [ ] 只使用必要資料
- [ ] Sensitive Data 已遮罩
- [ ] Retention 已定義

## Secrets

- [ ] 無 Secret 進入 Repository
- [ ] Secret 使用外部管理
- [ ] Credential Scope 最小
- [ ] Token 有效期合理

## Access

- [ ] Least Privilege
- [ ] Authorization 明確
- [ ] 高風險操作有人工確認
- [ ] 權限變更有紀錄

## Execution

- [ ] 優先 Dry Run
- [ ] 有 Stop Condition
- [ ] 有 Rollback
- [ ] 不可逆操作已核准

## Tools

- [ ] Tool 已核准
- [ ] 權限合理
- [ ] 輸入輸出已驗證
- [ ] External Content 不具權限

## Config and Schema

- [ ] Config 無 Secret
- [ ] Defaults 安全
- [ ] Schema 限制合理
- [ ] Additional Properties 已控制

## Logging

- [ ] 操作有紀錄
- [ ] Log 無 Secret
- [ ] Retention 已定義
- [ ] Access Control 已建立

## Supply Chain

- [ ] Dependency 來源可信
- [ ] Version 固定
- [ ] License 已確認
- [ ] 漏洞已掃描

## Review

- [ ] Security Review 完成
- [ ] Findings 已分級
- [ ] Critical Findings 為 0
- [ ] Release Recommendation 已完成

---

# 29. Anti-Patterns

## 29.1 Secret in Example

將真實 Key 放入範例。

修正：

- 使用 Environment Variable 或 Placeholder。

## 29.2 Over-Privileged Tool

給 Tool 超過需求的權限。

修正：

- 限縮 Scope。

## 29.3 Silent External Action

未經確認就執行外部寫入。

修正：

- Preview、Confirm、Execute。

## 29.4 Trust External Content

直接執行外部文件中的指令。

修正：

- 將外部內容視為資料。

## 29.5 Logging Everything

將完整 Prompt、文件與敏感資料寫入 Log。

修正：

- Data Minimization 與 Redaction。

## 29.6 Unsafe Defaults

預設允許刪除、發布或高權限操作。

修正：

- Secure Defaults。

## 29.7 Security Review at the End

最後才考慮安全。

修正：

- Security by Design。

---

# 30. Immediate Corrections

本版已建立並修正以下核心要求：

1. **Security 從附加檢查提升為設計前置條件**
   - 高風險功能必須在 Blueprint 與 Design 階段納入控制。

2. **加入 Data Classification**
   - Public、Internal、Confidential、Restricted。

3. **加入 Prompt Injection 與 External Content 控制**
   - 外部內容不得成為權限來源。

4. **加入 Tool Allowlist 與 Least Privilege**
   - Tool 只能取得必要權限。

5. **加入 Fail Closed 與 Irreversible Action 規則**
   - 安全條件不明時必須停止。

6. **加入 Supply Chain 與 GitHub Security**
   - 第三方依賴、GitHub Actions 與版本固定納入安全範圍。

7. **加入 Incident Response 與 Security Release**
   - 安全事件有正式處理與版本流程。

8. **加入 Logging、Privacy 與 Retention**
   - 避免過度記錄與敏感資料外洩。

---

# 31. Definition of Done

本文件完成代表：

- 已建立 CSE Security 的正式標準
- 已定義 Security Principles 與 Risk Classification
- 已建立 Data Classification 與 Data Minimization
- 已建立 Secret、Identity、Access 與 Authorization 規則
- 已建立 Execution Safety 與 Irreversible Action 規則
- 已建立 Prompt Injection 與 External Tool 控制
- 已建立 Config、Schema、Logging 與 Privacy 規則
- 已建立 Supply Chain 與 GitHub Security
- 已建立 Security Validation、Severity 與 Incident Response
- 已建立 Security Release 與 Human Review 規則
- 已建立完整 Security Checklist
- 可供所有 CSE Framework 建立一致、可審核與可維護的安全控制

---


# Related Documents

- [Validation Standard](./11-validation-standard.md)
- [Governance Standard](./12-governance-standard.md)
- [Glossary](./14-glossary.md)

# Next Document

**14-glossary.md**

下一份文件將定義：

- CSE 核心術語
- 正式名稱
- 禁止混用詞
- Framework、Skill、Prompt、Template、Validation、Governance、Security 等定義
- 中英文對照
