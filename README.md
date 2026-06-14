# FlowThis Visual Skill

An open Agent Skill for turning papers, repositories, architecture notes,
conversations, workflows, and reports into polished, source-aware HTML visuals.

FlowThis Visual Skill gives coding agents a visual operating system: classify
the source, choose the right structure, build a readable mini-site, keep
diagrams precise, label evidence, and ship one self-contained HTML file with no
JavaScript or remote assets.

![FlowThis Visual Skill demo](assets/flowthis-visual-skill-demo.gif)

## Why It Exists

Agents are good at generating HTML, but without a strong visual standard they
often produce generic cards, weak diagrams, overlapping arrows, vague summaries,
and layouts that do not match the source. This skill gives the agent a clear
default grammar for turning real context into reviewable visual documents.

Use it when you want an agent to produce a shareable visual that feels designed,
evidence-aware, and useful on the first pass.

## What Makes It Different

- **Visual brief first:** source type, audience, confidence, reader job, and
  what to inspect first.
- **Source-first identity:** a repo can become an IDE-style explorer, docs
  workspace, directory mock, or wide architecture canvas; a paper can become an
  annotated brief; a product page can become an editorial share page.
- **Deep architecture by default:** repo visuals explain modules, contracts,
  runtime paths, tests, risks, and exact files to inspect.
- **Interactive without JavaScript:** anchors, `:target`, `details`, and CSS
  states create navigable documents that still work in strict sandboxes.
- **Crafted diagrams:** boundary-safe arrows, animated SVG flow paths, semantic
  icons, grouped system boundaries, and large maps that use the available width.
- **Evidence-aware summaries:** source-backed facts and inferred summaries are
  visually separated so readers know what is known and what is interpretation.

## Examples

| Example | What It Shows |
| --- | --- |
| [`TokenGate repository architecture`](examples/tokengate-repo-architecture.html) | A deep repo visual generated from [`Mario-Vishal/tokengate`](https://github.com/Mario-Vishal/tokengate), with animated architecture, semantic icons, directory previews, runtime notes, tests, and review targets. |
| [`Qwen3 technical report brief`](examples/qwen3-paper-brief.html) | A research-paper route generated from the open [`Qwen3 Technical Report`](https://arxiv.org/abs/2505.09388), with contribution cards, method map, evidence matrix, limitations, and read-next notes. |

The examples are self-contained HTML files. No secrets, env values, raw private
source, scripts, remote fonts, or external assets are embedded.

## Install

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
