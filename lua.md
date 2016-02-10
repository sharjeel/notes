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

## Types

Lua is dynamically typed. There are eight basic types: nil, boolean, number, string, userdata, function, thread and table. `type()` function returns type of a given value. e.g. `type("sharjeel") --> string`.

### Integers

Lua has no integer type. Numbers are double-precision floating point. It is also possible to compile Lua to use single precision or long for arithmetic operations, specially for CPUs which don't have hardware support for floating point. 

### Strings

Lua is 8-bit clean. Strings may contain any numeric value including embedded zeroes and other binary data. String are immutable -- you apply modification to create a new string. e.g.:

```
a = "one string"
b = string.gsub(a, 'one', "another") -- substitute
print(a) -- one string
print(b) -- another string
````

C-like escape sequences are supported in Lua. e.g.: `\n New line \r Carriage return \t tab \v vertical tab \\ backslash \[ square bracket \" \'`. `\ddd` where ddd is a three lettered digit, replaces with ASCII eqiuvalents of the number.

Multiline strings can be written with square brackets:

```
page = [[
<html>
  <head><title>This is a title</title></head>
  <body> whteva! </body>
</html>
]]
```

Automatic conversion with the best effort when doing numeric operations in mix with strings:

```
print("10" + 1) --> 11
print("5" * "6") --> 30
print("hello" + 1) --> error
```

Conversely, it also tries to convert numbers to string: `print(10 .. 20)` prints a string with value "1020".

However `10 == "10"` is always `false`. Explicit conversion can be done with `tonumber` and `tostring` which convert or return nil in case of errors.



