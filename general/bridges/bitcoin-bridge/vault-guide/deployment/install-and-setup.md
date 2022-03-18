# Install & Setup

#### Set up the vault client using docker-compose:

* Install [docker](https://docs.docker.com/engine/install/)

```
sudo yum update -y
sudo yum install docker -y
sudo service docker start
sudo usermod -a -G docker ec2-user
```

**You may be required to use 'apt' instead of 'yum'.**

{% hint style="info" %}
Digital Ocean customers can see Docker installation steps [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04).
{% endhint %}

Install [docker-compose](https://docs.docker.com/compose/install/)

```
sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose version
```

* Download the docker-compose file and start the vault client

```
mkdir vault && cd vault
curl -L -o 'docker-compose.yml' https://raw.githubusercontent.com/harmony-one/onebtc.relayer-client/main/docker-compose.yml
```

#### Adding your Harmony & Bitcoin accounts to vault server

* There are two ways:
  1. Using the environment file (less secure)
  2. Using AWS KMS (more secured)

{% tabs %}
{% tab title="Environment File" %}
1\) Create a file with name `./keys/.env.private` under the vault directory

```
mkdir keys
vi ./keys/.env.private
```

2\) Add following env variables to it

```
HMY_VAULT_PRIVATE_KEY=0x6a36da....
BTC_VAULT_PRIVATE_KEY=16878a5c....
```

{% hint style="info" %}
Note that, bitcoin private key must be in the hex format
{% endhint %}

{% hint style="info" %}
The environment file storing your BTC and ONE private keys only need to be present during the start-up of your vault. Once started, you may remove the file for enhanced security. However, if your vault restarts or reboots, you must ensure to re-upload the environment file for the vault to start again.
{% endhint %}

3\) Modify the `docker-compose.yml` file by changing the following variable

```
VAULT_CLIENT_WALLET: "env"
```
{% endtab %}

{% tab title="AWS KMS" %}
1\) Create IAM user using [https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam)

* Copy the aws\__access\_key\_id, aws\_secret\_access\_key, and region to \~/.aws/credentials file_
* _The \~/.aws/credentials file should look something_

```
[default]
aws_access_key_id = <your-access-key-id>
aws_secret_access_key = <your-access-secret-key>
region = <your-region, e.g. us-west-1>
```

2\) Create a KMS key using [https://console.aws.amazon.com/kms](https://console.aws.amazon.com/kms) and add the above IAM user to it. Copy the key id (looks like `381ea1d6-8213-4c96-b072-aea222d29581`) which is needed in the next step.

3\) Encrypt your Harmony and Bitcoin account private keys using AWS KMS (additional details in [these](https://docs.aws.amazon.com/cli/latest/reference/kms/encrypt.html) steps) and create the two encrypted files with names `./keys/hmy-secret` and `./keys/btc-secret`

```
aws kms encrypt --key-id <your-key-id-from-step-2> --plaintext "your-harmony-account-private-key" --query CiphertextBlob --output text | base64 -d > ./keys/hmy-secret
```

```
aws kms encrypt --key-id <your-key-id-from-step-2> --plaintext "your-bitcoin-account-private-key" --query CiphertextBlob --output text | base64 -d > ./keys/btc-secret
```

Note that,

* the above encrypt command will only work if you have the correct credentials in `~/.aws/credentials` file (from step 1)
* the harmony private key may or may not include `0x` prefix
* the bitcoin private key could be in any form: base58 `xprv`, wif, or hex form

4\) Modify the docker-compose.yml file to add your AWS credentials, under the `vault`section. Add these

{% hint style="info" %}
AWS\_ACCESS\_KEY\_ID: "\<your-aws-access-key-id>"

AWS\_SECRET\_ACCESS\_KEY: "\<your-aws-secret-key>"

AWS\_CONFIG\_REGION: "\<your-aws-region>"
{% endhint %}

4\) Modify the `docker-compose.yml` file by changing the following variable

```
VAULT_CLIENT_WALLET: "aws"
```
{% endtab %}
{% endtabs %}

#### Starting the vault client:

You can simply run the docker-compose command to launch your vault

```
docker-compose up -d
```

Following docker commands are helpful to view the vault client docker process and make sure that it is running and also checking the logs.

```
docker-compose ps
docker-compose logs -f
```
