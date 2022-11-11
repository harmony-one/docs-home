# Dev Environment Setup

Most of the blockchain apps are developed in JavaScript, hence setting up Node.js is the first step.

## Install Node.js

Skip this section if Node.js `>=12.0`is already installed.

#### Ubuntu

```
sudo apt update
sudo apt install curl git
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt install nodejs
```

#### MacOS

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.35.2/install.sh | bash
nvm install 12
nvm use 12
nvm alias default 12
npm install npm --global # Upgrade npm to the latest version
```

#### Windows

Get node-v12.XX.XX-x64.msi from [here](https://nodejs.org/dist/latest-v12.x/)

