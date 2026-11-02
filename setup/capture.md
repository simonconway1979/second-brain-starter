# Capture new files

`raw/` is the only folder for sources. Files stay there for good, because wiki pages link to them. `wiki/log.md` records which ones are done.

1. If they pasted text, save it word for word as a new file: `raw/notes-YYYY-MM-DD-short-topic.md`. If they gave the path of a file outside `raw/`, copy it into `raw/`. Never summarise at this step.
2. List every file in `raw/`, including subfolders. Ignore hidden files. A file is new if its path isn't in an `ingest` or `skip` line in `wiki/log.md`.
3. If nothing is new, say "Nothing new in raw/. Add files here: [the full path of raw/]" and stop.
4. Say "Captured [number] new files into raw/: [names]. Now adding them to your wiki, one at a time."
5. Ingest each one, following the rules in the instructions file. If you can't read a file, don't guess. Add `## [YYYY-MM-DD] skip | raw/file-name: reason` to the log and carry on.
6. Finish by listing the pages you created, the existing pages you changed, and any files you skipped.
