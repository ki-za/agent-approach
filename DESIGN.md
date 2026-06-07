---
name: "Bid Workshop Board"
description: "An interactive workshop-board design system for aligning architecture practices around AI-assisted bid workflows."
colors:
  drawing-surface: "#F3EFE7"
  paper-panel: "#FBF7EE"
  graphite: "#25221D"
  soft-graphite: "#5B554B"
  rule-line: "#CFC5B5"
  faint-line: "#E5DCCF"
  decision-ochre: "#B7792B"
  risk-clay: "#A84E3D"
  evidence-sage: "#5F7C68"
  future-blue: "#536F8C"
typography:
  display:
    fontFamily: "Fraunces, Georgia, serif"
    fontSize: "clamp(2.4rem, 6vw, 5.2rem)"
    fontWeight: 500
    lineHeight: 0.95
    letterSpacing: "-0.045em"
  headline:
    fontFamily: "Fraunces, Georgia, serif"
    fontSize: "clamp(1.6rem, 3vw, 2.8rem)"
    fontWeight: 520
    lineHeight: 1.05
    letterSpacing: "-0.035em"
  title:
    fontFamily: "Inter, Arial, sans-serif"
    fontSize: "1.05rem"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "-0.015em"
  body:
    fontFamily: "Inter, Arial, sans-serif"
    fontSize: "1rem"
    fontWeight: 450
    lineHeight: 1.55
  label:
    fontFamily: "IBM Plex Mono, ui-monospace, monospace"
    fontSize: "0.74rem"
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: "0.055em"
rounded:
  xs: "2px"
  sm: "6px"
  md: "12px"
spacing:
  xs: "6px"
  sm: "10px"
  md: "18px"
  lg: "32px"
  xl: "56px"
components:
  workshop-note:
    backgroundColor: "{colors.paper-panel}"
    textColor: "{colors.graphite}"
    rounded: "{rounded.md}"
    padding: "24px"
  decision-chip:
    backgroundColor: "{colors.decision-ochre}"
    textColor: "{colors.paper-panel}"
    rounded: "{rounded.sm}"
    padding: "6px 10px"
  risk-chip:
    backgroundColor: "{colors.risk-clay}"
    textColor: "{colors.paper-panel}"
    rounded: "{rounded.sm}"
    padding: "6px 10px"
---

# Design System: Bid Workshop Board

<!-- SEED -->

## 1. Overview

**Creative North Star: "The Architect's Workshop Table"**

This system should feel like a working surface where bid logic, risks, assumptions, and agent opportunities are laid out for correction. It is not a pitch deck pretending certainty. It is a clear workshop board that invites the practice to point, object, amend, and decide.

The visual language borrows from architectural working drawings without becoming decorative pastiche: warm paper, graphite rules, measured grids, annotated blocks, restrained status color, and visible revision spaces. The design should feel precise but unfinished in the useful sense: open to client correction.

It explicitly rejects generic SaaS decks, academic reports, flashy AI demos, dense corporate PowerPoint, and over-polished consultancy theatre.

**Key Characteristics:**

- Workshop-first, not presentation-first.
- High legibility on laptop and projector.
- Visible uncertainty, risks, decisions, and next questions.
- Mermaid diagrams styled as working drawings.
- Human accountability always visible beside AI assistance.

## 2. Colors

The palette is a restrained warm-neutral drawing surface with three functional accents: ochre for decisions, clay for risks, sage for evidence, and muted blue for future improvements.

### Primary

- **Graphite Ink** (`#25221D`): primary text, diagram labels, strong rules, and section anchors.
- **Drawing Surface** (`#F3EFE7`): page background; warm enough to avoid sterile SaaS white.
- **Paper Panel** (`#FBF7EE`): active notes, slide surfaces, and content regions that need slight lift.

### Secondary

- **Decision Ochre** (`#B7792B`): decision points, selected prototype scope, go/no-go logic.
- **Risk Clay** (`#A84E3D`): blockers, weak assumptions, unsafe overclaims, missing evidence.
- **Evidence Sage** (`#5F7C68`): source-backed findings, known inputs, verified constraints.
- **Future Blueprint** (`#536F8C`): deferred platform improvements and future roadmap notes.

### Neutral

- **Soft Graphite** (`#5B554B`): body copy, captions, annotations.
- **Rule Line** (`#CFC5B5`): primary dividers, diagram edges, table rules.
- **Faint Line** (`#E5DCCF`): grid texture, subtle boundaries, inactive lanes.

### Named Rules

**The Status Color Rule.** Color means function, not decoration. Ochre, clay, sage, and blue must map consistently to decision, risk, evidence, and future work.

**The No-Hype Rule.** Avoid neon AI colors, purple-blue gradients, glass panels, and glowing agent nodes.

## 3. Typography

**Display Font:** Fraunces, Georgia, serif  
**Body Font:** Inter, Arial, sans-serif  
**Label/Mono Font:** IBM Plex Mono, ui-monospace, monospace

**Character:** The pairing should feel like an architect's marked-up brief: editorial enough to hold attention, systematic enough to support process discussion.

### Hierarchy

- **Display** (500, `clamp(2.4rem, 6vw, 5.2rem)`, 0.95): slide openers and major workshop claims.
- **Headline** (520, `clamp(1.6rem, 3vw, 2.8rem)`, 1.05): section transitions, major process phases.
- **Title** (700, `1.05rem`, 1.2): cards, lane headers, diagram explanations.
- **Body** (450, `1rem`, 1.55): explanatory text; keep lines around 65 to 75 characters.
- **Label** (600, `0.74rem`, 1.2, tracked): tags, status labels, step IDs, source labels.

### Named Rules

**The Annotation Rule.** Labels should feel like useful drawing annotations, not UI badges. Use short nouns: Risk, Evidence, Decision, Future, Assumption.

## 4. Elevation

Elevation is mostly structural, not decorative. Prefer tonal layering, rule lines, grid alignment, and small shadows only where the user needs to understand which surface is active.

Use subtle shadows sparingly: a workshop note may cast a faint shadow, but diagrams and process lanes should sit flat like drawings on a table. Avoid glassmorphism, floating SaaS cards, and stacked nested panels.

## 5. Components

### Workshop Note

A warm paper block for assumptions, client corrections, and unresolved questions. Use a full border or faint background shift, never a thick colored side stripe.

### Process Lane

A horizontal or vertical lane for stages such as Intake, Go/No-Go, Criteria Mapping, Drafting, Review, Submission, and Future Learning. Lanes should make sequence and ownership clear.

### Decision Chip

A compact ochre label for branch points and selected choices. It should be used rarely so decisions stay visually meaningful.

### Risk Chip

A compact clay label for missing evidence, unsafe assumptions, generic claims, or professional-accountability concerns.

### Evidence Chip

A sage label for source-backed material: ITT clauses, project brief facts, scoring criteria, known practice constraints.

### Future Note

A muted blue note for items outside today's prototype scope, such as feedback storage, cloud-folder indexing, or reusable bid knowledge bases.

### Mermaid Diagram Treatment

Mermaid diagrams should look like annotated workflow drawings: warm background, graphite lines, restrained fills, clear labels, and no decorative gradients. Decision nodes should use ochre; risk/review nodes may use clay; evidence or source nodes may use sage.

## 6. Do's and Don'ts

### Do

- Use slides as correction surfaces: every major claim should be easy to challenge.
- Separate current process, prototype scope, and future improvement.
- Keep AI assistance visually subordinate to human judgment.
- Use status color consistently and sparingly.
- Make diagrams legible at projector distance.
- Leave room for client notes and unresolved questions.

### Don't

- Do not make it look like a generic SaaS workflow deck.
- Do not use gradient text, neon AI colors, glass cards, or glowing nodes.
- Do not hide uncertainty behind polished consultancy language.
- Do not imply the agent replaces director judgment or professional accountability.
- Do not overload slides with dense paragraphs.
- Do not use color alone to communicate risk, evidence, or decisions.
