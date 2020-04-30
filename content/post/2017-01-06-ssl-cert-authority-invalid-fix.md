---
layout: post
title: namecheap ssl cert authority invalid fix    
excerpt: "Old Year experience over New Year Resolution(s)"
modified: 2017-01-06
tags: [namecheap, ssl, CERT_AUTHORITY]
comments: true
---

#### Happy New Year 


Last year we deployed our rails application over nginx with ssl certificates
obtained from namecheap. everything ewas working fine but over Android moblie
we found a bug as in image below

<figure class="third">
	<img src="/images/ssl_cert_authority.png">
</figure>


#### Solution   

We got two files from NameCheap for example: 

   *  *youdomainname*.crt
   *  *youdomainname*.ca-bundle


What we missed to combine the certificates(thought ca-bundle is already combination).
We're wrong and our application stopped working on android phone's browser.

It is mandatory to combine the certificates in case of PositiveSSL. It will look like:
   
       $ cat *yourdomainname*.crt COMODO_DV_SHA-256_bundle.crt >> cert_chain.crt
       or
       $ cat *yourdomainname*.crt *yourdomainname*.ca-bundle >> cert_chain.crt


##### Sample nginx configuration

        ssl on;
        # ssl_certificate should be pointed to the file with combined certificates (file you created in step 2)
        ssl_certificate /etc/ssl/cert_chain.crt;
        # ssl_certificate_key should be pointed to the Private Key that has been generated with the CSR code that you have used for activation of the certificate.
        ssl_certificate_key /etc/ssl/*your_private_key*.key;

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
                  
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
