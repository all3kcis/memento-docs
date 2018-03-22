# Raspbian
## Ajout GUI sur Raspbian Lite
> https://dadarevue.com/ajouter-gui-raspbian-lite/
```sh
apt-get update
apt-get dist-upgrade
reboot
apt-get install --no-install-recommends xserver-xorg
apt-get install raspberrypi-ui-mods lightdm
reboot
```
