---
layout: post
title: Setup multiple ssl enabled applications on apache and ubuntu   
excerpt: "SSL configurations on Apache"
modified: 2016-08-27
tags: [SSL configurations, open-source, apache]
comments: true
---

### How to host multiple SSL certificates on one Web-Server(Apache) ? 

To host multiple SSL certificates on one IP Address, We need to configure
Apache Server Name Indication (SNI).

### Setup
SNI does need to have registered domain names in order to serve the certificates.

 * Install Apache2 `sudo apt-get install apache2`
 * Get SSL certificates for site1.com,site2.com
 * have directory structure like 
     `/etc/apache2/ssl/site1.com`
     `/etc/apache2/ssl/site2.com`
 * enable ssl mod for apache `sudo a2enmod ssl`
 * restart apache `sudo service apache2 restart`

Assuming you have the certificates saved as per above directory structure,
we can create two virtual host files to store virtual host configurations
in separate files.

 * `sudo nano /etc/apache2/sites-available/site1.com`
 * `sudo nano /etc/apache2/sites-available/site2.com`
 
Following configurations I've used for site1 and site2 respectively.
 
{% highlight ruby %}
<VirtualHost *:80>
	ServerName site1.com
	ServerAlias www.site1.com
	Redirect / https://www.site1.com/
</VirtualHost>
<VirtualHost *:443>
	ServerName site1.com
	ServerAlias www.site1.com
	SSLEngine on
	SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
	SSLCertificateFile /etc/ssl/crt/site1.crt
	SSLCertificateKeyFile /etc/ssl/key/site1.key
	SSLCertificateChainFile /etc/ssl/crt/site1.ca-bundle   
    DocumentRoot site1SourcePath
	<Directory site1SourcePath>
        Options Indexes FollowSymLinks
	    AllowOverride All
	    Require all granted
	</Directory>
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
{% endhighlight %}

{% highlight ruby %}
<VirtualHost *:80>
	ServerName site2.com
	ServerAlias www.site2.com
	Redirect / https://www.site2.com/
</VirtualHost>
<VirtualHost *:443>
	ServerName site2.com
	ServerAlias www.site2.com
	SSLEngine on
	SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
	SSLCertificateFile /etc/ssl/crt/site2.crt
	SSLCertificateKeyFile /etc/ssl/key/site2.key
	SSLCertificateChainFile /etc/ssl/crt/site2.ca-bundle   
    DocumentRoot site1SourcePath
	<Directory site1SourcePath>
        Options Indexes FollowSymLinks
	    AllowOverride All
	    Require all granted
	</Directory>
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
{% endhighlight %}

and just to confirm `/etc/apache2/ports.conf` looks like this :-

{% highlight ruby %}
Listen 80
<IfModule ssl_module>
	Listen 443
</IfModule>
<IfModule mod_gnutls.c>
	Listen 443
</IfModule>
{% endhighlight %}


### Activate the Virtual Hosts
 * `sudo a2ensite site1.com`
 * `sudo a2ensite site2.com`
 
 (You can deactivate virtual hosts with the command: `sudo a2dissite site1.com`)
 
With all of the virtual hosts in enabled, restart apache.
 
 `sudo service apache2 restart`
 
You should now be able to access both sites, each with its own domain name and SSL certificate.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
