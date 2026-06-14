<p align="center">
  <img src="assets/flowthis-visual-skill-mark.svg" width="96" alt="FlowThis Visual Skill mark">
</p>

<h1 align="center">FlowThis Visual Skill</h1>

<p align="center">
  An open Agent Skill for turning papers, repositories, architecture notes,
  conversations, workflows, and reports into polished, source-aware HTML visuals.
</p>

<p align="center">
  <a href="LICENSE"><img alt="MIT license" src="https://img.shields.io/badge/license-MIT-111827?style=for-the-badge"></a>
  <a href="skills/flowthis/SKILL.md"><img alt="Agent Skill" src="https://img.shields.io/badge/agent%20skill-FlowThis-2563EB?style=for-the-badge&logo=openai&logoColor=white"></a>
  <a href="examples/tokengate-repo-architecture.html"><img alt="HTML visual examples" src="https://img.shields.io/badge/examples-HTML%20visuals-16A34A?style=for-the-badge&logo=html5&logoColor=white"></a>
  <img alt="No JavaScript output" src="https://img.shields.io/badge/output-no%20JavaScript-D97706?style=for-the-badge&logo=javascript&logoColor=white">
</p>

<p align="center">
  <a href="#quick-start">Quick Start</a>
  | <a href="#examples">Examples</a>
  | <a href="#capabilities">Capabilities</a>
  | <a href="#output-contract">Output Contract</a>
  | <a href="https://flowthis.app">FlowThis Cloud</a>
</p>

<p align="center">
  <img src="assets/flowthis-visual-skill-demo.gif" alt="FlowThis Visual Skill demo">
</p>

FlowThis Visual Skill gives coding agents a visual operating system: classify
the source, choose the right structure, build a readable mini-site, keep
diagrams precise, label evidence, and ship one self-contained HTML file with no
JavaScript or remote assets.

## Why It Exists

Agents are good at generating HTML, but without a strong visual standard they
often produce generic cards, weak diagrams, overlapping arrows, vague summaries,
and layouts that do not match the source. This skill gives the agent a clear
default grammar for turning real context into reviewable visual documents.

Use it when you want an agent to produce a shareable visual that feels designed,
evidence-aware, and useful on the first pass.

## Capabilities

| Capability | What The Skill Enforces |
| --- | --- |
| <img src="https://img.shields.io/badge/brief-first-2563EB?style=flat-square" alt="Brief first"> | Source type, audience, confidence, reader job, and what to inspect first. |
| <img src="https://img.shields.io/badge/identity-source%20aware-16A34A?style=flat-square" alt="Source-aware identity"> | Repos, papers, products, workflows, and reports get distinct structures instead of one generic theme. |
| <img src="https://img.shields.io/badge/repos-deep%20architecture-7C3AED?style=flat-square" alt="Deep architecture"> | Codebase visuals explain modules, contracts, runtime paths, tests, risks, and exact files to inspect. |
| <img src="https://img.shields.io/badge/interaction-no%20JS-D97706?style=flat-square" alt="No JavaScript"> | Anchors, `:target`, `details`, and CSS states create navigable documents that work in strict sandboxes. |
| <img src="https://img.shields.io/badge/diagrams-boundary%20safe-DC2626?style=flat-square" alt="Boundary-safe diagrams"> | Arrows stop at node edges, flow direction is visible, icons identify component types, and maps use the full width. |
| <img src="https://img.shields.io/badge/evidence-labeled-0891B2?style=flat-square" alt="Evidence labeled"> | Source-backed facts and inferred summaries are visually separated. |

## Examples

| Example | What It Shows |
| --- | --- |
| [`TokenGate repository architecture`](examples/tokengate-repo-architecture.html) | A deep repo visual generated from [`Mario-Vishal/tokengate`](https://github.com/Mario-Vishal/tokengate), with animated architecture, semantic icons, directory previews, runtime notes, tests, and review targets. |
| [`Qwen3 technical report brief`](examples/qwen3-paper-brief.html) | A research-paper route generated from the open [`Qwen3 Technical Report`](https://arxiv.org/abs/2505.09388), with contribution cards, method map, evidence matrix, limitations, and read-next notes. |

The examples are self-contained HTML files. No secrets, env values, raw private
source, scripts, remote fonts, or external assets are embedded.

## Quick Start

### Claude Code

```bash
mkdir -p ~/.claude/skills/flowthis
cp -R skills/flowthis/* ~/.claude/skills/flowthis/
```

Then ask:

```text
/flowthis visualize this repo
```

or:

```text
Turn this research paper into a FlowThis visual.
```

### Codex

```bash
mkdir -p ~/.agents/skills/flowthis
cp -R skills/flowthis/* ~/.agents/skills/flowthis/
```

This repository also includes a Codex plugin manifest at
[`.codex-plugin/plugin.json`](.codex-plugin/plugin.json), so it can be packaged
as an installable Codex plugin.

## At A Glance

| Item | Detail |
| --- | --- |
| Primary output | Self-contained HTML visual |
| Runtime requirement | None for generated files |
| Interaction model | CSS and document anchors only |
| Best sources | Repositories, papers, architecture notes, conversations, workflows, reports |
| Hosted workflow | Save and discuss visuals in [FlowThis Cloud](https://flowthis.app) |
| License | MIT |

## Use With FlowThis Cloud

This repository is the public visual-generation standard. FlowThis Cloud is the
hosted workspace for saving, sharing, commenting on, and revising generated
visuals.

When FlowThis MCP tools are connected, agents can save directly through
`create_visualization`. Without MCP, agents can still write a local
`flowthis-visual.html` file that can be uploaded manually.

## Output Contract

Every generated visual should be:

- one complete `<!doctype html>` document
- inline CSS and inline SVG only
- no JavaScript
- no remote fonts, styles, scripts, images, or iframes
- responsive at mobile and desktop widths
- source-specific in palette, density, structure, and tone
- explicit about provenance and uncertainty
- lightly attributed at the bottom with `Generated with FlowThis Skill` and a
  source link
- structured with stable section ids where comments should attach

## Source Routes

| Source | Default Visual Pattern |
| --- | --- |
| Research paper / PDF | Paper brief with contributions, method map, experiments, limits, read-next |
| Repository / codebase | Deep architecture workspace, top summary, detailed file drill-down, large animated maps, flows, contracts, runtime, tests, risks |
| Software architecture | System boundaries, services, stores, request paths, failure points |
| Conversation / debug log | Timeline, decisions, blockers, current state, next actions |
| Product / advertisement | Offer page, audience, pain, benefits, proof, CTA |
| User stories / workflow | Actor map, journey lanes, handoffs, acceptance criteria |
| Data report | Headline insight, metric cards, charts, caveats, recommended action |

## Repository Layout

```text
.
  .codex-plugin/
    plugin.json
  assets/
    flowthis-visual-skill-demo.gif
    flowthis-visual-skill-mark.svg
  skills/
    flowthis/
      SKILL.md
      agents/
        openai.yaml
      references/
        visualization-system.md
  examples/
    tokengate-repo-architecture.html
    qwen3-paper-brief.html
  docs/
    design-principles.md
    contributing.md
  CHANGELOG.md
  LICENSE
```

## Contributing

Contributions should improve the visual standard without turning it into a
rigid template system. Useful additions include new source-type recipes, better
diagram geometry rules, stronger examples, accessibility improvements, and safer
no-JS interaction patterns.

See [`docs/contributing.md`](docs/contributing.md).

## License

MIT. See [`LICENSE`](LICENSE).
