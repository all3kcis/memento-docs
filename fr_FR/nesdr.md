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
