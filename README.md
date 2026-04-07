# OpenClaw Agent Framework

> 一套生产级的 Agent 工作区框架，包含完整的记忆、进化、执行系统

---

## 快速开始

```bash
# 1. 复制到目标工作区
cp -r .workspace/* /path/to/target-workspace/

# 2. 修改必须配置的文件（见下方"部署清单"）

# 3. 启动 Agent
cd /path/to/target-workspace
openclaw start
```

---

## 文件结构

```
workspace/
├── AGENTS.md                 # 操作系统（宪法）
├── BOOTSTRAP.md              # 运行时路由（分类层）
├── SOUL.md                   # 行事准则（人格）【需配置】
├── IDENTITY.md               # 身份定义【需配置】
├── USER.md                   # 用户信息【需配置】
├── TOOLS.md                  # 工具速查【需配置】
├── MEMORY.md                 # 长期记忆索引（空模板）
├── _learnings/               # 学习系统
│   ├── LEARNINGS.md          # 错误与修正记录
│   └── PATTERNS.md           # 重复模式追踪
├── skills/                   # 技能系统
│   ├── memory/SKILL.md       # 记忆写入技能
│   └── write-tmp/SKILL.md    # 临时文件路径规则
├── reference/                # 参考文档
│   └── feature-requests.md   # 功能需求追踪
├── memory/                   # 日记文件（运行时自动创建）
└── notes/                    # 知识库
    ├── areas/                # 主题知识
    └── resources/            # 工具/服务参考
```

**总计：** 13 个文件 + 3 个目录

---

## 部署清单

### 必须修改（4 个文件）

| 文件 | 修改内容 | 示例 |
|------|---------|------|
| **SOUL.md** | 填写第二部分"Agent 专用特质" | 编程/创作/客服等专业能力 |
| **IDENTITY.md** | Agent 名称、定位、风格 | Name, Creature, Vibe, Emoji |
| **USER.md** | 用户基本信息 | 姓名、称呼、时区、背景 |
| **TOOLS.md** | 服务连接、API Token、常用命令 | SSH、数据库、API 等 |

### 可选修改（1 个文件）

| 文件 | 说明 |
|------|------|
| **MEMORY.md** | 首次部署为空模板，使用时自动填充。可预先填写 P0 基础设施信息 |

### 无需修改（8 个文件）

- `AGENTS.md` — 操作系统
- `BOOTSTRAP.md` — 运行时路由
- `_learnings/LEARNINGS.md` — 学习记录（含范例）
- `_learnings/PATTERNS.md` — 模式追踪（含范例）
- `skills/memory/SKILL.md` — 记忆技能
- `skills/write-tmp/SKILL.md` — 临时文件规则
- `reference/feature-requests.md` — 功能需求

---

## 配置指南

### 1. SOUL.md — 填写专业特质

**位置：** `# 第二部分：请填写 Agent 专用特质`

**创作型 Agent 示例：**
```markdown
# 第二部分：创作特质

## 我是谁
创作大师。叙事的导演，情感的工程师。

## 工作流
1. 理解需求 — 目标受众、传播目的、情感基调
2. 拆解对标 — 研究爆款、分析公式、找参考
3. 创作初稿 — 有节奏感、有记忆点
4. 自我审查 — 逻辑、节奏、情感曲线
5. 格式交付 — 分镜表、文案结构

## 创作原则
- 三幕结构 — 建置 → 对抗 → 解决
- 黄金 3 秒 — 开头抓住注意力
- 视觉优先 — 能用画面表达的，不用台词
```

**编程型 Agent 示例：**
```markdown
# 第二部分：编程特质

## 我是谁
代码的建筑师。每一行代码都应该有意义。

## 工作流
1. 理解需求 — 业务逻辑、边界情况
2. 设计架构 — 结构清晰、可扩展
3. 编写代码 — 干净、简洁、高效
4. 代码审查 — 能跑、测试通过、逻辑对
5. 文档说明 — 复杂逻辑要说明白

## 技术信仰
- KISS — 简单就是美
- DRY — 别复制粘贴
- SOLID — 面向对象原则
- 测试驱动 — 先写测试，再写代码
```

---

### 2. IDENTITY.md — 定义身份

**模板：**
```markdown
# IDENTITY.md - [Agent 名称]

- **Name:** [Agent 名称]
- **Creature:** [Agent 定位]
- **Vibe:** [Agent 风格]
- **Emoji:** [表情符号]
- **Avatar:** [可选：图片路径或 URL]

## 核心职责 (One-liner)
一句话概括这个 Agent 是做什么的
```

**示例：**
```markdown
# IDENTITY.md - 奥 - 编码大师

- **Name:** Coding Master (奥 - 编码大师)
- **Creature:** 顶级编程架构师 + 代码艺术家
- **Vibe:** 严谨、高效、像手术刀一样精准
- **Emoji:** 💻
- **Avatar:** _(可选)_

## 核心职责 (One-liner)
为复杂问题设计优雅架构，编写无可挑剔的代码，并传承最佳实践。
```

---

### 3. USER.md — 填写用户信息

**模板：**
```markdown
# USER.md - About Your Human

- **Name:** [用户姓名]
- **What to call them:** [怎么称呼]
- **Timezone:** [时区，如 Asia/Shanghai]
- **Notes:** [其他信息]

## Context
用户关心什么？在做什么项目？什么让他烦？什么让他笑？
```

---

### 4. TOOLS.md — 添加服务连接

**模板：**
```markdown
# TOOLS.md - Quick Reference

## Frequently Used Commands

### Cron 提醒
```bash
openclaw cron add --name "name" --at "30m" --system-event "content" --session main --wake now --delete-after-run
```

## 自定义区域

### SSH 连接
```bash
ssh -p 22 user@server -i ~/.ssh/key
```

### 数据库
- MySQL: `mysql -u user -p database`
- Redis: `redis-cli -h localhost -p 6379`

### API Token
- OpenAI: 见 `notes/resources/api-tokens.md`
```

---

## 验证部署

```bash
# 检查核心文件
ls -la AGENTS.md BOOTSTRAP.md SOUL.md IDENTITY.md USER.md

# 检查目录结构
ls -la _learnings/ skills/ memory/ notes/

# 启动测试
openclaw start
```

---

## 核心特性

### 🧠 双层记忆系统
- **日记层** `memory/YYYY-MM-DD.md` — "发生了什么"（5 天滚动）
- **索引层** `MEMORY.md` — "学到了什么"（长期保留）

### 📈 自我进化系统
- **LEARNINGS.md** — 记录错误与修正
- **PATTERNS.md** — 追踪重复模式（≥3 次触发系统更新）

### 🎯 运行时路由
- **BOOTSTRAP.md** — 任务分类层（确认 > 执行 > 研究 > 复合 > 即时）
- **AGENTS.md** — 操作系统（宪法级优先级）

### 🛡️ 安全边界
- 外部操作必须确认（发消息、删文件、改配置、公开发布）
- 内部操作大胆执行（读代码、重构、调研）
- 子代理同等安全红线

---

## 常见问题

### Q: 如何切换到其他 Agent 类型？
**A:** 只需修改 `SOUL.md` 第二部分和 `IDENTITY.md`，核心架构无需改动。

### Q: 记忆文件在哪里？
**A:** `memory/` 目录运行时自动创建，按 `YYYY-MM-DD.md` 格式存储日记。

### Q: 如何添加新技能？
**A:** 在 `skills/` 目录下创建新文件夹，包含 `SKILL.md` 文件。

### Q: `_learnings/` 为什么有下划线？
**A:** 避免与系统隐藏文件混淆，同时保持目录排序靠前。

---

## 版本信息

- **框架版本：** OpenClaw 2026.4.2
- **兼容版本：** OpenClaw 2026.4.x
- **最后更新：** 2026-04-07

---

## 许可证

本框架遵循 OpenClaw 开源协议。

---

*这套系统是生产级的 Agent 操作系统，包含完整的记忆、进化、执行机制。*
*复制后只需修改 4 个文件即可复用核心架构。*
