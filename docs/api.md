# Commands

The public interface is the interactive prompt. There are no command-line
flags: you start the program, type one command, answer its prompts, and the
program exits. Run it again for each command.

Every command below is recognised by `lego_cmd()` in `main.py`. Anything else
prints an error telling you to try `help`.


!!! warning "These describe the intended behaviour, not the current behaviour"
    The commands accept their input as documented. None of them store or retrieve
    anything: every sort and search prints a fixed placeholder dictionary, and
    additions are echoed and discarded. See
    [known issues](internal/known-issues.md).

## Pieces

<div class="wt-reference" markdown>

| Command | Prompts for | Description |
|---|---|---|
| `newcolour` / `newcolor` | Colour name | Creates a new colour. Run this before adding a piece in that colour. |
| `newpiece` | Piece name, colour, quantity | Creates a new piece. The colour must already exist. |
| `addpiece` | Piece name, quantity | Adds a quantity of an existing piece. |
| `removepiece` | Piece name, quantity | Removes a quantity of an existing piece. |

</div>

```text
LEGO CMD: newpiece
Name the piece you would like to add: 2x4 Brick
What is the piece colour (make sure this colour is in the colour database, otherwise add using "newcolour")? Bright Red
How many of this piece do you have? 12
```

### Sorting pieces

<div class="wt-reference" markdown>

| Command | Prompts for | Description |
|---|---|---|
| `sortparts-all` | — | Prints every piece with its colour and quantity. |
| `sortparts-name` | Search query | Prints pieces matching the query, with colour and quantity. |
| `sortparts-colour` / `sortparts-color` | Colour | Prints every piece in that colour, with name and quantity. |

</div>

```text
LEGO CMD: sortparts-colour
What colour would you like to sort by? Bright Red
```

## Sets

<div class="wt-reference" markdown>

| Command | Prompts for | Description |
|---|---|---|
| `newtheme` | Theme name | Creates a new theme. Run this before adding a set in that theme. |
| `newset` | Set name, number, theme, piece count, quantity | Creates a new set. |
| `addset` | Set name, quantity | Adds a quantity of an existing set. |
| `removeset` | Set name, quantity | Removes a quantity of an existing set. |

</div>

### Sorting sets

<div class="wt-reference" markdown>

| Command | Prompts for | Description |
|---|---|---|
| `sortsets-all` | — | Prints every set with its number, theme, piece count, and quantity. |
| `sortsets-name` | Search query | Prints sets matching the name. |
| `sortsets-number` | Set number | Prints sets matching the number. |
| `sortsets-theme` | Theme | Prints sets in that theme. |

</div>

```text
LEGO CMD: sortsets-theme
What theme would you like to sort by? City
```

## Utility

<div class="wt-reference" markdown>

| Command | Description |
|---|---|
| `help` | Prints the full command list. |
| `copyright` / `license` | Prints licence and copyright information, and opens the licence in your default text editor. |

</div>

```text
LEGO CMD: help
You have entered the help area! Here is a list of commands for your reference:
newpiece - creates a new piece in the database.
newcolour/newcolor - creates a new colour in the database.
...
```

## Spelling variants

Every colour-related command accepts both British and American spellings, and
they behave identically:

- `newcolour` and `newcolor`
- `sortparts-colour` and `sortparts-color`

## Using it as a library

`main.py` exposes a single function, `lego_cmd()`, which reads one command from
stdin and returns. It takes no arguments and returns nothing, so there is no
useful programmatic interface — the console script installed by pip simply
calls it.

{{ support() }}
