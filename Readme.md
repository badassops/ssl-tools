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
_my_key_pass='Cr@zYP@$$wod!'
_my_domain="momo.com"

```

### Create you own CA
Before anything else, you need to create the CA first.
This will be a self signed ca cert, the name is always  <font color='red'>ca</font>

```
create the CA : ./makeca
```

### Create a self signed Cert
This will create a cert signed by the ca previously created.
The certs can be found under the <font color='red'>certs</font>
directory

```
example : ./makecert awesome.momo.com
````

Note:
1. makecert support SAN certs
2. the keyword star and wildcard indicates a wildcard cert
3. makecert -h for more help


### Create a CSR (Certificate Signing request)
This wil create a csr that can be use to request real certs. Do note
that the information must match real values. no fakes. Normally the
values from whois.
 
```
example : ./makecsr awesome.momo.com
```

Note:
1. makecsr support SAN request
2. the keyword star and wildcard indicates a wildcard cert
3. makecsr -h for more help


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


Enjoy
d@ momo
