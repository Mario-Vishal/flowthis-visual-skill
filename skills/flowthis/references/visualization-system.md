# FlowThis Visualization System

Use this reference whenever a user asks FlowThis to visualize a document, PDF,
repo, architecture, conversation, plan, product idea, advertisement, or any
context without specifying an exact layout. FlowThis owns the default visual
language. The agent owns source understanding and final assembly.

## Core Contract

- Create one complete, self-contained HTML document.
- Treat the visual as a readable mini-website, not a static screenshot.
- Start with a visual brief before designing: audience, source type, reader job,
  primary insight, confidence level, and the one thing the reader should inspect
  first.
- Make the first viewport immediately explain what this is, why it matters, and
  what the reader can do next.
- Prefer clear structure over decoration: title, short summary, labeled
  sections, visual map, evidence/details, and provenance.
- Choose a visual identity from the source material. Do not force the FlowThis
  product palette, logo style, or green accent into the artifact unless the
  source is specifically about FlowThis or the user asks for it.
- For long inputs, include a sticky or side table of contents with anchor links.
- Keep all navigation CSS/HTML only. Use anchors, `details`, `summary`, and
  `:target` patterns. Do not use JavaScript.
- Add a small provenance line when the visual is derived from a document, paper,
  URL, repo, meeting, or conversation: "Source: <type/title/date if known>".
- Add a lightweight bottom attribution on shareable visuals: `Generated with
  FlowThis Skill` and `Source: <source title or URL>`. Keep it aligned,
  unobtrusive, and professional. Link the word `FlowThis` when a website URL is
  available, but do not add remote images, scripts, fonts, or badges.
- Do not invent claims. Separate "stated in source" from "inferred summary".
- Every visual needs a visible reading path: start here, inspect the map, expand
  evidence, then decide next action.

## Depth Contract

Visual polish is not enough. Every artifact must increase understanding of the
source, not merely package it.

- Optimize for UI plus depth: every major section should explain what the thing
  is, how it works, why it matters, what evidence supports it, what tradeoffs it
  creates, and what the reader should inspect next.
- Prefer dense-but-readable explanation over vague marketing copy. A beautiful
  page with generic rectangles and shallow summaries fails the skill.
- Use the number of diagrams the source needs. A complex paper, architecture, or
  workflow can require multiple focused diagrams rather than one overloaded map.
- Use tables whenever comparisons, tradeoffs, baselines, ablations, risks,
  assumptions, metrics, or design choices would be clearer in rows and columns.
- Separate summary from analysis. A summary says what the source states; an
  analysis explains mechanisms, implications, alternatives, and limits.
- Add depth progressively: gist first, then mechanism, evidence, tradeoffs,
  limitations, and read-next references.

## FlowThis Signature

FlowThis should feel different from a generic LLM HTML dump because it applies
an opinionated visual operating system while still allowing freeform output.

- Visual DNA: every artifact declares its source type, audience, confidence, and
  navigation model through small chips or a compact meta row.
- Source-first styling: palette, density, icon set, and motion come from the
  material. A codebase visual can feel like an editor; a paper can feel like an
  annotated brief; a product launch can feel editorial.
- Component recipes, not rigid templates: use the source router and recipes as
  defaults, then adapt the composition to the content.
- Evidence rails: important claims should be tied to source sections, files,
  figures, commits, comments, or clearly marked inference.
- Progressive detail: readers should get the gist in 20 seconds, the system in 2
  minutes, and the evidence only when they expand or navigate deeper.
- Comment-ready structure: major sections and meaningful diagram nodes should
  have stable `id` or `data-element-id` attributes.
- Share polish: the page should have a title, source line, compact summary,
  primary visual, read-next area, and lightweight bottom attribution even when
  the prompt was vague.

## Input Router

When the user gives no layout instructions, classify the source and choose the
default pattern below.

| Source type | Default visual |
| --- | --- |
| Research paper, PDF, arXiv, technical report | Paper brief: problem, contributions, method pipeline, figures, experiments, limitations, takeaways |
| Repository, GitHub tree, codebase, system design | Deep architecture workspace: source-aware summary, detailed repo/file drill-down, large animated architecture diagrams, key flows, contracts, runtime/deploy/security maps |
| Cloud/software architecture | System map: actors, services, data stores, trust boundaries, request flows, failure points |
| Conversation history, meeting notes, debug session | Narrative timeline: context, decisions, open questions, blockers, next actions |
| Product/advertisement/launch copy | Polished product page: offer, audience, benefit stack, feature proofs, CTA blocks |
| User stories, process, team workflow | Workflow board: actors, jobs-to-be-done, journey states, handoffs, acceptance criteria |
| Data/report/metrics | Dashboard narrative: headline numbers, comparisons, trends, explanation, caveats |
| Learning/explainer content | Guided lesson: concept map, steps, examples, pitfalls, recap |

If the source fits multiple types, combine only the top two. Avoid building a
giant omnibus page.

## Universal Layout

Use this page skeleton unless the user asks otherwise:

1. Hero/header: title, one-sentence purpose, source/provenance, status chips.
2. Executive summary: 3-6 concise bullets or cards.
3. Primary visual: diagram, flow, map, timeline, matrix, or dashboard.
4. Detail sections: anchored sections with evidence, explanations, and caveats.
5. Reader actions: open questions, next steps, or what to inspect first.

For long documents, use:

- A desktop sidebar TOC and a compact mobile top TOC.
- Section ids and anchor links.
- `details` blocks for dense evidence and long code snippets.
- A "Start here" block for non-expert readers.

## Component Recipes

Use these reusable structures before inventing a new component:

- Visual brief strip: source, audience, confidence, last updated, and primary
  action.
- Start-here panel: 3-5 bullets that tell a new reader what to understand first.
- Evidence rail: short source-backed facts beside the main narrative.
- Focus map: one primary diagram with grouped boundaries and boundary-safe
  connectors.
- Decision ledger: decision, reason, tradeoff, owner/status.
- Risk board: risk, why it matters, mitigation, deploy/runtime owner.
- Comparison matrix: options vs criteria, with a visible recommendation only if
  the source supports it.
- Technical deep-dive panel: mechanism, assumptions, inputs, outputs, failure
  modes, and "why this design exists".
- Approach comparison table: prior/baseline approach, proposed approach,
  advantage, cost, failure mode, and evidence.
- Tradeoff matrix: choice, benefit, cost, operational/research risk, when it
  wins, when it fails.
- Ablation/results table: variant, changed component, metric movement, likely
  interpretation, caveat.
- Equation/algorithm explainer: symbol glossary, step-by-step interpretation,
  intuition, and implementation/evaluation impact.
- Explorer-detail pair: compact left navigation with selected file/folder state
  and a right-side detail pane. This can look like an IDE, docs workspace,
  directory mock, or file-preview browser depending on the source.
- Architecture canvas: a full-width SVG/system map with meaningful icons,
  grouped boundaries, semantic node shapes, animated flow arrows, and drill-down
  anchors for important components.
- Figure digest: image or schematic, caption, what it proves, caveat.
- Read-next footer: exact files, sections, figures, prompts, or tasks to inspect.

## No-JS Interaction Recipes

- Anchor navigation with `:target` highlighting for sections and selected items.
- `details` / `summary` for evidence, long notes, code, and caveats.
- CSS-only tabs with radios only when the state remains accessible and readable
  without interaction.
- Hover/focus reveal for secondary labels, never for essential content.
- SVG/CSS motion only when it communicates flow, progress, or dependency.

## Source Patterns

### Research Paper / PDF

- Paper identity: title, authors if known, venue/date if known, source URL/file.
- One-screen abstract rewrite: problem, approach, result, why it matters. Keep
  it technical and precise; avoid ad-style copy.
- Problem formulation: task, inputs, outputs, constraints, assumptions, and why
  prior approaches are insufficient when the paper explains it.
- Contribution map: 3-5 claims tied to source sections, figures, tables, or
  equations when available.
- Method deep dive: inputs -> preprocessing -> model/method -> training or
  optimization -> evaluation -> output. Explain the mechanism, not only labels.
- Algorithm/equation explainer when present: define symbols, explain the steps
  in plain language, and connect the math to implementation or result.
- Approach comparison table: baseline/prior method, proposed change, advantage,
  cost, failure mode, and evidence.
- Tradeoff matrix: accuracy/quality, compute, data needs, latency, robustness,
  interpretability, reproducibility, and deployment fit when relevant.
- Experiment matrix: datasets, baselines, metrics, main result, statistical or
  qualitative caveat.
- Ablation table when present: variant, removed/changed component, metric
  movement, interpretation, caveat.
- Figure digest: reproduce provided images only when available; otherwise draw
  simplified schematics and label them as summaries.
- Multiple focused diagrams when useful: problem setup, method pipeline, model
  architecture, training/evaluation loop, data flow, loss/objective, results
  comparison, and failure modes. Do not force everything into one diagram.
- Limitations, assumptions, and threats to validity.
- Reproducibility checklist: data availability, code availability, compute,
  hyperparameters, evaluation protocol, and missing details when known.
- Critical reading notes: what is strong, what is uncertain, what evidence would
  change the conclusion.
- Read next: exact sections/figures to inspect in the original.

Research paper quality bar:

- The visual should feel like a technical reading companion, not a product
  advertisement.
- A reader should understand the paper's core mechanism, evidence, tradeoffs,
  and limitations without having to read the full paper first.
- Prefer tables for baselines, metrics, ablations, and tradeoffs; prefer
  diagrams for mechanism, data flow, architecture, and evaluation loops.
- If the source does not provide a detail, label it as "not specified in source"
  instead of guessing.

### Architecture / Repository

- System purpose and audience.
- Top summary: include a source-aware summary of what the system does, the core
  loop, key entrypoints, architecture focus, and review lens. Do not make the
  repo visual feel like only a source tree.
- Deep repo explanation: go beyond high-level modules. Explain important
  folders/files with responsibilities, inbound/outbound dependencies, data
  contracts, config/env surfaces, tests, runtime assumptions, and review targets.
  When source access is limited, label what is inferred.
- Directory explorer or directory mock: show the project structure with
  folder/file icons, nested indentation, selected state, and per-item summaries.
  The layout can be a Mac/VS Code-like IDE, a docs-style workspace, a file
  preview browser, or a directory with PNG/screenshot-like preview tiles. Use the
  pattern that makes the architecture easiest to understand.
- Selected item detail pane: for each important folder/file, show a document-like
  detail view with a title, path pill, short purpose, headings/subheadings,
  source-backed facts, inferred responsibilities, contracts, and review targets.
  Do not make it a generic card list.
- Architecture map: clients, API/server, background jobs, storage, external
  services, observability, and auth/security boundaries.
- Request or data-flow diagram for the most important path.
- Key contracts: routes, events, schemas, env vars, permissions.
- Risk map: bottlenecks, failure modes, deployment assumptions.
- Evidence/read-next map: exact files, classes/functions, routes, migrations,
  tests, or docs to inspect after the visual.

Architecture map recipes:

- Context map: users, clients, app/API, workers/jobs, stores, external systems.
- Request path: one important request from entry to persistence and response.
- Trust map: browser/app/content/origin boundaries, secrets, permissions, auth.
- Runtime map: local dev, preview, production, deploy-dependent services.
- Ownership map: which code paths own validation, storage, rendering, revision,
  and moderation.
- Dependency map: which modules call, configure, store, or render each other.
- Data model map: entities/tables/files, ownership, lifecycle, and mutation
  paths.

Architecture visual depth rules:

- The primary architecture diagram should use most of the available width. Avoid
  narrow, card-sized maps. Use constrained inner widths only for text-heavy
  reading sections, not for the main system canvas.
- If an IDE/window frame is used, expand the frame to the page width and make the
  architecture pane or tab large enough to inspect without zooming.
- Avoid generic plain rectangles. Use semantic visual language: browser/device
  frames for clients, service cards with icon headers for APIs/workers, database
  cylinders for DBs, stacked pages for documents/files, queue rails for events,
  shield/lock badges for auth/security, gear badges for config/runtime, and
  test/check icons for verification.
- Use inline SVG icon symbols or CSS-drawn icons only. Keep icons consistent in
  stroke weight and style. Icons should clarify component type, not decorate.
- Add CSS/SVG-only flow animation where it improves comprehension: animated
  `stroke-dashoffset` arrows, moving dots along paths, soft pulses at handoff
  points, or direction markers. Respect `prefers-reduced-motion`.
- Use distinct visual treatments for request flow, data persistence, auth/trust,
  and background/async work. Do not make every connection the same color or
  weight.
- Break large systems into multiple full-width maps: context, request path,
  runtime/deploy, trust/security, data model, and ownership. Link them through
  anchors or directory/mock items.

Directory explorer rules:

- Put the tree on the left and the summary/detail pane on the right on desktop,
  when using an explorer layout. The frame can be an IDE, docs browser, file
  preview workspace, or source-aware directory mock.
- Include an explicit `Architecture` folder or Explorer item near the top when a
  tree is present. Put key system maps and flow diagrams there instead of hiding
  them as tiny tabs or lowercase side labels.
- On mobile, stack the tree above the detail pane.
- Use CSS/HTML only: `details`, `summary`, anchor links, and `:target`.
  Selecting a file/folder in the left pane should update the right pane without
  JavaScript.
- When the selected item is an architecture map, let the diagram fill most of
  the right detail pane. The frame is already a constraint, so avoid small inset
  diagrams unless the map is secondary.
- Important folder rows need a one-line purpose. Important file rows need a
  one-line "contains/does" summary. For richer repo visuals, add tiny preview
  thumbnails or PNG/screenshot-like tiles for docs, diagrams, dashboards, or
  important rendered files when source material supports it.
- Use simple inline SVG or CSS icons for folders, files, config, database,
  route/API, UI component, test, and documentation when they improve scanning.
- Keep the tree compact, like VS Code's Explorer. Avoid oversized folder cards.

### Conversation / Debug Timeline

- Context: what problem was being solved.
- Timeline: events in chronological order.
- Decision log: decision, reason, tradeoff, owner/status, and evidence.
- Root-cause or hypothesis map when the conversation is a debug session.
- Evidence table: symptom, observation, command/log/source, implication.
- Current state: what works, what is blocked, what is next.
- Open questions: only unresolved questions.

### Product / Advertisement

- Hero with product/offer name as the headline.
- Audience and pain point.
- Benefit stack with proof points.
- Feature or product sections with precise copy.
- Pricing/availability/status if provided.
- CTA area.
- Claim/evidence table when the source includes proof, metrics, testimonials,
  benchmarks, or comparisons.

Use polished motion sparingly: CSS-only fades, line movement, reveal bands, or
subtle SVG strokes. Avoid stock-like filler, fake metrics, and empty hype.

### User Stories / Team Workflow

- Actor map.
- Journey stages or workflow lanes.
- User stories in cards: "As a..., I want..., so that...".
- Acceptance criteria and edge cases.
- Handoffs and ownership.
- Delivery plan or next sprint candidates.
- Tradeoff and dependency table for scope, risk, effort, sequencing, and owner.

### Data / Metrics

- The headline insight.
- Metric cards with units and date ranges.
- Charts with legends and axis labels.
- Explanation of trends and caveats.
- Recommended action.
- Method notes: source, date range, filters, sample size, calculation formula,
  missing data, and confidence.
- Segment or cohort tables when totals hide important differences.

Use SVG charts or CSS layout. Do not fake precision. If data is incomplete,
label it clearly.

## Diagram Geometry Rules

All diagrams must be readable before they are beautiful.

- Prefer SVG for diagrams. Use explicit coordinates and `viewBox`.
- Use `marker-end` arrowheads and stop connector lines at node boundaries.
- Never draw arrows through text.
- Never let arrowheads enter the interior of a box/circle. Leave 6-12px padding.
- For architecture diagrams, prefer visible direction: marker-end arrowheads
  plus animated dashed strokes or moving dots when motion helps explain flow.
- Route connectors orthogonally or with gentle curves. Avoid diagonal clutter.
- Minimize crossings. If a crossing is unavoidable, add a tiny bridge/gap.
- Use consistent node sizes, alignment, and spacing.
- Use labels near connectors only when the label adds real meaning.
- Group systems by boundary: user/client, app/API, worker/job, database/storage,
  external provider, security/trust boundary.
- For dense systems, make multiple diagrams instead of one overloaded diagram.
- Use icons and semantic shapes to encode component type; avoid a page that
  looks like plain rectangles with labels.

### Boundary-aware arrow recipe

For a rectangle-to-rectangle flow:

1. Pick anchor points on the box edges, not centers.
2. Start at the source edge plus 2px outside.
3. End at the target edge minus arrowhead padding.
4. Add a label at the midpoint with a small background pill if needed.
5. Test visually at mobile and desktop widths.

For circle/database nodes, compute or approximate the edge point. Do not connect
to the center unless the line is hidden behind a boundary-safe marker.

## Visual Style

- Default style: minimal, premium, readable, calm.
- Use a dynamic palette selected from the source type, audience, and mood.
- Use one or two purposeful accents plus neutral surfaces.
- Icons are encouraged when they clarify scanning.
- Architecture visuals should feel crafted: meaningful icons, semantic shapes,
  animated flow lines, large readable maps, and source-aware color roles. Avoid
  default-looking boxes connected by static arrows.
- Keep cards at 8px radius or less unless the surrounding style supports more.
- Avoid glass effects, blurred blobs, ornamental gradients, and decoration that
  does not explain content.
- Use system fonts.
- Make text fit at mobile and desktop sizes.
- Use CSS-only animation only when it clarifies flow, progress, or attention.

## Quality Gates

Score the artifact before saving. Revise until all five gates are acceptable:

- Clarity gate: a reader understands the artifact's purpose without the original
  prompt.
- Structure gate: the page has a primary path, not a pile of unrelated cards.
- Geometry gate: diagrams have boundary-safe arrows, no text collisions, and
  readable spacing at desktop and mobile widths.
- Evidence gate: source-backed statements and inferred summaries are visually
  distinguishable.
- Depth gate: the artifact explains mechanisms, tradeoffs, limits, and evidence
  beyond a surface summary.
- Share gate: title, provenance, summary, visual map, detail sections, and
  read-next are present.

If a gate fails, simplify before adding more visuals.

## Hard Restrictions

- No JavaScript.
- No inline event handlers.
- No remote scripts, fonts, stylesheets, images, iframes, or hotlinked images.
- No secrets, tokens, private keys, credentials, or raw private source.
- No UI that only works after script execution.
