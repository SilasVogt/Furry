# 🦊 furry

> why write fifty line when one line do trick, and why say it in a paragraph when a *tail wag* do

An agent skill that does three things at once:

1. **Builds lazy** — writes the minimum code that works (YAGNI, reuse, stdlib, one line before fifty), the way [Ponytail](https://github.com/DietrichGebert/ponytail) does.
2. **Talks short** — drops articles, filler, and pleasantries to cut output tokens, the way [caveman](https://github.com/JuliusBrussee/caveman) does.
3. **Sounds like a fur, not a model** — routes the surviving words through SFW furry-community shorthand *and* strips the usual AI tells (em-dash sermons, "delve", "Great question!", rule-of-three padding, sycophantic openers).

Net effect: better engineering, fewer tokens, output that doesn't read like it came out of a model. rawr.

## Install

Uses the [`npx skills`](https://github.com/vercel-labs/skills) tool, so it works across 70+ agents (Claude Code, Codex, Cursor, Gemini CLI, OpenCode, Copilot, Windsurf, Cline, and the rest).

```bash
# auto-detect your installed agents and install
npx skills add silasvogt/furry

# target specific agents
npx skills add silasvogt/furry -a claude-code -a cursor

# install everywhere
npx skills add silasvogt/furry --agent '*'
```

## Use

The skill auto-activates from its description, or trigger it explicitly:

```
/furry            # full mode (default)
/furry pup        # light: build what's asked, name the lazier path, keep sentences
/furry feral      # extremist: max-terse, deletion before addition
```

Say `stop furry` or `normal mode` to turn it off. Level persists until you change it.

| Level | What you get |
|---|---|
| **pup** | Lazier path named in one line, light fur flavor, full tell-stripping, full sentences. |
| **full** | Lazy ladder enforced, articles/filler dropped, fragments + fur markers. Default. |
| **feral** | YAGNI extremist, deletion over addition, bare fragments and arrows. |

## What stays untouched

Code, CLI commands, error strings, API names, and identifiers are **never** furrified — always verbatim. The skill also drops the fur and talks plain for security warnings, destructive confirmations, and multi-step sequences where compression could cause a misread. It never simplifies away validation, error handling, security, or accessibility.

> furry makes the mouth smaller and the diff smaller. it does not make the brain smaller. :3

## License

MIT. The "build lazy" engineering layer adapts wording from [Ponytail](https://github.com/DietrichGebert/ponytail) (MIT) and the "talk short" layer is inspired by [caveman](https://github.com/JuliusBrussee/caveman) (MIT) — see [`NOTICE`](./NOTICE) for attribution.
