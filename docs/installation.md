# Installation

LEGO Block Creator installs from the [Python Package Index](https://pypi.org/project/lego-block-creator/),
runs as a [Docker](https://www.docker.com/) container from GitHub Packages, or
runs directly from a source checkout.

## Requirements

| Requirement | Version | Notes |
|---|---|---|
| Python | 3.9 or later | Not needed for the Docker install |
| Docker | any | Only for the container install |

There are no runtime package dependencies. `requirements.txt` lists `pytest`
and `pytest-cov`, which are needed only to run the test suite.

## Install

=== "pip"

    ```bash
    pip install lego-block-creator
    ```

    Start it with the console command installed alongside the package:

    ```bash
    lego-block-creator
    ```

=== "Docker"

    ```bash
    docker pull ghcr.io/willtheorangeguy/lego-block-creator:master
    ```

    The image's default command is a shell, so name the script explicitly and
    run the container interactively — the program reads from stdin:

    ```bash
    docker run -i -t ghcr.io/willtheorangeguy/lego-block-creator:master python main.py
    ```

=== "From source"

    ```bash
    git clone https://github.com/willtheorangeguy/LEGO-Block-Creator.git
    cd LEGO-Block-Creator
    python main.py
    ```

    Source archives for tagged versions are on the
    [releases page](https://github.com/willtheorangeguy/LEGO-Block-Creator/releases/latest).

## Verify the installation

```bash
lego-block-creator
```

```text
LEGO CMD:
```

Type `help` and press ++enter++ to confirm the command list prints.

## Upgrading

=== "pip"

    ```bash
    pip install --upgrade lego-block-creator
    ```

=== "Docker"

    ```bash
    docker pull ghcr.io/willtheorangeguy/lego-block-creator:master
    ```

=== "From source"

    ```bash
    git pull
    ```

## Uninstalling

```bash
pip uninstall lego-block-creator
```

The program writes nothing to disk, so there is no data or configuration left
behind to remove.

{{ support() }}
