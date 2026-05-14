# Conceptual overview of Skyline Bridge

The Skyline bridging process encompasses several clearly defined phases, each designed for maximum security, transparency, and ease-of-use. The entire workflow is orchestrated to ensure decentralized integrity and a seamless user experience. Each step of the process is thoroughly validated, providing robust protection against fraud and technical errors, while maintaining clear visibility for end-users.

Below is a comprehensive breakdown of the Skyline Bridge workflow:

1. **Transfer Initiation by End-User**  

* The bridging process begins at the user interface level, providing an intuitive and simple interaction. Users initiate a cross-chain asset transfer through Skyline's user-friendly interface. At this initial phase, the user explicitly selects:

  1. Source chain (e.g., Cardano or Apex Fusion’s Nexus

  2. Destination chain

  3. Connects wallet (e.g., Eternl or MetaMask)

  4. Proceeds to move funds

  5. User specifies the destination address, source token, and amount of tokens to send, and before submitting the transaction for moving funds, the user is presented    with information about the cost and timeframe for the execution

2. **Handling Tokens on Source Chain**

* Once the user confirms the transaction request, the Skyline system initiates a secure locking mechanism to lock the specified tokens on the originating blockchain. This locking process utilizes inherent security features provided by originating chain:

  1. Multisignature UTXO schemes provided by both Cardano and Apex Fusion’s Prime and Apex Fusion’s Vector ecosystems. This multisignature UTXO requires cryptographic signatures from multiple independent validator nodes to release the locked assets, thereby ensuring no single entity can unilaterally unlock tokens.

  2. Smart contract validation for EVM-type chains - this smart contract employs the elliptic-curve signatures for validation and consensus-based unlocking.

* This locking mechanism guarantees that tokens remain safely reserved and can only be unlocked once validators achieve consensus on this request, significantly reducing risk and enhancing security.

3. **Decentralized Validation and Consensus**

* The core of Skyline's security model is its decentralized validation approach, involving multiple independent validator nodes. These validators collectively perform thorough and rigorous verification procedures of bridging requests.

* The consensus mechanism utilized by Skyline validators is based on Istanbul Byzantine Fault Tolerance and ensures a secure and transparent approval process. Only after successfully reaching a consensus among validators does the bridging request receive final authorization to continue to the next stage. This ensures strict adherence to protocol standards and prevents fraudulent or erroneous transactions.  
  Following the consensus approval, validators group multiple validated bridging requests into a single aggregated transaction referred to as a Batch. This Batch transaction efficiently consolidates multiple requests and is cryptographically signed by the validators, ensuring integrity and authenticity. Once signed, the Batch transaction is finalized and prepared for secure submission to the destination blockchain.

* This structured and clearly-defined validation workflow enhances the bridge's operational efficiency, ensures rigorous security standards, and maintains full decentralization and transparency throughout the asset bridging process.

4. **Relaying Signed Transactions**

* Once a Batch is successfully signed by the validators, the Skyline bridge activates specialized blockchain entities known as Relayer. The Relayer performs a critical role within the bridging workflow - securely submitting Batches to the destination blockchain.

* The Relayer operates as neutral entities within the network. Skyline's system requires the existence of at least one trustworthy Relayer at any time, ensuring the reliable execution of validated transactions. The Relayers facilitates prompt and efficient communication between blockchains, ensuring bridging transactions are finalized without delays.

5. **Handling Tokens On Destination Chain**

* Once a batch - containing multiple validated bridging requests - successfully reaches the destination blockchain, the automatic unlocking mechanism for the corresponding tokens is initiated. Upon the batch transaction's successful execution on the destination blockchain, all tokens represented by bridging requests within that batch become immediately accessible to the end-users. This automated and secure unlocking process ensures seamless finalization of each bridging request contained within the batch, promptly making the wrapped assets available and effectively completing the cross-chain transfer.

* This simultaneous lock-unlock mechanism ensures secure asset representation across ecosystems, providing immediate liquidity, and enhancing overall cross-chain asset utility.
