# Contributing

Contributions should improve the visual standard without turning it into a
rigid template system.

Good contributions:

- new source-type recipes
- better diagram geometry, icon, animation, and full-width architecture rules
- stronger repo/codebase depth patterns for contracts, runtime, tests, risks,
  and read-next paths
- safer no-JS interaction patterns
- stronger examples
- clearer quality gates
- accessibility improvements
- security improvements

Avoid:

- forcing one visual theme onto every artifact
- adding JavaScript-only behavior
- adding remote assets or hotlinked images
- embedding proprietary source or secrets in examples
- broad, vague prompt text that makes the skill trigger for unrelated tasks

Before opening a pull request, check:

- examples are self-contained HTML
- examples contain no scripts, iframes, external links, or inline event handlers
- diagrams are readable at desktop and mobile widths
- architecture visuals use meaningful icons/semantic shapes when they clarify
  component types
- architecture flow animation, when present, is CSS/SVG-only and respects reduced
  motion
- source-backed claims and inference are visually distinguishable
