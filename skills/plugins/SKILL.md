---
name: plugin
description: Design, organize, evaluate, and improve AI plugins. Use to select components, structure a package, review a manifest or README, or verify a plugin before use or packaging.
---

# Objective

Organize a plugin around concrete use cases. Give each component a clear responsibility and verify that the package, documentation, and actual behavior agree.

## When to use and inputs

Use for plugin architecture, structural diagnosis, manifests, and package documentation. Gather the objective, representative requests, target platform, and delivery format. For an update, inspect the actual tree, current manifest, documentation, dependencies, and affected components. Consult the plugin, README, and skill sections of AI_Customization.md if present in the working project.

Use [skill](../skill/SKILL.md) to author individual skills, [analyze-sources](../analyze-sources/SKILL.md) to extract knowledge from documents, and [agents](../agents/SKILL.md) to define persistent behavior.

## Procedure

1. Define what the plugin should return for a typical request. Identify which parts require instructions, reference knowledge, executable code, or integrations.
2. For existing packages, distinguish implemented capabilities from proposals. Check identifiers and paths, find overlapping responsibilities, and identify consumers before moving shared resources.
3. Keep procedures in `skills/`, skill-specific resources alongside their skill, and shared code in `src/` when needed. Add tests, examples, configuration, or orchestration when they serve a specific use case. Group shared code by language only if it improves navigation.
4. Follow the target platform's manifest and package conventions. Keep credentials outside the package. For executable tools, define inputs, validation, processing, verification, outputs, and error behavior.
5. Draft or update the README using the template below. Include supported requirements and usage steps. Keep detailed task procedures in their skills and update the index to match the actual tree.
6. Parse the manifest, check skill names, paths and links, and walk through a typical request and an invalid input. When available, test discovery and execution in the target host. Distinguish package inspection from installation and runtime verification.

### Copyable README.md template

Replace the prompts with project details. Omit sections that add no information and list only files and directories that exist in the documented package.

````markdown
# Plugin Name

Briefly explain what the plugin does and who it serves.

## 1. Objective

State the problem and intended outcome.

## 2. Features

- List the capabilities and their expected results.

## 3. Requirements

List the supported platform, dependencies, or configuration.

## 4. Installation and usage

Explain how to install, configure, and use the plugin.
Include one representative request when useful.

## 5. Architecture

Explain what each component owns and how components interact.

## 6. Limitations

State unsupported cases and known constraints.

## 7. File index

```txt
my-plugin/
├── README.md
├── plugin.json         # Example manifest location
├── skills/
├── src/                # Optional shared code
└── tests/              # Optional tests
```
````

### Architecture and execution diagrams

Use fenced `txt` blocks for file trees, architecture, nodes, branches, and paths. Use actual names for existing components and label hypothetical examples. For example, a plugin with external data connections could be organized as follows.

```txt
┌─────────────────────────────────────┐
│ Example economics plugin            │
├─────────────────────────────────────┤
│ plugin.json   Identity and metadata │
│ connectors/   PostgreSQL and FRED   │
│ skills/       Credit risk           │
│               Macroeconomic models  │
│               Automated audit       │
└─────────────────────────────────────┘
```

In an execution diagram, label each decision and its destination. Define each node's input and resulting output. If execution logs are available, show the route actually taken. For a design, label the flow as proposed.

```txt
[Input] → [Validate]
          ├── Valid   → [Process] → [Verify] → [Output]
          └── Invalid → [Report error] → [End]
```

## Outputs and constraints

For a design, provide a tree and each component's responsibility. For an audit, prioritize issues that prevent loading, execution, or interpretation. Give the location, impact, and proposed correction. For edits, report the changes, checks, and pending host verification. Preserve existing interfaces within the task scope and treat packaging, installation, and publication as separate actions.
