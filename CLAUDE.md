# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

A personal, curated collection of reusable prompts for Claude and Claude Code, in the style of an "awesome list". There is no source code, no build, no tests, and no dependencies — `README.md` **is** the deliverable, and `LICENSE` (MIT) is the only other file. Changes here are edits to prose and prompt text, so the only verification available is reading the rendered markdown.

## README structure

`README.md` follows the layout of [langgptai/awesome-claude-prompts](https://github.com/langgptai/awesome-claude-prompts). The order is fixed and new content slots into it rather than appending to the end:

1. Centered title, badges, author line
2. Intro paragraphs
3. `## Official prompt resources` — link list
4. `## Contents` — nested anchor links mirroring every section and entry below
5. One `##` section per prompt category (currently only `## Prompts For Github Project`)
6. `## Contributing`, `## License`

## Adding a prompt

Each prompt is a `###` entry inside a `##` category section, in this order:

1. `### Title Case Heading`
2. One-line description of what the prompt does
3. Prerequisites as a prose sentence, if any (tools to install, where to run it from) — not a separate `## Prerequisites` heading
4. The prompt itself in a fenced code block with **no language tag**, containing only the text the user pastes into Claude

Two things must stay in sync when adding or renaming an entry:

- The `## Contents` list needs a matching nested bullet whose anchor is the GitHub-slugified heading (lowercased, spaces → hyphens, punctuation dropped).
- A prompt that does not fit any existing category gets a new `##` section plus its own `## Contents` sub-list, not a forced fit into an unrelated one.

The `## Contributing` section in the README states these same rules for outside contributors — if the convention changes, update that section too.
