# Plugin with Brain

Plugin with Brain is a set of four AI skills for turning reference material and project requirements into maintainable plugins, skills, and agent instructions.

## Objective

Use the plugin to extract useful rules from books, Markdown notes, and documentation, decide where those rules belong, and turn them into instructions with observable checks.

## Features

- **analyze-sources** captures findings, source locations, conditions, and proposed uses.
- **agents** defines or improves persistent instructions for an AI agent.
- **skill** authors, evaluates, and revises individual skills.
- **plugin** designs or reviews package structure, manifests, and documentation.

## Requirements and usage

Use a host that supports portable Agent Plugins packages and discovers skills under `skills/`. This package contains Markdown instructions and a JSON manifest. Any tools needed to inspect sources, edit target files, or run checks depend on the host and the specific task.

After importing the package, describe the desired change and provide the relevant files or source material. For example, ask “Use my Markdown notes to draft a skill for checking SQL join cardinality,” or “Review this plugin structure and suggest the smallest changes needed.”

## Architecture

Each skill owns one part of the workflow and can be used by itself. `plugin.json` describes the package. The repository's AI_Customization.md informed the design, and the packaged instructions are self-contained.

Use fenced `txt` blocks for file trees, architecture diagrams, nodes, and execution paths. Label branch conditions and distinguish examples from observed execution.

## Limitations

Host import and skill activation require verification on the destination platform.

## File index

```txt
plugin-with-brain/
├── README.md
├── plugin.json
└── skills/
    ├── agents/SKILL.md
    ├── analyze-sources/SKILL.md
    ├── plugin/SKILL.md
    └── skill/SKILL.md
```
