dtail - Bash script to watch file modification using inotify
===

## Description

`dtail` is a simple bash script to watch file modification in directories using [inotify\-tools](//github.com/rvoicilas/inotify-tools/wiki) and `tail -f`.

`dtail` watches all files and directories specified by user and traps events CREATE, MODIFY and DELETE.
If a event of directory or file which the user does not have reading permission, the event is ignored.
When CREATE event or MODIFY event of file that is not monitored by `dtail` is fired, `dtail` starts background `tail` process and adds it to the process pool.
Yes, `dtail` uses pool strategy to avoid resource overrun of the user and operating system.
The pool size, that is the maximum number of background `tail` processes, can be specified as command line option.
If the pool is full, the oldest process is deleted from the pool and the tail process is killed.

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

