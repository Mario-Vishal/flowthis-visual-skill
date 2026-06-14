# Design Principles

FlowThis Visual Skill is an operating system for agent-generated visuals, not a
fixed theme.

## Source-first identity

The source material chooses the visual identity. A codebase visual can feel like
an editor. A research paper can feel like an annotated brief. A product launch
can feel editorial. Do not stamp one brand skin onto every artifact.

## Progressive detail

Readers should get the gist in 20 seconds, understand the system in 2 minutes,
and inspect evidence only when they expand or navigate deeper.

## Evidence over decoration

Important claims need source anchors: files, sections, figures, comments, data
ranges, or an explicit inference label.

## Boundary-safe diagrams

Arrows stop at node boundaries. They do not enter boxes, cross text, or hide
meaningful labels. Dense systems become multiple focused diagrams.

## One file

Every output is one complete HTML file with inline CSS/SVG. No JavaScript, no
external fonts, no remote images, no iframes, and no network requests.

