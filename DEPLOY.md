# 部署指南

## 方式一：OpenClaw（推荐）

### 前置要求
- macOS / Windows / Linux 已安装 [QClaw](https://qclaw.com)（OpenClaw 桌面客户端）
- QClaw 已登录并正常运行

### 安装步骤

**方法 A：通过 SkillHub 安装（推荐）**

1. 在 QClaw 对话中输入：
   ```
   安装技能 热搜发推文
   ```
   或直接说"帮我安装热搜发推文技能"

**方法 B：手动安装**

1. 下载 `.skill` 文件（或从 GitHub Release 下载）
2. 将文件放入 `~/.qclaw/skills/` 目录
   - **macOS/Linux**: `~/.qclaw/skills/`
   - **Windows**: `C:\Users\你的用户名\.qclaw\skills\`
3. 重启 QClaw，或在设置中刷新技能列表

### 验证安装

在 QClaw 中发送：
```
热搜情况
```

如果 Skill 正常工作，会自动抓取微博、百度、知乎热搜并输出格式化内容。

---

## 方式二：Claude Code（Claude Desktop）

### 前置要求
- 已安装 [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- Node.js >= 18

### 安装步骤

1. **创建 Skills 目录**
   ```bash
   mkdir -p ~/Library/Application\ Support/Claude/claude-desk/skills/
   ```

2. **将 SKILL.md 放入目录**
   ```bash
   cp 热搜发推文/SKILL.md ~/Library/Application\ Support/Claude/claude-desk/skills/热搜发推文.md
   ```

3. **配置 Claude Code**
   在 `~/.claudeerc.json` 中添加：
   ```json
   {
     "skills": {
       "热搜发推文": {
         "path": "~/Library/Application Support/Claude/claude-desk/skills/热搜发推文.md"
       }
     }
   }
   ```

4. **重启 Claude Code**，输入 `/热搜发推文` 或直接说"热搜情况"

---

## 方式三：手动复制（通用）

直接将 `SKILL.md` 文件内容复制到任意 Agent 的上下文中使用。

---

## 依赖说明

本 Skill 依赖以下工具，均为 OpenClaw 内置，无需额外安装：

| 工具 | 用途 |
|------|------|
| `online-search` | 联网抓取热搜数据 |
| `browser` | 备用：直接抓取页面内容 |

---

## 常见问题

**Q: 热搜抓取为空怎么办？**
A: 搜索结果来自搜索引擎代理，确保网络畅通。如持续无数据，可稍后重试。

**Q: 政治类内容如何过滤？**
A: Skill 内置政治类关键词过滤规则，涉政话题会自动跳过并向下延伸取值。

**Q: 能定时自动推送吗？**
A: 当前版本为手动触发，如需定时可在 OpenClaw 中配置 Cron 任务。
