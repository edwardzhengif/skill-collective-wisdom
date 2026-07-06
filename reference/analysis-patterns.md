# Analysis Patterns & Anti-Patterns

This document provides detailed examples and anti-patterns that are too long for SKILL.md but valuable for understanding how to apply the framework correctly.

---

## Good Analysis Examples

### Example 1: Decision Problem (Standard Mode)

**User question**: "Should I quit my stable corporate job to start a business? I have 500k savings, married with one kid."

**Good Step 3 output**:

```
### Perspective 1: Benefits

**Core insight**: Entrepreneurship offers uncapped upside and autonomy, but the real benefit for your situation is timing — with 500k savings and presumably no elderly dependents mentioned, you have a 12-18 month runway that many aspiring entrepreneurs lack.

**Analysis**:
- **Financial runway**: 500k covers ~18 months of family living expenses + startup costs, giving you enough time to validate a business model
- **Learning acceleration**: Even if the business fails, the skills gained (sales, operations, hiring) compound and make you more valuable if you return to corporate
- **Age advantage**: If you're in your 30s-40s, you have enough experience to avoid rookie mistakes but enough career runway to recover from failure

**Limitations of this perspective**: This angle is inherently optimistic. It downplays the emotional and relational costs that aren't captured in financial calculations.

**Confidence**: Medium — the financial runway is calculable (High), but "learning acceleration" depends heavily on what business you start (Low without knowing the domain)
```

**Why this is good**:
- Specific to the user's concrete situation (500k, married, kid)
- Confidence is split by sub-claim (financial vs experiential)
- "Limitations" is honest about what this positive angle misses
- Not generic — references real tradeoffs (12-18 month runway, age consideration)

### Example 2: Diagnostic Problem (Standard Mode)

**User question**: "Why is our project always delayed?"

**Good Step 3 output**:

```
### Perspective 1: Direct causes

**Core insight**: The most visible cause is scope creep — 60% of features were added after sprint planning

**Analysis**:
- **No change control**: Anyone can add requirements mid-sprint without impact assessment
- **Estimation bias**: Team estimates based on best-case, not average-case scenarios
- **Dependency waits**: Backend APIs consistently delivered 2-3 days late, blocking frontend

**Limitations of this perspective**: Focuses on symptoms, not root causes. Why does scope creep happen? That's the systemic question.

**Confidence**: High (based on project management research — scope creep is the #1 cause of delays in 70% of studies)
```

**Why this is good**:
- Specific numbers (60%, 2-3 days)
- Acknowledges limitation honestly
- Confidence citation is relevant

### Example 3: Comparison Problem (Comparison Mode)

**User question**: "React vs Vue for a small team?"

**Good Step 3 output**:

```
## React vs Vue

| Dimension | React | Vue | Winner |
|-----------|-------|-----|--------|
| Learning curve | Steeper (JSX, concepts) | Gentler (template syntax, gradual adoption) | Vue |
| Ecosystem breadth | Vast (more libraries) | Growing but smaller | React |
| Hiring (2024) | ~3x more developers | Smaller but passionate pool | React |
| Small team fit | Overkill for simple apps | Right-sized, faster onboarding | Vue |
| Long-term flexibility | More options if you scale | May need migration if complexity grows | React |

**Bottom line**: For a 5-person startup building an MVP, Vue is likely the better fit — faster onboarding, right-sized for the complexity level.

**It depends on**: If you plan to scale to 20+ engineers in 12 months, React's hiring advantage starts to matter more.

**Pre-mortem**: If you choose Vue and it fails, the most likely reason is: you hit a complexity ceiling at ~50k lines and need to rewrite components that Vue's reactivity system handles poorly.
```

**Why this is good**:
- Table format is scannable
- "Winner" column gives clear recommendation per dimension
- Pre-mortem is specific and actionable
- "It depends on" is concrete, not vague

---

## Anti-Patterns (What NOT to do)

### Anti-Pattern 1: Empty Analysis

**Bad**:
```
There are both opportunities and risks. You need to consider multiple factors and weigh the pros and cons carefully. It depends on your specific situation.
```

**Why it's bad**: Could apply to literally any question. Provides zero insight.

**Fix**: Be specific. "The main risk is X because Y. The main opportunity is Z because W."

### Anti-Pattern 2: Forced Balance

**Bad**:
```
React has a larger community, but Vue also has a strong community. React has more jobs, but Vue also has job opportunities. Both are good choices.
```

**Why it's bad**: Pretends both sides are equal when evidence clearly favors one. Misleads user.

**Fix**: "React's community is 3x larger (source: StackOverflow survey). For hiring, React has a clear advantage. However, Vue's community is more cohesive and helpful for beginners."

### Anti-Pattern 3: Pretending Expertise

**Bad**:
```
According to industry experts, React is the best choice for enterprise applications. Research shows that companies using React have 30% higher productivity.
```

**Why it's bad**: "Industry experts" is vague, "30% higher productivity" is fabricated.

**Fix**: "From the ecosystem perspective, React has broader library support for enterprise patterns. I don't have specific productivity data — this would need case studies from similar companies."

### Anti-Pattern 4: Generic Confidence

**Bad**:
```
Confidence: Medium
```

**Why it's bad**: Doesn't explain why. User can't calibrate.

**Fix**: "Confidence: Medium — logical reasoning based on general principles, but I don't have data specific to your industry/company size."

### Anti-Pattern 5: Missing "When This Loses"

**Bad** (for Comparison):
```
### React Strengths
- Larger ecosystem
- More developers
- Better for complex apps
```

**Why it's bad**: Only shows one side. User can't make informed trade-off.

**Fix**: Add "When React loses: small teams, simple apps, rapid prototyping needed"

---

## Yellow Zone Handling Examples

### Example: Mixed Professional + Non-Professional

**User**: "I have chronic back pain. Should I switch to a standing desk?"

**Correct handling**:
```
**Important**: I cannot diagnose or treat your back pain — please consult a doctor or physiotherapist for the medical aspect.

For the standing desk decision itself, here's a multi-perspective analysis:

### Benefits perspective
[analyze ergonomic research on standing desks]

### Risks perspective
[analyze potential downsides of standing desks]

### Recommendation
See a physiotherapist who can assess YOUR specific condition. The standing desk decision depends on whether your pain is muscular, disc-related, or postural — only a professional can determine this.
```

### Example: Decision + Emotional State

**User**: "Should I quit my job? I've been feeling burned out for months."

**Correct handling**:
```
**Important**: Burnout can be a serious condition. I'd strongly recommend speaking with a mental health professional — this analysis covers the career decision, not the health aspect.

For the career decision:
[analyze benefits, risks, costs, stakeholders]

**Separately for the burnout**: Please consider talking to a therapist or counselor. Burnout affects decision-making quality, and addressing it first might change how you view the career options.
```

---

## Pre-Mortem Examples

### Example: Business Decision

**Question**: "Should we expand to Southeast Asia?"

**Pre-mortem perspective**:
```
Assume you expanded and it failed 18 months later. The most likely reasons:

1. **Underestimated localization**: Consumer behavior in Indonesia is fundamentally different from China. Your China playbook didn't transfer.
2. **Cash drain**: You needed 3x the initial investment to reach breakeven. By month 12, you were pulling resources from the core business.
3. **Talent gap**: Couldn't hire quality local leadership fast enough. Remote management from HQ created cultural friction.

**What this means**: Before expanding, validate each of these with specific data. Talk to 5 companies that tried similar expansion. What did they learn?
```

### Example: Personal Decision

**Question**: "Should I go back to school for an MBA?"

**Pre-mortem perspective**:
```
Assume you did the MBA and regretted it 2 years later. The most likely reasons:

1. **Opportunity cost**: 2 years of salary + tuition = $300k. The post-MBA salary bump didn't recoup this in 5 years.
2. **Network mismatch**: Your classmates went into consulting/finance. You wanted to stay in tech. The network wasn't useful.
3. **Skill gap**: The MBA taught general management. You needed specific technical leadership skills that the program didn't cover.

**What this means**: Talk to 3 people who did an MBA and stayed in your industry. Was it worth it for them? Why or why not?
```

---

## Solution Problem Example

### Example 4: Solution Problem (Standard Mode)

**User question**: "How should I reduce customer churn for my SaaS product?"

**Good Step 3 output**:

```
### Perspective 1: Ideal solution

**Core insight**: The ideal is zero churn — every customer stays forever. While impossible, the closest achievable version is: identify at-risk customers 30 days before they leave and intervene with targeted retention actions.

**Analysis**:
- **Predictive churn model**: Use usage patterns (login frequency, feature adoption, support tickets) to score churn risk
- **Proactive outreach**: At-risk customers get a personal call from their account manager, not an automated email
- **Value reinforcement**: Show customers the ROI they're getting (e.g., "You've saved 40 hours this month using feature X")

**Limitations of this perspective**: Assumes you have the data infrastructure and team to build this. For an early-stage startup, this is 6-12 months away.

**Confidence**: Medium — this is proven methodology (used by Salesforce, HubSpot), but I don't know your specific product's data maturity
```

**Why this is good**:
- Concrete, actionable (not "improve customer experience")
- Acknowledges feasibility constraints in the Limitations section
- Confidence distinguishes between proven methodology and user-specific applicability

---

## Brainstorming Problem Example

### Example 5: Brainstorming Problem (Standard Mode)

**User question**: "Help me brainstorm ways to improve employee engagement at our company."

**Good Step 3 output**:

```
### Perspective 1: Ideal solution

**Core insight**: The highest-engagement companies treat engagement as an outcome of good management, not a program to be launched. The ideal is: every manager creates conditions where people do their best work naturally.

**Analysis**:
- **Autonomy**: Give teams ownership of their roadmap, not just execution tickets
- **Mastery**: Create visible growth paths (not just "senior" titles, but skill-based tracks)
- **Purpose**: Connect daily work to customer impact — share customer stories weekly, not just quarterly all-hands

**Limitations of this perspective**: This is aspirational. It doesn't address the "what can we do by Friday" question.

**Confidence**: High — these are well-established engagement drivers (based on decades of organizational psychology research)
```

```
### Perspective 2: Wildcard ideas

**Core insight**: The most impactful engagement initiatives are often the ones that feel slightly uncomfortable or unconventional.

**Analysis**:
- **Reverse mentoring**: Junior employees mentor senior leaders on technology, culture trends, or new tools — flips hierarchy and gives juniors visibility
- **"FedEx days"**: One day per quarter where anyone can build anything and present it — some of Google's best features came from this
- **Transparent salary bands**: Publish everyone's compensation range — terrifying to implement, but companies that do it report higher trust and lower resentment

**Limitations of this perspective**: Wildcard ideas are high-variance. Some will be transformative, others will flop. The key is creating a safe space to experiment.

**Confidence**: Medium — these work in specific cultures (tech, creative), but may backfire in traditional or highly regulated environments
```

**Why this is good**:
- "Ideal solution" gives a strategic frame (engagement as outcome, not program)
- "Wildcard ideas" are genuinely unconventional (not just "do team lunches")
- Each idea has a specific mechanism, not just a label
- Confidence distinguishes between universal principles and culture-dependent ideas

---

## Quick Mode Example

**User question**: "Should I learn Python or JavaScript first? Quick answer please."

**Good Quick Mode output**:

```
**Quick analysis of**: Python vs JavaScript as a first language

**Key considerations**:
1. **Python**: Easier syntax, great for data/AI/automation, slower path to building visible products
2. **JavaScript**: Steeper initial curve, but you can build websites immediately, larger job market for web roles
3. **Your goal matters most**: Data science → Python. Web development → JavaScript. General programming → Python is gentler.

**My read**: If you have no specific goal, start with Python — the learning curve is gentler and the skills transfer well. You can always learn JavaScript later. Confidence: Medium (depends on your goals, which I don't know).

**Caveat**: Quick AI analysis, not comprehensive. For important decisions, think deeper.
```

**Why this is good**:
- Stays within 200-400 word target
- Still gives a clear recommendation with conditions
- Confidence is honest about what it doesn't know (user's goals)
- Ends with the standard caveat

---

## Step 4 Synthesis Example

**User question**: "Should our 10-person team adopt microservices or stay with our monolith?"

**Good Step 4 output**:

```
## Summary

### Key Findings
1. **Your team size is the deciding factor**: At 10 people, the operational overhead of microservices likely outweighs the architectural benefits. Most successful microservices adoptions happen at 30+ engineers.
2. **Your monolith isn't the problem**: The symptoms you described (slow deployments, hard to test) are solvable within a monolith through better modularization — which is 10x cheaper than a microservices migration.
3. **The real tension**: Microservices would give you better scaling and team autonomy, but only if you can afford 2-3 dedicated platform/DevOps engineers — which is 20-30% of your current team.

### Perspective Summary
| Perspective | Core View | Confidence | Key Basis |
|-------------|-----------|------------|-----------|
| Benefits | Better scaling, team autonomy | Medium | Only works at sufficient team size |
| Risks | Operational complexity, distributed system failures | High | Well-documented in industry literature |
| Costs | 2-3 engineers dedicated to infrastructure | High | Based on typical microservices overhead |
| Stakeholders | Developers bear the burden of complexity | Medium | Depends on current team's distributed systems experience |

### What I'm Fairly Certain About
- At 10 people, microservices adoption is premature
- Modular monolith solves 80% of the problems at 20% of the cost

### What I'm Less Sure About
- Whether your specific scaling needs justify the early migration
- How your team's skill set would handle the transition

### What I Cannot Determine
- Your actual traffic/growth projections (would change the scaling argument)
- Your team's appetite for operational complexity

### Suggested Next Steps
1. **First action**: Try modularizing your monolith (extract 1-2 bounded contexts as modules within the monolith). This gives you 80% of the organizational benefits without the infrastructure cost. Timeline: 2-4 weeks.
2. **Gather info**: Measure your current deployment frequency and incident rate. Track these for 1 month after modularization.
3. **Consult**: Talk to a CTO or engineering leader who has done both monolith-to-microservices AND monolith-modularization. Ask them which they'd recommend at your scale.
```

**Why this is good**:
- Clear, opinionated conclusion ("microservices adoption is premature") — not wishy-washy
- Separates certainty levels clearly
- "First action" has specific timeline (2-4 weeks) appropriate to the decision scale
- "Consult" recommendation is specific (find someone who's done both)

---

## Special Handling Examples

### Example: User Refuses to Clarify (Assumption Annotation)

**User**: "Help me analyze whether I should switch jobs."

**AI**: "To give better analysis, what industry are you in? What's your main concern — salary, growth, or work-life balance?"

**User**: "Just analyze it. Don't ask me questions."

**Good output**:

```
**Quick analysis of**: Whether to switch jobs

⚠️ **Assumptions made** (since context was not confirmed):
- I'm assuming you're in a professional/white-collar role (analysis would differ greatly for different industries)
- I'm assuming you have 3-7 years of experience (career stage affects the calculus)
- I'm assuming salary and growth are both important (you didn't specify priorities)

If these assumptions are wrong, the analysis may not apply to your situation.

### Benefits of switching
[analysis based on assumptions]

### Risks of switching
[analysis based on assumptions]

...
```

**Why this is good**:
- Assumptions are explicit and numbered
- Each assumption includes WHY it was made
- Clear caveat that wrong assumptions = wrong analysis
- Still provides value despite missing information

### Example: User Corrects the Analysis

**AI**: "...the market is growing at 15% annually..."

**User**: "That's wrong. The market actually shrank 5% last year. Here's the report."

**Good response**:

```
Thanks for the correction. With the market actually shrinking 5% (not growing 15%), the analysis changes significantly:

**What changes**:
- The "Benefits" perspective is now much weaker — market expansion is no longer a reason to enter
- The "Risks" perspective strengthens — entering a shrinking market means fighting for existing share, not riding a growing tide
- The "Costs" perspective is relatively unchanged — the investment required is the same regardless of market direction

**Updated conclusion**: The evidence now more strongly favors NOT entering this market. The original analysis leaned toward "cautiously enter" — with the corrected data, I'd lean toward "wait and observe."

Note: Your correction is marked as High confidence since you provided a source.
```

**Why this is good**:
- Accepts correction without defensiveness
- Maps the correction to specific affected perspectives
- Updates the conclusion explicitly
- Acknowledges the source-based confidence

### Example: Confirmation Bias Detection

**User**: "I think React is better than Vue. Can you help me convince my team?"

**Good response**:

```
I notice you've already decided React is better and want help communicating your reasoning to others. I'll help, but first let me make sure you've considered the counterarguments — your team might have valid reasons for preferring Vue.

### Why your team might prefer Vue (deliberately strengthened)
[deeper-than-usual analysis of Vue's advantages]

### Why React might genuinely be better in your case
[analysis supporting React]

### What would change my mind
[specific conditions where Vue would be the better choice]

If you still prefer React after considering these counterarguments, that's a stronger position — you've stress-tested your preference rather than just confirming it.
```

**Why this is good**:
- Explicitly flags the user's bias upfront
- Deliberately strengthens the opposing perspective
- Frames the analysis as "stress-testing your preference" not "undermining your decision"
- Gives the user agency while providing intellectual honesty
