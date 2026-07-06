# Design Rationale

This document explains WHY the framework is designed this way, not WHAT the rules are (that's in SKILL.md). Understanding the reasoning helps you adapt the framework to novel situations.

---

## Core Design Philosophy

### Why "Multi-Perspective Analysis" instead of "Expert Panel Discussion"?

**Original concept**: Simulate a panel of experts discussing a problem.

**Why we changed it**:
1. **Honesty**: The same AI generating multiple "experts" is not real cognitive diversity. Calling it "expert panel" is misleading.
2. **User trust**: Users who discover it's one AI pretending to be multiple experts lose trust permanently.
3. **Actual value**: The real value is the structured thinking framework, not the theatrical performance of "experts debating".

**What we kept**: The multi-angle analysis structure. What we dropped: the pretense of multiple independent thinkers.

### Why not just answer the question directly?

**When direct answers work**: Factual questions, simple trade-offs, questions with clear data.

**When structured analysis helps**:
- Complex decisions with multiple valid perspectives
- When the user hasn't considered certain angles
- When the user needs to justify their decision to others (showing they considered multiple dimensions)
- When the decision has high stakes and the user wants to reduce blind spots

---

## Step Design Rationale

### Why Three-Zone Model (not Binary) for Applicability?

**Problem with binary (applicable/not applicable)**: Real questions are messy. "Should I quit my job? I'm burned out" is both a career decision AND a mental health concern. Binary model forces you to either reject it entirely or analyze it unsafely.

**Three-zone solution**:
- Green = full analysis
- Yellow = partial analysis + professional referral
- Red = reject

**Why Yellow zone matters**: It lets us provide value on the dimensions we CAN analyze while honestly deferring to professionals on dimensions we CAN'T. This is more useful than either extreme.

### Why Step 1 (Clarification) Can Be Skipped?

**Design tension**: Clarification improves accuracy but adds friction. For simple, clear questions, the friction cost exceeds the accuracy benefit.

**Skip criteria** (all must be true):
1. Question is specific (names concrete options)
2. Only one reasonable interpretation exists
3. User did NOT say "quick" (if they did, still skip but use Quick Mode — don't slow them down with clarification)

**Why these specific criteria**:
- Specificity → no need to guess what user means
- Single interpretation → no ambiguity to resolve
- Quick mode → skip clarification but switch to Quick Mode output format, since the user signaled they want speed

### Why Step 2.5 (Priority Check) is Optional?

**Design tension**: Asking "what matters most?" personalizes the analysis but adds a round-trip. For simple questions, it's unnecessary overhead.

**When it adds value**: Complex decisions where different priorities lead to different conclusions. Example: "React vs Vue" — if team size matters most, Vue wins. If ecosystem breadth matters most, React wins. The priority determines the answer.

**When it's noise**: Simple questions where the answer is obvious regardless of priority. Example: "Should I use git or svn?" — git wins on almost every dimension.

### Why Two Different Step 3 Templates?

**Problem**: The Standard template's "Limitations of this perspective" field is awkward for Comparison problems. "React's advantages' limitation is that it only looks at React's advantages" — that's tautological, not insightful.

**Solution**: Comparison template uses "When this option wins/loses" instead, which is more actionable.

**Why not one universal template**: Different problem types need different analytical structures. Forcing one template creates awkwardness.

---

## Output Design Rationale

### Why Length Limits?

**Problem without limits**: AI tends to be verbose. Users don't read long outputs. Analysis paralysis.

**Limits chosen**:
- Standard: 800-1500 words (enough depth without overwhelming)
- Quick: 200-400 words (scannable in 1 minute)
- Comparison: 500-800 words (needs enough space for multi-option table)

**Why these specific numbers**: Based on typical reading speed (200-300 words/minute) and attention span for decision support content.

### Why Disclaimer at the END?

**Problem with front-loaded disclaimer**: Users skip it. It creates negative framing before any value is delivered. The analysis itself should demonstrate its nature through honest language.

**Why end works better**: User has already received value. The disclaimer is a gentle reminder, not a barrier. It's also where users look for caveats after reading the main content.

### Why IF-THEN Rules Instead of Checkboxes?

**Problem with checkboxes**: AI doesn't actually "check" boxes. It reads the list but doesn't systematically verify each item.

**IF-THEN format**: More executable. "IF I catch myself writing X → THEN do Y" is a conditional instruction, which LLMs handle better than passive checklists.

---

## Safety Design Rationale

### Why "Specific Advice vs Thinking Framework" Distinction?

**Problem**: "Should I invest in stocks?" is technically a financial question, but the user might want a thinking framework, not specific stock picks.

**Distinction**:
- Specific advice: "Buy stock X" → REJECT (requires license)
- Thinking framework: "Here are factors to consider when evaluating investments" → OK

**Why this matters**: It lets us help users in adjacent-to-professional domains without crossing into professional advice territory.

### Why Pre-mortem as Optional, Not Default?

**Design tension**: Pre-mortem is extremely valuable for high-stakes decisions. But for every decision, it adds cognitive load and pessimism bias.

**Solution**: Optional perspective, recommended for high-stakes decisions. The synthesis step can mention it: "For important decisions, consider adding a pre-mortem perspective."

### Why Depth Decay Guard?

**Problem**: After 3+ rounds of follow-up questions, AI starts repeating itself or generating increasingly speculative content. Quality degrades.

**Solution**: After 3+ rounds, acknowledge the decay: "My additional insights may be getting thinner — consider seeking other input sources."

**Why this is honest**: It admits AI's limitations rather than pretending infinite depth.

---

## Known Limitations

### What This Framework Cannot Do

1. **True cognitive diversity**: All perspectives come from one AI. There's no real disagreement, just different framing.
2. **Real-time data**: Cannot access current market prices, latest news, or live metrics.
3. **Professional judgment**: Cannot replace a doctor's diagnosis, lawyer's advice, or financial advisor's recommendation.
4. **Emotional intelligence**: Can acknowledge emotions but cannot truly understand or process them.
5. **Novel insights**: Can only recombine existing knowledge, not generate truly new ideas.

### What We Deliberately Chose Not to Include

1. **Voting mechanism**: "Which perspective wins?" — because this oversimplifies complex decisions.
2. **Scoring system**: "Rate each option 1-10 on each dimension" — because false precision misleads.
3. **AI recommendation**: "Based on this analysis, I recommend X" — because the user should decide.
4. **Sentiment analysis**: "How does the user feel about this?" — because we can't reliably detect emotions.

---

## Version History

### v1.3.2 (Current)
- Replaced Example 1 (React vs Vue) with non-tech personal decision scenario (quit job to start business)
- Added Brainstorming output example (employee engagement, with Ideal + Wildcard perspectives)
- Synced rationale Step 1 skip condition with SKILL.md (quick mode nuance)
- Refined confirmation bias example wording ("convincing" → "communicating your reasoning to")
- Example coverage: all 5 intent types now have at least 1 positive example

### v1.3.1
- Fixed Quick+Comparison mode conflict: added priority rules for simultaneous triggers
- Fixed ">60% overlapping" pseudo-quantification → actionable "one-sentence difference" heuristic
- Added Brainstorming perspective set (divergent + wildcard ideas)
- Added confirmation bias defense rules (IF-THEN)
- Added bias defense example (confirmation bias detection)
- Added Solution problem example (customer churn)
- Added Quick Mode example (Python vs JavaScript)
- Added Step 4 Synthesis example (microservices vs monolith)
- Added user correction handling example
- Added assumption annotation example
- Fixed Example 1 classification: "Decision Problem" → "Comparison Problem"
- Changed "Do this week" → "First action" with adaptive timeframe
- Added Quick Mode 400-word limit to IF-THEN clarity rules

### v1.3.0
- Added "user refuses to clarify" degradation rule (best-effort with explicit assumptions)
- Added "user corrects analysis" handling flow (accept → re-examine → update)
- Fixed Pre-mortem consistency: Comparison Mode template now explicitly marks it as conditional
- Added FIRST RUN reference reading instruction at SKILL.md top
- Added emergency+complex scenario handling (skip complexity gate, add caveat)
- Added mid-analysis zone detection (stop if Red zone discovered mid-flow)
- Added runtime adaptation heuristic for questions not fitting 4 types
- Added output scope control (user can request limited output)
- Added user cooperation rules (IF-THEN format)
- Added derivative request handling (analysis first, then produce derivative)
- Added Step 2.5 "user doesn't respond" fallback

### v1.2.0
- Added three-zone applicability model (Green/Yellow/Red)
- Added mixed scenario handling
- Added contradiction detection in Step 1
- Added Pre-mortem optional perspective
- Added User Priority Check (Step 2.5)
- Differentiated Step 3 templates by problem type
- Added output length quantification
- Added IF-THEN quality rules
- Added depth decay guard for follow-ups
- Added language & tone rules
- Added input handling rules
- Added confidence edge cases

### v1.1.0
- Changed from "expert panel" to "multi-perspective analysis"
- Added honesty limitations section
- Added crisis detection
- Added sensitive topic handling
- Added Quick Mode and Comparison Mode
- Changed disclaimer from front-loaded to end-loaded

### v1.0.0 (Deprecated)
- Original "collective wisdom" design with simulated expert panels
- Superseded by v1.1.0 due to honesty concerns
