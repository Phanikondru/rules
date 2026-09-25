# rules

Personal library of **generic, reusable** Claude Code slash commands, skills, and rules.
Organized by **skill / concept**, never by the project they came from.

## Layout

```
commands/<concept>/<command-name>.md    # slash commands, grouped by concept (e.g. git/, review/, ui/)
skills/<skill-name>/SKILL.md            # skills, one folder each (plus any supporting files)
rules/<group>/<concept>.md              # standing rules/conventions, grouped (ux/, ui-design/, content-and-feedback/, process/)
```

Rules and commands cross-reference each other by filename as `.claude/rules/<file>.md` and `/<command>`.
When installing into a project, copy them flat into that project's `.claude/rules/` and `.claude/commands/`.
Rule concepts that overlap a skill (e.g. UX laws, motion) live in the skill and are referenced, not duplicated.

## Conventions

- One concept per file/folder. Merge into the existing one instead of creating near-duplicates.
- Generic only: no project names, paths, repo URLs, secrets, or product-specific details.
  Use placeholders or describe the concept in general terms.
- Project-specific variants stay in their project; only the reusable core lives here.
- Filenames are kebab-case and describe the concept, not the origin project.

## Populated automatically

A global rule in `~/.claude/CLAUDE.md` makes Claude sync generic commands/skills/rules here
whenever they are created or improved in any other project.
