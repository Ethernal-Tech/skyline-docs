# Technical Design

This chapter presents a concise overview of the Skyline Bridge architecture. As previously emphasized, Skyline is explicitly designed to facilitate secure, decentralized, and bi-directional transfers of native blockchain assets thereby ensuring seamless interoperability between supported blockchain networks.

Skyline's architectural design incorporates robust mechanisms for securely handling native tokens on source and on the destination blockchain. Through this secure, multisignature-based handling approach, asset integrity and value preservation are consistently maintained throughout the bridging process. Consequently, users gain effortless access to cross-chain applications, tokens within the different ecosystem, and blockchain dApps.

At its core, Skyline functions as a dedicated, independent blockchain network with its own decentralized validator nodes. These validators play an essential dual role:

1. Block production

* Validators produce new blocks on the Skyline blockchain, maintaining the network's decentralized consensus and security.

2. Information collection and validation

* Validators employ specialized, secure components - referred to as trusted components - to collect accurate bridging-related data from supported ecosystems.

3. Batch creation

Moreover, these trusted components are instrumental in creating structured batches of validated bridging requests. Each batch encapsulates multiple validated bridging requests, optimally organized for efficient submission to the destination blockchain. After validator consensus and cryptographic signing, Batches are securely relayed to the target blockchain network.

The following sections will provide explanations of Skyline's key architectural components, clearly outlining their roles, interdependencies, and the specific dataflows occurring within the system.