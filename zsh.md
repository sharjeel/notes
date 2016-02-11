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

Swap the parameters of the last command with `Alt-T`

### Key Bindings

List all key bindings `bindkey`

List keymaps `bindkey -l`

List keymap linked to main `binkey -lL main`

### Positional Arguments

`$n` contains the nth arg where $0 is the name of the script/function itself. `$*` gets all the args passed to the script, without the scriptname itself, i.e. $* doesn't include $0. 

To split out parameters:

```
echoargs () {
  firstparam = $1
  shift 1
  echo "All passed args except first: " $*
}
```

### Help

Help on a builtin function `run-help func-name`

Help on user contributed items `run-help run-help`
