---
description: This tutorial will teach you how to use NFT.Storage to store NFTs on IPFS and Filecoin for the Harmony blockchain.
---

# Using NFT.Storage

**NFT.Storage** is a long-term storage service designed for **off-chain** NFT data (like metadata, images, and other assets). Data is [content addressed](https://nftschool.dev/concepts/content-addressing) using **IPFS**, meaning the URL pointing to a piece of data (“ipfs://…”) is completely unique to that data. IPFS URLs can be used in NFTs and metadata to ensure the NFT forever actually refers to the intended data (eliminating things like rug pulls). IPFS URLs are storage layer agnostic - meaning you can store your data on [many storage layers at once](https://nft.storage/blog/post/2021-12-14-storage-layer-maximalism/) (whether it be on local storage, cloud storage, or multiple decentralized storage networks.

NFT.Storage stores many copies of uploaded data on the public **IPFS** network and **Filecoin** network in two primary ways: in dedicated IPFS servers managed by NFT.Storage, and decentralized on [Filecoin](https://filecoin.io/). Since IPFS is a standard used by many different storage services, it's easy to redundantly store data uploaded to NFT.Storage on any other IPFS-compatible storage solutions.

This tutorial will walk you through the process of creating a simple NFT on Harmony, using NFT.Storage to store off-chain NFT data on IPFS and Filecoin to achieve a fully decentralized, verifiable NFT.

### Overview

This tutorial will walk you through the process of creating a simple NFT on Harmony, using NFT.Storage to store off-chain NFT data on IPFS and Filecoin to achieve a fully decentralized, verifiable NFT. It is organized in 4 steps:

1. Write an NFT smart contract using Truffle
2. Connect to Harmony blockchain via Metamask
3. Upload your NFT assets via NFT.Storage
4. Invoking NFT smart contract to mint NFT via MetaMask

### Prerequisites

This tutorial requires basic knowledge about Harmony blockchain, HRC721/ERC721, Truffle and Metamask.

Before you start this tutorial, make sure you have installed these necessary tools:

+ [Node.js](https://nodejs.org/en/)
+ [Truffle](https://trufflesuite.com/docs/truffle/quickstart.html#installing-truffle)
+ [Metamask browser extension](https://metamask.io/download/)

### Part 1: Write the NFT smart contract

In this step, we will create a React application and use the Truffle framework to developer, compile, and deploy our NFT smart contract. 

1. **Create the React project and initialize Truffle**

   ```shell
   npx create-react-app harmony-nft
   cd harmony-nft
   truffle init
   ```

   Once the project is created and initialized successfully, you will have a basic React project structure and Truffle project structure which will include:

   + `contracts` for our smart contracts
   + `migrations` for the deployment scripts
   + `truffle.js` for all Truffle-related configurations

2. **Create the Solidity contract**

   Next, let's create the smart contract. We will use the [ERC721URIStorage contract from the Openzepplin contracts library](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol) so that our NFT contract inherits standard ERC721 functions as well as storage based token URI management.
   
   First, install `openzepplin` via npm:

   ```shell
   // run this command under harmony-nft folder
   npm install @openzeppelin/contracts
   ```

   Then create a `HarmonyNFT.sol` file under the `contracts` folder, and copy the ERC721URIStorage smart contract code into that file.

   ```solidity
   // SPDX-License-Identifier: UNLICENSED
   pragma solidity >=0.4.22 <0.9.0;
   
   import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
   import "@openzeppelin/contracts/utils/Counters.sol";
   
   contract HarmonyNFT is ERC721URIStorage{
       using Counters for Counters.Counter;
       Counters.Counter private _tokenIds;
   
       event NewHarmonyNFT(address sender, uint256 tokenId, string tokenURI);
       
       //Deploy EPC721 with name and description specified.
       constructor() ERC721 ("ETH on Harmony using NFT.Storage", "HNFT") {}
   
   	//Mint a new NFT Item and update its tokenURI with IPFS link.
       function mintItem(string memory tokenURI) public{
           _tokenIds.increment();
           uint256 newItemId = _tokenIds.current();
           _mint(msg.sender, newItemId);
           _setTokenURI(newItemId, tokenURI);
           emit NewHarmonyNFT(msg.sender, newItemId, tokenURI);
       }
   }
   ```

3. **Build smart contract**

   Now the NFT smart contract is ready, let's compile it.

   ```shell
   truffle compile
   ```
   
   If the contract compiles successfully, related manifest files will be generated in `build/contracts`, which we will use later in this tutorial. (Tip: If you get a solidity compiler version incompatibility error, we can configure it in `truffle.js` to use the right compiler version.)
   
4. **Create deployment script**

   Next, we need to to deploy the Solidity contract to the Harmony blockchain. Create a file named `2_deploy_contracts.js` under `migrations` folder with the following code:

   ```javascript
   var HarmonyNft = artifacts.require("HarmonyNFT");
   
   module.exports = function(deployer) {
     deployer.deploy(HarmonyNft);
   };
   ```

5. **Deploy NFT contract to Harmony Testnet**

   In order to deploy the NFT smart contract to Harmony Testnet, you need to let Truffle which network configuration and which Harmony wallet to use. You can do this by configuring truffle in `truffle-config.js`.

   First, install `@truffle/hdwallet-provider` via npm.

   ```shell
   npm install --save-dev @truffle/hdwallet-provider
   ```

   Add harmony testnet configuration to `truffle-config.js` file. Also make sure requesting some TestNet token (ONE) from [Harmony TestNet Faucet](https://faucet.pops.one/) to the wallet so we can pay for transaction fees for smart contract deployment.

   ```javascript
   const HDWalletProvider = require('@truffle/hdwallet-provider');
   //If you have a Harmony wallet in MetaMask, you can export the private key.
   const privateKeyTest = '<ADD-YOUR-PRIVATE-KEY-HERE>';
   
   ....<other code>....
   networks: {
       harmonyTestnet: {
         provider: () => {
           if (!privateKeyTest.trim()) {
             throw new Error(
               'Please enter a private key with funds, you can use the default one'
             );
           }
           return new HDWalletProvider({
             privateKeys: [privateKeyTest],
             providerOrUrl: 'https://api.s0.b.hmny.io',
           });
         },
         network_id: 1666700000,
       },
     },
   ... <other code>...
   ```

   Now the truffle configuration is all set, we can run the following command to deploy the NFT contract to Harmony Testnet.

   ```shell
   truffle deploy --network harmonyTestnet
   ```

   Once the smart contract is deployed success, remember to record your **smart contract address** which we will also use later. You can also find your NFT contract on [Harmony Testnet blockchain explorer](https://explorer.pops.one/hrc721), also test it on [Remix](https://remix.ethereum.org/).

### Part 2: Connect to Metamask 

In this step, we will write some front-end code to connect to a MetaMask wallet so that you can use it to mint the NFT and pay transaction fees. 

Before we move forward, make sure we have installed MetaMask browser extension and add Harmony Network RPC Endpoint (we will use Harmony Testnet in this tutorial). Check more instructions [here](https://docs.harmony.one/home/network/wallets/browser-extensions-wallets/metamask-wallet#1.-adding-a-custom-rpc-endpoint). 

Now, let's start coding. 

1. **Create a WalletConnect component**

   This component will detect the wallet provider and connect to MetaMask. Go to the `harmony-nft/src` folder which was created as part of your React app in Part 1. 

   Within `harmony-nft/src`, create a new folder `components`. Inside `components`, create a `WalletConnect.js` file and paste in the following code: 

   Also make sure requesting some TestNet token (ONE) from [Harmony TestNet Faucet](https://faucet.pops.one/) to the wallet so we can pay for transaction fees for minting NFT on Harmony Blockchain.

   ```javascript
   //The core code to detect wallet provider and connect to MetaMask
   const connectWalletHandler = async() => {
   		if (window.ethereum && window.ethereum.isMetaMask) {
   			console.log('MetaMask Here!');
   
   			try {
   				const accounts = await window.ethereum.request({ method: 'eth_requestAccounts'});
   				accountChangedHandler(accounts[0]);
   				setConnButtonText('Wallet Connected');
   				setWalletConnected(true);
   			} catch (error) {
   				setErrorMessage(error.message);
   			}
   
   		} else {
               setWalletConnected(false);
   			console.log('Need to install MetaMask');
   			setErrorMessage('Please install MetaMask browser extension to interact');
   		}
   	}
   ```

2. **Add the WalletConnect component to `App.js`**

   ```javascript
   import WalletConnect from './components/WalletConnect'
   ...<other code>...
   function App() {
     return (
       <div className='App'>
         <div className='logos'>
           <img className='harmony' src={harmonyLogo} alt="Harmony Logo"/>
           <img className='nftStorage' src={nftStorageLogo} alt="Harmony Logo"/>
         </div>
         <WalletConnect/>
       </div>
     );
   }
   ```

   Now, let's test the wallet connection function. Run the following command to start the React application.

   ```shell
   npm start
   ```

   Once the application is up, you can click the `Connect Wallet` button to invoke the MetaMask and authorize the connection.

   ![Connect to MetaMask](https://bafybeidngoqv4qq46bcb434em6skbg2b4ogyate3fwewutro67pm2j34qy.ipfs.dweb.link/HarmonyNFT-WalletConnect.png)

   

### Part 3: MintNFT process

In this step, we will write the code that mints the NFT. Have the following items ready:

+ NFT Smart Contract deployed to Harmony Testnet. 
  + NFT contract address
  + NFT contract manifest JSON file

+ Metamask browser extension installed and filled your wallet with some TestNet token - ONE.

In this step, we will write code to mint a NFT on Harmony blockchain and also upload your NFT asset and metadata to IPFS & Filecoin so that your NFT is truly decentralized other than storing on centralized cloud. Here, we will use a tool called [NFT.Storage](https://nft.storage/) which offers free and long-term storage on **IPFS** and **Filecoin**.

1. **Create a NFT.Storage account.**

   In order to use NFT.Storage to upload NFT assets, we will need to sign up an account and create a new API Key which will be used in our code to access NFT.Storage services. 

   ![NFT Storage API Key](https://bafybeibckdbu5uorpl6itmukw7o35zq3xsvzeynwxdkbl3azrd64xwtgfm.ipfs.dweb.link/NFTStorage-API-KEYS.png)

   Also we will use ethers to interact with MetaMask to invoke NFT smart contract which is deployed on Harmony blockchain. 

2. **Create mintNFT component**

   Now we will create a `MintNFT.js` component in `src/components` folder. Let's first create a form to upload NFT Images in `MintNFT.js`.

   ```javascript
   import React, {useState} from 'react';
   const MintNFT =() => {
     const [uploadedFile, setUploadedFile] = useState();
   
     const handleFileUpload = (event) => {
         setUploadedFile(event.target.files[0]);
     }
   
     const mintNFTToken = async(inputFile) =>{
         //Will add MintNFT logic here.
     }
   
     return(
         <div className='MintNFT'>
             <form>
                 <h3>Mint your NFT on Harmony & Filecoin/IPFS</h3>
                 <input type="file" onChange={handleFileUpload}></input>
                 <button onClick={e=>mintNFTToken(e, uploadedFile)}>Mint NFT</button>
             </form>
         </div>
     )
   }
   export default MintNFT;
   ```
   
   Once the NFT image is captured via form upload, we will upload the NFT asset and metadata to IPFS/Filecoin via NFT.storage, then invoke the NFT smart contract on Harmony to mint a new item. The basic logic will be like following:
   
   ```javascript
   const mintNFTToken = async(event, uploadedFile) =>{
       //1. Upload NFT content via NFT.storage
       const metaData = await uploadNFTContent(uploadedFile);
   
       //2. Mint a NFT token on Harmony
       const mintNFTTx = await sendTxToHarmony(metaData);
   }
   ```
   
3. **Upload NFT asset via NFT.Storage**

   Now let's set up NFT.Storage so you can upload NFT assets.

   + Install NFT.Storage dependency in your React app.

     ```shell
     npm install nft.storage
     ```

   + We are all set to start coding your logic. Add the following code blocks to `MintNFT.js`. (You can also [copy the entire sample file from Github](https://github.com/longfeiWan9/harmony-nft-demo/blob/master/src/components/MintNFT.js).)
   
    First, import NFTstorage and get the API Key that we created in the first step.

     ```javascript
     import { NFTStorage } from "nft.storage";
     const APIKEY = '<Your-API-KEY>';
     ...
     ```

   + Then, initialize the NFTStorage connection using your API KEY.

     ```javascript
     const uploadNFTContent = async(inputFile) =>{
     	//Initialize NFTStorage
         const nftStorage = new NFTStorage({token: APIKEY,});
     }
     ```

   + We can simply call `nftStorage.store()` to upload NFT content, which will upload your NFT as well as its related metadata to IPFS & Filecoin. You can customize your NFT metadata by updating properties like name and description.

     ```javascript
     const uploadNFTContent = async(inputFile) =>{
         //Initialize NFTStorage
         const nftStorage = new NFTStorage({token: APIKEY,});
         try {
             //Upload NFT to IPFS & Filecoin
             const metadata = await nftStorage.store({
                 name: 'Harmony NFT collection',
                 description: 'This is a Harmony NFT collenction stored on IPFS & Filecoin.',
                 image: file
             });
             return metadata;
     
         } catch (error) {
             setErrorMessage("Could not save NFT to NFT.Storage - Aborted minting.");
             console.log(error);
         }
     }
     ```
   
     If NFT asset is uploaded successfully, NFT.Storage will do the following two things:

     + Store NFT image on IPFS & Filecoin.
     + Update NFT metadata with the IPFS link to your NFT image, then also store the NFT metadata on IPFS & Filecoin.
   
4. **Mint a new NFT on Harmony**

   After getting the metadata on IPFS, we can invoke the NFT smart contract on Harmony to mint a new NFT using that metadata as tokenURI.

   In this step, we will need to use `ethers` to interact with Metamask, so we first install this dependency.

   ```shell
   npm install ethers
   ```

   In order to invoke the NFT contract we have deployed to Harmony Testnet, we need to grab the contract ABI from the manifest JSON file which was generated via smart contract compilation.

   ```shell
   //run this command under harmony-nft folder
   cp ../build/contracts/HarmonyNFT.json src/abi/
   ```

   Then we are ready to write code to send MintNFT transaction in `MintNFT.js` . This will import ethers and the smart contract manifest file, and also create a `nftContractAddress` for the deployed NFT contract. 

   ```javascript
   import HarmonyNFT from "../abi/HarmonyNFT.json";
   import { ethers } from 'ethers';
   
   const nftContractAddress = '0x494543afa8445025B9dBc7a39EdC7Fc624cA46F6';
   ```

   Then we can load the deployed NFT contract and invoke mintItem method.

   ```javascript
   //Add this code to load deployed NFT contract and invoke mintItem method.
   const sendTxToHarmony = async(metadata) =>{
       try {
           const provider = new ethers.providers.Web3Provider(window.ethereum);
           const connectedContract = new ethers.Contract(
               nftContractAddress,
               HarmonyNFT.abi,
               provider.getSigner()
           );
           const mintNFTTx = await connectedContract.mintItem(metadata.url);
           console.log(mintNFTTx);
       } catch (error) {
           setErrorMessage("Failed to send tx to Harmony.");
           console.log(error);
       }
   }
   ```

5. **Preview the new minted NFT**  

   By now, we have all the codes to upload NFT data, send mint item transaction to Harmony. If everything works as expected, we will be able to mint a fresh NFT with its images and metadata stored on IPFS & Filecoin, minting transaction recorded on Harmony Blockchain. Let's add some code to preview our fresh minted NFT, including the NFT image, NFT metadata on IPFS and mintNFT transaction on Harmony.

   ```javascript
   const MintNFT =() => {
     ...
         const [imageView, setImageView] = useState();
         const [metaDataURL, setMetaDataURl] = useState();
         const [txURL, setTxURL] = useState();
         const [txStatus, setTxStatus] = useState();
     ...
     const mintNFTToken = async(inputFile) =>{
         ...
         //3. review your nft
         previewNFT(metaData, mintNFTTx);
     }
     ...
     const previewNFT = (metaData, mintNFTTx) =>{
         let imgViewString = getIPFSGatewayURL(metaData.data.image.pathname);;
         setImageView(imgViewString);
         setMetaDataURl(getIPFSGatewayURL(metaData.url));
         setTxURL('https://explorer.pops.one/tx/'+ mintNFTTx.hash);
         setTxStatus("NFT is minted successfully!");
     }
   
     //
     const getIPFSGatewayURL = (ipfsURL)=>{
         let urlArray = ipfsURL.split("/");
         let ipfsGateWayURL = `https://${urlArray[2]}.ipfs.dweb.link/${urlArray[3]}`;
         return ipfsGateWayURL;
     }
     ...
     return(
         <div className='MintNFT'>
             <form>
                 <h3>Mint your NFT on Harmony & Filecoin/IPFS</h3>
                 <input type="file" onChange={handleFileUpload}></input>
                 <button onClick={e=>mintNFTToken(e)}>Mint NFT</button>
             </form>
             {errorMessage}
             {txStatus && <p>{txStatus}</p>}
             {imageView && <img className='NFTImg' src={imageView} alt="NFT image preview"/>}
             {metaDataURL && <p><a href={metaDataURL}>Metadata on IPFS</a></p>}
             {txURL && <p><a href={txURL}>See the mint transaction</a></p>}
         </div>
     )
   }
   ```

   You can find the full [MintNFT.js file on Github](https://github.com/longfeiWan9/harmony-nft-demo/blob/master/src/components/MintNFT.js).

### Let's run it

Now that we've finished writing all the code, we can run `npm start` to start our React application. If everything is working, you should see a page like this:

![HarmonyNFT-start-app](https://bafybeifkrkikkkc5uhj4l7pthq4gp6ujqkwfgs36gismt724wln5ric2uy.ipfs.dweb.link/HarmonyNFT-start-app.png)

Once we connect to MetaMask and upload a image to mint NFT, we will need to sign the transaction via MetaMask. Then a new NFT on Harmony is minted. We can also check the NFT metadata on IPFS and the minting transaction on Harmony Testnet.

![Mint NFT Success](https://bafybeihkk5n3up4cualw5e5psrph5y6r4zuktybu6ftobibdi77evys3je.ipfs.dweb.link/HarmonyNFT-mint.png)

![NFT Metadata on IPFS](https://bafybeicw64qqgrprcs4fqvc4ihryr2bz5a3je4kbbguzwnrv3xdbqfiz5m.ipfs.dweb.link/HarmonyNFT-IPFS-Metadata.png)

Congratulations! You have written a simple React app for minting NFTs on Harmony with storage on IPFS and Filecoin. Feel free to explore more possibilities. 

Looking for the sample code from this tutorial? You can find it in the [harmony-nft-demo](https://github.com/longfeiWan9/harmony-nft-demo) Github repo.
