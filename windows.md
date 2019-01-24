## Contents







## Cmd

As usual, to see all the options `cmd /?`  

`/c` Carries out the command specified by string and then terminates.  
`/k` Carries out the command specified by string but remains.

An example of using `/c`, you want to delete a file. `del /q` deletes without prompting for confirmation:

```bat
/c del /q "a-file.txt"
```

## [Net](https://www.computerhope.com/nethlp.htm)

[`net use`](https://www.lifewire.com/net-use-command-2618096) connects or disconnects your computer from a shared resource or displays information about your connections.

The following will map `\\server\media\music` to your `Z` drive, not persisting on log out/in:

```bat
net use z: \\server\media\music
```

If you want persistence, use `/persistent:yes` or `/p:yes` at the end.





