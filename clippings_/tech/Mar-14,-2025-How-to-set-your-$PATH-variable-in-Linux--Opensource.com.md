---
created: Mar 14, 2025, 8:10 AM
title: How to set your $PATH variable in Linux | Opensource.com
tags: Our latest Linux articles,How-tos and tutorials,Linux
source: https://opensource.com/article/17/6/set-path-linux
description: Telling your Linux shell where to look for executable files is easy, and something everyone should be able to do.
author: Jason B
published: |
---


![A path through nature](https://opensource.com/sites/default/files/lead-images/set-your-path.png) Image by: 
Thomas Hendele on Pixabay (CC0). Modified by Opensource.com. CC BY-SA 4.0.
Being able to edit your  **$PATH**  is an important skill for any beginning  [POSIX](https://opensource.com/article/19/7/what-posix-richard-stallman-explains)  user, whether you use  [Linux](https://opensource.com/resources/linux) ,  [BSD](https://opensource.com/article/19/3/netbsd-raspberry-pi) , or macOS.
When you type a command into the command prompt in Linux, or in other Linux-like operating systems, all you're doing is telling it to run a program. Even simple commands, like  **ls** , ****  **mkdir** ,  **rm** , and others are just small programs that usually live inside a directory on your computer called  **/**  **usr**  **/bin** . There are other places on your system that commonly hold executable programs as well; some common ones include  **/**  **usr**  **/local/bin** ,  **/**  **usr**  **/local/**  **sbin** , and  **/**  **usr**  **/**  **sbin** . Which programs live where, and why, is beyond the scope of this article, but know that an executable program can live practically anywhere on your computer: it doesn't have to be limited to one of these directories.
Skip to content
When you type a command into your Linux shell, it doesn't look in every directory to see if there's a program by that name. It only looks to the ones you specify. How does it know to look in the directories mentioned above? It's simple: They are a part of an environment variable, called  **$PATH** , which your shell checks in order to know where to look.


## View your PATH

Sometimes, you may wish to install programs into other locations on your computer, but be able to execute them easily without specifying their exact location. You can do this easily by adding a directory to your  **$PATH** . To see what's in your  **$PATH**  right now, type this into a terminal:

```
echo $PATH
```


You'll probably see the directories mentioned above, as well as perhaps some others, and they are all separated by colons. Now let's add another directory to the list.


## Set your PATH

Let's say you wrote a little shell script called  **hello.sh**  and have it located in a directory called  **/place/with/the/file** . This script provides some useful function to all of the files in your current directory, that you'd like to be able to execute no matter what directory you're in.
Simply add  **/place/with/the/file**  to the  **$PATH**  variable with the following command:

```
export PATH=$PATH:/place/with/the/file
```


You should now be able to execute the script anywhere on your system by just typing in its name, without having to include the full path as you type it.


## Set your PATH permanently

But what happens if you restart your computer or create a new terminal instance? Your addition to the path is gone! This is by design. The variable  **$PATH**  is set by your shell every time it launches, but you can set it so that it always includes your new path with every new shell you open. The exact way to do this depends on which shell you're running.
Not sure which shell you're running? If you're using pretty much any common Linux distribution, and haven't changed the defaults, chances are you're running Bash. But you can confirm this with a simple command:

```
echo $0
```


That's the "echo" command followed by a dollar sign ($) and a zero.  **$0 ** represents the zeroth segment of a command (in the command  **echo $0** , the word "echo" therefore maps to $1), or in other words, the thing running your command. Usually this is the  [Bash shell](https://opensource.com/resources/what-bash) , although there are others, including Dash,  [Zsh](https://opensource.com/article/19/9/getting-started-zsh) , Tcsh, Ksh, and  [Fish](https://opensource.com/article/20/3/fish-shell) .
For Bash, you simply need to add the line from above, ** export PATH=$PATH:/place/with/the/file** , to the appropriate file that will be read when your shell launches. There are a few different places where you could conceivably set the variable name: potentially in a file called  **~/.bash_profile** ,  **~/.bashrc** , or  **~/.profile.**  The difference between these files is (primarily) when they get read by the shell. If you're not sure where to put it,  **~/.bashrc**  is a good choice.
For other shells, you'll want to find the appropriate place to set a configuration at start time; ksh configuration is typically found in  **~/.kshrc** , zsh uses  **~/.zshrc** . Check your shell's documentation to find what file it uses.
This is a simple answer, and there are more quirks and details worth learning. Like most everything in Linux, there is more than one way to do things, and you may find other answers which better meet the needs of your situation or the peculiarities of your Linux distribution. Happy hacking, and good luck, wherever your  **$PATH**  may take you.
--- 

 *This article was originally published in June 2017 and has been updated with additional information by the editor.* What to read nextThis work is licensed under a Creative Commons Attribution-Share Alike 4.0 International License.