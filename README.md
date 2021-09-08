# About `grep+`

`grep+` performes grep searches while improving results display. Each result is aligned, has a clickable link to the file at the specific result line number and has syntax highlighting applied to the entire result line.

Syntax highlighting is adjusted automatically according to the terminal background detected (dark or light).

# Installation

Download the script and run it to create the default configuration file (`$HOME/.config/grep+/config.ini`) and make a copy in the default binary emplacement for the current user (`$HOME/.local/bin` by default):

	wget "https://raw.githubusercontent.com/misa-ki/grepp/main/grep%2B"
	bash grep+

# Usage and help

The simplest invocation is `grep+ SEARCHED`. A search will be performed in the current emplacement. It's possible to specify the emplacement:

	grep+ SEARCHED /path/to/folder

A detailed explanation of commands and settings is displayed when the script is invoked without arguments (`grep+`).

*Note: depending on your terminal settings, you may have to hold the `Ctrl` key while clicking on the link to open the file.*

## Dependencies

The package `highlight` must be installed.

`grep+` is developed on Ubuntu with Bash 5 with the multilayouts terminal [Tilix](https://github.com/gnunn1/tilix).

## Scheme handler

A custom scheme handler is created in order to open files at a specific line number. Examples of scheme handlers are `https://`, `file://`, etc. The script will create the scheme handler `grep+`, so any URL with the following format will be handled by `grep+`:

	grep+://FILE:LINE_NUMBER

Example:

	url="grep+:///home/user/Desktop/script.js:150"
	xdg-open "$url"

## Terminals without link support

If your terminal doesn't support custom links, you can enable the link fallback in the configuration file. However, it will disable line number support.

# Screenshots

*Note: in all examples, the searched term is `HARDCODED_INI`.*

## Default style

### Default dark style

![Default dark style](https://raw.githubusercontent.com/misa-ki/grepp/main/assets/default-dark.png)

### Default light style

![Default light style](https://raw.githubusercontent.com/misa-ki/grepp/main/assets/default-light.png)

## More examples

Here are a few examples of different styles after changing settings and color highlighting in the `grep+` configuration file.

### Dark compact style 1

![Dark compact style 1](https://raw.githubusercontent.com/misa-ki/grepp/main/assets/dark-compact-1.png)

### Dark compact style 2

![Dark compact style 2](https://raw.githubusercontent.com/misa-ki/grepp/main/assets/dark-compact-2.png)

### Light compact style 1

![Light compact style 1](https://raw.githubusercontent.com/misa-ki/grepp/main/assets/light-compact-1.png)

### Light compact style 2

![Light compact style 2](https://raw.githubusercontent.com/misa-ki/grepp/main/assets/light-compact-2.png)

# License

Copyright (C) 2021  Misaki F. <https://github.com/misa-ki/grepp>

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
