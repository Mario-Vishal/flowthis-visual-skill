# Design Principles

FlowThis Visual Skill is an operating system for agent-generated visuals, not a
fixed theme.

## Source-first identity

The source material chooses the visual identity. A codebase visual can feel like
an editor, docs workspace, directory mock, or wide architecture canvas. A
research paper can feel like an annotated brief. A product launch can feel
editorial. Do not stamp one brand skin onto every artifact.

## Progressive detail

Readers should get the gist in 20 seconds, understand the system in 2 minutes,
and inspect evidence only when they expand or navigate deeper.

## Evidence over decoration

Important claims need source anchors: files, sections, figures, comments, data
ranges, or an explicit inference label.

## Boundary-safe diagrams

Arrows stop at node boundaries. They do not enter boxes, cross text, or hide
meaningful labels. Dense systems become multiple focused diagrams.

## Architecture craft

Architecture visuals should not look like plain rectangles joined by static
lines. Use meaningful inline SVG icons, semantic node shapes, grouped
boundaries, large full-width canvases, and CSS/SVG-only animated flow arrows
when motion clarifies request, data, auth, or background work.

## Repo depth

Repository visuals should let a reader go deep. Explain important folders and
files, contracts, dependencies, runtime assumptions, tests, risks, and exact
read-next paths. A source tree alone is not enough.

## One file

Every output is one complete HTML file with inline CSS/SVG. No JavaScript, no
external fonts, no remote images, no iframes, and no network requests.
