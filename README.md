# About `grep+`

![Demo of grep+](https://raw.githubusercontent.com/misaki-web/grepp/main/assets/demo.gif)

`grep+` performs `grep` searches while improving result display. Each result is aligned, has a clickable link to the file at the specific line number, and includes syntax highlighting for the entire line.

Syntax highlighting is automatically adjusted according to the detected terminal background (dark or light).

## Installation

Download the script and run it to create the default configuration file (`$HOME/.config/grep+/config.ini`) and make a copy in the default binary location for the current user (`$HOME/.local/bin` by default):

	wget "https://raw.githubusercontent.com/misaki-web/grepp/main/grep%2B"
	bash grep+

## Usage and help

The simplest invocation is `grep+ SEARCHED`. A search will be performed in the current directory. You can also specify a different location:

	grep+ SEARCHED /path/to/folder

Regular expressions are used by default. For example, to search for the exact word "declare" and exclude "undeclare", "declared", etc.:

	grep+ "\bdeclare\b"

To disable regular expressions, start the search expression with `g+nore:`:

	grep+ "g+nore:declare"

To limit results to one occurrence per file, start the search expression with `g+one:`:

	grep+ "g+one:declare"

To use several "g+" options, include them in alphabetical order. Example:

	grep+ "g+force:g+nore:g+one:expression searched"

Results that are too long are truncated and enclosed in "[...]". Example:

	/path/to/file:150 | [...] pharetra ut, malesuada et, magna class aptent taciti litora [...]

To speed up the search, binary files and the following folders from version control systems are excluded:

- `.bzr` from GNU Bazaar
- `.git` from Git
- `.hg` from Mercurial
- `.svn` from Apache Subversion

A detailed explanation of commands and settings is displayed when running `grep+ -h`. Help output is also accessible in the file [help.md](https://github.com/misaki-web/grepp/blob/main/help.md).

*Note: depending on your terminal settings, you may have to hold the `Ctrl` key while clicking on the link to open the file.*

### Dependencies

The `highlight` package must be installed.

`grep+` is developed on Ubuntu using Bash 5 with the multi-layout terminal [Tilix](https://github.com/gnunn1/tilix).

### Scheme handler

A custom scheme handler is created to open files at a specific line number. Examples of scheme handlers include `https://`, `file://`, etc. This script creates the `grep+` scheme handler, so any URL with the following format will be handled by `grep+`:

	grep+://FILE:LINE_NUMBER

Example:

	url="grep+:///home/user/Desktop/script.js:150"
	xdg-open "$url"

`grep+` will attempt to open the file at the specified line number, looking for a supported editor installed on the system and running it with the appropriate arguments (e.g., `gedit /path/to/file +150`). Supported editors include:

- atom
- code (Visual Studio Code)
- eclipse
- emacs / emacsclient
- geany
- gedit
- gvim
- jedit
- kate
- kile
- kwrite
- micro
- nano
- notepadqq
- pluma
- qtcreator
- scite
- vi
- vim

### Terminals without link support

If your terminal doesn't support custom links, you can enable the link fallback in the configuration file. However, this disables line number support.

## Screenshots

*Note: in all examples, the searched term is `HARDCODED_INI`.*

### Default style

#### Default dark style

![Default dark style](https://raw.githubusercontent.com/misaki-web/grepp/main/assets/default-dark.png)

#### Default light style

![Default light style](https://raw.githubusercontent.com/misaki-web/grepp/main/assets/default-light.png)

### More examples

Here are a few examples of different styles after changing settings and color highlighting in the `grep+` configuration file.

#### Dark compact style 1

![Dark compact style 1](https://raw.githubusercontent.com/misaki-web/grepp/main/assets/dark-compact-1.png)

#### Dark compact style 2

![Dark compact style 2](https://raw.githubusercontent.com/misaki-web/grepp/main/assets/dark-compact-2.png)

#### Light compact style 1

![Light compact style 1](https://raw.githubusercontent.com/misaki-web/grepp/main/assets/light-compact-1.png)

#### Light compact style 2

![Light compact style 2](https://raw.githubusercontent.com/misaki-web/grepp/main/assets/light-compact-2.png)

## License

Copyright (C) 2021  Misaki F. <https://github.com/misaki-web>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
