@AGENTS.md

## Claude specifics

The shared project briefing lives in [`AGENTS.md`](AGENTS.md) and is imported above.
Everything in it applies here.

- This repo is both a plugin and a marketplace. Test locally with
  `claude --plugin-dir .` or add the repo as a marketplace source and install
  `littlebird-voice-tools`.
- In Cowork, the three skills trigger on "build my voice skill", "make Claude write
  like me", a Facebook export upload, or Littlebird voice-mining requests. When a user
  has both sources, prefer `combined-voice-creator`.
- Use the AskUserQuestion tool at every decision point the skills specify - export
  options, fact confirmation, sample approval. Recommended answers go first.
- The no-em-dash rule applies to everything you author in this repo, including commit
  messages and docs.
