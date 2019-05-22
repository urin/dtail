dtail - Bash script to watch file modification using inotify
===

## Description

`dtail` is a simple bash script to watch file modification in directories using [inotify\-tools](//github.com/rvoicilas/inotify-tools/wiki) and `tail -f`.

## Requirement

- bash 3.1+
- inotify-tools 3.7+

## Usage

```
Usage: dtail [options] [--] path...

Options:
  -r|--recursive
    Watch subdirectories recursively.
  --exclude  <pattern> | --excludei <pattern>
    Exclude files if filename matches <pattern> (POSIX extended regular expression).
    It is case insensitive with --excludei.
  --fromfile <file>
    Read filenames to watch or exclude from a file, one filename per line.
    If filenames begin with @ they are excluded as described above.
  -p|--poolsize <num>
    Maximum number of watching processes. Default 1.

```

## License

[MIT](//github.com/tcnksm/tool/blob/master/LICENCE)

## Author

[urin](//github.com/urin)

