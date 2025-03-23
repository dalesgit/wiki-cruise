---
created: Mar 14, 2025, 8:07 AM
title: Linux Fu: Use The Source (Command), Luke | Hackaday
tags: Hackaday Columns,Linux Hacks,bash,linux,shell script
source: https://hackaday.com/2025/03/13/linux-fu-use-the-source-command-luke/
description: Linux Fu: Use The Source (Command), Luke | Hackaday
author: Al Williams
published: March 13, 2025 at 11:14 am
---

You can argue if bash is a good programming language or not, but you can’t argue that it is a programming language. However, there are a few oddities about it that make it different from most other languages you probably know. For one thing, variables are dynamically scoped. Second, you can easily change variables in an upper scope. This leads to a problem when you want to do something like reset your path:
|123| `#!/bin/bash`  `PATH=`  `/usr/bin`  `:`  `/bin` |
|---|--------------------------------------------------|

Well, actually, it does work; it just doesn’t work the way you imagine it might. The key is to realize that when you execute our script (say, resetpath), a new copy of bash runs. It inherits all the variables from your shell. Now the script sets PATH for the new copy of bash. Anything else you run in that script will see your change. But when the script exits, the new copy of bash is gone and the old copy sees the same old PATH it always did.

Sometimes, this is a benefit, similar to “call by value” in other languages. However, what if you want to influence things? What’s more is that the situation is just the opposite within bash functions. For example:
|1234567891011121314151617| `#!/bin/bash`  `b() {`  ``  `echo`  `B: $x`  ``  `x=200`  `}`  `a() {`  ``  `x=100`  ``  `b`  ``  `echo`  `A: $x`  `}`  `a` |
|-------------------------|-----------------------------------------------------------------------------------------------|

Function b has no difficulty reading and even setting variable x.


## The Answer, Of  ~~Source~~  Course

The answer to the first problem is to use the source command (which can be either the word source or a single period). This tells bash to avoid running a new interpreter and just pretend you’d entered all the lines in a file from the console.
This is great sometimes. Our resetpath script will actually work just fine with either of these commands:
|12| `source`  `resetpath`  `. resetpath` |
|--|---------------------------|

You don’t even need the #! line, although it doesn’t hurt. However, there are a few problems.


## The Catches

First, if you exit, then you exit the entire shell, not something you probably meant to do. Second, you wind up polluting the variable space of the parent. For example, if your script creates a function X, with a regular shell script, that function goes away as soon as your script stops. With a source script, function X now will live forever unless you do something about it.
Neither of these problems are insurmountable, of course, and you’ll see a few ways to address it in the example code in this post.


## A Simple Example

If you spend a lot of time on the command line, you might want to have shortcut names for directories. What’s more, you might want to execute a little script when you go to particular directories or even when you leave them.
My plan is to keep a simple file in ~/.proj_dirs. To keep things simple, I’m assuming you can figure out the bash format:
|1234| `PROJ_DIRS[`  `"docs"`  `]=`  `"~/library/documents"`  `PROJ_DIRS[`  `"video"`  `]=`  `"~/library/videos"`  `PROJ_DIRS[`  `"arduino"`  `]=`  `"/home/alw/projects/embedded/Arduino"`  `. . .` |
|----|-------------------------------------------------------------------------------------------------------------------------------------------|

The eventual goal is to replace the cd command (or, at least, allow for that). However, it would be a pain to have to write something like “source pcd arduino” every time.


## The Alias Solution

The answer is pretty simple. You can create a script that can install itself as an alias. Here’s the basic flow:
|12345678910111213141516171819| `#!/bin/bash`  `if`  `[ `  `"$1"`  `== `  `"--__install"`  `] `  `then`  ``  `aname=`  `"$2"`  ``  `if`  `[ `  `"$aname"`  `== `  `""`  `] `  ``  `then`  ``  `aname=`  `"pcd"`  ``  `fi`  ``  `echo`  `-n `  `"alias '$aname'='source "`  ``  `aname=$(realpath -s `  `"$0"`  `)`  ``  `echo`  `"$aname'"`  ``  `exit`  `0 `  `fi`  `...` |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

The idea is that if you run as a regular script with –__install, it returns the alias command. You can then eval that in, for example, a startup script (like .bashrc or .profile), and then you’ll have the alias you want. By default, the code uses pcd, although you can set up any name you like on the command line. You could even create an alias for cd if you wanted to do that.


## Why Not Automatic?

You could, of course, detect if you were running normally or as a source automatically. Turns out this is somewhat finicky across shells, although if you are sure you are always using real bash, it is feasible. For example:
|1234| `if`  `[[ `  `"${BASH_SOURCE[0]}"`  `== `  `"$0"`  `]]`  `then`  ``  `echo`  `I am not sourced!`  `fi` |
|----|-------------------------------------------------------------------|



## Variables

Once you have the basic framework, it is easy to write the scripts to read the “database” (also using source) and do the actual work. However, there is a slight problem. Once you produce all the variables you need to do the work, it leaves all that pollution in your shell’s namespace.
Of course, you could write a function to clean up everything you use, but that’s a pain and error prone, too. A better idea is to write your code in a bash function. Then you can use local variables that will go away when the function returns. That leaves you with just your function to clear up with unset.
That leads to this simple framework:
|12345678910111213141516171819202122232425262728293031323334353637383940| `#!/bin/bash`  `if`  `[[ `  `"${BASH_SOURCE[0]}"`  `== `  `"$0"`  `]]`  `then`  ``  `if`  `[ `  `"$1"`  `== `  `"--__install"`  `] `  ``  `then`  ``  `aname=`  `"$2"`  ``  `if`  `[ `  `"$aname"`  `== `  `""`  `]`  ``  `then`  ``  `aname=`  `"pcd"`  ``  `fi`  ``  `echo`  `-n `  `"alias '$aname'='source "`  ``  `aname=$(realpath -s `  `"$0"`  `)`  ``  `echo`  `"$aname'"`  ``  `exit`  `0`  ``  `fi`  ``  `echo`  `"You must source this script"`  ``  `exit`  `1`  `fi`  `main() {`  `. . .`  `}`  `go() {`  ``  `local`  `tmprv`  ``  `main `  `"$@"`  ``  `tmprv=$?`  ``  `unset`  `main, go`  ``  `return`  `$tmprv`  `}`  `go `  `"$@"`  `return`  `$?` |
|-----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

The very bottom calls the  **go**  function, which calls your main function. Then the go function destroys your main function and itself. If you create new functions that you don’t want to keep around, you’ll need to destroy them yourself. Besides, you might be creating functions you want to keep, so the framework can’t decide.


## The Whole Thing

You can find the entire example on  [GitHub](https://gist.github.com/wd5gnr/c5681f2f7072938d5d7afe7a1e3e9132) . Outside of the management of the alias and the variable scope, the script is unremarkable. Note the optional scripts in the directories (.dir_enter and .dir_exit) are sourced also, so they only need to be readable (-r) not executable (-x).
The only other nuance is that if you enter anything as a directory that the program doesn’t recognize, it assumes it is an actual directory, so you can use this to replace the cd command entirely if you want.
Since the script can tell if it is sourced or not, it is possible to start in the source mode and then call yourself as a normal script to do work where that makes more sense. As usual with bash, there are lots of possibilities.
We talk about  [bash programming](https://hackaday.com/2017/07/21/linux-fu-better-bash-scripting/)  a lot around here.  [Debugging](https://hackaday.com/2019/12/11/linux-fu-debugging-bash-scripts/)  can be helpful, although they haven’t packaged the debugger for newer versions of bash lately.