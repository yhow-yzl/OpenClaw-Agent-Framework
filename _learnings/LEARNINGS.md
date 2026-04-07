# LEARNINGS.md - 学习改进

> 记录错误、用户纠正、知识缺口、最佳实践等改进机会
> 
> **触发：** AGENTS.md Self-Improvement: `Corrected → _learnings/LEARNINGS.md`

## 格式说明

每笔学习记录使用以下格式：

```markdown
## [LEARNING-YYYYMMDD-XXX] 简短标题

**Type:** [error/correction/knowledge_gap/best_practice/manual_repeat]

**Summary:** 一句话描述学到的东西

**Context:**
什么情况下发现这个学习点

**What Happened:**
实际发生的情况（错误现象/用户纠正内容）

**What I Learned:**
具体学到的知识或方法

**Action Taken:**
基于这个学习采取的行动

**Prevention:**
如何预防同类问题再次发生

**Fields:**
- recurring_count: [次数]
- module: [相关模块]
- priority: [low/medium/high]
- status: [noted/applied/integrated]
- learn_date: [学习日期]
```

## Type 说明

| Type | 说明 | 例子 |
|------|------|------|
| **error** | 指令失败、功能回归、配置错误 | Gateway 启动失败、端口冲突 |
| **correction** | 用户纠正了我的理解或行为 | "回复简洁点"、"不要问直接做" |
| **knowledge_gap** | 发现知识盲点或过时资讯 | 不知道 GitHub API 有 rate limit |
| **best_practice** | 发现更好的做法或流程 | 发现更高效的配置方式 |
| **manual_repeat** | 发现重复手动操作，应该自动化 | 每天都手动检查邮箱 |

## 记录列表

### [LEARNING-20260407-001] 测试写入：临时文件路径错误

**Type:** error

**Summary:** 尝试写入 `/tmp` 路径失败，应使用 `/root/clawd/tmp/`

**Context:**
测试写入流程，创建临时文件

**What Happened:**
- 错误现象：`Error: Path escapes workspace root`
- 尝试路径：`/tmp/output.md`
- 预期结果：成功写入临时文件

**What I Learned:**
1. `/tmp` 不在 workspace 内，会被阻止
2. 正确路径是 `/root/clawd/tmp/`
3. 需要先创建目录：`mkdir -p /root/clawd/tmp`

**Action Taken:**
1. 创建技能文件：`skills/write-tmp/SKILL.md`
2. 记录正确路径规则

**Prevention:**
已创建 `skills/write-tmp/SKILL.md`，AI 会读取此技能

**Fields:**
- recurring_count: 1
- module: filesystem
- priority: medium
- status: applied
- learn_date: 2026-04-07

---

## 范例记录（仅供参考，不要删除）

```markdown
## [LEARNING-20241201-001] Gateway 端口冲突

**Type:** error

**Summary:** OpenClaw Gateway 无法绑定到指定端口

**Context:**
执行 `openclaw gateway start` 启动第二个实例

**What Happened:**
- 错误现象：Error: listen EADDRINUSE :::8080
- 预期结果：Gateway 正常启动在 8080 端口
- 根本原因：端口 8080 已被另一个实例占用

**What I Learned:**
1. OpenClaw 多实例部署需要使用不同端口
2. 启动前应该检查端口占用情况
3. 配置变更应该先备份

**Action Taken:**
1. 检查端口使用状况：`lsof -i :8080`
2. 修改配置使用不同端口：8081
3. 备份原配置：`cp openclaw.json openclaw.json.bak`

**Prevention:**
在 AGENTS.md Config Change Protocol 中加入多实例部署注意事项

**Fields:**
- recurring_count: 1
- module: gateway
- priority: medium
- status: resolved
- learn_date: 2024-12-01
```

```markdown
## [LEARNING-20241201-002] 用户偏好：简洁回复

**Type:** correction

**Summary:** 用户偏好简洁直接的回覆，不要冗长的说明

**Context:**
回覆天气查询时提供了详细的解释，用户说"太长了，简单点就好"

**What Happened:**
- 用户纠正："太长了，简单点就好"
- 我的回复超过了用户期望的长度

**What I Learned:**
1. 日常查询只要核心资讯
2. 技术解释只有在被询问时才提供
3. 可以用"需要详细说明吗？"来确认

**Action Taken:**
1. 更新 SOUL.md 加入简洁回覆偏好
2. 调整常用查询的回应模式

**Prevention:**
SOUL.md Decision Priors 已加入"高密度输出"原则

**Fields:**
- recurring_count: 1
- module: interaction
- priority: high
- status: integrated
- learn_date: 2024-12-01
```

```markdown
## [LEARNING-20241201-003] GitHub API Rate Limit 处理

**Type:** knowledge_gap

**Summary:** 学会 GitHub API 的 rate limiting 机制和最佳实践

**Context:**
执行批次 GitHub 操作时遇到 403 错误，原来不知道有 rate limit

**What Happened:**
- 错误现象：HTTP 403 Forbidden
- 原因：超过 GitHub API 每小时 5000 次请求限制

**What I Learned:**
1. GitHub API 有每小时 5000 次请求限制（认证用户）
2. 应该检查 X-RateLimit-Remaining header
3. 可以用 conditional requests 减少 rate limit 消耗
4. 批次操作应该加入适当的延迟

**Action Taken:**
1. 更新 GitHub 相关脚本加入 rate limit 检查
2. 在 TOOLS.md 中记录 GitHub API 使用注意事项
3. 实作 rate limit aware 的 GitHub 操作函数

**Prevention:**
在 TOOLS.md GitHub 部分加入 rate limit 注意事项

**Fields:**
- recurring_count: 1
- module: github
- priority: medium
- status: applied
- learn_date: 2024-12-01
```

## 累积机制

当 `recurring_count ≥ 3` 时：

1. **自动汇总** → 更新 `_learnings/PATTERNS.md`
2. **提议升级** → 根据类型提议更新对应文件：
   - `correction` → 提议更新 `SOUL.md` 或 `AGENTS.md`
   - `error` → 提议更新 `Config Change Protocol` 或 `Red Lines`
   - `knowledge_gap` → 提议更新 `TOOLS.md` 或 `notes/`
   - `best_practice` → 提议更新 `AGENTS.md` 或 `SOUL.md`
   - `manual_repeat` → 提议创建自动化脚本

## 与 AGENTS.md 的对应关系

| AGENTS.md 章节 | 本文件记录类型 | 升级目标 |
|--------------|--------------|---------|
| `Self-Improvement` | 全部类型 | `MEMORY.md` (recurring ≥ 3) |
| `Reliability (Four Defense Lines)` | error | `Config Change Protocol` |
| `Reply Principles / Friction Check` | correction | `SOUL.md Decision Priors` |
| `Config Change Protocol` | error | `AGENTS.md Config Change Protocol` |
| `Memory Retrieval Strategy` | knowledge_gap | `TOOLS.md` 或 `notes/` |

---

*记住：每个纠正都是改进的机会。记录下来，避免重复同样的错误。*
*累积到 3 次 → 提议更新系统文件（SOUL.md / AGENTS.md）*
