# FlowThis Visual Skill

An open Agent Skill for turning documents, research papers, repositories,
architecture notes, conversations, workflows, product ideas, and data reports
into polished, shareable, self-contained HTML visuals.

FlowThis Visual Skill is the open visual-generation layer behind FlowThis. It
does not require the FlowThis app to be useful: any compatible coding agent can
read the skill and generate a single HTML artifact with inline CSS/SVG, no
JavaScript, no external assets, clear provenance, readable diagrams, and a
structured reading path.

## Why this exists

Most AI-generated visuals fail in predictable ways: vague structure, overloaded
cards, arrows crossing text, one fixed theme applied to every topic, missing
source provenance, and no useful path for readers. This skill gives agents a
visual operating system:

- visual brief first
- source-type routing
- source-first styling
- reusable component recipes
- evidence rails
- no-JS interaction patterns
- boundary-safe diagram geometry
- comment-ready stable ids
- five quality gates before saving

## What it can visualize

- Research papers and PDFs
- GitHub repositories and codebases
- Cloud/software architecture
- Conversation history and debug sessions
- Product pages and advertisements
- User stories and team workflows
- Data reports and dashboards
- Learning and explainer content

## Install in Claude Code

Copy the skill into your personal Claude Code skills directory:

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

## Install in Codex

Codex can use the skill directly from an Agent Skills folder, or as a plugin.

Personal skill install:

```bash
mkdir -p ~/.agents/skills/flowthis
cp -R skills/flowthis/* ~/.agents/skills/flowthis/
```

For plugin packaging, the root of this repository includes a Codex plugin
manifest at `.codex-plugin/plugin.json`.

## Use with FlowThis Cloud

When FlowThis MCP tools are connected, the skill saves directly to your
FlowThis account with `create_visualization`. Without MCP, agents can still
write a local `flowthis-visual.html` file that can be uploaded manually.

The hosted FlowThis app remains separate from this open skill. This repository
is the public visual-generation standard; FlowThis Cloud is the hosted
workspace for saving, sharing, discussing, and revising visuals.

## Examples

- [`examples/repo-architecture.html`](examples/repo-architecture.html) shows a
  repo/system architecture visual with an editor-like explorer, boundary-safe
  SVG map, skill recipes, runtime flows, and quality gates.

Open the HTML file directly in a browser. It is self-contained.

## Repository layout

```text
.
  .codex-plugin/
    plugin.json
  skills/
    flowthis/
      SKILL.md
      agents/
        openai.yaml
      references/
        visualization-system.md
  examples/
    repo-architecture.html
  docs/
    design-principles.md
    contributing.md
  CHANGELOG.md
  LICENSE
```

## License

MIT. See [`LICENSE`](LICENSE).

