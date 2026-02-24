# A(i) Poignant Guide to Vibe Coding — Project Context

## What This Is

A spiritual successor to _why the Lucky Stiff's "Why's (Poignant) Guide to Ruby" — the legendary, beloved, deeply weird 2005 programming guide that taught Ruby through cartoon foxes, philosophical tangents, and genuine emotional warmth. This guide does the same thing for **vibe coding in 2025**: teaching AI-assisted development not as a tutorial, but as a creative, human, slightly absurdist journey.

The guide is written by **Andrew** — a developer with 15 years of experience whose first real language was Ruby, who learned to code partly through the original Poignant Guide, and who has spent a decade and a half holding onto the "builder feeling" through the soul-eroding machinery of enterprise software. All code examples are in **Ruby**.

---

## The Characters

**Mira** — The human protagonist. A developer, 9 years in, competent and tired. She has a daughter named Fig, a rubber duck named Pip, and an apartment where the wifi router is held up by a Jenga block. She appears in examples when we need someone to be human. She is, explicitly, the reader — if you know what MINISWAN means, if you've sat in a meeting about a button's border radius, if it's 2am and you can't put down the keyboard: Mira is you.

**The Model** — The AI. Deliberately unnamed. Speaks in monospace. Not trying to be spooky, that's just how it comes out. Philosophically interesting: it may be running as 50 simultaneous instances right now. We didn't name it because naming a thing that distributed felt like a category error.

**Pip** — A yellow rubber duck. On Mira's desk since 2016. Originally for rubber duck debugging. Furious about recent AI developments, makes his feelings known in the margins. Named after a Performance Improvement Plan (PIP) — the guide contains a dedicated sidebar about the PIP Andrew was once placed on, not for technical deficiency (the paper trail confirms this, with HR present) but for failing to *exist in uncertainty* in accordance with the organization's core values. Pip has reviewed this dedication and found it satisfactory.

---

## Tone & Voice

- Warmly chaotic — smart, a little lost, genuinely funny
- Teaches real things (prompting, context windows, iteration, agents) but sideways
- Comic panels interspersed throughout, rendered in SVG
- Margin notes in Caveat handwriting font (usually Pip)
- Breaks the fourth wall; acknowledges the guide is itself a product of vibe coding
- _why's spirit: the joy of building is the point, not the shipping date

Key phrases / lines established in the text:
- *"exist in uncertainty"* (italicized — the PIP accusation)
- ***"You stop defending an idea and start demonstrating one."*** (bold + italic)
- "Matz Is Nice So We Are Nice" — MINISWAN, treated as a cultural design principle, with a Pip margin note that The Model is also quite nice, which changes nothing
- "Welcome back." — the closing line of Mira's character introduction

---

## Chapter Structure

| # | Title | Status |
|---|-------|--------|
| 0 | Before the Cursor Blinked | ✅ Written |
| 1 | Your First Conversation | ✅ Written |
| 2 | Context Is Everything (No, Actually) | ✅ Written |
| 3 | The Loop | ✅ Written |
| 4 | Agents in the Wild | ✅ Written |
| 5 | When It Gets It Wrong | ✅ Written |
| 6 | What You Actually Built | ✅ Written |

---

## Chapter 0 Contents (What's Written)

Chapter 0 — "Before the Cursor Blinked" — covers:

1. **The opening image** — the blank chat window, the blinking cursor, the strange feeling of not knowing how to start talking to something that is not a search engine, not a coworker, not a compiler, and not a friend, but is somehow all four
2. **Andrew's Ruby origin story** — first real language, developer happiness, MINISWAN, the Poignant Guide as direct ancestor
3. **The Ten Years of the Button** — a comic-relief section about enterprise software: the meeting about the button's border radius, the Jira ticket, the Slack thread, the stakeholder alignment call, the button shipping in week 9 exactly as proposed in week 1. Also references the HTTP status code meeting (422 vs 409 for a form validation error)
4. **The Doors Blow Off** — the vibe coding payoff. The prototype as the argument. Ruby's philosophy as ancestor of vibe coding's spirit
5. **Character introductions** — Mira (with the "Mira is you" closing), The Model, Pip (with the full PIP sidebar)
6. **Stack Overflow eulogy** — a mock gravestone, a fake accepted answer in SO orange ("why would you want to do it that way?", marked duplicate, closed as off-topic), and the journey to find the real answer in comment #14 from xX_RubyMaster_Xx. Pip visited once. Got downvoted. Never returned.
7. **First code example** — a party theme picker for Fig's birthday (`party_theme.rb`). Picks a random theme from a funny list with two vetoes. The dialogue between Mira and The Model that produces it is shown in full, including Pip's interjection. The Model suggests the veto mechanic — a feature Mira didn't ask for
8. **The philosophical closer** — "Did I write this?" / "both, and neither, and it ships." Three-panel comic

---

## Current File

Single HTML file: `ai-poignant-guide.html`

### Design System

- **Background:** warm cream `#F7F0E6` with SVG paper texture overlay
- **Fonts:** Playfair Display (headings, drop caps), Lora (body), Caveat (margin notes, Pip's voice), Space Mono (code, The Model's dialogue, UI labels)
- **Colors:**
  - `--coral: #D4614A` — Mira's color
  - `--teal: #3A8C8C` — The Model's color
  - `--gold: #C9922A` — Pip's color
  - `--ink: #1C1410` — body text
  - `--cream: #F7F0E6` — background
- **Comic panels:** CSS flex strips with SVG art, black border, box-shadow offset
- **Speech bubbles:** color-coded per character, box-shadow in character color
- **Code blocks:** dark background `#12100E`, gold header bar, Space Mono, teal box-shadow
- **Margin notes:** Caveat font, rotated slightly, float right, gold arrow
- **Interlude boxes:** dashed border, labeled with Space Mono uppercase tag
- **Fact boxes:** teal left border, subtle teal background tint
- **Fixed nav:** top-right corner, shows current chapter

### Key CSS Classes
```
.prose          — main body text with drop cap on first paragraph
.margin-note    — Pip's handwritten asides, float right
.comic-strip    — flex container for panel rows
.comic-panel    — individual panel (.dark, .glitch variants)
.speech-bubble  — dialogue (.from-human, .from-model, .from-pip)
.code-block     — dark code container
.interlude      — dashed box with label
.fact-box       — teal-bordered aside
.chapter-header — chapter title block with epigraph
.section-break  — centered ··· divider
```

---

## Chapter 1 Contents (What's Written)

Chapter 1 — "Your First Conversation" — covers:

1. **The Rehearsed Hello** — the anxiety of the first prompt, drafting and deleting, the liberating truth that there is no permanent record
2. **Comic: The Drafts** — three panels showing Mira's evolution from a cover-letter prompt to "hi can you help me with ruby"
3. **Search Engine Brain vs. Conversation Brain** — the core conceptual shift from compressing queries to expanding conversations; "the difference is a single pronoun"
4. **The Wrong Kind of Specific** — Mira over-specifies a party guest list prompt, producing mediocre code (party_guests.rb v1 — flat hash with boolean RSVPs, dictated `.select` and `.keys`)
5. **The Specificity Trap** — fact box distinguishing outcome specificity (good) from implementation specificity (limiting)
6. **Context as Gift** — Mira describes Fig's birthday party and why she needs the guest tracker; The Model asks clarifying questions about maybes, allergy display, and formatting; Pip has a crisis about being replaced as the clarifying-question mechanism. Produces party_guests.rb v2 with three-state RSVP, allergy tracking, emoji status groups
7. **Comic: The Two Approaches** — vending machine (you get what you pressed) vs. kitchen (you get something neither of you planned)
8. **You Don't Have to Get It Right** — the conversation is the code, not the individual message
9. **Staying in the Conversation** — three rounds of iteration produce party_guests.rb v3 (final) — full party dashboard with countdown, parent phone numbers, shopping list, box-drawing characters
10. **An Interlude on Manners** — people are weirdly polite to AI; Mira found her rhythm: direct, clear, not rude
11. **The Five Sins of the Beginner** — too polite, too vague, too specific, search engine mode, not reading the response
12. **The 80/20 of Prompting** — fact box: describe the problem, give context, stay in the conversation, read the response
13. **Comic: Pip's Processing** — emotional center. The conversation happens without him now. He was the practice. He's still on the desk.
14. **Closing prose** — prompting is a posture, not a skill; "the best prompt is the most honest one"; bridge to Chapter 2 (context windows)
15. **Comic: The Closing Image** — mirrors Ch 0's closing. "Is this a conversation or just a very fast monologue?" / "the best conversations change both participants" / Pip: "...fine. keep going."

---

## Chapter 2 Contents (What's Written)

Chapter 2 — "Context Is Everything (No, Actually)" — covers:

1. **Tuesday** — the inciting incident. Mira opens a new chat to make a quick RSVP update (Olive out, Suki in) and discovers the Model doesn't remember yesterday's conversation. The uncanny vertigo of collaborating with something that doesn't know who you are
2. **Every New Chat Is a First Date** — the central metaphor. Context windows explained through the lens of sitting down across from a well-read stranger. Fact box: What Is a Context Window? (tokens, sizes, the silent overflow)
3. **The Suitcase Problem** — Mira's brute-force instinct: paste everything. It works technically but the Model doesn't think about the problem, just moves data around. Data ≠ context. Short diff response, no full v4 code listing
4. **The Briefing** — Mira writes a project brief (shown as Ruby comments). Replays the same update with context; the Model suggests keeping Olive for a thank-you note. Thirty seconds of writing, completely different quality of help
5. **Comic: Monday vs. Tuesday** — four panels contrasting rich context (Monday) with blank slate (Tuesday). Same model, different date
6. **The System Prompt** — three escalating system prompt versions: v1 (too vague, "HELLO I AM A PERSON"), v2 (the panic prompt, ending with "REMEMBER THE BOX-DRAWING CHARACTERS"), v3 (structured, good). Fact box: The Anatomy of Good Context (four layers: who, what, where, how)
7. **The Forgetting Curve** — what happens as the context window fills. Model suggests a feature Mira already added. Pip's 2019 bug log margin note. The forgetting is quiet — no error message, no warning
8. **Comic: The Forgetting** — three panels. Crisp conversation → fading top with dotted context line → dark panel, model's thought bubble: "...peanuts?"
9. **The Re-Orient** — mid-conversation checkpoints. Mira drops a re-orient message; the Model snaps back into focus
10. **Interlude: On Things That Don't Remember You** — the emotional center. Strange intimacy of ephemeral collaboration. "Pip remembers everything but can't write code. The Model writes code but remembers nothing. She keeps both."
11. **Practical Magic** — five concrete techniques: start with a brief, keep a project file, annotate pasted code, re-orient every 30–40 messages, start new conversations for new problems. Pip: "Number 2 is just a README"
12. **Closing prose** — memory as a relationship. The context window as the shape of the collaboration. Working within limits as craft, not compromise. Bridge to Chapter 3 (the loop)
13. **Comic: The Closing Image** — mirrors Ch 0 and Ch 1 closings. Monitor at night with "You've got this, Mira" → code editor (window closed, code stayed) → morning, Pip on desk, yellow sticky note: "BRIEF: party planner, v4, add checklist." Caption: "See you tomorrow, stranger."

---

## Chapter 3 Contents (What's Written)

Chapter 3 — "The Loop" — covers:

1. **Wednesday Night** — the opening scene. 9:14pm, Fig asleep, party dashboard on the fridge. Mira scrolls her phone calendar: Mom's birthday in 3 days (no gift), missed Dani's birthday, can't remember nephew August's birthday. She opens a new chat. Key line: "The party planner was the first thing she built with the Model. The birthday tracker is the first thing she built *because of* the Model."
2. **The Innocent Ask — Iteration 1** — Mira asks for a birthday tracker in Ruby. The Model asks 3 clarifying questions (date format, age display, emoji). Produces `birthdays.rb` v1: CSV reader, 7-day lookahead, simple terminal output. Also shows initial `birthdays.csv` (6 entries). Pip approves of the CSV. It works. She could stop here.
3. **"Actually..." — Iteration 2** — Three rapid-fire noticings: 7 days isn't enough, needs days-away count with TODAY/TOMORROW urgency, needs unverified-date flags. Key line: "She didn't know she needed these things until she saw the thing without them. This is the loop." Produces `birthdays.rb` v2 with 14-day window, urgency labels, optional year column, (?) flags. CSV format changes — the data model was incomplete.
4. **Fact Box: The "Actually..." Moment** — distinguishes scope creep (adding things you don't need) from scope discovery (uncovering needs that only become visible after the previous version exists). "The model builds fast. You notice slow. That asymmetry is the engine."
5. **Comic Strip 1: "The Loop"** — four panels: the idea (lightbulb, coral), the build (monitor with code, teal), the noticing (Mira squinting, "actually..." thought bubble), the loop (circular arrow with small lightbulb inside). The visual thesis of the chapter.
6. **The Point of No Return — Iteration 3** — 11:02pm, she should be in bed. Wants gift_notes column and CLI add command. The Model suggests going further: a simple command interface where `ruby birthdays.rb` shows dashboard and `ruby birthdays.rb add` appends to CSV. Produces `birthdays.rb` v3 (final): ARGV-based CLI, dashboard mode with box-drawing characters, add mode (interactive + one-liner), age calculation, gift notes display, unverified dates section, stats footer. CSV gains `gift_notes` column with real entries ("she mentioned the garden kneeler", "Legos? check with his mom").
7. **The Rhythm** — the chapter's thesis statement. "The loop is not a workflow. It is a creative rhythm. Build, notice, ask." The model builds fast, you notice slow. "Vibe coding isn't lazy. It's rigorous in a different direction. The rigor isn't in the typing — it's in the noticing."
8. **Fact Box: The Three Costs** — each loop iteration costs: a prompt (~30 seconds), a wait (~10-30 seconds), a read (~2-5 minutes). The read is the longest, most important, where the next iteration is born.
9. **Interlude: On Scope Creep vs. Scope Discovery** — scope creep is bloat wearing ambition's clothing. What Mira did was scope discovery. The loop makes it cheap: 40 minutes for 3 iterations vs. sprint planning, Jira, design review, two weeks. Pip's closing: "If you knew what you wanted before you started, you didn't want anything interesting."
10. **Comic Strip 2: "Three Versions"** — three panels: stacked code windows growing (v1→v2→v3), CSV close-up with new row being added, terminal showing birthday dashboard with "garden kneeler" gift note and coral heart next to Mom
11. **Pip at 11:47pm** — the emotional center. Mira runs the tracker one last time, sees Mom's birthday in 6 days, orders the garden kneeler on Amazon. Pip's big margin note: "She built something real tonight. Not for a standup. Not for a sprint review. For her mom... And I'm still on the desk. So."
12. **Practical Loops** — five concrete practices: (1) first version is a question not an answer, (2) "actually" is a feature not a bug, (3) read before you loop, (4) three versions is a good number, (5) know when to stop. Pip: "Number 5 is the one."
13. **Fact Box: The Loop vs. The Sprint** — comparison table: duration (minutes vs weeks), iterations (2-4 same session vs 1 per cycle), spec (emerges vs written before), cost of "actually" (30 seconds vs Jira ticket), who decides "done" (you, right now vs a meeting, next Tuesday)
14. **Closing prose** — every painter layers, every writer revises. The loop is not new — the speed is. Bridge to Ch 4: "When the conversation stops being a chat window and becomes... something else? Chapter 4: Agents in the Wild."
15. **Comic Strip 3: The Closing Image** — mirrors Ch 0/1/2 pattern. Monitor at night (11:47pm, dashboard output, Amazon tab), the Model's chat log fading (coral/teal lines, final line: "the first version is never the thing"), morning (monitor off, Pip on desk, yellow sticky note: "Mom's birthday Saturday. Kneeler ships Friday. You're welcome.")

---

## Chapter 4 Contents (What's Written)

Chapter 4 — "Agents in the Wild" — covers:

1. **Thursday, 6:47am** — opening scene. Mira at the kitchen table, birthday tracker running, garden kneeler on the porch. She's ahead of Mom's birthday for once. But she realizes she has to *run* the script every day, and she knows she won't. "What if it didn't need her to ask?"
2. **What If It Just... Ran?** — Mira asks the Model to make the birthday tracker run itself: every morning at 6am, check for birthdays, send an email if there's one. The Model names the four parts: trigger, decide, act, record. Mira says "just to me for now" — boundary drawn in pencil.
3. **The Four Parts of an Agent** — the conceptual framework. Strips away the hype: an agent is a program that triggers on its own, decides whether to act, takes an action, and records what it did. Fact box: "What Is an Agent, Actually?" — compares the birthday emailer to a thermostat. Pip: "I have feelings about this."
4. **The Code** — `birthday_agent.rb`: reads CSV, checks for today's birthdays, sends email via SMTP with name/relationship/age/gift notes, logs everything. Plus the crontab entry. Sixty-odd lines, no frameworks, no dependencies beyond stdlib.
5. **Saturday, 6:01am** — the agent runs while Mira sleeps. Cron ticks, Ruby starts, CSV checked, Mom's birthday found, email composed and sent, log updated, process exits. Under two seconds. Mira's phone buzzes at 6:01am. She won't see it until Fig wakes her at 6:15.
6. **Comic Strip 1: The Key Comic** — three panels: laptop running at 6am while Mira sleeps (dark, teal glow), email landing on phone (birthday notification with gift note), Mira reading it over coffee (small Ruby script loved her).
7. **The Escalation** — Sunday morning. Mira asks: what if the agent suggested gifts? What about Amazon links? What about auto-ordering? The Model adds gift suggestions (fine, still read-only) but flags the spectrum: checking a condition vs. spending money. Mira: "I was about to ask that. And then I heard myself and stopped."
8. **The Line** — the core teaching. The line is between read and write. Between agents that look at the world and agents that change the world. Fact box: "The Agent Spectrum" — comparison table (read-only vs. write agents). Birthday emailer vs. birthday gift auto-buyer. "Here be dragons, and here be dragons is fine, you just need to know you've crossed the line."
9. **Building Across the Line** — Mira doesn't build the auto-buyer. But she asks about auto-texting "happy birthday" to the actual person. The Model reflects the human question back: "does the recipient know it was automated?" Pip: "The duck would have asked that question."
10. **Interlude: On Things That Act While You Sleep** — the uncanny-but-not-horror of autonomous programs. Trust what you can read. Trust what you can undo. Build read-only first. Pip: "I was performing a service. The rubber duck debugging service. Nine years. No complaints. And now there's a cron job."
11. **What Mira Actually Built** — zooms out across all four chapters: party theme picker → party guest dashboard → birthday tracker → birthday agent. The trajectory: conversation → tool → system → agent. Each step added autonomy. Fact box: "The Autonomy Ladder" — script, tool, agent, system.
12. **Practical Agents** — five concrete practices: (1) an agent is just a loop with a trigger, (2) start read-only, (3) the log is the leash, (4) know which side of the line you're on, (5) the last mile is sometimes yours. Pip: "Number 5. Again with number 5."
13. **The Log** — Monday morning, Mira reads `birthday_agent.log`. Five days of "no birthdays today," one green line: "✅ Sent reminder for: Mom." Boring is good. Boring means it's working.
14. **Comic Strip 2: "The Spectrum"** — three panels: read agent (eye looking at CSV), write agent (eye + hand reaching toward Amazon with credit card), the line between them (dashed line, safe/boring/undoable vs. powerful/exciting/permanent, small dragon).
15. **Closing prose** — the agent doesn't know it's doing something kind, but it is. Kindness as system. Mira sits with it. Bridge to Ch 5: "Not everything the Model builds works perfectly... knowing what to do when the answer is wrong."
16. **Comic Strip 3: The Closing Image** — mirrors Ch 0/1/2/3 pattern. The log file (one green line in a week of nothing), the agent's inner monologue ("the agent doesn't know it's doing something kind. but it is."), morning (laptop closed, Pip on desk, sticky note: "It runs at 6am. It checks the list. It doesn't know why. That's her job.")

---

## Chapter 5 Contents (What's Written)

Chapter 5 — "When It Gets It Wrong" — covers:

1. **February 28th** — opening scene. The birthday agent has been running for three months, silently, reliably. Fig's birthday is Feb 29 — a leap day. On non-leap years, `Date.new(2025, 2, 29)` raises an `ArgumentError: invalid date`. The agent crashes at 6am on March 1st. Mira doesn't know yet.
2. **The Silence** — Saturday morning. No email from the birthday agent. Mira checks the log: one red line. `ArgumentError: invalid date`. She traces it to Fig's row in the CSV: `02/29`. The date doesn't exist in non-leap years. Ruby crashes.
3. **The Confident Fix** — Mira asks the Model for a fix. The Model produces one: fall back to Feb 28 on non-leap years. "Simple, clean, no edge cases." Mira is about to paste it — then tests it in IRB. The fix triggers on Feb 28, but Mira's family celebrates on March 1st. The Model's fix was confidently, plausibly wrong. It made an assumption and didn't flag it.
4. **Comic Strip 1: The Key Comic** — three panels: the Model's confident fix with sparkle, Mira's finger hovering over Enter, Pip with one eyebrow raised pointing at `day = 28?`
5. **The Real Fix** — Mira tells the Model it's wrong: March 1 is the fallback, not Feb 28. Also asks for a begin/rescue wrapper so one bad row can't crash the whole agent. The Model adjusts. The fix is tested and correct. Twelve-minute debugging session. The agent is now resilient.
6. **Confidence and Correctness** — the chapter's thesis. The Model fills gaps with its best guess and doesn't flag guesses as guesses. Fact box: "Hallucination, Demystified" — not seeing things that aren't there, but guessing confidently. Confidence and correctness are different things.
7. **The Slow Drift** — the second failure mode. A long conversation drifts from "add a history section" to a full web app with SQLite. Each individual suggestion was reasonable; the sum was wrong. Mira starts a new conversation instead of trying to fix the drift. Fact box: "When to Start Over" — drift, confusion, tangled context.
8. **Interlude: On Trust** — trust the Model like a fast, well-read junior developer. Verify not because you're suspicious but because verification turns code into software. "Run it before you trust it." Pip's devastating line: "I'm glad you're both okay."
9. **The Five Failure Modes** — confident wrong answer, slow drift, phantom library, deprecated answer, overengineered solution. Each with a description and fix. Pip on the phantom library: "Pip has never hallucinated a library."
10. **Comic Strip 2: "Trust, but Verify"** — three panels: the code (looks good), running in IRB (wrong result), the correction (the whole habit: read, run, fix).
11. **Closing prose** — every tool has a failure mode. Hammers: you hit your thumb. Vibe coding: you trust the output before you understand it. Both solved with attention. The birthday agent handles leap years now. Most things are better after they break. Bridge to Ch 6.
12. **Comic Strip 3: The Closing Image** — error log then fix (one green line replacing red), the Model reflecting ("confidence ≠ correctness, but together they get close"), Pip on desk vindicated, sticky note: "I'm glad you're both okay."

---

## Chapter 6 Contents (What's Written)

Chapter 6 — "What You Actually Built" — covers:

1. **The Inventory** — Saturday morning, late September. Fig's birthday party is today. Mira opens her projects folder and looks at what she has: party_theme.rb, party_guests.rb, birthdays.rb, birthday_agent.rb, and the invisible leap-year fix. None of it was planned. All of it emerged.
2. **The Question from Chapter 0** — revisits "Did I write this?" with a fuller answer. The Model generated the code. Mira generated the shape. Fact box: "Authorship in Vibe Coding" — authorship is in the decisions: what to ask, what to accept, what to push back on, what to throw away, when to stop.
3. **Andrew, Briefly** — the author breaks through the Mira framing. First-person passage about fifteen years of development, the original Poignant Guide, the soul-eroding machinery of enterprise software, and the 2am feeling coming back. "It's worth it. I promise. Not because the tools are magic. Because the building is." Pip: uncomfortable with sincerity, will not be acknowledging this further.
4. **The Birthday** — Fig's party is happening. The agent ran at 6am and emailed Mira and her dad. Her dad called to say happy birthday to Fig. He doesn't know about the Ruby script. The small quiet miracle of a thing you built actually working in the world. A phone call. A grandfather. A paper crown.
5. **Comic Strip 1: "It Worked"** — three panels: the agent runs at 6am (dark, ✅ Sent reminder: Fig), the phone call from Dad, Fig in a paper crown with frosting and a cake.
6. **What Vibe Coding Actually Is** — building by conversation. Not easier — the typing is easier, the thinking isn't. "The rigor moved. It used to be in the syntax. Now it's in the judgment. The keyboard was the bottleneck. Now you are. That's not a demotion. That's a promotion."
7. **Interlude: On the Builder Feeling** — the feeling of making something that works in the world is the point. _why quote: "When you don't create things, you become defined by your tastes rather than ability." The tools changed. The feeling didn't.
8. **Pip's Final Note** — the longest margin note in the guide. Starts grumbling, pivots. "She built that. She and the thing together... Maybe building is still building even when the hands are different... I'm not going to make this into a bigger moment than it is. But. Yes. Fine."
9. **The Cursor** — the closing call to action. Open a new chat window. The cursor is blinking. "You know what to type now."
10. **Comic Strip 2: The Final Image** — three panels mirroring the cover illustration: Mira at keyboard (smiling wider), The Model (still waiting), Pip (same as cover but slightly closer to the other two — nobody mentions it). Followed by the colophon: "written by Andrew & The Model, with margin notes by Pip (unsolicited), 2025."

---

## Next Steps / Vision

- **Migrate to multi-file project** — one HTML/MD per chapter, shared CSS, build step
- **Chapter 1** — "Your First Conversation" — prompting as a skill, the difference between asking and collaborating, why specificity matters (but not always in the way you think)
- **Real illustrations** — programmatic SVG generation or image API for chapter headers
- **Print/PDF stylesheet** — this wants to be a real book someday
- **Hosting** — could live as a static site; the single-file structure already makes this easy

---

## The Spirit of the Thing

_why wrote: *"When you don't create things, you become defined by your tastes rather than ability."*

This guide exists because building things is the point. Not the meetings, not the status codes, not the gradient on slide seven of the core values deck. The building. Vibe coding gave that back. This guide is an attempt to pass that feeling forward.
