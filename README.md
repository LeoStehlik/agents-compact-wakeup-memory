# wake-up-memory-dashboard

**Compact startup memory for AI agents.**

This pattern adds a small, high-signal dashboard that an agent reads at session startup before touching the larger memory system.

The goal is simple: start from current operating reality, not from a haze of old context.

---

## Why this exists

As file-based memory systems grow, startup context can become noisy.

If an agent loads too much broad memory too early, it risks:
- over-weighting stale projects
- dragging old context into unrelated work
- spending tokens on archive instead of action
- starting each session with diffuse, low-priority context

A wake-up dashboard fixes that by creating a **first-light layer**: a compact summary of what matters right now.

---

## What the dashboard contains

A good wake-up dashboard usually includes:

1. **Current focus**
   - the 2 to 4 live priorities that define the current operating week

2. **Immediate blockers and waiting-on items**
   - anything that is blocked, externally dependent, or needs a human decision

3. **Critical facts for this week**
   - high-salience operating facts the agent should remember early

4. **Fresh handoff from the last 24 hours**
   - new decisions, resets, and important changes from recent work

5. **What not to preload unless needed**
   - known context that matters, but should stay out of startup unless the task directly touches it

---

## Design rules

A wake-up dashboard should be:
- short enough to read in under a minute
- current rather than comprehensive
- explicit about what is high-salience now
- separate from the full memory index
- maintained continuously, not treated as a static file

It is a startup instrument, not an archive.

---

## Relationship to the broader memory system

The dashboard sits above the normal memory stack.

Typical layering:

```text
wake-up dashboard        startup alignment
MEMORY.md                memory index / routing map
memory topic files       structured long-term memory
recent logs/transcripts  raw source material
```

Use the dashboard first.
Use the rest of memory on demand.

---

## Maintenance pattern

A nightly consolidation loop such as AutoDream can maintain this file by:
- refreshing current focus
- removing stale startup items
- promoting fresh blockers and new operating context
- keeping the dashboard compact and readable

This prevents startup state from drifting away from reality.

---

## Suggested update rules

When updating a wake-up dashboard:
- prefer current reality over completeness
- remove cooled-off priorities quickly
- promote only durable short-term signal
- avoid duplicating entire sections from the full memory index or task tracker
- keep old deep context out unless it is active again

---

## Example sections

```text
1. Current focus
2. Immediate blockers
3. Critical facts for this week
4. Fresh handoff from the last 24 hours
5. Do not preload unless needed
```

---

## Companion patterns

This pattern pairs well with:
- nightly memory consolidation
- skeptical retrieval / recall weighting
- structured topic memory files
- daily logs that are mined into durable memory

---

## License

MIT
