<p align="center"><h1>🗂️ Personal Prompts</h1></p>

[![Code License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

- Author: Ralph Largo

Welcome to the "Personal Prompts" repository! This is a personal collection of prompt examples to be used with [Claude](https://claude.ai/) and [Claude Code](https://claude.com/claude-code).

Every prompt here is one that earned its place by being reused — copy it, paste it, and adapt the bracketed placeholders to your own project.

In this repository, you will find prompts organized by what they are used for. You are welcome to [add your own prompts](../../edit/main/README.md), and to use Claude to generate new ones as well.

To get started, simply copy a prompt from the section below and use it as input for Claude.

## Official prompt resources

- [Anthropic Prompt Library](https://docs.anthropic.com/claude/prompt-library)
- [Anthropic's Prompt Engineering Interactive Tutorial](https://github.com/anthropics/prompt-eng-interactive-tutorial)
- [Claude Code documentation](https://docs.claude.com/en/docs/claude-code/overview)

## Contents

- [Prompts For Github Project](#prompts-for-github-project)
  - [Analyze Codebase and Create Issues](#analyze-codebase-and-create-issues)
  - [Update Changelog and Set Up Releases](#update-changelog-and-set-up-releases)

## Prompts For Github Project

Prompts for working on a repository — auditing code, filing issues, and keeping a project tidy.

### Analyze Codebase and Create Issues

A reusable prompt for auditing any codebase and filing the findings as GitHub issues.

Requires the [GitHub CLI](https://cli.github.com/) installed and authenticated (`gh auth login`), and must be run from inside the repository you want audited.

```
Thoroughly examine the whole codebase and create issues as you see fit — improvements, enhancements, code smells, etc.
Each GitHub issue must have a title and a descriptive body. I'll review them one by one to decide whether each should be done.
```

### Update Changelog and Set Up Releases

A reusable prompt for writing user-facing `CHANGELOG.md` entries for the current branch and scaffolding a release workflow if one is missing.

Must be run from inside a git repository; creating the release workflow assumes the project is hosted on GitHub.

````
Update CHANGELOG.md to cover the changes in this working tree.

1. Find the file

Look for CHANGELOG.md at the repository root.

If it exists, read it before writing anything and match what is already there — heading style, bullet style, date format, and whether entries are grouped by category. The existing file wins over every formatting rule below. If there is no ## [Unreleased] heading, add one at the top.

If it does not exist, create it with exactly this and nothing more:

```markdown
# Changelog

## [Unreleased]
```

2. Check for project rules

If the repo has a CLAUDE.md, AGENTS.md, CONTRIBUTING.md, or .github/copilot-instructions.md with changelog rules, follow those wherever they conflict with anything here.

3. Work out what changed

Diff the current branch against the base branch. Determine the base branch from the repo rather than assuming — check git symbolic-ref refs/remotes/origin/HEAD or fall back to whichever of main or master exists. If the branch has no commits yet, use the uncommitted changes instead.

4. Write the entries

Add bullets under ## [Unreleased].

Write for the person using the software, not the person reading the diff. Say what changed for them and why it matters — not which files moved or which functions were renamed.
One short bullet per user-visible change.
Group under Added, Changed, Fixed, Removed, or Security only if the file already groups that way, or if this change set genuinely spans several of those. Otherwise keep a flat list.
No commit hashes, no branch names, no file paths, no issue-tracker jargon.

Skip entirely: internal refactors with no visible effect, test-only changes, formatting and lint fixes, dependency bumps that change nothing observable, and edits to docs or tooling config. If you cannot describe a change without naming a file or a function, it does not belong in the changelog.

5. Stay out of releases

Never invent a version number or a release date, and never move bullets out of ## [Unreleased] yourself. Cutting a version is the release workflow's job, not yours.

6. Make sure a release workflow exists

Check for a release workflow under .github/workflows/. If there isn't one, create .github/workflows/release.yml that does the version cut automatically:

Trigger: push to the default branch — main or master, whichever this repo uses — so it runs on every merge. Also expose workflow_dispatch with an optional bump input (a choice of patch, minor, or major, defaulting to patch) for cutting a release by hand.
Guard: on a push, do nothing and exit successfully unless CHANGELOG.md changed in that push and ## [Unreleased] has bullets under it. On a manual run, stop with a clear message if ## [Unreleased] is empty. There is nothing to release either way.
Bump: compute the next semver from the current version — package.json for Node projects, otherwise whichever file this repo already treats as the source of truth. On a push, take the bump level from the changelog entries themselves: major if any bullet is marked breaking, minor if anything was added, patch otherwise. On a manual run, use the bump input. Write the new version back to that file.
Rewrite the changelog: rename the ## [Unreleased] heading to ## [x.y.z] (YYYY-MM-DD) using today's UTC date, and insert a fresh empty ## [Unreleased] above it. Leave every other line untouched.
Commit and tag: commit the version file and CHANGELOG.md together as chore: release v<version>, tag it v<version>, and push both the commit and the tag. Every version bump written into the changelog must get its matching tag in the same run — a released section without a tag is a bug.
Skip if already tagged: if v<version> already exists, do not re-tag or re-release; exit successfully instead, so a re-run or the workflow's own release commit cannot cut the same version twice.
Publish: create a GitHub release for that tag whose body is the bullets from the section just cut.

Run it with git config user.name/user.email set to the Actions bot, permissions: contents: write, and actions/checkout with fetch-depth: 0 so the tag history is available. Guard against the workflow retriggering itself on its own release commit. Tag names must be v<version> — some of my projects have updaters that compare app.getVersion() against the latest release tag.

If a release workflow already exists, leave it alone and just tell me it's there.

7. Show your work

Print the CHANGELOG.md diff, plus any new workflow file, and stop. Do not commit or push unless I ask.
````

## Contributing

Add your prompt as a `###` entry under the section it belongs to, with a one-line description, any prerequisites, and the prompt itself in a fenced code block. Add a matching link to the [Contents](#contents) list. Create a new `##` section when no existing one fits.

## License

[MIT](LICENSE)
