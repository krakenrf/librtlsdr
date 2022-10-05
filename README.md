[![librtlsdr version](https://img.shields.io/github/tag/librtlsdr/librtlsdr.svg?style=flat&label=librtlsdr)](https://github.com/librtlsdr/librtlsdr/releases)
[![GPLv2 License](http://img.shields.io/badge/license-GPLv2-brightgreen.svg)](https://tldrlegal.com/license/gnu-general-public-license-v2)

# Description

Modified version of librtlsdr forKkrakenSDR devices

# Build / Install (on debian/ubuntu)

## prerequisites

```
sudo apt-get install libusb-dev libusb-1.0-0-dev build-essential cmake git
```

## Purge old RTL-SDR and librtlsdr install

NOTE: this could break other RTL-SDR programs if they were relying on a specific driver branch

```
sudo apt purge librtlsdr*
sudo rm -rvf /usr/lib/librtlsdr* /usr/include/rtl-sdr* /usr/local/lib/librtlsdr* /usr/local/include/rtl-sdr*
```

## Install librtlsdr to system

```
git clone https://github.com/krakenrf/librtlsdr
cd librtlsdr
mkdir build
cd build
cmake ../ -DINSTALL_UDEV_RULES=ON
make
sudo make install
sudo ldconfig 

echo 'blacklist dvb_usb_rtl28xxu' | sudo tee --append /etc/modprobe.d/blacklist-dvb_usb_rtl28xxu.conf
```
