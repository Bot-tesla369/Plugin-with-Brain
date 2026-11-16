---
name: skill
description: Create, evaluate, and improve AI skills and their SKILL.md files. Use when turning notes into reusable instructions, fixing activation or execution problems, or checking that a revision preserves expected behavior.
---

# Objective

Build skills with one clear responsibility and instructions the agent can follow and verify. For revisions, identify the cause of the problem and preserve behavior that still serves the user.

## When to use

Create a skill for a recurring procedure or specialized knowledge. Evaluate an existing skill when asked for findings. Edit it when asked to fix a failure, add a requirement, or simplify its behavior.

## Inputs

Identify the intended tasks, minimum inputs, constraints, and expected outputs. For a revision, inspect the current skill, the resources it calls, applicable plugin rules, and examples of success or failure. If the working project provides AI_Customization.md, use its guidance on skills and instructions.

## Procedure

1. Define one responsibility, one request that should trigger the skill, and one similar request outside its scope.
2. Use YAML frontmatter with a directory-matching lowercase name and a description that states what the skill does and when to use it. Keep existing identifiers unless a rename is requested.
3. Write steps that specify the condition, action, and observable result. Put decisive constraints before the actions they govern. Describe how to validate the input, carry out the task, verify the result, and prepare the output.
4. Read only the resources needed for the task. Resolve minor gaps from context and ask for missing information when it materially changes the result, permission, or scope.
5. For an existing skill, compare expected and observed behavior. Classify findings by activation, clarity, consistency, feasibility, duplication, or validation. Prioritize errors that block work or produce incorrect output. Label risks inferred from reading separately from observed failures.
6. Apply the smallest sufficient edit to the specified file. Check a typical request, a nearby out-of-scope request, and the original failure when available. Compare output formats and constraints before and after the change. Report which checks were performed by inspection and which were exercised in a session.

### Copyable SKILL.md template

Replace the example text and adapt the sections to the workflow.

```markdown
---
name: skill-name
description: Describe what the skill does and when to use it.
---

# Objective

State the problem and expected result.

## When to use

List the tasks or conditions that trigger this workflow.

## Inputs

List required files, data, or parameters. Identify optional inputs.

## Procedure

1. Validate the inputs.
2. Perform the required operations.
3. Verify the result against an observable criterion.
4. Prepare the output.

## Outputs

Specify the deliverable, format, and checks to report.

## Constraints

- Preserve scope and permissions.
- Report errors, missing inputs, and unverified results.
```

### Structure and resources

```txt
skills/
└── skill-name/
    ├── SKILL.md       # Metadata and core instructions
    ├── scripts/       # Optional executable helpers
    ├── references/    # Optional reference material
    └── assets/        # Optional templates and output resources
```

Put the decision rules in the skill. For a reference, specify which file to read and when. For a script, document inputs, output, and failure behavior. For an asset, identify which fields to fill and the expected final format. Use relative paths and add resources only when justified.

**Example.** Replace “verify the report” with “compare each table value with its source. If a value lacks support, identify the row and mark it pending.” Check the rule against one supported value and one unsupported value.

### Markdown conventions

Use fenced `txt` blocks for trees, architecture diagrams, nodes, and execution paths. Use exact names, consistent indentation, and labels for branch conditions. Distinguish proposed examples from observed routes.

| Element | Syntax | Use |
| --- | --- | --- |
| Headings | `#` through `######` | Recommended |
| Bold | `**text**` | Recommended |
| Italic | `*text*` | Optional |
| Bulleted or numbered list | `- Item` or `1. Item` | Recommended |
| Checklist | `- [ ] Task` | Optional |
| Blockquote | `> Text` | Optional |
| Separator | `---` | Optional |
| Inline code | `` `print()` `` | Recommended |
| Code block | Three backticks with an optional language tag | Recommended |
| Table | `\| Column \|` | Optional |
| YAML frontmatter | Opening and closing `---` at the top | Required |
| LaTeX | `$...$` or `$$...$$` | Optional content |

| File | Suggested length | Purpose |
| --- | --- | --- |
| `plugin.json` | 20–100 lines | Minimal configuration |
| `README.md` | 200–800 words | General documentation |
| `SKILL.md` | 500–2,000 words | Main instructions |
| `references/*.md` | 500–3,000 words | Detailed knowledge |
| `scripts/*.py` | 50–300 lines | Modular code |
| `*.yaml` | 10–100 lines | Configuration and metadata |
| Data `*.json` | As needed | Depends on purpose |

Treat lengths as planning guidelines. Keep short files short when they already contain everything needed.

## Outputs and constraints

For edits, deliver the revised file and summarize the behavior change and verification. For evaluations, report prioritized findings with location, impact, and proposed correction. Check that referenced resources exist and that the target environment provides the tools required by the instructions. Report checks you could not run.
