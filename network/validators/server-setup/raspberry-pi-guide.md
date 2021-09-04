# Raspberry Pi Guide

{% hint style="info" %}
Before setting up Raspberry Pi, check requirements [here](requirements.md#for-raspberry-pi).
{% endhint %}

## 1. UPS Device

Connect the UPS to the power supply and let it charge.

## 2. Connect the Modem to the UPS and Set it up

Plug in the modem, the swith and the Raspberry into the UPS and access the Modem. Later we need to set up a fixed IP address and port forwarding \(TCP 6000/9000/9500\) for the Rasperry.

## 3. Prepare the Raspberry

3.1.  Install Heatsinker on Raspberry

3.2.  Install Fan

3.3.  Connect Mini HDMI -&gt; HDMI cable \(if you like, otherwise you can use SSH\)

3.4.  Connect the keyboard \(if you like, otherwise you can use SSH\)

3.5.  Connect Ethernet

3.6.  Install Ubuntu Server 20.04 LTS on MircoSD and on SSD. Click [here](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview) for instructions

3.7.  Start the UPS Power for the Raspberry

## 4. Update Raspberry Pi

4.1.  Access via Powershell, Terminal or directly via Keyboard and Monitor

```text
ssh username@ip address
```

4.2.  Login: ubuntu / Password: ubuntu

{% hint style="warning" %}
For security reasons Linux requires to change the default ubuntu password.
{% endhint %}

4.3.  Update & Upgrade

```text
sudo apt update && sudo apt upgrade
```

{% hint style="info" %}
During update we can set up a static IP on the Modem and set up Port forwarding.
{% endhint %}

4.4.  Restart

```text
sudo reboot
```

## 5. Install SSD

{% hint style="info" %}
Code is adapted from an Instruction, check [here](https://jamesachambers.com/raspberry-pi-4-ubuntu-20-04-usb-mass-storage-boot-guide/) if you need further information’s.
{% endhint %}

5.1.  Download Eeprom

```text
sudo apt install rpi-eeprom
```

5.2.  Restart

```text
sudo reboot
```

5.3.  Connect the hard disk and check

```text
lsblk
```

5.4.  Read out the SSD ID via and write it down

```text
sudo lsusb
```

5.5.  Mount the hard disk

```text
 sudo mkdir /mnt/boot
 sudo mkdir /mnt/writable
 sudo mount /dev/sda1 /mnt/boot
 sudo mount /dev/sda2 /mnt/writable
```

5.6.  Check again with point 5.3 if mount has worked

5.7.  Automatically boot from SSD using this script

```bash
 sudo curl https://raw.githubusercontent.com/TheRemote/Ubuntu-Server-raspi4-unofficial/master/BootFix.sh | sudo bash
 sudo umount /mnt/boot
 sudo umount /mnt/writable
 sudo shutdown now
```

5.8.  Create Quirks driver  
  
In point 5.4. the SSD ID was read out via `sudo lsusb xxxx:xxxx`  
Now connect the hard disk to a computer and add in `/boot/firmware/cmdline.txt` `“usb-storage.quirks=xxxx:xxxx:u”` in the first place, without the quotation marks and save. For example for the Samung T7, `usb-storage.quirks=04e8:4001:u`

5.9.  Remove the MicroSD and boot from SSD

Now it should start from the SSD, let it around 20 Minutes so settle down everything, special if you have a bigger SSD.

{% hint style="info" %}
In case it searches still for MicroSD, write with the Pi Imager «Misc utility images -&gt; Bootloader -&gt; USB Boot to the MicroSD, put it in and start the Rasperry, wait around 15 seconds, remove power and MicroSD and try again.
{% endhint %}

## 6. Set up the Raspberry again

By starting from the SSD, the password must be changed again. Upon logging in for the first time if the Pi is connected to the internet Ubuntu will immediately/soon start a lengthy update process via snapd and apt. 

{% hint style="warning" %}
Make sure you give the system enough time \(20 Minutes at least\) to finish this process before doing going forward.
{% endhint %}

## 7. Change basic settings

{% hint style="info" %}
Code is adapted from an Instruction, check [here](https://www.elektronik-kompendium.de/sites/raspberry-pi/2007031.htm) if you need further information’s\).
{% endhint %}

7.1.  Update by command

```bash
sudo apt update && sudo apt upgrade
```

7.2.  Restart by command

```text
sudo reboot
```

7.3.  Change the keyboard to your Language \(if wished\)

```bash
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
arm_freq=1800
force_turbo=1
gpu_mem=16
gpu_freq=300
dtoverlay=disable-bt
dtoverlay=disable-wifi
```

Save via ctrl + x and confirm.

## 9. Final Establishment

9.1.  Change host name

{% hint style="info" %}
Code is adapted from an Instruction, check [here](https://phoenixnap.com/kb/ubuntu-20-04-change-hostname) if you need further information’s\).
{% endhint %}

```text
hostnamectl set-hostname NEWHOSTNAME
```

9.2.  Create user

{% hint style="info" %}
Code is adapted from an Instruction, check [here](https://brightwhiz.com/add-users-ubuntu-20-04/) if you need further information’s\).
{% endhint %}

```text
 sudo -i
 sudo adduser NEWUSER
```

Enter your new password and confirm again.

9.3.  Give sudo permission

```text
sudo usermod -aG sudo NEWUSER
```

9.4.  Check and even extend authorization

```text
 groups NEWUSER && groups ubuntu
 sudo usermod -G ubuntu, adm, dialout, cdrom, floppy, sudo, audio, dip, video, plugdev, netdev, lxd, root NEWUSER
```

9.5.  Add the entry for the new user in Visudo

```text
visudo
```

```text
root ALL = (ALL: ALL) ALL 
NEWUSER ALL = (ALL: ALL) ALL
```

Save via ctrl + x and confirm.

9.6.  Terminate old processes and block users

```text
 sudo pkill -u ubuntu
 sudo usermod -L ubuntu
```

9.7.  Change to new User

```text
sudo su -NEWUSER
```

## 10. Firewall Setup

{% hint style="info" %}
Code is adapted from an Instruction, check [here](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-20-04) if you need further information’s\).
{% endhint %}

10.1.  Install & activate the firewall

```text
 sudo apt install ufw
 sudo ufw enable
```

10.2.  Open the corresponding TCP ports for Harmony & local SSH from another PC

```text
sudo ufw allow from LOCALIP to any port 22
sudo ufw allow 6000/tcp
sudo ufw allow 9000/tcp
sudo ufw allow 9500/tcp
```

10.3.  Check Firewall

```text
sudo ufw status
```

_Congratulation you set up your Raspberry Pi and it is ready for setting up as Node!_

{% hint style="warning" %}
Since [HMY CLI](../node-setup/hmy-cli-download.md) is not natively supported ARM systems yet, install it on a x86\_64 system to [setup the BLS Keys](../node-setup/generating-a-bls-key.md). After that, copy them to the same  `.hmy/blskeys` folder on Raspberry Pi.
{% endhint %}

## 11. Continue Node Setup

Continue node setup from [Rclone](../node-setup/syncing-db.md) onwards.  


