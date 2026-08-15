# Getting started

By the end of this page you will have LEGO Block Creator installed, a piece and
a set in your inventory, and both listed back to you.

## Prerequisites

| Requirement | Minimum version | Check with |
|---|---|---|
| Python | 3.9 | `python --version` |
| pip | any | `pip --version` |

Nothing else. The program has no runtime dependencies.

## Install

```bash
pip install lego-block-creator
```

Docker and source installs are covered in [Installation](installation.md).

## First run

1. Start the program.

    ```bash
    lego-block-creator
    ```

    ```text
    LEGO CMD:
    ```

    The prompt reappears after every command. It handles one command per
    invocation, so run the program again for each step below.

2. Add a colour. Every piece must reference a colour that already exists, so
    this comes first.

    ```text
    LEGO CMD: newcolour
    Name the colour you would like to add: Bright Red
    ```

3. Add a piece, giving the colour you just created.

    ```text
    LEGO CMD: newpiece
    Name the piece you would like to add: 2x4 Brick
    What is the piece colour (make sure this colour is in the colour database, otherwise add using "newcolour")? Bright Red
    How many of this piece do you have? 12
    ```

4. List everything you have entered.

    ```text
    LEGO CMD: sortparts-all
    ```

5. Add a theme, then a set that belongs to it.

    ```text
    LEGO CMD: newtheme
    Name the theme you would like to add: City

    LEGO CMD: newset
    Name the set you would like to add: Fire Station
    ```

6. Ask for help at any time to see every command.

    ```text
    LEGO CMD: help
    ```

## What just happened

Each command prompted you for the values it needed and stored them in memory.
Colours and themes exist so that pieces and sets can be grouped by them, which
is why you create those first.

Because nothing is written to disk, closing the program clears the inventory.
This is a property of the current design, not a misconfiguration — see
[Architecture](architecture.md#state-and-persistence).

## Next steps

- [Commands](api.md) — every command, with the prompts each one asks
- [Installation](installation.md) — Docker and source installs
- [Architecture](architecture.md) — how the CLI is put together

{{ support() }}
