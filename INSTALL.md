# Install

## As a personal Claude Code skill

One line, in a terminal or pasted straight into Claude Code:

```bash
mkdir -p ~/.claude/skills && git clone https://github.com/nixthinh-bit/gtm-industry-research.git ~/.claude/skills/gtm-industry-research
```

Then in Claude Code:

```
/gtm-industry-research
```

## As part of a plugin

Drop this folder under your plugin's `skills/` directory:

```
your-plugin/
  skills/
    gtm-industry-research/
      SKILL.md
      references/
```

At runtime the skill resolves `SKILL_DIR` to its own folder
(`${CLAUDE_PLUGIN_ROOT}/skills/gtm-industry-research`), so references are found either way.

## Prerequisites

- **Web search** available to Claude Code (`WebSearch` / `WebFetch`) — this skill is research-first;
  without it there is nothing to cite.

That's the entire dependency list. No CLI, no auth, no API keys — this skill never touches Lark, any
CRM, or any third-party service. Output is a local Markdown file.

## Verify

In Claude Code, run:

```
/gtm-industry-research <any industry you're curious about>
```

Expected: the skill first checks `~/Downloads/industry-library/_index.md` (silently, if it doesn't
exist yet), then asks 2–4 short scoping questions, then researches with parallel `WebSearch` calls
and cites every claim as it goes, then shows you a draft report — with `[S#]` source markers and a
coverage note — before writing anything to disk.

If it writes a fact without a `[S#]` marker, or states an industry-wide claim without naming how many
companies it sampled, that's a bug in the run, not expected behavior — the skill's own guardrails
forbid both.
