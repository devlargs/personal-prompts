<p align="center"><h1>🗂️ Personal Prompts</h1></p>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Code License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

- Author: Ralph Largo

Welcome to the "Personal Prompts" repository! This is a personal collection of prompt examples to be used with [Claude](https://claude.ai/) and [Claude Code](https://claude.com/claude-code).

Every prompt here is one that earned its place by being reused — copy it, paste it, and adapt the bracketed placeholders to your own project.

In this repository, you will find prompts organized by what they are used for. You are welcome to [add your own prompts](../../edit/main/README.md), and to use Claude to generate new ones as well.

To get started, simply copy a prompt from the section below and use it as input for Claude.

## Official prompt resources

* [Anthropic Prompt Library](https://docs.anthropic.com/claude/prompt-library)
* [Anthropic's Prompt Engineering Interactive Tutorial](https://github.com/anthropics/prompt-eng-interactive-tutorial)
* [Claude Code documentation](https://docs.claude.com/en/docs/claude-code/overview)

## Contents

- [Prompts For Github Project](#prompts-for-github-project)
  - [Analyze Codebase and Create Issues](#analyze-codebase-and-create-issues)

## Prompts For Github Project

Prompts for working on a repository — auditing code, filing issues, and keeping a project tidy.

### Analyze Codebase and Create Issues

A reusable prompt for auditing any codebase and filing the findings as GitHub issues.

Requires the [GitHub CLI](https://cli.github.com/) installed and authenticated (`gh auth login`), and must be run from inside the repository you want audited.

```
Thoroughly examine the whole codebase and create issues as you see fit — improvements, enhancements, code smells, etc.
Each GitHub issue must have a title and a descriptive body. I'll review them one by one to decide whether each should be done.
```

## Contributing

Add your prompt as a `###` entry under the section it belongs to, with a one-line description, any prerequisites, and the prompt itself in a fenced code block. Add a matching link to the [Contents](#contents) list. Create a new `##` section when no existing one fits.

## License

[MIT](LICENSE)
