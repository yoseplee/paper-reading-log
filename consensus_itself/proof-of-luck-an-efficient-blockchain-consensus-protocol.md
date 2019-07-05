# Proof of Luck: an Efficient Blockchain Consensus Protocol
> MILUTINOVIC, Mitar, et al. Proof of luck: an efficient blockchain consensus protocol. In: Proceedings of the 1st Workshop on System Software for Trusted Execution. ACM, 2016. p. 2.
> [Link to paper](http://delivery.acm.org/10.1145/3010000/3007790/a2-milutinovic.pdf?ip=220.149.235.83&id=3007790&acc=CHORUS&key=4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E6D218144511F3437&__acm__=1554180898_e5a9f91705b7f99bf4f6c730726dda35)

## characterisic
* Hardware support: TEE(such as Intel ???)
    * We have proposed three TEE-enabled building block designs for systems using existing proof of work schemes:
        1. TEE-enabled proof of work
        2. TEE-enabled proof of time
        3. TEE-enabled proof of ownership
* Proof of luck consensus protocol uses TEE platform's random number generation to choose a consensus leader
* as with choosing a consensus leader, proof of luck offers low-latency transaction validation, deterministic confirmation time, negligible energy consumption, and equitably distributed mining
* hardware based security protocols

## criticisim
* H/W에 종속
    * TEE 제조 회사에 종속, 특히 Inter SGX에 완전히 종속될 가능성이 있음. 이는 완전한 분산 철학을 가진 블록체인에서는 허용되어선 안 될 것으로 생각함.

## pros
* 

## cons
* 

## Assumption
H/W support(TEE)가 존재하고 이를 신뢰한다: TEE(Trusted Execution Environment) such ans Intel SGX

## problem definition
* basically, there is double spending problem in distribued ledger
* fork problem
* It's not energy efficient
* It's not resistant to ASIC
* synchronized clock problem between participants

## SGX backgroun(kind of TEE)
* typical TEE: isolation and remote attestation feature
* SGX: provide relative timestamps, monotonic counters, and Enhanced privacy Id(EPID) signatures, allowing anonymous and pseudonymous attestation.

## TEE-enabled building block design
TEE가 제공하는 feature로 기존 PoW를 개선하고 Proof of time, proof of ownership을 더하여 block 생성에 있어서 Integrity의 의미를 더하겠다는 뜻
1. TEE-enabled proof of work
    * problem: PoW should be ASIC-resistant as its robustness
    * how: TEE.attestation(H/W supported verification)
        * wraps any existing proof of work algorithm into a TEE-enable one.
2. TEE-enabled proof of time
    * problem: proof of work effectively enforces that a sufficient amount of time has passed by requiring the participant to do work
    * how: a TEE can enforce this directly by requiring the participant to wait for the desired time, saving CPU cycles and energy for other meaningful work
        * SLEEP function of TEE
3. TEE-enabled proof of ownership
    * problem: an attacker acts as multiple participants - such an attacker would have to do many times the amount of work.
    * how: TEE can make it expensive to maintain such virtual participants by physically limiting each participant to owning a unique CPU
        * SGX's EPID

## Proof of luck
* 