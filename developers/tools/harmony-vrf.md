# Harmony VRF

## What is Harmony VRF

Harmony brings the technology of VRF \(Verifiable Random Function\) natively on chain to create a optimal solution for randomness that is unpredictable, unbiasable, verifiable and immediately available. Harmony VRF is a unique construction based on our existing cryptographic primitive of BLS signatures which makes the computation efficient without extra burden to our network validators. Harmony VRF is available for every single block and any smart contract can access the random output through a precompiled contract without paying additional fees.

VRF is a cryptographic invention to solve the problem of onchain randomness. VRF introduces the cryptographic construction where a private key SK is used to work on an arbitrary message and produce a unique and random output along with a proof. The validity of the random output can be verified by any one who knows the corresponding public key PK and the proof. 

Harmony supports the on-chain verifiable random source based on VRF \(Verifiable Random Function\). Specifically, for every new block, the block producing validator computes a VRF based on his private key and the latest block hash to produce a 32-bytes VRF output and 96-bytes proof. The VRF output and proof are concatenated as a 128-bytes data and put in the VRF field of the header of the newly proposed block. 

## How to Access Harmony VRF within Smart Contract

The VRF data are available to be consumed by any chain clients by querying the block header. We also exposed the VRF data in the smart contract level via a new EVM precompiled contract at address 0xff. Any smart contract on Harmony can access it with following solidity assembly code:

```text
  function vrf() public view returns (bytes32 result) {
    uint[1] memory bn;
    bn[0] = block.number;
    assembly {
      let memPtr := mload(0x40)
      if iszero(staticcall(not(0), 0xff, bn, 0x20, memPtr, 0x20)) {
        invalid()
      }
      result := mload(memPtr)
    }
  }
```

Note the input of the precompiled contract at 0xff is the block number for which the VRF is requested. The block number should be only within the last 256 blocks. If a block number outside this range is provided, the current block's VRF will be returned.

## How Harmony VRF is Constructed

Harmony builds on the existing cryptographic primitive of BLS signatures which are currently used for block signing and consensus to create an efficient and secure VRF construction. The BLS-based VRF works as follows. Given a VRF input M, a BLS private key SK is first used to sign on M to produce a signature S=sign\(SK, M\). Then the signature is hashed with sha256 to produce the VRF random output R=hash\(S\), and the signature itself becomes the VRF proof P=S. The VRF output R can be verified with the proof P by checking that P is the correct signature from PK on message M and that hash\(P\)=R. More formally, the BLS-based VRF construction \(Keygen, Compute, Verify\) can be specified as follows:

* Keygen\(r\) → \(PK, SK\). The BLS key generation algorithm produces a pair of public key PK and private key SK.
* Compute\(SK, M\): Hash\(Sign\(SK, M\)\) → \(R, P\). The computation of VRF output R is the hashing of the signature signed with the private key SK on message M. The VRF proof P equals the signature from Sign\(SK, M\).
* Verify\(PK, M, R, P\): SigVerify\(PK, P, M\)=True & Hash\(P\)=R. The verification of the VRF works by checking 1\) the VRF proof P is the correct signature from public key PK and message M; 2\) the VRF output R equals the hash of P.

## What Harmony VRF Brings to your Dapps

Harmony VRF brings the opportunity for developers to build trust-worthy and fair Dapps and protocols on chain. To name a few potential applications using VRF:

1. Make blockchain games provably fair and entertaining by using VRF to generate random game scenarios, distribute loot fairly and shuffle players unpredictably.
2. Randomly and fairly assign tasks or assets to participants of DAO, DeFi or NFT.
3. Select a random sample of protocol validators or governance voters from all participants for consensus or decentralized governance.

With Harmony VRF, a new realm of randomness-based trust-worthy applications can be built natively on Harmony blockchain. Developers with a security-focused mindset can feel safe to build applications using Harmony’s secure on-chain randomness. It’s guaranteed by cryptography with verifiable proof that no malicious participants are able to predict or influence the random outcome and make unfair profits. Additionally, Harmony VRF is available on every block of all 4 shards in Harmony and is easily accessible through a simple smart contract call without extra fee.  


