---
layout: post
title: install your public key in a remote machine's authorized_keys
excerpt: "linux ssh shorthand "
modified: 2016-09-17
tags: [ssh, authorized_keys]
comments: true
---


#### Problem
We frequently add developer ssh keys to remote machine with following three steps

 * `ssh username@remote_host`
 * `mkdir -p ~/.ssh`
 * `cat ~/.ssh/id_rsa.pub` and copy it
 * `nano ~/.ssh/authorized_keys` and paste copied content.

Quite Annoying.

#### Solution
    `ssh-copy-id`.

ssh-copy-id [-i [identity_file]] [user@]machine

##### Description

ssh-copy-id is a script that uses ssh to log into a remote
machine (presumably using a login password, so password
authentication should be enabled, unless you've done some
clever use of multiple identities) It also changes the
permissions of the remote user's home, `~/.ssh`, and
`~/.ssh/authorized_keys` to remove group writability
(which would otherwise prevent you from logging in, if
the remote sshd has StrictModes set in its configuration).
If the -i option is given then the identity file (defaults
to `~/.ssh/id_rsa.pub`) is used, regardless of whether
there are any keys in your ssh-agent. Otherwise, if this:
`ssh-add -L` provides any output, it uses that in preference
to the identity file. If the -i option is used, or the ssh-add
produced no output, then it uses the contents of the identity
file. Once it has one or more fingerprints (by whatever means)
it uses ssh to append them to `~/.ssh/authorized_keys` on the
remote machine (creating the file, and directory, if necessary)


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
