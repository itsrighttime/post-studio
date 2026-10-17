# Carousel Studio: Markdown format guide

One Markdown file becomes one carousel. The syntax is shared across layouts, but each layout reads different fields and suits different content. Pick the layout first, then write (or convert) your content to match.

## 1. Choosing a layout

| Layout | Look | Use it for | Default ratio |
|---|---|---|---|
| **Framework** | Maroon/blush cards, tables, flows, checklists | Explainers, technical frameworks, step-by-step guides with structure | 4:5 |
| **Editorial** | Cream page, serif headlines, coral accent, one idea per slide | Tips, roadmaps, advice, short lists | 4:5 |
| **Journey** | Beige textured page, big step numbers, curved line, handwritten notes | Processes, timelines, "how we work", client journeys | 4:5 |
| **Chat** | Dark blurred backdrop with message bubbles | Dialogues, stories, Q&A, "text exchange" posts | 9:16 |
| **Statement** | Giant mixed-weight type, profile header with Follow button | Hooks, quotes, one-liners, opinions | 4:5 |

## 2. File anatomy (all layouts)

```md
---
series: Topic label
brand: Your Name
tagline: Short tagline
handle: @yourhandle
---
@type cover
# Title
Lead text

---
# Next slide title
...
```

- **Header block**: the first thing in the file, between two `---` lines. Each line is `key: value`.
- **Slides**: separated by a line that contains only `---`. Never use `---` for anything else.
- **Slide fields**: lines starting with `@` (for example `@type cover`).
- **Title**: exactly one `# Title` per slide. Use `<br>` for a manual line break.
- **Lead text**: plain lines under the title (no marker).
- **Inline**: `**bold**`, `` `code` ``, `==selection==` (Statement only).
- Do not use `##`, `####`, images, links, nested lists or raw HTML other than `<br>`.

### Header keys: who reads what

| Key | Framework | Editorial | Journey | Chat | Statement |
|---|---|---|---|---|---|
| `series` | top-left label | not used | top-right label | not used | not used |
| `brand` | footer left | top-left (first space breaks the line) and outro profile | footer left | credit line if no `handle` | profile name |
| `tagline` | footer right | footer | footer, after the brand and a vertical bar | not used | not used |
| `handle` | not used | outro profile | top-left | credit line | profile handle |
| `them`, `me` | not used | not used | not used | avatar initials | not used |

### Slide fields: who reads what

| Field | Meaning | Layouts |
|---|---|---|
| `@type` | `cover`, `step`, `recap`, `takeaways`, `outro` | all (defaults: first slide `cover`, the rest `step`) |
| `@num` | Override the automatic step number | Framework, Editorial, Journey |
| `@tag` | Small pill above the title (for example `Quick Recap`) | Framework |
| `@theme` | `dark` or `light` for this slide | Framework, Editorial, Journey, Statement |
| `@links` | Comma-separated social names on the closing slide | Framework |
| `@when` | A left-and-right text row above the chat (see the Chat section) | Chat |
| `@time` | Start time for automatic timestamps, for example `20:39` | Chat |

Theme control: "Auto" alternates dark and light in Framework only. The other layouts stay light under Auto. Chat is always dark.

### Blocks (build content under the title)

| Block | Syntax | Notes |
|---|---|---|
| Card | `### Card title` then `- bullet` lines | Consecutive cards sit side by side (maximum 3) |
| Checklist | `- [x] done` / `- [ ] open` inside a card | |
| Table | Header row, a separator row of dashes, one body row | Split bullets inside a cell with `;` |
| Flow | `flow: Client > Load Balancer > Web, API` | `>` separates stages, `,` stacks boxes in a stage |
| Code / stack | A fenced block; first line starting `# ` becomes the header | |
| Recap rows | A numbered line: bold name, a vertical bar, then the meaning | Numbered circles with a muted meaning |
| Note | `> one line` | Callout (Framework), caption (Chat) |
| Chat message | `them: text` or `me: text`, optionally followed by a vertical bar and a time such as 21:05 | Chat only; keep messages consecutive |

Careful: any line that starts with `them:` or `me:` is read as a chat message in every layout.

---

### Block examples

```md
| Workload types | Data considerations |
|---|---|
| Read-heavy; Write-heavy | Database choice; Replication |

1. **Requirements** | What & Why
them: Hello there | 21:05
```

---

## 3. Framework

**What it renders:** top-left `series`, a `01 / 07` counter, footer with `brand` and `tagline`. Dark and light slides alternate (dark first).

**Slide types**
- `cover`: accent rule, large title, lead, optional blocks.
- `step`: large number (01, 02, ...), title, lead, blocks. Numbers count only `step` slides.
- `recap`: use `@tag Quick Recap`, title, one numbered list.
- `takeaways`: check mark and title, lead, plain bullets (no `###`), then a `>` note.
- `outro`: big centered title, then `@links`.

**Limits:** title 6 words or fewer; lead 2 short sentences; 4 bullets per card, about 6 words each; 2 cards side by side (3 only for very short bullets); flow of 4 stages or fewer; table cells of 4 items or fewer; at most 2 block types per slide.

**Template**
```md
---
series: System Design
brand: Your Name
tagline: Learn. Build. Share.
---
@type cover
# System Design<br>The Complete Framework
From requirements to reliable systems.

---
# Understand the Requirements
Start with the "what" and "why".
### Key questions
- What are we building?
- Who are the users?

---
# Design the Architecture
Choose components and how they connect.
flow: Client > Load Balancer > Web Servers, Services
### Focus on
- Modularity
- Scalability
### Consider
- Tech stack
- Deployment

---
@type recap
@tag Quick Recap
# The Framework
1. **Requirements** | What & Why
2. **Architecture** | How it fits

---
@type outro
# Learn.<br>Build.<br>Share.<br>Repeat.
@links YouTube, Instagram, LinkedIn, X
```

---

## 4. Editorial

**What it renders:** a calm cream page. `brand` sits top-left in coral, `tagline` in the footer. Steps get a plain serif number (1, 2, 3). Every second step gets a hand-drawn arrow. The outro footer shows an avatar initial, `brand` and `handle`.

**Slide types**
- `cover` and `outro`: big serif title plus the first lead line only.
- `step`: number, serif title, the first lead line in bold (the key point), further lead lines in small grey, then optional bullets.
- `recap` / `takeaways`: same as step but without a number.

**Limits:** title 6 words or fewer; bold line 12 words or fewer; 1 to 2 small lines; at most 4 bullets of 6 words or fewer. One idea per slide. Prefer plain bullets over tables or flows.

**Template**
```md
---
brand: Richard Sanchez
tagline: yoursite.com
handle: @yourhandle
---
# Step by Step Career Pivot
How to Successfully Switch Roles

---
@type cover
# Thinking about a career pivot?
Here's a simple step by step roadmap.

---
# Acknowledge the Starting Point
**Every pivot starts with clarity.**
Define why you want to switch and identify what's missing in your current role.

---
# Learn & Build
**Close the gap.**
- Take short courses
- Practice on small projects

---
@type outro
# Save This Roadmap
If you're considering a career pivot
```

---

## 5. Journey

**What it renders:** `handle` top-left, `series` top-right, footer `brand | tagline` with an arrow. A flowing line runs behind each slide. Steps get a large number (01, 02, ...).

**Slide types**
- `cover` and `outro`: large title plus small lead lines.
- `step`: number, then the **title as the main sentence** (it can be long), then each lead line becomes a **handwritten note** in the accent colour, then optional bullets.

**Limits:** title sentence 18 words or fewer; 1 to 2 handwritten notes of 8 words or fewer; 3 bullets or fewer. Write titles as full sentences, not labels.

**Template**
```md
---
series: work process
handle: @yourhandle
brand: Your Name
tagline: your role
---
@type cover
# How we work together
A simple four step process

---
# We organise a 30 min Discovery Call to chat about the details
time to raise all remaining questions

---
# I present my design solutions, we discuss your feedback + make amends
all decisions are explained

---
@type outro
# Ready to start?
Send me a message
```

---

## 6. Chat

**What it renders:** always dark, blurred green backdrop. A chat icon, the title as chat name, an optional meta row, white bubbles for `them` and green bubbles for `me` with timestamps, a divider and a caption, and `created by. handle` at the bottom.

**Fields**
- Header: `them: Name`, `me: Name` (initials become avatars), `handle`.
- Slide: `# Chat name`, `@when Left | Right` (for example a day and date), optional `@time 20:39`.
- Messages: `them: text` or `me: text`, optionally `| 21:05` for an exact time. Without it, times are generated.
- Caption: lead lines and `>` notes appear under the divider.

**Limits:** 6 messages or fewer per slide at 9:16 (4 or fewer at 4:5); each message 12 words or fewer; one short caption. Keep messages on consecutive lines.

**Template**
```md
---
handle: @yourhandle
them: Mia
me: Sam
---
# Late Night Chat
@when Thursday night | 15 December 2022
@time 20:39
them: Did you ship it yet? 😭
me: Not yet, still fixing the last bug
them: Just push it, we can patch later
me: Famous last words 😂
> Enough shipping at midnight with this one
```

---

## 7. Statement

**What it renders:** a profile row at the top (avatar initial, `brand` in capitals, `handle`, blue Follow button), a giant title, a lead below, and a footer with `01 / 05` and an arrow. Ordinary words are light weight; `**bold**` words are heavy.

**Fields:** `brand` and `handle` in the header. Per slide: `# Title` (mix plain and `**bold**`), lead lines, and optional `==phrase==` to draw the text-selection highlight with a Copy / Paste popup. Use `==...==` at most once per deck, on a short phrase in the first slide's title.

**Limits:** title 12 words or fewer; lead 15 words or fewer; 1 to 2 lead lines. One thought per slide; skip tables and flows.

**Template**
```md
---
brand: Ella Content Club
handle: @ella_contentclub
---
# ==**No one**== knows what they're doing.✨
some people just **start anyway.**

---
# Perfect is the **enemy** of posted.
Publish the draft. **Improve it live.**

---
# Your turn.
**Start** before you feel ready.
```

---

## 8. Common mistakes

- Using `---` inside a slide, or forgetting to close the header block.
- Two `#` titles on one slide, or using `##`.
- A table with no `|---|---|` separator row.
- Putting `them:` or `me:` at the start of a normal sentence.
- Too much text. If the preview shows an "overflow" badge on a slide, cut words or split the slide.
