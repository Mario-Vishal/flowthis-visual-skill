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
- Do not invent claims. Separate "stated in source" from "inferred summary".
- Every visual needs a visible reading path: start here, inspect the map, expand
  evidence, then decide next action.

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
  primary visual, and read-next area even when the prompt was vague.

## Input Router

When the user gives no layout instructions, classify the source and choose the
default pattern below.

| Source type | Default visual |
| --- | --- |
| Research paper, PDF, arXiv, technical report | Paper brief: problem, contributions, method pipeline, figures, experiments, limitations, takeaways |
| Repository, GitHub tree, codebase, system design | IDE architecture workspace: Mac/VS Code-style window, clickable Explorer tree, file tabs, editor/detail pane, service/data-flow diagram, key files, runtime/deploy map |
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
- Explorer-detail pair: literal IDE-style layout with an activity bar or window
  chrome, compact left navigation, selected file/folder state, tabs, and a
  right-side editor/detail pane.
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
- One-screen abstract rewrite: problem, approach, result, why it matters.
- Contribution cards: 3-5 claims tied to source sections when available.
- Method pipeline: inputs -> preprocessing -> model/method -> evaluation -> output.
- Figure digest: reproduce provided images only when available; otherwise draw
  simplified schematics and label them as summaries.
- Experiment matrix: datasets, baselines, metrics, main result.
- Limitations and assumptions.
- Read next: exact sections/figures to inspect in the original.

### Architecture / Repository

- System purpose and audience.
- Directory explorer: render the project structure as a literal Mac/VS Code-like
  IDE window. Include window chrome, a compact activity bar when useful, a left
  Explorer sidebar with folder/file icons, nested indentation, selected state,
  and editor tabs. The right editor/detail pane must change according to the
  selected folder/file using CSS-only anchors and `:target`.
- Selected item detail pane: for each important folder/file, show a document-like
  editor view with a title, path pill, short purpose, headings/subheadings,
  source-backed facts, inferred responsibilities, and review targets. Do not
  make it a generic card list.
- Architecture map: clients, API/server, background jobs, storage, external
  services, observability, and auth/security boundaries.
- Request or data-flow diagram for the most important path.
- Key contracts: routes, events, schemas, env vars, permissions.
- Risk map: bottlenecks, failure modes, deployment assumptions.

Architecture map recipes:

- Context map: users, clients, app/API, workers/jobs, stores, external systems.
- Request path: one important request from entry to persistence and response.
- Trust map: browser/app/content/origin boundaries, secrets, permissions, auth.
- Runtime map: local dev, preview, production, deploy-dependent services.
- Ownership map: which code paths own validation, storage, rendering, revision,
  and moderation.

Directory explorer rules:

- Put the tree on the left and the summary/detail pane on the right on desktop,
  inside a recognizable IDE/window frame.
- On mobile, stack the tree above the detail pane.
- Use CSS/HTML only: `details`, `summary`, anchor links, and `:target`.
  Selecting a file/folder in the left pane should update the right pane without
  JavaScript.
- Important folder rows need a one-line purpose. Important file rows need a
  one-line "contains/does" summary.
- Use simple inline SVG or CSS icons for folders, files, config, database,
  route/API, UI component, test, and documentation when they improve scanning.
- Keep the tree compact, like VS Code's Explorer. Avoid oversized folder cards.

### Conversation / Debug Timeline

- Context: what problem was being solved.
- Timeline: events in chronological order.
- Decision log: decision, reason, tradeoff, owner/status.
- Current state: what works, what is blocked, what is next.
- Open questions: only unresolved questions.

### Product / Advertisement

- Hero with product/offer name as the headline.
- Audience and pain point.
- Benefit stack with proof points.
- Feature or product sections with precise copy.
- Pricing/availability/status if provided.
- CTA area.

Use polished motion sparingly: CSS-only fades, line movement, reveal bands, or
subtle SVG strokes. Avoid stock-like filler, fake metrics, and empty hype.

### User Stories / Team Workflow

- Actor map.
- Journey stages or workflow lanes.
- User stories in cards: "As a..., I want..., so that...".
- Acceptance criteria and edge cases.
- Handoffs and ownership.
- Delivery plan or next sprint candidates.

### Data / Metrics

- The headline insight.
- Metric cards with units and date ranges.
- Charts with legends and axis labels.
- Explanation of trends and caveats.
- Recommended action.

Use SVG charts or CSS layout. Do not fake precision. If data is incomplete,
label it clearly.

## Diagram Geometry Rules

All diagrams must be readable before they are beautiful.

- Prefer SVG for diagrams. Use explicit coordinates and `viewBox`.
- Use `marker-end` arrowheads and stop connector lines at node boundaries.
- Never draw arrows through text.
- Never let arrowheads enter the interior of a box/circle. Leave 6-12px padding.
- Route connectors orthogonally or with gentle curves. Avoid diagonal clutter.
- Minimize crossings. If a crossing is unavoidable, add a tiny bridge/gap.
- Use consistent node sizes, alignment, and spacing.
- Use labels near connectors only when the label adds real meaning.
- Group systems by boundary: user/client, app/API, worker/job, database/storage,
  external provider, security/trust boundary.
- For dense systems, make multiple diagrams instead of one overloaded diagram.

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
- Share gate: title, provenance, summary, visual map, detail sections, and
  read-next are present.

If a gate fails, simplify before adding more visuals.

## Hard Restrictions

- No JavaScript.
- No inline event handlers.
- No remote scripts, fonts, stylesheets, images, iframes, or hotlinked images.
- No secrets, tokens, private keys, credentials, or raw private source.
- No UI that only works after script execution.
