---
layout: post
title: "Uninstall and install node nodejs npm on ubuntu"
modified: 2015-06-12
excerpt: "Uninstall and install node nodejs npm on ubuntu Easy way"
tags: [node, nodejs, npm, ubuntu]
comments: true
---

### Remove old “node” Package to Avoid Conflicts

    $ dpkg --get-selections | grep node
    ax25-node                                       install
    node                                            install

If you found the old “node” package installed, run this command to completely remove it:
	
    sudo apt-get remove --purge node


<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-1411898088670168"
     data-ad-slot="3525987534"
     data-ad-format="auto"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>


### Install Node.js with Ubuntu Package Manager

To install Node.js, open a terminal and type the following command:

    sudo apt-get install nodejs 

Then install the Node package manager called “npm”:

    sudo apt-get install npm

Create a symbolic link for “node” as many Node.js tools use this name to execute.

    sudo ln -s /usr/bin/nodejs /usr/bin/node

Now we should have both the node and npm commands working:	

    $ node -v
    v0.10.25
    $ npm -v
    1.3.10

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-1411898088670168"
     data-ad-slot="3525987534"
     data-ad-format="auto"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

### Install Node.js with Maintained Ubuntu Packages

The process below is described here, too.

Add the Node.js maintained repositories to your Ubuntu package source list with this command:
	
    curl -sL https://deb.nodesource.com/setup | sudo bash -

Then install Node.js with apt-get:
	
    sudo apt-get install nodejs

Optionally we can create a symbolic link for “node” (for reasons mentioned earlier):
    
    sudo ln -s /usr/bin/nodejs /usr/bin/node

Using this install option, we end up with newer versions of “nodejs” and “npm”:
	
    $ node -v
    v0.10.35
    $ npm -v
    1.4.28

######  And if you get stuck… [Ask Here](http://stackoverflow.com/) 

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>