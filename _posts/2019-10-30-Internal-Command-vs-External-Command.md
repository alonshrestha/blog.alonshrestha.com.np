---
title: Internal Command Vs External Command | Linux Shell
layout: post
author: alonshrestha
categories:
- Linux
- Shell
- Command
- Types
- Bash
- Internal Command
- External Command
- tech
- tech tips
- Linux tips
---

# Internal Command
This type of command is the part of the system which is already loaded in the system. They are independent and can be executed at any time from the memory. Execution of this command is assumed to be fast because of the shell builtin. Some of the examples of this are `cd`, `source`, `history`, `help`, `kill` etc. To see the list of  the builtin command type `help` in your shell. 

{%highlight ruby%}

[alon@localhost ~]$ help
GNU bash, version 4.2.46(2)-release (x86_64-redhat-linux-gnu)
These shell commands are defined internally.  Type `help' to see this list.
Type `help name' to find out more about the function `name'.
Use `info bash' to find out more about the shell in general.
Use `man -k' or `info' to find out more about commands not in this list.

A star (*) next to a name means that the command is disabled.

 job_spec [&]                                                                                                          history [-c] [-d offset] [n] or history -anrw [filename] or history -ps arg [arg...]
 (( expression ))                                                                                                      if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [ else COMMANDS; ] fi
 . filename [arguments]                                                                                                jobs [-lnprs] [jobspec ...] or jobs -x command [args]
 :                                                                                                                     kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
 [ arg... ]                                                                                                            let arg [arg ...]
 [[ expression ]]                                                                                                      local [option] name[=value] ...
 alias [-p] [name[=value] ... ]                                                                                        logout [n]
 bg [job_spec ...]                                                                                                     mapfile [-n count] [-O origin] [-s count] [-t] [-u fd] [-C callback] [-c quantum] [array]
 bind [-lpvsPVS] [-m keymap] [-f filename] [-q name] [-u name] [-r keyseq] [-x keyseq:shell-command] [keyseq:readlin>  popd [-n] [+N | -N]
 break [n]                                                                                                             printf [-v var] format [arguments]
 builtin [shell-builtin [arg ...]]                                                                                     pushd [-n] [+N | -N | dir]
 caller [expr]                                                                                                         pwd [-LP]
 case WORD in [PATTERN [| PATTERN]...) COMMANDS ;;]... esac                                                            read [-ers] [-a array] [-d delim] [-i text] [-n nchars] [-N nchars] [-p prompt] [-t timeout] [-u fd] [name ...]
 cd [-L|[-P [-e]]] [dir]                                                                                               readarray [-n count] [-O origin] [-s count] [-t] [-u fd] [-C callback] [-c quantum] [array]
 command [-pVv] command [arg ...]                                                                                      readonly [-aAf] [name[=value] ...] or readonly -p
 compgen [-abcdefgjksuv] [-o option]  [-A action] [-G globpat] [-W wordlist]  [-F function] [-C command] [-X filterp>  return [n]
 complete [-abcdefgjksuv] [-pr] [-DE] [-o option] [-A action] [-G globpat] [-W wordlist]  [-F function] [-C command]>  select NAME [in WORDS ... ;] do COMMANDS; done
 compopt [-o|+o option] [-DE] [name ...]                                                                               set [-abefhkmnptuvxBCHP] [-o option-name] [--] [arg ...]
 continue [n]                                                                                                          shift [n]
 coproc [NAME] command [redirections]                                                                                  shopt [-pqsu] [-o] [optname ...]
 declare [-aAfFgilrtux] [-p] [name[=value] ...]                                                                        source filename [arguments]
 dirs [-clpv] [+N] [-N]                                                                                                suspend [-f]
 disown [-h] [-ar] [jobspec ...]                                                                                       test [expr]
 echo [-neE] [arg ...]                                                                                                 time [-p] pipeline
 enable [-a] [-dnps] [-f filename] [name ...]                                                                          times
 eval [arg ...]                                                                                                        trap [-lp] [[arg] signal_spec ...]
 exec [-cl] [-a name] [command [arguments ...]] [redirection ...]                                                      true
 exit [n]                                                                                                              type [-afptP] name [name ...]
 export [-fn] [name[=value] ...] or export -p                                                                          typeset [-aAfFgilrtux] [-p] name[=value] ...
 false                                                                                                                 ulimit [-SHacdefilmnpqrstuvx] [limit]
 fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command]                                                      umask [-p] [-S] [mode]
 fg [job_spec]                                                                                                         unalias [-a] name [name ...]
 for NAME [in WORDS ... ] ; do COMMANDS; done                                                                          unset [-f] [-v] [name ...]
 for (( exp1; exp2; exp3 )); do COMMANDS; done                                                                         until COMMANDS; do COMMANDS; done
 function name { COMMANDS ; } or name () { COMMANDS ; }                                                                variables - Names and meanings of some shell variables
 getopts optstring name [arg]                                                                                          wait [id]
 hash [-lr] [-p pathname] [-dt] [name ...]                                                                             while COMMANDS; do COMMANDS; done
 help [-dms] [pattern ...]                                                                                             { COMMANDS ; }


{%endhighlight%}
# External Command
These commands are not built into the shell. For executing the `external command` shell needs to look for the `$PATH Variable` of the command. While executing the external command new process has to be release. These commands take more time to execute compared to internal command. Example of external command are `cat` , `mv` , `cp`, `less` etc.

{% include tip.html content= "You can find out whether a command is internal or external by `type` command. Eg: type cat " %}

**Example**
{%highlight ruby%}
[alon@localhost ~]$ type cat
mv is /usr/bin/cat
{%endhighlight%}

{% include summaryCallout.html heading= "Summary" content= "In this article, you learned difference about internal and external command on Linux. Please feel free to write me if need any help." %}