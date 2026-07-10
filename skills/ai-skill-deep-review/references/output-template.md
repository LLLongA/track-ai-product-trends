# AI Skill Deep Review Output Template

Use this template when writing a full review. Keep facts and inference separate.

## Title

`# Skill 深度评测：{name}`

## Evidence Snapshot

| Evidence | Value |
| --- | --- |
| Target | `{skill / bundle / repo}` |
| Source | `{local path or URL}` |
| Host | `{Codex / Claude / Cursor / generic agent}` |
| Files inspected | `{SKILL.md, references, scripts, agents metadata...}` |
| Metrics date | `{YYYY-MM-DD, if applicable}` |
| Confidence | `{high / medium / low}` |

## Bottom Line

- `{sharp judgment 1}`
- `{sharp judgment 2}`
- `{sharp judgment 3}`

## Product Packaging Review

### Positioning

`一句话定位：...`

### User And Scenario

Explain who benefits most and where the workflow sits.

### Product Mechanism

Describe how the skill/repo packages a workflow: discovery, install, invocation, evidence, output, reuse.

### Adoption And Risk

Explain time-to-value, onboarding friction, differentiation, platform absorption risk, and what must be true for repeat use.

## Skill Architecture Map

| Component | Role | Evidence | Notes |
| --- | --- | --- | --- |
| Trigger/frontmatter |  |  |  |
| Procedure/body |  |  |  |
| References |  |  |  |
| Scripts/assets |  |  |  |
| Commands/personas |  |  |  |
| Validation loop |  |  |  |

For a skill set, add lifecycle coverage:

| Stage | Covered by | Missing or weak |
| --- | --- | --- |
| Discover |  |  |
| Plan |  |  |
| Execute |  |  |
| Verify |  |  |
| Review |  |  |
| Ship |  |  |

## Skill Engineering Review

| Dimension | Score | Evidence | Judgment |
| --- | ---: | --- | --- |
| Trigger Contract |  |  |  |
| Procedural Executability |  |  |  |
| Evidence And Validation Loop |  |  |  |
| Context Economy |  |  |  |
| Composability And Conflict Control |  |  |  |
| Guardrail Strength |  |  |  |
| Resource Leverage |  |  |  |
| Maintenance And Portability |  |  |  |

## Scorecard

| Score | Value | Confidence | Interpretation |
| --- | ---: | --- | --- |
| Skill Engineering Score |  |  |  |
| Product Packaging Score |  |  |  |

Do not merge the two scores unless the user asks for a single ranking.

## Red Flags And Failure Modes

- `{risk}`
- `{risk}`
- `{risk}`

## Improvement Backlog

| Priority | Change | Why it matters |
| --- | --- | --- |
| P0 |  |  |
| P1 |  |  |
| P2 |  |  |

## Adoption Verdict

Use one of: `adopt`, `trial`, `adapt`, `watch`, `pass`.

State who should use it, who should not, and what evidence would change the verdict.

## Social Card Script

When requested, prepare 6-9 pages:

1. Cover.
2. Product vs skill distinction.
3. Architecture map.
4. Trigger and execution.
5. Validation and guardrails.
6. Composability/context economy.
7. Scorecard/red flags.
8. Recommendation/backlog.

## Sources

Group sources by local files, official repo/docs, metrics, and competitors/comparables.
