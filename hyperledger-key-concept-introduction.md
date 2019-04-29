# Hyperledger fabric readthedocs - key concepts(introduction)
> [Link](https://hyperledger-fabric.readthedocs.io/en/release-1.4/blockchain.html)

> all the images are from the link above(hyperledger fabric readthedocs)

## What is a blockchain?
* A Distributed Ledger
![blockchain](https://hyperledger-fabric.readthedocs.io/en/release-1.4/_images/basic_network.png)
    * a blockchain ledger is often described as decentralized because it is replicated across many network participants, each of whom collaborate in its maintenance.
    * in additions to being decentralized and collaborative, the information recorded to a blockchain is append-only, using cryptographic techniques that gurantee that once a transaction has been added to the ledger it cannot be modified(immutabilitiy).
    * sometimes blockchain is described as **system of proof**
* smart contract
![smart contract](https://hyperledger-fabric.readthedocs.io/en/release-1.4/_images/Smart_Contract.png)
    * smart contract to provide controlled access to the ledger
    * can be written to allow participants to execute certain aspects of transactions automatically
* consensus
![consensus](https://hyperledger-fabric.readthedocs.io/en/release-1.4/_images/consensus.png)
    * the process of keeping the ledger transaction synchronized across the network is called consensus
    * to ensure that ledger update only when transactions are approved by the appropriate participants

## Why is a Blockchain useful?
* today's system of record
    * transacting must have their provenance establiched each time they're sold to ensure that the business selling an item possesses a chain of title verifying their ownership of it
    * modern technology has taken this process from stone tables and paper folders to hard drives and cloud platforms, but the underlying structure is the same
    * it's impossible with today's fractured approach to information and process sharing to build a system of record that spend a business network, even though the needs of visibility and trust and clear
* the blockchain difference
![blockchain](https://hyperledger-fabric.readthedocs.io/en/release-1.4/_images/future_net.png)
    * what if business networks had standard methods for establishing identity on the network, executing transactions, and storing data?
    * every participant has their own replicated copy of the ledger
    * unlike today's system, where a participant's private programs are used to update their private ledgers, a blockchain system has shared programs to update shared ledgers
    * with the ability to coordinate their business network through a shared ledger, blockchain networks can reduce the time, cost, and rist associated with private information and processing while improving trust and visibility
* What is Hyperledger Fabric?
    * by the Linux foundation from 2015
    * private and permissioned blockchain
    * the members of a Hyperledger fabric network enroll through a trusted Membership Service Provider(MSP)
    * offers the ability to create channels
    * shared ledger
        * world state and transaction log. each participant has a copy of the ledger to every Hyperledger fabric network they belong to
        * the world state component describes the state of the ledger at a given point in time. it's database of the ledger
        * transaction log is the update history of the world state
        * the ledger has a replaceable data for the world state
        * LevelDB, Couchdb is for world state
    * smart contracts
        * are written in chaincode and are invoked by an application external to the blockchain when that application needs to interact with the ledger
        * **in most cases, chaincode interacts only with the database component of the ledger, the world state, and not the transaction log**
        * Go, Node
    * privacy
        * as b2b network, there might be extremely sensitive about how much information they share
        * channel
    * consensus
        * the order of transactions must be established and a method for rejecting bad transactions that have been inserted into the ledger in error(or maliciously) must be put into place
        * This is throughly researched area of computer science
        * PBFT for file replicas to communicate with each other to keep each copy consistent
        * Bitcoin's Pow
        * Hyperledger fabric has been designed to allow network starters to choose a consensus mechanism
        * SOLO and Kafka