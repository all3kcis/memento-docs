# Envoi SMS modem GSM
 https://techexpert.tips/fr/ubuntu-fr/envoyer-un-sms-depuis-la-ligne-de-commande-linux-ubuntu-via-le-modem-gsm/  
https://tutoandco.colas-delmas.fr/software/envoyer-sms-gammu-deamon/

```sh
apt install wvdial
wvdialconf

apt-get install gammu
gammu-config


gammu getsecuritystatus
      Waiting for PIN.
gammu entersecuritycode PIN 1234
gammu getsecuritystatus
      Nothing to enter.
      
gammu sendsms TEXT 06xxxxxxxx -text "Test tutoandco"
echo "Test tutoandco" | gammu --sendsms TEXT 06XXXXXX
```
