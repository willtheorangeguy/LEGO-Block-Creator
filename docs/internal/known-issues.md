# Known Issues — LEGO-Block-Creator

Concrete defects and gaps found while writing this repository's documentation in
August 2026. **Nothing here was changed** — each one needs a code, configuration, or
licensing decision rather than a documentation one.

Ordered by severity. See [`docs/roadmap.md`](../roadmap.md) for the narrative version,
which also covers deliberate non-goals.


**2 open:** 1 high, 1 low.

## 1. The CLI stores nothing and every search returns a fixed placeholder dictionary

**Severity:** High  
**Where:** `main.py` -> `lego_cmd`

**What:** There is no data structure holding pieces or sets anywhere in the program -- no file, no database, and no in-memory collection. `newpiece` reads four inputs into module globals and prints a confirmation; nothing is appended to anything. Every sort and search command builds a dictionary of **literal placeholder strings** and prints it. Verified by running it:

    $ printf 'sortparts-name\n2x4 Brick\n' | python main.py
    The following results were found for this search keyword: "2x4 Brick",
     {'piecename': 'piecenamescontainingINPUTsearch',
      'piececolour': 'piecescolour', 'piececount': 'numofpieces'}

That output is identical whatever you enter, and identical whether or not you added anything first.

**Why it matters:** The package is published to PyPI as `lego-block-creator`, ships a Docker image, and carries over 1,500 lines of documentation describing it as offline inventory tracking. What exists is a command surface over an unimplemented back end. The failure is quiet in the worst way: `newpiece` prints 'A new piece has been created named: "2x4 Brick"...', which reads exactly like success, and the search output is a dictionary that looks like a result until you notice the values are the names of the variables that should have produced them. Someone cataloguing a collection could enter a great deal before realising none of it went anywhere.

The documentation was closer than most -- `docs/index.md` warned that nothing is saved to disk -- but it described the state as in-memory-until-exit, which is more generous than the truth, and it listed sorting and searching among the working features.

**Suggested fix:** Owner's decision on scope. The minimum is honest labelling, done in this pass: `index.md` and `api.md` now say the commands are an intended interface rather than working behaviour. Implementing it means a collection held in `lego_cmd`'s scope (or a module-level store), the sort commands filtering it, and -- given the tool's purpose -- somewhere to persist it between runs, since the CLI handles one command per invocation and exits.

## 2. The copyright command names a company that is not the copyright holder

**Severity:** Low  
**Where:** `main.py` -> the `copyright` / `license` command; module header; `LICENSE.md`

**What:** The command prints `Copyright (C) 2018-2023 Dog Face Development Co.` and refers the user to `LICENSE.md`. The module's own header reads `Copyright (C) 2016-2026 @willtheorangeguy`, and `LICENSE.md` is MIT in willtheorangeguy's name. Three different attributions, two different date ranges. The same phantom company appears in `ProgramVer`'s version window, where it is likewise placeholder text.

**Why it matters:** This is the one command whose entire job is stating the copyright accurately, and it states someone else's. It is also the output a user is most likely to quote or screenshot when asking about licensing. The stale end date (2023) compounds it -- a copyright notice that stopped being maintained is a small signal that nobody has looked at this in a while, on the one line where that matters.

**Suggested fix:** Print the same holder and range as the module header and `LICENSE.md`, or better, read the year from `datetime` and the holder from package metadata so the three cannot drift apart again.


---

## Also, across every repository

**`.bandit` is present on disk but untracked in git.** Verified in PyWorkout, treklogger,
skyscanner-cli, booking-cli, piggy, and aibot — the config file exists locally in each but
`git ls-files` does not know about it, so none of it reached GitHub.

The August 2026 security sweep therefore looks complete locally and landed nowhere. Worth
checking across all 44 repositories it covered.
