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
