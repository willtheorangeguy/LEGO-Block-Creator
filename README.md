<!-- Logo -->
<h1 align="center">
  <img src="https://raw.githubusercontent.com/willtheorangeguy/LEGO-Block-Creator/master/docs/images/logo.png" height="250px" width="400px" alt="LEGO Block Creator">
  <br>
  LEGO Block Creator
  <br>
</h1>

<!-- Copy -->
<h4 align="center">Offline inventory tracking of LEGO parts and sets through an easy to use CLI.</h4>

<!-- Badges -->
<div align="center">
  <!-- Stability -->
  <img alt="Docker Build State" src="https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/docker-publish.yml/badge.svg">
  <!-- Stability -->
  <img alt="PyPI Build State" src="https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/push-to-pypi.yml/badge.svg">
  <!-- Stability -->
  <img alt="Pytest State" src="https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/pytest.yml/badge.svg">
  <!-- Stability -->
  <img alt="Pylint State" src="https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/pylint.yml/badge.svg">
  <!-- CodeQL -->
  <img alt="CodeQL State" src="https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/codeql-analysis.yml/badge.svg">
  <!-- Version -->
  <img alt="GitHub Version" src="https://img.shields.io/github/v/release/willtheorangeguy/LEGO-Block-Creator?include_prereleases">
  <!-- Issues -->
  <img alt="GitHub Issues" src="https://img.shields.io/github/issues/willtheorangeguy/LEGO-Block-Creator">
  <!-- Pull Requests -->
  <img alt="GitHub Pull Requests" src="https://img.shields.io/github/issues-pr/willtheorangeguy/LEGO-Block-Creator">
  <!-- Discord -->
  <img alt="Discord Server ID" src="https://img.shields.io/discord/961502230521978920">
  <!-- Downloads -->
  <img alt="Downloads" src="https://img.shields.io/github/downloads/willtheorangeguy/LEGO-Block-Creator/total">
  <!-- Language Count -->
  <img alt="GitHub Languages" src="https://img.shields.io/github/languages/count/willtheorangeguy/LEGO-Block-Creator">
</div>

<!-- Navigation -->
<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#download">Download</a> •
  <a href="#how-to-use">How To Use</a> •
  <a href="#support">Support</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#changelog">Changelog</a> •
  <a href="#credits">Credits & Contributors</a>
</p>

<!-- Screenshot(s) -->
![screenshot](https://raw.githubusercontent.com/willtheorangeguy/LEGO-Block-Creator/master/docs/images/newpiece.png)
![screenshot](https://raw.githubusercontent.com/willtheorangeguy/LEGO-Block-Creator/master/docs/images/newset.png)

## Key Features

* Easy to use CLI interface.
* Can create pieces, sets and colors.
* Able to add and remove new pieces to previously existing pieces.
* Able to add and remove new sets to previously existing sets.
* Can sort items by name, color, number and theme.
* Cross platform.

## Download

You can **[download](https://github.com/willtheorangeguy/LEGO-Block-Creator/releases/latest) the source code** to run the CLI from the command line on Windows, macOS and Linux. **This will require [Python](https://www.python.org/downloads/).**

You can **[download](https://github.com/willtheorangeguy/LEGO-Block-Creator/releases/latest) the latest executable launcher** of LEGO Block Creator for Windows. **This does not require Python.**

## How To Use

To run the application, you can use [Git and the Python Interpreter](https://github.com/willtheorangeguy/LEGO-Block-Creator/main/README.md#git), which allows you to clone and run the application, [`pip`](https://github.com/willtheorangeguy/LEGO-Block-Creator/main/README.md#pip) to create a command line application, or [Docker](https://github.com/willtheorangeguy/LEGO-Block-Creator/main/README.md#docker) to create a container of the application.

### Git

To clone and run this application, you'll need [Git](https://git-scm.com/downloads) and [Python](https://www.python.org/downloads/) installed on your computer. If you would rather not use Git, you can just download the script from GitHub above. From your command line:

```bash
# Clone this repository
$ git clone https://github.com/willtheorangeguy/LEGO-Block-Creator

# Go into the repository
$ cd LEGO-Block-Creator

# Run the CLI
$ python main.py
```

### `pip`

You can install the program from the [Python Package Index](https://pypi.org/project/LEGO-Block-Creator/) through `pip`.

```bash
# Install via pip
$ pip install lego-block-creator

# Run the CLI
$ lego-block-creator
```

### Docker

You can pull the [Docker](https://www.docker.com/) image from GitHub Packages. From your command line:

```bash
# Pull image
$ docker pull ghcr.io/willtheorangeguy/lego-block-creator:master

# Run container
$ docker run -i -t ghcr.io/willtheorangeguy/lego-block-creator:master python send.py
```

## Support

To create your part and set library and manipulate it, just launch the app using the instructions above!

More documentation is available in the **[Documentation](https://github.com/willtheorangeguy/LEGO-Block-Creator/tree/main/docs)** and on the **[Wiki](https://github.com/willtheorangeguy/LEGO-Block-Creator/wiki)**. If more support is required, please open a **[GitHub Discussion](https://github.com/willtheorangeguy/LEGO-Block-Creator/discussions/new)** or join our **[Discord](https://discord.gg/hnKjsBcpBR)**.

## Contributing

Please contribute using [GitHub Flow](https://guides.github.com/introduction/flow). Create a branch, add commits, and [open a pull request](https://github.com/willtheorangeguy/LEGO-Block-Creator/compare).

Please read [`CONTRIBUTING`](https://github.com/willtheorangeguy/.github/blob/main/CONTRIBUTING.md) for details on our [`CODE OF CONDUCT`](https://github.com/willtheorangeguy/.github/blob/main/CODE_OF_CONDUCT.md), , and the process for submitting pull requests to us.

## Changelog

See the [`CHANGELOG`](CHANGELOG.md) file for details.

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

## Contributors

* [@willtheorangeguy](https://github.com/willtheorangeguy) - Sponsor on [PayPal](https://paypal.me/wvdg44?country.x=CA&locale.x=en_US)

## You may also like...

* [ProgramVer](https://github.com/willtheorangeguy/ProgramVer) - An open-source, Python GUI version window to show copyright info and licenses.
* [PyWorkout](https://github.com/willtheorangeguy/PyWorkout) - A minimal CLI to keep you inspired during your workout!
* [PyAvatar](https://github.com/willtheorangeguy/PyAvatar) - Easily display all of your creative avatars to keep them consistent across websites.

## License

This project is licensed under the [MIT License](https://mit-license.org/) - see the [`LICENSE`](LICENSE.md) file for details.

**This project is in no way endorsed and/or affiliated by/with the LEGO Group or any of its subsidiaries.** LEGO, the LEGO logo, the Minifigure, DUPLO, LEGENDS OF CHIMA, NINJAGO, BIONICLE, MINDSTORMS and MIXELS are trademarks and copyright the [LEGO Group](https://www.lego.com/en-ca/legal/).
