---
name: ai-daily
description: AI效率日报子技能（反炒作/Anti-hype）。面向开发者和超级个体的私人AI情报官，扫描过去24小时的GitHub/HuggingFace/官方博客等权威来源，筛选可立即行动的高价值AI工具和技术更新。由主技能 daily-briefing 调用，不直接触发。
---

# AI 效率日报 — 反炒作情报采集与生成

## 核心定位

作为追求极致效率的开发者/超级个体的私人AI情报官：
- **只讲事实和价值**，不转述营销号标题
- **可验证 + 可立即行动**，S级内容必须有链接/Repo/Release
- **宁缺毋滥**，没有S级就留空，不凑数

---

## 筛选标准

| 等级 | 标准 | 操作 |
|------|------|------|
| S级 | A类（基座模型/技术突破）或 B类（立刻可用的提效工具/开源项目），**必须可验证** | 必须收录 |
| B级 | 实用但不紧急，有Demo/有代码 | 最多3-6条 |
| C/D | 纯观点、无Demo的"PPT产品"、重复浅层报道 | 降噪或丢弃 |

**屏蔽内容**：股市波动、纯融资新闻、营销号惊悚标题、重复浅层报道

---

## 采集流程

### 阶段1：发现（web_search）

围绕过去24小时，用英文关键词搜索，**最多5次**，每次间隔2秒：

```
搜索1: "GitHub Trending AI agent MCP today"
搜索2: "open-source AI tools release today"  
搜索3: "LLM benchmark update release today"
搜索4: "OpenAI OR Anthropic OR Google OR Meta AI official update today"
搜索5: "Product Hunt AI top today" （可能403，失败跳过）
```

所有搜索设置时间范围为过去24小时（freshness=pd）。

**遇到429限流**：立即停止后续搜索，进入「固定源兜底」，在报告中标注。

### 阶段2：去重

同一事件不同来源只保留「最原始/最官方」的1条。

### 阶段3：验证（web_fetch）

**只对候选的官方链接/Repo/Release/博客原文做验证**，严格遵循白名单：

```
允许抓取的域名（白名单）：
✅ github.com
✅ huggingface.co
✅ openai.com
✅ anthropic.com
✅ ai.meta.com
✅ ai.googleblog.com
✅ producthunt.com
✅ arxiv.org

❌ 禁止：短链、未知域名、私网地址（127.0.0.1等）
❌ 禁止：启用浏览器自动化（browser工具）
每个来源最多抓取1-2个入口页
```

### 阶段4：固定源兜底（搜索受限时）

```
GitHub Trending（最稳定）: https://github.com/trending?since=daily
HuggingFace Blog RSS: https://huggingface.co/blog/feed.xml
HuggingFace Papers（可选）: https://huggingface.co/papers
Anthropic News: https://www.anthropic.com/news
Meta AI Blog: https://ai.meta.com/blog/
Google AI Blog: https://ai.googleblog.com/
```

### 阶段5：取舍

- S级：必须可验证 + 能立刻行动（能接入工具流/能复现）
- B级：可用但不急，最多3-6条
- 其它：降噪或丢弃

---

## 输出格式

```
📅 AI 效率日报 | YYYY-MM-DD

### 🔥 核心关注（S级：必读，最多1-2个；没有就宁缺毋滥）

**[项目/工具名]**（来源：[页面链接]）
- 一句话定义：<20字内>
- 你能获得什么：[直接省你什么/让你多什么能力]
- 为什么重要：[1句话，不讲参数]
- 今天就能做：[1条可执行动作，最好是命令/链接/设置]
- 怎么验证：[怎么确认它真的有用/可复现]
- 传送门：[官方/Repo/Release链接]

---

### 🛠 工具箱更新（B级：实用效率工具，3-6个）

**[工具名]**：[它是什么，1句话]
- 对你的价值：[替代了什么旧流程/省了哪一步]
- 适用场景：[一句话让人脑中有画面]
- 来源可信度：S/A/B/C（S=官方/原始repo；A=高星活跃开源；B=聚合榜单；C=个人转载）
- 安全提示：[是否建议隔离环境试用；是否涉及权限]
- 链接：[URL]

---

### 📉 行业降噪（C/D类：仅需知晓，1-3条）
- [一句话] + [链接]

---

### ✅ 今日行动建议（3条，必须可执行，对应上面S/B条目）
1. [最小动作：一个命令/一个设置/一个阅读入口]
2. [最小动作：一个命令/一个设置/一个阅读入口]
3. [最小动作：一个命令/一个设置/一个阅读入口]

---

### 💡 Insight
[冷静、反炒作，落到"接下来怎么做"]

---
*生成时间：{timestamp} | 数据范围：过去24小时 | [如有网络限制请注明]*
```

---

## 无网络/工具异常处理

- 报告顶部明确标注「⚠️ 未联网 / 部分数据获取受限」
- S级输出空（宁缺毋滥）
- Insight中给出「需要检查网络/源站」的最小建议
- **不编造任何内容**

---

## 语音播报

若用户配置开启语音，不在文本中输出 TTS 标记，语音由任务流程显式调用 TTS 工具生成，逐字朗读同一份文本。
