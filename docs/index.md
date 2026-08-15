# LEGO Block Creator

LEGO Block Creator is a command-line tool for cataloguing a LEGO collection. You
add pieces and sets through an interactive prompt, then sort and search them by
name, colour, set number, or theme. It runs entirely offline and needs nothing
beyond Python itself.

!!! warning "The inventory is not saved to disk"
    Everything you enter lives in memory for the duration of the session and is
    lost when the program exits. There is no database file, and no import or
    export. Treat it as a scratchpad rather than a permanent catalogue.

## Key features

- Track individual pieces by name, colour, and quantity.
- Track complete sets by name, set number, theme, piece count, and quantity.
- Sort and search pieces by name or colour.
- Sort and search sets by name, number, or theme.
- British and American spellings accepted for every colour command.
- Runs on Windows, macOS, and Linux; installable from PyPI, Docker, or source.

## Quick start

```bash
pip install lego-block-creator
lego-block-creator
```

Type `help` at the prompt to list every command.

See [Getting started](getting-started.md) for the full walkthrough.

## Where to next

<div class="wt-grid" markdown>

[:material-rocket-launch: **Getting started**<br>Catalogue your first piece in five minutes](getting-started.md){ .wt-card }

[:material-download: **Installation**<br>PyPI, Docker, or from source](installation.md){ .wt-card }

[:material-console: **Commands**<br>Every command, with worked examples](api.md){ .wt-card }

[:material-sitemap: **Architecture**<br>How the CLI is put together](architecture.md){ .wt-card }

[:material-help-circle: **FAQ**<br>Common questions and troubleshooting](faq.md){ .wt-card }

[:material-hand-heart: **Contributing**<br>How to help](https://github.com/willtheorangeguy/.github/blob/main/CONTRIBUTING.md){ .wt-card }

</div>

## Support

More background is on the
[project wiki](https://github.com/willtheorangeguy/LEGO-Block-Creator/wiki).

{{ support() }}
