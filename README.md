# Introduction

`Lua-ApLo.tmbundle` provides support for Lua syntax checking and running of Lua scripts. It requires [`ApLo.tmbundle`](https://github.com/gknops/aplo.tmbundle).

**NOTE**: this bundle does NOT replace the standard Lua bundle, you still need that for the language definition etc.

## Syntax Check

The Lua syntax check is tied to `callback.document.did-save` semantic class and the `source.lua` scope, so it will check any Lua file on save.

![LuaSyntaxCheck](https://github.com/gknops/Lua-ApLo.tmbundle/raw/master/LuaSyntaxCheck.png)


## Run

Running a Lua script using this bundle will create 'clickable' log output if the messages are formatted in a specific way (see the *DEBUG output* section below).

![LuaRun](https://github.com/gknops/Lua-ApLo.tmbundle/raw/master/LuaRun.png)


# Installation

Open a terminal window and enter these commands:

	cd ~/Library/Application\ Support/Avian/Bundles
	git clone --recursive git://github.com/gknops/Lua-ApLo.tmbundle.git


# .tm_properties variables

You can control some functions of this plugin by defining variables in a `.tm_properties` file, either in your home directory, the project directory or anywhere else `.tm_properties` files are allowed at.


## APLO\_LUA\_SCRIPT

By default *Run* will attempt to run the current file. By setting `APLO_LUA_SCRIPT` somewhere upstream you can force the given script to run instead. This is useful if you are working on modules.


# DEBUG output

Here is a handy Lua function that will produce 'clickable' debug output from your script when using this bundle:

	function dprint(msg)
	
		if DEBUG then
			local info=debug.getinfo(2)
			local file=info.source
			
			print(string.format('%s:%d: %s',file,info.currentline,msg))
			io.stdout:flush()
		end
	
	end

