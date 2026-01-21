---
name: tasknotes
description: This skill should be used when the user asks to "create a task", "add a task", "new task", "edit task properties", "set task due date", "task priority", "TaskNotes format", or needs guidance on TaskNotes YAML structure, recurrence rules, task dependencies, time tracking, or reminders in Obsidian.
---

# TaskNotes Skill

TaskNotes manages tasks as individual Markdown notes in Obsidian. Each task stores metadata in YAML frontmatter, and views are powered by Obsidian Bases (`.base` files).

Reference: [TaskNotes Documentation](https://github.com/callumalpass/tasknotes)

## Core Properties

Create tasks with this basic structure:

```yaml
---
title: Task description here
status: open
priority: normal
due: 2025-01-20
scheduled: 2025-01-15
contexts:
  - work
projects:
  - "[[Project Name]]"
tags:
  - category
timeEstimate: 30
---

Task notes and details go here.
```

### Property Reference

| Property | Type | Description | Example |
|----------|------|-------------|---------|
| `title` | text | Task name (or use filename) | `"Review budget"` |
| `status` | enum | Workflow state | `open`, `in-progress`, `done` |
| `priority` | enum | Importance level | `low`, `normal`, `high` |
| `due` | date | Deadline | `2025-01-20` |
| `scheduled` | date | When to work on it | `2025-01-15` |
| `contexts` | list | Location/tool groupings | `["@home", "@work"]` |
| `projects` | list | Related project notes | `["[[Project A]]"]` |
| `tags` | list | Standard Obsidian tags | `["finance", "urgent"]` |
| `timeEstimate` | number | Minutes to complete | `60` |

### Date Formats

```yaml
# Date only (YYYY-MM-DD)
due: 2025-01-20

# Date with time (ISO 8601)
due: 2025-01-20T14:30:00

# With timezone
due: 2025-01-20T14:30:00Z
```

### Metadata Properties

Auto-managed by TaskNotes:

```yaml
dateCreated: 2025-01-10T08:00:00
dateModified: 2025-01-15T14:30:00
completedDate: 2025-01-20T16:45:00
```

## Quick Example

A project task with estimate:

```yaml
---
title: Design new landing page
status: in-progress
priority: high
due: 2025-01-25
scheduled: 2025-01-20
projects:
  - "[[Website Redesign]]"
tags:
  - design
  - marketing
timeEstimate: 240
---

## Requirements
- Mobile-first responsive design
- A/B test ready

## Notes
- Review competitor sites for inspiration
```

## Advanced Features

For complex task management, see the reference files:

- **Recurrence** (RRULE format): See `references/advanced-properties.md`
- **Dependencies** (blockedBy): See `references/advanced-properties.md`
- **Time Tracking** (timeEntries): See `references/advanced-properties.md`
- **Reminders**: See `references/advanced-properties.md`
- **Natural Language Parsing**: See `references/advanced-properties.md`
- **Complete Examples**: See `references/examples.md`

## Integration with Bases

TaskNotes views use `.base` files. Common filter pattern:

```yaml
filter:
  - property: status
    operator: "!="
    value: done
  - property: due
    operator: "<="
    value: "{{endOfWeek}}"
```

See the `obsidian-bases` skill for complete `.base` file syntax.

## External References

- [TaskNotes GitHub](https://github.com/callumalpass/tasknotes)
- [RFC 5545 - iCalendar RRULE](https://datatracker.ietf.org/doc/html/rfc5545#section-3.3.10)
- [ISO 8601 Duration](https://en.wikipedia.org/wiki/ISO_8601#Durations)
