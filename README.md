# pipe transformation workflow for Alfred

An [Alfred](http://www.alfredapp.com/) workflow enabling easy transformation of the current contents of the clipboard by piping through arbitrary shell one-liners.

## Requirements

- [Alfred](http://www.alfredapp.com/) (version 2.0+)
- The [Alfred Powerpack](http://www.alfredapp.com/powerpack/).

## Usage

Trigger the workflow by hotkey or keyword (default=`|`, override with the `keyword` variable) followed by an arbitrarily simple or complex shell one-liner to transform the contents of the clipboard in-place; optionally use the `Cmd`-modifier to immediately paste the results into the foreground app, or the `Alt`-modifier to show the results in large type.

Two hotkeys are configurable:
- transform the current contents of the clipboard (like the keyword); recommended hotkey: `Ctrl-Cmd-\`
- transform the current selection in the foreground app; recommended hotkey: `Ctrl-Cmd-C`

When triggered via hotkey, the leading keyword (e.g. `|`) is not required.

### Examples

- Transform to UPPERCASE: `| perl -nle 'print uc'` or `| tr a-z A-Z`
- Base64 encode: `| base64`
- Base64 decode: `| base64 --decode`
- Top 10 unique lines with counts: `| sort | uniq -c | sort -rn | head -10`

### Built-ins

A number of example pipelines (including those above) are [built-in](https://github.com/isometry/alfred-pipe/raw/master/builtins.json).

Built-ins can be disabled en-mass by setting the `load_builtins` variable to any value other than `yes`.

### Aliases

To save repetitive typing, custom aliases can be defined with the following syntax:

`| alias NAME=PIPE | LINE @@@`

The trailing `@@@` (override with the `alias_terminator` variable) terminates the alias definition and causes it to be saved.

#### Examples

- `| alias tac=sed '1!G;h;$!d' @@@`
- `| alias top10=sort | uniq -c | sort -rn | head -10 @@@`

#### Alias removal

Any custom alias can be removed with:

`| alias NAME=@@@`

## Contributions & Thanks

- ctwise
