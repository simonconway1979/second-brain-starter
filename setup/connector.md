# Connect a source

Walk them through this one stage at a time. Keep every message short, in plain words. Where a stage says **Stop**, end your message with the question and wait. Don't add a recap, a status note or a next-step box.

First read `setup/connector-rules.md`, and follow those rules exactly.

**If they named a source that already has a state file in `raw/.state/`,** read its recipe in `connectors/`, run it using the saved settings, print the one line, and finish.

## Stage 1: pick a source

List the recipes in `connectors/`. Say: "Which source do you want to connect? If you don't have one ready, pick rss: it needs no login."

**Stop.**

If there's no recipe for their source, say you'll build one from the rules, and write `connectors/<source>.md` in the same shape as the others.

## Stage 2: check the tool

Read the recipe and do its "Connect" steps. List what the tool can do, and mark which actions you'll use and which you won't touch. Then say: "I'll only use the read actions. OK to collect 5 items?"

**Stop.**

## Stage 3: collect and structure

Collect the 5 newest items and write the files, following the rules and the recipe. Save the state file. Print the one line. Give the full path of one file and say: "Open this one. The seven fields at the top are what every connector writes."

Then say: "Let's test it. A second run should write nothing new."

**Stop.**

## Stage 4: test

Run it again and print the one line. Check the three tests in the rules, and say which passed.

## Stage 5: what's next

Say: "That's your capture layer. To run it again, type /connector [source]. To schedule it, ask me to run that every morning. Then /capture adds what's new to your wiki. Next, type /build-agent to make your first agent."
