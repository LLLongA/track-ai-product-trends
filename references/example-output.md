# Example Output Pattern

Use this as a compact shape for daily reports.

## Bottom Line

- AI coding and workflow automation are the strongest repeated launch clusters today.
- Product Hunt adds non-open-source product packaging signals that GitHub misses.
- GitHub Trending Daily shows short-term developer attention; GitHub new-hot shows recent breakout projects; Product Hunt shows packaged launch signals.

## GitHub Trending Daily 榜

| 排名 | 项目 | 一句话定位 | 产品设计分 |
|---:|---|---|---:|
| 1 | example/trending-agent | 今日 GitHub Trending 上的 agent 工作流工具 | 4.1/5 |
| 2 | example/trending-model | 今日 GitHub Trending 上的 AI 模型/工具项目 | 3.9/5 |

## GitHub 新增热门项目榜

GitHub 新增热门口径：created:>近30天 + AI/LLM/agent/MCP/coding keywords + sort=stars，并按产品相关性筛选重排。

| 排名 | 项目 | 一句话定位 | 产品设计分 |
|---:|---|---|---:|
| 1 | example/new-hot-agent | 面向 coding agent 的运行与评估工具 | 4.2/5 |
| 2 | example/new-hot-context | 面向 AI 编程的代码上下文治理层 | 4.0/5 |

## Product Hunt 产品榜

Product Hunt window: previous-day / last-24-hour leaderboard.

| 排名 | 产品 | 一句话定位 | 产品设计分 |
|---:|---|---|---:|
| 1 | Example Agent Eval | 面向 AI agent 的评估、定位问题和修复工具 | 4.3/5 |
| 2 | Example MCP App | 面向 MCP 应用的开发框架 | 4.0/5 |

## GitHub Trending Daily 分项目 quick-pm 分析

### 1. example/trending-agent：4.1/5

定位：今日 GitHub Trending 上的 agent 工作流工具。
用户价值：代表当天开发者注意力，适合判断短期传播和技术兴趣。
差异化：Trending 信号强，但需要和 README、代码、竞品证据交叉验证。
反向思考：Trending 热度可能来自话题性，不一定代表长期产品价值。
建议：适合作为今日观察入口，不要和新增热门榜混用。

## GitHub 新增热门分项目 quick-pm 分析

### 1. example/new-hot-agent：4.2/5

定位：近 30 天新增并快速获得 stars 的 coding agent 运行与评估工具。
用户价值：帮助团队发现 agent 执行链路中的错误、上下文遗漏和质量风险。
差异化：不是单纯代码生成，而是补足 agent 上线前后的评估与治理层。
反向思考：新项目 star 增长快不等于产品成熟，需要验证文档、集成、维护节奏和真实使用案例。
建议：值得重点跟踪，适合进一步做 quick-pm 深挖。

## Product Hunt 分产品 quick-pm 分析

### 1. Example Agent Eval：4.3/5

定位：面向 AI agent 的评估、定位问题和修复工具。
用户价值：解决 agent 从 demo 到生产过程中的可靠性、调试和信任问题。
差异化：切入 agent evaluation，而不是再做一个通用 agent wrapper。
反向思考：Product Hunt 热度只能说明 launch momentum，不能证明留存和生产可用性。
建议：先观察官网、定价、集成和真实客户案例，再决定是否深挖。

## Social Card Order

When this report is turned into social cards, the file order should be:

1. `xhs-01-summary.png`
2. `xhs-02-github-trending-daily.png`
3. `xhs-03-github-trending-detail-1.png`
4. `xhs-04-github-trending-detail-2.png`
5. `xhs-05-github-new-hot.png`
6. `xhs-06-github-new-hot-detail-1.png`
7. `xhs-07-github-new-hot-detail-2.png`
8. `xhs-08-product-hunt.png`
9. `xhs-09-product-hunt-detail-1.png`
10. `xhs-10-product-hunt-detail-2.png`
