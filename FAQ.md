# FAQ 
## About USB booting, what is UASP?
* Without UASP, a drive is mounted as a Mass Storage Device using Bulk Only Transport (or BOT), a protocol that was designed for transferring files way back in the USB 'Full speed' days, when the fastest speed you could get was a whopping 12 Mbps!
* With USB 3.0, the BOT protocol cripples throughput. USB 3.0 has 5 Gbps of bandwidth, which is 400x more than USB 1.1. The old BOT protocol would transfer data in large chunks, and each chunk of data had to be delivered in order, without regard for buffering or multiple bits of data being able to transfer in parallel.
* So a new protocol was created, called 'USB Attached SCSI Protocol', or 'UASP'
 
## How to check if my drive is support UASP?
* If you have a USB drive and don't want to take it apart and look up the specs of the controller chip, the only reliable way to tell if it's being mounted with UASP support or not is to plug it into your Pi, then run the command lsusb -t:
```bash
$ lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=uas, 5000M
```
This command lists all the USB devices in a tree, and for each of the hard drives, you should see a Driver listed. If it's uas (like in the above example), then your drive supports UASP and you'll get the best speed. If it's usb-storage, then it's using the older BOT protocol and you won't see the full potential.

## Why doesn't my fan spin around when the DeskPi has idled for a while? 
* By default, DeskPi's fan driver adjusts the speed according to CPU temperature. If the current temperature is lower than the fan rotation threshold, the fan will automatically stop. If you need the fan to run at a specific speed, please open a terminal, run `deskpi-config` and select the corresponding operating mode according to the prompt.

## What is the pre-installed Raspbian OS's username and password? 
* Pre-install Raspbian OS's username is `pi` and password is `raspberry`, it is original of Raspiban, we did not change it when we distribute this image.

## Why does the pre-installed Raspbian OS image's setting is China? 
* This pre-installed Raspbian OS image is based on Raspbian OS buster(ver:2020-08-20), and when we are initializing this OS and try to connect to internet and download deskpi driver from github.com, we must set the wi-fi country before we enable the wifi adapters. and this product may sale all around the world, we can not detect which country or nation that our costomer is in, so the default set is Shanghai China. and you can just change the wi-fi country by using command in terminal : `sudo raspi-config` and select Localisation Options to configure language and regional settings.

## The front panel USB is unavailable.
* Because there is no configuration: /boot/config.txt file, you need to add in this configuration file: dtoverlay=dwc2,dr_mode=host, and restart the Raspberry Pi. and if you installed deskPi driver, it will add to config.txt file automatically. 

## Can I change computer name in pre-installed Raspbian OS?
* Yes, of course, Typing `sudo raspi-config` to select System Options (item 1) and navigate to S4 Hostname to configure your hostname or just typing `sudo hostnamectl set-hostname YOURHOSTNAMEHERE` to set hostname in commandline.

## How can I check if my drive supports UASP?
* Open a terminal and type: `lsusb -t | grep -i "uas"` and press Enter.

## How to install DeskPi fan control driver when i've reflashed my TF card? 
* Make sure your OS is on the support OS list.
* Make sure your Raspberry Pi can access internet.
* git clone https://github.com/DeskPi-Team/deskpi.git
* Type the following commands into a terminal:
```bash
cd ~/deskpi/
chmod +x install.sh
sudo ./install.sh
```

## Where is the list of supported Operating Systems?
* https://github.com/DeskPi-Team/deskpi/blob/master/README.md#about-the-deskpi-pro
