# 3. Group content system + problem research: Plan

[Back to index](../README.md)

## Changed / checked / next

- **Changed (Plan, Nov 15–17):** The first draft proposed the concept, sources, workflow, retrieval approach, stories and owner/reviewer split, and each member reviewed it. Dhruvi's review ([#2](https://github.com/mcbridgeee/is373-group-course-reference/issues/2)) made E1, E2 and E5 measurable with a top-three rule and a no-match message. Ann's review ([#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1)) led to story 5 and E7 defining how a re-import detects unchanged content and what it reports. The Nov 17 source check corrected S02, S04 and S05.
- **Checked (actually run):** the [source check on Nov 17](#source-check-run-on-nov-17-executed-not-planned) cloned or opened all five sources and confirmed the S01 text used in the trace. Every story and evaluation item is still `planned`; nothing has been built.
- **Next:** an outside peer (from another team) follows the source trace and questions one assumption ([#3](https://github.com/mcbridgeee/is373-group-course-reference/issues/3)); all three members mark the decisions they agree to as `agreed` in the index; confirm sources and team size with Professor Williams; choose hosting before Build.

## Reader, problem and research question

- **Reader:** IS373 students, especially anyone who is behind, new to the command line, or returning to the material before Demo Day.
- **Problem:** course information is spread across Canvas pages, announcements, several course sites and many GitHub repos. Finding one command, what it does and why you'd use it, or what a term like "Traefik" or "chunking" means, takes digging through a dozen pages. (Course direction: **educational-content publishing**.)
- **Research question:** can AI turn the course's own material into a reference students can trust, if every entry is linked to its source and checked by a person before it's published?
- **Why this is more than a chat:** the shared workflow is the **review queue**. AI drafts, a human approves or edits, and only approved entries become the published reference. Students read a reviewed reference, not raw model output.

## Permitted sources

Course materials provided by the instructor for this course, used within the course for a course assignment. _Confirm with Professor Williams in class and note the date here._

| ID | Source | URL | What we take from it | Date checked |
| --- | --- | --- | --- | --- |
| S01 | Linux, Vim, Git, Docker and Python Survival Guide (README) | https://github.com/kaw393939/linux_vim_git_docker_python_survival_guide | Git workflow commands (issue → branch → commit → PR) | 2026-11-17 |
| S02 | Server Studio (373_hosting): README plus the `book/` chapters | https://github.com/kaw393939/373_hosting | Docker Compose, Traefik and HTTPS commands and terms (the commands are in `book/04-deploy.md`, `book/07-operations.md` and `book/10-application-delivery.md`, not the README) | 2026-11-17 |
| S03 | App Studio (is373-app-studio) README | https://github.com/kaw393939/is373-app-studio | FastAPI, local Python and test/check commands (`python3 studio.py check` runs Black, Pylint and pytest) | 2026-11-17 |
| S04 | IS373 Studio course site: overview, plus the linked milestone checklist | https://kaw393939.github.io/is373-studio/course/overview.html | Course terms: Plan, Build, Checked Release, Improve, project record (the overview names them; definitions come from the milestone checklist) | 2026-11-17 |
| S05 | IS373 RAG student guides | https://kaw393939.github.io/is373-rag/students/ (redirects to keithwilliams.org/is373-rag/students/) | Technical terms from "Embeddings and similarity," "Chunking and source boundaries" and "Databases and retrieval" (closest guide to vector search) | 2026-11-17 |

Each source keeps a stable ID, URL and the date we imported it. If a page changes, re-import sends only the changed sections' entries back to review (see story 5).

### Source check run on Nov 17 (executed, not planned)

| Source | What we checked | Result | Change it caused |
| --- | --- | --- | --- |
| S01 | Cloned the repo (commit `e863cbe`) and searched for the traced command | Found in README §3 "Issue → Branch → Pull Request," step 3: "Make focused commits. Stage only your task's files and reference the issue," followed by the `git commit -m` example | None; confirms the trace, and the "stage first" point the reviewer is meant to catch is in the source |
| S02 | Cloned the repo (commit `0a149f0`) and searched for `docker compose` and Traefik | The README mentions Docker/Traefik only as prerequisites; the commands are in the `book/` chapters | Updated S02 to name the `book/` chapters, so import must cover more than the README |
| S03 | Cloned the repo (commit `ced701d`) and read the README | FastAPI and the `studio.py check` command are there | Updated S03 wording to match what the README actually contains |
| S04 | Opened the overview page | Page exists and names the four stages and the project record, but does not define them | Updated S04 to include the milestone checklist as the source of definitions |
| S05 | Opened the student guides page | Page exists but redirects to keithwilliams.org; embeddings and chunking have their own guides, and vector search sits under "Databases and retrieval" | Recorded the redirect, because import must store the final URL so source links don't break |

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

**Trace (the source step was verified against S01 on Nov 17; every later step is a planned sketch, not executed):**

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
- Re-importing an unchanged source creates no duplicate entries, and re-importing a changed source tells the person which sections changed.

## Stories and checks

| # | Story | Observable check | Status |
| --- | --- | --- | --- |
| 1 | As a student, I want to search in my own words, so I find the command without knowing its name | "How do I undo my last commit?" returns the matching Git entry | planned |
| 2 | As a student, I want each entry linked to its source, so I can read the original | Every published entry has a working source link | planned |
| 3 | As a reviewer, I want drafts held until I approve them, so wrong entries never reach students | A draft is not visible on the public reference until approved | planned |
| 4 | As a reviewer, I want to edit or reject a draft, so bad AI output is fixed or removed | Edited text is what gets published; rejected drafts never appear | planned |
| 5 | As the team, we want re-importing a source to skip unchanged content and tell us when content changed, so the queue isn't flooded with duplicates and real changes aren't missed | Each imported section stores a hash of its text. Importing S01 twice in a row adds no new drafts and reports "no changes." Editing one section in a test copy of S01 and re-importing reports that one section as changed and sends only its entries back to review. ([#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1)) | planned |

## Evaluation set

Planned student questions, written before anything is built. Expected sources are predictions to check once entries exist.

| # | Type | Student question | Expected entry / source | Expected behavior | Status |
| --- | --- | --- | --- | --- | --- |
| E1 | Exact term | `git commit -m` | Git commit entry · S01 §3 | Run keyword and vector search. Record the expected entry’s rank for each, or record no match. Each method passes if the entry appears in its top three results. | planned |
| E2 | Paraphrase | How do I save my changes with a message? | Git commit entry · S01 §3 | Run keyword and vector search. Record the expected entry’s rank for each, or record no match. Each method passes if the entry appears in its top three results. | planned |
| E3 | Related terms | What does Traefik have to do with Docker? | Traefik glossary entry and its reviewed related-term link · S02 | Shows the Traefik entry and links to the Docker entry | planned |
| E4 | Ordinary useful | What is chunking? | Chunking glossary entry · S05 | Plain-English meaning with a source link | planned |
| E5 | Not covered | How do I deploy to AWS? | none | Passes if the UI shows “No matching entry in the course reference” and displays zero results. | planned |
| E6 | Review gate | Search for a term whose entry is still a draft | none publicly | Draft does not appear until a reviewer approves it | planned |
| E7 | Re-import | Import S01, import it again unchanged, then import a test copy with one section edited | Same S01 entries · no new drafts on the second import | Second import reports "no changes" and adds zero drafts; third import reports exactly one changed section and queues only that section's entries for review | planned |

## Owners and reviewers

_Ann accepted her slice in [#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1); Dhruvi accepted the AI drafting slice on Nov 17._ We are a team of three; the brief starts from pairs, so we will confirm the team size with Professor Williams. Each slice has an owner and a different reviewer, and the reviews rotate so everyone checks someone else's work.

| Slice | Owner | Reviewer |
| --- | --- | --- |
| Source import, source tracking, duplicate checks (stories 2, 5) | Ann | Bridget |
| AI drafting: entry format, prompts, quality of drafts against sources | Dhruvi | Ann |
| Review queue, publishing, and the student-facing reference and search (stories 1, 3, 4) | Bridget | Dhruvi |
| Architecture choice, integration, evaluation and demo | All three, with named work | Cross-review + another real peer |

## Open questions

- Confirm with Professor Williams that his course sites and repos can be used as sources, and that a team of three is OK.
- Hosting: on one member's existing server, or both? (decide by Build)

## Help received

- AI: Claude helped draft this plan's structure, compare approaches and check that the sources exist. The team reviews and owns the decisions.
- Teammates: we discussed the plan in our team group chat. Ann's review of story 5 ([#1](https://github.com/mcbridgeee/is373-group-course-reference/issues/1)) and Dhruvi's review of the evaluation set ([#2](https://github.com/mcbridgeee/is373-group-course-reference/issues/2)) each changed the plan.
- Outside peer: not yet. A walkthrough of the source trace by someone from another team is planned for the Nov 17/19 workshop ([#3](https://github.com/mcbridgeee/is373-group-course-reference/issues/3)).
