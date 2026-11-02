# Set up this second brain

You are walking someone through setting up an LLM Wiki in this folder, based on this idea file:
https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

Read it first. If you can't open it, say so in one line and carry on. The stages below are enough.

Work through one stage at a time. Where a stage says **Stop**, end your message and wait for their reply. Keep every message short, in plain words. If `wiki/` already exists, ask before changing anything.

## Stage 1: the purpose

Ask: "What do you want this second brain to help you with? One sentence is fine."

**Stop.**

## Stage 2: the files

Ask: "Will you use your own files, or the sample files? The sample files are about Rehanga, a made-up company."

**Stop.**

- Sample files: copy everything from `setup/sample-files/` into `raw/`.
- Own files, if `raw/` has fewer than 5 files: say "Please add 5 files to this folder: [the full path of raw/]. Transcripts and your own notes work best. PDFs and images are fine too. Tell me when they're in." **Stop.**

Check what's in `raw/`, and name the files you found.

## Stage 3: the structure

Create `wiki/`, `wiki/index.md`, `wiki/log.md` and the instructions file: `CLAUDE.md` if you are Claude Code, `AGENTS.md` if you are Codex.

Write these rules into the instructions file. It's the owner's rulebook, so keep it short and in plain words.

1. Never change anything in `raw/`. Only the wiki changes.
2. Every wiki page starts with the front matter below. Use these five fields, with no others.
3. Every claim links back to the raw file it came from.
4. Update `wiki/index.md` on every change: one line per page, with a one-line summary. `wiki/index.md` and `wiki/log.md` have no front matter.
5. Append one line to `wiki/log.md` for every ingest, query or lint, starting `## [YYYY-MM-DD] ingest |`, `## [YYYY-MM-DD] query |` or `## [YYYY-MM-DD] lint |`. An ingest line names the raw file. A file you can't read gets `## [YYYY-MM-DD] skip |` and the reason.
6. Ingest one file at a time. Finish its pages, the index and the log before starting the next file, even when asked to ingest several.
7. Source pages stay short: under 100 words, saying what the file is and which pages it fed. Facts go on topic, person and decision pages. Never copy tables or long passages from `raw/`.
8. I use this wiki for: [their answer from stage 1].

Also add: `setup/`, `.claude/`, `README.md`, `LICENSE` and `START-HERE.md` are not sources. Never ingest them.

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

Tell them in one line where the instructions file is, and that it's their rulebook. Then say: "We'll ingest these files one at a time, so you can see what happens. Would you like to ingest the first file?" Name the file you'd start with: the shortest one.

**Stop.**

## Stage 4: the first file

Ingest it. List the pages you wrote, each with its full path.

Then say: "Open one of these pages. Does it say what you'd expect, and do its links go back to your raw file? If not, tell me and I'll fix it. Would you like to ingest the second file?"

**Stop.**

## Stage 5: the second file

Ingest it. List the pages you created and, separately, the existing pages you changed and why.

Then say: "This is the wiki starting to build up: the new file changed pages that were already there. Would you like to ingest the rest?" If no existing page changed, say that instead of the first sentence.

**Stop.**

## Stage 6: the rest

Say: "While this runs, open your rulebook and change one rule so it fits what you want." Then ingest the other files, one at a time.

Then show them what they've built, using the real files and links:
1. A picture: raw files on the left, wiki pages on the right, with a line from each raw file to each page that cites it. Draw it as a visual if you can. If you can't, skip it.
2. The file structure of `raw/` and `wiki/` as a text tree.
3. A short table of how the wiki pages link to each other.

Then say: "Now ask it something you'd normally dig for. Add: answer from the wiki, and name the raw file behind each point."

**Stop.**

## Stage 7: keep it going

After their question, say: "Pick one source that comes in every week, like your meeting notes. Put 10 minutes in your calendar each Friday: add the week's files to raw/, type /capture, and ask me to lint the wiki."
