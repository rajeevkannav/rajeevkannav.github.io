---
layout: post
title: "linuxbrew node nodejs npm on ubuntu"
modified: 2015-06-13
excerpt: "linuxbrew node nodejs npm on ubuntu"
tags: [linuxbrew, nodejs, npm, ubuntu]
comments: true
---

### Remove old “node” Package to Avoid Conflicts

Linuxbrew is a fork of [Homebrew](http://brew.sh/) , the Mac OS package manager, for Linux.

### Dependencies

   * Ruby 1.8.6 or newer
   * GCC 4.2 or newer
   * 64-bit x86 platform


    sudo apt-get install build-essential curl git m4 ruby texinfo libbz2-dev libcurl4-openssl-dev libexpat-dev libncurses-dev zlib1g-dev
    
###  Install Linuxbrew 

Paste at Terminal prompt:

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/linuxbrew/go/install)"

Add to your .bashrc or .zshrc:

    export PATH="$HOME/.linuxbrew/bin:$PATH"
    export MANPATH="$HOME/.linuxbrew/share/man:$MANPATH"
    export INFOPATH="$HOME/.linuxbrew/share/info:$INFOPATH"


then: 

    source ~/.bashrc


### update Linuxbrew  

Paste at a Terminal prompt:

        brew update
        brew doctor

### Install “node” Package 
    
     brew install node

### Confirm Installation 
 
    node -v # Output should be something like v0.12.4
    npm -v  # Output should be something like 2.10.1  

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>