---
description: Upload a custom logo to be displayed on your Staking Dashboard profile
---

# Adding A Validator Logo

### &#x20;Option 1: Using Keybase (Recommended) <a href="using-keybase-recommended" id="using-keybase-recommended"></a>

1. Login to your [Keybase](https://keybase.io) account or create a new one.
2. On your profile, if you don't have a PGP key set yet, just click on "Add a PGP key" to create or import an existing one.
3. Once you have created it just click on it like it is shown on the example below:

![](../../../.gitbook/assets/add\_edit\_pgp\_key.png)

Once you click on it, Keybase will open a new page. Click on the link "this key":

![](../../../.gitbook/assets/pgp\_this\_key.png)

This will open a new page with the PGP public key finger print:

![PGP Public Key Finger Print](../../../.gitbook/assets/pgp\_fingerprint.png)

Use the following command to update your validator identity with the keybase fingerprint.&#x20;

```
./hmy --node="https://api.s0.t.hmny.io" staking edit-validator --validator-addr [YOUR VALIDATOR ONE ADDRESS] --identity [YOUR KEYBASE FINGERPRINT] --passphrase
```

Enter the passphrase when prompted. Just wait 10 min and your Keybase profile picture will automatically be used for your validator image on the Staking Dashboard!

### Option 2: Using Github (Deprecated) <a href="uploading-a-custom-logo" id="uploading-a-custom-logo"></a>

{% hint style="warning" %}
This option will be deprecated and is not recommended anymore. For now, we still maintain compatibility with it, but we urge users to migrate to Option 1: Using Keybase.
{% endhint %}

1\. Fork this github repo: [https://github.com/harmony-one/validator-logos](https://github.com/harmony-one/validator-logos)​

2\. Add your logo by creating the logo image name using your Harmony one address as the file name and placing it inside "validators" folder. The logo image needs to be a .jpg file with 256x256 pixels or 512x512 pixels.\
\
Example: validators/one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy.jpg

{% hint style="danger" %}
Do not upload the .jpg file in the main repository directory. It must be inside the "validators" directory.
{% endhint %}

3\. Create a pull request for your changes. A Harmony team member will review the image & approve it.

![](https://blobs.gitbook.com/assets%2F-M-IDt7HenNiPUXWT\_3k%2F-M1q8Eka44xqHjcC7U5S%2F-M1qUcrcCDBse9V2-zhm%2FScreen%20Shot%202020-03-07%20at%2011.34.55%20AM.png?alt=media\&token=1c53a6a9-ce60-414e-9c57-21f9d6e7b731)
