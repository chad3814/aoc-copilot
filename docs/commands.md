# Commands

AoC Copilot (AoCC) supports a few custom commands:
- [Index](#index)
- [Refresh](#refresh)
- [Cache](#cache)

Help is available from the command line by running:

```shell
npx aoc-copilot --help
```

and on specific commands by running:

```shell
npx aoc-copilot <command> --help
```

## Development

Commands in this group are useful during development - both of puzzle solutions as well as further enhancement of AoCC.

<a id="index"></a>
### Index

Display the index numbers and corresponding values for a selector which is particularly useful in creating an [example database](./egdb.md) entry.

Usage:

```shell
npx aoc-copilot index <year> <day> [selector]
```

For example:

```shell
npx aoc-copilot index 2020 2
```

will search the 2020 day 2 puzzle for the default selector `code` and display a list of indexes and values like:

```shell
Puzzle 2020 day 2 indexes matching selector 'code':
000:  
1-3 a: abcde    
1-3 b: cdefg    
2-9 c: ccccccccc

001:  1-3 a
002:  a    
003:  1    
...
```

Values without line breaks are shown immediately to the right of the index (e.g. indexes 1, 2 and 3), and multi-line ones are shown starting on a new line after the index (e.g. index 0).

You can use compound selectors, too:

```shell
npx aoc-copilot index 2020 2 "code, em"
```

```shell
Puzzle 2020 day 2 indexes matching selector 'code, em':
000:  passwords
001:  the corporate policy when that password was set
002:  
1-3 a: abcde
1-3 b: cdefg
2-9 c: ccccccccc

003:  1-3 a
004:  a
005:  1
...
```

<a id="refresh"></a>
### Refresh

Force the re-download of the puzzle page, and optionally the inputs.  Useful if your local cache has gotten out of sync with your actual progress, for example if you manually enter an answer on the website and AoCC is unaware of it.

Usage:

```shell
npx aoc-copilot refresh <year> <day> [--no-puzzle] [-i|--input]
```

For example, to re-download the puzzle for 2020 day 2:

```shell
npx aoc-copilot refresh 2020 2
```

You can use the `--no-puzzle` option to prevent the re-download of the puzzle, and the `--input` option to force the re-download of the input.  For exmaple, to re-download just the input file:

```shell
npx aoc-copilot refresh 2020 2 --no-puzzle --input
```

Or to re-download both the puzzle and the input:
```shell
npx aoc-copilot refresh 2020 2 --input
```

## Troubleshooting

<a id="cache"></a>
### Cache

Prints the location where puzzles, inputs and attempted answers are cached.  For example:

```shell
npx aoc-copilot cache
```

will print

```shell
Cache location: C:\Users\<user>\AppData\Local\AoC-Copilot
```

on Windows, or the equivalent path on Linux or Mac.