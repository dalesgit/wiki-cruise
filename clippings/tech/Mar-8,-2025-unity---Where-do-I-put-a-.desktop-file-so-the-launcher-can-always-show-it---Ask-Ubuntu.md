---
created: Mar 8, 2025, 7:31 AM
title: unity - Where do I put a .desktop file so the launcher can always show it? - Ask Ubuntu
tags: unity,launcher,unity,launcher
source: https://askubuntu.com/questions/173958/where-do-i-put-a-desktop-file-so-the-launcher-can-always-show-it
description: unity - Where do I put a .desktop file so the launcher can always show it? - Ask Ubuntu
author: 
published: 12 years, 7 months ago
---




#  [Where do I put a .desktop file so the launcher can always show it?](https://askubuntu.com/questions/173958/where-do-i-put-a-desktop-file-so-the-launcher-can-always-show-it) 
AskedModified [10 years, 6 months ago](https://askubuntu.com/questions/173958/where-do-i-put-a-desktop-file-so-the-launcher-can-always-show-it?lastactivity) Viewed                        18k times
                    This question shows research effort; it is useful and clear19        This question does not show any research effort; it is unclear or not usefulSave this question. [ ](https://askubuntu.com/posts/173958/timeline)Show activity on this post.
I recently installed e-Sword on my 12.04 Unity laptop. The installation creates a desktop icon of the application. I dragged the icon to the launcher and the icon was created in the launcher. But, when I move the desktop icon to trash, the launcher icon also disappears. What I need to do to delete the desktop icon without the launcher icon disappearing?
-  [unity](https://askubuntu.com/questions/tagged/unity) 
-  [launcher](https://askubuntu.com/questions/tagged/launcher) 
Follow this question to receive notifications                            Get updates on questions and answers
                         [edited Aug 9, 2012 at 19:35 ](https://askubuntu.com/posts/173958/revisions) [ ](https://askubuntu.com/users/235/jorge-castro) [Jorge Castro](https://askubuntu.com/users/235/jorge-castro) 73.3k            asked Aug 9, 2012 at 19:10 [ ](https://askubuntu.com/users/51325/williepabon) [williepabon](https://askubuntu.com/users/51325/williepabon) williepabon327


##                                         5 Answers
                                    
This answer is useful22        This answer is not usefulSave this answer. [ ](https://askubuntu.com/posts/173965/timeline)Show activity on this post.
> **You can copy the .desktop into  `~/.local/share/applications`**
Basically you're doing the end steps of this:
-  [How can I edit/create new launcher items in Unity by hand?](https://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand) 

After this the application will show up in the Dash, then you can either drag it to the launcher or run it and right click "Lock to Launcher".Follow this answer to receive notifications [edited Apr 13, 2017 at 12:24 ](https://askubuntu.com/posts/173965/revisions) [ ](https://askubuntu.com/users/-1/community) [Community](https://askubuntu.com/users/-1/community) Bot1            answered Aug 9, 2012 at 19:36 [ ](https://askubuntu.com/users/235/jorge-castro) [Jorge Castro](https://askubuntu.com/users/235/jorge-castro) Jorge Castro73.3k2This answer is useful1        This answer is not usefulSave this answer. [ ](https://askubuntu.com/posts/173962/timeline)Show activity on this post.
Right click the icon on the Launcher, and choose Keep in Launcher

![enter image description here](https://i.sstatic.net/SrsaD.jpg) Follow this answer to receive notifications [edited Jul 1, 2014 at 14:43 ](https://askubuntu.com/posts/173962/revisions) [ ](https://askubuntu.com/users/235/jorge-castro) [Jorge Castro](https://askubuntu.com/users/235/jorge-castro) 73.3k            answered Aug 9, 2012 at 19:18 [ ](https://askubuntu.com/users/49189/lnxslck) [LnxSlck](https://askubuntu.com/users/49189/lnxslck) LnxSlck12.4kThis answer is useful0        This answer is not usefulSave this answer. [ ](https://askubuntu.com/posts/173988/timeline)Show activity on this post.
Work around. Moved the desktop icon to the e-Sword folder created on my home folder by the installation, and from there, I dragged and drop to the Launcher.Follow this answer to receive notifications            answered Aug 9, 2012 at 20:38 [ ](https://askubuntu.com/users/51325/williepabon) [williepabon](https://askubuntu.com/users/51325/williepabon) williepabon327This answer is useful0        This answer is not usefulSave this answer. [ ](https://askubuntu.com/posts/490406/timeline)Show activity on this post.
desktop files are stored: globally in /usr/share/applications, locally in ~/.local/share/applications. You can use the below format to create a .desktop file for your app using a text-editor:

```
[Desktop Entry]
Encoding=UTF-8
Name=PyCharm 3.0
Comment=Jetbrains Python IDE
Exec=/home/sysadmin/programs/pycharm-community-3.0/bin
Icon=/home/sysadmin/programs/pycharm-community-3.0/bin/pycharm.png
Categories=Application;Development;Python;IDE
Version=1.0
Type=Application
Terminal=0

```


Alternatively, you may do a "unix sacrilege", and use one of those GUI tools out there! Once you've created the .desktop file in the corresponding path, you may find it though the dash. To make it stick permanently to the launcher, just right-click and say "Lock to Launcher" as LnxSlck has mentionedFollow this answer to receive notifications            answered Jul 1, 2014 at 14:54 [ ](https://askubuntu.com/users/49938/prahlad-yeri) [Prahlad Yeri](https://askubuntu.com/users/49938/prahlad-yeri) Prahlad Yeri1,657This answer is useful0        This answer is not usefulSave this answer. [ ](https://askubuntu.com/posts/513928/timeline)Show activity on this post.
arronax is a great gui tool for creating application launchers and it allows you add the icon, description, etc then pressing the menu down arrow button it create the .desktop file for you.    All you have to do is move it to its permanent location.
 [http://www.florian-diesch.de/software/arronax/](http://www.florian-diesch.de/software/arronax/) 
There's 3 .deb files on the arronax site which you have to download and install w/ sw center, gdebi or synaptic.   And I forget the order but you do it in a certain sequence.
It works really well though.Follow this answer to receive notifications            answered Aug 20, 2014 at 18:10 [ ](https://askubuntu.com/users/89063/bmullan) [bmullan](https://askubuntu.com/users/89063/bmullan) bmullan774


## Not the answer you're looking for? Browse other questions tagged 
-  [unity](https://askubuntu.com/questions/tagged/unity) 
-  [launcher](https://askubuntu.com/questions/tagged/launcher) 
 or  [ask your own question](https://askubuntu.com/questions/ask) .                                
