---
layout: post
title: "Downgrade Mysql to 5.6 from 5.7 on Ubuntu 16.04(xenial)"
date:  2018-08-14 15:36:27 +05:30
categories: linux,infrastructure
---

Ubuntu 16.04 only provides packages for MySql 5.7(by default) which has a range of backwards compatibility issues
with code written against older MySql versions. for Rails specific see [this](https://github.com/brianmario/mysql2/issues/784)

Oracle maintains a list of official APT repositories for MySql 5.6, but those repository do not yet support
Ubuntu 16.04, However the 15.10 repos will work for 16.04.

Uninstall MySql 5.7 in any exists:

```SHELL 
sudo apt remove mysql-client mysql-server mysql-comman libmysqlclient-dev
```

Check you removed everything

```SHELL
sudo dpkg -l | grep mysql
``` 

Purge reminders (e.g. merged with rc) with

```SHELL
sudo dkpg P <package> [<package>]
```

Download the apt_config-debain package from [Oracle](https://dev.mysql.com/get/mysql-apt-config_0.8.0-1_all.deb) and install it

```SHELL
sudo dpkg -i mysql-apt-config_0.8.0-1_all.deb
```

Choose "MySQL 5.6" and RUN

```SHELL 
sudo apt-cache policy mysql-server
```

If this shows a 5.6 version, continue.

If not, check your `/etc/apt/sources.list.d/mysql.list`. It should look roughly like this:

```SHELL

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may Ubuntu 16.04 only provides packages for MySQL 5.7 which has a range of backwards compatibility issues with code written against older MySQL versions.comment out entries below, but any other modifications may be lost.
# Use command 'dpkg-reconfigure mysql-apt-config' as root for modifications.
deb http://repo.mysql.com/apt/ubuntu/ wily mysql-apt-config
deb http://repo.mysql.com/apt/ubuntu/ wily mysql-5.6
deb http://repo.mysql.com/apt//ubuntu/ wily mysql-tools
deb-src http://repo.mysql.com/apt/ubuntu/ wily mysql-5.6
### You might have to replace "xenial" with "wily". Although you are using 16.04 (codename Xenial), Oracle currently 
### seems to only provide 5.6 in the repos for 14.04 (codename Wiley). But those sources work for 16.04, too.

```

Create a file `/etc/apt/preferences.d/mysql` with this content

```SHELL
Package: *
Pin: origin "repo.mysql.com"
Pin-Priority: 999
Run
```

```SHELL
sudo apt-get update
```

Now recipe's run should provide

```SHELL
sudo apt install mysql-client mysql-server libmysqlclient-dev
```

You should get 5.6 versions.

Cheers :)

Things I learned : Use P(purge), dpkg -l

Links : [Gist](https://gist.github.com/Voronenko/31161ab292c7967fcd38c092335a99e1)