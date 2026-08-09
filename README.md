# csm-industry-learner

A Claude Code skill: from an industry name to a source-cited industry report, built on a 5-layer
operating framework. Optionally it also builds a product-mapping brief with ranked POC hypotheses
and discovery questions.

> Trigger: **`/csm-industry-learner`**

**[🇬🇧 English](#-english) · [🇻🇳 Tiếng Việt](README.vi.md)**

---

# 🇬🇧 English

## What problem this solves

Before stepping into a new industry, most CSMs and sellers read market-size reports and lists of top
players. It feels informed. It rarely produces a sharp discovery question.

This skill learns an industry the way work actually flows through it, in 5 layers.

**Unit economics.** What they earn per unit, how thin the margin is, when the slow season hits and
therefore when a customer actually has bandwidth to run an implementation.

**The core process chain.** Every step from demand to cash, and specifically where it hands off
between departments or shifts. Pain almost always lives at the handoff, not inside a single team's
workflow.

**Role, KPI, pain.** What number each role is measured on and by whom. Users only change behavior
when a new tool makes their KPI look better, so this layer decides adoption and can't stay thin.

**Vocabulary and systems.** The 20 to 30 terms people actually use, not textbook definitions, plus
the systems already running (ERP, POS, CRM, industry-specific software). This tells you whether
you're integrating or replacing.

**Hard constraints.** Legal, audit, safety, shift work, end-user devices. The thing most likely to
kill a POC, usually discovered too late.

The part that matters most: it refuses to guess. Every number, date, or system name carries a
citation. What can't be verified gets written as "Not found in retrieved sources." What's inferred
gets labeled **H** for hypothesis, with the discovery question that would test it.

Industry research has a failure mode that company research doesn't: generalizing from one company.
Every industry-level claim has to cite 3+ different businesses or get demoted to a named example.
That's a hard rule, not a style preference. It's also the fastest way to lose credibility in front of
someone who actually works in the industry.

## Two-phase workflow

**Phase 1, industry report, always runs.** Scope in 1-2 lines (industry slice, geography, research
depth), then parallel web research across the 5 layers, weighted toward job postings and
annual-report risk sections rather than market-sizing decks. Then a self-check against a quality bar,
including a "day in the life" test: can you narrate one day of the frontline user, not the person who
signs the contract? If not, the research isn't done. Show the draft for approval, then write it to a
local Markdown file and append a line to a running library index.

**Phase 2, product mapping, optional but always offered.** Name your product and the skill researches
its public feature pages. It always asks whether you have a feature doc to add, and that file wins
over the web when they conflict. Then a mapping table where every row needs a measurable metric
(rows that don't get one move to a separate "not proven yet" list), 3 ranked POC hypotheses each
scoped to one process, one role, one metric, 2-4 weeks, real data, no third-department dependency, 10
discovery questions that probe exactly where this business diverges from the industry norm, landmines,
and a mandatory section on what the product does not do for this industry.

## Output

Local Markdown only. No Lark Doc, no lark-cli, this skill never touches your Lark org. Files land in:

```
~/Downloads/industry-library/
├── _index.md
└── <industry-slug>/
    ├── <slug>-industry-report.md
    └── <slug>-product-mapping.md   (only if you ran Phase 2)
```

The `_index.md` is what makes the third industry faster than the first. Each run reads it before
scoping and appends any recurring pain motif it recognizes.

## Guardrails

Never invents a number, name, date, or system name. Unverifiable gets written as "Not found in
retrieved sources." Inferred gets labeled H with a testing question.

Never generalizes from one company to a whole industry.

Never writes in the voice of an industry expert. The report frames itself as "enough to ask the right
question," not a conclusion for the customer.

Never overwrites an existing report file without reading it first and asking.

Never touches lark-cli, creates a Lark Doc, or sends a message.

## Prerequisites

Web search available to Claude Code (`WebSearch` / `WebFetch`). This skill is research-first, without
it there's nothing to cite.

That's it. No CLI, no auth, no API keys.

## Install

```bash
git clone https://github.com/nixthinh-bit/csm-industry-learner.git
mkdir -p ~/.claude/skills
cp -R csm-industry-learner ~/.claude/skills/csm-industry-learner
```

Restart Claude Code so it picks up the new skill.

### As part of a plugin

Drop this folder under your plugin's `skills/` directory:

```
your-plugin/
  skills/
    csm-industry-learner/
      SKILL.md
      references/
```

## Verify

In Claude Code:

```
/csm-industry-learner logistics in Vietnam
```

Expected: the skill asks 2-4 short scoping questions, researches with parallel WebSearch calls, then
shows a draft report with `[S#]` citations before writing anything to disk.

## Usage

```
/csm-industry-learner <industry, e.g. "convenience retail in Vietnam">
```

You'll get a few short scoping questions first (industry slice, geography/scale, research depth,
anything you already have). Answer briefly, the research is where the value is.

The skill then researches, self-checks, and shows you a draft to approve before writing anything to
disk. Once the report is saved, it asks if you want Phase 2 (product mapping). Say yes and name your
product, or say no and you're done with a complete, standalone deliverable.

## Related skills

This skill sits upstream of per-account research. It builds reusable industry knowledge, not a brief
for one company. Once you've picked a target company in that industry, hand off to a company-level
research skill (e.g. `customer-research-poc`) for the account-specific brief.

## License

MIT, see [LICENSE](LICENSE).
