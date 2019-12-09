---
title: Using Screen Command on Linux | How this helps and Why you should use it?
layout: post
author: alonshrestha
categories:
- Linux
- CentOS 8
- screen
- virtual
- tech
- tech tips
- Linux tips
image: assets/images/blog/2019-12-08/1.png
featured: true
---

Screen command on Linux is a useful utility for those people who work on multiple screen using SSH session. This command allows you to open multiple session in a terminal even if you are not in a graphical session. This also allows you to share a session with other users or to attach and detach to a remote terminal session. Screen command is used when you need to perform a long-running task on a remote machine.
# Installing Screen
**Debian base system**
{%highlight ruby%}
[stechalon@localhost ~]$ sudo apt-get install screen
{%endhighlight%}

**RedHat base system**
{%highlight ruby%}
[stechalon@localhost ~]$ sudo yum install screen
{%endhighlight%}

After completing installation check its version by typing `screen -v`
{%highlight ruby%}
[stechalon@localhost ~]$  screen -v
Screen version 4.01.00devel (GNU) 2-May-06
{%endhighlight%}

> **Table Of Content**

* TOC
{:toc}
# Useful Screen Command

|Wildcards  | Explanation  |
|---|---|
| Ctrl+a - c |  Create a new window |
| Ctrl+a - n |  Goes to the next window |
| Ctrl+a - " | List all windows |
| Ctrl+a - Ctrl+a |  Goes back to last used window |
| Ctrl+a - n |  Goes to the next windows |
| Ctrl+a - k | Kills the current windows |
| Ctrl+a - 0,1| Switch to window 0 ,1|
| Ctrl+a - (Shift+\ ) |  Divides region into  two vertical regions |
| Ctrl+a - S | Divides region into  two horizontal regions |
| Ctrl+a - tab | Change input to next region |
| Ctrl+a - A | Rename current window |
| Ctrl+a - Q | Close all region except current one |
| Ctrl+a - X | Close current region |
| Ctrl+a - d | Detach the session without sopping  event |
| Ctrl+a - r | Reattach the detach session |
| Ctrl+a - ] | Reattach the detach session |
| Ctrl+a - [ | Reattach the detach session |

# Working with Screen Command
## Starting Screen
To star a screen type `screen` command.
{%highlight ruby%}
[stechalon@localhost ~]$ screen
{%endhighlight%}

## Starting Screen with Session Name
To star a screen with session name type `screen -S session_Name` command.
{%highlight ruby%}
[stechalon@localhost ~]$ screen -S top
{%endhighlight%}

## Show Screen Parameter

Type `Ctrl+a - ? ` to show screen parameter.

{%highlight ruby%}
                       Screen key bindings, page 1 of 2.

                       Command key:  ^A   Literal ^A:  a

  break       ^B b         license     ,            removebuf   =
  clear       C            lockscreen  ^X x         reset       Z
  colon       :            log         H            screen      ^C c
  copy        ^[ [         login       L            select      '
  detach      ^D d         meta        a            silence     _
  digraph     ^V           monitor     M            split       S
  displays    *            next        ^@ ^N sp n   suspend     ^Z z
  dumptermcap .            number      N            time        ^T t
  fit         F            only        Q            title       A
  flow        ^F f         other       ^A           vbell       ^G
  focus       ^I           pow_break   B            version     v
  hardcopy    h            pow_detach  D            width       W
  help        ?            prev        ^H ^P p ^?   windows     ^W w
  history     { }          quit        \            wrap        ^R r
  info        i            readbuf     <            writebuf    >
  kill        K k          redisplay   ^L l         xoff        ^S s
  lastmsg     ^M m         remove      X            xon         ^Q q

                  [Press Space for next page; Return to end.]

{%endhighlight%}

## Show List of Screen Running in Background
{%highlight ruby%}
[stechalon@localhost ~]$ screen -ls
There are screens on:
        3784.top        (Attached)
        2077.pts-0.localhost    (Detached)
2 Sockets in /var/run/screen/S-alon.
{%endhighlight%}

## Detach Screen 
Type `screen -d ID` so that this can be reattach in future.

{%highlight ruby%}
[stechalon@localhost ~]$ screen -d 3784
{%endhighlight%}

## Reattach Screen 
Type `screen -r ID` for the screen which was previously detached.

{%highlight ruby%}
[stechalon@localhost ~]$ screen -r 2077
{%endhighlight%}

{% include summaryCallout.html heading= "Summary" content= "In this article, you learned about screen command on Linux. Please feel free to write me if you need any help." %}