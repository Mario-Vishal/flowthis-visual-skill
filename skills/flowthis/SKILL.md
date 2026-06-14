---
name: flowthis
description: >-
  Turn conversations, documents, PDFs, research papers, repositories,
  architecture notes, product ideas, ads, user stories, debug timelines, PR
  summaries, or other context into polished FlowThis-owned self-contained HTML
  visuals. Use when the user says things like "visualize this", "make a
  FlowThis visual", "save this as a visual", "turn this document into a
  visual", "diagram this repo", "create a research paper visual", or runs
  /flowthis. Provides visual briefs, source-type routing, component recipes,
  evidence rails, no-JS interaction patterns, quality gates, and diagram
  guardrails when the user does not specify a layout.
---

# FlowThis: create a shareable visual

Your job is to transform the user's source material into one polished,
self-contained HTML document.

## 1. Decide what to visualize

- If the user named a focus, use it.
- Otherwise classify the source type and choose the default FlowThis pattern.
  Read `references/visualization-system.md` for routing, component patterns,
  interaction rules, and diagram rules whenever the source is a document/PDF,
  research paper, repo, architecture, conversation history, product/ad,
  user-story workflow, or data report.
- Start with a visual brief: source type, audience, confidence, reader job,
  primary insight, and what to inspect first.
- If the source is genuinely ambiguous, ask one short question.
- Keep the title short and specific.
- Add a source/provenance line when the visual is derived from a document, PDF,
  URL, repo, conversation, or meeting notes.

## 2. Generate the HTML

The HTML must be:

- A complete `<!doctype html>` page with everything inline.
- No JavaScript at all: no `<script>` and no inline event handlers.
- No external requests: no external stylesheets, fonts, remote images, or
  iframes. Images, if any, must be `data:` URIs.
- Styled with inline CSS and inline SVG.
- Animated only with CSS or SVG, never JavaScript.
- Responsive and readable on mobile and desktop.
- Free of secrets, tokens, credentials, private keys, and raw private source.
- Source-specific in style. Do not force FlowThis's own product palette unless
  the source is FlowThis or the user asks for it.
- Structured with stable section ids or `data-element-id` attributes where
  comments would naturally attach.

Aim for something genuinely worth sharing, not a placeholder.

## 3. Apply the FlowThis quality gates

Before finishing, revise until all five gates are acceptable:

- Clarity: the first screen explains the artifact without the original prompt.
- Structure: the page has a primary reading path.
- Geometry: arrows stop at boundaries and do not collide with text.
- Evidence: source-backed facts and inferred summaries are distinguishable.
- Share polish: title, provenance, summary, primary visual, detail sections, and
  read-next area are present.

## 4. Save or hand off

If FlowThis MCP tools are available:

1. Optionally call `list_groups` if the user wants a folder.
2. Call `create_visualization` with `title` and `html`.
3. Share the returned URL.
4. For revisions, read feedback with `get_visualization_suggestions`, fetch the
   current HTML with `get_visualization`, and publish a new version with
   `create_visualization_version`.

If FlowThis MCP tools are not available:

1. Write the document to `flowthis-visual.html` in the working directory.
2. Tell the user they can preview it locally and upload it manually to FlowThis.

Do not dump the full HTML into chat unless asked.

