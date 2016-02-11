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
```

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

Regular expressions are escaped using `%`. e.g. `string.match("10.15.3",6 "%.")`

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

### Tables

Python equivalent of map. Lua uses tables to represent ordinary arrays, symbol tables, sets, records, queues and other data structures. Packaes are also represented by tables. To Lua `io.read` means use the `read` entry from `io` table. 

```
-- Empty table
a = {} 

-- Creating arrays. Index starts at 1.
days = {"Tuesday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday"}
first = days[1]

-- Create a Record. Following two lines are equivalent.
point = {x=0, y=0}
points = {}; point.x = 0; point.y = 0

-- Tables are pretty much mutable
nums = {"One", "Two", "Three"}
nums.lang = "English"
num[4] = "Four"
```

The initialization of tables can be mix record and list style intialization at the same time:

```
video_comments = {url="https://www.youtube.com/watch?v=jNQXAC9IVRw", views=835412817,
             "first comment on youtube ever",
             "internet explorer finally loaded this video",
             "why is this his ONLY video in 10 years why hasnt he uploaded more?",
             "say hello if you are watching in february 2016﻿"
           }
```

The record initialization syntax requires proper identifier names for keys and hence disallows using negative indices, abitrary indices and non-variable name identifiers. To overcome this, there is special syntax:

`a = { [-273] = "absolute zero", ["-"] = "sub", ["+"] = "add", [100] = "Century" }`

This may be used to make arrays start at zero index:

`nums = { [0] = "Zero", "One", "Two", "Three" }`

Semicolons can also be used in place of commas. They are usually used to separate record for its last apart.

`{x=10, y=45; "one", "two", "three"}`

Getting the size of the table, or the len() equivalent of Python:

`table.getn(t)` or using the length operator introduced in 5.1: `#t`

Appending at the end of array:

`table.insert(t, val)` to `t[#t+1] = val` 

## Expressions

### Relational and logical operators

`< > <= >= == ~=`, all of them return true or false. `~=` is the negation of equality.

Lua compares tables, userdata and function by reference. Lua compares strings in alphabetical order which follows the locale set for Lua. Order comparison results in error. e.g.: `2 < "15" -- error`.

`and`, `or` and `not` are the logical operators. They consider `false` and `nil` as false and everything else as `true`. Short-circuit evaluation is used. `and` returns its first argument if it is false, otherwise second argument. For `or`, it is converse. e.g.

```
print (4 or 5) -- 4
print (4 and 5) -- 5
```

Useful idiom: `x = x or v`

### Concatenation

Concatenation is denoted by two dots `..`. If any operand is a number, it is converted to a string.

```
print(0 .. 1) -- 01
print("Hello" .. "world") -- helloworld
```

## Packages

Lua does not provide an explicit mechanism for packages but they can be implemented using other language features. by representing each package by a table, the way standard libraries do. There are several different methods to write a package.

A simple way is to use table and declare each ofthe methods as a new package. Using local variable not exposed outside and making a global package name alias to that local variable drops the requirement of explicitly prefixing everything with the package name.

```
local P = {}
complex = P

function P.new (r, i) 
  return {r=r, i=i}
end

-- defines a constant 'i'
P.i = P.new(0, 1)

-- Function internal to the package
local function checkComplex (c)
  if not ( type(c) == "table" and tonumber(c.r) and tonumber(c.i)) then
    error("bad complex number", 3)
  end
end

-- Adds two complex numbers
function P.add(c1, c2)
  checkComplex(c1)
  checkComplex(c2)
  return P.new(c1.r + c2.r, c1.i + c2.i)
end

--...similarly other functions...--

```

Now we can use any complex operation like this:

`c = complex.add(complex.i, complex.new(100,200))`

An alternative is to make all functions local then export them using a table:

```
local function new (r, i)
  return {r=r, i=i}
end

local function add(c1, c2)
  return new(c1.r+c2.r, c1.i+c2.i)
end

--...

complex = {
  new = new,
  add = add,
  sub = sub,
  mul = mul,
  div = div
}
```
