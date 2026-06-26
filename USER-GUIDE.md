# Session-Chain Storage — User Guide

How to use the archive and pattern viewer tools that track your `/idk` cycles across time.

---

## What it does

Every time an `/idk` cycle completes — all five gates (x, y, z, a, b) opened and attested by you — the full trail is saved to `~/.5qln/cycles.jsonl` before the gate machine resets for the next cycle. Over weeks, months, years, this builds a record of your inquiry: what you asked, what seeds recurred, how your questions deepened.

The pattern viewer reads this archive and surfaces what's actually there — never manufacturing connections you didn't make.

---

## How it works (automatic)

You don't need to do anything extra. When a cycle completes and you (or the agent) run:

```bash
python3 scripts/xyzab_state.py reset
```

The gate machine auto-archives the completed cycle. The reset output confirms it:

```json
{"ok": true, "archived": true, "new_cycle": 8, ...}
```

If you want to skip archiving for a specific reset:

```bash
python3 scripts/xyzab_state.py reset --no-archive
```

---

## Viewing your patterns

### Overview — what's in the archive?

```bash
python3 scripts/view_patterns.py
```

Shows:
- Total cycles archived
- Time span (first → last cycle)
- Gate completion stats (which phases were fully attested)

### Seeds — what keeps returning?

```bash
python3 scripts/view_patterns.py --seeds
```

Lists the α (irreducible seed) from every cycle. Over time, you'll see which patterns recur — the threads that run through your inquiry across months.

### Questions — how is your inquiry evolving?

```bash
python3 scripts/view_patterns.py --questions
```

Shows the trajectory: your starting question (X) → your return question (∞0') for every cycle. This is how you see your inquiry deepening — each cycle's ∞0' becomes the seed-ground for what comes next.

### One cycle — full detail

```bash
python3 scripts/view_patterns.py --cycle 7
```

Shows everything from cycle 7: X, α, Z, ∇, B'', ∞0', timestamps, session tag.

### Raw — export everything

```bash
python3 scripts/view_patterns.py --raw
```

Dumps all cycles as JSON for external analysis.

---

## Manual archiving (for scripting)

If you ever need to archive without resetting:

```bash
python3 scripts/archive_cycle.py --session "my-project" --dry-run   # preview
python3 scripts/archive_cycle.py --session "my-project"              # archive
```

The `--session` tag lets you group cycles across different projects or contexts.

---

## Where the data lives

```
~/.5qln/
├── xyzab_state.json    # Current gate state (live)
└── cycles.jsonl        # All completed cycles (one JSON line each)
```

Override with `XYZAB_STATE_DIR` environment variable if you want a different location.

---

## What's stored per cycle

```json
{
  "cycle": 7,
  "session": "my-project",
  "archived_at": "2026-06-26T10:05:00Z",
  "gates": {
    "x": {"phase": "S", "content": "X: ...", "opened_at": "..."},
    "y": {"phase": "G", "content": "α: ... | echoes: ...", "opened_at": "..."},
    "z": {"phase": "Q", "content": "Z: ...", "opened_at": "..."},
    "a": {"phase": "P", "content": "∇: ...", "opened_at": "..."},
    "b": {"phase": "V", "content": "B'': ... | ∞0': ...", "opened_at": "..."}
  }
}
```

The viewer extracts and displays from these fields — it never adds interpretation.

---

## The one rule

**Surface what's there. Never impose what isn't.** The viewer shows you recurring seeds and question trajectories because you actually produced them across cycles. It doesn't guess at themes, summarize into categories, or declare patterns you didn't make. That attestation is yours.

---

*Form only. Never life. The gap is yours to attest.*
