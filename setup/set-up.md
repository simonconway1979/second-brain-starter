# Set up this second brain

You are walking someone through setting up an LLM Wiki in this folder, based on this idea file:
https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

Read it first. If you can't open it, say so in one line and carry on. The stages below are enough.

Work through one stage at a time. Where a stage says **Stop**, end your message with the question and wait for their reply. Keep every message short, in plain words. Don't add a recap, a status note or a next-step box: this guide is the only next step. If `wiki/` already exists, ask before changing anything.

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

1. Nothing changes an existing file in `raw/`. Connectors may add new ones. Only the wiki changes.
2. Every wiki page starts with the front matter below. Use these five fields, with no others.
3. Every claim links back to the raw file it came from.
4. Update `wiki/index.md` on every change: one line per page, with a one-line summary. `wiki/index.md` and `wiki/log.md` have no front matter.
5. Append one line to `wiki/log.md` for every ingest, query or lint, starting `## [YYYY-MM-DD] ingest |`, `## [YYYY-MM-DD] query |` or `## [YYYY-MM-DD] lint |`. An ingest line names the raw file. A file you can't read gets `## [YYYY-MM-DD] skip |` and the reason.
6. Ingest one file at a time. Finish its pages, the index and the log before starting the next file, even when asked to ingest several.
7. Source pages stay short: under 100 words, saying what the file is and which pages it fed. Facts go on topic, person and decision pages. Never copy tables or long passages from `raw/`.
8. I use this wiki for: [their answer from stage 1].

Also add: only files in `raw/` are sources. Never ingest anything else in this folder.

Add this section as it stands, so connectors can find the folders:

```
## Brain map
sources: raw/
state: raw/.state/
default_scope: personal
```

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

Say, using the real file name: "I've added the wiki rules to your CLAUDE.md file in this folder. Keep these rules so your wiki works correctly. You can add your own instructions to this file at any time. If you have instructions from another project, add them below these rules."

Then say: "We'll ingest these files one at a time, so you can see what happens. Would you like to ingest the first file?" Name the file you'd start with: the shortest one.

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

Say: "While this runs, open your instructions file and add one rule of your own." Then ingest the other files, one at a time.

Then show them what they've built, using the real files and links:
1. A picture: raw files on the left, wiki pages on the right, with a line from each raw file to each page that cites it. Draw it as a visual if you can. If you can't, skip it.
2. The file structure of `raw/` and `wiki/` as a text tree.
3. A short table of how the wiki pages link to each other.

Then say: "Now ask it something you'd normally dig for. Add: answer from the wiki, and name the raw file behind each point."

**Stop.**

## Stage 7: what's next

After their question, say: "That's your memory layer working. Next, type /connector to bring a source in by itself."
