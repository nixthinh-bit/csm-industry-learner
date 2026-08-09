# Install

## As a personal Claude Code skill

```bash
git clone https://github.com/nixthinh-bit/csm-industry-learner.git
mkdir -p ~/.claude/skills
cp -R csm-industry-learner ~/.claude/skills/csm-industry-learner
```

Then in Claude Code:

```
/csm-industry-learner
```

## As part of a plugin

Drop this folder under your plugin's `skills/` directory:

```
your-plugin/
  skills/
    csm-industry-learner/
      SKILL.md
      references/
```

At runtime the skill resolves `SKILL_DIR` to its own folder
(`${CLAUDE_PLUGIN_ROOT}/skills/csm-industry-learner`), so references are found either way.

## Prerequisites

- **Web search** available to Claude Code (`WebSearch` / `WebFetch`) — this skill is research-first;
  without it there is nothing to cite.

That's the entire dependency list. No CLI, no auth, no API keys — this skill never touches Lark, any
CRM, or any third-party service. Output is a local Markdown file.

## Verify

In Claude Code, run:

```
/csm-industry-learner <any industry you're curious about>
```

Expected: the skill first checks `~/Downloads/industry-library/_index.md` (silently, if it doesn't
exist yet), then asks 2–4 short scoping questions, then researches with parallel `WebSearch` calls
and cites every claim as it goes, then shows you a draft report — with `[S#]` source markers and a
coverage note — before writing anything to disk.

If it writes a fact without a `[S#]` marker, or states an industry-wide claim without naming how many
companies it sampled, that's a bug in the run, not expected behavior — the skill's own guardrails
forbid both.
