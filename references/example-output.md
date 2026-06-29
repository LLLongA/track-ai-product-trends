# Example Output Pattern

Use this as a compact shape for daily reports.

## Bottom Line

- AI coding and workflow automation are the strongest repeated launch clusters today.
- Skill 日榜 adds workflow packaging signals that GitHub misses.
- GitHub Trending Daily shows short-term developer attention; GitHub new-hot shows recent breakout projects; skill 日榜 shows packaged capability signals.

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

## skill 日榜

skill 日榜 window: latest completed daily leaderboard.

| 排名 | 项目 | 一句话定位 | 产品设计分 |
|---:|---|---|---:|
| 1 | Example Agent Skill | 面向 AI agent 的评估、排障和执行增强 skill | 4.3/5 |
| 2 | Example Workflow Skill | 面向工作流自动化的可复用 skill 打包 | 4.0/5 |

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

## skill 日榜分项目 quick-pm 分析

### 1. Example Agent Skill：4.3/5

定位：面向 AI agent 的评估、定位问题和执行增强 skill。
用户价值：把一段分散的 agent 经验沉淀成可复用工作流，缩短试错时间。
差异化：切入 skill packaging，而不是只做一个仓库或一次性 prompt。
反向思考：skill 日榜热度只能说明当日关注度，不能证明长期复用和团队采用。
建议：先验证 linked repo、说明文档、输入输出边界和真实使用案例，再决定是否深挖。

## Social Card Order

When this report is turned into social cards, the default file order should be:

1. `xhs-01-summary.png`
2. `xhs-02-github-trending-1.png`
3. `xhs-03-github-trending-2.png`
4. `xhs-04-github-new-hot-1.png`
5. `xhs-05-github-new-hot-2.png`
6. `xhs-06-skill-daily-1.png`
7. `xhs-07-skill-daily-2.png`

## Social Card Content Mapping

Use this fixed mapping when turning the Markdown report into social cards:

### `xhs-01-summary.png`

- 这是什么报告
- 今日 2-3 条趋势判断
- 今天最值得跟踪的 3-5 个项目 / skills

### `xhs-02-github-trending-1.png`

- 覆盖 GitHub Trending 的 `01-05`
- 每个项目都要直接带：
  - `项目名`
  - `产品设计分`
  - `定位`
  - `价值`
  - `差异化`
  - `建议`

### `xhs-03-github-trending-2.png`

- 覆盖 GitHub Trending 的 `06-10`
- 延续同样的高密度合并结构

### `xhs-04-github-new-hot-1.png`

- 覆盖 GitHub 新增热门的 `01-05`
- 每个项目都要直接带：`项目名 / 产品设计分 / 定位 / 价值 / 差异化 / 建议`

### `xhs-05-github-new-hot-2.png`

- 覆盖 GitHub 新增热门的 `06-10`
- 延续同样的高密度合并结构

### `xhs-06-skill-daily-1.png`

- 覆盖 skill 日榜的 `01-05`
- 每个项目都要直接带：`项目名 / 产品设计分 / 定位 / 价值 / 差异化 / 建议`

### `xhs-07-skill-daily-2.png`

- 覆盖 skill 日榜的 `06-10`
- 延续同样的高密度合并结构

Hard rule:

- 只要榜单列了 10 个项目，对应两张 merged cards 就必须把 `01-10` 全部覆盖。
- 不允许只做前 5 个项目的进一步点评。
- 不要退回成“单独榜单页 + 单独 detail 页”的默认结构。

Card label tone:

- 页面上的几个字尽量客观、克制。
- 可以直接跟内容走，比如：`GitHub Trending Daily`、`GitHub 新增热门`、`skills.sh`、`Top 10`、`01-05`、`06-10`
- 避免：`最强信号`、`下半场信号`、`边缘但重要` 这类太“起标题感”的说法

Dense layout cues:

- `项目名` 要明显大于四行说明，承担扫描入口。
- `定位` 略轻，和 `价值 / 差异化 / 建议` 间隔开一点。
- `建议` 需要更像结论，通常给一点额外上间距，并让标签更醒目。
- 项目之间不要松散，但页面底部也不要出现大块无意义留白。
