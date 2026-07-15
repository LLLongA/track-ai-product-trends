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
| Review folder | `{ai-skill-review-{slug}-{YYYYMMDD}}` |
| Trial mode | `{real invocation / dry-run / partial trial}` |
| Metrics date | `{YYYY-MM-DD, if applicable}` |
| Confidence | `{high / medium / low}` |

## Practice Trial

### Trial Task

`真实试用任务：...`

Explain why this task represents the skill's intended use case and what a good result should look like.

### Trial Prompt Or Command

Store the exact prompt/command in `trial/trial-prompt.md`, then summarize it here:

```text
{prompt or command excerpt}
```

### Trial Artifacts

| Artifact | Path | Notes |
| --- | --- | --- |
| Trial plan | `trial/trial-plan.md` |  |
| Execution notes | `trial/execution-notes.md` |  |
| Output files | `trial/outputs/...` |  |
| Screenshots/images | `trial/screenshots/...` |  |
| Validation | `trial/validation.md` |  |

### Observed Result

- `What worked:` ...
- `Where the skill helped:` ...
- `Where the agent had to improvise:` ...
- `What failed or remained ambiguous:` ...

### Validation Result

State the checks performed and whether the output passed the trial criteria.

Use one of:

- `pass`
- `partial pass`
- `fail`
- `blocked`

Explain how the trial result affects the engineering score and adoption verdict.

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
| Evidence And Validation Loop |  | `trial/validation.md`, screenshots, tests, output artifacts |  |
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

When requested, prepare 7-9 pages. The card script must include at least one page or evidence strip based on the real trial artifacts.

1. Cover.
2. Product vs skill distinction.
3. Practice trial result.
4. Architecture map.
5. Trigger and execution.
6. Validation and guardrails.
7. Composability/context economy.
8. Scorecard/red flags.
9. Recommendation/backlog.

For the practice trial card, specify:

- source text path from `trial/`,
- screenshot/image path if applicable,
- one observed output excerpt,
- trial verdict: `pass / partial pass / fail / blocked`.

## Sources

Group sources by local files, official repo/docs, metrics, and competitors/comparables.
