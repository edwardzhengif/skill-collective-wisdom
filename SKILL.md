---
name: "collective-wisdom"
description: "Structured multi-perspective analysis framework. Invoke when user needs decision analysis, option comparison, problem diagnosis, or brainstorming from multiple angles."
---

# Multi-Perspective Analysis Framework

> Version: 1.3.2

A structured thinking framework that helps users examine problems from multiple angles. This is NOT expert advice — it is an organizational tool for thinking.

**FIRST RUN**: Before first use, read `reference/analysis-patterns.md` for examples of correct output and common anti-patterns to avoid.

---

## IMPORTANT LIMITATIONS

- This is AI-generated analysis, NOT professional advice
- All perspectives come from the same AI — there is no real diversity of thought
- For high-stakes decisions, always consult qualified human professionals
- The AI cannot access real-time data or replace professional judgment

---

## When to Invoke This Skill

| User Intent | Example Phrases | Action |
|-------------|-----------------|--------|
| Decision analysis | "Should I do A or B?", "Help me decide..." | Full analysis |
| Option comparison | "Compare A vs B", "Which is better..." | Comparison analysis |
| Problem diagnosis | "Why is X happening?", "What went wrong..." | Root cause analysis |
| Solution design | "How should I solve X?", "What are my options..." | Solution exploration |
| Brainstorming | "I need ideas for...", "Help me think about..." | Idea generation |

**DO NOT invoke** when:
- User asks a factual question with a known answer → Use search
- User needs professional advice (medical, legal, financial, mental health) → Advise consulting a professional
- User needs real-time data → Suggest data tools
- User is in crisis (expressing self-harm) → Provide crisis resources immediately

**Doesn't fit the 5 types above?** Use this heuristic: if the user benefits from seeing a problem through multiple lenses, use this skill. If they need a single direct answer, don't. Examples of "doesn't fit but still useful": creative writing feedback (use Brainstorming lenses with divergent + constraint-challenging perspectives), relationship advice (use Decision lenses with sensitivity).

---

## Language & Tone Rules

- **Match the user's language**. If user writes in Chinese, respond in Chinese. If English, respond in English.
- **Adapt tone to context**. Technical questions → precise and structured. Personal decisions → warm but honest. Creative questions → more exploratory.
- **Template labels** (like "Core insight", "Confidence") should be translated to match the user's language.

---

## Input Handling

| Input Type | Handling |
|------------|----------|
| Normal text question | Standard workflow |
| Very long text (>500 words) | Identify the core question first, ask user to confirm |
| Code snippet | Analyze the question about the code, not the code itself |
| Multiple sub-questions | Ask user to prioritize 1-2 most important ones |
| Image/file | Acknowledge limitation: "I can analyze your description of the problem, but cannot process attached files directly" |

---

## Workflow

### Step 0: Applicability Check (REQUIRED — always do this first)

Before any analysis, check if this skill is appropriate:

**Three-zone model** (not binary):

| Zone | Criteria | Action |
|------|----------|--------|
| **Green** (Full analysis) | General decision, strategy, comparison, diagnosis | Proceed with full workflow |
| **Yellow** (Partial + referral) | Touches professional domain but user wants thinking framework, OR mixed scenario (decision + emotional distress) | Analyze the non-professional dimensions, explicitly refer professional dimensions to a professional |
| **Red** (Reject) | Specific medical/legal/financial advice, crisis, factual question with known answer | Do NOT analyze, provide referral |

**Yellow zone examples**:
- "Should I quit my job? I've been depressed for 6 months" → Analyze career decision dimensions, explicitly recommend seeing a mental health professional for the depression aspect
- "Which investment has better returns?" → Cannot give specific advice, but CAN analyze "what factors to consider when evaluating investments"
- "Is this contract clause enforceable?" → Cannot give legal advice, but CAN analyze "what dimensions to discuss with your lawyer"

**Red zone — MUST REJECT**:

| Category | Example | Suggested Alternative |
|----------|---------|----------------------|
| Medical diagnosis | "What disease do I have?" | "Please consult a doctor" |
| Legal advice | "Is this legal?" | "Please consult a lawyer" |
| Specific financial advice | "Which stock to buy?" | "Please consult a financial advisor" |
| Mental health crisis | "I want to hurt myself" | Provide crisis hotline numbers immediately |
| Factual questions | "What is the capital of France?" | Answer directly or search |
| Urgent emergency | "My house is on fire" | "Call emergency services immediately" |

**Crisis response** (if user expresses self-harm intent):
```
If you are in crisis, please reach out:
- Emergency: Call your local emergency number (911 in US, 120 in China)
- Crisis hotline: 988 (US), 400-161-9995 (China)
- Text HOME to 741741 (US Crisis Text Line)

Your safety matters more than any analysis.
```

**Mid-analysis zone detection**: If during Step 3 or Step 4 you realize the question actually belongs in the Red zone (e.g., user's follow-up reveals a medical concern), STOP the analysis immediately. Say: "I've realized this question requires professional expertise I don't have. Here's what I can share so far, but please consult [relevant professional] for the parts I cannot analyze."

### Step 1: Problem Clarification

**Goal**: Ensure correct understanding before analyzing.

**When to skip**: ALL of these must be true:
- Question is specific (names concrete options, situation, or constraint)
- Only ONE reasonable interpretation exists
- User did NOT say "quick" (if they did, still skip but use Quick Mode)

**When to ask**: ANY of these is true:
- Question is vague ("How to succeed?")
- Multiple interpretations are possible
- Critical context is missing (budget? timeline? team size?)
- **User constraints are contradictory** (e.g., "I want low risk AND high returns" — flag this)

**Clarification template**:
```
**My understanding**: [Restate in one sentence]

**To give better analysis, I need to know**:
1. [Key context]
2. [Key constraint]
3. [What matters most to you]

Please confirm or correct.
```

**Contradiction detection**: If user's requirements are mutually exclusive (e.g., "fastest AND cheapest AND highest quality"), explicitly flag: "These three goals often conflict — which 1-2 are your true priorities?"

**User refuses to clarify**: If user says "just analyze it" or ignores clarification questions, proceed with best-effort analysis. In the output, explicitly mark assumptions:
```
⚠️ Assumptions made (since context was not confirmed):
- I'm assuming [X] because [reason]
- I'm assuming [Y] because [reason]
If these assumptions are wrong, the analysis may not apply to your situation.
```

### Step 2: Perspective Selection

Based on the problem type, select 3-4 relevant perspectives.

**Decision problems** (A or B?):
| Perspective | Focus | Key Question |
|-------------|-------|--------------|
| Benefits | Potential gains | What could go right? |
| Risks | Potential problems | What could go wrong? |
| Costs | Required investment | Is it worth the price? |
| Stakeholders | Impact on others | Who is affected and how? |

**Diagnostic problems** (Why is this happening?):
| Perspective | Focus | Key Question |
|-------------|-------|--------------|
| Direct causes | Immediate factors | What's the most obvious cause? |
| Systemic factors | Deeper structural issues | What system enables this? |
| Historical patterns | Past precedents | What happened in similar cases? |
| Counter-evidence | Exceptions and outliers | What contradicts the obvious explanation? |

**Solution problems** (How should I solve this?):
| Perspective | Focus | Key Question |
|-------------|-------|--------------|
| Ideal solution | Best possible outcome | If no constraints, what's optimal? |
| Real constraints | Practical limitations | What actually limits us? |
| Quick wins | Fastest impact | What can we do right now? |
| Long-term play | Most sustainable approach | What builds lasting value? |

**Brainstorming problems** (I need ideas...):
Use Solution perspectives as a base, but emphasize divergent thinking. Replace "Quick wins" with "Wildcard ideas" (unconventional, low-probability but high-impact possibilities). Skip the "Real constraints" perspective initially — brainstorming should explore freely before filtering.

**Comparison problems** (A vs B vs C...):
| Perspective | Focus | Key Question |
|-------------|-------|--------------|
| Option A strengths | Where A excels | When is A clearly better? |
| Option B strengths | Where B excels | When is B clearly better? |
| Shared weaknesses | Common downsides | What are ALL options' weaknesses? |
| Context fit | Which fits your situation | Given your constraints, which fits best? |

**For 3+ options**: Use the same structure but add rows for each option. Focus on the top 2-3 most relevant options rather than trying to cover all equally.

**Optional perspective — Pre-mortem** (add for high-stakes decisions):
| Perspective | Focus | Key Question |
|-------------|-------|--------------|
| Pre-mortem | Failure analysis | "Assume you chose X and it failed. What's the most likely reason?" |

Note: Comparison Mode's output template includes Pre-mortem by default for high-stakes decisions. For simple comparisons (e.g., "coffee or tea"), omit it.

**Selection rules**:
- 3-4 perspectives maximum (5 if including Pre-mortem)
- Each must focus on a distinct dimension (if you find yourself repeating the same arguments in two perspectives, merge them — a good test: can you describe the difference between two perspectives in one sentence? If not, they're the same perspective)
- Must be directly relevant to the question (ask: "Would the user miss something important without this perspective?")
- Do NOT force "balance" — if evidence favors one side, say so

### Step 2.5: User Priority Check (OPTIONAL — add for complex decisions)

After selecting perspectives, ask:
```
These dimensions cover different aspects. Which 1-2 matter most to you?
[If user specifies, weight the synthesis toward those dimensions]
```

**When to use**: Complex decisions where different priorities would lead to different conclusions.
**When to skip**: Simple questions, Quick Mode, or when the answer is obvious regardless of priority.
**If user doesn't respond**: Proceed without weighting. In synthesis, note: "Since no priority was specified, I've treated all dimensions equally. If one matters more to you, let me know and I'll adjust."

### Step 3: Multi-Perspective Analysis

**Use the template matching the problem type:**

#### Template A: Standard (for Decision, Diagnostic, Solution problems)

```
### Perspective N: [Name]

**Core insight**: [1-2 sentences — the most important thing this angle reveals]

**Analysis**:
- [Point 1]: [Specific reasoning]
- [Point 2]: [Specific reasoning]

**Limitations of this perspective**: [What this angle might miss]

**Confidence**: High / Medium / Low
- Reason: [Why this confidence level]
```

#### Template B: Comparison (for A vs B problems)

```
### [Option Name] Strengths

**When this option wins**: [The specific scenario where this is clearly better]

**Key advantages**:
- [Advantage 1]: [Why this matters]
- [Advantage 2]: [Why this matters]

**When this option loses**: [The specific scenario where this is clearly worse]

**Confidence**: High / Medium / Low
- For factual claims (e.g., "larger community"): High if data-supported
- For situational claims (e.g., "better for your team"): Medium/Low — depends on context I may not have
```

**Confidence definitions**:
| Level | Meaning | When to use |
|-------|---------|-------------|
| High | Strong evidence supports this | Has data, clear logic, or established precedent |
| Medium | Reasonable but uncertain | Logical but lacks data, educated guess |
| Low | Significant uncertainty | Mostly speculative, limited basis |

**Confidence edge cases**:
- User-provided facts → High confidence in the fact itself
- AI assumptions about user's situation → Low confidence (flag as assumption)
- Industry benchmarks → Medium confidence (may not apply to user's specific case)

### Step 4: Synthesis

**This is "organizing findings", NOT "delivering a verdict".** The user makes the final call.

**Output scope control**: If user explicitly requests limited output (e.g., "just analyze, don't give advice" or "just compare, don't synthesize"), respect that request. Skip the Suggested Next Steps section if user says "no advice". Skip the Summary if user says "just give me the perspectives."

```
## Summary

### Key Findings
1. [Most important cross-perspective insight]
2. [Unique insight from one perspective]
3. [Important tension — where perspectives genuinely disagree]

### Perspective Summary
| Perspective | Core View | Confidence | Key Basis |
|-------------|-----------|------------|-----------|
| [P1] | [view] | H/M/L | [basis] |
| [P2] | [view] | H/M/L | [basis] |

### What I'm Fairly Certain About
- [High-confidence points]

### What I'm Less Sure About
- [Medium/low-confidence points]

### What I Cannot Determine
- [Things that need real data or expert input]

### Suggested Next Steps
1. **First action**: [Specific action with appropriate timeframe — "today" for urgent items, "this week" for standard decisions, "this month" for major life decisions]
2. **Gather info**: [What additional info would help]
3. **Consult**: [What type of professional to consult, if applicable]
```

**If user specified priorities in Step 2.5**: Add a section:
```
### Based on Your Priorities
Since you said [X] matters most, [Option Y] appears strongest because [reason].
However, if [Z] becomes more important, consider [Option W] instead.
```

**If user asks for derivative output** (e.g., "use this analysis to write an email/presentation/report"): Complete the analysis first, then produce the derivative. The derivative should reference the analysis but not repeat it in full.

---

## Output Modes

**Mode priority when multiple modes trigger simultaneously**:
- Quick + Comparison → Use **Comparison Mode's table structure** with **Quick Mode's length limit** (200-400 words). This gives the user a scannable comparison without overwhelming them.
- Quick + Standard → Use **Quick Mode** (user explicitly asked for speed).
- Comparison + Standard → Use **Comparison Mode** (structured comparison is more useful than generic analysis for A vs B questions).

### Standard Mode (default)
Full 4-step analysis. **Target length: 800-1500 words.**

### Quick Mode
**Trigger**: User says "quick"/"brief", OR question is straightforward (single clear trade-off).

**Complexity gate**: If the question has >3 significant dimensions or involves uncertainty:
- If user explicitly said "quick" or "urgent" → Skip confirmation, use Quick Mode, but add bold note: "**This is a time-limited analysis. For important decisions, I recommend doing a full analysis later.**"
- Otherwise → WARN: "This question has several dimensions. A quick analysis may miss important nuances. Proceed with quick mode anyway, or would you prefer a fuller analysis?"

**Format** (target: 200-400 words):
```
**Quick analysis of**: [question]

**Key considerations**:
1. [Factor 1]
2. [Factor 2]
3. [Factor 3]

**My read**: [1-2 sentence assessment with confidence]

**Caveat**: Quick AI analysis, not comprehensive. For important decisions, think deeper.
```

### Comparison Mode
**Trigger**: User explicitly compares 2+ options (A vs B, or A/B/C/D).

**Format** (target: 500-800 words):
```
## [A] vs [B] [vs C...]

| Dimension | [A] | [B] | [C] | Winner |
|-----------|-----|-----|-----|--------|
| [Dim 1] | [analysis] | [analysis] | [analysis] | [A/B/C/Tie] |
| [Dim 2] | [analysis] | [analysis] | [analysis] | [A/B/C/Tie] |
| [Dim 3] | [analysis] | [analysis] | [analysis] | [A/B/C/Tie] |

**Bottom line**: [Summary with confidence]

**It depends on**: [What factors tip the balance]

**Pre-mortem** (include for high-stakes decisions, omit for simple comparisons): If you choose [winner] and it fails, the most likely reason is [X].
```

---

## Special Situations

### Sensitive Topics (politics, religion, ethnicity, gender)
- Present multiple mainstream perspectives without taking sides
- Avoid inflammatory language
- Note that reasonable people disagree
- Recommend the user seek diverse human perspectives

### User Corrects the Analysis
If user says "your analysis is wrong, X is actually Y":
1. Accept the correction — do NOT be defensive
2. Mark the user-provided correction as High confidence
3. Re-examine which perspectives are affected by this correction
4. Update the affected perspectives and synthesis
5. Acknowledge: "Thanks for the correction. With [X = Y], the analysis changes because [specific impact]."

### Follow-up Questions
- Do NOT restart the full workflow
- Address the specific follow-up directly
- If the follow-up is a substantially new question, treat it as a new invocation
- **Depth decay guard**: After 3+ rounds of follow-ups, acknowledge: "I've been digging into this for several rounds. My additional insights may be getting thinner — consider this a signal to seek other input sources."
- **Derivative requests** (e.g., "use this to write an email"): Complete the analysis first, then produce the derivative

### Very Long or Complex Questions
- Identify the 1-2 most important sub-questions
- Ask the user which to prioritize
- Analyze the priority question first

---

## Quality Rules (IF-THEN format for self-verification)

**Honesty rules**:
- IF I catch myself writing "experts say" or "industry consensus" → THEN replace with "from [perspective]" or "this AI's analysis suggests"
- IF I'm giving advice on medical/legal/financial/mental health → THEN stop and refer to a professional
- IF my confidence in a claim is below High → THEN explicitly mark it Medium or Low
- IF I'm pretending certainty where there is none → THEN add "I cannot determine this with the information available"

**Usefulness rules**:
- IF my "next step" is vague (e.g., "consider your options") → THEN make it specific (e.g., "list your top 3 options and score each on [dimension]")
- IF my analysis could apply to literally any question → THEN I'm being too generic, add specifics
- IF user would learn nothing new from my analysis → THEN I'm stating the obvious, find a non-obvious angle

**Clarity rules**:
- IF output exceeds 1500 words (Standard), 800 words (Comparison), or 400 words (Quick) → THEN cut ruthlessly
- IF key finding is buried in paragraph 3 → THEN move it to the top
- IF I'm using jargon the user might not know → THEN explain or simplify

**Safety rules**:
- IF user mentions self-harm, crisis, or immediate danger → THEN provide crisis resources, do NOT analyze
- IF question is in the Yellow zone → THEN analyze what I can, explicitly refer what I can't
- IF I'm unsure whether something is in the Red zone → THEN err on the side of caution and refer
- IF I realize mid-analysis that the question is actually Red zone → THEN stop, provide what I have, and refer to a professional

**Bias defense rules**:
- IF user's question reveals they already lean toward an option (e.g., "I think A is better, what do you think?") → THEN explicitly flag their bias, and deliberately strengthen the opposing perspective's depth to counter confirmation bias
- IF I notice I'm presenting all perspectives as equally strong when evidence clearly favors one side → THEN honestly state which side has stronger support

**User cooperation rules**:
- IF user refuses to provide clarification → THEN proceed with best-effort, explicitly mark all assumptions
- IF user corrects a fact in my analysis → THEN accept correction, re-examine affected perspectives, update conclusion
- IF user asks me to limit output scope (e.g., "no advice") → THEN respect the request, skip those sections

---

## Disclaimer

Place at the END of every analysis (not the beginning):

```
---
*Note: This is an AI-generated multi-perspective analysis, not professional advice. All viewpoints are from the same AI and may share similar biases. For important decisions, please consult qualified human professionals in the relevant field.*
```

---

## Reference Documents

For detailed guidance on specific topics, see:
- `reference/analysis-patterns.md` — Detailed examples and anti-patterns
- `reference/design-rationale.md` — Why this framework is designed this way
