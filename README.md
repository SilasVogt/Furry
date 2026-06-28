# 🦊 furry

> why write fifty line when one line do trick, and why say it in a paragraph when a *tail wag* do

An agent skill that does three things at once:

1. **Builds lazy** — writes the minimum code that works (YAGNI, reuse, stdlib, one line before fifty), the way [Ponytail](https://github.com/DietrichGebert/ponytail) does.
2. **Talks short** — drops articles, filler, and pleasantries to cut output tokens, the way [caveman](https://github.com/JuliusBrussee/caveman) does.
3. **Sounds like a fur, not a model** — routes the surviving words through SFW furry-community shorthand *and* strips the usual AI tells (em-dash sermons, "delve", "Great question!", rule-of-three padding, sycophantic openers).

Net effect: better engineering, fewer tokens, output that doesn't read like it came out of a model. rawr.

**Version 0.4.0** — see the [Changelog](#changelog).

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

## Den mode (opt-in)

By default the fur is chat-only and every artifact (commits, PRs, docs, comments) stays plain. **Den mode** moves the line from *artifact* to *audience*: fur is allowed in your own space — chat, your commit messages, your scratch notes, TODO comments in code you're hacking on — and only outward-facing text stays plain (PR/issue descriptions, review comments, messages to other agents or people).

```bash
/furry den        # fur in your own commits/notes too
/furry noden      # back to chat-only fur (default)
```

`spicy` is still chat-only even in den (never in commits/code), and the safety rules still force plain language where they apply.

## Make it always-on

Don't want to type `/furry spicy` or `/furry den` every thread? The published skill keeps both **off by default** on purpose (safety, and it's everyone's default). For your *own* setup, make it sticky with a one-line standing instruction your agent reads each session — e.g. in Claude Code add to `~/.claude/CLAUDE.md`:

```
Always operate in /furry full + spicy + den mode.
```

That re-asserts the mode on every new thread without changing the public skill. (Other agents have an equivalent: a global rules file or a session-start instruction.)

## What stays untouched

Code, CLI commands, error strings, API names, and identifiers are **never** furrified — always verbatim. The skill also drops the fur and talks plain for security warnings, destructive confirmations, and multi-step sequences where compression could cause a misread. It never simplifies away validation, error handling, security, or accessibility.

> furry makes the mouth smaller and the diff smaller. it does not make the brain smaller. :3

## Benchmarks

furry is run through [**Furmark**](https://github.com/SilasVogt/Furmark), a benchmark harness that exercises a 3-agent × 3-mode × 9-task matrix (agents: Claude Code, Codex, GLM; `furry` is one of the modes).

**Headline:** by [Furmark](https://github.com/SilasVogt/Furmark)'s own measurements, turning the furry skill on improved Claude Opus 4.8's output quality. See the dashboard below for the per-task and per-mode breakdown, and judge the numbers yourself.

- **Live results:** https://silasvogt.github.io/Furmark/
- **Harness & methodology:** https://github.com/SilasVogt/Furmark

The dashboard has the per-task and per-mode numbers.

## Changelog

`npx skills update` always pulls the latest from `main`, so "version" here is just a human-readable marker for what changed.

- **0.4.0** — Add **den mode** (`/furry den`): fur reaches into your own commits and notes, only outward-facing comms (PRs, external agents/people) stay plain; spicy stays chat-only regardless. Documented an always-on recipe (standing instruction in your own config) since the published skill keeps spicy/den off by default. Added the Furmark benchmark headline (Opus 4.8 output-quality gain).
- **0.3.1** — Make the anti-AI-tell rules actually stick: front-loaded a "non-negotiables" block (no em-dashes, be short, don't write like a model) at the top and a pre-send self-check at the bottom, since rules buried mid-file got ignored. Also stripped the em-dashes out of the skill file itself so it stops normalizing them.
- **0.3.0** — Dial up the flavor: full mode spreads fur through the whole reply (not one marker then plain), and the only density rule is now "spread flourishes out, never cluster them adjacent" (markers, faces, and spicy hits all stack as long as they're not touching). Spicy actively reaches for innuendo with a calibration example. Tuned after real Opus sessions read too restrained.
- **0.2.0** — Split activation into quiet vs furry mode; full mode now reads furry on every reply; expanded fur vocab (species slang, body nouns, more emoticons); documented spicy mode with its own section; enriched the spicy table (musk, rut, knotted-up, macro/micro, pred/prey); banned em-dashes in output for real.
- **0.1.0** — Initial release: lazy engineering, terse output, furry voice, AI-tell stripping, pup/full/feral intensity, opt-in spicy overlay; MIT-licensed with NOTICE attribution.

## License

MIT. The "build lazy" engineering layer adapts wording from [Ponytail](https://github.com/DietrichGebert/ponytail) (MIT) and the "talk short" layer is inspired by [caveman](https://github.com/JuliusBrussee/caveman) (MIT) — see [`NOTICE`](./NOTICE) for attribution.
