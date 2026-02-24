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
| 3 | The Loop | 🔲 Outlined |
| 4 | Agents in the Wild | 🔲 Outlined |
| 5 | When It Gets It Wrong | 🔲 Outlined |
| 6 | What You Actually Built | 🔲 Outlined |

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
