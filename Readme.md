# SSL TOOLS

These are tool to create youw own ca and own certs
and csr that can be use to get real live certs)


### Installation Instructions

```
make sure openssl is install
```

Do note that the values can either be real or private.
To make CSR for real life cert you should use correct
information. Using real values is does not hurt for
usage in a private enviroment:

edit the file <font color='red'>env</font> with your favorite editor and set the value
example:

```
_my_country="US"
_my_state="Momo State"
_my_city="MomoVille"
_my_org="Momo LLC"
_my_email="momo@momo.com"
_my_valid_days=1830
_my_sec_size=2048
_my_req_pass='Cr@zYP@$$wod!'
_my_domain="momo.com"

```


### Create you own CA
Before anything else, you need to create the CA first.
This will be a self signed ca cert, the name is always  <font color='red'>ca</font>

```
create the your CA : ./makeca
```

```
example : create the your CA : ./makeca
```


### Create a self signed Cert
This will create a cert signed by the ca previously created.
The certs can be found under the <font color='red'>certs</font>
directory

```
create a cert : ./makecert name
```

```
example : ./makecert awesome.momo.com
````

### Create a CSR (Certificate Signing request)
This wil create a csr that can be use to request real certs. Do note
that the information must match real values. no fakes. Normally the
values from whois.
 
```
create a csr : ./makecsr name
```

```
example : ./makecsr awesome.momo.com
```


### View a cert (cert/key/csr)

view cert

```
./viewssl --type cert cert-file
```

view key

```
./viewssl --type key key-file
```

view csr

```
./viewssl --type csr csr-file
```



### Outout

#### create CA
Note: the password need to be enter 3 time! The script will generate the 
file <font color='red'>ca.passwd</font> so you have the entered password
on file

```
./makeca                                                                                                                                                                                                  
This script will create your own CA certificate, this should not be used in live production!
Press Enter to continue or Control-C to cancel...

       	*** Generating RSA private key for CA (2048 bit) [.key] ***
       	*** Generating X.509 certificate request for CA [.csr] ***
       	**************************************************************
       	********** DO NOT USE SAME PASSWORD AS THE KEY FILE **********
       	**************************************************************
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
1. Country Name             (2 letter code) [XX]:
2. State or Province Name   (full name)     [YYYYYYY]:
3. Locality Name            (eg, city)      [ZZZZZZZ]:
4. Organization Name        (eg, company)   [KKKKKKK]:
5. Organizational Unit Name (eg, section)   [KKKKKKK Certificate Authority]:
6. Common Name              (eg, CA name)   [ca.NNNNNNN]:
7. Email Address            (eg, name@fqdn) [LLLLLLL]:

Please enter the following 'extra' attributes
to be sent with your certificate request
The password for the request file [MMMMMMM]:MMMMMMM
Organization Name [KKKKKKK]:
       	*** Generating X.509 certificate for CA signed by itself [.crt] ***
       	*** Verify: matching certificate & key modulus ***
       	*** Verify: matching certificate signature ***
       	*** Enrypting RSA private key of CA with a pass phrase for security [.key] ***
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
       	*** About to Create the password file for the CA cert, so we have it in case we forgot the password ***
Enter the same password one more time..*** Own CA Cert. created and ready for usage. ***
```


#### create CERT
Note: the password need to be enter 3 time! The script will generate the 
file <font color='red'>certs/cert-name.passwd</font> so you have the entered password
on file

```
./makecert awesome.momo.com                                                                                                                                                                                       
This script will create your certificate based on your own CA certificate, this should not be used in live production!
Press Enter to continue or Control-C to cancel...

       	*** Generating RSA private key for SERVER (2048 bit) [awesome.momo.com.key] ***
       	*** Generating X.509 certificate request for SERVER [awesome.momo.com.csr] ***
       	**************************************************************
       	********** DO NOT USE SAME PASSWORD AS THE KEY FILE **********
       	**************************************************************
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
1. Country Name             (2 letter code) [XX]:
2. State or Province Name   (full name)     [YYYYYYY]:
3. Locality Name            (eg, city)      [ZZZZZZZ]:
4. Organization Name        (eg, company)   [KKKKKKK]:
5. Organizational Unit Name (eg, section)   []:
6. Common Name              (eg, fqdn)      [awesome.momo.com]:
7. Email Address            (eg, name@fqdn) [LLLLLLL]:

Please enter the following 'extra' attributes
to be sent with your certificate request
The password for the request file [MMMMMMM]:
Organization Name [KKKKKKK]:
       	*** Generating X.509 certificate signed by own CA [awesome.momo.com.crt] ***
       	*** Verify: matching certificate & key modulus ***
       	*** Verify: matching certificate signature ***
       	*** Enrypting RSA private key of SERVER with a pass phrase for security [awesome.momo.com.key] ***
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
       	*** About to Create the password file for the CA cert, so we have it in case we forgot the password ***
Enter the same password one more time..Server awesome.momo.com's CERT created and ready for use.....
```


#### create CSR
Note: the password need to be enter 3 time! The script will generate the 
file <font color='red'>real_certs/cert-name.passwd</font> so you have the entered password
on file

```
./makecsr bigsome.momo.com                                                                                                                                                                                         
This script will create your certificate request and certificate key files, this is for in live production!
Press Enter to continue or Control-C to cancel...

       	*** Generating RSA private key for SERVER (2048 bit) [bigsome.momo.com.key] ***
       	*** Generating X.509 certificate request for SERVER [bigsome.momo.com.csr] ***
       	**************************************************************
       	********** DO NOT USE SAME PASSWORD AS THE KEY FILE **********
       	**************************************************************
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
1. Country Name             (2 letter code) [XX]:
2. State or Province Name   (full name)     [YYYYYYY]:
3. Locality Name            (eg, city)      [ZZZZZZZ]:
4. Organization Name        (eg, company)   [KKKKKKK]:
5. Organizational Unit Name (eg, section)   []:
6. Common Name              (eg, fqdn)      [bigsome.momo.com]:
7. Email Address            (eg, name@fqdn) [LLLLLLL]:

Please enter the following 'extra' attributes
to be sent with your certificate request
The password for the request file [MMMMMMM]:
Organization Name [KKKKKKK]:
       	*** Enrypting RSA private key of SERVER with a pass phrase for security [bigsome.momo.com.key] ***
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
       	*** About to Create the password file for the CA cert, so we have it in case we forgot the password ***
Enter the same password one more time..Server bigsome.momo.com's CERT created and ready for use.....
```



Enjoy
d@ momo
