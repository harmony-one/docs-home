# Covalent

## Covalent

[Covalent](https://www.covalenthq.com/?utm\_source=harmony\&utm\_medium=partner-docs) provides a unified API to bring full transparency and visibility to assets across all blockchains including Harmony Mainnet and Testnet.

To get started, sign up for an [**API Key**](https://www.covalenthq.com/platform/?utm\_source=harmony\&utm\_medium=partner-docs).

|                                        _JSON support_                                        |                                       _CSV support_                                      |
| :------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------: |
| ![Developer Mode](https://www.covalenthq.com/static/images/partner-docs/developer\_mode.png) | ![Analyst Mode](https://www.covalenthq.com/static/images/partner-docs/analyst\_mode.png) |

The Covalent API is RESTful and offers the following out-of-the-box for _Harmony_:

| **Covalent API**          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Response formats**      | JSON and CSV                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **Real time response**    | 2 blocks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **Batch response**        | 30 minutes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **Request volume limit**  | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **Request rate limit**    | 5 requests per second                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **Base URL**              | https://api.covalenthq.com/v1/                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **Networks & `chain_id`** | <p>Mainnet: - <code>1666600000</code><br>Testnet: - <code>1666700000</code></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Supported Endpoints**   | <p><strong>Class A Universal</strong><br>- <a href="https://www.covalenthq.com/docs/api/#/0/Get%20token%20balances%20for%20address/USD/1666600000/?utm_source=harmony&#x26;utm_medium=partner-docs">Balances</a><br>- <a href="https://www.covalenthq.com/docs/api/#/0/Get%20transactions%20for%20address/USD/1666600000/?utm_source=harmony&#x26;utm_medium=partner-docs">Transactions</a><br>- <a href="https://www.covalenthq.com/docs/api/#/0/Get%20ERC20%20token%20transfers%20for%20address/USD/1666600000/?utm_source=harmony&#x26;utm_medium=partner-docs">Transfers</a><br>- <a href="https://www.covalenthq.com/docs/api/#/0/Get%20token%20holders%20as%20of%20any%20block%20height/USD/1666600000/?utm_source=harmony&#x26;utm_medium=partner-docs">Token Holders</a><br>- <a href="https://www.covalenthq.com/docs/api/#/0/Get%20log%20events%20by%20contract%20address/USD/1666600000/?utm_source=harmony&#x26;utm_medium=partner-docs">Log Events (Contract Address)</a><br>- <a href="https://www.covalenthq.com/docs/api/#/0/Get%20log%20events%20by%20topic%20hash(es)/USD/1666600000/?utm_source=harmony&#x26;utm_medium=partner-docs">Log Events (Topic Hash)</a></p> |

Try the supported endpoints directly in your browser from our [API Reference](https://covalenthq.com/docs/api/?utm\_source=harmony\&utm\_medium=partner-docs) or use the following code examples. **The JSON response format is the same for all endpoints:**

```
❴ 
    "data": ..., 
    "error": false,
    "error_message": null,
    "error_code": null
❵
```

#### Curl

```
curl -X GET "https://api.covalenthq.com/v1/{chain_id}/address/{address}/balances_v2/?key={YOUR API KEY}" -H "Accept: application/json"
```

#### JavaScript

```
const APIKEY = 'YOUR API KEY';
const baseURL = 'https://api.covalenthq.com/v1'
const HarmonyChainId = '1666600000'
const demoAddress = 'one1xfftrrcjnq807klgc4fu2k3stlgfzzh06tn09u'

async function getWalletBalance(chainId, address) {
    const url = new URL(`${baseURL}/${chainId}/address/${address}/balances_v2/?key=${APIKEY}`);
    const response = await fetch(url);
    const result = await response.json();
    const data = result.data;
    console.log(data)
    return data;
}

// Example address request
getWalletBalance(HarmonyChainId, demoAddress);
```

#### Python

```
import requests

API_KEY = 'YOUR API KEY'
base_url = 'https://api.covalenthq.com/v1'
harmony_chain_id = '1666600000'
demo_address = 'one1xfftrrcjnq807klgc4fu2k3stlgfzzh06tn09u'

def get_wallet_balance(chain_id, address):
    endpoint = f'/{chain_id}/address/{address}/balances_v2/?key={API_KEY}'
    url = base_url + endpoint
    result = requests.get(url).json()
    data = result["data"]
    print(data)
    return(data)


# Example address request
get_wallet_balance(harmony_chain_id, demo_address)
```

&#x20;

## Use Cases

The Covalent API supports a broad range of Web3 data use cases including:

|                                                                               |                                                                                       |                                                                                            |                                                                               |
| :---------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------: |
|  ![Gaming](https://www.covalenthq.com/static/images/partner-docs/gaming.png)  |        ![DeFi](https://www.covalenthq.com/static/images/partner-docs/defi.png)        |            ![KYC](https://www.covalenthq.com/static/images/partner-docs/kyc.png)           |  ![NFT](https://www.covalenthq.com/static/images/partner-docs/nft\_icon.png)  |
|                                     Gaming                                    |                                       DeFi Taxes                                      |                                             KYC                                            |                                      NFTs                                     |
| ![Wallets](https://www.covalenthq.com/static/images/partner-docs/wallets.png) |  ![Dashboards](https://www.covalenthq.com/static/images/partner-docs/dashboards.png)  | ![On-Chain Forensics](https://www.covalenthq.com/static/images/partner-docs/forensics.png) |     ![DAO](https://www.covalenthq.com/static/images/partner-docs/dao.png)     |
|                                    Wallets                                    |                                       Dashboards                                      |                                     On-Chain Forensics                                     |                                    DAO Data                                   |
| ![Trading](https://www.covalenthq.com/static/images/partner-docs/trading.png) | ![Predictions](https://www.covalenthq.com/static/images/partner-docs/predictions.png) |     ![Governance](https://www.covalenthq.com/static/images/partner-docs/governance.png)    | ![Pricing](https://www.covalenthq.com/static/images/partner-docs/pricing.png) |
|                                 DEXs & Trading                                |                                  Predictive Analytics                                 |                                         Governance                                         |                                    Pricing                                    |

Check out our collection of ready-to-ship [**Code Templates**](https://covalenthq.notion.site/dbf062042f4a463a950f0047b9df9ec1?v=2f7a0d7267034526a641ce7215dd7512/?utm\_source=harmony\&utm\_medium=partner-docs) that you can use to build your Web3 data-powered dApps.

&#x20;

## Resources

Here are some additional resources to help you get started with the Covalent API:

* [Harmony Network Details](https://www.covalenthq.com/docs/networks/harmony/?utm\_source=harmony\&utm\_medium=partner-docs)
* [Covalent API Reference](https://covalenthq.com/docs/api/?utm\_source=harmony\&utm\_medium=partner-docs)
* [Project Showcase](https://www.covalenthq.com/docs/project-showcase/?utm\_source=harmony\&utm\_medium=partner-docs)
* [API FAQs](https://www.covalenthq.com/docs/developer/faq/?utm\_source=harmony\&utm\_medium=partner-docs)
* [Discord Support](https://www.covalenthq.com/discord/?utm\_source=harmony\&utm\_medium=partner-docs)

&#x20;

## About Covalent

Covalent provides the industry-leading Unified API bringing visibility to billions of Web3 data points. Developers use Covalent to build exciting multi-chain applications like crypto wallets, NFT galleries, and investor dashboard tools utilizing data from most major blockchains. Covalent is trusted by a community of 15,000+ developers and powers data for hundreds of applications including 0x, Zerion, Rainbow Wallet, Rotki, Bitski and others.

[Website](https://www.covalenthq.com/?utm\_source=harmony\&utm\_medium=partner-docs) | [Discord](https://covalenthq.com/discord/?utm\_source=harmony\&utm\_medium=partner-docs) | [Telegram](https://t.me/CovalentHQ) | [Twitter](https://twitter.com/covalent\_hq) | [YouTube](https://www.youtube.com/channel/UCGn-T9qPiXAx490Wr6WPbOw/?utm\_source=harmony\&utm\_medium=partner-docs) | [WeChat](https://mp.weixin.qq.com/s?\_\_biz=MzU0MzY5ODMzMg==\&mid=2247483899\&idx=1\&sn=9c1d4df3acc04bc35c429b244307d3c7\&chksm=fb063d08cc71b41e2da96b4747513acf2ab9182babe57c135e4a7d1fef9255eb3b310217835c\&token=2144505038\&lang=zh\_CN#rd)
