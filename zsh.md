ZSH
===

### Globbing

List, removing or executing any command upon recursively matching pattern: `**/*`

```
ls **/*.java
rm **/*.bak
git diff **/Network*.py
```

### Histoy repetition

Repeat last argument of the last command: `!$` or `ESC-.` or `Alt-.`

```
$ echo hello world
hello world
$ echo $!
world
```

Repeat first argument of the last command: `!^`
n-th argument: `!:n`


Change the path in the current directory by replacing: `cd old new`

```
$ pwd
/home/user/java/com/example/hello/world/
$ cd java javatests
$ pwd
/home/user/javatests/com/example/hello/world/
```

### Key Bindings

List all key bindings `bindkey`

List keymaps `bindkey -l`

List keymap linked to main `binkey -lL main`

## Help

Help on a builtin function `run-help func-name`

Help on user contributed items `run-help run-help`
