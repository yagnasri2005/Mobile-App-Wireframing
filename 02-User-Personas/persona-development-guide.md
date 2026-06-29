# User Personas: Development Guide

## What Makes a Good Persona?

A persona is a semi-fictional representation of your target user, based on real research. It should include:

✅ **Based on Research** - Derived from interviews, surveys, and data
✅ **Specific Demographics** - Age, role, location, experience level
✅ **Clear Goals** - What does this person want to accomplish?
✅ **Real Pain Points** - What frustrates them?
✅ **Honest Behaviors** - How do they actually work?
✅ **Memorable** - Give them a name and picture, make them real
✅ **Actionable** - Helps guide design decisions

❌ **Not Based on Assumptions** - Avoid guessing
❌ **Too Broad** - "People who use apps" is not a persona
❌ **Too Narrow** - "Left-handed developers in Austin" is too specific
❌ **Wishful Thinking** - Design for actual users, not ideal users

---

## Persona Template

Use this template to develop personas for your own app:

```markdown
# Persona: [Name]

## Demographics
- **Name**: 
- **Age**: 
- **Location**: 
- **Role/Title**: 
- **Years of Experience**: 
- **Team/Company Size**: 
- **Primary Device**: 
- **Tech Comfort Level**: 

## Goals (Primary & Secondary)
**Primary Goals**
1. [Goal 1]
   - Current friction: 
   - Desired outcome: 

2. [Goal 2]
   - Current friction: 
   - Desired outcome: 

**Secondary Goals**
1. [Goal 3]

## Pain Points (Ranked by Severity)
1. **[Pain Point]** (Severity: High/Medium/Low)
   - Description: 
   - Impact: 

## Behaviors
- **Daily Routine**: 
- **Device Usage**: 
- **Session Duration**: 
- **Peak Times**: 
- **Weekly Pattern**: 
- **Notification Preference**: 
- **Work Environment**: 

## Quote
> "[Memorable quote that captures their perspective]"

## Design Implications
- 
- 
- 

## Pricing Acceptability
- **Would pay**: 
- **Budget constraints**: 
- **Decision factors**: 
```

---

## How to Develop Personas

### Step 1: Define Your User Segments (Research Phase)

**Conduct interviews** with 8-15 potential users
- Ask about their goals and frustrations
- Understand their current workflows
- Learn about their environment
- Identify patterns

**Distribute surveys** to 50-100+ people
- Validate patterns found in interviews
- Get quantitative data
- Identify segments

**Analyze competitive products**
- Who uses competitor apps?
- What features do different users rely on?
- Are there underserved segments?

**Look at your own data** (if available)
- How do different users interact with your product?
- What features do different cohorts use?
- Where do they get stuck?

### Step 2: Identify Common Patterns

Look for themes across your research:
- What goals appear repeatedly?
- What pain points are universal?
- Are there distinct behavioral patterns?
- Do certain demographics cluster together?

**Example Pattern Identification**:
```
Interview 1: "I check my tasks on my phone while commuting"
Interview 4: "I mostly use the app on mobile"
Interview 7: "Phone is how I stay connected to my team"
Survey Result: 68% check tasks on mobile daily

→ Pattern: Mobile-centric users are a significant segment
```

### Step 3: Group Users into Segments

Typically, you'll find 2-4 major segments. Each should represent:
- Similar goals
- Similar pain points
- Similar behaviors
- Similar needs

**But different from other segments in meaningful ways**

**Example Segments**:
- Segment A: Team leads managing others (need team visibility)
- Segment B: Individual contributors (need personal efficiency)
- Segment C: Executives (need strategic overview)

### Step 4: Create 2-4 Personas

For each segment, create one persona:
- Give them a name and face (use stock photos)
- Write their demographic profile
- Document their goals
- List their pain points
- Describe their typical behaviors
- Add a memorable quote
- Note design implications

### Step 5: Validate Your Personas

**Ways to validate**:
1. **Interview existing customers** - Do they match your personas?
2. **Survey potential users** - "Which persona sounds like you?"
3. **User testing** - Do people behave as predicted?
4. **Track actual usage** - Do patterns match predictions?
5. **Support tickets** - Which personas ask for what?

---

## Common Persona Mistakes to Avoid

### ❌ Mistake 1: Making Personas Too Similar
**Problem**: If personas are too similar, they're not useful
**Solution**: Personas should differ in goals, pain points, or behaviors

### ❌ Mistake 2: Making Personas Too Specific
**Problem**: "Android user with 7 years experience in Nashville" is too narrow
**Solution**: Focus on what matters for your product

### ❌ Mistake 3: Not Basing on Research
**Problem**: Making up personas based on assumptions
**Solution**: Every detail should come from research

### ❌ Mistake 4: Creating "Ideal" Users
**Problem**: Creating persona of perfect user instead of typical user
**Solution**: Include frustrations and limitations

### ❌ Mistake 5: Too Many Personas
**Problem**: Creating 5+ personas dilutes focus
**Solution**: Stick to 2-4 personas that cover 80%+ of users

### ❌ Mistake 6: Not Updating Personas
**Problem**: Creating personas once, never revisiting
**Solution**: Refresh personas quarterly based on new data

---

## Persona Template Examples

### Example 1: E-commerce Persona

```
# Persona: Jennifer - The Busy Mom

## Demographics
- **Age**: 35-42
- **Role**: Working parent, household manager
- **Income**: $60-100k household
- **Device**: iPhone (primary)
- **Tech Comfort**: Intermediate

## Goals
1. **Quick Shopping** - Find and buy what I need in < 5 minutes
2. **Good Deals** - Save money on regular purchases
3. **Convenience** - No need to visit stores

## Pain Points
1. **Limited Time** - Can't browse, need directed options
2. **Decision Paralysis** - Too many choices
3. **Mobile Experience** - Current apps are slow

## Behaviors
- Shops in short 5-10 minute windows
- Uses phone exclusively
- Values time over features
- Prefers simplicity

## Design Implications
- Quick checkout (< 3 steps)
- Personalized recommendations
- Mobile-first design
- Fast load times
- Saved preferences
```

### Example 2: SaaS Personas

```
# Persona: David - The Tech-Savvy Founder

## Demographics
- **Age**: 28-35
- **Role**: Startup founder/CEO
- **Company**: 5-15 employees
- **Device**: Mac + iPad
- **Tech Comfort**: Expert

## Goals
1. **Solve Real Problem** - Address specific pain point
2. **ROI** - Measure business impact
3. **Integration** - Works with current stack

## Pain Points
1. **Tool Proliferation** - Too many apps
2. **API/Integration Issues** - Tools don't talk
3. **Costs Add Up** - SaaS budget ballooning

## Behaviors
- Tests new tools frequently
- Reads product blogs, follows indie hackers
- Uses multiple tools but wants consolidation
- Cares about pricing

## Design Implications
- Clear integration story
- Pricing transparency
- API-first approach
- Power user features
- Good documentation
```

---

## Using Personas in Design

### When Making Design Decisions, Ask:

**"Which persona is this for?"**
- If different personas need different solutions → complex
- If all personas agree → simple, build it
- If one persona strongly disagrees → make it optional

**"Does this solve their pain point?"**
- If yes → include it
- If partially → iterate
- If no → remove or rethink

**"Can they accomplish their goal?"**
- If yes → good
- If it's hard → simplify
- If it's impossible → redesign

**"Does this respect their behaviors?"**
- If they work on mobile → make it mobile-optimized
- If they work in short bursts → make it fast
- If they work in teams → make collaboration easy

### Example Decision Using Personas:

**Decision**: Should we include task templates?

**Analyze by Persona**:
- **Sarah (PM)**: "Yes, save templates for recurring projects" → Useful
- **Marcus (Dev)**: "Too much overhead, I just want to list tasks" → Not useful
- **Elena (Exec)**: "Maybe, if templated dashboards" → Partially useful

**Decision**: Include templates, but make them optional and simple. Default is blank task creation for Marcus's workflow, templates available for Sarah's workflow.

---

## Persona Documentation

### What to Include in Your Persona Document

1. **Overview** - Why these personas?
2. **Primary Personas** - Detailed profile of 2-3 main personas
3. **Secondary Personas** - Brief profile of supporting personas
4. **Comparison Matrix** - Side-by-side comparison
5. **Usage Scenarios** - Day-in-the-life for each persona
6. **Design Priorities** - What matters to each persona?
7. **Validation Data** - How we know this is accurate
8. **Update Schedule** - When to refresh personas

### Sharing Personas

1. **Team Alignment** - Print persona posters for the wall
2. **Interview Guides** - Use personas to guide user interviews
3. **Design Specs** - Reference personas in design decisions
4. **Feature Prioritization** - Use to make tough tradeoffs
5. **Product Roadmap** - Which personas' needs are we addressing?

---

## Persona Refresh Schedule

**Monthly**: Track usage data, note patterns
**Quarterly**: Validate assumptions with interviews
**Bi-annually**: Major persona refresh if needed
**Annually**: Comprehensive persona review

---

**Guide Created**: June 2026
**Last Updated**: June 29, 2026