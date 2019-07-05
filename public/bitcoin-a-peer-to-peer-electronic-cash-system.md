# Bitcoin: A Peer-to-Peer Electronic Cash System
> NAKAMOTO, Satoshi, et al. Bitcoin: A peer-to-peer electronic cash system. 2008.
> [Link to document](https://bitcoin.org/bitcoin.pdf)

## key sentences
* the bitcoin whitepaper. worth reading it.
* Merkle tree references: Protocols for public key cryptosystems
> MERKLE, Ralph C. Protocols for public key cryptosystems. In: 1980 IEEE Symposium on Security and Privacy. IEEE, 1980. p. 122-122.

## 1. Introduction
* There is the inherent weakness of the trust based model.
    1. there's no completely non-reversible transactions: possibility of reversal
    2. trusted 3rd party institutions cannot avoid mediating disputes
* cost of mediating disputes and payment uncertainities can be avoided in person by using physical currcncy, but no mechanism exists to make payments over a communications channel without a trusted party.
* What is needed is an electronic payment system based on cryptographic proof instead of trust. So we propose a solution to the double-spending problem using a peer-to-peer distributed timestamp server to generate computational proof of the chronological order of transactions.

## 2. Transactions
* we define an electronic coin as a chain of digital signatures
* the problem of course is the payee can't verify that one of the owners did not double-spending the coin. a common solution is to introduce a trusted central authority
* we need a way for the payee to know that the previous owners did not sign any earlier transactions. for our purpose, the earliest transaction is the one that counts, so we don't care about later attempts to double spend
* **the only way to confirm the absense of a transaction is to be aware of all transaction**
* transactions must be publicly announced, and we need a system for participants to **agree on a single history**(to prevent double-spending problem) of the order in which they were received.

## 3. Timestamp Server
* a timestamp server works by taking a hash of a block of items to be timestamped and widely publishing the hash, such as in a newspaper of usenet post. this proves that the data must have existed at the time. each timestamp includes the previous timestamp in its hash, forming a chain, with each additional timestamp reinforcing the ones before it.
* *timestamp server == blockchain == ledger?*

## 4. Proof-of-work
* similar to Adam Back's Hashcash
* Pow involves scanning for a value that when hashed, such as with SHA-256, the hash begins with a number of zero bits.
* the average work required is exponential in the number of zero bits required
* the block cannot be changed without redoing the work.
* PoW solves double-spending problem and problem of determining representation in majority decision making, as PoW is essentially one-CPU-one-vote
* proof-of-work difficluty is determined by a moving average targeting an average number of blocks per hour

## 5. Network
* steps to run the network are as follows
    1. New transaction are broadcast to all nodes
    2. Each node collects new transactions into a block
    3. Each node works on finding a difficult PoW for its block
    4. When a node finds a PoW, it broadcasts the block to all nodes
    5. **Nodes accepts the block only if all transactions in it are valid and not already spent**
    6. Nodes express their acceptance of the block by working on creating the next block in the chain, using the hash of the accpeted block as the previous hash
* branch: if two nodes broadcast different version of the next block simultaneously, some nodes may receive one or the other first. In that case, they work on the **first one they received, but save the other branch in cast it becomes longer**
* tolerant of dropped messages: if a node does not receive a block, it will request it when it receives the next block and realized it missed one.

## 6. Incentive
* coinbase transaction: by convention, the first transaction in a block is a special transaction that starts a new coin owned by the creator of the block
* the incentive can also be funded with transaction fees. this makes the network be completely inflation free
* Pros: the incentive may help encourge nodes to stay honest
* robustness: greedy attackers may find it more profitable to play by the rules, such rules that favour him with more new coins than everyone else combined, than to undermine the system and the validity of his own wealth

## 7. Reclaiming Disk Space
* Useing Merkle Tree: the spent transactions before it can be discarded to save disk space. to facilitate this without breaking the block's hash, transactions are hashed in a Merkle Tree, with only root included in the block's hash.
```diff
- TODO: What is the merkle tree?
```

## 8. Simplified Payment Verfification
* thanks to the merkle tree, a user only needs to keep a copy of the block headers of the longest proof-of-work chain, which he can get by querying newwork nodes until he's convinced he has the longest chain, and obtain Merkle branch linking the transaction to the block it's timestamped in.
* by linking a transaction to a plcae to the chain, a user can see that a network node has accepted it, and blocks added after it futher confirm the network has accepted it
* threat: transaction verification is vulnerable if the network is overpowered by an attacker. While network can verify transactions for themselves, the simplified methods can be fooled by an attacker's fabricated transactions for as long as the attacker can continue to overpower the network
* strategy to prevent from being fooled by attacker: accepting alerts from network nodes whtn they detect an invalid block, promting the user's software to download the full block and alerted transactions to confirm the inconsistency

## 9. Combining and Splitting Value
* it would be unwiedly to make a seperate transaction for every cent in a transter
* to allow value to be split and combined, transactions contain multiple inputs and outputs
* type of transactions: single/multiple input - multiple outputs(\* for payments and changes)
* there is never need to extract a complete standalone copy of a transaction's history

## 10. Privacy
TBU

## 11. Calculations
TBU

## 12. Conclusion
* started with the usual framework of coins made from digital signatures, which provides strong control of ownership, but is **incomplete without a way to prevent double-spending.**
* to solve double-spending problem, we proposed a peer-to-peer network using proof-of-work to record a public history of transactions
* the network is robust in its unstructured simplicity.
* they vote with their CPU power, expressing their acceptance of valid blocks by working on extending them and rejecting invalid blocks by refusing to work on them. any needed rules and incentives can be enforced with this consensus mechanism
