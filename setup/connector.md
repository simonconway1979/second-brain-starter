# Connect a source

Walk them through this one stage at a time. Keep every message short, in plain words. Where a stage says **Stop**, end your message with the question and wait. Where a stage gives a **Button**, ask with your question tool (AskUserQuestion in Claude Code), so they can click. If you have no question tool, ask in plain text. Don't add a recap, a status note or a next-step box.

First read `setup/connector-rules.md`, and follow those rules exactly.

**If they named a source that already has a state file in `raw/.state/`,** read its recipe in `connectors/`, run it using the saved settings and print the one line. If there's anything new, follow `setup/capture.md` to add it to the wiki. Then finish.

**If they named a source that has a recipe but no state file,** go to stage 2. If its tools still aren't connected, say what's missing and stop.

## Stage 1: pick a source

Say: "Which source do you want to connect? If you don't have one ready, pick RSS: it needs no login."

**Buttons:** one for each recipe in `connectors/`, plus "Other"

**Stop.**

If they pick a recipe, go to stage 2.

If they pick "Other", ask: "What do you want to connect?" **Stop.** Then:

1. Check if you already have tools for it. If you do, go to step 4.
2. If you don't, find its MCP and do your best to guide them through connecting it, one step at a time. Say so plainly if you can't find one. Logins happen in the browser. Keys never go in this chat.
3. Write `connectors/<source>.md` in the same shape as the other recipes. Then say: "Restart Claude, then run /connector <source> and we'll carry on from here." **Stop.**
4. Write the recipe if you haven't yet, then go to stage 2.

## Stage 2: check the tool

Read the recipe and do its "Connect" steps. List what the tool can do, and mark which actions you'll use and which you won't touch. Then say: "I'll only use the read actions. OK to collect 5 items?"

**Buttons:** "Yes, collect 5 items" · "Not yet"

**Stop.**

## Stage 3: collect and structure

Collect the 5 newest items and write the files, following the rules and the recipe. Save the state file. Print the one line. Give the full path of one file and say: "Open this one. The seven fields at the top are what every connector writes."

Then say: "Let's test it. A second run should write nothing new."

**Buttons:** "Yes, run the test" · "Not yet"

**Stop.**

## Stage 4: test

Run it again and print the one line. Check the three tests in the rules, and say which passed.

If they passed, follow `setup/capture.md` to add the new files to the wiki. If they didn't, fix the problem first: don't add files that failed.

## Stage 5: what's next

Say: "That's your capture layer. To run it again, type /connector [source]. It brings in anything new and adds it to your wiki. To schedule it, ask me to run that every morning."

End your message with exactly this, with the file name as a link to `.claude/skills/daily-briefing/SKILL.md`:

```
---

ACT

---

Your first agent: [daily-briefing]
```

**Buttons:** "Run daily briefing" · "Not now"

If they pick "Run daily briefing", read `.claude/skills/daily-briefing/SKILL.md` and follow it.
