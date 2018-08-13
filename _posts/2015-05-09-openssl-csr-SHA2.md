---
layout: post
title: "Openssl CSR SHA-2"
modified: 2015-05-09
excerpt: "To generate SHA-2 based CSR as SHA-1 is on a plan to phase out"
tags: [CSR, Openssl, SHA-2]
comments: true
---

For those of you who may have seen 


    This site makes use of a SHA-1 Certificate; it's recommended you use certificates
    with signature algorithms that use hash functions stronger than SHA-1. 

Mozilla, along with other browser vendors, is working on a plan to phase out support for the SHA-1 hash algorithm.
Weaknesses in hash algorithms can lead to situations in which attackers can obtain fraudulent certificates.


### Generate a SSL Key File

Firstly you will need to generate a key  file. The example below will generate a 2048 bit key file with a SHA-256 signature.

    openssl genrsa -out key_name.key 2048 

If you want extra security you could increase the bit lengths.

    openssl genrsa -out key_name.key 4096

** Please note that both these examples will not add a password to the key file. To do that you will need to add -des3 to the command.

### Create a Certificate Signing Request (CSR)

 This step will create the actually request file that you will submit to the Certificate Authority (CA) of your choice.

    openssl req -out CSR.csr -key key_name.key -new -sha256

You can check that your Certificate Signing Request (CSR) has the correct signature by running the following.

    openssl req -in CSR.csr -noout -text

It should display the following if the signature is correct.

    Signature Algorithm: sha256WithRSAEncryption

### Install the Certificate (CRT)

    Will Come Soon.
    
### Test your installed Certificate

    Will Come Soon.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>