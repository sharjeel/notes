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

Change the path in the current directory by replacing: `cd old new`

```
$ pwd
/home/user/java/com/example/hello/world/
$ cd java javatests
$ pwd
/home/user/javatests/com/example/hello/world/
```





