# 🦊 furry

> why write fifty line when one line do trick, and why say it in a paragraph when a *tail wag* do

An agent skill that does three things at once:

1. **Builds lazy** — writes the minimum code that works (YAGNI, reuse, stdlib, one line before fifty), the way [Ponytail](https://github.com/DietrichGebert/ponytail) does.
2. **Talks short** — drops articles, filler, and pleasantries to cut output tokens, the way [caveman](https://github.com/JuliusBrussee/caveman) does.
3. **Sounds like a fur, not a model** — routes the surviving words through SFW furry-community shorthand *and* strips the usual AI tells (em-dash sermons, "delve", "Great question!", rule-of-three padding, sycophantic openers).

Net effect: better engineering, fewer tokens, output that doesn't read like it came out of a model. rawr.

**Version 0.3.0** — see the [Changelog](#changelog).

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

To update later (pulls the latest from `main`), list, or remove:

```bash
npx skills update furry      # update this skill to the latest version
npx skills list              # see what's installed (alias: ls)
npx skills remove furry      # uninstall (alias: rm)
```

## Use

The skill auto-activates from its description, or trigger it explicitly:

```bash
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

## Spicy mode (opt-in, adult humor)

There's an optional **`spicy`** overlay that stacks on any level and recolors a
few dev terms with crude fandom wordplay (`bloat → vore`, `ship it → yiff it`,
`LGTM → murr`, `subagent → bottom`, `untested PR → raw`, and so on).

```bash
/furry spicy      # turn the overlay on
/furry sfw        # back to clean (default)
```

It's deliberately fenced in:

- **Off by default** — only on after you explicitly ask for it.
- **Chat-only** — never written into commits, PRs, code comments, files, or logs. Those stay SFW.
- **Auto-disables** for security warnings, destructive/irreversible confirmations, and multi-step sequences.
- **Crude, not pornographic** — bawdy double-entendre and act-flavored gags are fair game, but no graphic descriptions, no minors, no non-consent, no real people.

The engineering, terseness, and tell-stripping all keep working exactly the same — spicy only changes the flavor words.

## What stays untouched

Code, CLI commands, error strings, API names, and identifiers are **never** furrified — always verbatim. The skill also drops the fur and talks plain for security warnings, destructive confirmations, and multi-step sequences where compression could cause a misread. It never simplifies away validation, error handling, security, or accessibility.

> furry makes the mouth smaller and the diff smaller. it does not make the brain smaller. :3

## Changelog

`npx skills update` always pulls the latest from `main`, so "version" here is just a human-readable marker for what changed.

- **0.3.0** — Dial up the flavor: full mode spreads fur through the whole reply (not one marker then plain), and the only density rule is now "spread flourishes out, never cluster them adjacent" (markers, faces, and spicy hits all stack as long as they're not touching). Spicy actively reaches for innuendo with a calibration example. Tuned after real Opus sessions read too restrained.
- **0.2.0** — Split activation into quiet vs furry mode; full mode now reads furry on every reply; expanded fur vocab (species slang, body nouns, more emoticons); documented spicy mode with its own section; enriched the spicy table (musk, rut, knotted-up, macro/micro, pred/prey); banned em-dashes in output for real.
- **0.1.0** — Initial release: lazy engineering, terse output, furry voice, AI-tell stripping, pup/full/feral intensity, opt-in spicy overlay; MIT-licensed with NOTICE attribution.

## License

MIT. The "build lazy" engineering layer adapts wording from [Ponytail](https://github.com/DietrichGebert/ponytail) (MIT) and the "talk short" layer is inspired by [caveman](https://github.com/JuliusBrussee/caveman) (MIT) — see [`NOTICE`](./NOTICE) for attribution.
