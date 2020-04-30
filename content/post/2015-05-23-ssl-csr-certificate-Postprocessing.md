---
layout: post
title: "SSl csr-certificate post-processing for Web-Server usage"
modified: 2015-05-26
excerpt: "To un-lock openssl key and combined certificates in One"
tags: [CSR, Openssl, SSl, csr-certificate, post-processing, Web-Server, NameCheap]
comments: true
---

For those of you who may refer my early written post [Openssl CSR SHA-2.](http://rajeevkannav.github.io/openssl-csr-SHA2).
Here is Part 2.

### Install the Certificate (CRT)

After giving your CSR to SSL Provider, you need to wait for their response. They'll validate your CSR and give you some
certificates and file as in package. We're using NameCheap as SSL Provider so this blog will follow according to their
response. NameCheap sends you an zipped folder which will have :


  * AddTrustExternalCARoot.crt
  * COMODORSAAddTrustCA.crt
  * COMODORSADomainValidationSecureServerCA.crt
  * STAR_xxxxx_com.crt

And you already have


  * xxxxx.key
  * xxxxx.csr

Now you'll need to have one pass phrase protected key and one combined ssl certificate in right order. You need to remove
the pass phrase. To do that have that key and run following command

    openssl rsa -in xxxxx.key -out xxxxx.nopass.key

Enter the private key pass phrase when asked. And Get set Go! Use this new key to your
Elastic Load Balancer/nginx/Apache. For combined SSL certificate :--

    cat STAR_xxxxx_com.crt COMODORSADomainValidationSecureServerCA.crt COMODORSAAddTrustCA.crt AddTrustExternalCARoot.crt > SSL.crt

Use SSL.crt and xxxxx.nopass.key to your Web Server configuration.

### Test your installed Certificate

Visit your web Application after configuring certificates and key at web server and see Browser console.
There should not any waring or error related to SSL. for e.g.

    This site makes use of a SHA-1 Certificate; it's recommended you use certificates
    with signature algorithms that use hash functions stronger than SHA-1.


######  And if you get stuck… [Ask Here](http://stackoverflow.com/) 

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>