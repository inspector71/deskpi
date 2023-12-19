# About the DeskPi Pro

The DeskPi Pro is a hardware kit for converting a standard Raspberry Pi 4 from a naked SBC, with limited storage, into a mini PC complete with a power button, cooling, better ports and, via SATA then USB3, 2.5" or M.2 SSD storage.

## Operating Systems (OS)

### Tested successfully with DeskPi scripts
* DietPi (64bit)
* Kali-linux-arm (32bit)
* Manjaro (32bit) 
* Raspberry Pi OS (32bit) 
* RaspiOS (64bit) 
* RetroPie OS (32bit)
* Twister OS v2.0.2 (32bit)
* Ubuntu-mate OS(32bit)
* Ubuntu (64bit) 
* Volumio OS Version: 2021-04-24-Pi (32bit) 

### Yet to be tested with DeskPi scripts
* Kali-linux-arm OS (64-Bit)
* Manjaro OS (64bit)
* Windows 11 

### Not supported
* Windows 10 IoT 

## Please read this section carefully
* If using a 64bit OS, the script to control the fan is in the `rivers/c/` directory. The file suffix with `64` means `64bit` and the one without a `32bit` executable file
* Before you install this script, please make sure your Raspberry Pi can access the GitHub website

## Installation

### For Raspbian OS 64bit (bookworm)
* Step 1. Enable Front USB port
Edit `/boot/firmware/config.txt` file by adding the following parameter:
```bash
dtoverlay=dwc2,dr_mode=host
```
Save it and reboot your Raspberry Pi.
* Step 2. Install fan driver
TO BE DONE, we are working on it...

### For Raspbian and RetroPie OS
```bash
cd ~
git clone https://github.com/DeskPi-Team/deskpi.git
cd ~/deskpi/
chmod +x install.sh
sudo ./install.sh
```
### For Ubuntu 64bit OS
```bash
cd ~
git clone https://github.com/DeskPi-Team/deskpi.git
cd ~/deskpi/
chmod +x install-ubuntu-64.sh
sudo ./install-ubuntu-64.sh
```
### For Ubuntu-mate OS
```bash
cd ~
git clone https://github.com/DeskPi-Team/deskpi.git
cd ~/deskpi/
chmod +x install-ubuntu-mate.sh
sudo ./install-ubuntu-mate.sh
```
### For Manjaro OS
```bash
cd ~
git clone https://github.com/DeskPi-Team/deskpi.git
cd ~/deskpi/
chmod +x install-manjaro.sh
sudo ./install-manjaro.sh
```
### For Kali-linux-arm OS
* Image Download URL: https://images.kali.org/arm-images/kali-linux-2020.3a-rpi3-nexmon.img.xz


