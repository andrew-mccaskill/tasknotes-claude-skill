# TaskNotes Advanced Properties

This reference covers advanced TaskNotes features: recurrence, dependencies, time tracking, reminders, and natural language parsing.

## Recurrence

TaskNotes uses RRULE format (RFC 5545) for recurring tasks:

```yaml
---
title: Weekly team standup
recurrence: "FREQ=WEEKLY;BYDAY=MO"
scheduled: 2026-01-13T09:00:00
complete_instances:
  - "2026-01-06"
  - "2026-01-13"
---
```

### Common Recurrence Patterns

| Pattern | RRULE |
|---------|-------|
| Every day | `FREQ=DAILY` |
| Every week | `FREQ=WEEKLY` |
| Mon, Wed, Fri | `FREQ=WEEKLY;BYDAY=MO,WE,FR` |
| First of each month | `FREQ=MONTHLY;BYMONTHDAY=1` |
| Annually | `FREQ=YEARLY` |

### With Start Date

```yaml
recurrence: "DTSTART:20260115T090000Z;FREQ=DAILY"
```

## Dependencies

Tasks can block or be blocked by other tasks:

```yaml
---
title: Deploy to production
blockedBy:
  - uid: "[[Run integration tests]]"
    reltype: FINISHTOSTART
  - uid: "[[Code review approved]]"
    reltype: FINISHTOSTART
    gap: P1D
---
```

### Relationship Types

| Type | Description |
|------|-------------|
| `FINISHTOSTART` | Blocker must finish before this starts (default) |
| `FINISHTOFINISH` | Blocker must finish before this finishes |
| `STARTTOSTART` | Blocker must start before this starts |
| `STARTTOFINISH` | Blocker must start before this finishes |

### Gap Format

Uses ISO 8601 duration: `P1D` (1 day), `PT2H` (2 hours), `P1W` (1 week)

## Time Tracking

Track time spent on tasks:

```yaml
---
title: Write documentation
timeEstimate: 120
timeEntries:
  - startTime: "2026-01-15T09:00:00"
    endTime: "2026-01-15T10:30:00"
    description: "Initial draft"
  - startTime: "2026-01-15T14:00:00"
    endTime: "2026-01-15T15:00:00"
    description: "Revisions"
---
```

## Reminders

### Relative Reminders

Offset from due or scheduled date:

```yaml
reminders:
  - id: "rem_001"
    type: relative
    relatedTo: due
    offset: "-PT15M"
    description: "Review task details"
  - id: "rem_002"
    type: relative
    relatedTo: scheduled
    offset: "-P1D"
    description: "Prepare materials"
```

### Absolute Reminders

Specific time:

```yaml
reminders:
  - id: "rem_003"
    type: absolute
    absoluteTime: "2026-01-19T09:00:00"
    description: "Follow up with client"
```

### Offset Format

ISO 8601 duration with sign:
- `-PT15M` = 15 minutes before
- `PT1H` = 1 hour after
- `-P1D` = 1 day before

## Natural Language Parsing

TaskNotes supports NLP triggers for quick task creation:

| Trigger | Property | Example |
|---------|----------|---------|
| `@` | contexts | `@work @phone` |
| `+` | projects | `+[[Project A]]` |
| `#` | tags | `#urgent #finance` |
| `!` | priority | `!high` (if enabled) |
| `*` | status | `*in-progress` |

### Example Input

```
Review quarterly report tomorrow @work +[[Q1 Planning]] #finance !high
```

### Parses To

```yaml
---
title: Review quarterly report
due: 2026-01-16
contexts:
  - work
projects:
  - "[[Q1 Planning]]"
tags:
  - finance
priority: high
---
```

## Field Mapping

TaskNotes allows remapping property keys. Configuration is done in TaskNotes settings, not in individual files.

| Default Key | Can Map To |
|-------------|------------|
| `due` | `deadline`, `dueDate` |
| `scheduled` | `start`, `scheduledDate` |
| `status` | `state`, `taskStatus` |
| `priority` | `importance`, `prio` |
