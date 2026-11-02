# Set up this second brain

You are setting up an LLM Wiki in this folder, based on this idea file:
https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

Read it first. If you can't open it, say so in one line and carry on with the steps below. They are enough.

## Step 1: ask two questions

Ask these together, then wait for the answers:

1. What do you want this wiki to help you with? One sentence is fine.
2. Are you using your own files or the sample files? (Own files go in `raw/`. The sample files are about Rehanga, a made-up company.)

If they choose the sample files, copy everything from `setup/sample-files/` into `raw/`.
If they choose their own files and `raw/` is empty, ask them to add about 5 files and tell you when they're done.

## Step 2: build the structure

Create:
- the instructions file: `CLAUDE.md` if you are Claude Code, `AGENTS.md` if you are Codex
- `wiki/`
- `wiki/index.md`
- `wiki/log.md`

## Step 3: write these rules into the instructions file

Keep them short. This file is the owner's rulebook, so write it in plain words.

1. Never change anything in `raw/`. Only the wiki changes.
2. Every wiki page starts with the front matter below. Use these five fields, with no others.
3. Every claim links back to the raw file it came from.
4. Update `wiki/index.md` on every change: one line per page, with a one-line summary. `wiki/index.md` and `wiki/log.md` have no front matter.
5. Append one line to `wiki/log.md` for every ingest, query or lint, starting `## [YYYY-MM-DD] ingest |`, `## [YYYY-MM-DD] query |` or `## [YYYY-MM-DD] lint |`.
6. Ingest one file at a time. Finish its pages, the index and the log before starting the next file, even when asked to ingest several.
7. Source pages stay short: under 100 words, saying what the file is and which pages it fed. Facts go on topic, person and decision pages. Never copy tables or long passages from `raw/`.
8. I use this wiki for: [their answer to question 1].

Also add: `setup/` and `START-HERE.md` are not sources. Never ingest them.

Copy this front matter into the instructions file exactly, under the rules:

```yaml
---
title: Page title
type: source          # source, topic, person or decision
sources:              # paths in raw/, one per line
  - raw/file-name.md
updated: YYYY-MM-DD
confidence: medium    # high, medium or low
---
```

## Step 4: stop

Don't ingest anything yet. Show the instructions file, then tell them to go to step 3 in `START-HERE.md`.
