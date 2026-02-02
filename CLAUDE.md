# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a collection of agent skills for Claude Code and agentskills.io-compatible agents. Skills provide specialized domain knowledge and frameworks for specific use cases (UX design, marketing, product strategy, etc.).

## Repository Structure

```
skills/
├── .claude-plugin/
│   └── marketplace.json   # Marketplace configuration for plugin installation
├── {skill-name}/
│   ├── SKILL.md           # Main skill file with YAML frontmatter + markdown instructions
│   └── references/        # Supporting reference files (optional)
│       └── *.md
└── README.md              # Skill catalog with descriptions and installation instructions
```

## Skill File Format

Each skill has a `SKILL.md` with this structure:

```markdown
---
name: skill-name
description: Brief description used for skill matching/discovery. Include trigger phrases.
license: MIT
metadata:
  author: wondelai
  version: "1.0.0"
---

# Skill Title

Main skill instructions in markdown...
```

### Required Fields
- `name`: Unique identifier (lowercase, hyphens for spaces, max 64 chars)
- `description`: What the skill does and when to use it (max 1024 chars)

### Recommended Fields (for marketplace)
- `license`: License name (we use MIT)
- `metadata.author`: Author/organization name
- `metadata.version`: Semantic version

The YAML frontmatter `description` field is critical for skill discovery - it should include keywords and trigger phrases that help match user requests to the skill.

## Adding New Skills

1. Create a new folder: `{skill-name}/`
2. Create `SKILL.md` with YAML frontmatter (`name`, `description`) and skill instructions
3. Optionally add `references/` folder with supporting `.md` files
4. Add the skill to `README.md` with description and example prompts

## Installation

### Via Claude Code Plugin Marketplace
```bash
/plugin marketplace add wondelai/skills
/plugin install product-strategy@wondelai-skills    # Jobs to Be Done
/plugin install ux-design@wondelai-skills           # UI/UX skills collection
/plugin install marketing-cro@wondelai-skills       # Marketing/CRO skills
```

### Via skills.sh
```bash
npx skills add wondelai/skills              # All skills
npx skills add wondelai/skills/{skill-name} # Individual skill
```

## Versioning Policy

Skills use semantic versioning (`MAJOR.MINOR.PATCH`):
- **MAJOR**: Breaking changes or complete rewrites
- **MINOR**: New features, significant enhancements, new sections
- **PATCH**: Bug fixes, typo corrections, small clarifications

**Auto-increment rule:** When modifying a skill's `SKILL.md` or its `references/` files, always bump the version in the frontmatter:
- Content addition/enhancement → bump MINOR (e.g., `1.0.0` → `1.1.0`)
- Small fix/typo → bump PATCH (e.g., `1.1.0` → `1.1.1`)

Example:
```yaml
metadata:
  author: wondelai
  version: "1.1.0"
```

## Commit Policy

Commit directly to main.
