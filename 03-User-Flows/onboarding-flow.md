# Onboarding Flow: TaskFlow

## Flow Overview

**Flow Name**: First-Time User Onboarding
**Personas**: All (Sarah, Marcus, Elena)
**Goal**: New user creates account, joins/creates team, sees first tasks
**Duration**: 5-10 minutes
**Success Rate Target**: 80%+ completion within first session

---

## Onboarding Context

### When Does This Flow Happen?
- User installs app for first time
- User has no existing account
- User is new to TaskFlow

### Success Criteria
User completes onboarding when:
1. ✅ Account created
2. ✅ Team created or joined
3. ✅ First teammates invited or added
4. ✅ First task visible or created
5. ✅ Settings reviewed

---

## Onboarding Flow Diagram

```
┌──────────────┐
│ App Launched │ [First time, no account]
└──────┬───────┘
       │
       ▼
  ┌─────────────────────┐
  │ Welcome Screen      │ [Hero image, value prop]
  │ "Get Started" CTA   │
  └──────┬──────────────┘
         │
         ▼
    ┌────────────────────┐
    │ Sign Up / Login    │ [Email or social auth]
    │ Email input        │
    └──┬────────────────┬┘
       │                │
   Valid?           Invalid?
       │                │
       ▼                ▼
   ┌─────────┐     ┌──────────────┐
   │ Email   │     │ Show Error   │
   │ Verify  │     │ "Invalid     │
   │ (OTP)   │     │  email"      │
   └────┬────┘     └──────┬───────┘
        │                 │
        │         [User corrects and retries]
        │                 │
        └────────┬────────┘
                 ▼
        ┌──────────────────────┐
        │ Create Profile       │
        │ - Full name          │
        │ - Profile picture    │
        │ - Role/Title         │
        └────────┬─────────────┘
                 │
                 ▼
        ┌──────────────────────┐
        │ Team Decision        │ [Decision point]
        │ Create vs Join?      │
        └─┬────────────────┬───┘
          │                │
    [Create]         [Join]
          │                │
          ▼                ▼
    ┌─────────────┐  ┌──────────────────┐
    │ New Team    │  │ Join Team        │
    │ - Name      │  │ - Enter code or  │
    │ - Industry  │  │   scan QR code   │
    │ - Size      │  │ - Select team    │
    └──────┬──────┘  └────────┬─────────┘
           │                  │
           └────────┬─────────┘
                    ▼
        ┌─────────────────────────────┐
        │ Invite Teammates (Optional) │
        │ - Add emails                │
        │ - Send invites              │
        │ - Or skip for now           │
        └────────┬────────────────────┘
                 │
                 ▼
        ┌─────────────────────┐
        │ Settings Review     │
        │ - Notifications     │
        │ - Preferences       │
        │ - Integrations      │
        └────────┬────────────┘
                 │
                 ▼
        ┌─────────────────────┐
        │ Tutorial (Optional) │
        │ - Key features demo │
        │ - Shortcut to skip  │
        └────────┬────────────┘
                 │
                 ▼
        ┌─────────────────────┐
        │ Home Screen         │
        │ - Show first tasks  │
        │ - Celebration toast │
        │ [✓ Onboarding done] │
        └─────────────────────┘
```

---

## Step-by-Step Breakdown

### Step 1: Welcome Screen

**Screen Elements**:
- Large app logo
- Hero image/illustration
- Headline: "Meet your team. Stay aligned."
- Subheading: "TaskFlow: Lightweight task management for remote teams"
- 3-4 benefit bullets
- Large "Get Started" button
- Small "Already have an account? Sign In" link

**Design Notes**:
- Mobile-optimized (full screen on small devices)
- Minimal text, clear CTA
- Professional but approachable tone
- No complexity

**User Journey**:
```
User sees welcome screen
  ├─ Impressed by design/message? → "Get Started"
  ├─ Already has account? → "Sign In"
  └─ Close app? → [Lost user, goal: Re-engage]
```

### Step 2: Sign Up / Login

**Email Entry**:
- "What's your email?" input field
- Clear label and placeholder
- Email validation (must be valid format)
- "Continue" button
- "Already have account? Sign In" link

**Error Handling**:
```
Invalid email format
  ├─ Show: "Please enter a valid email"
  ├─ Highlight field (red border)
  └─ Focus cursor in field for correction

Email already registered
  ├─ Show: "This email already has an account. Sign In?"
  ├─ Option: [Sign In] or [Use different email]
```

**Design Notes**:
- Single field, single action
- No password yet (reduce friction)
- Social auth (Google/GitHub) option below
- Mobile keyboard triggers email mode

### Step 3: Email Verification (OTP)

**OTP Entry**:
- "Check your email for a code"
- 4-6 digit code input field
- Auto-focus on field
- Auto-submit when all digits entered
- "Didn't get code? Resend" link
- Timer showing resend availability (60 seconds)

**Error Handling**:
```
Invalid code
  ├─ Show: "This code isn't valid"
  ├─ Clear field
  └─ Allow retry

Code expired (> 10 minutes)
  ├─ Show: "This code expired. Request a new one."
  ├─ "Resend" button enabled

Too many failed attempts
  ├─ Show: "Too many attempts. Try again in 5 minutes."
  ├─ Disable input temporarily
```

**Design Notes**:
- No password complexity = simpler, more secure
- OTP sends to email (no SMS dependency)
- Auto-submit improves UX
- Mobile-friendly input

### Step 4: Create Profile

**Profile Form**:
```
What's your name?
[Full name input field]

Choose a profile picture (optional)
[Camera icon] [Upload] [Skip]

What do you do?
[Project Manager ▼] [dropdown]

[Continue button]
```

**Form Validation**:
- Name required (min 2 characters)
- Name auto-capitalized
- Picture optional (default avatar)
- Role optional (can be set later)

**Error Handling**:
```
Name too short
  ├─ Show: "Please enter your full name"

Profile picture too large
  ├─ Show: "Image must be under 2MB"

Invalid image format
  ├─ Show: "Please use JPG, PNG, or GIF"
```

**Design Notes**:
- 3 simple fields
- Profile picture optional (reduces friction)
- Pre-filled with detected name if available
- Mobile: Vertical stacking, large inputs

### Step 5: Team Decision Point

**Decision Screen**:
```
Do you want to start a new team or join an existing team?

[Create a new team]
[Button with + icon]

[Join a team]
[Button with link icon]
```

**Design Notes**:
- Large, clear buttons
- Icons help with quick comprehension
- No default selection (intentional choice)
- Both options equally prominent

### Step 5a: Create New Team Path

**New Team Form**:
```
Team name
[My Team name input]

Industry (optional)
[Select industry ▼]

Team size
[2-5 people ▼]

[Create team button]
```

**Validation**:
- Team name required (3-50 characters)
- Industry optional
- Team size helps with onboarding suggestions

**What Happens Next**:
- Team created with user as owner
- User shown unique team code for invites
- Option to invite teammates immediately

### Step 5b: Join Existing Team Path

**Join Team Options**:
```
How do you want to join?

[Enter team code]
[Paste code: ______]

OR

[Select from list]
Available teams:
- Acme Inc
- Project Runway
- Startup XYZ

[Request to join]
```

**Error Handling**:
```
Invalid team code
  ├─ Show: "This code isn't valid"
  ├─ Show: "Check the code and try again"

Team code expired
  ├─ Show: "This code has expired"
  ├─ Show: "Ask your team lead for a new code"

Team full
  ├─ Show: "This team has reached capacity"
```

**Design Notes**:
- Two join methods (flexibility)
- Copy/paste code is simpler than manual entry
- Option to browse teams if available

### Step 6: Invite Teammates (Optional)

**Invite Screen**:
```
Invite your teammates (optional)

Email addresses
[sarah@company.com, mark@company.com  ▼]
[Add another]

[Send invites]
[Skip for now]
```

**Design Notes**:
- Multi-email input
- Auto-detection of domain colleagues (if available)
- Completely optional (can add later)
- Skip button prominent

**After Send**:
- Show: "Invites sent! They'll receive emails to join."
- Show loading as invites process
- Option to add more or continue

### Step 7: Settings Review

**Quick Settings Screen**:
```
Final setup

Notifications
[Toggle] Receive push notifications
[Toggle] Receive email digests

Preferences
[Toggle] Show unread badge
[Toggle] Dark mode (opt-in)

[I'm ready! button]
```

**Design Notes**:
- Only essential settings
- Sane defaults (push notifications ON, email ON)
- Users can customize later in Settings
- Minimal friction approach

### Step 8: Tutorial (Optional)

**Quick Tour**:
```
Screen 1: "Welcome to TaskFlow"
- Show home screen
- Highlight key features
- "Next" button

Screen 2: "Manage your tasks"
- Show task example
- Highlight priority, deadline
- "Next" button

Screen 3: "Collaborate with your team"
- Show comment/mention
- "Next" button

Screen 4: "You're all set!"
- Show team dashboard
- "Let's go" button
- "Skip tour" always available
```

**Design Notes**:
- 3-4 screens max (don't overwhelm)
- Each screen highlights one concept
- Skip button always available
- Can re-access tutorial in Settings

### Step 9: Home Screen (Success)

**First Look Home Screen**:
```
┌─────────────────────────┐
│ Welcome to TaskFlow, Name! │ [Personalized greeting]
│                           │
│ [Create your first task] │ [Highlighted CTA]
│  Big friendly button      │
│                           │
│ Quick start guides        │
│ - How to create a task    │
│ - How to collaborate      │
│ - Settings & preferences  │
│                           │
│ [Your team members]       │
│ Sarah Chen                │
│ Marcus Johnson            │
│ (if invited)              │
│                           │
│ 🎉 Congrats! You're set up.│
└─────────────────────────┘

[Bottom Navigation]
[Home] [Team] [Create] [Messages] [Profile]
```

**Design Notes**:
- Celebratory but not cheesy
- Onboarding-specific content
- Easy path to first task creation
- Shows team members (if any)

---

## Error Scenarios & Recovery

### Scenario 1: User Abandons at Email Entry
**Problem**: User doesn't have email or doesn't want to share
**Solution**: 
- Show: "We only use email for verification"
- Social auth options (Google, GitHub)
- Clear privacy note: "We'll never spam you"

### Scenario 2: User Doesn't Get OTP
**Problem**: Email bounces or takes time
**Solution**:
- Resend button (60 second timer)
- "Check spam folder" hint
- Option to resend to different email
- Support link if persistent issue

### Scenario 3: User Doesn't Know Team Code
**Problem**: User invited but doesn't have code
**Solution**:
- "Ask your team lead for an invite code"
- Browse available teams option
- Support/help link
- Request to join (if team discovery enabled)

### Scenario 4: User Leaves During Onboarding
**Problem**: User closes app mid-onboarding
**Solution**:
- Save progress (email verified, profile created)
- Resume where they left off next session
- Don't require re-entry of completed steps

---

## Mobile-Specific Considerations

### Keyboard Management
- Show keyboard only when needed
- Hide keyboard for decision screens
- Auto-move between fields
- Clear visual feedback on focus

### Screen Space
- Full-screen modals, not overlays
- Vertical scrolling for longer forms
- Large touch targets (44x44px min)
- Bottom navigation clear and reachable

### Network Handling
- Cache welcome content
- Show loading indicators clearly
- Handle slow/offline connections
- Retry logic for failed submissions

---

## Success Metrics

### Primary Metrics
- **Completion Rate**: % who finish onboarding in first session
  - Target: > 80%
- **Time to Completion**: How long does onboarding take?
  - Target: < 8 minutes
- **Drop-off Points**: Where do users quit?
  - Track each step completion %
- **Activation**: % who create first task within 24h
  - Target: > 60%

### Secondary Metrics
- **Team Creation**: % who create vs join team
- **Profile Completion**: % who add picture/role
- **Invite Rate**: % who invite teammates
- **Settings**: % who customize preferences
- **Return Rate**: % who come back after 7 days
  - Target: > 70%

---

## A/B Testing Ideas

1. **Tutorial**: With vs without video tutorial
2. **Invites**: Invite screen placement (early vs late)
3. **Settings**: Simplified vs full settings screen
4. **Onboarding Copy**: Formal vs friendly tone
5. **Button Text**: "Get Started" vs "Launch App"

---

## Post-Onboarding Experience

Once onboarding completes, user should:
1. See empty/sample dashboard
2. Understand next steps clearly
3. Have easy path to first action
4. Feel supported (help/FAQ links)
5. Know how to get teammates involved

---

**Onboarding Flow Created**: June 2026
**Last Updated**: June 29, 2026