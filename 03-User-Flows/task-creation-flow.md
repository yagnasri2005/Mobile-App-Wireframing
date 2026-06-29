# Task Creation Flow: TaskFlow

## Flow Overview

**Flow Name**: Create and Assign Task
**Primary Persona**: Sarah (Project Manager)
**Secondary Personas**: Marcus (self-assign), Elena (delegate)
**Goal**: Create a new task, set details, and assign to teammate
**Duration**: 1-2 minutes
**Success Rate Target**: > 95% task creation completion

---

## Task Creation Context

### When Does This Flow Happen?
- User taps "+ Create" button
- User has 1+ team setup
- User wants to create task

### Success Criteria
Task created successfully when:
1. ✅ Task title entered
2. ✅ Assignee selected (optional)
3. ✅ Priority set (optional, defaults to Medium)
4. ✅ Deadline set (optional)
5. ✅ Task saved to database
6. ✅ Confirmation shown
7. ✅ User can view task or create another

---

## Task Creation Flow Diagram

```
┌──────────────────────┐
│ Tap "+ Create" Btn   │ [From home, team, or anywhere]
└──────┬───────────────┘
       │
       ▼
  ┌────────────────────────┐
  │ Task Creation Sheet    │ [Bottom sheet modal]
  │ ┌────────────────────┐ │
  │ │ What's the task?   │ │ [Text input field]
  │ └────────────────────┘ │
  │ [Suggested options]    │ [Auto-complete]
  │ [Assignee field]       │ [Optional]
  │ [Priority: Med ▼]      │ [Optional]
  │ [Deadline: None ▼]     │ [Optional]
  │                        │
  │ [Create] [Cancel]      │ [Buttons]
  └────┬─────────────┬─────┘
       │             │
   Title          Cancel
  filled?         clicked?
       │             │
       │             ▼
    YES          ┌──────────┐
       │          │ Discard  │
       │          │ Return to│
       │          │ Previous │
       │          └──────────┘
       │
       ▼
  ┌────────────────────┐
  │ Validate Task      │ [Client validation]
  │ - Title present?   │
  │ - Valid assignee?  │
  │ - Date in future?  │
  └────┬───────────┬───┘
       │           │
    Valid?      Invalid?
       │           │
       │           ▼
       │      ┌──────────────────┐
       │      │ Show Error       │ [Toast/inline]
       │      │ "Title required" │ [Focus to fix]
       │      └──────┬───────────┘
       │             │
       │      [User corrects]
       │             │
       └─────────────┘
       │
       ▼
  ┌──────────────────────┐
  │ Submit to Server     │ [API call]
  │ Create task          │
  └──┬──────────────────┬┘
     │                  │
  Success?            Error?
     │                  │
     │                  ▼
     │           ┌──────────────────┐
     │           │ Server Error     │ [Toast]
     │           │ "Failed to save" │ [Retry option]
     │           └──────┬───────────┘
     │                  │
     │          [Retry or Save Offline]
     │                  │
     └──────────┬───────┘
                ▼
        ┌────────────────────────┐
        │ Task Created!          │ [Success state]
        │ ✓ Task added           │
        │                        │
        │ [+ Create Another]     │ [Quick action]
        │ [View Task]            │ [View details]
        │ [Dismiss]              │ [Return to home]
        └────────────────────────┘
```

---

## Step-by-Step Breakdown

### Step 1: Trigger (Create Button)

**Button Location**:
- Bottom tab: "+" or "Create" tab
- Floating action button (on home screen)
- Keyboard shortcut (mobile: pull to refresh gesture)
- Menu option (overflow)

**Design Notes**:
- Always accessible
- Primary CTA visually prominent
- Color: Brand color (blue/green)
- Icon: "+" symbol
- Mobile: Bottom-safe area

### Step 2: Task Creation Sheet

**Sheet Layout**:
```
┌─────────────────────────────────┐
│ ≡ [Drag handle]     [×] Close    │ [Header]
├─────────────────────────────────┤
│                                 │
│ What's the task?                │ [Label]
│ ┌───────────────────────────────┐│
│ │ [Enter task title...]         ││ [Input field]
│ └───────────────────────────────┘│
│ Suggested:                      │ [Auto-complete]
│ • Fix login bug                 │ (if similar tasks)
│ • Update dashboard              │
│                                 │
├─────────────────────────────────┤ [Divider]
│                                 │
│ [👤 Assign to me ▼]             │ [Assignee - optional]
│ [📅 No deadline ▼]              │ [Deadline - optional]
│ [🚩 Medium priority ▼]          │ [Priority - optional]
│ [📝 No description]             │ [Description hint]
│                                 │
├─────────────────────────────────┤
│                                 │
│ [← Cancel]     [Create Task →]  │ [Footer buttons]
│                                 │
└─────────────────────────────────┘
```

**Field Details**:

**1. Task Title**
- Label: "What's the task?"
- Placeholder: "Enter task title..."
- Auto-focus when sheet opens
- Max 200 characters
- Auto-suggest similar tasks (if typing similar)
- Clear field button (X on right)

**2. Assignee**
- Label: "👤 Assign to"
- Default: "Me" (current user)
- Tap to select: Shows team member list
- Search to filter by name/email
- Unassigned option available
- Avatar shown for selected person

**3. Deadline**
- Label: "📅 Deadline"
- Default: "None"
- Tap to open date picker
- Quick options: Today, Tomorrow, Next week, Custom
- Date format: "Jun 29, 2026"
- If past date selected: Show warning

**4. Priority**
- Label: "🚩 Priority"
- Default: "Medium"
- Options: Low, Medium, High, Urgent
- Tap to select
- Color-coded: Green (low), Blue (med), Orange (high), Red (urgent)

**5. Description (Hidden/Hint)**
- "+ Add description"
- Tapping opens expanded form
- Allows longer text and formatting
- Optional field

**Buttons**:
- **Cancel**: Closes sheet, discards form (confirm if data entered)
- **Create Task**: Submit form, validate, create

### Step 3: User Input

**Typing Task Title**:
```
User types: "Fix login bug"

As they type, show suggestions:
- ✓ Similar to "Login authentication error"
- ✓ Similar to "Fix auth flow"

User can:
- Keep typing new task
- Tap suggestion to select
- Clear and start over
```

**Selecting Assignee**:
```
User taps assignee field

Sheet expands to show:
┌─────────────────────────────┐
│ Assign to                   │
├─────────────────────────────┤
│ 🔍 [Search by name...]      │ [Search]
│                             │
│ Me                          │ [Current user]
│ Sarah Chen                  │ [Avatar] [Checked]
│                             │
│ Team members                │
│ Marcus Johnson              │ [Avatar]
│ Elena Rodriguez             │ [Avatar]
│ David Park                  │ [Avatar]
│ (Not assigned)              │ [Option]
│                             │
│ ✓ Unassigned                │ [Option]
│                             │
└─────────────────────────────┘

User taps "Marcus Johnson"
Field updates: "👤 Marcus Johnson"
Sheet collapses back
```

**Setting Deadline**:
```
User taps deadline field

Calendar picker opens:
┌──────────────────────────┐
│ Select deadline          │
├──────────────────────────┤
│ Quick options:           │
│ [Today]                  │
│ [Tomorrow]               │
│ [Next week]              │
│ [Next month]             │
│                          │
│ June 2026                │
│ Su Mo Tu We Th Fr Sa     │ [Calendar]
│    ...                   │
│    ...29(today) 30       │
│                          │
│ [← Prev] [Date] [Next →] │
│                          │
│ [Clear] [Select]         │
│                          │
└──────────────────────────┘

User taps "29" (today)
Field updates: "📅 Today"
Picker closes
```

**Setting Priority**:
```
User taps priority field

Dropdown appears:
┌─────────────────────────┐
│ Priority                │
├─────────────────────────┤
│ 🟢 Low                  │
│ 🔵 Medium (current)     │ [Checkmark]
│ 🟠 High                 │
│ 🔴 Urgent               │
│                         │
└─────────────────────────┘

User taps "High"
Field updates: "🚩 High"
Dropdown closes
```

### Step 4: Validation

**Client-Side Validation** (as user enters):
```
Title field:
- ✓ Empty → Placeholder text shown
- ✓ Length < 200 chars → OK
- ✓ Length > 200 chars → Truncate + warning

Assignee field:
- ✓ User exists → OK
- ✓ User not in team → Show "Not in team" label
- ✓ User deactivated → Show warning

Deadline field:
- ✓ Future date → OK
- ✓ Past date → Show "This date is in the past"
- ✓ No date → OK (optional)

Priority field:
- ✓ Always valid (5 options)
```

**Validation on Submit**:
```
User taps "Create Task"

Server validates:
1. Title present? (required)
   ✓ Yes → Continue
   ✗ No → Focus field, show "Title required"

2. Title length? (1-200 chars)
   ✓ Valid → Continue
   ✗ Too long → Truncate and continue

3. Assignee valid?
   ✓ User exists → Continue
   ✗ Invalid → Show "This user no longer exists"

4. Date valid?
   ✓ Valid date → Continue
   ✗ Invalid format → Reset to None

5. All OK?
   ✓ Yes → Create task
   ✗ No → Stop and show errors
```

**Error Handling**:

```
Empty Title:
┌──────────────────────────┐
│ ⚠️ Title is required     │ [Toast alert]
└──────────────────────────┘
Field highlighted in red
Cursor focused in field

Invalid Assignee:
┌────────────────────────────────────┐
│ ⚠️ This user is no longer          │
│    in the team                     │
│ [Use unassigned instead] [Edit]    │
└────────────────────────────────────┘

Server Error:
┌────────────────────────────────────┐
│ ⚠️ Failed to create task           │
│ [Retry] [Save for later] [Cancel]  │
└────────────────────────────────────┘
```

### Step 5: Submission

**Loading State**:
```
After "Create Task" pressed:

[Create Task →] button becomes:
[Loading spinner] "Creating..."

Form fields disabled
Sheet can't be dismissed
No back navigation
```

**API Call**:
```
POST /api/tasks
{
  "title": "Fix login bug",
  "assignee_id": "marcus_id",
  "deadline": "2026-06-29",
  "priority": "high",
  "team_id": "current_team_id",
  "description": ""
}

Response (Success):
{
  "id": "task_123",
  "title": "Fix login bug",
  "created_at": "2026-06-29T14:30:00Z",
  "status": "created"
}

Response (Error):
{
  "error": "Invalid assignee",
  "field": "assignee_id"
}
```

### Step 6: Success State

**Success Feedback**:
```
Task created successfully!

┌──────────────────────────────────┐
│ ✓ Task created                   │ [Toast - 3 sec]
│                                  │
│ [← View Task] [+ Another]        │ [Action buttons]
└──────────────────────────────────┘

Sheet remains open (ready for next task)
Or close on tap
```

**Post-Creation Options**:

1. **Create Another**
   - Clear form
   - Reset to defaults
   - Cursor in title field
   - Stay in create sheet

2. **View Task**
   - Close sheet
   - Navigate to task detail
   - Show newly created task
   - Can add description, attachments

3. **Dismiss**
   - Close sheet
   - Return to home
   - Task in list (if visible)

---

## Mobile-Specific Notes

### Touch Optimization
- All fields have 44x44px+ touch targets
- Text input has proper zoom prevention
- Date picker optimized for mobile
- Large buttons at bottom

### Keyboard Management
- Auto-focus on title input
- Show keyboard for text fields
- Hide keyboard for picker fields
- Clear keyboard when picker opens

### Safe Area
- Buttons in safe area (not under notch)
- Scroll space for long forms
- Bottom navigation remains accessible

### Performance
- Form stores to local storage (auto-save)
- If device lost connectivity, queue task
- Sync when online

---

## Error Scenarios

### Scenario 1: No Internet
**Problem**: User creates task without connection
**Flow**:
1. User fills form, taps Create
2. No network connection detected
3. Show: "You're offline. Task will sync when online."
4. Queue task locally
5. Sync when connection returns
6. Show: "Task synced successfully"

### Scenario 2: User Removed from Team
**Problem**: User creates task after being removed
**Flow**:
1. User fills form, taps Create
2. Server: Team no longer valid
3. Show: "You're no longer in this team"
4. Queue task (show draft)
5. Offer options: Pick new team, discard, save draft

### Scenario 3: Assignee Left Team
**Problem**: Selected person no longer in team
**Flow**:
1. User selects person who left
2. On submit, server rejects
3. Show: "[Name] is no longer in your team"
4. Options: [Unassign] [Choose someone else]
5. Keep other fields intact

### Scenario 4: Session Expired
**Problem**: User was logged out mid-creation
**Flow**:
1. User fills form, taps Create
2. Server: Auth required
3. Show: "Your session expired. Sign in again."
4. Navigate to login
5. Upon re-login, show: "Complete creating your task?"
6. Restore form data

---

## Success Metrics

### Primary Metrics
- **Completion Rate**: % who complete task creation
  - Target: > 95%
- **Time to Complete**: How fast can user create task?
  - Target: < 90 seconds
- **Error Rate**: % of submissions that fail
  - Target: < 2%
- **Abandonment**: % who start but don't finish
  - Target: < 5%

### Secondary Metrics
- **Field Completion**: % who fill optional fields
  - Assignee: > 70%
  - Deadline: > 50%
  - Priority: > 40%
- **Error Types**: Which validations fail most?
- **Retry Rate**: % who retry after error
- **Multiple Creates**: % who create another task

---

**Task Creation Flow Created**: June 2026
**Last Updated**: June 29, 2026