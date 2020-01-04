---
title: Analyze Solution
has_children: false
nav_order: 8
---

# Analyze Solution

In this section, we will go into greater detail about the decisions made and why we believe that they are correct and suitable in the new architecture of GRAMA.

Go was the selected programming language of choice for the rewrite from scratch because of its support, simplicity, very easy cross-compilation, and built-in concurrency capabilities.  Go was created by some of the same individuals that brought us C, UTF8, and Unix, basically very smart people.  Go is not as low level as C or C++, the most commonly found languages in the space, so there are less inherent risks of exploitation.

Badger is a key-value file storage system that provides high-end performance on more common SSD drives.  It is written in Go and does not require any external dependencies or interfacing.  There are forks of go-eth (Ethereum) that use badger due to its performance.  LevelDB implementations, at the time of writing, require interfacing overhead between Go and its native language.

Noise protocol is written in Go by Perlin Network and provides end to end encryption and Kademlia hash table routing.  The interface is simple and allows for granular control of message formats while simplifying NAT traversal out of the box.  LibP2P by IPFS is another popular choice for distributed networks written in Go but suffers from a specific use case not closely aligned with GRAMA’s.    

ED25519 is an elliptic curve public-key signature algorithm used for accounts due in fact that it provides fast key generation, signing, and signature verification.  It provides strength similar to a 3000 bit RSA and has a 2^128 target while avoiding side-channel leakage attacks.  Public keys are small containing only 32 bytes without compression.  This allows GRAMA to maintain its lightweight data requirements.  

Delegated proof of stake adds a second layer of validation and investment that is self-regulated where all elected delegates in a term must validate every block.  Delegates must also come to a majority agreement of 75% on every block in order for the block to be considered valid.  

Before a delegate’s turn in block creation, it must submit a bond transaction to the network that will be held until it expires or used in a valid forfeiture.  The bond transaction will be included by the next delegate if forfeit or removed from the pool.  Delegates that do not produce a block within 5 seconds or it is not voted valid loses its turn and bond.  

Delegated proof of stake allows for offline staking and reward potential for its constituents with kickbacks and network improvements.  Accounts can elect a delegate that provides rewards creating the potential for staking pools. 

Account sidechain proof of ownership empowers the modular design of GRAMA while allowing for easy additions of functionality based on an account.  Ownership is proven by the account signing transactions that can be validated with the signature, sequence, and its publicly known public key.  

Resource usage is light and relies heavily on the underlying cryptography which means if an account is compromised, which will happen as someone always get social engineered, the damage is limited to only that account, the perpetrator cannot prove ownership of any other account.  

Required operation size for a connected node grows linearly with the number of active accounts.  Account lookup, along with all sections of GRAMA’s code is asymptotically optimized for performance.

The popular vote was selected as an easy no-nonsense way of calculating totals at any given time on the blockchain.  Delegates are easily selected from most votes to least with only the top 21 being selected for the next term.  Delegates must provide KYC information before being accepted and the cost of maintaining minimum balances alleviates any form of Sybil attack against the voting process.

Total supply exists at the very beginning and is held in genesis accounts that are hardcoded into the consensus protocol and controlled by the foundation.  Fraud is easily shown by the internal reporting requirements of the foundation that will make all transactions public knowledge. 
