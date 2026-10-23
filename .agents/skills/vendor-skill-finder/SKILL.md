---
name: vendor-skill-finder
description: Find the best matching skill under the repository's vendor directory when the user describes a task, goal, or desired capability.
metadata:
  short-description: Search vendor skills by task and explain which one to use
---

# Find a vendor skill

Use this skill when the user asks which skill under `vendor` can handle a task, or asks you to find a skill by describing what they want to do.

## Search

Search the repository's `vendor` directory. Do not search only filenames because many skills have generic names.

1. List skill entrypoints with `rg --files vendor | rg '/SKILL\.md$'`.
2. Read YAML frontmatter from candidate files to collect each skill's `name` and `description`.
3. Search candidate names, descriptions, and bodies for the user's key concepts. Include English equivalents for Korean requests.
4. Read the strongest candidates in full before ranking them.

Prefer an exact task match over a broad skill. Use the skill description, not the directory name alone, as the primary evidence.

## Return

Return the best match first. For each useful candidate, include:

- skill name
- repository-relative path
- what the skill does
- why it matches the request
- a closely related skill when it answers a different version of the question

If multiple copies exist, identify the canonical-looking path and mention duplicates or mirrors only when they could confuse the user. Paths under `vendor/cursor-plugins/pstack/skills` are the preferred pstack paths when a matching copy also exists under a harness directory.

If no strong match exists, say so and list the nearest candidates with their limitations. Do not create, modify, install, or invoke a skill while searching unless the user separately asks for that action.

## Scope

This skill finds and explains existing skills. It does not search outside `vendor`, inspect remote repositories, or infer that a skill is installed globally.
