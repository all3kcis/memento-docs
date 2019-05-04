# NESDR
Source : https://www.raspberrypi.org/forums/viewtopic.php?t=45142  

```sh
# Install dependencies
sudo apt-get update
sudo apt-get -y install git cmake build-essential libusb-1.0 qt4-qmake libpulse-dev libx11-dev

# Fetch and compile rtl-sdr source
mkdir -p ~/src/
cd ~/src/
git clone git://git.osmocom.org/rtl-sdr.git
cd rtl-sdr
mkdir build
cd build
cmake ../ -DINSTALL_UDEV_RULES=ON -DDETACH_KERNEL_DRIVER=ON
make
sudo make install
sudo ldconfig

# Fetch and compile multimonNG
cd ~/src/
git clone https://github.com/EliasOenal/multimonNG.git
cd multimonNG
mkdir build
cd build
qmake ../multimon-ng.pro
make
sudo make install
```
Fonctionnement :  
```sh
rtl_fm -f 466231250 -s 22050 -g 30 -E dc - | multimon-ng -t raw -p -c -a POCSAG1200 -f alpha /dev/stdin &
```
-g 30 = gain  
-E DC = supprime le pique DC
