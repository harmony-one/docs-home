# Oracle: Band Protocol

## How to Interact with BandChain from Harmony Smart Contracts

We will go through each of these steps:

1. Requesting data using BandChain.js library
2. Using BandChain data in EVM Smart Contract in Harmony

### Requesting data using BandChain.js library <a id="e952"></a>

BandChain provides the[ BandChain.js](https://www.npmjs.com/package/@bandprotocol/bandchain.js) JavaScript library so developers can submit data requests right from their dApp client.

Once BandChain has successfully executed the requested oracle script, it will return the data and EVM proof payload back to the client to then be passed to our smart contracts in harmony blockchain.

Here is an example simple Node file requesting data using the library that queries the current Bitcoin\(BTC\) price from BandChain.

```text
const BandChain = require('@bandprotocol/bandchain.js');
const { Obi } = require('@bandprotocol/obi.js');//BandChain POA mainnet endpoint URL
//const endpoint = 'http://poa-api.bandchain.org';
//BandChain dev-net endpoint URL
const endpoint = 'http://guanyu-devnet.bandchain.org/rest';const getBTCPrice = async () => {
 // Instantiating BandChain with REST endpoint
 const bandchain = new BandChain(endpoint);// Create an instance of OracleScript with the script ID
 const oracleScript = await bandchain.getOracleScript(76);// Create a new request, which will block until the tx is confirmed
 try {
   const minCount = 3;
   const askCount = 4;
   const mnemonic =
     'panther winner rain empower olympic attract find satoshi meadow panda job ten urge warfare piece walnut help jump usage vicious neither shallow mule laundry';
   const requestId = await bandchain.submitRequestTx(
     oracleScript,
     {
       symbol: 'BTC',
     },
     { minCount, askCount },
     mnemonic
   );
   // Get final result (blocking until the reports & aggregations are finished)
   const finalResult = await bandchain.getRequestResult(requestId);
   let result = new Obi(oracleScript.schema).decodeOutput(
     Buffer.from(finalResult.response_packet_data.result, 'base64')
   );
   console.log('RequestID: ' + requestId);
   console.log(result);
 } catch {
   console.error('Data request failed');
 }
};getBTCPrice();
```

Now let’s go through each section of the code.

Import the library and declare the necessary variables:

```text
const BandChain = require('@bandprotocol/bandchain.js');
const { Obi } = require('@bandprotocol/obi.js');
```

The code requires two libraries:

* [@bandprotocol/obi.js](https://www.npmjs.com/package/@bandprotocol/obi.js): a helper library to assist us when encoding/decoding data to/from Band Protocol’s OBI standard
* [@bandprotocol/bandchain.js](https://www.npmjs.com/package/@bandprotocol/bandchain.js): the library that we’ll be using to make the queries to BandChain

Now, set the request parameters:

```text
// BandChain devnet endpoint URL
const endpoint = 'http://guanyu-devnet.bandchain.org/rest';
// Mnemonic of the account to make the query from.
const mnemonic =
 'panther winner rain empower olympic attract find satoshi meadow panda job ten urge warfare piece walnut help jump usage vicious neither shallow mule laundry';// Request parameters
const bandchain = new BandChain(endpoint);
const oracleScript = await bandchain.getOracleScript(76);
const minCount = 3;
const askCount = 4;
```

Here we set the values that we will be using to make the request

* `endpoint`: the endpoint we will make the query to
* `mnemonic`: the mnemonic we will use to make the query. The associated account must have a balance to make a request
* `bandchain`: contains the necessary functions we’ll need to make the request
* `oracleScript`: object containing details of the oracle script we will be querying
* `minCount`: the minimum number of BandChain’s validators that responds for us to consider the request successful
* `askCount`: the maximum number of validators that we want to respond to the request

Now make the Oracle request and get the random hash:

```text
const requestId = await bandchain.submitRequestTx(
   oracleScript,
   {
     symbol: 'BTC',
   },
   { minCount, askCount },
   mnemonic
 );
  // Get final result (blocking until the reports & aggregations are finished)
 const finalResult = await bandchain.getRequestResult(requestId);
 let result = new Obi(oracleScript.schema).decodeOutput(
   Buffer.from(finalResult.response_packet_data.result, 'base64')
 );
 console.log('RequestID: ' + requestId);
 console.log(result);
```

Finally, we execute the `submitRequestTx` member function of the previously declared bandchain object to make the oracle data request.

We can then do one of two things with regards to this request:

* Call `getRequestResult`, as we did here, to get the actual result of the request
* Call `getRequestProof` to get the proof bytes associated with the request

Both of these functions take in one argument, the `requestID` of the request you want to retrieve the result/proof from.

If the query is successful, the code should print a value similar to:

`{ price: 11406282500000n }`,

which is the retrieved price of Bitcoin multiplied by 1 billion.

### Using BandChain data in EVM Smart Contract in Harmony <a id="cc5a"></a>

Now that we know how to make a request to BandChain and retrieve the corresponding proof, we will now examine how we can use that proof in our smart contract.

The code below demonstrates an example contract that retrieves the latest price of Bitcoin from Band’s bridge contract and saves it onto the contract’s state:

```text
pragma solidity 0.6.11;
pragma experimental ABIEncoderV2;import {Obi} from "./libraries/Obi.sol";
import {IBridge} from "./interfaces/IBridge.sol";
import {IBridgeCache} from "./interfaces/IBridgeCache.sol";
import "openzeppelin-solidity/contracts/math/SafeMath.sol";contract SimplePriceDB {
   using SafeMath for uint256;
   using ResultDecoder for bytes;
   using ParamsDecoder for bytes;IBridge bridge;
   IBridge.RequestPacket req;uint256 public price;constructor(IBridge bridge_) public {
        bridge = bridge_;req.clientId = "from_scan";
       req.oracleScriptId = 76;
       // {symbol:"BTC"}
       req.params = hex"00000003425443";
       req.askCount = 4;
       req.minCount = 4;
   }// getPrice fetches the latest BTC/USD price value from the bridge // contract and saves it to state.
   
   function getPrice() public {
      (IBridge.ResponsePacket memory res,) = bridge.getLatestResponse(req);
       ResultDecoder.Result memory result = res.result.decodeResult();
       price = result.px;
   }
}
```

Okay, now let’s break down the code.

```text
import {Obi} from "./libraries/Obi.sol";
import {IBridge} from "./interfaces/IBridge.sol";
import {IBridgeCache} from "./interfaces/IBridgeCache.sol";
import "openzeppelin-solidity/contracts/math/SafeMath.sol";
```

Aside from OpenZeppelin’s [SafeMath.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/math/SafeMath.sol), the contract we will be writing requires three helper files specific to Band’s oracle and bridge architecture: `Obi.sol`, `Decoders.sol`, and `IBridgeWithCache.sol`.

### Obi.sol <a id="7f84"></a>

This contains a set of functions to help serialize and deserialize binary data when interacting with the BandChain ecosystem. The full standard specification can be found on their wiki and the code on the [BandChain repository](https://github.com/bandprotocol/bandchain/blob/master/bridges/evm/contracts/obi/Obi.sol).

### Decoders.sol <a id="007e"></a>

This is what we will use to work with data related to requests made on BandChain. This will help us in extracting the various information, such as the price value, we may need from the request response from Band’s oracle. The file is available from an oracle script’s bridge code tab on the devnet explorer. For this particular example, the code is available [here](https://guanyu-devnet.cosmoscan.io/oracle-script/76#bridge).

### IBridgeCache.sol <a id="d6df"></a>

The interface file for Band’s bridge contract. The code for this can also be found on the BandChain [repository](https://github.com/bandprotocol/bandchain/blob/master/bridges/evm/contracts/IBridgeCache.sol).

Now let’s look at the contract itself:

```text
contract SimplePriceDB {
   using SafeMath for uint256;
   using ResultDecoder for bytes;
   using ParamsDecoder for bytes;IBridge bridge;
   IBridge.RequestPacket req;uint256 public price;constructor(IBridge bridge_) public {
        bridge = bridge_;req.clientId = "from_scan";
       req.oracleScriptId = 76;
       // {symbol:"BTC"}
       req.params = hex"00000003425443";
       req.askCount = 4;
       req.minCount = 4;
   }// getPrice fetches the latest BTC/USD price value from the bridge // contract and saves it to state.   function getPrice() public {
      (IBridge.ResponsePacket memory res,) = bridge.getLatestResponse(req);
       ResultDecoder.Result memory result = res.result.decodeResult();
       price = result.px;
   }
}
```

The contract itself can then be further broken down into two parts: the `constructor` and the main `getPrice` function.

## Contract Constructor <a id="de69"></a>

```text
constructor(IBridge bridge_) public {
    bridge = bridge_;req.clientId = "from_scan";
   req.oracleScriptId = 76;
   // {symbol:"BTC"}
   req.params = hex"00000003425443";
   req.askCount = 4;
   req.minCount = 4;
}
```

The contract’s constructor takes one argument, the address of the bridge contract. It then sets the various fields of the req `RequestPacket` variable. This req variable will be what we will use as the key to match and retrieve the price from the bridge contract. Specifically, in this case, we set req to have the following parameters.

* `bridge`: the address of Band’s bridge contract on the blockchain this example contract is deployed to. See this [list](https://docs.bandchain.org/developer/dapp-integrations/supported-blockchains.html) for the chains that Band currently supports and corresponding contract addresses. You can deploy the bridge contract by yourself on the harmony chain. Bridge contract can be found [here](https://github.com/bandprotocol/bandchain/tree/master/bridges/evm).
* `clientId` \(“from\_scan”\): the unique identifier of this oracle request, as specified by the client.
* `oracleScriptId` \(76\): The unique identifier number assigned to the oracle script when it was first registered on Bandchain.
* `params` \(hex”00000003425443"\): The data passed over to the oracle script for the script to use during its execution. In this case, it is hex representation of the OBI-encoded request struct
* `minCount` \(4\): The minimum number of validators necessary for the request to proceed to the execution phase
* `askCount` \(4\): The number of validators that are requested to respond to this request

### getPrice Function <a id="d3dc"></a>

```text
// getPrice fetches the latest BTC/USD price value from the bridge // contract and saves it to state.function getPrice() public {(IBridge.ResponsePacket memory res,) = bridge.getLatestResponse(req);ResultDecoder.Result memory result = res.result.decodeResult();price = result.px;}
```

This is then the main function that we will use to fetch the price from Band’s bridge contract and save it into our price database contract’s state. It calls the bridge contract’s getLatestResponse to retrieve the latest request response associated with a BTC/USD price request. It then uses Decoders.sol’s decodeResult method to parse that response into a struct. Finally, we save the price value from that response into the contract’s price variable.

### References: <a id="44ed"></a>

1. [https://docs.bandchain.org/developer/dapp-integrations/requesting-data-from-bandchain.html\#requesting-data-using-the-bandchain-js-library](https://docs.bandchain.org/developer/dapp-integrations/requesting-data-from-bandchain.html#requesting-data-using-the-bandchain-js-library)
2. [https://docs.bandchain.org/developer/dapp-integrations/using-bandchain-data-evm.html](https://docs.bandchain.org/developer/dapp-integrations/using-bandchain-data-evm.html)

## Examples

Examples can be found here
https://github.com/harmony-one/band_oracle

### Requesting data using BandChain.js library  
https://github.com/harmony-one/band_oracle/blob/main/main.js

```
git clone https://github.com/harmony-one/band_oracle
cd band_oracle

yarn
node main.js
```

### Using BandChain data in EVM Smart Contract in Harmony
https://github.com/harmony-one/band_oracle

```
git clone https://github.com/harmony-one/band_oracle
cd band_oracle

yarn
export PRIVATE_KEY=place your private key here
yarn hardhat run ./scripts/deploy
```

contract's been deployed and you can call `getPrice` or `getMultiPrices` to get actual prices

Band’s StdReference contract for testnet
0xE740092E081CA7491A46C8Aa0175446e962e2A08

mainnet contract is coming soon 
