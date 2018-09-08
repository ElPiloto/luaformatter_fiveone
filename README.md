# Lua Formatter

**This is a fork of:**
https://github.com/LuaDevelopmentTools/luaformatter

with a **critical** patch to enable formatting from stdin from:

https://github.com/shuxiao9058/luaformatter

This library beautify Lua code:

* Indent block
* Indent expressions
* Trim trailing white spaces

It is plain _Lua 5.1_.

## Prerequisites

* Lua 5.1
* Metalua >= 0.7
* Penlight ~> 0.9

## Installation

```sh
$ luarocks install --local formatterfiveone
```

## How does it work?

### Library

```lua
$ lua
Lua 5.1.5  Copyright (C) 1994-2012 Lua.org, PUC-Rio
> formatter = require 'formatter'
> code = [[do
>> local var = 
>> 42
>> end]]
> formattedcode = formatter.indentcode(code, '\n', true, '  ')
> print( formattedcode )
do
  local var =
    42
end
```

### Command line

```sh
$ cat sample.lua
do
local var =
42
end
$ luaformatterfiveone sample.lua
do
  local var =
    42
end
```

Want more options?

```sh
$ luaformatterfiveone --help
Formats Lua code.
  -i, --stdin Read buffer from stdin.
  -a, --autosave Flush formatted Lua in given file instead of stdout.
  -s, --spaces (default 2) Spaces to use as indentation.
  -t, --tabs   (default 0) Tabulation(s) to use as indentation.
  -d, --delimiter (default unix) Type of new line to detect and use while formatting:
    * unix: '\n' LF Line feed.
    * windows: '\r\n' CR+LF
    * mac: '\r' CR Carriage Return of Macs before OSX.
  -h, --help This help.
  [files] Files to format.
```
