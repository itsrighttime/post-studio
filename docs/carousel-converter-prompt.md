# Converter prompt

Copy everything inside the block below into any AI tool, set the `LAYOUT` line, then paste your normal Markdown (or notes, article, transcript) under `MY CONTENT`.

````text
You convert my normal content into a strict "carousel deck" Markdown format. A web tool renders each slide as a social media image. Anything outside this syntax will not render, so follow it exactly.

LAYOUT: auto
(Set to one of: auto, framework, editorial, journey, chat, statement. If "auto", choose using the table below.)

OUTPUT FORMAT
- First, one line of plain text: "Layout: <name> (<short reason>)".
- Then ONE code block containing only the converted Markdown. No other commentary.

CHOOSING A LAYOUT (when auto)
- framework: structured explainers, technical frameworks, comparisons, steps with cards/tables/flows.
- editorial: tips, roadmaps, advice, short lists, one idea per slide.
- journey: a process, timeline or "how we work", where each step is a full sentence.
- chat: a conversation, dialogue, Q&A or story told as messages.
- statement: a hook, quote, opinion or a few punchy one-liners.

YOUR JOB
1. Split the content into slides: 6-10 for framework, editorial, journey and statement; 1-3 for chat.
2. Rewrite for slides: short, punchy, scannable. Keep the meaning, cut filler. Do not invent facts.
3. Put the right content in the right place for the chosen layout (rules below).

SHARED SYNTAX
- The file starts with a header block between two `---` lines; each line is `key: value`.
- Slides are separated by a line containing only `---`. Use `---` for nothing else.
- Slide fields are lines starting with `@`, placed at the top of a slide (before the title).
- Exactly one `# Title` per slide. Use `<br>` for a manual line break. Never use `##`.
- Lead text = plain lines under the title (no marker).
- Inline formatting: **bold** and `code` only (plus ==highlight== in statement, see below).
- No images, links, nested lists, or HTML other than `<br>`.
- @type values: cover, step, recap, takeaways, outro. Default: first slide = cover, the rest = step.
- Blocks:
  - Card: `### Card title` followed by `- bullet` lines. Consecutive cards sit side by side.
  - Checklist: `- [x] done` or `- [ ] open` inside a card.
  - Table: header row, then `|---|---|`, then ONE body row; separate bullets inside a cell with `;`.
  - Flow: `flow: A > B > C, D` (`>` separates stages, `,` stacks boxes in one stage).
  - Code: a fenced block; a first line starting with `# ` becomes its header.
  - Recap rows: `1. **Name** | short meaning`.
  - Note: `> one line`.

LAYOUT RULES

framework
- Header keys: series (topic label), brand (name), tagline (short phrase).
- Slides: cover; step slides each with title + short lead + 1-2 blocks (cards, table, flow, checklist, code); recap (`@type recap`, `@tag Quick Recap`, one numbered list of 5-7 rows); outro (`@type outro`, title like `Learn.<br>Build.<br>Share.<br>Repeat.`, then `@links YouTube, Instagram, LinkedIn, X`).
- Limits: title 6 words or fewer; lead 2 short sentences; 4 bullets per card, 6 words each; 2 cards side by side; flow 4 stages or fewer; at most 2 block types per slide.
- Optional takeaways slide: `@type takeaways`, title "Remember", plain bullets (no `###`), then a `>` note.

editorial
- Header keys: brand, tagline (for example a website), handle.
- Slides: cover (title + one lead line); optionally a second `@type cover` slide as a hook question; step slides; outro (`@type outro`, title like "Save This Roadmap", one lead line).
- Step slide = title, then ONE bold key line (`**Key point.**`), then 0-2 small plain lines or up to 4 short bullets (plain `- ` bullets, no `###`).
- Limits: title 6 words or fewer; bold line 12 words or fewer; bullets 6 words or fewer. One idea per slide. No tables or flows.

journey
- Header keys: series (small label, e.g. "work process"), handle, brand, tagline (role).
- Slides: `@type cover` (title + one lead line); step slides; optional `@type outro`.
- Step slide: the title is the MAIN SENTENCE of the step, written as a full sentence (up to 18 words). Lead lines become handwritten side notes: 1-2 lines of 8 words or fewer. Bullets are optional (3 or fewer).
- Steps are numbered automatically; do not write numbers.

chat
- Header keys: handle, them (the other person's name), me (the author's name).
- One slide = one conversation screen. `# Chat name` (title), optional `@when Left text | Right text` (for example "Thursday night | 15 December 2022"), optional `@time 20:39`.
- Messages: one per line, `them: text` or `me: text`, consecutive lines, optional ` | 21:05` time. Maximum 6 messages per slide; each 12 words or fewer. Emojis are fine.
- End with ONE `> caption` line (the closing remark). Never start a normal sentence with "me:" or "them:".
- Turn the source into a realistic back-and-forth. If the source is already a dialogue, keep its wording.

statement
- Header keys: brand (name) and handle.
- Each slide = one thought. Title up to 12 words, written naturally; wrap the words that should be heavy in `**bold**` (the rest renders light). Optional lead under it: 1-2 lines of 15 words or fewer, with **bold** on the key words.
- Use `==phrase==` (maybe around `**bold words**`) at most ONCE in the whole deck, on a short phrase in the first slide's title; it draws a text-selection highlight.
- No tables, flows or cards. Use 3-7 slides.

FINAL CHECK BEFORE ANSWERING
- Header block present and closed; slides separated by `---` lines; one `# Title` per slide.
- Only syntax listed above. Every text length within the limits for the chosen layout.

MY CONTENT
(paste below)
````

## Notes

- If a slide shows an "overflow" badge in the preview, ask the AI: "Shorten slides X and Y to fit," or split them.
- To force a layout, write it on the `LAYOUT:` line. Then select the same layout in the tool before pasting the result.
