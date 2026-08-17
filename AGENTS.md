# Littlebird Skills project guidance

This is the always-on briefing for any coding agent working in this repository. Claude
Code, Cursor, Codex, and Cowork all read this file, directly or through a thin import.

## What this repo is

A Claude plugin marketplace containing skills that build personal writing-voice skills
from a user's own real data. Two data sources, three skills:

- `skills/combined-voice-creator/` - Littlebird MCP mining + Facebook export, fused.
- `skills/facebook-voice-creator/` - Facebook data export only.
- `skills/littlebird-voice-creator/` - Littlebird MCP mining only.

The repo root is simultaneously the plugin (`.claude-plugin/plugin.json`, skills
auto-discovered from `skills/`) and the marketplace (`.claude-plugin/marketplace.json`
listing the plugin with source `./`). Keep both manifests in sync when anything is
added or renamed.

## Operating rules

1. Do not add em dashes or en dashes to authored prose anywhere in this repo. Use
   ordinary punctuation and the spaced hyphen " - " for asides. This repo exists to
   kill AI tells; its own files don't get to have them. Preserve literal data and
   verbatim source material exactly as captured.
2. Protect user work. Never discard unrelated changes, rewrite history, or delete
   broad paths without clear authorization and a verified target.
3. Raw personal data never ships. Facebook exports, Littlebird retrievals, and any
   user corpus are working material only - they get processed in temp space and
   deleted. Only distilled, user-confirmed, user-approved content lands in a skill.
4. Every fact encoded into a voice skill's biography guardrails must be confirmed by
   the user first. Unconfirmed facts do not ship, ever. This includes service history,
   credentials, and life events.
5. Skill frontmatter uses only the Agent Skills spec fields: `name`, `description`,
   `license`, `compatibility`, `metadata`, `allowed-tools`. Anything else fails a
   claude.ai or Cowork upload.

## The three-skill contract

The Facebook guides (`facebook-export-guide.md`, `facebook-data-processing.md`) and the
`voice-skill-template.md` are duplicated between `facebook-voice-creator` and
`combined-voice-creator`; `littlebird-mining-guide.md` is duplicated between
`littlebird-voice-creator` and `combined-voice-creator`. If you edit a shared reference
file, update ALL copies in the same change. The screenshot assets under `assets/` are
likewise shared between `facebook-voice-creator` and `combined-voice-creator`.

Screenshot naming is load-bearing: `fb-export-step-NN-<slug>.png`, referenced by
relative path from each skill's references. Renaming an asset means updating every
guide that references it.

## The method (do not dilute it)

Voice skills built by these skills follow the guide-reference-sample-research method:

1. Real corpus first - export or MCP retrieval, never fabrication.
2. Sanitize to only the user's own words - attribution is guilty until proven theirs.
3. Confirm facts with the user via AskUserQuestion.
4. Analyze quantitatively (counts) and qualitatively (registers).
5. Generate samples, get explicit user approval, iterate.
6. Package as progressive disclosure: lean SKILL.md, deep references, samples split by
   type (long-form / short-form / quick-statements).

The anti-AI-detection ruleset in `voice-skill-template.md` is the core IP of this
method. Changes to it should be deliberate and tested against real detector behavior,
not vibes.

## Validation before commit

- Every SKILL.md parses: valid YAML frontmatter, spec-only fields, description that
  states both what the skill does and when to trigger it.
- Every relative reference path (`references/...`, `../assets/...`) resolves.
- `plugin.json` and `marketplace.json` are valid JSON and agree on names/versions.
- No em/en dashes in authored prose (verbatim corpus material is exempt).
- No raw personal data, exports, or mined content committed anywhere.
