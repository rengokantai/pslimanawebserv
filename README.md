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

###5. Understanding CipherSuites
```
Listen 443
LoadModule ssl_module modules/mod_ssl.so
SSLCipherSuite HIGH:MEDIUM:!3DES:!RC4:!MD5:!SSLv3:!SSLv2
SSLHonorCipherOrder on
SSLProtocol sll -SSLv2 -SSLv3
```
######cipher subcommand
```
openssl ciphers -V 'HIGH:MEDIUM:!aRSA'
```

###6. Deploying Virtual Server with TLS/SSL
```
apachectl configtest
systemctl restart httpd.service
```

## 9.Using NGINX as a Web Server
```
pacman -S --noconfirm nginx
```
