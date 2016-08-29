Grep
========

Utility for searching plain-text data sets for lines matching a regular expression. Each input line that matches at least one of the patterns is written to the standard output.

Options
----------

### -A num, --after-context=num
  + Print num lines of trailing context after each match.

### -a, --text
  + Treat all files as ASCII text.
  + Use of this option forces grep to output lines matching the specified pattern.

### -B num, --before-context=num
  + Print num lines of leading context before each match.

### -b, --byte-offset
  + The offset in bytes of a matched pattern is displayed in front of
the respective matched line.

### -C[num, --context=num]
  + Print num lines of leading and trailing context surrounding each match.
  + The default is 2 and is equivalent to -A 2 -B 2.
  + No whitespace may be given between the option and its argument.

### --colour=[when, --color=[when]]
  + Mark up the matching text with the expression stored in GREP_COLOR environment variable.
  + The possible values of when can be `never`, `always` or `auto`.

### -D action, --devices=action
  + Specify the demanded action for devices, FIFOs and sockets.
  + The default action is `read', which means, that they are read as if they were normal files.
  + If the action is set to `skip', devices will be silently skipped.

### -d action, --directories=action
  + Specify the demanded action for directories.
  + Default is `read`
  + `skip` to silently ignore the directories
  + `recurse' to read directories recursively

### -E, --extended-regexp
  + Interpret pattern as an extended regular expression
  + Forces grep to behave as egrep

### -e pattern, --regexp=pattern
  + Specify a pattern used during the search of the input.
  + An input line is selected if it matches any of the specified patterns.
  + Useful when multiple -e options are used to specify multiple patterns, or when a pattern begins with a dash (`-').

### --exclude
  + Excludes files matching the given filename pat tern from the search.
  + `--exclude patterns` take priority over `--include patterns`
  + Patterns are matched to the full path specified, not only to the filename component.

### --exclude-dir
  + If -R is specified, it excludes directories matching the given
filename pattern from the search.
  + `--exclude-dir` patterns take priority over `--include-dir` patterns.

### -F, --fixed-strings
  + Interpret pattern as a set of fixed strings.
  + Forces grep to behave as fgrep

### -f file, --file=file
  + Read one or more newline separated patterns from file.

### -G, --basic-regexp
  + Interpret pattern as a basic regular expression
  + Forces grep to behave as traditional grep

### -H
  + Always print filename headers with output lines.

### -h, --no-filename
  + Never print filename headers (i.e. filenames) with output lines.

### -I
  + Ignore binary files.

### -i, --ignore-case
  + Perform case insensitive matching.
  + Grep is case sensitive by default

### --include
  + Only files matching the given filename pattern are searched.

### --include-dir
  + If -R is specified, only directories matching the given filename pattern are searched.

### -L, --files-without-match
  + Only the names of files **not** containing selected lines are written to standard output.
  + Pathnames are listed once per file searched.

### -l, --files-with-matches
  + Only the names of files containing selected lines are written to standard output.
  + Will only search a file until a match has been found, making searches potentially less expensive.
  + Pathnames are listed once per file searched.

### --mmap
  + Use mmap(2) instead of read(2) to read input.
  + Can result in better performance under some circumstances but can cause undefined behaviour.

### -m num, --max-count=num
  + Stop reading the file after num matches.

### -n, --line-number
  + Each output line is preceded by its relative line number in the file.

### o, --only-matching
  + Prints only the matching part of the lines.

### -q, --quiet, --silent
  + Quiet mode
  + Suppress normal output.
  + Will only search a file until a match has been found.
  + Makes searches potentially less expensive.

### -R, -r, --recursive
  + Recursively search subdirectories listed.

### -S
  + If -R is specified, all symbolic links are followed.
  + The default is not to follow symbolic links.

### -U, --binary
  + Search binary files, but do not attempt to print them.

### -v, --invert-match
  + Selected lines are those not matching any of the specified patterns.

### -w, --word-regexp
  + The expression is searched for as a word.
  + As if surrounded by `[[:<:]]` and `[[:>:]]`

### -x, --line-regexp
  + Only input lines selected against an entire fixed string or regular expression are considered to be matching lines.

### --binary-files=value
  + Controls searching and printing of binary files
  + `binary`, the default: search binary files but do not print them
  + `without-match`: do not search binary files
  + `text`: treat all files as text.

### --context[=num]
  + Print num lines of leading and trailing context.
  + Default is 2.

### --line-buffered
  + Force output to be line buffered.
  + By default, output is line buffered when standard output is a terminal and block buffered otherwise.

Sample Commands
---------------
`grep pattern files`: Search for 'pattern' in 'files'

`grep -r pattern dir`: Search recursively for 'pattern' in dir

`cmd | grep pattern`: Search for 'pattern' in output of cmd