---
description: >-
  Termux is an Android terminal emulator and Linux environment app that works
  directly with no rooting or setup required. A minimal base system is installed
  automatically - additional packages are avail
---

# Termux

1. Download and Install the Termux app in the [Playstore](https://play.google.com/store/apps/details?id=com.termux&hl=en).

![](../../.gitbook/assets/image%20%28138%29.png)

2. Run the app and install the SSH for the program by typing:

```bash
pkg install openssh
```

3. Setup your instance in the different [cloud providers](../cloud-guides/).

4. Connect your instance by using the Termux app and use the following command:

```bash
ssh root@<INSTANCEIPADDRESS>
```

5. Click "yes" for authentication and retype again the command to access your instance. After that, type the unique password associated with your instance that comes from your cloud provider.

