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

Delete indentation

`M-^`

Paste in the search mini-buffer

`C-s M-y`

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

Edit the search mini-buffer

`M-e`

### Macros

Start keyboard macro recording

`C-x (` or `F3`

Stop keyboard macro recording

`C-x )` or `F4`

Execute macro

`C-x e` or `F4`
