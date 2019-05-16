# Demystifying Hyperledger Fabric ordering and decentralization
> Is the Fabric ordering service centralized or not? Can organizations within a Fabric network run ordering nodes?
by Arnaud Le Hors | Published April 23, 2019 | IBM Developers
> [Link to article](https://developer.ibm.com/articles/blockchain-hyperledger-fabric-ordering-decentralization/?fbclid=IwAR1jg1q2eV1oyLdwqBwk5oOw7UhadVVeYjXqB2rLu_5r7J9pciuwpc0Ko6M)

## my opinion
* CFT can be regarded as a subset of BFT. As BFT can do what CFT have, but cannot vice versa.
* Kafka, RAFT is all not BFT family, but CFT.(actually Raft is strongly based on VR(Viewstamped Replication))
* may the Hyperledger project not implement BFT family network as its complexity and burden on network. Or its unnecessarity. Its powerful, and fully logical security cluster don't have strong need for BFT network. If its peer is never be a malicious, why such costy BFT network is needed?

## key sentences
* explaining Fabric’s design, the different types of ordering services available today and in the future, and the different degrees of decentralization that they provide.
* One of the most unique characteristics of Hyperledger Fabric’s architecture is its consensus mechanism, which consists of three steps — execute > order > validate — as opposed to the more traditional order > execute mechanism typically found in other blockchain frameworks.
* As of version 1.4.0, Fabric’s ordering service came in two different flavors: Solo, for development purposes, and Kafka, for production.

## Ordering mechanisms
* Solo
    * Solo is designed to provide the ordering service in its simplest possible form so that you can focus on other matters, such as the development of your chaincode and application, without having to worry about the ordering service.
* Kafka
    * The Kafka ordering service leverages a cluster of Kafka brokers and a Zookeeper ensemble to provide for a crash fault tolerant (CFT) ordering service. It is possible for your ordering service to consist of several ordering nodes that are under the control of different organizations on your network.
    * having ordering nodes run by different organizations doesn’t give you much in terms of decentralization because they will all go to the same Kafka cluster, which is under the control of a single organization.
* Raft
    * with the removal of the dependency on Kafka and Zookeeper, having ordering nodes run by different organizations now makes sense.
    * Raft is expected to become the default ordering service in all production deployments moving forward. It is actually simpler to manage because it is just a library that is used by the ordering node, so there are fewer moving parts and it provides for decentralization.

## don't have to adopt BFT network(Trade-off)
* It is also worth noting that not all use cases require a BFT network. For example, when deploying a blockchain network within a single enterprise or within a small set of business partners, a fully BFT network might not be worth the associated performance cost.
