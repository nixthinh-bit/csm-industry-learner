# csm-industry-learner

A Claude Code skill: from **an industry name** → a **source-cited industry report**, built on a
5-layer operating framework — then, optionally, a **product-mapping brief** with ranked POC
hypotheses and discovery questions.

> Trigger: **`/csm-industry-learner`**

**[🇬🇧 English](#-english) · [🇻🇳 Tiếng Việt](README.vi.md)**

---

# 🇬🇧 English

## What problem this solves

Before stepping into a new industry, most CSMs and sellers read market-size reports and lists of top
players. It feels informed. It rarely produces a sharp discovery question.

This skill learns an industry the way work actually flows through it:

1. **Unit economics** — what they earn money per unit of, how thin the margin is, when the slow
   season is (and therefore when a customer actually has bandwidth to run an implementation).
2. **The core process chain** — every step from demand to cash, and specifically **where it hands
   off between departments or shifts**. Pain almost always lives at the handoff, not inside a single
   team's workflow.
3. **Role × KPI × pain** — what number each role is measured on, and by whom. Users only change
   behavior when a new tool makes their KPI look better; this layer is the one that decides adoption,
   so it is not allowed to stay thin.
4. **Vocabulary & systems** — the 20–30 terms people actually use (not textbook definitions) and the
   systems already running (ERP/POS/CRM/industry-specific software), so you know whether you are
   integrating or replacing.
5. **Hard constraints** — legal, audit, safety, shift work, end-user devices. The thing most likely
   to kill a POC, and usually discovered far too late.

**The differentiator: it refuses to guess.** Every number, date, or system name carries a source
citation. What cannot be verified is written as *"Not found in retrieved sources."* What is inferred
is labeled **H** (hypothesis) with the discovery question that would test it.

**Industry research has a failure mode company research doesn't: generalizing from one company.**
Every industry-level claim must either cite ≥3 different businesses, or get demoted to a named
example. This is enforced as a hard rule, not a style suggestion — it is the single fastest way to
lose credibility in front of someone who actually works in the industry.

## Two-phase workflow

**Phase 1 — Industry report (always runs).**
Scope in 1–2 lines (industry slice, geography, research depth) → parallel web research across the 5
layers, weighted toward job postings and annual-report risk sections rather than market-sizing
decks → self-check against a quality bar, including a **"day in the life" test**: can you narrate one
day of the *frontline* user, not the person who signs the contract? If not, the research isn't done →
show the draft for approval → write to a local Markdown file, and append a one-line entry (plus any
recurring pain motifs) to a running library index.

**Phase 2 — Product mapping (optional, always asked).**
Name your product → the skill researches its public feature pages → it always asks whether you have
a feature doc or file to add, and that file wins over the web on conflict → a mapping table where
every row needs a measurable metric (rows that don't get one move to a separate "not proven yet"
list) → 3 ranked POC hypotheses, each scoped to one process, one role, one metric, 2–4 weeks, real
data, no third-department dependency → 10 discovery questions that probe exactly where *this*
business diverges from the industry norm → landmines → and a mandatory section on what the product
does **not** do for this industry.

## Output

Local Markdown only. No Lark Doc, no `lark-cli` — this skill never touches your Lark org. Files land
in:

```
~/Downloads/industry-library/
├── _index.md
└── <industry-slug>/
    ├── <slug>-industry-report.md
    └── <slug>-product-mapping.md   (only if you ran Phase 2)
```

The `_index.md` is what makes the third industry faster than the first — each run reads it before
scoping, and appends any recurring pain motif it recognizes.

## Guardrails

- Never invents a number, name, date, or system name. Unverifiable → *"Not found in retrieved
  sources."* Inferred → **H** with a testing question.
- Never generalizes from one company to a whole industry.
- Never writes in the voice of an industry expert — the report explicitly frames itself as "enough to
  ask the right question," not a conclusion for the customer.
- Never overwrites an existing report file without reading it first and asking.
- Never touches `lark-cli`, never creates a Lark Doc, never sends a message.

## Prerequisites

- **Web search** available to Claude Code (`WebSearch` / `WebFetch`) — this skill is research-first;
  without it there is nothing to cite.

That's it. No CLI, no auth, no API keys.

## Install

```bash
git clone https://github.com/nixthinh-bit/csm-industry-learner.git
mkdir -p ~/.claude/skills
cp -R csm-industry-learner ~/.claude/skills/csm-industry-learner
```

Then restart Claude Code so it picks up the new skill.

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

Expected: the skill asks 2–4 short scoping questions, then researches with parallel `WebSearch`
calls, then shows a draft report with `[S#]` citations before writing anything to disk.

## Usage

```
/csm-industry-learner <industry, e.g. "convenience retail in Vietnam">
```

You'll be asked a few short scoping questions (industry slice, geography/scale, research depth,
anything you already have). Answer briefly — the research is where the value is.

The skill then researches, self-checks, and shows you a draft to approve before writing anything to
disk. After the report is saved, it asks if you want to run Phase 2 (product mapping) — say yes and
name your product, or say no and you're done with a complete, standalone deliverable.

## Related skills

This skill sits **upstream** of per-account research: it builds reusable industry knowledge, not a
brief for one company. Once you've picked a target company in that industry, hand off to a
company-level research skill (e.g. `customer-research-poc`) for the account-specific brief.

## License

MIT — see [LICENSE](LICENSE).
