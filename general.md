> OpenSSL

```
ls /etc/certs

curl -k https://details:9080/details/100 --key /etc/certs/key.pem --cert /etc/certs/cert-chain.pem --cacert /etc/certs/root-cert.pem

cat /etc/certs/cert-chain.pem | openssl x509 -text -noout | grep Validity -A 2


cat /etc/certs/cert-chain.pem | openssl x509 -text -noout | grep 'Subject Alternative Name' -A 1
```
