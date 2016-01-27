# Reference

* <https://www.sslshopper.com/article-most-common-openssl-commands.html>

# Check a certificate

    openssl x509 -in certificate.crt -text -noout

# Convert PEM to pkcs8 for Java

    openssl pkcs8 -topk8 -inform PEM -outform DER -in privateKey.pem  -nocrypt > pkcs8_key