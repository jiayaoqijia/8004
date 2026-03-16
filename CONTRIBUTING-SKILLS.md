# Contributing a New Skill

This guide walks you through creating a new [ClawHub](https://clawhub.ai)-standard skill for the ERC-8004 ecosystem.

## Skill Structure

```
.claude/skills/<skill-name>/
├── SKILL.md                    # Main skill file (required)
└── references/                 # Supporting reference files
    ├── <topic-1>.md
    ├── <topic-2>.md
    └── ...
```

## Step 1: Create SKILL.md

Every skill starts with a `SKILL.md` file containing YAML frontmatter and markdown content.

### Template

```markdown
---
name: my-skill
description: >-
  One-paragraph description of what this skill does and when to consult it.
  Be specific about trigger phrases and use cases.
version: 1.0.0
allowed-tools: "Bash(curl:*) Bash(jq:*)"   # Optional: tools the skill needs
metadata:
  openclaw:
    requires:                   # Optional: runtime dependencies
      bins:
        - curl
      env:
        - MY_API_KEY
    primaryEnv: MY_API_KEY      # Optional: main env variable
    emoji: "🔧"
    homepage: https://example.com
---

# Skill Title

Brief overview of what this skill provides.

## Reference Map

| File | When to read |
|------|-------------|
| `{baseDir}/references/api.md` | Full API documentation |
| `{baseDir}/references/examples.md` | Usage examples |

---

## Request Classification

1. **Query type A** ("example phrases") → Action/file to consult.
2. **Query type B** ("example phrases") → Action/file to consult.

---

## Quick Reference

Core information that should be in SKILL.md itself (not in references).

---

## Examples

**Example 1: Title**
User: "Example user request"
→ What the skill should do, with code/commands.
```

## Step 2: Write Reference Files

Reference files contain detailed information that is lazy-loaded on demand.

### Guidelines

- **One concept per file** — keep files focused and small
- **Text only** — no binaries, images, or generated files
- **Use `{baseDir}`** — reference other files with `{baseDir}/references/filename.md`
- **Include code examples** — practical, copy-pasteable examples
- **Keep under 300 lines** — split large topics into multiple files

### Naming Convention

- `api-reference.md` — endpoint documentation
- `authentication.md` — auth and rate limits
- `examples.md` — usage examples
- `<feature>.md` — specific feature documentation

## Step 3: Write the Description

The `description` field in frontmatter is critical — it determines when the skill is activated.

### Good Description

```yaml
description: >-
  Query the 8004scan public API to discover, search, and analyze ERC-8004
  AI agents registered on the blockchain. Covers agent listing, semantic
  search, agent details, account lookups, platform statistics, supported
  chains, and feedback queries. Consult this skill when the user wants to
  search for agents, browse the agent registry, check agent details on
  8004scan, get platform stats, look up agents by owner address, query
  feedback scores, or integrate with the 8004scan API programmatically.
```

Why it works:
- Lists all capabilities
- Includes trigger phrases ("search for agents", "check agent details")
- Mentions key terms a user might say

### Bad Description

```yaml
description: API skill for 8004scan.
```

Why it fails: too vague, no trigger phrases, doesn't help with activation.

## Step 4: Define Allowed Tools

If your skill needs to execute commands, declare them in `allowed-tools`:

```yaml
# Read-only knowledge skill (no tools needed)
# Just omit allowed-tools

# API skill that needs curl
allowed-tools: "Bash(curl:*) Bash(jq:*)"

# Skill that needs npm
allowed-tools: "Bash(npm:*) Bash(npx:*)"
```

If your skill is pure knowledge (no actions), omit `allowed-tools` entirely.

## Step 5: Add Request Classification

Map user intents to actions. This helps the AI route requests correctly:

```markdown
## Request Classification

1. **Search query** ("find X", "search for Y") → Search endpoint.
2. **Detail query** ("show agent X", "get details") → Detail endpoint.
3. **Action request** ("register", "submit") → Specific action.
4. **Docs query** ("how does X work?") → Read reference file.
```

## Step 6: Test Your Skill

1. Clone the repo and navigate to it:
   ```bash
   git clone https://github.com/<your-fork>/8004.git && cd 8004
   ```

2. Claude Code auto-detects skills in `.claude/skills/`

3. Test with relevant prompts:
   - Does the skill activate on the right queries?
   - Are the reference files loaded when needed?
   - Do the examples work?

## Checklist Before Submitting

See [SKILL-CHECKLIST.md](SKILL-CHECKLIST.md) for the full quality checklist.

Quick check:
- [ ] SKILL.md has valid YAML frontmatter
- [ ] Description includes trigger phrases
- [ ] Reference files are text-only and under 300 lines
- [ ] All code examples are tested and work
- [ ] No secrets, API keys, or private data in any file

## Submitting

1. Fork the repository
2. Create a branch: `feat/skill-<name>`
3. Add your skill in `.claude/skills/<name>/`
4. Open a PR with:
   - What the skill does
   - Example prompts that activate it
   - How you tested it
