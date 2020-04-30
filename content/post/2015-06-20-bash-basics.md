---
layout: post
title: "bash basics linux"
modified: 2015-06-20
excerpt: "bash basics linux"
tags: [bash, basics, linux]
comments: true
---

### Bash Basics

  * Learn basic Bash. Actually, type man bash and at least skim the whole thing; it's pretty easy to follow and not that long.
    Alternate shells can be nice, but Bash is powerful and always available (learning only zsh, fish, etc., while tempting on your own laptop, restricts you in many situations, such as using existing servers).

  * Learn at least one text-based editor well. Ideally Vim (vi), as there's really no competition for random editing in a
    terminal (even if you use Emacs, a big IDE, or a modern hipster editor most of the time).

  * Learn about stdout and stderr also learn about redirection of output and input using > and < and pipes using "|" 
  
  * Learn about file glob expansion with * (and perhaps ? and {...}) and quoting and the difference between double " and single ' quotes.
    (See more on variable expansion below.)

  * Be familiar with Bash job management: &, ctrl-z, ctrl-c, jobs, fg, bg, kill, etc.

  * Know ssh, and the basics of passwordless authentication, via ssh-agent, ssh-add, etc.

  * Basic file management: ls and ls -l (in particular, learn what every column in ls -l means), less, head, tail and
    tail -f (or even better, less +F), ln and ln -s (learn the differences and advantages of hard versus soft links),
    chown, chmod, du (for a quick summary of disk usage: du -sk *), df, mount.

  * Basic network management: ip or ifconfig, dig.

  * Know regular expressions well, and the various flags to grep/egrep. The -i, -o, -A, and -B options are worth knowing.

  * Learn to use apt-get, yum, or dnf (depending on distro) to find and install packages. And make sure you have pip to 
    install Python-based command-line tools (a few below are easiest to install via pip).


  For More : [Source](https://github.com/jlevy/the-art-of-command-line)

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>