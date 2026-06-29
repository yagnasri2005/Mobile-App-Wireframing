# User Flows Overview: TaskFlow

## What Are User Flows?

User flows map the journey a user takes through your app to accomplish a goal. They show:
- **Starting point** - Where the user begins
- **Steps** - Actions the user takes
- **Decision points** - Where the user makes choices
- **Success path** - Happy path to accomplishing the goal
- **Error paths** - What happens when things go wrong
- **End point** - Goal accomplished

---

## TaskFlow Key User Flows

We've identified 5 critical user flows that cover the main use cases:

### Flow 1: Onboarding (New User First Experience)
**User**: Sarah, Marcus, or Elena (first time using TaskFlow)
**Goal**: Get set up and see first team tasks
**Time**: 5-10 minutes
**Importance**: Critical - first impression matters

### Flow 2: Task Creation (Core Action)
**User**: Sarah (creating tasks for team)
**Goal**: Create and assign a task to teammate
**Time**: 1-2 minutes
**Importance**: Critical - primary workflow

### Flow 3: Daily Task Check (Quick Status)
**User**: Marcus (checking tasks on mobile)
**Goal**: See what I need to work on today
**Time**: 2-3 minutes
**Importance**: High - frequent action

### Flow 4: Collaboration (Team Communication)
**User**: Sarah & team (commenting on task)
**Goal**: Discuss task, unblock, provide update
**Time**: 1-2 minutes per interaction
**Importance**: High - core collaboration

### Flow 5: Team Analytics (Strategic View)
**User**: Elena (checking team progress)
**Goal**: Understand team status, blockers, progress
**Time**: 3-5 minutes
**Importance**: Medium - leadership function

---

## User Flow Symbols & Notation

### Basic Flow Elements

```
┌─────────────────┐
│  Start Point    │   Screen/page in app
└────────┬────────┘
         │
         ▼
    ┌─────────┐
    │ Action  │    User action or system event
    └────┬────┘
         │
         ▼
      ◇──────◇   Decision point - branches to different paths
     ╱        ╲
    ╱          ╲
   ▼            ▼
 Success      Error
  Path         Path
   │            │
   └────┬───────┘
        ▼
   ┌──────────┐
   │ End Goal │   Goal accomplished
   └──────────┘
```

### Flow Notation
- **Rectangle** = Screen/state/page
- **Arrow** = Flow/progression
- **Diamond** = Decision point (yes/no, success/error)
- **Circle** = Start/end
- **Bold text** = Key action
- **[Details]** = Additional context

---

## Detailed Flow Diagrams

See individual flow files for complete diagrams:
- [Onboarding Flow](onboarding-flow.md)
- [Task Creation Flow](task-creation-flow.md)
- [Daily Task Check Flow](daily-task-check-flow.md) - Coming soon
- [Collaboration Flow](collaboration-flow.md)
- [Team Analytics Flow](team-analytics-flow.md) - Coming soon

---

## Flow Design Principles

### 1. Happy Path First
Design the successful, main path clearly. Then add error handling.

### 2. Minimize Steps
Reduce number of taps/clicks to accomplish goal. Aim for:
- Task creation: < 5 steps
- Status check: < 3 steps
- Add comment: < 2 steps

### 3. Provide Context
At each step, user should know:
- Where they are
- What to do next
- How to go back
- How to get help

### 4. Handle Errors Gracefully
When things go wrong:
- Show clear error message
- Explain what happened
- Suggest how to fix it
- Keep user context

### 5. Mobile-First Thinking
Flows should work on small screens:
- Minimize modal dialogs
- Use bottom sheets instead
- Keep forms short
- Big touch targets (44x44px min)

### 6. Offline Considerations
Think about offline scenarios:
- Can user view? Yes (cached data)
- Can user create? Queue for later
- Can user update? Queue for later
- Notify when offline/online

---

## Cross-Flow Patterns

### Pattern 1: Task Status Updates
**Common to**: Task creation, daily check, collaboration flows
**Actions**: Create → Set status → Set priority → Assign → Done
**Design**: Reusable flow, consistent across app

### Pattern 2: Collaboration Interactions
**Common to**: Collaboration, team analytics flows
**Actions**: Open task → Add comment → @mention → Resolve
**Design**: Consistent comment UI, notification flow

### Pattern 3: Notifications/Alerts
**Common to**: All flows
**Actions**: Alert → Notification → Action → Dismiss/Snooze → Done
**Design**: Smart notification system, central notification management

### Pattern 4: Error Recovery
**Common to**: All flows
**Actions**: Error occurs → Show message → User corrects → Retry
**Design**: Clear error states, undo when possible

---

## Persona-Specific Flow Emphasis

### Sarah's Flows (PM)
Priority:
1. Task creation (assign to others)
2. Team analytics (see progress)
3. Collaboration (resolve blockers)
4. Notification management (smart alerts)

### Marcus's Flows (Developer)
Priority:
1. Daily task check (what's my work?)
2. Task status update (mark done)
3. Quick comments (provide update)
4. Offline access (work without internet)

### Elena's Flows (Executive)
Priority:
1. Team analytics (strategic view)
2. Blocker alerts (problems to solve)
3. Report generation (stakeholder update)
4. Quick check (5-minute status)

---

## Success Metrics by Flow

### Onboarding Flow
✅ **Success metrics**:
- Time to first meaningful action: < 2 minutes
- User creates first task: Within first session
- User adds first teammate: Within 24 hours
- Activation rate: > 80% within 7 days

### Task Creation Flow
✅ **Success metrics**:
- Time to create task: < 90 seconds
- Form completion rate: > 90%
- Task assignment accuracy: 99%+
- Bounce rate: < 5%

### Daily Task Check Flow
✅ **Success metrics**:
- Load time: < 2 seconds
- Tasks shown: All relevant tasks
- Engagement: Daily active users > 60%
- Mobile completion rate: 95%+

### Collaboration Flow
✅ **Success metrics**:
- Comment addition time: < 1 minute
- Notification delivery: < 5 seconds
- Comment visibility: 100% of mentioned users see it
- Response rate: > 70% within 1 hour

### Team Analytics Flow
✅ **Success metrics**:
- Data accuracy: 100%
- Load time: < 3 seconds
- Export success: 99%+
- Report generation: < 30 seconds

---

## Mobile vs Desktop Flow Differences

### Task Creation
**Desktop**:
- Full form visible at once
- Inline validation
- Bulk actions available

**Mobile**:
- Step-by-step wizard
- Vertical scrolling form
- Top action bar for save/cancel

### Team Dashboard
**Desktop**:
- Multiple columns (tasks, team, activity)
- Kanban board view
- Customizable widgets

**Mobile**:
- Single column
- Tab-based navigation
- Stacked cards

### Comments Section
**Desktop**:
- Side panel with comments
- Inline editing
- Rich text formatting toolbar

**Mobile**:
- Bottom sheet for comments
- Simple text input
- Formatting via buttons

---

## Error Scenarios Handled

### Connection Errors
**Scenario**: User loses internet while creating task
**Flow**:
1. User types task details
2. Presses save
3. Network error occurs
4. App shows: "No internet connection"
5. Option: "Save for later" (queue)
6. When online: Auto-sync queued tasks

### Permission Errors
**Scenario**: User tries to assign task to person not in team
**Flow**:
1. User selects assignee
2. Person not in team
3. App shows: "This person isn't in your team"
4. Option: "Invite them" or "Choose different person"

### Validation Errors
**Scenario**: User creates task without title
**Flow**:
1. User presses save
2. Validation fails: "Title is required"
3. App highlights field: Title (red border)
4. Shows hint: "Enter a task name"
5. User corrects and retries

### Server Errors
**Scenario**: Server fails to save task
**Flow**:
1. User creates task
2. Submit pressed
3. Server error (500)
4. App shows: "Something went wrong. Retry?"
5. Option: "Retry", "Save for later", "Discard"

---

## Notification Flow (Cross-App)

```
Event Occurs
    │
    ▼
Check: Should notify user?
    ├─ @mention → YES → Urgent
    ├─ Task assigned to me → YES → High
    ├─ Comment on my task → YES → Medium
    ├─ Task completed → MAYBE → Based on settings
    └─ Status update → NO → Show in feed
    │
    ▼
Check: Notification preference
    ├─ Do Not Disturb? → Queue
    ├─ App open? → In-app notification
    └─ App closed? → Push notification
    │
    ▼
Deliver Notification
    │
    ▼
User Interaction
    ├─ Tap notification → Navigate to task
    ├─ Dismiss → Mark as read
    └─ Snooze → Re-notify later
```

---

## Flow Validation Checklist

Use this checklist to validate each user flow:

- [ ] **Happy path** clearly defined
- [ ] **Error paths** documented
- [ ] **Mobile-friendly** - works on small screens
- [ ] **Quick** - meets time targets
- [ ] **Clear** - user knows what to do next
- [ ] **Accessible** - keyboard + screen reader support
- [ ] **Offline-aware** - handles no internet
- [ ] **Consistent** - matches other flows in app
- [ ] **Tested** - validated with users
- [ ] **Documented** - diagram + description complete

---

## Flow Implementation Priority

### Phase 1 (MVP - Launch)
1. Onboarding Flow
2. Task Creation Flow
3. Daily Task Check Flow
4. Basic Collaboration (Comments)

### Phase 2 (Post-Launch)
5. Team Analytics Flow
6. Advanced Collaboration (Mentions, reactions)
7. Notification Management

### Phase 3 (Future)
8. Integrations (Slack, Calendar)
9. Automation Flows
10. Advanced Analytics

---

## How to Read Detailed Flow Documents

Each flow document includes:

1. **Overview** - What is this flow?
2. **Personas** - Who uses this?
3. **Goal** - What do they want to accomplish?
4. **Context** - When do they do this?
5. **Main Flow Diagram** - Step-by-step visual
6. **Step Descriptions** - Detail for each step
7. **Decision Points** - Key branches
8. **Error Scenarios** - What goes wrong?
9. **Mobile Considerations** - Phone-specific notes
10. **Success Metrics** - How do we know it works?

---

## Design Decisions Informed by Flows

### Decision 1: Bottom Tab Navigation
**Flow impact**: All flows benefit from quick tab access
**Result**: 5-6 main tabs for primary actions

### Decision 2: Modal vs Full Screen
**Flow impact**: Quick flows (add comment) use modals; complex flows (create task) use full screen
**Result**: Modals for < 30 second actions, full screens for multi-step flows

### Decision 3: Inline Editing
**Flow impact**: Status updates need to be quick (1 tap)
**Result**: Inline dropdown for status, priority on task list

### Decision 4: Activity Feed
**Flow impact**: Users want to see what happened (all flows feed into this)
**Result**: Central activity feed showing all task changes

---

**Flow Documentation Created**: June 2026
**Last Updated**: June 29, 2026
**Next Update**: After user testing validates flows