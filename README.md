# TaskNotes Claude Code Skill

A [Claude Code](https://claude.ai/code) skill for [TaskNotes](https://github.com/callumalpass/tasknotes) - task management in Obsidian with YAML frontmatter.

## What is TaskNotes?

TaskNotes is an Obsidian plugin that manages tasks as individual Markdown notes with metadata stored in YAML frontmatter. It supports:

- Task status, priority, and due dates
- Recurring tasks (RRULE format)
- Task dependencies
- Time tracking
- Reminders
- Natural language parsing

## What does this skill do?

This Claude Code skill teaches Claude how to create and edit valid TaskNotes task files. When you ask Claude to create a task, it will generate proper YAML frontmatter following TaskNotes conventions.

## Installation

```bash
claude plugins install github:andrew-mccaskill/tasknotes-claude-skill
```

Or manually copy the `skills/tasknotes/` folder into your `.claude/skills/` directory.

## Usage

Once installed, Claude will automatically use this skill when you ask about tasks:

- "Create a task for reviewing the quarterly budget"
- "Add a recurring task for weekly standups"
- "Set up a task with dependencies"
- "Help me create a TaskNotes file"

## Skill Structure

```
tasknotes-claude-skill/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── tasknotes/
│       ├── SKILL.md              # Core skill
│       └── references/
│           ├── advanced-properties.md
│           └── examples.md
├── README.md
└── LICENSE
```

## Related

- [TaskNotes Plugin](https://github.com/callumalpass/tasknotes) - The Obsidian plugin this skill supports
- [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) - Core Obsidian skills (Markdown, Bases, Canvas)

## License

MIT
