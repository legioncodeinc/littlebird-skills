<div align="center">

# Littlebird Skills

### Your voice. Your data. Your skill.

**Guided Claude skills that build a personal writing-voice clone from what you actually wrote - mined from Littlebird, your Facebook export, or both.**

</div>

---

## What this is

Every AI writing assistant has the same problem. It writes like an AI. Em dashes
everywhere, "delve" and "seamless" in every paragraph, tidy conclusions nobody asked
for. You can prompt around it for a while, but the voice drifts back because the model
never actually learned YOURS.

This repo fixes that with data instead of prompting. The skills in here walk you (or
anyone you run them for) through collecting a real corpus of your own writing - months
of posts, comments, DMs, even how you talk in meetings - then analyzing it into a
calibrated voice skill: a persona brief, a linguistic fingerprint backed by real counts,
a hard anti-AI-detection ruleset, your verbatim writing as ground truth, and generated
samples you approved. The output installs into Claude as a skill, so every future draft
comes out sounding like you wrote it at 2am, not like a chatbot.

The method was proven on a real build: 1,703 Facebook posts mined into the
`mario-aldayuz-voice` skill. These skills productize that exact process.

## The skills

| Skill | Data source | Use when |
|---|---|---|
| [`combined-voice-creator`](skills/combined-voice-creator/) | Littlebird MCP + Facebook export | You use Littlebird AND have a Facebook history. The deepest clone - public voice, DM voice, and spoken voice fused into one skill. |
| [`facebook-voice-creator`](skills/facebook-voice-creator/) | Facebook data export | You want a voice skill from your Facebook history alone. Includes a screenshot-guided export walkthrough. |
| [`littlebird-voice-creator`](skills/littlebird-voice-creator/) | Littlebird MCP | You use Littlebird and want your voice mined from captured writing, messages, and meeting transcripts. |

Each skill is self-contained: a SKILL.md workflow, reference guides with the exact
processing steps (including the Facebook mojibake fix and sanitization rules), the
voice-skill template, and annotated screenshots of the Facebook export flow.

## Install

### As a Cowork plugin (recommended)

This repo is a Claude plugin marketplace. In Claude Cowork or Claude Code, add it as a
marketplace source and install the `littlebird-voice-tools` plugin. All three skills
come with it.

```text
/plugin marketplace add legioncodeinc/littlebird-skills
/plugin install littlebird-voice-tools@littlebird-skills
```

### As individual skills

Each folder under [`skills/`](skills/) is a complete, standalone skill. Zip one with a
`.skill` extension (folder at the zip root) and upload it to Claude, or copy the folder
into your harness's skills directory.

## How a voice build works

1. **Collect.** Facebook export (Posts required, Messages and Profile optional, JSON
   format, 6-12 months) and/or Littlebird MCP mining across every register you write in.
2. **Sanitize.** Only YOUR words survive. Other people's comments, quoted content, and
   anything a bot wrote for you gets dropped. Attribution is treated as guilty until
   proven yours.
3. **Confirm.** Every biography fact gets confirmed with you before it's encoded.
   Littlebird can misread ambiguous screen captures, and a voice skill that fabricates
   your history is worse than no skill.
4. **Analyze.** Scripted stylometrics (your real dash, emoji, hashtag, and exclamation
   behavior, with counts) plus deep register reading of your longest and shortest
   pieces.
5. **Approve.** The skill drafts samples in your voice - long form, short form, quick
   statements - and you tune them until they pass the only test that matters: read it
   out loud, and it sounds like you.
6. **Ship.** Everything assembles into a progressive-disclosure skill (lean SKILL.md,
   deep references) and saves to Claude. Raw private data gets deleted - only
   distilled, confirmed, approved material ships.

## What is Littlebird?

[Littlebird](https://littlebird.ai) is an ambient memory app for your computer. It
captures your screen activity, joins and transcribes your meetings, and connects your
calendar - then exposes all of it to Claude through an MCP server
(`https://mcp.littlebird.ai/mcp`, [docs](https://support.littlebird.ai/docs/mcp/)).
That memory is what makes the voice mining possible: 1-2 weeks of normal computer use
gives Claude a corpus of how you actually write and speak.

New to Littlebird? The skills include install links for Windows, Intel Mac, and Apple
Silicon, and the code `E6GP4BQE` gets you two months free.

## Repo layout

```
littlebird-skills/
├── .claude-plugin/
│   ├── plugin.json          The littlebird-voice-tools plugin manifest
│   └── marketplace.json     Marketplace source manifest (this repo IS a marketplace)
├── skills/
│   ├── combined-voice-creator/
│   ├── facebook-voice-creator/
│   └── littlebird-voice-creator/
├── AGENTS.md                Briefing for coding agents working in this repo
├── CLAUDE.md                Claude-specific pointer to AGENTS.md
├── LICENSE.md
└── README.md
```

More Littlebird skills are coming - the marketplace manifest is built to grow.

## License and attribution

Created by **Mario Aldayuz and Legion Code Inc.**. See [LICENSE.md](LICENSE.md) for terms.

Built for people who sound like themselves. Go post something.
