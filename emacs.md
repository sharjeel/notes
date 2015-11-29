Emacs
===

Help on a key:

`C-h k`
or
`C-h c <key sequence>`

Find key shortcut for a function

`C-h function-name`
or
`C-h w function-name`

Describe Key bindings

`M-x describe-bindings`

Info engine

`M-x info`

Go Back:

`C-u C-SPC` or `C-u C-@`

Go back in different buffers:

`C-x C-SPC` or `C-x C-@`

Save in register: 

`C-x r s`

Insert from register:

`C-x r i` or `C-x r g`

Filter lines:

```
M-x keep-lines
M-x filter-lines
```

Join lines with a delimiter e.g. ",":

```
M-x replace-string
C-q C-j
, 
```

Query replace to interactively replace:

`M-x query-replace` or `M-%`

Delete indentation

`M-^`

Paste in the search mini-buffer

`C-s M-y`

Mark rectangle (emacs 24.4+)

`C-x SPC`

Kill rectangle

`C-x r k`

Blank out rectangle

`C-x r c`

Add prefix each line in rectangle

`C-x r t`

Repeat last command

`C-x z`

Repeat last command 3 times

`C-x z z z`

Search the word following the mark

`C-s C-w`

Search the word before the mark

`C-r C-w`

Find all occurances of a regexp

`M-x occur`

Edit the search mini-buffer

`M-e`

Search Regexp

`C-M-s` and `C-M-r`

### Macros

Start keyboard macro recording

`C-x (` or `F3`

Stop keyboard macro recording

`C-x )` or `F4`

Execute macro

`C-x e` or `F4`

Balance Windows

`C-x +`

Eval in minibuffer

`M-:`

To get full path of current buffer, use the variable `buffer-file-name`

```
M-:
buffer-file-name
```

### Eshell

Redirect output to an emacs buffer

`cat mylog.log >> #<buffer *scratch*>`

or to append at the point

`cat mylog.log >>> #<buffer *scratch*>`

Use emacs variables in eshell

```
$ echo foo bar baz > #'myvar
$ echo $(cadr myvar)
bar
```

Open a file

`find-file filename`

Pseudo-devices

```
$ echo 'This goes to clipboard' > /dev/clip
$ echo 'This gets to kill-ring' > /dev/kill
```

The variable `eshell-virtual-targets` can be used to add more pseudo-devices.


