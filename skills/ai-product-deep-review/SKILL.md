---
name: ai-product-deep-review
description: Deeply review a single AI product, open-source repo, or launch from a product strategy perspective, with evidence collection, product scoring, adoption analysis, and social-card-ready output. Use when the user asks for AI 产品深度评测, 单个产品拆解, product teardown, 项目深度分析, or wants a cover card with logo/stars/conclusion plus multi-dimensional analysis.
---

# AI Product Deep Review

## Purpose

Create a repeatable deep-review workflow for one AI product at a time. The output should help product managers, founders, operators, investors, and content creators understand:

- what the product is,
- why it matters now,
- how it works as a product system,
- where its design is strong or fragile,
- whether it deserves adoption, tracking, or content coverage.

This skill complements `track-ai-product-trends`: use trend tracking to discover candidates, then use this skill to produce a deep review for a single selected product.

## Default Assumptions

If the user provides only a product name, infer the most likely official product/repo, state the assumption, and verify with live sources when the product is current or ambiguous.

Default audience: product-manager-facing, Chinese output, with enough technical evidence to avoid shallow commentary.

Default deliverable: a Markdown deep-review article that can later be turned into social cards.

If the user asks for cards/images, first create or confirm the Markdown artifact, then invoke `guizang-social-card-skill` for image generation.

## Deep Review Visual Direction

This skill must not reuse the same visual language as `track-ai-product-trends`.

The distinction is intentional:

- Trend radar cards are discovery-oriented: lighter, faster to scan, lower-to-medium density, and comfortable with more breathing room.
- Deep-review cards are teardown-oriented: denser, colder, more severe, and more analytical. The reader should feel they are looking at an analyst workbench, not a discovery carousel.

When this skill continues into `guizang-social-card-skill`, use these defaults unless the user explicitly asks for another direction:

1. Visual stance
- Prefer `Swiss International` over `Editorial Magazine` for most deep reviews.
- Use a cold paper / dark ink / hard-accent palette. Think steel, slate, IKB-blue, or similarly restrained cold accents.
- Avoid warm magazine palettes, soft lifestyle styling, and airy trend-radar composition.

2. Information density
- Most 3:4 pages should contain at least three layers: `judgment`, `evidence`, and `implication`.
- Prefer structured modules: comparison tables, stacked ledgers, matrix fills, h-bar charts, KPI strips, system maps, and compact score rows.
- Avoid pages that are only a slogan plus 3 bullets unless it is the single intentional rhythm-break page.
- The cover may breathe slightly more, but it still needs a representative image plus multiple hard signals.

3. Cover requirements
- Include the product logo or representative product image.
- Include at least three hard signals when available: stars, forks, score, collection date, launch date, pricing, deployment model, or adoption signal.
- The conclusion sentence should be decisive and specific, not a vague compliment.

4. Relationship to trend-radar output
- `track-ai-product-trends` is for breadth and ranking.
- `ai-product-deep-review` is for depth and mechanism.
- If both outputs appear in the same broader workflow, the deep-review deck should feel more rigorous, colder, and more evidence-heavy than the trend deck.

## Evidence Collection

Prefer official and primary sources:

1. Official website or landing page.
2. GitHub repo README, metadata, stars/forks/issues, recent commits, releases, license.
3. Docs, changelog, pricing, demo videos, screenshots, product pages.
4. Product Hunt page or launch page if the product was launched there.
5. Competitor official docs or websites for comparison.

For GitHub projects, collect at least:

- repo URL,
- one-line description,
- star count and fork count with collection date,
- created/pushed date when available,
- README positioning,
- package/dependency or architecture signal,
- 1-2 core files when making technical claims.

For non-GitHub products, collect at least:

- official URL,
- positioning/tagline,
- target user,
- onboarding or demo evidence,
- pricing or deployment model if available,
- public traction signal if available.

Always separate facts from inference. Include exact dates for volatile data.

## Review Dimensions

Use these dimensions unless the user asks for a different angle:

1. Product positioning
- What category is it creating or entering?
- What is the sharpest one-sentence description?
- Is it a tool, workflow, platform, infrastructure layer, marketplace, or organization system?

2. Core user and scenario
- Who has the strongest pain?
- What job-to-be-done does it serve?
- Is it for individuals, teams, enterprises, developers, creators, or operators?

3. Problem intensity and value
- Is the pain frequent, expensive, trust-sensitive, or strategically important?
- Does AI create a step-change rather than a small convenience?
- Is time-to-value visible?

4. Product mechanism
- What workflow does the product introduce?
- What are the key objects, actions, loops, and feedback surfaces?
- For AI products, identify where intelligence enters the workflow and where product structure constrains or amplifies it.

5. Differentiation and defensibility
- Is the advantage model-level, workflow-level, data-level, distribution-level, ecosystem-level, or organizational?
- What could a model vendor or large platform easily absorb?
- What is hard to copy?

6. Adoption and go-to-market
- What is the first useful use case?
- What is the expansion path from one user/team to larger adoption?
- What integrations, deployment model, pricing, and trust requirements affect adoption?

7. Risks and reverse thinking
- What could break user trust?
- Where might the product be too heavy, too narrow, or too dependent on external platforms?
- What assumptions must be true for the product to keep growing?

8. Market timing
- Why is this product possible now?
- What model/platform/user behavior changes create the opening?
- Is the trend durable or likely to be absorbed?

## Scoring Model

Score 0-5, with one decimal when useful.

Product Design Score:
- positioning clarity 20%,
- pain/value intensity 20%,
- workflow and interaction design 20%,
- differentiation 20%,
- adoption path 20%.

Opportunity Score:
- timing 25%,
- market size and expansion potential 20%,
- defensibility 20%,
- urgency of pain 20%,
- distribution or ecosystem leverage 15%.

Interpretation:

- 4.6-5.0: rare strong product; deep-track immediately.
- 4.1-4.5: strong product with meaningful tradeoffs.
- 3.5-4.0: promising but not yet clearly durable.
- 2.5-3.4: useful or interesting, but narrow/incremental.
- below 2.5: weak product shape unless it reveals a broader trend.

Always include confidence: high, medium, or low.

## Markdown Output Structure

Use this structure by default:

1. Title
- `# 产品深度评测：{Product Name}`

2. Cover card brief
- logo/source image suggestion,
- GitHub stars or public traction signal,
- one decisive conclusion sentence,
- product design score,
- opportunity score.

3. Bottom line
- 3-5 short bullets with the strongest judgments.

4. One-line positioning
- `一句话定位：...`

5. What it is / who it serves
- Explain plainly before technical detail.

6. Why now
- Link the product to model/platform/workflow changes.

7. Product mechanism
- Map the product's key workflow, objects, loops, and control points.

8. Dimension-by-dimension review
- Use the Review Dimensions above.
- Keep each dimension concrete and evidence-linked.

9. Scorecard
- Table with dimension scores, rationale, and confidence.

10. Reverse thinking
- List the strongest failure triggers and adoption risks.

11. Comparison table
- Compare with 2-4 relevant products, official sources preferred.

12. Recommendation
- Use one of: `adopt`, `trial`, `deep-track`, `watch`, `pass`.
- Add the scenario where the recommendation changes.

13. Social card script
- Include page-by-page card copy if the user wants images or likely wants content output.

14. Sources
- Group sources by official product, GitHub, Product Hunt, competitors, and date-sensitive metrics.

## Social Card Density Requirements

When preparing page-by-page card copy, do not stop at title-plus-bullets. Each page should usually contain:

1. a clear claim,
2. one evidence block or structured breakdown,
3. one implication, recommendation, or reverse-thinking line.

Preferred page devices:

- positioning page: category + ICP + why-now relationship,
- mechanism page: objects + flow + loop,
- value page: pain + value + organizational leverage,
- differentiation page: common vs unique vs hard-to-copy,
- adoption page: first use case + rollout path + friction,
- risk page: failure trigger + trust break + must-be-true assumption,
- judgment page: score + recommendation + what would change the view.

## Social Card Structure

When generating or preparing cards, use this default reading order:

1. Cover card
- Product logo or representative product image.
- Product name.
- GitHub stars / public traction signal if available.
- One decisive conclusion sentence.
- Product Design Score and Opportunity Score.

2. Positioning card
- What it is.
- Who it serves.
- Why it matters now.

3. Mechanism card
- Key workflow or system map.
- Main objects/actions/loops.

4. Value card
- Core user pain.
- User value.
- Team/company value.

5. Differentiation card
- What is common.
- What is unique.
- What is hard to copy.

6. Adoption card
- First use case.
- Expansion path.
- Setup/friction/trust requirements.

7. Risk card
- Reverse thinking and failure triggers.

8. Final judgment card
- Recommendation.
- Who should use/track/pass.
- What evidence would change the view.

For open-source repos, the cover card should preferably include:

- repo owner/name,
- logo if available,
- stars and forks,
- collection date,
- conclusion sentence.

Recommended filename pattern:

- `xhs-01-cover.png`
- `xhs-02-positioning.png`
- `xhs-03-mechanism.png`
- `xhs-04-value.png`
- `xhs-05-differentiation.png`
- `xhs-06-adoption.png`
- `xhs-07-risks.png`
- `xhs-08-judgment.png`

## Output Style

Write in Chinese unless the user asks otherwise.

Be sharp but fair:

- Avoid generic praise like "前景广阔".
- Explain why a design choice matters.
- Prefer "what must be true" over vague risk lists.
- Call out when something is only a launch signal, not durable evidence.
- Do not equate stars, upvotes, or hype with product quality.

For concepts such as AI infrastructure, agent platforms, or workflow systems, distinguish:

- model capability layer,
- agent execution layer,
- product/workflow layer,
- organization/governance layer.

This distinction is especially important when reviewing products that do not improve model intelligence directly, but build frameworks, protocols, systems, or operating layers on top of AI capabilities.

## Skill Composition

Use `analyze-open-source-repo` when the target is a GitHub repository and code/repo-level evidence matters.

Use `track-ai-product-trends` only for upstream discovery or when the user asks to connect the product to a broader daily trend report.

Use `guizang-social-card-skill` after the Markdown review is confirmed or when the user explicitly asks to create Xiaohongshu/social cards.
