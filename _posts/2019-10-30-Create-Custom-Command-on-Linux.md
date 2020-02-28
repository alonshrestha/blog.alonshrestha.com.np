---
title: Create Custom Commands in Linux
layout: post
author: alonshrestha
categories:
- Linux
- Shell
- Command
- Bash
- Tech
- Custom Command
- Tech Tips
- aliases
- ubuntu 
- kali linux
- centos
image: assets/images/blog/2019-10-30/1.png
---

Linux provides users to create custom commands on the terminal. This allows users to execute the command in terminal and function according to the need. For custom command Linux uses `aliases` command type.

# Aliases
This kind of commands are set by user as their need. Some aliases are provided by default on Linux.  You can find the overview of command `alias` in your shell by typing alias.

**Example**
{% highlight ruby %}

[alon@localhost ~]$ alias
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'


{% endhighlight %}

You can create your own alias. For that, follow this syntax `alias yourCommand ` = `commandYouWantToReplace `.

**Example**
{%highlight ruby%}
[alon@localhost ~]$ alias move=mv
[alon@localhost ~]$ move testFile /tmp/
[alon@localhost ~]$ alias mv=move
{%endhighlight%}

**Example**
{%highlight ruby%}
[alon@localhost ~]$ alias testPrint=echo
[alon@localhost ~]$ testPrint This is blog.alonshrestha.com.np
This is blog.alonshrestha.com.np
{%endhighlight%}

{% include summaryCallout.html heading= "Summary" content= "In this article, you learned how to create custom command on Linux. Please feel free to write me if need any help." %}