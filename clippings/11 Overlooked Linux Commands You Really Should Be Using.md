---
created: 2025-04-01T11:07:24 (UTC +13:00)
tags: []
source: https://www.howtogeek.com/overlooked-linux-commands-you-should-be-using/
author: JT McGinty
---

# 11 Overlooked Linux Commands You Really Should Be Using

> ## Excerpt
> These commands could significantly enhance your workflow!

---
Beneath the surface of the well-known Linux commands lies a treasure trove of lesser-known utilities that can make your life easier, enhance your productivity, and even impress your fellow Linux users. Let's explore some of the most powerful but overlooked commands that deserve more attention.

## 1 rsync - The Smarter Alternative to cp and scp

Most people rely on cp to copy files, but rsync does the same job better. It’s faster, supports resume functionality, and can synchronize files across systems efficiently. It can also preserve file and directory attributes such as timestamps, permissions, and symlinks. It works great for everything from copying one file to backing up an entire file system.

rsync is installed on virtually all Linux systems by default. If it happens that it is not on your system, install with the following command:

```
        <code id="code-lang-xml">sudo apt install rsync  #Debian / Ubuntusudo dnf install rsync  #Red Hat / Fedora</code>
    
```

    ![A screenshot of the man page for the rsync utility.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/rsync-man-page.png)

Basic usage:

```
        <code id="code-lang-xml">#Copy a file or directoryrsync -av source/ destination/</code>
    
```

```
        <code id="code-lang-xml">#Copy over SSH with transfer compressionrsync -avz source/ user@remote:/destination</code>
    
```

```
        <code id="code-lang-xml">#Preview without moving anythingrsync --dry-run -av source/ destination/</code>
    
```

    [![Two terminals on a laptop screen, showing the man pages for the scp and rsync commands.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/wm/2024/11/two-terminals-on-a-laptop-screen-showing-the-man-pages-for-the-scp-and-rsync-commands.jpg)](https://www.howtogeek.com/how-to-transfer-files-between-systems-using-scp-and-rsync/)

Related

##### [How to Transfer Files Between Systems Using scp and rsync](https://www.howtogeek.com/how-to-transfer-files-between-systems-using-scp-and-rsync/ "How to Transfer Files Between Systems Using scp and rsync")

Either of these commands let you securely transfer files between computers, but there are good reasons to know them both.

## 2 bat - A Better cat

One of the first Linux command line tools most users learn about is cat. It's often used to print text files to the screen in a terminal. It is effective, but provides only very basic and mostly WYSIWYG output. bat is a powerful alternative that, among other things, provides syntax coloring for code, paging functionality, forward and backward scrolling, and much more.

Install with:

```
        <code id="code-lang-xml">sudo apt install batsudo dnf install bat</code>
    
```

    ![Sample output from the bat command in the Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/bat-command-output.png)

Basic usage:

```
        <code id="code-lang-xml">bat&nbsp;FileToRead.txt</code>
    
```

With bat open, you can maneuver easily using the arrow or page keys. Press H to see the full help and Q to quit back to a command prompt.

## 3 fd - A Faster, Smarter find

The find command is powerful but can quickly become overly-complicated if you want to go beyond fairly basic searches. The fd command is both faster and more intuitive, making it a great alternative.

Install with:

```
        <code id="code-lang-xml">sudo apt install fd-findsudo dnf install fd-find</code>
    
```

    ![Output from the fd command in a Linux terminal.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/fd-command-output.png)

Basic usage:

```
        <code id="code-lang-xml">#Search using regular expression pattern match#Matches pattern anywhere in name or pathfd "pattern" /search/pathfd ".log" /var/log</code>
    
```

```
        <code id="code-lang-xml">#Search using glob pattern matching#Matches using traditional wildcard notationfd -- glob "*.log"fd&nbsp;--glob "specific.file.txt"</code>
    
```

fd does a good job of combining powerful features and ease of use. If you're not very tech savvy, the --glob switch is most likely what you'll be looking for. For more advanced users, the ability to use regular expressions will allow you to find just about anything.

## 4 ncdu - A Better Disk Usage Analyzer

Most users go to the du command to check the condition of the overall disk usage on their system. It works fine if you just want to see how much space you have available but if you want to get into exactly what is using up that space, things become more difficult. That's where ncdu really shines.

Install with:

```
        <code id="code-lang-xml">sudo apt install ncdusudo dnf install ncdu</code>
    
```

    ![Output from the ncdu command in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/ncdu-terminal-output.png)

Basic usage:

```
        <code id="code-lang-xml">ncduncdu --help</code>
    
```

It will take a few moments for ncdu to scan your directory tree and set itself up the first time you run it. Subsequent runs will load significantly faster. You can hit the question mark key for help if you need it, but the interface is very intuitive. You'll quickly see what directories and files are taking up the most space on your system and can drill down as far as the tree goes.

    [![Hard drive connected to a USB adapter on a wooden surface.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2024/02/52975046360_2611d104fc_o.jpg)](https://www.howtogeek.com/how-to-use-ncdu-to-find-disk-hogging-directories-in-linux/)

Related

## 5 htop - A Better top

Most Linux users are quite familiar with the process viewer command top and there's a reason for that—it does what it does very well. There is, however, an alternative that improves on top both cosmetically and functionally. Let me introduce you to htop.

Install with:

```
        <code id="code-lang-xml">sudo apt install htopsudo dnf install htop</code>
    
```

    ![Output from the htop command in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/htop-terminal-output.png)

Basic usage:

```
        <code id="code-lang-xml">htophtop --help</code>
    
```

As you can see, htop adds color to its output, making it a bit easier to pick out the elements that interest you quickly. It also shows a bit more detail about your hardware by default. CPU, memory, and swap conditions are displayed by default. You can get a great idea of what's happening on your system with just a quick glance. Use the function keys to change settings, kill processes, and more.

    [![Konsole Terminal open on the Kubuntu Focus Ir14 Linux laptop.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2024/08/52972123178_c7bc15383d_o.jpg)](https://www.howtogeek.com/how-to-use-linux-htop-command/)

Related

## 6 column - Print Data in Neat, Aligned Columns

Have you ever found yourself looking at a file of comma, space, or semicolon-separated values, wishing there was a quick and easy way to organize it on the screen and make it easier to read? This is where column comes in. When you just need to get some quick information out of a file and don't want to actually process the data, column transforms your file into organized, easy-to-read tables right in the terminal.

This command should be available on virtually all Linux distributions with no need to install anything.

Here is an example of viewing a CSV file in the terminal with no extra formatting:

    ![Viewing an example CSV file in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/unformatted-csv-terminal-output.png)

    ![Output of the column command in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/column-terminal-output.png)

Basic usage:

```
        <code id="code-lang-xml"># Format data.txt into a tablecat data.txt | column -t#Format data into a table and run through morecat data.txt | column -t | more#Specify comma separator and make a tablecolumn&nbsp;-s, -t &lt; file.csv#Specify semicolon separator and make a tablecolumn&nbsp;-s; -t &lt; file.csv#Truncate data in column 1 if neededcolumn&nbsp;-s, -t&nbsp;--table-truncate 1 &lt; file.csv#See help for full explanation of switchesColumn --help</code>
    
```

You can get more out of column by piping its output into other tools or files. You can save the output as a new file or pipe it into more for the ability to move backward and forward through the data.

## 7 watch - Monitor Any Command in Real Time

The watch command will let you run any other command at specific time intervals (default of two seconds) and keep an eye on the output. It's perfect when you need to monitor some part of your system for changes.

The watch command should be available on all Linux distributions by default.

    ![Output from the watch df command in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/watch-df-command-terminal-output.png)

Basic usage:

```
        <code id="code-lang-xml">#Watch disk usagewatch df -h#Monitor directory for file changeswatch ls -l#Watch memory and highlight changeswatch -d free -m#Full helpwatch --helpman watch</code>
    
```

## 8 pv - A Progress Bar For Long-Running Commands

There are many Linux commands, such as cp and mv, that don't give any kind of useful output about their progress. If you're trying to manipulate large files or need to run other commands that can take some time to complete, you've undoubtedly found yourself in the "Is it actually doing anything?" situation. This is where pv comes in.

Install with:

```
        <code id="code-lang-xml">sudo apt install pvsudo dnf install pv</code>
    
```

    ![Example of pv output in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/pv-command-terminal-output.png)

Basic usage:

```
        <code id="code-lang-xml">#Monitor file copy progresspv source_file &gt; destination_file#Monitor file compression progresspv file_to_compress | gzip &gt; compressed_file.gz#Full help and usagepv --helpman pv</code>
    
```

    [![A command running in the Linux Terminal. ](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2024/01/52848912754_85c417d474_o.jpg)](https://www.howtogeek.com/428654/how-to-monitor-the-progress-of-linux-commands-with-pv-and-progress/)

Related

## 9 tldr - Simplified Manual Pages For Common Commands

The man pages built into Linux are a great resource when you need a detailed description of how something works and can be used. Sometimes, however, the information gets so detailed and complex that you end up more confused than when you started reading. That's where tldr comes in.

Install with:

```
        <code id="code-lang-xml">sudo apt install tldrsudo dnf install tldr</code>
    
```

    ![Sample output from the tldr command in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/tldr-terminal-output.png)

Basic usage:

```
        <code id="code-lang-xml">tldr tartldr cptldr &lt;any&nbsp;command&nbsp;here&gt;</code>
    
```

The tldr command works similar to man but it will give you simplified and more straightforward explanations. For most commands it also provides easy-to-understand command line examples to help you get through the most common tasks quickly.

## 10 eza - A Modernized ls Replacement

The directory listing command ls is probably the single most used command on any Linux system—and the oldest. eza gives the same basic functionality but adds many extras that enhance the experience of today's hyper productive power users.

Install with:

```
        <code id="code-lang-xml">sudo apt install ezasudo dnf install eza</code>
    
```

    ![Output from the exa command in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/exa-command-terminal-output.png)

Basic usage:

```
        <code id="code-lang-xml">#List all including hiddeneza --all#List tree structureeza --long --tree --level=3#List headers, icons, and Git statuseseza --long --header --icons --git#Helpeza --help</code>
    
```

For developers, analysts, and other power users, eza can quickly become an indispensable tool. It provides more meaningful information than its older counterpart and the color-coded output makes it easy to focus on exactly what you are looking for.

## 11 tree - View the Tree Structure of File Systems

The tree command will let you view the contents of any directory in a tree-like structure, allowing you to visualize the hierarchy of folders and files. It can be an effective tool to help keep things organized and in the right place.

Install with:

```
        <code id="code-lang-xml">sudo apt install treesudo dnf install tree</code>
    
```

    ![Output from the tree command in a Linux terminal](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/03/tree-terminal-output.png)

Basic usage:

```
        <code id="code-lang-xml">#Tree of current directorytree#Tree of specific directorytree /etc/#Help and usage:tree --helpman tree</code>
    
```

The tree command is a great tool to help you get a visual idea of the layout of any part of your file system. You can look at anything from the entire root directory down to collections of small personal files. It makes it easy to spot duplicated items, small directories that could be consolidated, and more.

___

One of the most appealing things about Linux is the abundance of alternatives and choices it makes available to everyone. It's normal to grow accustomed to the way you do things over time, but it never hurts to check out the alternatives once in a while. You just might find a hidden gem that will make a positive difference in your daily workflow.
