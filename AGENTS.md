# marketingskills — Agent Instructions

Read this file at the start of every session. It is deliberately thin: it tells
you where the real context lives, not what the context is. Standards, patterns,
and anti-patterns live in the Navigator knowledgebase, not here.

## What This Repo Is

Novatorius's fork of coreyhaines31/marketingskills (MIT) — a collection of
marketing Agent Skills (CRO, copywriting, SEO, analytics, growth engineering)
following the Agent Skills specification, doubling as a Claude Code plugin
marketplace via `.claude-plugin/marketplace.json`. There is no application
code: skills are markdown packages under `skills/`, validated by shell scripts.

- **Initiative:** `novatorius` (declared in `navigator.yaml`)
- **Repository:** `Novatorius/marketingskills` (fork of `coreyhaines31/marketingskills`)

## Before Coding: Load the KB Context

Repo standards live in the Navigator KB, referenced from `knowledgeDependencies`
in `navigator.yaml`. They are not in your training data.

1. If `.claude/kb-context.md` exists, read it.
2. If it doesn't, generate it, then read it:

```bash
navigator kb context
```

## Authoring and Editing Skills

The mechanics of adding or editing a skill — required `SKILL.md` frontmatter,
the `name` rules, the plugin marketplace manifest — are documented in
`CONTRIBUTING.md` and `README.md`. Follow them when touching `skills/`.

## Verification

The `ci` block in `navigator.yaml` is the contract. Run it before and after
every change and leave it green:

```bash
./validate-skills.sh   # ci.test — validates all skills against the Agent Skills spec
```

`.github/workflows/ci.yml` runs the same command on every pull request. What
"done" means is defined in the KB: `global-definition-of-done` (loads via
kb context).

## Session End

Journal early and often, not just at the end — journals are the update feed;
discovery docs (Navigator sources) hold current state. Conventions live in the
KB. Quick path: the `/log` skill, or:

```bash
navigator journal submit "<summary>" "<narrative content>" \
  --initiative=novatorius --tags=marketingskills --json
```
