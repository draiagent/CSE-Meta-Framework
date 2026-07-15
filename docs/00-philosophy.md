# 00 Philosophy

> CSE Meta Framework — Philosophy

Version: 1.0.0  
Status: Draft  
Owner: CSE  
Category: Core Foundation  
Source of Truth: Philosophy  
Last Updated: 2026-07-11

Depends On:
- None

Required By:
- `01-framework-lifecycle.md`
- `02-framework-blueprint.md`
- `03-design-principles.md`
- `06-core-methodology.md`
- `14-glossary.md`

---

# Purpose

本文件定義 **CSE Meta Framework** 的存在目的、核心哲學、價值主張與邊界。

它是所有 CSE Framework 的最高層原則。

任何後續 Framework、Standard、Skill、Template 或 Repository，都不得違反本文件。

---

# 1. Why CSE Meta Framework Exists

AI Framework 常見問題包括：

- 每個 Repository 結構不同
- 方法論互相重疊
- 文件格式不一致
- Skill 無法重複使用
- 模型與工具設定寫死
- 缺乏共同開發流程
- 新專案每次都從零開始
- 後續版本難以維護

CSE Meta Framework 的目的，是建立一套可重複使用的母架構，使所有 CSE Framework 都能依循相同的哲學、生命週期、設計標準與品質規範。

---

# 2. Vision

建立一套統一、模組化、可擴充的 AI Framework 母架構，讓不同類型的 CSE Framework 能以一致方式被設計、開發、驗證、發布與持續演進。

---

# 3. Mission

CSE Meta Framework 的使命是：

1. 定義 Framework 如何誕生。
2. 建立所有 Framework 共用的生命週期。
3. 統一 Repository、文件、Skill 與 Template 標準。
4. 降低重複設計與維護成本。
5. 提升人類與 AI 協作時的一致性與可理解性。
6. 讓新 Framework 能快速複製並持續擴充。

---

# 4. Core Philosophy

## 4.1 Build Once, Reuse Everywhere

建立一次，所有 Framework 共用。

所有方法、模板、規格與流程，應優先設計為可重複使用，而不是只服務單一專案。

---

## 4.2 Consistency Over Complexity

一致性優先於複雜功能。

若新增功能會破壞整體一致性，應先重新設計，而不是直接加入。

---

## 4.3 Framework Before Content

先定義 Framework，再產生內容。

任何新專案都應先完成問題、邊界、生命週期與架構，再進入文件與 Skill 開發。

---

## 4.4 Task-Driven, Not Model-Driven

以任務與能力需求驅動設計，而不是由特定模型名稱或平台主導。

---

## 4.5 Vendor Neutral by Default

核心方法論不得依賴單一供應商。

平台差異應集中於配置層，而不是寫入核心原則。

---

## 4.6 Human Readable and AI Readable

所有內容必須同時符合：

- 人類容易閱讀
- AI 容易理解
- 結構清楚
- 名詞一致
- 可被引用
- 可被驗證

---

## 4.7 Validate Before Release

任何 Framework 在發布前都必須經過驗證。

未驗證的內容只能視為 Draft，不得視為 Stable。

---

## 4.8 Evolve Through Evidence

所有重大調整應基於：

- 官方文件
- 實際測試
- 使用者回饋
- 可重現案例
- 版本紀錄

不得只依個人偏好修改核心標準。

---

# 5. Value Proposition

CSE Meta Framework 提供四項核心價值：

| Value | Description |
|---|---|
| Consistency | 所有 Framework 使用一致架構 |
| Reusability | 文件、Skill、Template 可重複使用 |
| Scalability | 可持續新增 Framework 與模組 |
| Maintainability | 易於版本管理與長期維護 |

---

# 6. Scope

## Included

CSE Meta Framework 負責：

- Framework 哲學
- Framework Lifecycle
- Framework Blueprint
- Design Principles
- Repository Architecture
- Document Standards
- Core Methodology
- Skill Standards
- Template Standards
- README Standards
- Release Standards
- Validation Standards
- Versioning Standards
- Governance Principles

## Excluded

CSE Meta Framework 不直接負責：

- Prompt Engineering 方法論
- Context Engineering 方法論
- Workflow Engineering 方法論
- Agent 設計
- MCP 設計
- RAG 設計
- 特定程式語言框架
- 特定模型操作教學
- 特定供應商產品比較

上述內容應由獨立 CSE Framework Repository 負責。

---

# 7. Framework Family

CSE Meta Framework 為所有 CSE Framework 的母架構。

```text
CSE Meta Framework
        │
        ├── CSE TaskRouter
        ├── CSE Prompt Engineering
        ├── CSE Context Engineering
        ├── CSE Workflow Engineering
        ├── CSE Agent Framework
        ├── CSE MCP Framework
        └── Future CSE Frameworks
```

---

# 8. Repository Boundary

CSE Meta Framework 只定義：

```text
How a Framework is created
How a Framework is structured
How a Framework is documented
How a Framework is validated
How a Framework is released
How a Framework evolves
```

它不直接定義各子 Framework 的專業內容。

---

# 9. Success Criteria

CSE Meta Framework 成功時，應達成：

- 新 Framework 可依標準流程建立
- Repository 結構一致
- 文件格式一致
- Skill 可直接重複使用
- 模型與工具設定不寫死
- 每個 Framework 邊界清楚
- 發布前有驗證流程
- 版本演進可追蹤
- 人類與 AI 都能快速理解

---

# 10. Non-Goals

CSE Meta Framework 不追求：

- 成為所有 AI 知識的百科全書
- 將所有方法論集中在單一 Repository
- 綁定單一平台
- 取代各專業 Framework
- 為所有情境提供唯一答案
- 以文件數量衡量完整度
- 以複雜度取代可用性

---

# 11. Governing Rule

當後續文件、Template、Skill 或 Repository 與本文件衝突時：

```text
00-philosophy.md 優先
```

任何例外都必須：

1. 明確記錄原因。
2. 經過 Review。
3. 更新 CHANGELOG。
4. 標示適用範圍。
5. 不得影響其他 Framework。

---

# 12. Checklist

- [ ] 已定義 CSE Meta Framework 存在目的
- [ ] 已定義 Vision 與 Mission
- [ ] 已定義核心哲學與價值主張
- [ ] 已定義 Scope 與 Non-Goals
- [ ] 已定義 Framework Family 與 Repository Boundary
- [ ] 已定義 Success Criteria
- [ ] 已定義 Governing Rule 與例外處理程序

---

# 13. Definition of Done

本文件完成代表：

- 已定義 CSE Meta Framework 的存在目的
- 已定義 Vision 與 Mission
- 已定義核心哲學
- 已定義 Scope 與 Non-Goals
- 已定義 Framework Family
- 已定義最高治理原則
- 可作為後續所有文件的基準

---


# Related Documents

- [Framework Lifecycle](./01-framework-lifecycle.md)
- [Framework Blueprint](./02-framework-blueprint.md)
- [Glossary](./14-glossary.md)
- [Roadmap](./15-roadmap.md)

# Next Document

**01-framework-lifecycle.md**

下一份文件將定義 Framework 的母方法論：

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
