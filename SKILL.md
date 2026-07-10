---
name: track-ai-product-trends
description: Track the latest AI product trends from GitHub Trending Daily, GitHub new-hot repositories, and skills.sh Trending + Hot. Use this skill when the user asks for AI product trend tracking, daily AI product radar, new AI project recommendations, GitHub/skill AI analysis, or product/opportunity scoring for emerging AI tools.
---

# Track AI Product Trends

## Purpose

Create a repeatable AI product trend radar for product managers, founders, investors, and content creators. The skill turns noisy daily signals into ranked recommendations with product-design and opportunity scores.

## Default Scope

Use these sources by default unless the user narrows the request:

1. GitHub Trending: daily developer attention.
2. GitHub new-hot repo榜: recently created repositories with unusually high traction.
3. skills.sh Trending + Hot: agent skill packaging signals and workflow-layer traction.

Optional later sources: Hacker News Show HN, Hugging Face Trending, Reddit/HN comments, Chrome Web Store/App Store reviews, YC launches, funding/news, and Chinese communities.

## When To Use skills.sh

Use skills.sh as a productization and workflow-packaging signal, not as final proof of product quality.

Default skills.sh window:
- Use `https://www.skills.sh/trending` as the primary source. It is a weekly-style momentum page, not a strict daily leaderboard.
- Use `https://www.skills.sh/hot` as the secondary recency source. It reflects right-now install movement and should be used for activity correction, not copied mechanically.
- State the exact report date and source口径, e.g. `skills.sh 口径：Trending 为主，Hot 做活跃校正；对同 publisher 或高度模板化条目做去重和代表性筛选。`

skills.sh is useful for:
- launch positioning, screenshots, concise capability packaging, and maker narrative,
- detecting which AI capabilities are being productized into reusable skills,
- finding workflow-layer innovation missed by GitHub repositories alone.

Treat skills.sh with caution when:
- Trending and Hot are volatile or dominated by install spikes,
- the listing page is sparse and only gives short descriptions without real usage evidence,
- the skill has launch polish but weak proof of repeat use or durable workflow value.

Best practice: use skills.sh Trending as the main source, Hot as active-use correction, then use the skill page itself, linked repo/site/docs, and adjacent launch context only for validation.

When the user wants to judge whether a skill or skill set is actually well engineered, do not rely on the five-dimension product score alone. Use `ai-skill-deep-review` for the deeper skill-quality layer: trigger contract, procedural executability, validation loop, context economy, composability, guardrails, resource leverage, and maintenance.

### skills.sh Deduplication Rules

- Do not keep `find-skills` as a default final-table item when it appears high in the raw list; it is too foundational and familiar to be useful as a daily recommendation unless the user explicitly asks for skill discovery infrastructure.
- If an entry is a generic installer, directory, or setup wrapper, include it only when it reveals a new adoption pattern. Prefer more concrete workflow skills such as video rendering, review/critiquing, office-document workflows, MCP building, PRD/issue conversion, or website-to-video.
- If one publisher occupies many adjacent slots with near-identical templates, keep the 1-2 most representative entries and replace the rest with diverse skill types.

## Workflow

1. Set date and market context.
- State the exact date and timezone if using daily signals.
- For volatile data, browse or query live sources.

2. Build candidate pool.
- Collect GitHub Trending AI-related repos.
- Collect GitHub new-hot repos using GitHub Search API or search queries, normally `created:>recent_date` + AI/LLM/agent/MCP/coding keywords + `sort=stars`.
- Collect skills.sh candidates from Trending + Hot, prioritizing AI-related skills, agent workflows, productivity automations, creator tools, and developer tooling.
- Deduplicate by product/repo/domain.
- When a previous weekly/daily report is available locally, collect extra candidates beyond the raw Top 10, normally at least 20 per source, so repeated items can be skipped in detailed analysis and backfilled with fresh candidates.

3. Classify each candidate.
- Type: repo, product, model, agent, workflow, infra, app, plugin, content/community signal.
- User: developer, PM/designer, sales/marketing, support, creator, consumer, enterprise ops, founder.
- Category: coding, agent infra, voice, meeting, search, media, automation, data, design, vertical SaaS, other.

4. Analyze evidence.
- For GitHub repos, use `analyze-open-source-repo` quick-pm when the user asks for repo-level analysis or when a repo enters the top shortlist.
- For skills.sh candidates, read the skill page plus linked repo/site/docs/examples if available.
- Separate facts from inference. Include confidence: high, medium, or low.

5. Score and rank.
- Score each candidate with the five-dimension model below.
- Produce `Product Design Score` and `Opportunity Score`, both 0-5.
- Rank by opportunity first unless the user asks for pure design quality.

6. Produce recommendations.
- Mark each candidate as `deep-dive`, `watch`, or `pass`.
- Include why now, why it matters, and what evidence would change the score.

## Repeat And Backfill Rules

When comparing with the previous issue, use the most recent prior Markdown report from the same workflow if available. Compare within the same source section first:

- `GitHub Trending Daily 榜` vs previous `GitHub Trending Daily 榜`
- `GitHub 新增热门项目榜` vs previous `GitHub 新增热门项目榜`
- `skills.sh 榜` vs previous `skills.sh 榜`

Use stable IDs for matching:

- GitHub: canonical `owner/repo` in lowercase.
- skills.sh: canonical skill name, stripping publisher prefixes such as `publisher · skill-name` when needed.

Default handling:

- If an item also appeared in the previous issue, mark it as `上周已在榜`.
- If an item did not appear in the previous issue, mark it as `本周新进入`.
- Repeated items should be shown only as rank/status observations: `#N 项目名 — 上周已在榜`.
- Repeated items must not receive a full one-sentence positioning, product-design score, or per-project quick-pm explanation in the current issue unless the user explicitly asks to re-analyze repeated items.
- After skipping repeated items from detailed coverage, continue down the raw candidate pool and backfill with the next eligible `本周新进入` items until each source has 10 fully explained items.
- If fewer than 10 fresh items are available after reasonable collection, state the count and do not pad with weak or unrelated candidates.

Recommended section shape:

1. `榜单变化`
- `上周已在榜：#1 xxx；#4 yyy`
- `本周新进入：10 个，本节展开前 10 个`

2. `本周展开项目`
- A table of 10 fresh items, each marked `本周新进入`, with positioning and score.

Do not let repeated items crowd out fresh recommendations. The purpose of this rule is to preserve continuity while keeping the report useful for weekly discovery.

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
- Keep GitHub and skills.sh in separate tables.
- Keep GitHub Trending Daily and GitHub new-hot in separate tables.
- Use `github.com/trending?since=daily` or another explicit GitHub Trending daily source.
- If GitHub Trending cannot be parsed or accessed, still include the section and state: `GitHub Trending Daily 数据获取失败，本次不混用新增热门项目替代。`
- Add `榜单变化` before the table when a previous issue is available, marking repeated raw-rank items as `上周已在榜`.
- Table columns for detailed fresh items: 排名, 项目, 状态, 一句话定位, 产品设计分.

3. GitHub 新增热门项目榜
- Use recently created repositories, usually `created:>近30天` or a concrete date such as `created:>2026-06-01`, filtered by AI/LLM/agent/MCP/coding keywords and sorted by stars.
- Add a one-line note before the table with the exact data口径, e.g. `GitHub 新增热门口径：created:>2026-06-01 + AI/LLM/agent/MCP/coding keywords + sort=stars，并按产品相关性筛选重排。`
- Add `榜单变化` before the table when a previous issue is available, marking repeated raw-rank items as `上周已在榜`.
- Table columns for detailed fresh items: 排名, 项目, 状态, 一句话定位, 产品设计分.

4. skills.sh 榜
- Treat `https://www.skills.sh/trending` as the primary source and `https://www.skills.sh/hot` as a secondary recency signal.
- Do not call this a strict `日榜` unless the source actually provides a completed daily leaderboard. Prefer `skills.sh 榜` or `skills.sh Trending + Hot`.
- Do not mechanically copy the raw Hot ranking into the final table. Use `Trending` as the main ranking base and use `Hot` only to promote still-active candidates or positive-change newcomers.
- If the top of `Trending` or `Hot` is dominated by the same publisher, generic setup wrappers, or near-identical media skills, deduplicate aggressively and keep only the most representative 1-2 entries from that cluster.
- Add `榜单变化` before the table when a previous issue is available, marking repeated raw-rank items as `上周已在榜`.
- Table columns for detailed fresh items: 排名, 项目, 状态, 一句话定位, 产品设计分.
- Add a one-line note before the table with the exact skills.sh source口径.

5. GitHub Trending Daily 分项目 quick-pm 分析
For each GitHub Trending Daily shortlisted candidate, use this compact Chinese structure:
- `N. owner/repo：X.X/5`
- `定位：...`
- `用户价值：...`
- `差异化：...`
- `反向思考：...`
- `建议：...`
- If the ranking table lists 10 items, this analysis section should also cover all 10 items unless the user explicitly asks for a shorter shortlist.
- Do not write quick-pm analysis for `上周已在榜` items under the default repeat/backfill rule; analyze the 10 `本周新进入` backfilled items instead.

6. GitHub 新增热门分项目 quick-pm 分析
For each GitHub shortlisted candidate, use this compact Chinese structure:
- `N. owner/repo：X.X/5`
- `定位：...`
- `用户价值：...`
- `差异化：...`
- `反向思考：...`
- `建议：...`
- If the ranking table lists 10 items, this analysis section should also cover all 10 items unless the user explicitly asks for a shorter shortlist.
- Do not write quick-pm analysis for `上周已在榜` items under the default repeat/backfill rule; analyze the 10 `本周新进入` backfilled items instead.

7. skills.sh 分项目 quick-pm 分析
For each skills.sh shortlisted candidate, use the same compact Chinese structure:
- `N. Skill Name：X.X/5`
- `定位：...`
- `用户价值：...`
- `差异化：...`
- `反向思考：...`
- `建议：...`
- If the ranking table lists 10 items, this analysis section should also cover all 10 items unless the user explicitly asks for a shorter shortlist.
- Do not write quick-pm analysis for `上周已在榜` items under the default repeat/backfill rule; analyze the 10 `本周新进入` backfilled items instead.

8. Trend clusters
- Group candidates into themes such as coding agents, AI voice, workflow automation, agent infra, AI content production, AI search, vertical AI SaaS.

9. Follow-up queue
- Which repos should be analyzed with `analyze-open-source-repo` quick-pm.
- Which skills.sh items need linked repo/site/docs validation.
- Which themes are suitable for content output.

10. Sources
- Keep sources grouped by GitHub and skills.sh.
- Include exact dates for GitHub/API/skills.sh data when available.

## Default Deliverable Scope

Unless the user explicitly asks for more, the daily radar should contain exactly these three ranking sections:

1. `GitHub Trending Daily 榜`
2. `GitHub 新增热门项目榜`
3. `skills.sh 榜`

Do not add a fourth default ranking table such as `GitHub star-growth榜`.
If star-growth data becomes available later, include it only when the user explicitly asks for it or when the report is clearly framed as an extended edition.

## Social Card Output Order

When the Markdown report is confirmed and the workflow continues into social-card generation, keep the output sequence grouped by榜单, and default to the denser merged-card layout instead of separating ranking and detail pages.

When producing a rendered card package, also copy or write the exact Markdown report used for that card set into the same `output/` directory as the images. The Markdown must match the final card data, not an earlier draft. Use a dated/versioned filename such as `ai-product-trends-YYYYMMDD-vN.md` when the card folder is versioned.

Required order:

1. Summary / cover card
2. `GitHub Trending Daily 榜` merged card `01-05`
3. `GitHub Trending Daily 榜` merged card `06-10`
4. `GitHub 新增热门项目榜` merged card `01-05`
5. `GitHub 新增热门项目榜` merged card `06-10`
6. `skills.sh 榜` merged card `01-05`
7. `skills.sh 榜` merged card `06-10`

Do not output all榜单 overview pages first and then push all点评页 to the back.
The intended reading flow is:
- first see one ranking set,
- that same page should already carry concise project-level evaluation,
- then continue to the second half of the same ranking set,
- then move to the next ranking set.

Recommended filename pattern:

- `xhs-01-summary.png`
- `xhs-02-github-trending-1.png`
- `xhs-03-github-trending-2.png`
- `xhs-04-github-new-hot-1.png`
- `xhs-05-github-new-hot-2.png`
- `xhs-06-skills-daily-1.png`
- `xhs-07-skills-daily-2.png`

If one榜单 has fewer than 10 entries, keep the same grouped ordering and simply reduce the second page to the remaining items.

## Social Card Content Contract

When this skill continues into `guizang-social-card-skill`, do not leave the image set at the level of ranking tables only. The card deck must carry both:

1. ranking overview information, and
2. further per-project evaluation information.

Default card shape:
- summary cover first,
- then each ranking set split into two dense Top 10 pages (`01-05`, `06-10`),
- and each project row already includes its short evaluation.

Do not default back to the old "one ranking table page + two separate detail pages" structure unless the user explicitly asks for a lighter, lower-density version.

### Required per-card payload

#### `xhs-01-summary.png`

Purpose:
- Tell the reader what this report is.
- Give 2-3 clear trend judgments.
- Surface the 3-5 most值得跟踪 items across all sources.
- When repeat/backfill mode is used, explain that repeated items are marked separately and the detailed cards focus on `本周新进入` items.

Must include:
- a prominent main-content date label using the exact Chinese copy pattern: `数据统计时间：YYYY.MM.DD`,
- source scope: GitHub Trending Daily, GitHub 新增热门, skills.sh Trending + Hot,
- a clear 3-source count strip: `10 个 GitHub Trending · 10 个新增热门 · 10 个 Skills`,
- three compact metrics:
  - `30 / TODAY'S LIST / 3 组榜单 · 每组 Top 10`
  - `3 / DATA FEEDS / Trending / New Hot / skills.sh`
  - `4 / ROW FIELDS / 定位、价值、差异化、建议`
- a 3-column preview of the top 3 entries from each ranking set.

Do not let the summary cover become only an abstract slogan with no clue that the report contains GitHub projects and skill recommendations.
Do not use an outdated cover that still says `20` items, `2` data feeds, or only GitHub/project signals when the deck contains the three default sources.
Do not use vague cover-date labels such as `更新`; the cover date represents the data collection/statistical time for the report.

#### Ranking cards: merged dense cards

Purpose:
- Present one ranking set in a denser, more readable form.
- Split Top 10 into two pages: `01-05` and `06-10`.
- Let the reader finish both ranking and basic judgment on the same page.

Must include on each project row:
- `排名`
- `项目名`
- `状态` when repeat/backfill mode is used; default detailed rows should show `本周新进入`
- `产品设计分`
- `定位`
- `价值`
- `差异化`
- `建议`

Must include on each page:
- ranking-set label,
- exact date or query window,
- half-range label such as `Top 10 · 01-05`,
- a short reader-facing line such as `今天最值得点开的 5 个项目` or `继续看后 5 个 skill`.

Do not use generic field-summary hints like:
- `一句话定位 + 价值 + 建议`

Prefer short reader-facing lines that explain why this half-page matters.

### Dense card UI contract

Use the current dense Swiss-style information card pattern as the default:

1. Each ranking set is two portrait pages, not one table page plus detached detail pages.
2. Each row is a compact evaluation block:
   - large red ranking number,
   - bold project name as the scan entry,
   - status label such as `本周新进入` when repeat/backfill mode is used,
   - score right-aligned,
   - four short lines in this order: `定位 / 价值 / 差异化 / 建议`.
3. Visual hierarchy:
   - `项目名` should be the strongest row-level entry point.
   - `定位` should be slightly lighter and separated a little from the next three lines.
   - `价值` is the main body line.
   - `差异化` is a secondary analytic line.
   - `建议` should stand out more clearly than the middle two lines, typically with a small top gap and accent-colored label.
4. Information density:
   - keep rows tighter between projects than the older detail-card layout,
   - but increase row-internal clarity through type hierarchy and micro-spacing instead of reducing content.
   - keep正文小字 comfortably readable: body/explanation text should use the enlarged v8.1 scale, roughly 3px larger than the earlier v8 small-text setting, while titles, project names, rank numbers, scores, and page chrome stay unchanged.
5. Avoid large unused blank space at the bottom of dense ranking pages. The 5 project rows should visually carry the page height more evenly.
6. Keep wording objective and restrained. Avoid dramatic section labels or slogan-like page subtitles.

The ranking card is not the place for long prose. It should behave like a compact leaderboard.

### Coverage rules

- If a ranking table lists 10 items, the two merged cards for that ranking set must cover all 10.
- Do not stop after the first 5 items.
- Do not create separate detached detail cards by default.
- Each listed item needs its evaluation directly inside the merged ranking card, not only in the Markdown article.
- In repeat/backfill mode, merged cards should cover the 10 detailed `本周新进入` items. Repeated `上周已在榜` items may appear as a small rank-only observation strip, but must not consume one of the 10 detailed row slots.

### Mapping from Markdown to cards

When converting the report into cards:

1. Ranking table + quick-pm analysis -> two merged dense cards for that ranking set.
2. Items `01-05` go to the first card; items `06-10` go to the second card.
3. Compress each candidate's analysis into `定位 / 价值 / 差异化 / 建议`.

Do not invent a new card-level structure each day. Reuse this mapping so the deck remains stable and comparable over time.

### Tone of section labels

For the short Chinese labels that appear on card pages, keep them objective and low-drama.

Use simple labels that match the actual content of the page.

Examples of acceptable tone:
- `GitHub Trending Daily`
- `GitHub 新增热门`
- `skills.sh`
- `具体评价`
- `Top 10`
- `01-05`
- `06-10`

Avoid overly dramatic or self-conscious labels such as:
- `最强信号`
- `延伸方向`
- `为什么上榜`
- `下半场信号`
- `产品化强信号`
- `边缘但重要`
- other headline-like phrasing that sounds too performative.

## skills.sh Trial Format

When the user asks to test skills.sh usefulness, run a small sample:

- Collect 5-10 AI-related skill candidates from skills.sh Trending + Hot, skill pages, search results, or official snippets.
- If direct page access is blocked or the listing is too thin, say so and mark confidence low/medium.
- Score each candidate with the five-dimension model.
- Conclude whether skills.sh adds signal beyond GitHub, and where it is noisy.

## Guardrails

- Do not equate upvotes/stars with product quality.
- Do not claim "latest" without live verification.
- Prefer official sources: GitHub repo, skill page, linked website/docs, changelog, pricing.
- Include exact dates for launches and volatile signals when available.
- For GitHub repos, avoid deep code claims unless README/docs/code files were read.
- For skills.sh, treat ranking position as launch momentum, not durable retention.
