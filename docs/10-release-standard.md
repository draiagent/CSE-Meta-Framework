# 10 Release Standard

> CSE Meta Framework — Release Standard

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Release Standard  
Source of Truth: Release Standard  
Last Updated: 2026-07-11

Depends On:
- `09-readme-standard.md`
- `11-validation-standard.md`
- `12-governance-standard.md`
- `13-security-standard.md`
- `14-glossary.md`

Required By:
- `08-template-standard.md`
- `15-roadmap.md`

---

# Purpose

本文件定義所有 CSE Framework、Skill、Template、Config、Schema 與 Repository 的發布標準。

Release 的目的不是「把檔案上傳到 GitHub」，而是確保一個版本具備：

- 明確版本
- 完整驗證
- 可追蹤變更
- 可理解發布內容
- 可處理相容性
- 可執行遷移
- 可回復
- 可持續維護

任何未通過 Release Gate 的版本，不得標示為 Stable。

---

# 1. Release Principles

所有 CSE Release 必須遵循：

1. **Validation Before Release**
2. **Version Every Meaningful Change**
3. **No Silent Breaking Change**
4. **Release Artifacts Must Be Complete**
5. **Migration Before Removal**
6. **Rollback Must Be Possible**
7. **Known Limitations Must Be Visible**
8. **Release Must Be Reproducible**
9. **Security Fixes Take Priority**
10. **Post-Release Review Is Required**

---

# 2. Release Scope

本標準適用於：

- Framework Release
- Repository Release
- Skill Release
- Template Release
- Config Release
- Schema Release
- Documentation Release
- Security Release
- Hotfix Release
- Deprecation Release
- Major Migration Release

---

# 3. Release Types

CSE Release 分為六類：

| Release Type | Purpose | Typical Version Impact |
|---|---|---|
| Initial Release | 首次正式發布 | `1.0.0` |
| Minor Release | 新增相容功能 | `1.x.0` |
| Patch Release | 修正錯誤 | `1.0.x` |
| Major Release | 不相容變更 | `x.0.0` |
| Hotfix Release | 緊急安全或重大錯誤修正 | Patch |
| Deprecation Release | 宣告舊功能淘汰 | Minor / Major |

---

# 4. Release Lifecycle

標準發布流程：

```text
Plan
  ↓
Prepare
  ↓
Validate
  ↓
Release Candidate
  ↓
Approve
  ↓
Publish
  ↓
Verify
  ↓
Review
```

每個階段都必須有明確完成條件。

---

# 5. Stage 1 — Plan

## 5.1 Objective

確認本次 Release 的內容、範圍與影響。

## 5.2 Required Questions

- 為什麼要發布？
- 解決什麼問題？
- 變更範圍是什麼？
- 是否包含 Breaking Change？
- 是否需要 Migration Guide？
- 是否有安全影響？
- 是否影響其他 CSE Framework？
- 是否需要更新 Adapter 或 Config？

## 5.3 Required Output

```text
Release Plan
```

至少包含：

- Release Type
- Proposed Version
- Scope
- Included Changes
- Excluded Changes
- Dependencies
- Risks
- Required Validation
- Required Migration
- Target Date
- Owner

## 5.4 Stage Gate

- [ ] Release Type 已確認
- [ ] Proposed Version 已確認
- [ ] Scope 已確認
- [ ] Breaking Change 已辨識
- [ ] 依賴影響已評估
- [ ] Migration 需求已確認
- [ ] Owner 已指定

---

# 6. Stage 2 — Prepare

## 6.1 Objective

完成所有 Release Artifact 與 Repository 準備。

## 6.2 Required Artifacts

正式 Release 至少應具備：

- README
- LICENSE
- CHANGELOG
- Release Notes
- Validation Report
- Version Metadata
- Updated Documentation
- Updated Skills
- Updated Templates
- Updated Configs
- Updated Schemas
- Known Limitations
- Migration Guide（如適用）
- Rollback Plan（重大版本）
- Security Notes（如適用）

## 6.3 Version Synchronization

以下位置的版本必須一致：

- Root Metadata
- README
- CHANGELOG
- Skill Front Matter
- Template Metadata
- Config Registry
- Schema Version
- Release Notes
- Git Tag

若不同元件使用獨立版本，必須提供 Compatibility Matrix。

## 6.4 Stage Gate

- [ ] 所有 Artifact 已建立
- [ ] 版本資訊已同步
- [ ] 文件連結有效
- [ ] Deprecated 內容已標示
- [ ] Migration 與 Rollback 已準備
- [ ] Security Notes 已準備（如適用）

---

# 7. Stage 3 — Validate

## 7.1 Objective

確認 Release Candidate 符合品質、相容性與安全要求。

Release Standard 只定義 Release Gate，不重複建立完整 Validation Model。

## 7.2 Required Validation

- Structural Validation
- Functional Validation
- Scenario Validation
- Regression Validation
- Security Validation
- Compatibility Validation
- Human Review（如適用）

## 7.3 Required Output

```text
Release Validation Report
```

## 7.4 Release Gate

- [ ] Critical Error 為 0
- [ ] Regression Validation 通過
- [ ] Security Validation 通過
- [ ] Compatibility 已確認
- [ ] Known Limitations 已記錄
- [ ] Release Recommendation 為通過

完整驗證規則請依 [Validation Standard](./11-validation-standard.md) 執行。

# 8. Stage 4 — Release Candidate

## 8.1 Objective

建立可供最終審核的 Release Candidate。

版本格式建議：

```text
1.0.0-rc.1
1.0.0-rc.2
```

## 8.2 RC Requirements

Release Candidate 必須：

- 功能凍結
- Scope 凍結
- 只接受 Critical Fix
- 通過主要驗證
- 文件接近最終版本
- 具備完整 Release Notes
- 具備完整 Migration Guide（如適用）

## 8.3 RC Exit Criteria

- [ ] 無 Critical Issue
- [ ] 所有 Major Issue 已處理
- [ ] 文件完成
- [ ] Compatibility 完成
- [ ] Reviewer 已核准
- [ ] 可正式發布

---

# 9. Stage 5 — Approve

## 9.1 Objective

由指定角色正式核准 Release。

## 9.2 Required Reviewers

依風險可包含：

- Framework Owner
- Maintainer
- Architect
- Security Reviewer
- Documentation Reviewer
- Business Owner
- Human Reviewer

## 9.3 Approval Record

```yaml
approval:
  version:
  owner:
  reviewers:
  approved_at:
  conditions:
  unresolved_items:
  release_status:
```

## 9.4 Stage Gate

- [ ] Owner 核准
- [ ] Required Reviewers 核准
- [ ] 未解問題已接受或修正
- [ ] 發布條件已明確
- [ ] Release Status 已確認

---

# 10. Stage 6 — Publish

## 10.1 Objective

正式發布並建立可追蹤版本。

## 10.2 Publish Actions

1. Merge Release Branch
2. Update Main Branch
3. Create Git Tag
4. Create GitHub Release
5. Attach Release Notes
6. Publish Package / Skill（如適用）
7. Update Documentation
8. Update Registry
9. Announce Release

## 10.3 Git Tag Standard

格式：

```text
v1.0.0
v1.1.0
v2.0.0
```

Hotfix：

```text
v1.0.1
```

Release Candidate：

```text
v1.0.0-rc.1
```

## 10.4 GitHub Release Title

格式：

```text
CSE Framework Name v1.0.0
```

---

# 11. Stage 7 — Verify

## 11.1 Objective

確認正式發布內容與預期一致。

## 11.2 Post-Publish Checks

- Git Tag 正確
- GitHub Release 可見
- Release Notes 完整
- README 顯示正確版本
- Download / Clone 正常
- Skill 可載入
- Template 可使用
- Link 有效
- Registry 已更新
- Package 可取得（如適用）

## 11.3 Stage Gate

- [ ] 發布內容可取得
- [ ] 版本資訊一致
- [ ] 快速測試通過
- [ ] 無立即 Critical Issue
- [ ] 發布結果已確認

---

# 12. Stage 8 — Review

## 12.1 Objective

在發布後評估品質、影響與下一步。

## 12.2 Post-Release Review

至少檢查：

- 是否出現新 Issue
- 是否有相容性問題
- 是否有文件誤差
- 是否有使用者困惑
- 是否需要 Hotfix
- 是否需要更新 Roadmap
- 是否需要補充 Migration Guide
- 是否需要增加 Regression Test

## 12.3 Review Output

```text
Post-Release Review
```

至少包含：

- Release Result
- Issues Found
- User Feedback
- Hotfix Requirement
- Improvement Items
- Next Version Recommendation

---

# 13. Semantic Versioning

CSE 採用：

```text
MAJOR.MINOR.PATCH
```

## 13.1 Major

適用：

- 修改 Core Methodology
- 修改 Input / Output Contract
- 移除主要功能
- 修改 Scope
- 修改 Repository Boundary
- 破壞既有 Skill 相容性
- 破壞 Schema 相容性

範例：

```text
1.5.2 → 2.0.0
```

## 13.2 Minor

適用：

- 新增相容 Skill
- 新增相容 Template
- 新增 Optional Field
- 新增 Example
- 新增 Adapter
- 新增不破壞既有流程的功能

範例：

```text
1.2.0 → 1.3.0
```

## 13.3 Patch

適用：

- 錯字修正
- 失效連結修正
- 非破壞性說明改善
- Bug Fix
- Security Patch
- 測試補強

範例：

```text
1.2.1 → 1.2.2
```

---

# 14. Pre-Release Versioning

可使用：

```text
1.0.0-alpha.1
1.0.0-beta.1
1.0.0-rc.1
```

規則：

- Alpha：功能不完整
- Beta：功能大致完整，可測試
- RC：功能凍結，等待最終核准

---

# 15. Release Status

| Status | Meaning |
|---|---|
| Draft | 尚未進入正式測試 |
| Alpha | 初步可用，變動大 |
| Beta | 可測試，可能有已知問題 |
| Release Candidate | 已通過主要驗證 |
| Stable | 正式支援 |
| Deprecated | 不建議新使用 |
| Archived | 停止維護 |

---

# 16. Release Notes Standard

每次 Release 必須有 Release Notes。

標準結構：

```markdown
# Release {{VERSION}}

Release Date: {{RELEASE_DATE}}
Status: {{STATUS}}

## Summary

{{SUMMARY}}

## Added

{{ADDED}}

## Changed

{{CHANGED}}

## Fixed

{{FIXED}}

## Deprecated

{{DEPRECATED}}

## Removed

{{REMOVED}}

## Security

{{SECURITY}}

## Compatibility

{{COMPATIBILITY}}

## Known Limitations

{{KNOWN_LIMITATIONS}}

## Migration

{{MIGRATION}}

## Validation

{{VALIDATION_SUMMARY}}
```

---

# 17. CHANGELOG Standard

採用以下分類：

```text
Added
Changed
Deprecated
Removed
Fixed
Security
```

每個版本需記錄日期。

範例：

```markdown
## [1.1.0] - 2026-07-11

### Added
- Added release compatibility matrix.

### Changed
- Updated validation gate requirements.

### Fixed
- Corrected broken documentation links.
```

---

# 18. Compatibility Matrix

當 Framework 包含多個元件時，應建立 Compatibility Matrix。

範例：

| Component | Version | Compatible With |
|---|---|---|
| Framework | 2.0.0 | Skill 2.x |
| Skill | 2.1.0 | Config 2.x |
| Template | 1.4.0 | Framework 1.x–2.x |
| Schema | 3.0.0 | Output Contract 3.x |

---

# 19. Migration Standard

Breaking Change 必須提供 Migration Guide。

至少包含：

- From Version
- To Version
- Breaking Changes
- Pre-Migration Checklist
- Migration Steps
- Validation Steps
- Rollback Plan
- Known Issues

禁止只寫：

```text
請更新到最新版本。
```

---

# 20. Rollback Standard

重大 Release 必須具備 Rollback Plan。

至少包含：

- Rollback Trigger
- Previous Stable Version
- Backup Requirements
- Rollback Steps
- Data Impact
- Validation After Rollback
- Owner

Rollback Trigger 範例：

- Critical Security Issue
- Major Compatibility Failure
- Data Corruption Risk
- Core Skill Failure
- Unrecoverable Deployment Error

---

# 21. Deprecation Standard

功能不得直接移除。

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

Deprecated 內容必須標示：

- Deprecated Version
- Removal Version
- Replacement
- Migration Guide
- Support Period

---

# 22. Hotfix Standard

Hotfix 適用：

- Critical Security Issue
- 無法使用的核心功能
- 重大資料風險
- 阻斷 Release 的錯誤

Hotfix 流程可縮短，但不得省略：

- Root Cause
- Fix Validation
- Security Review
- CHANGELOG
- Version Update
- Post-Release Review

---

# 23. Security Release

安全 Release 應：

- 優先處理
- 限制公開細節
- 指定安全 Reviewer
- 明確列出受影響版本
- 提供修復版本
- 必要時提供暫時緩解措施
- 避免在修復前公開利用方式

---

# 24. Release Branch Strategy

建議：

```text
main
develop
release/*
hotfix/*
feature/*
```

小型 Repository 可簡化為：

```text
main
feature/*
```

但 Stable Release 必須透過 Pull Request 與 Review。

---

# 25. Release Ownership

每次 Release 必須指定：

| Role | Responsibility |
|---|---|
| Release Owner | 最終負責 |
| Maintainer | Repository 操作 |
| Reviewer | 品質審查 |
| Security Reviewer | 安全審查 |
| Documentation Reviewer | 文件審查 |
| Migration Owner | 遷移與相容性 |

---

# 26. Release Checklist

## Plan

- [ ] Release Type 已確認
- [ ] Version 已確認
- [ ] Scope 已確認
- [ ] Breaking Change 已確認
- [ ] Owner 已確認

## Prepare

- [ ] README 已更新
- [ ] CHANGELOG 已更新
- [ ] Release Notes 已完成
- [ ] Migration Guide 已完成
- [ ] Rollback Plan 已完成
- [ ] Version 已同步

## Validate

- [ ] Structural Test 通過
- [ ] Functional Test 通過
- [ ] Regression Test 通過
- [ ] Security Test 通過
- [ ] Compatibility 已確認
- [ ] Critical Error 為 0

## Approve

- [ ] Owner 核准
- [ ] Reviewer 核准
- [ ] Security Reviewer 核准（如適用）
- [ ] Documentation Reviewer 核准

## Publish

- [ ] Merge 完成
- [ ] Git Tag 已建立
- [ ] GitHub Release 已建立
- [ ] Registry 已更新
- [ ] Announcement 已完成

## Verify

- [ ] Release 可取得
- [ ] Quick Start 可執行
- [ ] README 版本正確
- [ ] Skill 可載入
- [ ] Links 有效

## Review

- [ ] Post-Release Review 完成
- [ ] Issue 已收集
- [ ] Hotfix 需求已判斷
- [ ] Roadmap 已更新

---

# 27. Release Anti-Patterns

## 27.1 Upload Is Release

只把檔案推到 GitHub 就算發布。

修正：

- 建立 Version、Tag、Release Notes 與 Validation。

## 27.2 Silent Breaking Change

修改契約但不升級 Major Version。

修正：

- 提升 Major Version
- 提供 Migration Guide

## 27.3 No Rollback

發布重大版本但沒有回復方案。

修正：

- Release 前建立 Rollback Plan。

## 27.4 Release Without Validation

未測試就發布 Stable。

修正：

- 必須通過 Release Gate。

## 27.5 Version Drift

README、Skill、Config 與 Tag 版本不一致。

修正：

- 執行 Version Synchronization。

## 27.6 Hidden Limitations

已知問題未公開。

修正：

- Release Notes 必須列出 Known Limitations。

## 27.7 Immediate Removal

直接刪除舊功能。

修正：

- 使用 Deprecation 與 Migration Period。

---

# 28. Immediate Corrections

本版已建立並修正以下核心要求：

1. **Release 不再等同 GitHub 上傳**
   - 必須包含版本、驗證、Tag、Release Notes 與 Review。

2. **加入完整八階段 Release Lifecycle**
   - Plan、Prepare、Validate、RC、Approve、Publish、Verify、Review。

3. **加入 Compatibility、Migration 與 Rollback**
   - Breaking Change 不得直接發布。

4. **加入 Hotfix 與 Security Release**
   - 緊急修正可縮短流程，但不可省略驗證與紀錄。

5. **加入 Release Ownership**
   - 每次發布有明確責任人與 Reviewer。

6. **加入 Version Synchronization**
   - README、Skill、Config、Schema 與 Git Tag 必須一致。

7. **加入 Post-Release Review**
   - 發布後仍需驗證實際使用結果。

---

# 29. Definition of Done

本文件完成代表：

- 已定義 CSE Release 的正式標準
- 已建立 Release 類型與八階段 Lifecycle
- 已建立 Semantic Versioning 與 Pre-Release 規則
- 已建立 Validation Gate 與 Release Candidate
- 已建立 Release Notes 與 CHANGELOG 規範
- 已建立 Compatibility Matrix
- 已建立 Migration、Rollback 與 Deprecation
- 已建立 Hotfix 與 Security Release 規則
- 已建立 Release Ownership 與 Branch Strategy
- 已建立完整 Release Checklist
- 可供所有 CSE Framework 執行一致、可追蹤與可回復的發布流程

---


# Related Documents

- [README Standard](./09-readme-standard.md)
- [Validation Standard](./11-validation-standard.md)
- [Governance Standard](./12-governance-standard.md)
- [Security Standard](./13-security-standard.md)
- [Glossary](./14-glossary.md)
- [Roadmap](./15-roadmap.md)

# Next Document

**11-validation-standard.md**

下一份文件將定義：

- Validation Strategy
- Structural Validation
- Functional Validation
- Scenario Validation
- Regression Validation
- Security Validation
- Human Review
- Acceptance Criteria
- Validation Report
