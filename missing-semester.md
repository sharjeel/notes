# Missing Semester

Notable stuff from MIT's [Missing Semester 2020](https://missing.csail.mit.edu/2020/)

## [Shell Tools and Scripting](https://missing.csail.mit.edu/2020/course-shell/)

shellcheck tool: lint for your shell scripts
tldr: more tutorial oriented than man pages which just describe all the options of a program
man test # Gives a comprehensive overview of all the shell comparison predicates
convert image.{png,jpg} # as shortcut for converting image.png to image.jpg
Most Unix systems have indexed file lookup with "locate". `sudo updatedb` to update the database.
ripgrep for searching through files
fzf -- interactive grep, binds with history as well
tree -- prints tree
broot -- interactive tree explorer with fuzzy search

## [Data Wrangling](https://missing.csail.mit.edu/2020/data-wrangling/)

- In regular expression, ? prefix next to * or + disables greedy matching.
- If you are trying to parse HTML or JSON with REs, you should probably switch to another tool.
- sed is a terrible programming language except for searching and replacing (I'm an awk user anyway, so who cares)

## [Command-line environment](https://missing.csail.mit.edu/2020/command-line/)

### Job control
^C: SIGINT
^\: SIGQUIT
SIGINT, SIGQUIT mostly related to terminal. SIGTERM: More generic way of asking a process to terminate gracefully.
Python Signal handling: import signal; signal.signal(signal.SIGINT, handler_func)
Commands to control jobs: nohup, bg %n, fg %n, jobs, kill %n

### Tmux
`C-b <SPACE>` to cycle between layouts

(instructor uses alacritty as their GPU; GPU powered speed things up quite a bit)

## [Version Control](https://missing.csail.mit.edu/2020/version-control/)
(this was the best tutorial on git I've seen)
Every object has a sha1 hash and objects are tracked in .git directory.
git add -p <filename> # lets you interactively choose which portions of the fileto stage
git diff --cached # shows what changes are staged for commit instead of all changes
git bisect # figure out when did a particular unit test stopped working instead of manually toiling through history. Also takes in a script to figure out if aparticular commit is looking good or bad.
Recommended book: Pro Git -- free book and first couple of chapters would begood enough to get you started for real software projects.
  
## [Debugging and Profiling](https://missing.csail.mit.edu/2020/debugging-profiling/)

- printf on command line can be used to try escape characters
- journalctl to read systemd logs, dmesg to access the kernel logs, "logger" to
add an entry to system logs.
- ANSI Escape Code for color coding terminal output: https://en.wikipedia.org/wiki/ANSI_escape_code
- lnav: provides an improved presentation for reading log files (This was the
best thing I got out of this lecture)
- pdb has post-mortem debugging support (wish I'd known that much earlier!)
- gdb works with pretty much any binary you can execute
- strace for tracing syscalls as dynamic analysis, dtrace on Mac/BSD is complicated but dtruss gives an strace like interface on the top.
- For static analysis: pyflakes, mypy for python; writegood for English;
Firefox, Chrome have builtin debugging tools.
- Profiling
- time command: Realtime: entire time, User time: userspace time, System: kernelspace time
- Python: python -m cProfile ...
- Line Profiler: More readable. kernprof is one line profiler
- Memory Profiler: python -m memory_profiler ..._
- General perf profiler for CPU, mem pages etc: perf stat ...
- Visualization: Flame Graph, Call Graph (graph of which function called which
function)
- glances is a better and even more powerful alternative to htop which also
exports web interface.
- ncdu interactively shows disk usage
- ss can be an alternative to lsof for monitoring ports
- iftop and nethog are good interactive tools for monitoring traffic
- hyperfine benchmarks different commands
  
## [Metaprogramming](https://missing.csail.mit.edu/2020/metaprogramming/)
  
- Versioning: major.minor.patch -- change major when there are backwards incompatible changes and minor for features.  
  
## [Cryptography](https://missing.csail.mit.edu/2020/security/)
- OpenSSL is a handy CLI utility for encrypting and decrypting
  
## [Potpourri](https://missing.csail.mit.edu/2020/potpourri/)
- rclone for mountain cloud drives, such as DropBox, GDrive etc.
- kbfs for encrypted sharing
- hammerspoon: Desktop automation framework for MacOS
  

  
