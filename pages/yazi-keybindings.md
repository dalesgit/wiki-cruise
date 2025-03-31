# Yazi Keyboard Shortcuts Quick Reference - Adamsdesk KB

https://kb.adamsdesk.com/application/yazi-keyboard-shortcuts/

An efficient, user-friendly and customizable fast terminal file manager that is written in Rust based upon non-blocking async input/output (i/o). The name "Yazi" means "duck".

The following is the default keyboard shortcuts or keybindings configuration (keymap.toml).

File Operations
-----------------------------------------------------


|Task                                 |Shortcut(s)  |Notes                                        |
|-------------------------------------|-------------|---------------------------------------------|
|Cancel Copy/Cut File(s)              |X            |                                             |
|Cancel Copy/Cut File(s)              |Y            |                                             |
|Change Directory with zoxide         |z            |                                             |
|Change Directory/Reveal File with fzf|Z            |                                             |
|Copy Directory Path                  |c + d        |                                             |
|Copy File Path                       |c + c        |                                             |
|Copy Filename                        |c + f        |                                             |
|Copy Filename Without Extension      |c + n        |                                             |
|Copy Selected File(s)                |y            |                                             |
|Create File/Directory                |a            |End with a / (slash) for directories.        |
|Cut Selected File(s)                 |x            |                                             |
|Delete Selected File(s) (trash)      |d            |                                             |
|Delete Selected File(s) Permanently  |D            |                                             |
|Open Selected File(s)                |Enter        |                                             |
|Open Selected File(s)                |o            |                                             |
|Open Selected File(s) Interactively  |Ctrl + Enter |Some terminals don't support it yet.         |
|Open Selected File(s) Interactively  |O            |                                             |
|Open Selected File(s) Interactively  |Shift + Enter|                                             |
|Paste File(s)                        |p            |                                             |
|Paste File(s)                        |P            |If file(s) existing in destination overwrite.|
|Rename Selected File(s)              |r            |                                             |
|Run a Shell Command                  |;            |                                             |
|Run a Shell Command                  |:            |Block until finishes.                        |
|Symlink Absolute Path Copied File(s) |-            |                                             |
|Symlink Hardlink Copied File(s)      |Ctrl + -     |                                             |
|Symlink Relative Path Copied File(s) |_            |                                             |
|Toggle Hidden File(s) Visibility     |.            |                                             |


Find Files
-------------------------------------------


|Task                                  |Shortcut(s)|Notes|
|--------------------------------------|-----------|-----|
|Cancel Ongoing Search                 |Ctrl + s   |     |
|Filter File(s)                        |f          |     |
|Find Next File                        |/          |     |
|Find Previous File                    |?          |     |
|Next Found Item                       |n          |     |
|Previously Found Item                 |N          |     |
|Search File(s) By Content with ripgrep|S          |     |
|Search File(s) By Name with fd        |s          |     |


Misc
-------------------------------



* Task: Help
  * Shortcut(s): ~
  * Notes: Display help screen.
* Task: Help
  * Shortcut(s): F1
  * Notes: Display help screen.
* Task: Quit
  * Shortcut(s): q
  * Notes: Quit Yazi application.
* Task: Quit Without Writing CWD File
  * Shortcut(s): Q
  * Notes: Quite Yazi application without writing current working directory file.
* Task: Suspend Process
  * Shortcut(s): Ctrl + z
  * Notes: 


Navigation
-------------------------------------------



* Task: Back Parent Directory
  * Shortcut(s): ←
  * Notes: 
* Task: Back Parent Directory
  * Shortcut(s): h
  * Notes: 
* Task: Back Parent Directory
  * Shortcut(s): H
  * Notes: 
* Task: Change Directory Config
  * Shortcut(s): g + c
  * Notes: Change to the config directory, "~/.config".
* Task: Change Directory Downloads
  * Shortcut(s): g + d
  * Notes: Change to the downloads directory, "~/Downloads".
* Task: Change Directory Home
  * Shortcut(s): g + h
  * Notes: Change to the home directory, "~/".
* Task: Change Directory Interactively
  * Shortcut(s): g + Spacebar
  * Notes: Change to the entered directory path.
* Task: Enter Directory Highlighted
  * Shortcut(s): →
  * Notes: 
* Task: Enter Directory Highlighted
  * Shortcut(s): l
  * Notes: 
* Task: Forward Next Directory
  * Shortcut(s): L
  * Notes: 
* Task: Move Cursor Bottom
  * Shortcut(s): G
  * Notes: 
* Task: Move Cursor Down
  * Shortcut(s): ↓
  * Notes: 
* Task: Move Cursor Down
  * Shortcut(s): j
  * Notes: 
* Task: Move Cursor Down Half Page
  * Shortcut(s): Ctrl + d
  * Notes: 
* Task: Move Cursor Down Half Page
  * Shortcut(s): Shift + Page Down
  * Notes: 
* Task: Move Cursor Down One-Page
  * Shortcut(s): Ctrl + f
  * Notes: 
* Task: Move Cursor Down One-Page
  * Shortcut(s): Page Down
  * Notes: 
* Task: Move Cursor Top
  * Shortcut(s): g + g
  * Notes: 
* Task: Move Cursor Up
  * Shortcut(s): ↑
  * Notes: 
* Task: Move Cursor Up
  * Shortcut(s): k
  * Notes: 
* Task: Move Cursor Up Half Page
  * Shortcut(s): Ctrl + u
  * Notes: 
* Task: Move Cursor Up Half Page
  * Shortcut(s): Shift + Page Up
  * Notes: 
* Task: Move Cursor Up One-Page
  * Shortcut(s): Ctrl + b
  * Notes: 
* Task: Move Cursor Up One-Page
  * Shortcut(s): Page Up
  * Notes: 
* Task: Move Down 5 Units (preview)
  * Shortcut(s): J
  * Notes: 
* Task: Move Up 5 Units (preview)
  * Shortcut(s): K
  * Notes: 


Selection
-----------------------------------------


|Task                    |Shortcut(s)|Notes                                          |
|------------------------|-----------|-----------------------------------------------|
|Cancel Selection        |Ctrl + [   |                                               |
|Cancel Selection        |Ctrl + c   |                                               |
|Cancel Selection        |Esc        |                                               |
|Select All Files        |Ctrl + a   |                                               |
|Select All Files Inverse|Ctrl + r   |                                               |
|Submit Selection        |Enter      |                                               |
|Toggle Selection        |Spacebar   |Toggle highlighted file or directory selection.|
|Visual Mode Off         |V          |The unset mode.                                |
|Visual Mode On          |v          |The selection mode.                            |


Sort View
-----------------------------------------


|Task                          |Shortcut(s)|Notes|
|------------------------------|-----------|-----|
|Sort Alphabetically           |, + A      |     |
|Sort By Creation Time         |, + c      |     |
|Sort By Creation Time Reverse |, + C      |     |
|Sort By File Extension        |, + e      |     |
|Sort By File Extension Reverse|, + E      |     |
|Sort By Modified Time         |, + m      |     |
|Sort By Modified Time Reverse |, + M      |     |
|Sort By Size                  |, + s      |     |
|Sort By Size                  |, + S      |     |
|Sort Naturally                |, + n      |     |
|Sort Naturally Reverse        |, + N      |     |
|Sort Randomly                 |, + r      |     |


Tab Management
---------------------------------------------------



* Task: New Tab
  * Shortcut(s): t
  * Notes: The new tab created uses the current working directory (CWD).
* Task: Switch Tab
  * Shortcut(s): 1 to 9
  * Notes: Switches to the desired tab, 1 to 9.
* Task: Switch Previous Tab
  * Shortcut(s): [
  * Notes: 
* Task: Switch Next Tab
  * Shortcut(s): ]
  * Notes: 
* Task: Swap Current Tab with Previous Tab
  * Shortcut(s): {
  * Notes: 
* Task: Swap Current Tab with Next Tab
  * Shortcut(s): }
  * Notes: 
* Task: Close Current Tab
  * Shortcut(s): Ctrl + c
  * Notes: If only one tab then quit application.


Task Manager
-----------------------------------------------


|Task             |Shortcut(s)|Notes                          |
|-----------------|-----------|-------------------------------|
|Cancel Task      |x          |                               |
|Close Window     |Ctrl + [   |                               |
|Close Window     |Ctrl + c   |                               |
|Close Window     |Esc        |                               |
|Close Window     |w          |                               |
|Inspect Task     |Enter      |                               |
|Move Cursor Down |↓          |                               |
|Move Cursor Down |j          |                               |
|Move Cursor Up   |↑          |                               |
|Move Cursor Up   |k          |                               |
|Show Task Manager|w          |Display a list of active tasks.|


Notable Directories & Files
---------------------------------------------------------------------------


|Path                      |Description                                       |
|--------------------------|--------------------------------------------------|
|~/.config/yazi            |Yazi user configuration files.                    |
|~/.config/yazi/flavors/   |Where pre-made Yazi themes are stored.            |
|~/.config/yazi/keymap.toml|Keybindings/keyboard shortcuts configuration file.|
|~/.config/yazi/plugins/   |Where Lua plugins are stored.                     |
|~/.config/yazi/theme.toml |Colour scheme configuration file.                 |
|~/.config/yazi/yazi.toml  |General configuration file.                       |


External Links
---------------------------------------------------

*   [Yazi](https://yazi-rs.github.io/)
*   [Yazi project](https://github.com/sxyazi/yazi)
*   [Yazi Documentation](https://yazi-rs.github.io/docs/installation)
*   [Yazi Documentation Keybindings](https://yazi-rs.github.io/docs/quick-start#keybindings)
*   [Yazi Keybinding Defaults (keymap.toml)](https://github.com/sxyazi/yazi/blob/shipped/yazi-config/preset/keymap.toml)

