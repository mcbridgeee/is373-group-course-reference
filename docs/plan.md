# 3. Group content system + problem research: Plan

[Back to index](../README.md)

## Changed / checked / next

- **Changed (Plan, Nov 16):** proposed the course reference concept, sources, workflow, retrieval approach, stories and owner/reviewer split.
- **Checked:** confirmed the five planned sources exist and are readable, and that the survival guide contains copyable commands with explanations (used for the trace below). Nothing has been built or run yet.
- **Next:** both members confirm or change the proposed decisions; ask a peer to follow the source trace and question one assumption; record it in the peer feedback log.

## Reader, problem and research question

- **Reader:** IS373 students, especially anyone who is behind, new to the command line, or returning to the material before Demo Day.
- **Problem:** course information is spread across Canvas pages, announcements, several course sites and many GitHub repos. Finding one command, what it does and why you'd use it, or what a term like "Traefik" or "chunking" means, takes digging through a dozen pages. (Course direction: **educational-content publishing**.)
- **Research question:** can AI turn the course's own material into a reference students can trust, if every entry is linked to its source and checked by a person before it's published?
- **Why this is more than a chat:** the shared workflow is the **review queue**. AI drafts, a human approves or edits, and only approved entries become the published reference. Students read a reviewed reference, not raw model output.

## Permitted sources

Course materials provided by the instructor for this course, used within the course for a course assignment. _Confirm with Professor Williams in class and note the date here._

| ID | Source | URL | What we take from it | Date checked |
| --- | --- | --- | --- | --- |
| S01 | Linux, Vim, Git, Docker and Python Survival Guide | https://github.com/kaw393939/linux_vim_git_docker_python_survival_guide | Git workflow commands (issue → branch → commit → PR) | 2026-11-15 |
| S02 | Server Studio (373_hosting) README | https://github.com/kaw393939/373_hosting | Docker, Traefik and HTTPS commands and terms | 2026-11-15 |
| S03 | App Studio (is373-app-studio) README | https://github.com/kaw393939/is373-app-studio | FastAPI, virtual environment and test commands | 2026-11-15 |
| S04 | IS373 Studio course site: overview and milestones | https://kaw393939.github.io/is373-studio/course/overview.html | Course terms: Plan, Build, Checked Release, project record | 2026-11-15 |
| S05 | IS373 RAG student guides: embeddings, chunking | https://kaw393939.github.io/is373-rag/students/ | Technical terms: embedding, chunking, vector search, RAG | 2026-11-15 |

Each source keeps a stable ID, URL and the date we imported it. If a page changes, re-import updates its entries and sends them back to review.

## Observations vs. assumptions

| Type | Statement |
| --- | --- |
| Observation | Course instructions are spread across Canvas, at least three course sites and several repos (we followed the links ourselves on Nov 15). |
| Observation | The sources contain many commands and terms but no single place listing them with plain-English explanations. |
| Assumption | Other students find this as hard to navigate as we do. **Check:** ask 2–3 classmates how they find a command they've forgotten. |
| Assumption | AI drafts will be mostly right but sometimes wrong or out of context. **Check:** track how many drafts reviewers edit or reject. |

## Two approaches

| | A: AI publishes entries directly | B: AI drafts, a person reviews before publishing |
| --- | --- | --- |
| How it works | Import sources → AI writes entries → entries go live | Import sources → AI writes draft entries → reviewer approves, edits or rejects → only approved entries go live |
| Strength | Faster; no human bottleneck | Students only see checked content; mistakes are caught before publishing |
| Weakness | A wrong command (e.g. a destructive Git or Docker command explained badly) reaches students | Slower; needs a review screen and roles |
| **Choice** | | **B (proposed).** A wrong command can break a student's project or server, so trust matters more than speed. The review queue is also the shared workflow the brief asks for. |

## Vector, graph or both

| Option | What it would do here | Limit |
| --- | --- | --- |
| Keyword baseline | Search entries by exact command or term ("docker compose") | Misses questions in students' own words |
| Vector | Students search in their own words ("how do I undo my last commit?") and find the right entry | Only knows similar, not how terms relate |
| Graph | Store related terms as links ("Traefik *routes traffic to* containers," "commit *is part of* a pull request") so each glossary entry shows related terms | Every link has to be reviewed like an entry |

**Proposed choice:** vector search over **approved** entries, compared against keyword search. Related terms are stored as simple reviewed links on each glossary entry (a lightweight graph), not a separate graph database. **Why:** students ask in their own words, so meaning-based search is the main need; related terms add value but don't need their own database at this size.

## Workflow and one source traced

```text
course source (S0x, URL, date)
  → import: fetch page, keep URL + section, skip duplicates on re-import
  → split into sections (chunks) with source IDs
  → AI drafts entries: command / what it does / why / source link   or   term / meaning / related terms / source link
  → review queue: teammate approves, edits or rejects (draft stays private)
  → approved entries published to the reference + indexed for search
  → student searches or browses; every entry links back to its source
```

**Trace (planned sketch, not executed):**

| Step | One example |
| --- | --- |
| Source | S01, section 3 "Issue → Branch → Pull Request," step 3, which shows `git commit -m "Add Linux navigation guide #12"` |
| Chunk | `S01-C0xx`: that section, with URL and heading |
| AI draft | **Command:** `git commit -m "message #12"` · **What it does:** saves your staged changes with a message · **Why:** referencing the issue number links the commit to its issue · **Source:** S01 §3 |
| Review | Reviewer checks it against S01: is the explanation right, is anything missing (like staging first)? Approves or edits |
| Published | Entry appears in the cheat sheet under Git, with a link to S01 §3 |
| What failure looks like | The draft explains something S01 doesn't say, links the wrong source, or appears publicly before approval |

## Success criteria

- Every published entry links to the source section it came from.
- No entry is visible to students until a reviewer approves it.
- A student can find the right entry for a question asked in their own words.
- Re-importing an unchanged source creates no duplicate entries.

## Stories and checks

| # | Story | Observable check | Status |
| --- | --- | --- | --- |
| 1 | As a student, I want to search in my own words, so I find the command without knowing its name | "How do I undo my last commit?" returns the matching Git entry | planned |
| 2 | As a student, I want each entry linked to its source, so I can read the original | Every published entry has a working source link | planned |
| 3 | As a reviewer, I want drafts held until I approve them, so wrong entries never reach students | A draft is not visible on the public reference until approved | planned |
| 4 | As a reviewer, I want to edit or reject a draft, so bad AI output is fixed or removed | Edited text is what gets published; rejected drafts never appear | planned |
| 5 | As the team, we want re-importing a source to skip unchanged content, so the queue isn't flooded with duplicates | Importing S01 twice adds no new drafts | planned |

## Owners and reviewers

_Proposed; Ann to confirm or change._

| Slice | Owner | Reviewer |
| --- | --- | --- |
| Source import, source tracking, duplicate checks (stories 2, 5) | Ann | Bridget |
| Draft generation, review queue and publishing (stories 3, 4) | Bridget | Ann |
| Search and the student-facing reference (story 1) | Bridget | Ann |
| Architecture choice, integration, evaluation and demo | Both, with named work | Cross-review + another real peer |

## Open questions

- Confirm with Professor Williams that his course sites and repos can be used as sources.
- Hosting: on one member's existing server, or both? (decide by Build)
