# IS373 Course Reference (group content system)

IS373-001, Fall 2026 · Deliverable 3: group content system + problem research.

**Team:** Bridget McTiernan · Ann Carlos / GitHub: apink634 · Dhruvi Malusare / GitHub: dhruvi0805

A tool that turns the IS373 course material spread across Canvas, course sites and GitHub repos into a reviewed, searchable reference: a **command cheat sheet** (command, what it does, why you'd use it) and a **glossary** (term, plain-English meaning, related terms). AI drafts each entry from the course sources, a teammate reviews and approves it, and only approved entries are published, each linked to the page it came from.

This repository is our one shared record for Plan, Build, Checked Release and Improve. The plan lives in [docs/plan.md](docs/plan.md); code will live in `app/` from Build.

## Research review index

**Status labels:** `proposed` = not agreed by all members yet · `agreed` · `planned` = not run yet · `observed locally` · `observed hosted`.

| Item | Link | Status | Reviewed / checked |
| --- | --- | --- | --- |
| Reader, problem and research question | [Reader](docs/plan.md#reader-problem-and-research-question) | proposed | outside peer planned ([#3](https://github.com/mcbridgeee/is373-group-course-reference/issues/3)) |
| Permitted sources | [Sources](docs/plan.md#permitted-sources) | proposed | all five sources checked Nov 17 ([source check](docs/plan.md#source-check-run-on-nov-17-executed-not-planned)); instructor permission not yet confirmed |
| Observations vs. assumptions | [Evidence](docs/plan.md#observations-vs-assumptions) | proposed | assumption checks planned |
| Two approaches compared | [Approaches](docs/plan.md#two-approaches) | proposed | outside peer planned ([#3](https://github.com/mcbridgeee/is373-group-course-reference/issues/3)) |
| Vector, graph or both | [Retrieval](docs/plan.md#vector-graph-or-both) | proposed | keyword vs. vector comparison defined in [#2](https://github.com/mcbridgeee/is373-group-course-reference/issues/2) |
| Workflow and one source traced | [Workflow](docs/plan.md#workflow-and-one-source-traced) | proposed | source step verified Nov 17; later steps planned |
| Success criteria | [Criteria](docs/plan.md#success-criteria) | proposed | re-import criterion revised in [#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1) |
| Stories and checks | [Stories](docs/plan.md#stories-and-checks) | proposed | story 5 revised in [#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1); all checks planned |
| Evaluation set | [Evaluation](docs/plan.md#evaluation-set) | proposed | E1, E2, E5 revised in [#2](https://github.com/mcbridgeee/is373-group-course-reference/issues/2); E7 added for [#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1); all planned |
| Owners and reviewers | [Owners](docs/plan.md#owners-and-reviewers) | proposed | Ann accepted her slice in [#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1); Dhruvi accepted the AI drafting slice on Nov 17. |
| Each member's contribution | [Contributions](docs/contributions.md) | in progress | |

## Peer feedback log

| Date | Peer | What they tried | What they said / did | Our decision | Change link |
| --- | --- | --- | --- | --- | --- |
| Nov 16 | Ann (teammate) | Reviewed story 5 and her import slice | Asked how a re-import knows content is the same and what it reports | Store a hash per section; skip unchanged sections, report changed ones and send only those back to review | [#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1) · story 5, E7 |
| Nov 16 | Dhruvi (teammate) | Reviewed the evaluation set | Asked for a measurable pass rule and a defined no-match result | Compare keyword and vector rank with a top-three pass; E5 passes only with the no-match message and zero results | [#2](https://github.com/mcbridgeee/is373-group-course-reference/issues/2) · [9f30238](https://github.com/mcbridgeee/is373-group-course-reference/commit/9f30238de88284b7b16599323ece57084253b7e4) |
| planned, Nov 17/19 workshop | outside peer (another team) | Follow the S01 source trace | not yet run | | [#3](https://github.com/mcbridgeee/is373-group-course-reference/issues/3) |

## Review history

| Stage | Due (Eastern) | All submitted |
| --- | --- | --- |
| Plan | Nov 17, 1 p.m. | |
| Build | Nov 24, 1 p.m. | |
| Checked Release | Dec 3, 1 p.m. | |
| Improve | Dec 10, 11:59 p.m. | |
