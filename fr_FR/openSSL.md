# OpenSSL

## Extraire les détails d'un fichier PFX
`.\openssl.exe pkcs12 -info -in .\your_cert.pfx | ./openssl.exe x509 -noout -text > C:\tmp\cert.pfx.details.txt`
