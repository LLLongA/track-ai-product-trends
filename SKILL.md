name: track-ai-product-trends
description: Track the latest AI product trends from GitHub Trending Daily, GitHub new-hot repositories, and the skill daily leaderboard. Use this skill when the user asks for AI product trend tracking, daily AI product radar, new AI project recommendations, GitHub/skill AI analysis, or product/opportunity scoring for emerging AI tools.
---

# Track AI Product Trends

## Purpose

Create a repeatable AI product trend radar for product managers, founders, investors, and content creators. The skill turns noisy daily signals into ranked recommendations with product-design and opportunity scores.

## Default Scope

Use these sources by default unless the user narrows the request:

1. GitHub Trending: daily developer attention.
2. GitHub new-hot repo榜: recently created repositories with unusually high traction.
3. Skill 日榜: recent skill launches and packaging signals inside the skill ecosystem.

Optional later sources: Hacker News Show HN, Hugging Face Trending, Reddit/HN comments, Chrome Web Store/App Store reviews, YC launches, funding/news, and Chinese communities.

## When To Use Skill 日榜

Use skill 日榜 as a productization and workflow-packaging signal, not as final proof of product quality.

Default skill 日榜 window:
- Use the near-24-hour window, normally the most recent completed `skill 日榜` relative to the report date.
- If the skill platform's same-day ranking is still moving, prefer the latest completed daily snapshot unless the user explicitly asks for an intraday view.
- State the exact date used, e.g. `skill 日榜 window: 2026-06-25 daily leaderboard.`

Skill 日榜 is useful for:
- launch positioning, screenshots, concise capability packaging, and maker narrative,
- detecting which AI capabilities are being productized into reusable skills,
- finding workflow-layer innovation missed by GitHub repositories alone.

Treat skill 日榜 with caution when:
- the daily list is still young and the ranking is volatile,
- the listing page is sparse and only gives short descriptions without real usage evidence,
- the skill has launch polish but weak proof of repeat use or durable workflow value.

Best practice: use the latest completed skill 日榜 as the main source, then use the skill page itself, linked repo/site/docs, and adjacent launch context only for validation.

## Workflow

1. Set date and market context.
- State the exact date and timezone if using daily signals.
- For volatile data, browse or query live sources.

2. Build candidate pool.
- Collect GitHub Trending AI-related repos.
- Collect GitHub new-hot repos using GitHub Search API or search queries, normally `created:>recent_date` + AI/LLM/agent/MCP/coding keywords + `sort=stars`.
- Collect skill 日榜 candidates from the latest completed daily leaderboard, prioritizing AI-related skills, agent workflows, productivity automations, creator tools, and developer tooling.
- Deduplicate by product/repo/domain.

3. Classify each candidate.
- Type: repo, product, model, agent, workflow, infra, app, plugin, content/community signal.
- User: developer, PM/designer, sales/marketing, support, creator, consumer, enterprise ops, founder.
- Category: coding, agent infra, voice, meeting, search, media, automation, data, design, vertical SaaS, other.

4. Analyze evidence.
- For GitHub repos, use `analyze-open-source-repo` quick-pm when the user asks for repo-level analysis or when a repo enters the top shortlist.
- For skill 日榜 candidates, read the skill page plus linked repo/site/docs/examples if available.
- Separate facts from inference. Include confidence: high, medium, or low.

5. Score and rank.
- Score each candidate with the five-dimension model below.
- Produce `Product Design Score` and `Opportunity Score`, both 0-5.
- Rank by opportunity first unless the user asks for pure design quality.

6. Produce recommendations.
- Mark each candidate as `deep-dive`, `watch`, or `pass`.
- Include why now, why it matters, and what evidence would change the score.

## Five-Dimension Scoring Model

Use 0-5 for each dimension, then combine into the final scores.

1. Problem clarity and ICP fit
- Is the target user concrete?
- Is the job-to-be-done clear within 10 seconds?

2. User pain and value intensity
- Is the problem frequent, expensive, time-consuming, or trust-sensitive?
- Does AI create a visible step-change over the old workflow?

3. Differentiation and defensibility
- Is this meaningfully different from existing products?
- Is the advantage workflow/data/distribution-based, not only "uses AI"?

4. Adoption path and product experience
- Is setup easy?
- Is time-to-value short?
- Are integrations, onboarding, demos, docs, and pricing clear enough?

5. Timing and market signal
- Is there evidence from stars, vote/comment velocity, community discussion, recent launches, model/platform changes, or user behavior?
- Is the signal fresh and likely to persist?

Suggested weighting:
- Product Design Score: clarity 25%, value 25%, differentiation 20%, adoption 20%, timing 10%.
- Opportunity Score: value 25%, timing 25%, differentiation 20%, market signal 20%, adoption 10%.

Score interpretation:
- 4.5-5.0: strong candidate for immediate deep-dive.
- 3.8-4.4: promising; monitor or analyze competitors.
- 3.0-3.7: useful but likely incremental, narrow, or weakly differentiated.
- 2.0-2.9: interesting signal but weak product shape.
- 0-1.9: skip unless it reveals a broader trend.

## Output Format

For daily reports, use this structure:

1. Bottom line
- 3-5 bullets on today's AI product trend pattern.

2. GitHub Trending Daily 榜
- Keep GitHub and skill 日榜 in separate tables.
- Keep GitHub Trending Daily and GitHub new-hot in separate tables.
- Use `github.com/trending?since=daily` or another explicit GitHub Trending daily source.
- If GitHub Trending cannot be parsed or accessed, still include the section and state: `GitHub Trending Daily 数据获取失败，本次不混用新增热门项目替代。`
- Table columns: 排名, 项目, 一句话定位, 产品设计分.

3. GitHub 新增热门项目榜
- Use recently created repositories, usually `created:>近30天` or a concrete date such as `created:>2026-06-01`, filtered by AI/LLM/agent/MCP/coding keywords and sorted by stars.
- Add a one-line note before the table with the exact data口径, e.g. `GitHub 新增热门口径：created:>2026-06-01 + AI/LLM/agent/MCP/coding keywords + sort=stars，并按产品相关性筛选重排。`
- Table columns: 排名, 项目, 一句话定位, 产品设计分.

4. Skill 日榜
- Use the latest completed skill 日榜 by default.
- When the user explicitly wants `skills.sh`, treat `https://www.skills.sh/trending` as the primary source and `https://www.skills.sh/hot` as a secondary recency signal.
- For `skills.sh` mode, do not mechanically copy the raw Hot ranking into the final table. Use `Trending` as the main ranking base and use `Hot` only to promote still-active candidates or positive-change newcomers.
- If the top of `Trending` or `Hot` is dominated by the same publisher or near-identical media skills, deduplicate aggressively and keep only the most representative 1-2 entries from that cluster.
- Table columns: 排名, 项目, 一句话定位, 产品设计分.
- Add a one-line note before the table with the exact skill 日榜 date/window used.

5. GitHub Trending Daily 分项目 quick-pm 分析
For each GitHub Trending Daily shortlisted candidate, use this compact Chinese structure:
- `N. owner/repo：X.X/5`
- `定位：...`
- `用户价值：...`
- `差异化：...`
- `反向思考：...`
- `建议：...`
- If the ranking table lists 10 items, this analysis section should also cover all 10 items unless the user explicitly asks for a shorter shortlist.

6. GitHub 新增热门分项目 quick-pm 分析
For each GitHub shortlisted candidate, use this compact Chinese structure:
- `N. owner/repo：X.X/5`
- `定位：...`
- `用户价值：...`
- `差异化：...`
- `反向思考：...`
- `建议：...`
- If the ranking table lists 10 items, this analysis section should also cover all 10 items unless the user explicitly asks for a shorter shortlist.

7. Skill 日榜分项目 quick-pm 分析
For each skill 日榜 shortlisted candidate, use the same compact Chinese structure:
- `N. Skill Name：X.X/5`
- `定位：...`
- `用户价值：...`
- `差异化：...`
- `反向思考：...`
- `建议：...`
- If the ranking table lists 10 items, this analysis section should also cover all 10 items unless the user explicitly asks for a shorter shortlist.

8. Trend clusters
- Group candidates into themes such as coding agents, AI voice, workflow automation, agent infra, AI content production, AI search, vertical AI SaaS.

9. Follow-up queue
- Which repos should be analyzed with `analyze-open-source-repo` quick-pm.
- Which skill 日榜项目 need linked repo/site/docs validation.
- Which themes are suitable for content output.

10. Sources
- Keep sources grouped by GitHub and skill 日榜.
- Include exact dates for GitHub/API/skill 日榜 data when available.

## Default Deliverable Scope

Unless the user explicitly asks for more, the daily radar should contain exactly these three ranking sections:

1. `GitHub Trending Daily 榜`
2. `GitHub 新增热门项目榜`
3. `skill 日榜`

Do not add a fourth default ranking table such as `GitHub star-growth榜`.
If star-growth data becomes available later, include it only when the user explicitly asks for it or when the report is clearly framed as an extended edition.

## Social Card Output Order

When the Markdown report is confirmed and the workflow continues into social-card generation, keep the output sequence grouped by榜单 rather than by content type.

Required order:

1. Summary / cover card
2. `GitHub Trending Daily 榜` card
3. `GitHub Trending Daily` detail cards
4. `GitHub 新增热门项目榜` card
5. `GitHub 新增热门项目` detail cards
6. `skill 日榜` card
7. `skill 日榜` detail cards

Do not output all榜单 cards first and all detail cards later.
The intended reading flow is:
- first see one ranking card,
- then immediately see the detailed evaluations for that ranking set,
- then move to the next ranking set.

Recommended filename pattern:

- `xhs-01-summary.png`
- `xhs-02-github-trending-daily.png`
- `xhs-03-github-trending-detail-1.png`
- `xhs-04-github-trending-detail-2.png`
- `xhs-05-github-new-hot.png`
- `xhs-06-github-new-hot-detail-1.png`
- `xhs-07-github-new-hot-detail-2.png`
- `xhs-08-skill-daily.png`
- `xhs-09-skill-daily-detail-1.png`
- `xhs-10-skill-daily-detail-2.png`

If one榜单 has fewer detail pages, keep the same grouped ordering and simply skip the missing suffixes.

## Skill 日榜 Trial Format

When the user asks to test skill 日榜's usefulness, run a small sample:

- Collect 5-10 AI-related skill candidates from the latest completed daily leaderboard, skill pages, search results, or official snippets.
- If direct page access is blocked or the listing is too thin, say so and mark confidence low/medium.
- Score each candidate with the five-dimension model.
- Conclude whether skill 日榜 adds signal beyond GitHub, and where it is noisy.

## Guardrails

- Do not equate upvotes/stars with product quality.
- Do not claim "latest" without live verification.
- Prefer official sources: GitHub repo, skill page, linked website/docs, changelog, pricing.
- Include exact dates for launches and volatile signals when available.
- For GitHub repos, avoid deep code claims unless README/docs/code files were read.
- For skill 日榜, treat ranking position as launch momentum, not durable retention.
