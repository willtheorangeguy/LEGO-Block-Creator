# LEGO Block Creator

LEGO Block Creator is a command-line tool for cataloguing a LEGO collection. It
presents an interactive prompt for adding pieces and sets and for sorting and
searching them by name, colour, set number, or theme. It runs entirely offline
and needs nothing beyond Python itself.

!!! danger "The commands do not yet store or retrieve anything"
    This is a working command surface over an unimplemented back end. Adding a
    piece echoes back what you typed and stores it nowhere — not on disk, and
    not in memory. Every sort or search command prints the same fixed
    placeholder dictionary regardless of what you enter:

    ```
    {'piecename': 'piecenamescontainingINPUTsearch',
     'piececolour': 'piecescolour', 'piececount': 'numofpieces'}
    ```

    Treat the command list below as the intended interface rather than as
    behaviour you can rely on. See
    [known issues](internal/known-issues.md).

## Key features

- A command surface for pieces — name, colour, and quantity.
- A command surface for sets — name, set number, theme, piece count, quantity.
- Sort and search commands for pieces, by name or colour.
- Sort and search commands for sets, by name, number, or theme.
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
