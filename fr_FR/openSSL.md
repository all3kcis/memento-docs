# OpenSSL

## Extraire les détails d'un fichier PFX
`.\openssl.exe pkcs12 -info -in .\your_cert.pfx | ./openssl.exe x509 -noout -text > C:\tmp\cert.pfx.details.txt`

## Extract Private Key from PFX
`openssl pkcs12 -in myfile.pfx -nocerts -out private-key.pem -nodes`

## Extract Certificate from PFX
`openssl pkcs12 -in myfile.pfx -nokeys -out certificate.pem`
