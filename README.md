# Stretchtext

A small, model-agnostic instruction set for **short answers with detail on demand**.

Inspired by Ted Nelson's stretchtext idea and the interaction demonstrated by [`pro-vi/cc-stretch`](https://github.com/pro-vi/cc-stretch), but designed for ordinary text conversations. It requires no plugin, dependency, custom syntax, or particular LLM.

## Files

- **[INSTRUCTIONS.md](INSTRUCTIONS.md)** — Canonical instructions for any LLM.
- **[SKILL.md](SKILL.md)** — Optional adapter for agents that support the [Agent Skills format](https://agentskills.io/specification).
- **README.md** — This overview.

## Use with any LLM

Supply the contents of `INSTRUCTIONS.md` as instructions or context. If your assistant can open URLs, you can instead ask it to read that file from this repository.

For a repository published at `mad-ben/stretchtext`, use:

```text
Read and follow https://raw.githubusercontent.com/mad-ben/stretchtext/main/INSTRUCTIONS.md
for this conversation. If you cannot access the file, tell me rather than guessing its contents.
```

**Important:** A link alone is not sufficient for a model without web or repository access. Paste or attach `INSTRUCTIONS.md` in that case. The URL above works only after the repository and file have been published.

## Use as a skill

Place the `stretchtext` directory in a skill location supported by your agent. Its `SKILL.md` is intentionally short and points to `INSTRUCTIONS.md`; both files must remain together. Skill loading is agent-dependent, so direct use of `INSTRUCTIONS.md` is the most portable option.

## Example

**Question:** Why is CI restoring old dependencies?

**Answer:** The cache key ignores lockfile changes. Include the lockfile in the key so dependency updates invalidate stale caches. I can expand on **why this happens** or **how to verify the fix**.

**Follow-up:** Expand how to verify the fix.

**Answer:** Change the lockfile, trigger CI, and confirm that the generated key differs from the previous run. Check that dependencies are reinstalled and a subsequent unchanged run reuses the new cache.

## Scope

This protocol provides **conversational** expansion. It does not create clickable inline stretches or animations; those require support from the chat interface. The initial answer must remain accurate and actionable without expansion.
