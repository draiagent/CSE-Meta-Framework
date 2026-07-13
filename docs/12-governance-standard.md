# 12 Governance Standard

> CSE Meta Framework — Governance Standard

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Governance Standard  
Source of Truth: Governance Standard  
Last Updated: 2026-07-11

Depends On:
- `14-glossary.md`

Required By:
- `10-release-standard.md`
- `11-validation-standard.md`
- `13-security-standard.md`
- `15-roadmap.md`

---

# Purpose

本文件定義所有 CSE Framework、Repository、Skill、Template、Config、Schema、文件與 Release 的治理標準。

Governance 的目的，是確保 CSE 生態中的每一項重大決策、變更、責任與風險，都具備：

- 明確 Owner
- 清楚 Decision Rights
- 可追蹤變更
- 可審核紀錄
- 一致 Review 流程
- 可處理衝突
- 可管理淘汰
- 可維持長期可信度

Governance 不應增加不必要官僚程序，而應建立最小但足夠的控制機制。

---

# 1. Governance Principles

所有 CSE Governance 必須遵循：

1. **Clear Ownership**
2. **Explicit Decision Rights**
3. **One Source of Authority**
4. **Review Before Merge**
5. **Evidence-Based Decisions**
6. **Traceable Change Control**
7. **No Silent Breaking Change**
8. **Conflict Must Be Resolved Explicitly**
9. **Deprecation Before Removal**
10. **Auditability by Default**
11. **Minimum Necessary Governance**
12. **Security and Safety Override Convenience**

---

# 2. Governance Scope

本標準適用於：

- CSE Meta Framework
- 所有 CSE 子 Framework
- Repository 結構
- Core Methodology
- Skills
- Templates
- Prompts
- Configs
- Schemas
- Adapters
- Integrations
- Examples
- Tests
- Documentation
- Releases
- Deprecations
- Major Decisions
- Cross-Framework Dependencies

---

# 3. Governance Model

CSE Governance 採用五層模型：

```text
Principles
   ↓
Roles
   ↓
Decision Rights
   ↓
Change Control
   ↓
Audit and Review
```

---

# 4. Governance Roles

每個 Framework 至少應定義以下角色：

| Role | Primary Responsibility |
|---|---|
| Framework Owner | 決定方向、Scope 與重大變更 |
| Architect | 維護方法論、架構與技術一致性 |
| Maintainer | 維護 Repository、版本與日常變更 |
| Reviewer | 獨立審查品質、邏輯與一致性 |
| Security Reviewer | 審查安全、權限與資料風險 |
| Documentation Reviewer | 審查文件品質與一致性 |
| Contributor | 提交內容、修正、案例或程式 |
| User Representative | 提供實際使用需求與回饋 |

同一人可兼任多個角色，但重大變更不應由單一角色完全自我核准。

---

# 5. Role Responsibilities

## 5.1 Framework Owner

Framework Owner 負責：

- Vision
- Mission
- Scope
- Non-Goals
- Roadmap
- Major Release
- Deprecation
- Conflict Resolution
- Final Approval

Framework Owner 不應直接繞過 Review 與 Validation。

---

## 5.2 Architect

Architect 負責：

- Core Methodology
- Architecture
- Interface
- Dependency
- Compatibility
- ADR
- Breaking Change Impact

---

## 5.3 Maintainer

Maintainer 負責：

- Issue Triage
- Pull Request 管理
- Version 更新
- CHANGELOG
- Release 準備
- Link、Schema、Config 維護
- Deprecated 內容標示

---

## 5.4 Reviewer

Reviewer 負責：

- Scope Alignment
- Logic
- Consistency
- Validation
- Acceptance Criteria
- Known Limitations
- Release Recommendation

Reviewer 應盡可能獨立於原始作者。

---

## 5.5 Security Reviewer

Security Reviewer 負責：

- 權限
- 敏感資料
- 外部整合
- Secret
- 不可逆操作
- 安全預設值
- 高風險工具
- Security Release

---

# 6. Decision Rights

重大決策必須有明確權責。

## 6.1 Decision Types

| Decision Type | Owner | Required Review |
|---|---|---|
| Minor Documentation Change | Maintainer | Optional |
| Skill Patch | Maintainer | Reviewer |
| New Skill | Framework Owner / Architect | Reviewer |
| Scope Change | Framework Owner | Architect + Reviewer |
| Core Methodology Change | Framework Owner | Architect + Validation |
| Breaking Change | Framework Owner | Architect + Maintainer + Reviewer |
| Security Change | Security Reviewer | Framework Owner |
| Major Release | Framework Owner | Release Review |
| Deprecation | Framework Owner | Maintainer + Reviewer |
| Cross-Framework Dependency | Framework Owner | Both Framework Owners |

---

# 7. RACI Model

重大工作建議使用 RACI：

- **R — Responsible**
- **A — Accountable**
- **C — Consulted**
- **I — Informed**

範例：

| Activity | Owner | Architect | Maintainer | Reviewer | Security |
|---|---|---|---|---|---|
| Core Methodology Change | A | R | C | C | I |
| Release | A | C | R | C | C |
| Security Fix | A | C | R | C | R |
| Documentation Update | I | C | R | A | I |

---

# 8. Change Classification

所有變更分為四級：

| Level | Change Type | Example |
|---|---|---|
| Level 1 | Editorial | 錯字、格式、失效連結 |
| Level 2 | Compatible | 新增相容案例、Template、Optional Field |
| Level 3 | Significant | 新 Skill、架構調整、相容性影響 |
| Level 4 | Breaking / Critical | Scope、Core Methodology、Contract、安全重大變更 |

---

# 9. Change Control Process

標準流程：

```text
Propose
  ↓
Classify
  ↓
Analyze Impact
  ↓
Review
  ↓
Validate
  ↓
Approve
  ↓
Implement
  ↓
Release
  ↓
Audit
```

---

# 10. Change Proposal

Level 3 與 Level 4 變更必須建立正式 Proposal。

至少包含：

- Problem
- Proposed Change
- Why Now
- Scope Impact
- Compatibility Impact
- Security Impact
- Migration Requirement
- Alternatives
- Validation Plan
- Rollback Plan
- Owner
- Reviewers

---

# 11. Architecture Decision Record

重大決策必須建立 ADR。

## 11.1 ADR Required Conditions

以下情況必須建立 ADR：

- 修改 Core Methodology
- 修改 Repository Boundary
- 新增主要模組
- 移除核心模組
- 修改 Input / Output Contract
- 修改 Schema Contract
- 引入重大依賴
- 變更 Provider Strategy
- 進行 Breaking Change

## 11.2 ADR Structure

```markdown
# ADR-{{NUMBER}} {{TITLE}}

Status: Proposed
Date: YYYY-MM-DD
Owner: CSE

## Context

## Decision

## Alternatives

## Consequences

## Validation

## Related Documents
```

## 11.3 ADR Status

```text
Proposed
Accepted
Superseded
Deprecated
Rejected
```

---

# 12. Review Standard

所有重大變更必須經過 Review。

## 12.1 Review Dimensions

- Scope
- Methodology
- Architecture
- Compatibility
- Security
- Documentation
- Validation
- Migration
- Version Impact

## 12.2 Review Result

```text
Approve
Approve with Conditions
Request Changes
Reject
```

## 12.3 Review Record

```yaml
review:
  artifact:
  version:
  reviewer:
  result:
  findings:
  required_changes:
  conditions:
  reviewed_at:
```

---

# 13. Approval Standard

重大變更核准前必須確認：

- Proposal 完整
- Impact Analysis 完成
- Validation 通過
- Migration 已準備
- Rollback 已準備
- Reviewer 已核准
- CHANGELOG 已更新
- Version Impact 已確認

---

# 14. Merge Governance

## 14.1 Pull Request Requirements

重大 Pull Request 必須包含：

- Summary
- Change Type
- Related Issue
- Related ADR
- Validation Result
- Compatibility Impact
- Security Impact
- Migration Notes
- Screenshots / Evidence（如適用）

## 14.2 Merge Rules

- Stable Branch 不得直接 Push
- Core 變更必須 Pull Request
- Breaking Change 必須 Owner Approval
- Security Change 必須 Security Review
- 未通過 Validation 不得 Merge
- 所有 Review Comment 必須處理或明確回覆

---

# 15. Issue Governance

Issue 應分類：

| Type | Purpose |
|---|---|
| Bug | 功能錯誤 |
| Documentation | 文件問題 |
| Feature | 新功能 |
| Framework Change | 方法論或架構變更 |
| Security | 安全問題 |
| Deprecation | 淘汰建議 |
| Question | 使用問題 |

Issue 至少包含：

- Version
- Environment
- Reproduction
- Expected Result
- Actual Result
- Impact
- Evidence

---

# 16. Contribution Governance

所有 Contributor 應遵循：

- CONTRIBUTING.md
- CODE_OF_CONDUCT.md
- Naming Standard
- Document Standard
- Validation Standard
- License Requirement

重大貢獻需：

- 綁定 Issue
- 提供 Validation
- 說明相容性
- 提供必要測試
- 更新文件

---

# 17. Conflict Resolution

衝突類型包括：

- Scope Conflict
- Methodology Conflict
- Ownership Conflict
- Priority Conflict
- Cross-Framework Conflict
- Review Disagreement

## 17.1 Resolution Order

```text
Clarify Facts
   ↓
Check Philosophy
   ↓
Check Scope
   ↓
Review Evidence
   ↓
Compare Options
   ↓
Escalate to Owner
   ↓
Record Decision
```

## 17.2 Final Authority

- 技術架構：Architect
- Scope 與方向：Framework Owner
- 安全：Security Reviewer 可暫停 Release
- 發布：Release Owner
- 跨 Framework：雙方 Owner 共同決定
- 無法解決：提交 CSE Meta Governance Review

---

# 18. Cross-Framework Governance

跨 Framework 依賴必須：

- 記錄 Framework Name
- 記錄 Version
- 記錄 Component
- 記錄 Required / Optional
- 記錄 Owner
- 記錄相容範圍
- 記錄失效處理

範例：

```yaml
dependency:
  framework: CSE-TaskRouter
  version: ">=1.0.0 <2.0.0"
  component: routing-policy
  required: true
  owner: CSE
```

---

# 19. Deprecation Governance

功能不得直接刪除。

標準流程：

```text
Proposal
  ↓
Approval
  ↓
Deprecated
  ↓
Migration Period
  ↓
Removal
  ↓
Archive
```

Deprecated 內容必須提供：

- Deprecated Version
- Removal Version
- Replacement
- Migration Guide
- Support Period
- Known Risks

---

# 20. Emergency Governance

緊急治理適用於：

- Critical Security Issue
- Data Exposure
- Core Skill Failure
- Production Blocking Error
- Legal or Compliance Risk

緊急流程可以縮短，但不得省略：

- Owner Notification
- Immediate Mitigation
- Validation
- Version Update
- CHANGELOG
- Post-Incident Review

完整安全事件處理、Security Severity 與 Security Release，統一由 [Security Standard](./13-security-standard.md) 定義。

# 21. Audit and Traceability

重大變更必須可追蹤。

至少記錄：

- Issue
- Proposal
- ADR
- Pull Request
- Review
- Validation
- Approval
- Version
- Release
- Post-Release Review

不得只在聊天或口頭討論中保存重大決策。

---

# 22. Decision Log

建議位置：

```text
docs/decisions/
```

Decision Log 至少包含：

- Decision ID
- Date
- Owner
- Context
- Decision
- Alternatives
- Impact
- Status

---

# 23. Governance Metrics

建議追蹤：

| Metric | Purpose |
|---|---|
| Open Issues | 維護負荷 |
| Time to Review | Review 效率 |
| Time to Release | 發布效率 |
| Reopened Issues | 修正品質 |
| Regression Rate | 版本穩定性 |
| Breaking Changes | 相容性風險 |
| Security Findings | 安全風險 |
| Deprecated Items | 淘汰管理 |
| Documentation Drift | 文件一致性 |

---

# 24. Governance Profiles

## 24.1 Small

適用：

- 小型 Skill
- 個人維護
- 概念驗證

最低治理：

- Owner
- Version
- CHANGELOG
- Review
- Validation

## 24.2 Standard

適用：

- 公開 GitHub Framework

需要：

- Owner
- Maintainer
- Reviewer
- PR Review
- ADR
- Validation
- Release Governance

## 24.3 Enterprise

適用：

- 多團隊
- 高風險
- 長期維護

需要：

- Governance Board
- Security Review
- RACI
- Compatibility Management
- Formal Audit
- Change Advisory
- Incident Review

---

# 25. Governance Checklist

## Ownership

- [ ] Framework Owner 已指定
- [ ] Maintainer 已指定
- [ ] Reviewer 已指定
- [ ] Security Reviewer 已指定（如適用）

## Decision Rights

- [ ] 決策類型已分類
- [ ] RACI 已建立
- [ ] Final Authority 已定義

## Change Control

- [ ] Proposal 已建立
- [ ] Impact Analysis 已完成
- [ ] ADR 已建立（如適用）
- [ ] Validation 已完成
- [ ] Version Impact 已確認

## Review and Merge

- [ ] Pull Request 完整
- [ ] Reviewer 已核准
- [ ] Security Review 已完成
- [ ] 未通過項目已處理
- [ ] Merge Rules 已遵守

## Deprecation

- [ ] Replacement 已定義
- [ ] Migration Guide 已提供
- [ ] Support Period 已定義
- [ ] Removal Version 已標示

## Audit

- [ ] Issue 可追蹤
- [ ] Decision 可追蹤
- [ ] Validation 可追蹤
- [ ] Release 可追蹤
- [ ] Post-Release Review 已保存

---

# 26. Anti-Patterns

## 26.1 Ownerless Framework

沒有明確負責人。

修正：

- 指定 Framework Owner。

## 26.2 Self-Approved Breaking Change

作者自行核准重大變更。

修正：

- 使用獨立 Review 與 Owner Approval。

## 26.3 Decision in Chat Only

重大決策只存在對話中。

修正：

- 建立 ADR 或 Decision Record。

## 26.4 Silent Scope Expansion

功能逐步擴張但未更新 Blueprint。

修正：

- 建立 Change Proposal 與 Scope Review。

## 26.5 Direct Removal

直接刪除舊功能。

修正：

- 執行 Deprecation Governance。

## 26.6 Security Override by Schedule

因趕發布而跳過安全審查。

修正：

- Security Reviewer 可阻止 Release。

## 26.7 Governance Overload

小型專案套用過度複雜流程。

修正：

- 使用 Small / Standard / Enterprise Profile。

---

# 27. Immediate Corrections

本版已建立並修正以下核心要求：

1. **Governance 不再只有角色清單**
   - 加入 Decision Rights、RACI、Change Control 與 Audit。

2. **建立四級 Change Classification**
   - 不同變更採不同治理強度。

3. **建立正式 Proposal、ADR、Review 與 Approval 流程**
   - 重大變更不可只靠口頭決定。

4. **加入 Conflict Resolution**
   - 明確定義不同衝突的處理順序與最終權責。

5. **加入 Cross-Framework Governance**
   - 跨 Repository 依賴必須可追蹤。

6. **加入 Emergency Governance**
   - 緊急事件可加速，但不可省略紀錄與事後 Review。

7. **加入 Governance Profiles**
   - 小型、標準、企業級採不同治理強度。

8. **加入 Audit、Metrics 與 Decision Log**
   - 治理結果可被衡量與追蹤。

---

# 28. Definition of Done

本文件完成代表：

- 已建立 CSE Governance 的正式標準
- 已定義 Ownership、Roles 與 Decision Rights
- 已建立 RACI
- 已建立 Change Classification 與 Change Control
- 已建立 Proposal、ADR、Review、Approval 與 Merge Governance
- 已建立 Issue 與 Contribution Governance
- 已建立 Conflict Resolution
- 已建立 Cross-Framework Governance
- 已建立 Deprecation 與 Emergency Governance
- 已建立 Audit、Decision Log 與 Metrics
- 已建立 Small、Standard、Enterprise Governance Profiles
- 可供所有 CSE Framework 執行一致、可追蹤與可審核的治理

---


# Related Documents

- [Release Standard](./10-release-standard.md)
- [Validation Standard](./11-validation-standard.md)
- [Security Standard](./13-security-standard.md)
- [Glossary](./14-glossary.md)

# Next Document

**13-security-standard.md**

下一份文件將定義：

- Security Principles
- Data Classification
- Secret Management
- Least Privilege
- External Tools
- Prompt Injection
- Logging
- Incident Response
- Security Review
- Security Release
