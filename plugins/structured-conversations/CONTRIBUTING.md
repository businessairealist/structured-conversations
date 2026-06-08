# Contributing

## Adding a New Skill

1. Create a new directory under `skills/` using kebab-case naming (e.g., `my-new-skill/`)
2. Create `SKILL.md` with YAML frontmatter:
   ```yaml
   ---
   name: my-new-skill
   description: "[Imperative verb] [input] into [output] for [purpose]. Use when you need [trigger condition]."
   ---
   ```
3. Include all five standard sections in the body:
   - **Find Inputs Before Asking** — input resolution order
   - **Core Workflow** — the skill-specific process
   - **Write Outputs** — what to produce and where
   - **Quality Bar** — standards for output quality
   - **User Experience Contract** — interaction rules
4. Keep the SKILL.md body under 3000 words
5. Place detailed reference content in a `references/` subdirectory

## Modifying an Existing Skill

- Edit the SKILL.md body for instruction changes
- Update the frontmatter description if trigger conditions change
- Add or update reference files for deep domain content
- Do not remove standard sections

## Naming Conventions

- Directories and files: kebab-case (lowercase, hyphens only)
- Skill names must match their directory name exactly
- Reference files: descriptive kebab-case names ending in `.md`

## Quality Checklist

Before submitting changes:

- [ ] SKILL.md has `name` and `description` in frontmatter
- [ ] Description includes at least one quoted trigger phrase
- [ ] Body is under 3000 words
- [ ] All five standard sections are present
- [ ] No references to Codex, artifact.json, runs/manifests, or project-folder runtime
- [ ] `CHANGELOG.md` updated with your changes
