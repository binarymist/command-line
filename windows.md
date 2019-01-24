## Contents

* [Cmd](#cmd)
* [Findstr](#findstr)
* [Net](#net)
* [Sc](#sc)





## Cmd

As usual, to see all the options `cmd /?`  

`/c` Carries out the command specified by string and then terminates.  
`/k` Carries out the command specified by string but remains.

An example of using `/c`. You want to delete a file. `del /q` deletes without prompting for confirmation:

```bat
/c del /q "a-file.txt"
```

## [Findstr](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/findstr)

Searches for patterns of text in files.

An example could be:

```bat
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





