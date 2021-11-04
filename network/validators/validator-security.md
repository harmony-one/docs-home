---
description: Helpful information to keep your validating node secure
---

# Validator Security Tips

This section will teach you about improving the security of your validator. As a validator you play a crucial role in securing and decentralizing the Harmony network. The security of the network is compounded as a sum of all validator's security. Therefore is very important that every single piece in the chain is as secure as possible.&#x20;

Depending on your configuration, if you have the BLS key on your validator server and maybe also the password to decrypt it, for example in order to restart your node automatically, it is strongly recommended that you secure the access to your validator as much as possible.&#x20;

Using 2FA and other security measures can substantially improve the overall security of your validator. The state of the art for 2FA is to use a HSM module like YubiKey.&#x20;

**Very important:** it is highly recommended to have two YubiKeys associated to ensure one is not locked out in case a YubiKey is lost, stolen, or breaks.

In case you find YubiKey an expensive solution, other methods for 2FA can be used, like your phone or authenticator apps for example.&#x20;

**Very important:** Be aware that SMS based 2FA authentication methods are not secure and not recommended as one could hijack your smartphone’s SIM. Doing this hackers can redirect any two-factor notifications to their own devices.

### **What are and why use HSM modules?**

Hardware Security Modules (HSMs) generate, manage and store the secure cryptographic keys that are required for authenticating an user or device in a broader network. Malware attacks and remote extraction of private keys are much more difficult when a HSM module is configured properly. When you have your private key on your validator that is secured only by a password, an attacker can simply copy your private key and sign malicious transactions or generate double signs which can result for example in stake slashing or other unwanted operations on your node. By using Two-Factor Authenticator (2FA) and HSM module, you are strengthening the authentication on your Virtual Private Server (VPS). There are many options for 2FA but is recommended that you actually use a HSM module like YubiKey for this. Even better would be to use certificate in combination with a HSM module in order to authenticate and disable password login.

### **How can I secure the access to my VPS better?**

#### **1. **Add Two-factor Authenticator to your VPS provider if it is allowed.

Serious VPS providers allow this already and also to use a HSM module like YubiKey. This guide focuses on Vultr but the documentation for YubiKey activation can be found in the documentation of different VPS providers, e.g. Hetzner: [https://wiki.hetzner.de/index.php/KonsoleH:Zwei-Faktor-Authentifizierung/en](https://wiki.hetzner.de/index.php/KonsoleH:Zwei-Faktor-Authentifizierung/en)

**Activate 2FA with YubiYey for Vultr**

In order to use YubiKey Authentication, you need any of Yubico’s Yubikey USB devices. Next, you would need to login to your Vultr Account: Click Account -> Authentication -> Manage Two Factor Auth: [https://my.vultr.com/settings/twofactor/](https://my.vultr.com/settings/twofactor/)

Under Add new authentication method, select YubiKey, enter a description of your choice in the next field, then click Add.

In the next page, you will need to make sure your YubiKey device is plugged into one of your USB Ports on your computer. You will be presented with a text field in which you need to click, then press the button(s) on your YubiKey Device, or touch the edge of the device if you’re using a YubiKey Nano, then click Update.

In the next page, you will need to repeat the previous step to re-enter a secondary token, then click Update.

When you are finished, log out of your Vultr account. Then attempt to log back in. You will be asked to enter an authentication code. Insert the YubiKey device in one of your computer’s USB ports, and either press the button(s) or touch the edge of the device.

#### **2. Create a SSH Public-Private Key pair for your VPS and assign the Public Key to the VPS when creating it.**

On Windows you can use for example PuttyGen to generate your SSH Public-Private Key pair. Setting a passphrase is advisable as it offers another layer of security if your ssh keys will be compromised.

Popular algorithms for creating SSH Keys:

**RSA:** It depends on key size. It is recommend to have 3072 or even better 4096-bit length. The 1024-bit length is considered unsafe.&#x20;

**Ed25519:** It’s the most recommended public-key algorithm available today but you have to check with the cloud provider, e.g. Vultr, Hetzner, AWS if is supporting this.

To generate the SSH keys on macOS use the Terminal and the command below.&#x20;

```
ssh-keygen -t rsa
```

#### **3. Use SSH Private Key and not password to authenticate on your VPS**

#### **4. **If you received any root password after creating your VPS, change it

```
passwd
```

Make sure to **back-up this password** and also be aware where you place it so that it won’t get stolen.

**Very important:** For holding passwords, keywords, etc. an encrypted hardware device and paper wallets are recommended. It is not recommended to hold passwords or keywords on a hot storage like your personal computer or notebook.

#### 5. Once logged in, update your OS

For Debian based systems like Ubuntu or Debian use the command below:&#x20;

```
sudo apt-get update && sudo apt-get upgrade
```

For Amazon Linux use the command below:

```
sudo yum update
```

#### 6. Create a separate user than root for your application

It is not recommended to use directly the root user on your VPS. Therefore create a new user:

```
adduser <your-username>
```

Add the newly created \<your-username> user to the sudo group:

```
adduser <your-username> sudo
```

You can switch to the new user with the following command:

```
sudo -u <your-username> -i
```

#### **7. Create the necessary setup so that the new created user can login using certificate**

```
sudo mkdir -p "/home/<your-username>/.ssh"
sudo chmod 0700 "/home/<your-username>/.ssh"
sudo chown "<your-username>:<your-username>" "/home/<your-username>/.ssh"
```

Add the public key to your new created user

```
sudo nano "/home/<your-username>/.ssh/authorized_keys"
sudo ls "/home/<your-username>/.ssh" -l
sudo chown "<your-username>:<your-username>" "/home/<your-username>/.ssh/authorized_keys"
sudo chmod 0600 "/home/<your-username>/.ssh/authorized_keys"
```

#### **8. Setup Yubikey 2FA on Debian based systems like Ubuntu and strengthen the general authentication**

First add the PPA and install the library.

```
sudo add-apt-repository ppa:yubico/stable
sudo apt-get update
sudo apt-get install libpam-yubico
```

Let’s add pam settings for SSH.

```
sudo nano /etc/pam.d/sshd
```

Add the following line at the top to enable the module:

```
auth sufficient pam_yubico.so id=[Your API Client ID] key=[Your API Client Key] authfile=/etc/yubikey_mappings
```

You can use the following link in order to get the API Client ID and the API Client Key: [https://upgrade.yubico.com/getapikey/](https://upgrade.yubico.com/getapikey/)

![](https://lh4.googleusercontent.com/DUjKMlVdyfL7aPWzNZnpnkTbTw4jRqzfJEBiwYC0aaON0kjCf91UYcXEtEEOePO-S4UwLXWmmAC7EySW7yDLCQ99TgLkE2EsS448xkqTIQL29-pDP2yHwadq63wzpeZVMS3gPIw)

To improve the security you should comment the following line out:

```
@include common-auth
```

This way the YubiKey is required to authenticate without a possibility to fall back to providing the password.&#x20;

Result:

![](https://lh3.googleusercontent.com/6T2EW66tjlnLZWKCERhmLkfEg7wqGCmuamwAMmckh31Osz6K\_nGXkHR04SQca2\_D37bTvlJAz0Tvid8eX5vZ9FlpojHv6rg42wcz51bcbRrvT-Vi\_f8mBRl-PhQ87Q0SA7eN42I)

Save the file and exit -> press Ctrl+X and then press “y”

Next step is to create a mapping file where you define which YubiKey device is assigned to which user of your VPS.

The mapping file contains users and YubiKey identifiers. The YubiKey identifiers are always the first 12 characters of the generated YubiKey token. In order to generate the YubiKey token you just tap your YubiKey. Then you select its first 12 characters. In case you have multiple YubiKeys you can also add multiple.

```
sudo nano /etc/yubikey_mappings
```

Add the mappings for each user:

```
<user1:<first 12 characters of yubikey1>:<first 12 characters of yubikey2>
<user2>:<first 12 characters of yubikey1> 
```

Save the file and exit -> press Ctrl+X and then press “y”

Next step is to update sshd\_config file to authenticate via public key and pam.

```
sudo nano /etc/ssh/sshd_config
```

Following changes need to be made:

*   Enable challenge response authentication by changing it to “yes”** **

    _ChallengeResponseAuthentication yes_
*   Add a new line that sets the Authentication Methods to require first the public key to be valid and then the YubiKey token for each user.

    _AuthenticationMethods publickey,keyboard-interactive:pam_
* UsePAM yes
*   Disable the password authentication by removing “#” in front of this line:

    _PasswordAuthentication_ and set the value from _yes_ to _no_&#x20;
* Disable root authentication - if you have created a separate user for your application, deployments, etc. you can also disable the SSH root user access, which will add an extra layer of security to your VPS.** **Find the line _PermitRootLogin_, remove the comment sign “#” from the beginning of it and set the value to _no_
*   Change your SSH port from 22 to another one, for example 2225.** **

    Don’t use any of the ports in this list: [https://en.wikipedia.org/wiki/List\_of\_TCP\_and\_UDP\_port\_numbers](https://en.wikipedia.org/wiki/List\_of\_TCP\_and\_UDP\_port\_numbers) , as they are already being used.** **\


Example sshd\_config file - **take it only as reference to see the security changes and don't copy it!**

```
#	$OpenBSD: sshd_config,v 1.101 2017/03/14 07:19:07 djm Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

Port 2225
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key

# Ciphers and keying
#RekeyLimit default none

# Logging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:
AuthenticationMethods publickey,keyboard-interactive:pam


#LoginGraceTime 2m
PermitRootLogin no
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

#PubkeyAuthentication yes

# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile	.ssh/authorized_keys .ssh/authorized_keys2

#AuthorizedPrincipalsFile none

#AuthorizedKeysCommand none
#AuthorizedKeysCommandUser nobody

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no
#PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes
#GSSAPIStrictAcceptorCheck yes
#GSSAPIKeyExchange no

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PermitTTY yes
PrintMotd no
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS no
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
#PermitTunnel no
#ChrootDirectory none
#VersionAddendum none

# no default banner path
#Banner none

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# override default of no subsystems
Subsystem	sftp	/usr/lib/openssh/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#	X11Forwarding no
#	AllowTcpForwarding no
#	PermitTTY no
#	ForceCommand cvs server
```

Save the file and exit -> press Ctrl+X and then press “y”

Finally restart the sshd service to update the settings.

```
service sshd restart
```

**Test the configuration**\
It is recommended to keep the current session active. In case something went wrong, you will still have access to your VPS and be able to make changes.

Create a new ssh connection and check if the SSH login with certificate and YubiKey works. First the certificate will be used and then you will be prompted for YubiKey. Once this is the case just tap your YubiKey to enter your token and login.

Example:

![](https://lh5.googleusercontent.com/CbsdFWSupNGtPVqsKkzSlpzjS41ebLppXo0ERBV7SKNyLssZw0dBIyunKOXKI9rdX4cs0NA9-UX8j5SQbMcU9JLi5jgiRdHrtf4JWs0WHcKQr1UqGzXGVJJgpdupRAgcVSRf2r0)

**9. Install fail2ban to reduce brute force attacks**

```
sudo apt-get install -y fail2ban
```

Start and enable the service

```
sudo systemctl start fail2ban
sudo systemctl enable fail2ban
```

It is recommended to use a separate jail.local file to actually read your own configuration. For that first you have to copy the basic configuration jail.conf to the local one jail.local. The new file jail.local will override the original settings in jail.conf.

```
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

Edit the file jail.local

```
sudo nano /etc/fail2ban/jail.local
```

```
Enter your desired configuration, for example:
[sshd]
enabled = true
port = 22
filter = sshd
logpath = /var/log/auth.log
maxretry = 5
```

This configuration will block an IP address that is being used to log into your VPS via SSH, port 22 and fails for 5 times.

Save and close the file -> press Ctrl+X and then press “y”

Restart fail2ban to activate the settings

```
sudo systemctl restart fail2ban
```

**10. Configure system firewall with IPtables**\
More about it can be found here: [https://www.tecmint.com/linux-iptables-firewall-rules-examples-commands/](https://www.tecmint.com/linux-iptables-firewall-rules-examples-commands/)\
\
**11. Monitor and manage your system and process by using htop**

** **Install htop

```
sudo apt-get install htop
```

Run htop

```
htop
```
