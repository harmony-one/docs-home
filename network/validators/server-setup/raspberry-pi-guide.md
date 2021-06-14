# Raspberry Pi Guide

## 1. UPS device

Connect the UPS to the power supply and let it charge.

## 2. Connect the modem to the UPS and set it up

Plug in the modem, the swith and the Raspberries into the UPS. Access the Modem, later we need to set up a fixed IP address and port forwarding \(TCP 6000/9000/9500\) for Rasperry.

## 3. Prepare the Raspberry

3.1.  Install Heatsinker in Rasperry

3.2.  Install Fan

3.3.  Connect Mini HDMI -&gt; HDMI cable \(if you like, otherwise you can use SSH\)

3.4.  Connect keyboard \(if you like, otherwise you can use SSH\)

3.5.  Connect Ethernet

3.6.  Install Ubuntu Server 20.04 LTS on MircoSD. Click [here](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview) for instructions

3.7.  Start the UPS Power for the Raspberry

## 4. Update Raspberry Pi

4.1.  Access via Powershell or Terminal or directly on Keyboard & Monitor

```text
ssh username@ip address
```

4.2.  Login: ubuntu / Password: ubuntu, now you need to change the password

4.3.  Update & upgrade start by command

```text
sudo apt update && sudo apt upgrade
```

During update we can set up a fix IP in the Modem and set up Port forwarding.

4.4.  Restart by command

```text
sudo reboot
```

## 5. Install the SSD

{% hint style="info" %}
Codes adapted from an Instruction, check [here](https://jamesachambers.com/raspberry-pi-4-ubuntu-20-04-usb-mass-storage-boot-guide/) if you need further information’s.
{% endhint %}

5.1.  Download Eeprom

```text
sudo apt install rpi-eeprom
```

5.2.  Restart by command

```text
sudo reboot
```

5.3.  Then connect the hard disk and check

```text
lsblk
```

5.4.  Read out the SSD ID via and write it down

```text
sudo lsusb
```

5.5.  Mount the hard disk

5.6.  Check again with point 6.3 if mount has worked well

5.7.  Automatic boot from SSD by this script

```text
 sudo mkdir /mnt/boot
 sudo mkdir /mnt/writable
 sudo mount /dev/sda1/mnt/boot
 sudo mount /dev/sda2/mnt/writable
```

5.8.  Create Quirks driver  
  
In point 6.4. the SSD ID was read out via «sudo lsusb» xxxx:xxxx  
Now connect the hard disk to a computer and in /boot/firmware/cmdline.txt “usb- storage.quirks=xxxx:xxxx:u” in the first place and save "usb-storage.quirks=04e8 4001:u” for Samsung T7

5.9.  Remove MircoSD and boot from SSD

Now it should start from the SSD, let it around 20 Minutes so settle down everything, special if you have a bigger SSD.

{% hint style="info" %}
In case it searches still for MicroSD, write with the Pi Imager «Misc utility images -&gt; Bootloader -&gt; USB Boot to the MicroSD, put it in and start the Rasperry, wait around 15 seconds, remove power and MicroSD and try again.
{% endhint %}

## 6. Set up the Raspberry again

By starting from the SSD, the password must be changed again.

## 7. Change basic settings

{% hint style="info" %}
Codes adapted from an Instruction, check [here](https://www.elektronik-kompendium.de/sites/raspberry-pi/2007031.htm) if you need further information’s\).
{% endhint %}

7.1.  Update by command

```text
sudo apt update && sudo apt upgrade
```

7.2.  Restart by command

```text
sudo reboot
```

7.3.  Change the keyboard to your Language \(if wished\)

```text
sudo dpkg-reconfigure keyboard-configuration
```

7.4.  Restart by command

```text
sudo reboot
```

7.5.  Set the time zone

```text
sudo dpkg-reconfigure tzdata
```

7.6.  Restart by command

```text
sudo reboot
```

7.7.  Speed testing of SSD via

```text
sudo hdparm -tT /dev/sda && sudo hdparm -tT --direct /dev/sda
```

## 8. System optimization

8.1. Minimize GPU, deactivate Bluetooth, deactivate Wifi and overclocking

```text
sudo nano /boot/firmware/config.txt
```

Add the following in the config file under \[all\]

```text
over_voltage=5
arm_freq=18
gpu_mem=16
dtoverlay=disable-bt
dtoverlay=disable-wifi
```

Save via ctrl + x and confirm.

##  

