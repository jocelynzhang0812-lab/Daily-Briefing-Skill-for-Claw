# 数据源参考手册

## 通用新闻数据源

### 国内
| 来源 | 类型 | 适用日报 |
|------|------|----------|
| 新华社 | 政策/要闻 | 通用 |
| 人民日报 | 政策 | 通用 |
| 财联社 | 财经快讯 | 通用/股票 |
| 澎湃新闻 | 综合 | 通用 |
| 21世纪经济报道 | 财经 | 通用/股票 |
| 36氪 | 科技/创投 | 通用/投资 |
| 虎嗅 | 科技 | 通用 |
| IT之家 | 科技 | 通用/AI |
| 观察者网 | 国际/政策 | 通用 |
| 环球网 | 国际 | 通用 |
| 雪球 | 股票 | 股票 |
| 东方财富 | 股票/行情 | 股票 |
| 同花顺 | 股票/行情 | 股票 |
| 投中网 | VC/PE | 投资 |
| 创业邦 | 创投 | 投资 |
| IT桔子 | 融资数据 | 投资 |

### 海外
| 来源 | 类型 | 适用日报 |
|------|------|----------|
| TechCrunch | 科技/融资 | 通用/投资/AI |
| Crunchbase News | 融资数据 | 投资 |
| Bloomberg | 财经 | 通用/投资 |
| Reuters | 综合 | 通用 |
| GitHub Trending | 开源/AI | AI效率 |
| HuggingFace Blog | AI研究 | AI效率 |
| Product Hunt | AI产品 | AI效率 |
| arXiv | 学术论文 | AI效率（可选）|

---

## RSS 订阅推荐

```
# 科技/AI
TechCrunch: https://techcrunch.com/feed/
Ars Technica: https://feeds.arstechnica.com/arstechnica/index
36氪: https://36kr.com/feed
HuggingFace Blog: https://huggingface.co/blog/feed.xml
OpenAI Blog RSS: https://openai.com/blog/rss.xml
Anthropic News: https://www.anthropic.com/news
Meta AI Blog: https://ai.meta.com/blog/
Google AI Blog: https://ai.googleblog.com/

# 财经
财联社: 需通过API或爬虫获取
Bloomberg: 付费订阅
```

---

## 官方数据来源（不可替代）

- **A股公告**：巨潮资讯 http://www.cninfo.com.cn/
- **上交所公告**：http://www.sse.com.cn/
- **深交所公告**：http://www.szse.cn/
- **国家政策**：国务院 http://www.gov.cn/
- **外汇数据**：中国人民银行 http://www.pbc.gov.cn/

---

## 搜索关键词模板

### 通用日报
```
"{领域} 今日新闻 {YYYY-MM-DD}"
"今日财经要闻 {YYYY-MM-DD}"
"科技 AI 最新动态 {YYYY-MM-DD}"
```

### 投资日报
```
"融资 {YYYY-MM-DD} 亿元"
"startup funding {YYYY-MM-DD} million"
"VC investment news {YYYY-MM-DD}"
```

### 股票日报
```
"{股票名称} {代码} 今日行情 {YYYY-MM-DD}"
"{股票名称} 最新公告 {YYYY-MM-DD}"
"北向资金 今日 {YYYY-MM-DD}"
```

### AI效率日报
```
"GitHub Trending AI agent today"
"open-source AI tools release today"
"LLM benchmark update today"
"OpenAI Anthropic Google Meta official update today"
```
