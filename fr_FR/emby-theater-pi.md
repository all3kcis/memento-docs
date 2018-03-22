# How to install Emby theater on Raspberry Pi 3
First install Pi, download last Raspbian img  
If you have choosed Raspbian you have to install UI, see [Rasbian](fr_FR/raspbian.md)
```sh
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get install git npm cec-utils
# Link node
ln -s /usr/bin/nodejs /usr/bin/node
# Install electron 1.4.16 ( Important !)
npm -g install electron@1.4.16
cd ~
git clone https://github.com/MediaBrowser/emby-theater-pi.git
cd emby-theater-pi
electron . cec-client
```
