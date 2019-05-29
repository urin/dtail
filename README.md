dtail - Bash script to watch contents of files using inotify
===

## Overview

`dtail` is a simple bash script to watch contents of file in directories using [inotify\-tools](//github.com/rvoicilas/inotify-tools/wiki) and `tail`.
You can watch any file even if they are newly created in directories.

## Description

`dtail` watches all files and directories trapping events CREATE, MODIFY and DELETE.

`dtail` creates a `tail` process for each watching file and has a process pool that is a list of `tail` processes.
When CREATE or MODIFY event of a file that is not monitored by `dtail` is fired, `dtail` starts background `tail` process and adds it to the process pool. If the pool is full, the oldest process is deleted from the pool and the tail process is killed.

The pool size, that is the maximum number of background `tail` processes, can be specified by user.

Event of a directory or file without reading permission is ignored.

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

[MIT](/LICENSE)

## Author

[urin](//github.com/urin)

