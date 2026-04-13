# ppt-to-notes

A Claude skill that converts PowerPoint lecture slides (`.ppt` / `.pptx`) into comprehensive, exam-ready study notes — complete with structured Q&A and a quick-revision cheat sheet.

Works on **[claude.ai](https://claude.ai)** (no installs, no CLI, no setup).

---

## What It Does

Upload any lecture PPT and this skill instantly produces:

- **Structured Study Notes** — every definition, bullet, and table extracted verbatim from your slides
- **Q&A Blocks** — exam-style questions auto-generated for every concept, list, and table
- **Quick Revision Cheat Sheet** — key definitions, comparison tables, step-by-step processes, and examples in a compact format

All output uses exact slide wording — no paraphrasing, no hallucination, no outside knowledge added.

---

## How to Use on claude.ai (Recommended)

This is the easiest way — no installation required.

### Step 1 — Download the skill file

Go to the [Releases](../../releases) page of this repo and download **`SKILL.md`** from the latest release.

> Or download it directly: click `SKILL.md` in the file list above → click the **Download raw file** button (⬇ icon, top-right).

---

### Step 2 — Create a Claude Project

1. Open [claude.ai](https://claude.ai) and sign in
2. In the left sidebar, click **"New Project"**
3. Give it a name — e.g. `PPT Notes Generator`

---

### Step 3 — Add the skill as Project Instructions

1. Inside your project, click **"Project instructions"** (or the settings/pencil icon)
2. Open the downloaded `SKILL.md` file in any text editor (Notepad, VS Code, etc.)
3. **Select all** (Ctrl+A) → **Copy** (Ctrl+C)
4. **Paste** the full content into the Project Instructions box
5. Click **Save**

> This tells Claude exactly how to behave whenever you use this project.

---

### Step 4 — Generate notes from your PPT

1. Inside the project, start a **New Chat**
2. **Attach your `.ppt` or `.pptx` file** using the paperclip icon
3. Send the message — Claude will automatically detect the file and start generating

That's it. Claude will output full study notes, Q&A, and a cheat sheet in one go.

---

### What to say (any of these trigger the skill)

| What you send | What Claude does |
|---|---|
| Attach a `.ppt` / `.pptx` file (no message needed) | Auto-generates full notes |
| "generate notes from this" | Generates full notes |
| "make study material" | Generates full notes |
| "exam notes" / "revision notes" | Generates full notes |
| "cheat sheet only" | Generates cheat sheet only |
| "Q&A only" | Generates Q&A section only |
| "skip the cheat sheet" | Generates notes + Q&A only |

---

## Output Format

The skill adapts based on how large your PPT is:

| PPT Size | Strategy | Output |
|---|---|---|
| ≤ 40 slides | Single response | Full notes + Q&A + cheat sheet |
| 41–80 slides | Single response, compact Q&A | Full notes + inline Q&A + cheat sheet |
| 81–120 slides | Two responses | Response 1: notes + Q&A · Response 2: cheat sheet |
| 120+ slides | Three responses | Split across three responses |

At the start of every run, Claude tells you upfront:

```
📊 Detected: 52 slides
📝 Plan: Full notes in one message (~25% session usage)
Generating now...
```

### Sample output structure

```markdown
# Chapter Title

## Section Title

### Study Notes
- **Key Term**: exact definition from slide
- exact bullet point from slide

| Col1 | Col2 |
|---|---|
| data  | data  |

### Q&A

**Q: What is [X]?**
- exact answer point 1
- exact answer point 2

---

## Quick Revision — Exam Cheat Sheet

### Key Definitions
| Term | Definition |
|---|---|
| **term** | one-line exact definition |

### Comparison Tables
| Feature | X | Y |
|---|---|---|
| feature | value | value |
```

---

## Core Rules

These rules are baked into the skill and keep output reliable:

1. **Exact wording** — uses slide text verbatim, never paraphrases
2. **No outside knowledge** — only what's in your slides
3. **Bullet points only** — no prose paragraphs in answers
4. **Bold key terms** on first use
5. **All tables** in markdown format
6. **Generates immediately** — never asks clarifying questions first

---

## Error Handling

| Situation | What Claude says |
|---|---|
| File is not a PPT | "Please attach a .ppt or .pptx file" |
| PPT is image-only (no text) | "This PPT appears to be image-only. I cannot extract text from images." |
| PPT is empty | "This PPT appears to have no content." |

---

## Using with Claude Code (Optional)

If you use the [Claude Code](https://claude.ai/code) CLI or VS Code extension, you can install this as a persistent skill:

```bash
# Clone into your personal Claude skills folder
git clone https://github.com/<your-username>/ppt-to-notes ~/.claude/skills/ppt-to-notes
```

Then invoke it anywhere with `/ppt-to-notes`.

---

## File Structure

```
ppt-to-notes/
├── SKILL.md                  # Skill entrypoint — paste this into Project Instructions
└── references/
    └── format.md             # Output templates (full + compact formats)
```

---

## Requirements

- A free or paid [claude.ai](https://claude.ai) account
- A `.ppt` or `.pptx` file with readable text (not image-only)

---

## License

MIT — free to use, share, and modify.
