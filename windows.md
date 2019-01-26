## Contents

* [Cmd](#cmd)
* [Findstr](#findstr)
* [Net](#net)
* [Sc](#sc)
* [Tasklist](#tasklist)

## Cmd

As usual, to see all the options `cmd /?`  

`/c` Carries out the command specified by string and then terminates.  
`/k` Carries out the command specified by string but remains.  
`/s` Modifies the treatment of _string_ after `/c` or `/k`.

An example of using `/c`. You want to delete a file. `del /q` deletes without prompting for confirmation:

```bat
rem Example:
/c del /q "a-file.txt"
```

## [Findstr](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/findstr)

Searches for patterns of text in files.

```bat
rem Example:
/c sc qc "VMware" | findstr BINARY_PATH_NAME | findstr /i /v /l /c:"c:\windows" | findstr /v /c:""""
```

Where we pipe the results of `sc` to `findstr BINARY_PATH_NAME`, piping those results to `findstr /i /v /l /c:"c:\windows"` where `/i` ignores case, `/v` only prints lines that do not contain a match, `/l` processes the search string literally, `/c:` specifies the literal search string (within quotes) "`c:\windows`", piping the results to `findstr /v /c:""""` which looks for lines that do not contain a match of `""`.

## [Net](https://www.computerhope.com/nethlp.htm)

[`net use`](https://www.lifewire.com/net-use-command-2618096) connects or disconnects your computer from a shared resource or displays information about your connections.

The following will map `\\server\media\music` to your `Z` drive, not persisting on log out/in:

```bat
net use z: \\server\media\music
```

If you want persistence, use `/persistent:yes` or `/p:yes` at the end.

## Sc

Service Control - Create, Start, Stop, Query or Delete any Windows [SERVICE](https://ss64.com/nt/syntax-services.html). The command options for SC are case sensitive.

`qc`: Show config - dependencies, full path, etc

For example, show config for service `VMware`:

```bat
sc qc "VMware"
```

## [Tasklist](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/tasklist)

Displays a list of currently running processes on the local computer or on a remote computer.

`fi <filter>` Specifies the types of processes (_[filter](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/tasklist#filter-names-operators-and-values)_) to include in or exclude from the query.

`"IMAGENAME eq devenv.exe"`  Image name is equal to `devenv.exe` (VisualStudio).

`"PID eq 11184"` Process ID is equal to `11184`

`/fo {table | list | csv}` Specifies the format to use for the output. Valid values are `table`, `list`, and `csv`. The default format for output is table.

`/nh` Suppresses column headers in the output. Valid when the `/fo` parameter is set to `table` or `csv`.

```bat
rem Example:
/s /c "tasklist /fi "IMAGENAME eq devenv.exe" /fi "PID eq 11184" /fo TABLE /nh"
```





## License

[![Creative Commons License](http://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/)
