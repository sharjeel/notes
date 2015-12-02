rsync
===

Copy with progress

```
rsync -a --stats --progress src dst
```

Resume a failed scp transfer

```
rsync --partial --progress --rsh=ssh <remote-ssh-server+path> <localfilepath>
```

To copy symlinks, use `-l` flag

