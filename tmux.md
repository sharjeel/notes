Tmux
===

### Cursor Mode

Cursor mode:

`C-b [`

Quit cursor mode:

`q`

Move around, select, copy using emacs bindings:

```
C-p
C-n
C-a
C-b
C-f
M-w
C-space
```

Paste:

`C-b ]`

### Panes management

Split horizontally:

`C-b "`

Split vertically:

`C-b %`

Moves around:

`C-b <left|right|up|down>`

Kill current pane:

`C-b x`

Kill all panes except this one:

`C-b !`

Swap location of panes

`C-b C-o`

Identify panes

`C-b q`

### Sessions

Start new:

`tmux`

Start new named

`tmux new -s sessname`

Attach to existing session:

`tmux a`

Attached to named sesssion:

`tmux a -t sessname`

Detach from session:

`C-b d`

Detach other clients:

`C-b D`

List sessions:

`tmux ls`

Kill session:

`tmux kill-session -t sessname`

Rename current session:

`C-b $`

### Configuration

User's config file location:

`~/.tmux.conf`

Command Prompt (REPL):

`C-b :`

### Help

List Keys: 

`tmux list-keys`

List every command and it's arguments:

`tmux list-commands`

List detailed info about every session:

`tmux info`
