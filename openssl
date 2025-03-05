Decrypt certificate
openssl x509 -in certificate.crt -text -noout

Check a CSR
openssl req -text -noout -verify -in CSR.csr

New private key and CSR
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privateKey.key

Self-signed cert
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout privateKey.key -out certificate.crt

Generate CSR for an existing private key
openssl req -out CSR.csr -key privateKey.key -new

New CSR based on existing certificate
openssl x509 -x509toreq -in certificate.crt -out CSR.csr -signkey privateKey.key
