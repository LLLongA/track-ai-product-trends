---
name: ai-skill-deep-review
description: Deeply evaluate a Codex/agent skill, skill set, or skill repository with both product-packaging analysis and a dedicated skill-engineering quality framework. Use when the user asks for skill 深度评测, 评价一套 skills, agent skill 质量评估, skill repository teardown, or wants to know whether a skill is actually usable, maintainable, composable, and worth adopting.
---

# AI Skill Deep Review

## Purpose

Evaluate skills as behavior-shaping systems for agents, not only as products. Keep the product-review mechanism from `ai-product-deep-review`, but add a second lens that tests whether the skill can reliably improve agent work.

Default audience: skill authors, agent engineers, AI product builders, and content creators. Default output language: Chinese.

Default deliverable: a Markdown deep-review report. If the user asks for social cards, create or confirm the Markdown report first, then use `guizang-social-card-skill`.

## Core Distinction

Separate these two layers in every review:

1. Product packaging layer
- Is the skill/repo well positioned?
- Who is it for?
- Why does it matter now?
- How does it distribute, onboard, and compete?
- What adoption risks or platform-absorption risks exist?

2. Skill engineering layer
- Does the skill trigger at the right time?
- Does it give the agent executable procedure, not generic advice?
- Does it reduce hallucination, laziness, premature certainty, or context drift?
- Does it include validation loops, examples, references, scripts, or assets where needed?
- Can it compose with other skills without conflicts?
- Is it maintainable as models, tools, and host apps change?

Do not judge a skill mainly by stars, screenshots, launch polish, or product-market language. Those are adoption signals, not proof that the skill improves agent behavior.

## Evidence Collection

Prefer primary artifacts:

1. `SKILL.md` frontmatter and body.
2. `agents/openai.yaml` or equivalent UI/invocation metadata.
3. `references/`, `scripts/`, and `assets/` bundled resources.
4. Installation docs, plugin manifests, command files, personas, examples, and tests.
5. GitHub README, stars/forks/issues/releases/commit activity, and linked docs when reviewing a repo.
6. Example user prompts and observed outputs, if available.

For volatile GitHub or web metrics, collect live data and state exact collection date. Always separate facts from inference.

When reviewing a local skill folder, inspect the filesystem first. When reviewing a GitHub repo, prefer official GitHub/README/docs before third-party commentary.

## Review Workflow

1. Identify scope.
- Single skill, skill bundle, or full repository.
- Target host: Codex, Claude, Cursor, Gemini, Copilot, OpenCode, or generic agent.
- Intended user and task class.

2. Map the product layer.
- Use the product-review mechanism: positioning, user scenario, value intensity, product mechanism, differentiation, adoption, risks, timing.
- Keep this layer short when the user wants skill-quality analysis rather than market analysis.

3. Map the skill architecture.
- List every skill or major module.
- Identify routing/meta-skills, commands, personas, references, scripts, assets, and validation tools.
- For a bundle, draw the lifecycle coverage: discover -> plan -> execute -> verify -> review -> ship.

4. Score skill engineering.
- Use the dimensions below.
- Quote or point to concrete files/sections when possible.
- Reward executable specificity and validation; penalize vague principles without operational teeth.

5. Diagnose composition.
- Find overlaps, contradictions, missing handoffs, excessive context load, and unclear precedence.
- For multi-skill sets, identify which skill should be the router and where conflict resolution belongs.

6. Produce recommendations.
- Give adoption verdict: `adopt`, `trial`, `adapt`, `watch`, or `pass`.
- Include a prioritized improvement backlog for skill authors.
- Include what evidence would change the conclusion.

## Skill Engineering Dimensions

Score each dimension 0-5, with one decimal when useful.

1. Trigger Contract
- Clear when to use and when not to use.
- Frontmatter description contains the trigger conditions, not only the body.
- Ambiguity with adjacent skills is explicitly handled.

2. Procedural Executability
- Steps are concrete enough for an agent to act.
- Instructions include decision points, ordering, fallback behavior, and stop conditions.
- The skill avoids generic advice like "be careful" unless it defines how to check.

3. Evidence And Validation Loop
- Requires source inspection, tests, screenshots, validators, citations, or artifact review as appropriate.
- Defines what counts as done.
- Protects against fabricated facts, skipped verification, and overconfident conclusions.

4. Context Economy
- Keeps `SKILL.md` lean and moves details into references only when needed.
- Uses progressive disclosure with clear routing to references.
- Avoids loading huge irrelevant context or repeating obvious model knowledge.

5. Composability And Conflict Control
- Explains how to work with neighboring skills, tools, commands, personas, or MCP servers.
- Handles precedence when instructions conflict.
- Avoids hidden assumptions that break in another host app or model.

6. Guardrail Strength
- Names common rationalizations and failure modes.
- Converts values into operational checks.
- Reduces agent shortcuts: guessing, silent scope expansion, fake certainty, weak testing, or style drift.

7. Resource Leverage
- Uses scripts/templates/assets when repeated deterministic work would otherwise be retyped.
- References are discoverable, scoped, and directly useful.
- Bundled resources are tested or inspectable when they affect output quality.

8. Maintenance And Portability
- Easy to update when APIs, product docs, or host behavior changes.
- Version-sensitive claims are dated.
- Works across reasonable environments or clearly states host-specific assumptions.

## Scoring Model

Keep two scores separate by default:

1. `Skill Engineering Score`
- trigger contract 15%,
- procedural executability 20%,
- evidence and validation loop 20%,
- context economy 10%,
- composability and conflict control 15%,
- guardrail strength 10%,
- resource leverage and maintenance 10%.

2. `Product Packaging Score`
- positioning clarity 20%,
- user pain and value intensity 20%,
- workflow/product mechanism 20%,
- adoption and distribution path 20%,
- differentiation, timing, and defensibility 20%.

Interpretation:

- 4.6-5.0: excellent; adopt or model future skills on it.
- 4.1-4.5: strong; useful with clear tradeoffs.
- 3.5-4.0: promising but needs tightening before broad reuse.
- 2.5-3.4: usable in narrow cases, but fragile or under-specified.
- below 2.5: weak skill shape unless it is only a lightweight note.

Always include confidence: high, medium, or low.

## Red Flags

- Frontmatter says only what the skill is, not when to use it.
- The body is mostly philosophy with few executable steps.
- It asks the agent to "verify" but never defines how.
- It assumes screenshots, browsing, tools, or credentials exist without fallback.
- It has many references but no routing instructions.
- It duplicates another skill without precedence rules.
- It improves output style but not task success.
- It uses product traction as a proxy for skill quality.
- It creates huge context load for a narrow task.
- It lacks maintenance hooks for volatile sources, APIs, or models.

## Output Structure

Use `references/output-template.md` when writing a full review.

Default report sections:

1. Title: `# Skill 深度评测：{Skill or Repo Name}`
2. Evidence snapshot: files, repo, metrics, collection date.
3. Bottom line: 3-5 sharp judgments.
4. Product packaging review: positioning, user, mechanism, adoption, risk.
5. Skill architecture map: triggers, resources, workflow coverage, handoffs.
6. Skill engineering review: dimension-by-dimension analysis.
7. Scorecard: both scores plus confidence.
8. Red flags and failure modes.
9. Improvement backlog: high/medium/low priority.
10. Adoption verdict: adopt/trial/adapt/watch/pass.
11. Social card script when requested.
12. Sources.

## Social Card Guidance

When preparing cards, use a denser analytical style than trend-radar cards. Prefer Swiss International, hard grid, score rows, comparison tables, lifecycle maps, and evidence strips.

Default 8-page order:

1. Cover: skill/repo name, decisive conclusion, both scores, hard signals.
2. Core distinction: product packaging vs skill engineering.
3. Architecture map: routing, commands, references, scripts, personas.
4. Trigger and execution quality.
5. Validation and guardrails.
6. Composability and context economy.
7. Scorecard and red flags.
8. Recommendation and improvement backlog.

Do not reuse a pure product scorecard for skill cards. The visual language may resemble product deep-review cards, but the dimensions must be skill-specific.

## Composition

Use `ai-product-deep-review` only when the main target is a product, repo, or launch rather than the skill quality itself.

Use `analyze-open-source-repo` when repo architecture, code organization, scripts, or plugin manifests matter.

Use `guizang-social-card-skill` after the Markdown review is confirmed or when the user explicitly asks for Xiaohongshu/social cards.
