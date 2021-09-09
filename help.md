grep+ performes grep searches while improving results display. Each result is aligned,
has a clickable link to the file at the specific result line number and has syntax
highlighting applied to the entire line.

USAGE
=================================================================

Type one of the following commands:

grep+ SEARCH_PATTERN [EMPLACEMENT]
-----------------------------------------------------------------

SEARCH_PATTERN can be a regular expression pattern. EMPLACEMENT can be a folder for
recursive search or a specific file. If it's empty, the current folder returned by
the command "pwd" will be used. Example:

    grep+ "^function abc_[0-9]+_def\s*\(" "/path/to/folder"

If you want to search a pattern starting with a grep+ parameter (like "--install"),
the optional parameter "--force_search" can be used. Example:

    grep+ --force_search "--install" "/path/to/folder"

Regular expressions are used by default. For example, to search the exact word "declare" and exclude
"undeclare", "declared", etc.:

    grep+ "\bdeclare\b"

To disable regular expression, start the search expression with "g+nore:":

    grep+ "g+nore:declare"

To limit results to one occurrence per file, start the search expression with "g+one:":

    grep+ "g+one:declare"

To invoke several "g+" options, include them in alphabetical order. Example:

    grep+ "g+force:g+nore:g+one:expression searched"

In order to speed up search, binary files and the following folders from control version applications
are excluded from search:

- ".bzr" from GNU Bazaar
- ".git" from Git
- ".hg" from Mercurial
- ".svn" from Apache Subversion


grep+ --install
-----------------------------------------------------------------

Add grep+ in the local bin folder. The script will add it automatically if it's not
installed, so it shouldn't be necessary to install it manually.


grep+ --open SCHEME_HANDLER_URL
-----------------------------------------------------------------

Open the scheme handler URL (file at a specified line number). Example:

    grep+ --open "grep+:///home/user/folder/script.sh:250"


grep+ --add_scheme
-----------------------------------------------------------------

Add the custom scheme handler "grep+://" allowing to open files at
a specific line number. The script will add it automatically if it's not installed,
so it shouldn't be necessary to add it manually.


grep+ --rm_scheme
-----------------------------------------------------------------

Remove the custom scheme handler "grep+://".


CONFIGURATION
=================================================================

The configuration file path is "/home/jp/.config/grep+/config.ini". Here are all
available options:

- highlight_style: Style of the syntax highlighting applied to results.
  Value by default is as follows:

        highlight_style=

  To get all possible values, run the following command:

        grep+ --list_highlight_styles


- results_style: Style of results found by grep. Value by default is
  as follows:

        results_style=

  To get an overview of possibilities, run the following command:

        grep+ --list_results_styles


- path_relative_to_search: If "true", the file path is displayed relative
  to the search emplacement. For example, if "$(pwd)" returns "/home/user/Desktop" and
  the script is run to find results in "/home/user/Desktop/software", the file paths will
  be displayed like this:

        file.js
        subfolder/another-file.js

  If "false", the file path is displayed relative to the current emplacement. Example:

        software/file.js
        software/subfolder/another-file.js

  Default is "true".


- results_separator: Separator between file paths and results found. Default
  is "%BOX%". Example:

        path/to/file.js:250        | result lorem ipsum
        path/to/file.js:352        | result consectetuer lorem
        path/to/another/file.js:10 | result aliquet lorem quis

  The special word "%BOX%" means to adapt the symbol according to the results position in
  the list in order to have continuous lines. Example:

        ────────────────────────────┬────────────────────────────
         path/to/file.js:250        │ result lorem ipsum
        ────────────────────────────┼────────────────────────────
         path/to/file.js:352  AMET  │ result consectetuer lorem
        ────────────────────────────┼────────────────────────────
         path/to/another/file.js:10 │ result aliquet lorem quis
        ────────────────────────────┴────────────────────────────


- file_path_fallback: Useful only if the terminal used doesn't have full support
  for links. If "true", the script will display file paths with the scheme handler "file://".
  Note that opening files at a specific line number won't work if this option is enabled.

  Default is "false".


- launcher: Command to open files at a specific line number. About 20 editors are
  checked on the system. All editors found will be uncommented (without the leading symbol "#")
  on the configuration file. Example:

        launcher=nano +%LINE_NUMBER% %FILE%
        #launcher=kwrite -l %LINE_NUMBER% %FILE%
        #launcher=jedit %FILE% +line:%LINE_NUMBER%
        launcher=gedit %FILE% +%LINE_NUMBER%

  A custom launcher can be specified. To do so, add a new entry at the end of the configuration
  file:

        launcher=my-custom-editor PUT_CUSTOM_OPTIONS

