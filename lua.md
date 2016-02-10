Lua Programming Language
===

## Basics

Defining a function:

```
function fact(n) 
  if n == 0 then
    return 1
  else
    return n * fact(n-1)
  end
end
```

Calling:

```
print("Enter a number: ")
a = io.read("*number") -- read a number
print(fact(a));

print("Semicolons in Lua are options");
```

Invoking interpreter

```
lua script.lua
lua -lscript1.lua -lscript2.lua
```

Executing a script in interactive mode

```
> dofile("script.lua")
```

Block comments 
```
--[[
this block comment
spans multiple lines
--]]

If first line of a lua file is `#`, it is ignored to keep up with unix compatibility of scripts. 

Evaluate directly from the shell

`lua -e 'print(math.sin(12))'`

`lua -i -l a.lua -e "x = 10"` will load a.lua, evaluate x = 10 and put the interpreter in interactive mode.

Before starting the interpreter, Lua looks for an environment variable called LUA_INIT and evaluates it before starting the debugger.
If the variable's name starts with @, then the filename following @ is loaded at the initialization of the interpreter.

## Variables

Using an unassigned variable is OK:

```
> print(x)
nil
> x = 10
> print(x)
10
```

Identifier's definition of alphabet is locale dependant. With proper locale one can use variable using unicode characters of that locale. 

Special variable `_PROMPT` contains the prompt of interactive mode.

Command line arguments are stored in `arg`. The script name is at index zero.
The arguments for the scripts are indexed 1 and onwards while arguments passed to lua prior to the script name are indexed in negative.
e.g. `lua -e "pi=22/7" script a b` collects the arguments as following:

```
arg[-3] = "lua"
arg[-2] = "-e"
arg[-1] = "pi=22/7"
arg[0] = "script"
arg[1] = "a"
arg[2] = "b"
```
