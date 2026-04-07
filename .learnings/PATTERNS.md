# PATTERNS.md - 重复模式追踪

> 记录 `recurring_count ≥ 3` 的学习项，触发系统文件更新
> 
> **触发：** AGENTS.md Self-Improvement: `recurring ≥ 3 → promote to MEMORY.md`

## 格式说明

```markdown
## [PATTERN-XXX] 模式名称

**Source:** [LEARNING-YYYYMMDD-XXX, ...]

**Type:** [error/correction/knowledge_gap/best_practice/manual_repeat]

**Pattern:**
重复出现的问题或行为模式描述

**Impact:**
这个模式带来的影响

**Proposed Action:**
建议的系统更新行动

**Target File:**
- [ ] SOUL.md
- [ ] AGENTS.md
- [ ] TOOLS.md
- [ ] MEMORY.md
- [ ] 创建脚本/自动化

**Fields:**
- detected_date: [模式检测日期]
- recurring_count: [累积次数]
- status: [detecting/pending/completed]
```

## 模式列表

_(当 LEARNINGS.md 中某项的 `recurring_count ≥ 3` 时，自动添加到这里)_

---

## 范例记录

```markdown
## [PATTERN-001] 回复简洁偏好

**Source:** LEARNING-20241207-001, LEARNING-20241205-003, LEARNING-20241201-002

**Type:** correction

**Pattern:**
用户在多种场景下（天气查询、代码解释、状态报告）都要求"简洁点"、"不要太长"、"直接给答案"

**Impact:**
- 用户满意度下降
- 互动效率降低
- 需要反复纠正

**Proposed Action:**
1. 更新 SOUL.md Decision Priors，加入"简洁回复"原则
2. 在 AGENTS.md Reply Principles 中加入长度检查
3. 默认回复长度控制在 5 行以内，除非被要求详细

**Target File:**
- [x] SOUL.md (Decision Priors - 信息密度)
- [ ] AGENTS.md (Reply Principles - 长度检查)

**Fields:**
- detected_date: 2024-12-07
- recurring_count: 3
- status: pending
```

```markdown
## [PATTERN-002] Gateway 端口冲突

**Source:** LEARNING-20241201-001, LEARNING-20241128-002, LEARNING-20241115-001

**Type:** error

**Pattern:**
多实例部署时，多个 Gateway 尝试绑定同一端口，导致启动失败

**Impact:**
- Gateway 启动失败
- 需要手动检查和修改配置
- 可能影响服务可用性

**Proposed Action:**
1. 在 AGENTS.md Config Change Protocol 中加入多实例注意事项
2. 创建端口检查脚本，启动前自动检测
3. 在 TOOLS.md 记录端口分配规则

**Target File:**
- [ ] AGENTS.md (Config Change Protocol)
- [ ] TOOLS.md (端口分配规则)
- [ ] 创建脚本：scripts/check-port.sh

**Fields:**
- detected_date: 2024-12-01
- recurring_count: 3
- status: detecting
```

---

## 模式升级流程

```
LEARNINGS.md 单项 recurring_count ≥ 3
        ↓
自动添加到 PATTERNS.md
        ↓
分析模式，提出系统更新建议
        ↓
用户确认后执行更新
        ↓
更新对应文件（SOUL.md / AGENTS.md / TOOLS.md）
        ↓
status: completed
```

## 统计

| 状态 | 数量 |
|------|------|
| detecting | 0 |
| pending | 0 |
| completed | 0 |

---

*记住：重复 3 次的错误不是偶然，是系统问题。必须更新系统文件来预防。*
