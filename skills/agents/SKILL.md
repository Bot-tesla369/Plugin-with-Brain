---
name: agents
description: Design, evaluate, and improve persistent instructions for AI agents. Use when defining or reviewing a profile, an AGENTS.md file, or a specialized agent with a mission, scope, tools, and completion criteria.
---

# Objective

Turn a recurring responsibility into instructions that guide the agent across tasks. In a revision, correct observed behavior while preserving decisions that still serve the user.

## When to use

Use for a continuing role such as analysis, auditing, or maintenance, or when an agent ignores rules, exceeds scope, or claims completion without checking its output. For a focused, reusable task workflow, use [skill](../skill/SKILL.md). For package structure, use [plugin](../plugin/SKILL.md).

## Inputs

Identify the mission, users, recurring tasks, expected outputs, and delegated decisions. Inspect the target environment, applicable files, tools, dependencies, and permissions. For a revision, collect the current instructions and examples of success or failure. Consult the agent section of AI_Customization.md if the working project provides it.

## Procedure

1. **Define identity, mission, and scope.** State the role, the results it owns, and the operations it may perform. Distinguish routine choices from actions that require permission or user input. Define what the agent should report if a request exceeds its scope.
2. **Verify the environment.** Identify the host and check which file names, paths, metadata, and scope it recognizes. Before relying on a tool, identify the relevant version, configuration, or dialect. Describe environment preferences as preferences when alternatives are supported.
3. **Specify context and workflow.** Tell the agent which instructions and inputs it must inspect and when to consult a reference. Order the work from clarifying the goal to checking and delivering the result. Include domain-specific checks that change decisions. An analysis agent may need to check types, duplicates, and units before fitting a model and explain what evidence a causal claim would require.
4. **Define tool and error behavior.** Before an operation, check inputs, permissions, and expected effects. Afterward, inspect the result and errors. When a step fails, compare expected and observed behavior, investigate the cause, apply the smallest correction within scope, and verify again. If an essential tool is unavailable, report what remains pending and complete independent work where possible.
5. **Define communication and completion.** Specify language, output format, required evidence, and limitations to report. Use checks the agent can observe, such as opening a generated file or comparing output to a known reference case.
6. **Revise and validate.** Match a failed request to the instruction that governed it. Correct the cause and clarify priority where instructions overlap. Check a normal case, an out-of-scope case, and a case with an essential input or tool missing. Distinguish an inspection of the instructions from a run on the target host.

### Example decision flow

Use fenced `txt` blocks for nodes and branches. Label each condition and its destination.

```txt
[Receive request] → [Check required input]
                   ├── Available → [Execute] → [Verify] → [Deliver]
                   └── Missing   → [Ask for input] → [Continue independent work]
```

If an agent marked a script validated after reading it, specify when to report “reviewed by inspection” and when to report “executed and checked.” Verify the expected response for both situations.

## Outputs and constraints

Deliver the revised instructions in the requested file or report findings with their impact and proposed correction. Keep persistent rules in the agent file and task procedures in their respective skills. Preserve relevant user preferences and surface assumptions that affect behavior. Report any unverified loading, tools, permissions, or runtime behavior.
