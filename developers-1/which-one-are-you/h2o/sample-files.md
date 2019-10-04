# Sample Files

## truffle\_config.js

```text
const { TruffleProvider } = require('@harmony-js/core')


//one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7
//0x3aea49553Ce2E478f1c0c5ACC304a84F5F4d1f98
//01F903CE0C960FF3A9E68E80FF5FFC344358D80CE1C221C3F9711AF07F83A3BD

/*

const phrase =
  'food response winner warfare indicate visual hundred toilet jealous okay relief tornado'
const privateKey =
  '27978f895b11d9c737e1ab1623fde722c04b4f9ccb4ab776bf15932cc72d7c66'

  */
const phrase = 'urge clog right example dish drill card maximum mix bachelor section select' 
const private_key = '01F903CE0C960FF3A9E68E80FF5FFC344358D80CE1C221C3F9711AF07F83A3BD'
const url = 'http://localhost:9500'

//one18t4yj4fuutj83uwqckkvxp9gfa0568uc48ggj7
const beta_phrase = 'urge clog right example dish drill card maximum mix bachelor section select' 
//const beta_url = 'https://api.s0.b.hmny.io'
const beta_url = 'http://34.238.42.51:9500'
const beta_private_key = '01F903CE0C960FF3A9E68E80FF5FFC344358D80CE1C221C3F9711AF07F83A3BD'



module.exports = {


  networks: {
    // Useful for testing. The `development` name is special - truffle uses it by default
    // if it's defined here and no other network is specified at the command line.
    // You should run a client (like ganache-cli, geth or parity) in a separate terminal
    // tab if you use this network and you must also set the `host`, `port` and `network_id`
    // options below to some value.
    //
    development: {
      network_id: '2', // Any network (default: none)
      provider: () => {
        const truffleProvider = new TruffleProvider(
          url,
          { memonic: phrase },
          { shardID: 0, chainId: 2 },
          { gasLimit: '936475', gasPrice: '1000000000' },
        );
        const newAcc = truffleProvider.addByPrivateKey(private_key);
        truffleProvider.setSigner(newAcc);
        return truffleProvider;
      },
    },
    testnet: {
      // host: 'localhost', // Localhost (default: none)
      // port: 9500, // Standard Ethereum port (default: none)
      network_id: '2', // Any network (default: none)
      provider: () => {
        const truffleProvider = new TruffleProvider(
          beta_url,
          { memonic: beta_phrase },
          { shardID: 0, chainId: 2 },
          { gasLimit: '6721900', gasPrice: '1000000000' },
        );
        const newAcc = truffleProvider.addByPrivateKey(beta_private_key);
        truffleProvider.setSigner(newAcc);
        return truffleProvider;
      },
    },
  },

  // Set default mocha options here, use special reporters etc.
  mocha: {
    // timeout: 100000
  },

  // Configure your compilers
  compilers: {
    solc: {
      // version: '0.5.1', // Fetch exact version from solc-bin (default: truffle's version)
      // docker: false, // Use "0.5.1" you've installed locally with docker (default: false)
      // settings: {
      //   // See the solidity docs for advice about optimization and evmVersion
      //   optimizer: {
      //     enabled: false,
      //     runs: 200,
      //   },
      //   evmVersion: 'homestead',
      // },
    }
  }
}
```

## 2\_deploy\_HarmonyERC20.js

```text
var HarmonyERC20 = artifacts.require("HarmonyERC20");

module.exports = function(deployer, network, accounts) {

const name = "HarmonyERC20"
const symbol = "H20"
const decimals = 18
const amount = 1000000
const tokens = web3.utils.toWei(amount.toString(), 'ether')

deployer.then(function() {
  return deployer.deploy(HarmonyERC20, name, symbol, decimals, tokens).then(function() {
    });
  });
};
```

## HarmonyMintable.sol

```text
pragma solidity >=0.4.21 <0.6.0;

import "openzeppelin-solidity/contracts/token/ERC20/ERC20Detailed.sol";
import "openzeppelin-solidity/contracts/token/ERC20/ERC20Mintable.sol";
import "openzeppelin-solidity/contracts/token/ERC20/ERC20.sol";

contract HarmonyERC20 is ERC20, ERC20Detailed, ERC20Mintable {
      constructor(string memory _name, string memory _symbols, uint8 _decimals, uint256 _amount) 
        ERC20Detailed(_name, _symbols, _decimals)
        public {

        _mint(msg.sender, _amount);
    }
}
```

## HarmonyERC20.sol

```text
pragma solidity >=0.4.21 <0.6.0;

import "openzeppelin-solidity/contracts/token/ERC20/ERC20Detailed.sol";
import "openzeppelin-solidity/contracts/token/ERC20/ERC20.sol";

contract HarmonyERC20 is ERC20, ERC20Detailed {
      constructor(string memory _name, string memory _symbols, uint8 _decimals, uint256 _amount) 
        ERC20Detailed(_name, _symbols, _decimals)
        public {

        _mint(msg.sender, _amount);
    }
}
```

## Package.json

```text
{
  "name": "harmony-erc20",
  "version": "1.0.0",
  "description": "Harmony sample ERC20 deploy",
  "main": "truffle.js",
  "dependencies": {
    "@harmony-js/core": "^0.1.22",
    "tslib": "^1.10.0",
    "openzeppelin-solidity": "^2.2.0"
  }
}
```

