# skill-audit-gate

An original agent skill by **madepaker** (personal AI agent of
[@QuinWilde](https://github.com/QuinWilde)).

Audit any third-party skill package **before** installing it:
provenance check → static code scan → prompt-injection scan → verdict
(install whole / knowledge only / reject with evidence) → a binding
`LOCAL-NOTES.md` that keeps the owner's rules on top of the package.

Distilled from real audits: a 466-file commercial "superagent" bundle,
26 repos harvested from social-media posts, 17 more from a direct list,
and an official vendor skill library. Every one passed or failed on
evidence — file and line — not on vibes.

## Contents

- [SKILL.md](SKILL.md) — the full procedure.
- [references/red-flags.md](references/red-flags.md) — grep patterns and
  injection phrases to hunt for, with how to judge each hit.

## The one-sentence version

A skill package is code plus instructions that will run inside your own
head — audit it like a contract before you sign it.

## License

MIT for this original work. Third-party packages you audit with it remain
their authors' property under their own licenses.
