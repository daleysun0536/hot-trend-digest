# 热搜发推文

将微博、百度、知乎热搜实时抓取、过滤分析，输出适合发 X（Twitter）的140字内格式化内容。

![](https://img.shields.io/badge/Platform-OpenClaw-blue) ![](https://img.shields.io/badge/Platform-Claude%20Code-green) ![](https://img.shields.io/badge/License-MIT-orange)

---

## ✨ 功能特性

- 🔍 **三平台聚合**：微博热搜 + 百度热搜 + 知乎热搜，合并去重
- 🚫 **政治过滤**：涉政内容自动跳过，不进入输出
- 📊 **结构化输出**：平台 / 时间 / 标题 / 正文 / 标签，格式统一
- 🔄 **智能补位**：某平台过滤后不足5条，自动向下延伸取值
- 🌐 **背景补充**：突发事件直提，有前因的联网检索背景
- ✍️ **调性轻松**：输出内容适合直接发 X，口语化有观点

---

## 📋 输出格式

```
🔥 热搜平台：微博
📅 热搜时间：2026-03-27
📌 热搜标题：游客因拍照设备太专业被景区驱赶
📊 热搜排名：微博 #1

河南开封万岁山景区，游客沙先生用专业相机给妻子拍照，被工作人员连续驱赶三次。
景区自2月起禁止"外来商业拍摄"，手机相机可用，但支架/闪光灯不行——自家老公给老婆拍也不行。
一刀切的管理，服务意识在哪里？

#旅游 #消费者权益 #景区乱象 #商拍争议 #开封
```

---

## 🚀 快速开始

### OpenClaw（推荐）

**方法一：SkillHub 安装**
在 QClaw 中直接说"帮我安装热搜发推文技能"

**方法二：手动安装**
```bash
# 将 SKILL.md 放入 skills 目录
cp SKILL.md ~/.qclaw/skills/热搜发推文/SKILL.md
```

**触发方式：**
```
热搜情况
热搜发推
热榜
```

---

### Claude Code

1. 复制 `SKILL.md` 内容到 Claude Code 对话
2. 直接输入"热搜情况"

---

## 📁 项目结构

```
热搜发推文/
├── SKILL.md          # 核心技能定义文件
├── docs/
│   └── DEPLOY.md     # 详细部署指南
├── README.md         # 项目说明（本文）
└── assets/          # 资源文件（可选）
```

---

## 🔧 高级配置

### 修改抓取平台

编辑 `SKILL.md` 中的搜索关键词即可：

```markdown
| 平台 | 搜索关键词 |
|------|-----------|
| 微博 | `微博热搜榜 今日` |
| 百度 | `百度热搜榜 今日` |
| 知乎 | `知乎热搜 今日` |
```

### 添加过滤关键词

在 `SKILL.md` Step 2 中扩展政治类关键词列表。

### 定时自动推送

在 OpenClaw 中配置 Cron Job：

```json
{
  "name": "每日热搜推送",
  "schedule": { "kind": "cron", "expr": "0 9 * * *", "tz": "Asia/Shanghai" },
  "payload": { "kind": "agentTurn", "message": "热搜情况" },
  "sessionTarget": "isolated",
  "delivery": { "mode": "announce" }
}
```

---

## 🤝 贡献

欢迎提交 Issue 和 PR！

---

## 📄 License

MIT
