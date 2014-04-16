Tmux
===

### Cursor Mode

Cursor mode:

`C-b [`

Quit cursor mode:

`q`

Move around, select, copy using emacs bindings:

`C-p
C-n
C-a
C-b
C-f
M-w
C-space
`

Paste:

`C-b ]`

### Panes management

Split horizontally:

`C-b "`

Split vertically:

`C-b %`

Moves around:

`C-b <left|right|up|down>`

### Sessions

Start new:

`tmux`

Start new named

`tmux new -s sessname`

Attach to existing session:

`tmux a`

Attached to named sesssion:

`tmux a -t sessname`

List sessions:

`tmux ls`

Kill session:

`tmux kill-session -t sessname`


