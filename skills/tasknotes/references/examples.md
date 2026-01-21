# TaskNotes Complete Examples

Working examples for common task patterns.

## Simple Task

```yaml
---
title: Buy groceries
status: open
due: 2025-01-16
contexts:
  - errands
tags:
  - personal
---
```

## Project Task with Estimate

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
- Integrate with analytics

## Notes
- Review competitor sites for inspiration
- Check brand guidelines for color palette
```

## Recurring Task with History

```yaml
---
title: Weekly expense report
status: open
priority: normal
recurrence: "FREQ=WEEKLY;BYDAY=FR"
scheduled: 2025-01-17T16:00:00
contexts:
  - work
projects:
  - "[[Finance]]"
complete_instances:
  - "2025-01-03"
  - "2025-01-10"
---

Submit weekly expense report to accounting by EOD Friday.
```

## Task with Dependencies

```yaml
---
title: Deploy feature to staging
status: open
priority: high
due: 2025-01-22
blockedBy:
  - uid: "[[Complete unit tests]]"
    reltype: FINISHTOSTART
  - uid: "[[Code review]]"
    reltype: FINISHTOSTART
projects:
  - "[[Feature X]]"
---

## Checklist
- [ ] Run final tests locally
- [ ] Update deployment config
- [ ] Notify QA team
```

## Task with Time Tracking

```yaml
---
title: Write API documentation
status: in-progress
priority: normal
due: 2025-01-28
projects:
  - "[[API Redesign]]"
timeEstimate: 180
timeEntries:
  - startTime: "2025-01-20T09:00:00"
    endTime: "2025-01-20T10:30:00"
    description: "Outlined structure"
  - startTime: "2025-01-21T14:00:00"
    endTime: "2025-01-21T16:00:00"
    description: "Drafted endpoints section"
---

## Sections
- [ ] Authentication
- [x] Endpoints
- [ ] Error codes
- [ ] Examples
```

## Task with Reminders

```yaml
---
title: Quarterly review meeting
status: open
priority: high
due: 2025-02-01T10:00:00
scheduled: 2025-01-25
contexts:
  - work
projects:
  - "[[Q1 Planning]]"
reminders:
  - id: "rem_001"
    type: relative
    relatedTo: due
    offset: "-P1D"
    description: "Prepare presentation"
  - id: "rem_002"
    type: relative
    relatedTo: due
    offset: "-PT1H"
    description: "Review notes"
---

## Agenda
- Q4 results review
- Q1 goals
- Team updates
```

## Complex Task (All Features)

```yaml
---
title: Launch new product feature
status: open
priority: high
due: 2025-02-15
scheduled: 2025-02-01
contexts:
  - work
  - focus
projects:
  - "[[Product Launch]]"
  - "[[Q1 Goals]]"
tags:
  - launch
  - critical
timeEstimate: 480
blockedBy:
  - uid: "[[Complete QA testing]]"
    reltype: FINISHTOSTART
  - uid: "[[Marketing materials ready]]"
    reltype: FINISHTOSTART
    gap: P2D
reminders:
  - id: "launch_prep"
    type: relative
    relatedTo: due
    offset: "-P3D"
    description: "Final review with stakeholders"
  - id: "launch_day"
    type: relative
    relatedTo: due
    offset: "-PT2H"
    description: "Deployment check"
dateCreated: 2025-01-10T08:00:00
---

## Launch Checklist

### Pre-Launch
- [ ] All blockers resolved
- [ ] Stakeholder sign-off
- [ ] Rollback plan documented

### Launch Day
- [ ] Deploy to production
- [ ] Monitor metrics
- [ ] Send announcement

### Post-Launch
- [ ] Gather feedback
- [ ] Address critical issues
- [ ] Schedule retrospective
```

## GTD-Style Task (Parallel Systems Context)

Based on the vault conventions from CLAUDE.md:

```yaml
---
type: task
title: Review quarterly IT budget
status: open
priority: P2
due: 2025-01-31
contexts:
  - parallel
projects:
  - "[[IT Budget 2025]]"
tags:
  - finance
  - quarterly
timeEstimate: 60
---

Review and approve IT expenditure projections for Q1.

## Items to Review
- [ ] Cloud services (AWS, Azure)
- [ ] Software licenses
- [ ] Hardware refresh plan
```

Note: The `contexts: parallel` indicates this is work-related per the vault's context conventions.
