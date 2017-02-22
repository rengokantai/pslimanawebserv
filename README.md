# pslimanawebserv
## Securing Apache with HTTPS
###2 Creating Private Keys
```
cd /etc/httpd/conf
```
```
openssl genrsa -out server.key 2048
```
######04:37
```
openssl rsa -noout -text -in server.key
```


###3 Creating Certificate Signing Request
```
cd /etc/httpd.conf
openssl req -new -key server.key -out server.csr
cat server.csr
openssl req -noout -text -in server.csr
```

self sign CSR
```
openssl x509 -req -sha256 -in server.csr -signkey server.key -out server.crt
```
```
openssl x509 -noout -text -in server.crt
```
