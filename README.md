# openclaw-workspace-kit

> 复制此文件夹到任意 Agent 的 workspace 即可部署

---

## 文件清单

### 核心文件（8 个）

| 文件 | 用途 | 需要修改 |
|------|------|---------|
| `AGENTS.md` | 操作系统（宪法） | ❌ 否 |
| `BOOTSTRAP.md` | 运行时路由（分类层） | ❌ 否 |
| `SOUL.md` | 行事准则（人格） | ⚠️ **是** — 填写第二部分 |
| `IDENTITY.md` | 身份定义 | ⚠️ **是** — 全部内容 |
| `MEMORY.md` | 长期记忆索引（空模板） | ⚠️ **是** — 随使用填充 |
| `TOOLS.md` | 工具速查 | ⚠️ **是** — 添加服务连接 |
| `USER.md` | 用户信息 | ⚠️ **是** — 全部内容 |
| `HEARTBEAT.md` | 心跳配置（可选） | ⚠️ 可选 |

### 学习系统（2 个）

| 文件 | 用途 | 需要修改 |
|------|------|---------|
| `.learnings/LEARNINGS.md` | 学习记录（含范例） | ❌ 否 |
| `.learnings/PATTERNS.md` | 重复模式追踪（含范例） | ❌ 否 |

### 技能系统（2 个）

| 文件 | 用途 | 需要修改 |
|------|------|---------|
| `skills/memory/SKILL.md` | 记忆写入技能 | ❌ 否 |
| `skills/write-tmp/SKILL.md` | 临时文件路径规则 | ❌ 否 |

### 参考文档（1 个）

| 文件 | 用途 | 需要修改 |
|------|------|---------|
| `reference/feature-requests.md` | 功能需求追踪 | ❌ 否 |

### 空目录（按需填充）

| 目录 | 用途 |
|------|------|
| `scripts/` | 脚本（如需要） |
| `memory/` | 日记文件（自动创建） |
| `notes/areas/` | 主题知识 |
| `notes/resources/` | 工具/服务参考 |

---

## 必须修改的文件（5 个）

### 1. SOUL.md — 第二部分

**位置：** `# 第二部分：请填写 Agent 专用特质`

**填写示例（创作型 Agent）：**
```markdown
# 第二部分：创作特质（Creative Agent 专属）

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

**填写示例（编程型 Agent）：**
```markdown
# 第二部分：编程特质（Coding Agent 专属）

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

### 2. IDENTITY.md — 全部内容

**当前内容：**
```markdown
- **Name:** Coding Master (奥 - 编码大师)
- **Creature:** 顶级编程架构师 + 代码艺术家
- **Vibe:** 严谨、高效、像手术刀一样精准
- **Emoji:** 💻
- **Avatar:** _(可选：填路径或 URL)_

## 核心职责 (One-liner)
为复杂问题设计优雅架构，编写无可挑剔的代码，并传承最佳实践。
```

**修改为：**
```markdown
- **Name:** 你的 Agent 名称
- **Creature:** 你的 Agent 定位
- **Vibe:** 你的 Agent 风格
- **Emoji:** 你的表情符号
- **Avatar:** _(可选)_

## 核心职责 (One-liner)
一句话概括你的 Agent 是做什么的
```

---

### 3. USER.md — 全部内容

**填写你的用户信息：**
```markdown
- **Name:** 用户姓名
- **What to call them:** 怎么称呼
- **Timezone:** 时区（如 Asia/Shanghai）
- **Notes:** 其他信息

## Context
用户关心什么？在做什么项目？什么让他烦？什么让他笑？
```

---

### 4. TOOLS.md — 自定义区域

**当前内容：**
```markdown
## 自定义区域
_（按需添加实际的服务连接、API Token、常用命令）_
```

**填写示例：**
```markdown
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

### 5. MEMORY.md — 随使用填充

**首次部署时是空模板，使用时自动填充。**

**需要手动填充的部分（可选）：**
```markdown
## P0: Personal Preferences & Infrastructure

### Interaction Preferences
- **回复风格:** 高密度、表格优先、结论先行
- **决策风格:** 先做后报，外部操作确认

### Infrastructure
- **Workspace:** /path/to/workspace
- **Shell:** bash
- **OS:** Linux / macOS / Windows
```

---

## 可选修改的文件（1 个）

### HEARTBEAT.md — 心跳任务

**如果不需要心跳检查，留空或删除。**

**填写示例：**
```markdown
# 心跳检查任务

## 每天检查
- [ ] 邮箱有无紧急邮件
- [ ] 日历 24 小时内有无会议
- [ ] 天气（如果要出门）

## 每周检查
- [ ] 项目进度
- [ ] 账单/订阅
```

---

## 部署步骤

```bash
# 1. 复制整个 .workspace 到目标工作区
cp -r .workspace/* /path/to/target-workspace/

# 2. 编辑必须修改的文件（5 个）
#    - SOUL.md（第二部分）
#    - IDENTITY.md
#    - USER.md
#    - TOOLS.md
#    - MEMORY.md（可选）

# 3. 验证部署
ls -la /path/to/target-workspace/
```

---

## 验证清单

部署后检查：

- [ ] `SOUL.md` 第二部分已填写
- [ ] `IDENTITY.md` 已修改为新 Agent 身份
- [ ] `USER.md` 已填写用户信息
- [ ] `TOOLS.md` 已添加服务连接（如需要）
- [ ] 目录结构完整（`.learnings/`, `skills/`, `memory/`, `notes/`）

---

## 总计

**13 个文件 + 4 个目录**

- **必须修改：** 5 个（SOUL.md、IDENTITY.md、USER.md、TOOLS.md、MEMORY.md 可选）
- **无需修改：** 8 个（AGENTS.md、BOOTSTRAP.md、学习系统、技能系统、参考文档）

---

*这套框架是生产级的 Agent 操作系统，包含完整的记忆、进化、执行机制。*
*复制后只需修改 SOUL.md 第二部分和 IDENTITY.md 即可复用核心架构。*
