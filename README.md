<!-- Logo -->
<h1 align="center">
  <img src="https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/LEGO-Block-Creator/logo.png" height="250px" width="400px" alt="LEGO Block Creator">
  <br>
  LEGO Block Creator
  <br>
</h1>

<!-- Copy -->
<h4 align="center">A command-line catalogue for a LEGO collection — pieces, sets, colours, and themes, entirely offline.</h4>

<!-- Badges -->
<div align="center">
  <img alt="GitHub Version" src="https://img.shields.io/github/v/release/willtheorangeguy/LEGO-Block-Creator?include_prereleases">
  <img alt="GitHub Issues" src="https://img.shields.io/github/issues/willtheorangeguy/LEGO-Block-Creator">
  <img alt="GitHub Pull Requests" src="https://img.shields.io/github/issues-pr/willtheorangeguy/LEGO-Block-Creator">
  <img alt="License" src="https://img.shields.io/github/license/willtheorangeguy/LEGO-Block-Creator">
</div>

<!-- Navigation -->
<p align="center">
  <a href="#status">Status</a> •
  <a href="#key-features">Key Features</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#documentation">Documentation</a> •
  <a href="#support">Support</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#credits">Credits</a> •
  <a href="#license">License</a>
</p>

<!-- Screenshot -->
<div align="center">
  <img alt="Adding a piece" src="https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/LEGO-Block-Creator/newpiece.png">
  <img alt="Adding a set" src="https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/LEGO-Block-Creator/newset.png">
</div>

## Status

**The command surface works; the back end behind it does not.** Adding a piece echoes what you typed and stores it nowhere, and every sort or search prints a fixed placeholder dictionary regardless of input.

Treat the commands below as the intended interface. See [`docs/internal/known-issues.md`](docs/internal/known-issues.md) for exactly what happens today, and [`PLANNING.md`](PLANNING.md) for what is planned.

## Key Features

- An interactive prompt for pieces — name, colour, quantity.
- An interactive prompt for sets — name, number, theme, piece count, quantity.
- Sort and search commands for both, by name, colour, number, or theme.
- British and American spellings accepted for every colour command.
- Pure standard library; runs offline on Windows, macOS, and Linux.

## Installation

```bash
git clone https://github.com/willtheorangeguy/LEGO-Block-Creator
cd LEGO-Block-Creator
python main.py
```

Also on [PyPI](https://pypi.org/project/LEGO-Block-Creator/) as `lego-block-creator`, and as a Docker image — see [Installation](https://williamvdg.me/LEGO-Block-Creator/installation/).

## Usage

The program takes **one command per run**: start it, type a command, answer its prompts, and it exits.

```
LEGO CMD: newpiece
Name the piece you would like to add: 2x4 Brick
```

`help` lists every command. The full reference is in [Commands](https://williamvdg.me/LEGO-Block-Creator/api/).

## Documentation

Full documentation is published at **[williamvdg.me/LEGO-Block-Creator](https://williamvdg.me/LEGO-Block-Creator/)** and lives in [`docs/`](docs/index.md):
[Getting Started](docs/getting-started.md) · [Installation](docs/installation.md) · [Architecture](docs/architecture.md) · [Commands](docs/api.md) · [Testing](docs/testing.md) · [CI/CD](docs/ci-cd.md) · [FAQ](docs/faq.md)

## Support

Open a [GitHub Discussion](https://github.com/willtheorangeguy/LEGO-Block-Creator/discussions) or file an [issue](https://github.com/willtheorangeguy/LEGO-Block-Creator/issues/new/choose).

## Contributing

Please contribute using [GitHub Flow](https://guides.github.com/introduction/flow). Create a branch, add commits, and [open a pull request](https://github.com/willtheorangeguy/LEGO-Block-Creator/compare).

See the org-wide [Contributing Guide](https://github.com/willtheorangeguy/.github/blob/main/CONTRIBUTING.md) and [Code of Conduct](https://github.com/willtheorangeguy/.github/blob/main/CODE_OF_CONDUCT.md).

## Credits

This software uses the following open source packages, projects, services or websites:

<!-- Credits Table -->
<table>
  <tr>
    <th align="center"><img src="https://applets.imgix.net/https%3A%2F%2Fassets.ifttt.com%2Fimages%2Fchannels%2F2107379463%2Ficons%2Fmonochrome_large.png?w=240&h=240&s=8a19bbc158996d098e2fb18310ba7f33" width="150" height="150" alt="GitHub"/></th>
    <th align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/182px-Python-logo-notext.svg.png" width="150" height="150" alt="PSF"/></th>
    <th align="center"><img src="https://pyinstaller.readthedocs.io/en/v4.2/_static/pyinstaller-draft1a.ico" width="150" height="150" alt="PyInstaller"/></th>
    <th align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/LEGO_logo.svg/2048px-LEGO_logo.svg.png" width="150" height="150" alt="LEGO"/></th>
  </tr>
  <tr>
    <td align="center">GitHub</td>
    <td align="center">Python Software Foundation</td>
    <td align="center">PyInstaller</td>
    <td align="center">LEGO</td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/">Web</a> - <a href="https://github.com/pricing">Plans</a></td>
    <td align="center"><a href="https://www.python.org/">Web</a> - <a href="https://psfmember.org/civicrm/contribute/transact?reset=1&id=2">Donate</a></td>
    <td align="center"><a href="https://pyinstaller.readthedocs.io/en/stable/">Web</a> - <a href="https://www.pyinstaller.org/funding.html#funding-by-individuals">Donate</a></td>
    <td align="center"><a href="https://www.lego.com/">Buy a Set</a></td>
  </tr>
</table>

Sponsor [@willtheorangeguy](https://github.com/willtheorangeguy) on [PayPal](https://paypal.me/wvdg44?country.x=CA&locale.x=en_US).

## License

MIT — see [`LICENSE.md`](LICENSE.md).

**This project is in no way endorsed and/or affiliated by/with the LEGO Group or any of its subsidiaries.** LEGO, the LEGO logo, the Minifigure, DUPLO, LEGENDS OF CHIMA, NINJAGO, BIONICLE, MINDSTORMS and MIXELS are trademarks and copyright the [LEGO Group](https://www.lego.com/en-ca/legal/).
