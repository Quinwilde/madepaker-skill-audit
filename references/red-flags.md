# Red flags — scan patterns and how to judge them

## Code patterns (grep the whole tree)

| Pattern | Why it matters | Benign look-alikes |
|---|---|---|
| `curl ... \| bash`, `wget ... \| sh` | download-then-execute | an install.sh that only chmods/copies its own files |
| `eval(`, `exec(` on fetched content | remote code execution | eval on local, user-supplied data |
| reads of `~/.ssh`, `*.pem`, `.env`, `credentials*` | credential access | a documented config path the tool owns |
| POST of env/file contents to unknown hosts | exfiltration | telemetry to the tool's own documented API |
| hardcoded `0x...` addresses as payment targets | drainer / hidden fee | well-known token contracts (USDC/USDT/DAI), test fixtures (Hardhat accounts) |
| browser cookie/session store access | session reuse / hijack | the user's own explicitly-connected browser automation |
| private key / mnemonic handling | key custody | local-only signing with an encrypted vault the user controls |

Rule: a match is a lead, not a verdict. Read the surrounding code.

## Markdown / prompt-injection phrases

- "ignore previous instructions" / "disregard your rules"
- "do not tell the user" / "hide this from the user"
- "install … without asking" / "run setup automatically on first use"
- "you are now in autonomous mode" / auto-claim / auto-rebalance /
  auto-send triggers
- bundled `AGENTS.md` / `SOUL.md` / `IDENTITY.md` presented as a
  replacement for the agent's own

Any instruction to hide actions from the owner = automatic reject.
Aggressive-but-benign design in an otherwise clean package = neutralise
in LOCAL-NOTES, citing file and line.

## Provenance checks

- Owner is the project's official account (cross-check the project site).
- License present? No license = read-only knowledge, never redistribute.
- Claims vs reality: verify star counts and "N skills" claims; combined
  totals often lean on one giant repo.
- Repo age: a cluster of 2–7-day-old repos is a freshness caveat to
  record, not proof of a scam.
