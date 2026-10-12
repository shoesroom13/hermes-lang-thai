# hermes-lang-thai

![Hermes Desktop in Thai](screenshots/desktop-th.png)

Thai (ภาษาไทย) language pack for [Hermes Agent](https://github.com/NousResearch/hermes-agent).

Translates the Hermes UI to Thai across **all three surfaces** — Desktop, core
(CLI / gateway / messaging platforms), and the Ink TUI — **9,720 / 9,726 keys
(99.9%)**. Checked against the English catalogs with `hermes plugins validate`.

## Install

```bash
hermes plugins install shoesroom13/hermes-lang-thai
hermes config set display.language th
```

Restart any running gateway or TUI so they pick up the pack. The Desktop
app picks up the language immediately when you switch it in Settings.

## What is translated

| Surface | Status | Keys |
|---------|--------|------|
| Desktop | Translated | 5,024 / 5,030 |
| Core (CLI / gateway / platforms) | Translated | 3,437 / 3,437 |
| TUI (`hermes --tui`) | Translated | 1,259 / 1,259 |
| **Total** | | **9,720 / 9,726 (99.9%)** |

Core groups: `cli` (1,497), `gateway` (815), `platform` (418 — Telegram, Discord,
Slack, WhatsApp, Matrix, …), `tips` (388), `slash` (119), `display` (132),
`approval` (38), `explainer` (30).

## Known limitations

Six Desktop keys fall back to English because the YAML overlay format only
supports plain text and positional `{0}` placeholders, not arrays or conditionals:

| Key | Type | Impact |
|-----|------|--------|
| `composer.newSessionPlaceholders` | Array | English placeholder suggestions in a new chat |
| `composer.followUpPlaceholders` | Array | English placeholder suggestions in a follow-up |
| `ui.sidebar.toggle` | Conditional function | English "Show/Hide sidebar" tooltip |
| `sidebar.projects.toggle` | Conditional function | English "Show/Hide sessions" label |
| `sidebar.projects.branchOff` | Object-returning function | English "branch off" label in branch picker |
| `intro.custom` | Array-returning function | English fallback intro text (main intro still works) |

These can be resolved by contributing Thai to the bundled catalogs in the
upstream repo (`apps/desktop/src/i18n/th.ts`), which supports the full
TypeScript catalog shape.

## Contributing

Found a typo or want to add a missing key? Open an issue or a pull request.
The `locales/*.yaml` files are flat YAML overlays — edit the Thai value in
place and keep the structure unchanged. Placeholders (`{0}`, `{1}`), CLI flags,
slash commands, env vars, and brand names must be preserved verbatim.

## License

MIT — see [LICENSE](LICENSE).
