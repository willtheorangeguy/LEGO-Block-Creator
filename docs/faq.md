# FAQ

## Common questions

???+ question "Where did my inventory go? Nothing was saved."

    Nothing is written to disk. `main.py` contains no file operations at all —
    every piece, set, colour, and theme is held in memory and disappears when
    the program exits.

    "Offline" in the project description means it needs no network, not that it
    stores your data locally. There is no database file to find, and no import
    or export.

    See [Architecture](architecture.md#state-and-persistence) for what this
    means when reading the code.

??? question "Why does the program exit after one command?"

    That is how it works. `lego_cmd()` handles a single command and returns —
    it does not loop. The console script calls it once, so each run accepts one
    command and then ends.

    Combined with the answer above, this means a `sortparts-all` in a fresh run
    has nothing to list: the pieces you added in the previous run are gone.

??? question "Do I have to create a colour before adding a piece?"

    Yes. `newpiece` asks for a colour and expects it to exist already — the
    prompt says so:

    ```text
    What is the piece colour (make sure this colour is in the colour database,
    otherwise add using "newcolour")?
    ```

    The same applies to sets: run `newtheme` before `newset`.

??? question "Is it `newcolour` or `newcolor`?"

    Both. Every colour command accepts British and American spellings and they
    behave identically:

    - `newcolour` and `newcolor`
    - `sortparts-colour` and `sortparts-color`

??? question "Is there a Windows `.exe` I can download?"

    No. The releases carry source archives only — no binary assets have been
    published. Install with pip, run the source directly, or use the Docker
    image. All three are covered in [Installation](installation.md).

??? question "Can I use it as a Python library?"

    Not usefully. The only public function is `lego_cmd()`, which takes no
    arguments, returns nothing, and reads from stdin. There is no API for
    adding a piece programmatically — the prompt is the whole interface.

??? question "Which Python version do I need?"

    3.9 or later, declared as `requires-python = ">=3.9"` in `pyproject.toml`.
    The test suite runs against 3.9, 3.10, 3.11, and 3.12 on Ubuntu, Windows,
    and macOS.

## Troubleshooting

### `lego-block-creator: command not found`

**Cause.** The package installed, but the directory pip puts console scripts in
is not on your `PATH`. This is common with `pip install --user`.

**Fix.** Run the script directly from a source checkout, which does not depend
on `PATH` at all:

```bash
git clone https://github.com/willtheorangeguy/LEGO-Block-Creator.git
cd LEGO-Block-Creator
python main.py
```

The console script is the only thing pip puts on `PATH`; there is no
`python -m` form, because the project installs no importable package of its
own.

### The Docker container exits immediately

**Cause.** The image's default command is `bash`, and the program reads from
stdin. Without an interactive terminal, there is nothing to read and the
container stops.

**Fix.** Pass `-i -t` and name the script explicitly:

```bash
docker run -i -t ghcr.io/willtheorangeguy/lego-block-creator:master python main.py
```

### `Sorry, that command was not recognized`

**Cause.** A typo, or a command that does not exist. The sort commands in
particular are hyphenated and easy to get wrong — it is `sortparts-all`, not
`sortparts all` or `sort-parts-all`.

**Fix.** Run `help` to print the full list, or see [Commands](api.md).

### Tests fail with `ModuleNotFoundError: No module named 'main'`

**Cause.** pytest was run from somewhere other than the repository root. The
suite imports `main` directly, which relies on `pythonpath = ["."]` in
`pyproject.toml` resolving against the working directory.

**Fix.** Run pytest from the repository root:

```bash
cd LEGO-Block-Creator
pytest
```

## Getting help

{{ support() }}

When reporting a problem, include:

- The version you are running and how you installed it
- Your operating system and Python version
- The exact command you typed at the `LEGO CMD:` prompt and its complete output
