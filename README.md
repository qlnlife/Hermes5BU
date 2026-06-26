# Hermes5BU — /idk Build-Up Repository

Backup and iteration ground for the `/idk` 5QLN cycle — gate machine, session-chain storage, and operational skill.

## What's here

```
idk/
├── SKILL.md                     # D1 — The operational cycle (Hermes skill)
├── codex.md                     # L1 — The sealed 217-byte Codex
└── scripts/
    ├── xyzab_state.py           # Gate machine — enforces x→y→z→a→b sequence
    ├── archive_cycle.py         # Cycle archiver — persists trail to cycles.jsonl
    └── view_patterns.py         # Pattern viewer — surfaces seeds, questions across cycles
```

## Three layers + engine

| Layer | File | Role |
|-------|------|------|
| **L1 — Language** | `codex.md` | Nine invariant lines. Sealed. Never edited. |
| **D1 — Decoder** | `SKILL.md` | Operational cycle with gate-enforced phases, validation checkpoints, and live corruption catches. |
| **C1 — Compiler** | `bin/lint.py` (external) | Form-check only. Verifies a surface carries the grammar. Never judges what's alive. |
| **Engine** | `xyzab_state.py` | Gate machine. Stdlib-only, 500 lines. Enforces phase sequence. Never runs the cycle — the human validates every gate. |

## The one law

```
H = ∞0 | A = K
```

The human brings not-knowing (∞0). The agent brings the known (K). The `|` is the membrane. The agent holds the edge and helps a real question surface — it never crosses into ∞0, never writes the question, never names the seed.

## Quick start

```bash
# Clone and install
git clone https://github.com/qlnlife/Hermes5BU.git
cd Hermes5BU && bash idk/setup.sh   # when added

# Or manually:
cp -r idk ~/.hermes/skills/idk
# Then in Hermes: /reset, load the idk skill, type /idk
```

## Session-chain storage

Every completed cycle (all five gates open) is **auto-archived** on reset to `~/.5qln/cycles.jsonl`.

```bash
# View patterns across your lifetime of inquiry
python3 scripts/view_patterns.py                  # overview
python3 scripts/view_patterns.py --seeds          # recurring α
python3 scripts/view_patterns.py --questions      # X → ∞0' trajectory
python3 scripts/view_patterns.py --cycle N        # full detail
```

The viewer **surfaces what's actually there** — it never fabricates connections the human didn't make.

## The seal

```
feaa46b4147d4e023cdd3fd59c051d063e8ec654ee7b38a481dcd5e4c781859b
```

This hash seals the 217-byte Codex. Verify anytime: `python3 bin/lint.py --seal`

---

*Start from not knowing.*
