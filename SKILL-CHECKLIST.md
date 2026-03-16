# Skill Quality Checklist

Use this checklist when creating or reviewing ClawHub-standard skills for the 8004 ecosystem.

## SKILL.md Frontmatter

- [ ] `name` is lowercase, hyphenated, matches the directory name
- [ ] `description` is a detailed paragraph with trigger phrases and use cases
- [ ] `version` follows semver (e.g., `1.0.0`)
- [ ] `allowed-tools` lists only the tools the skill actually needs (omit for read-only skills)
- [ ] `metadata.openclaw.emoji` is set
- [ ] `metadata.openclaw.homepage` points to a valid URL
- [ ] `metadata.openclaw.requires.bins` lists required CLI tools (if any)
- [ ] `metadata.openclaw.requires.env` lists required environment variables (if any)
- [ ] `metadata.openclaw.primaryEnv` is set if the skill needs an API key

## SKILL.md Content

- [ ] Has a clear title and one-paragraph overview
- [ ] **Reference Map** table lists all reference files with "when to read" guidance
- [ ] **Request Classification** maps user intents to specific actions or files
- [ ] **Quick Reference** section covers the most common use cases inline
- [ ] **Examples** section has 3+ real-world examples with user prompts and expected responses
- [ ] Examples show actual commands/code, not just descriptions

## Reference Files

- [ ] Each file covers one focused topic
- [ ] Files are under 300 lines each
- [ ] Text-only content (no binaries, images, or generated files)
- [ ] Cross-references use `{baseDir}/references/filename.md` pattern
- [ ] Code examples are complete and copy-pasteable
- [ ] API examples include all required headers and parameters
- [ ] Response schemas show realistic sample data

## Description Quality

- [ ] Mentions all major capabilities of the skill
- [ ] Includes natural language trigger phrases users would actually say
- [ ] Specifies when to consult the skill vs. other skills
- [ ] Long enough to be unambiguous (50+ words recommended)

## Security

- [ ] No hardcoded API keys, secrets, or private data
- [ ] API keys are referenced via environment variables only
- [ ] Untrusted external data is handled safely (code blocks, no execution)
- [ ] HTTPS URLs only for API endpoints
- [ ] Webhook skills include signature verification guidance

## Code Examples

- [ ] All curl commands include proper headers (`Content-Type`, `X-API-Key`)
- [ ] All code examples have been tested and produce correct output
- [ ] Error handling is shown where appropriate
- [ ] Environment variable usage is consistent across examples
- [ ] Pagination patterns are demonstrated for list endpoints

## Completeness

- [ ] All endpoints/features the skill covers are documented
- [ ] Rate limits and authentication requirements are documented
- [ ] Error responses and status codes are listed
- [ ] Edge cases and limitations are noted
- [ ] Related skills are cross-referenced where appropriate

## Style

- [ ] Consistent markdown formatting throughout
- [ ] Tables are properly aligned
- [ ] Code blocks specify the language (```bash, ```json, ```typescript)
- [ ] No orphaned or broken cross-references
- [ ] Concise writing — no filler text or unnecessary repetition
