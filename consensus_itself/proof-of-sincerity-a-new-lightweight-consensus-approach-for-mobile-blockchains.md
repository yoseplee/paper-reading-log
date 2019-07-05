# Proof of Sincerity: A New Lightweight Consensus Approach for Mobile Blockchains
> ZAMAN, Miraz Uz; SHEN, Tong; MIN, Manki. Proof of Sincerity: A New Lightweight Consensus Approach for Mobile Blockchains. In: 2019 16th IEEE Annual Consumer Communications & Networking Conference (CCNC). IEEE, 2019. p. 1-4.
> [Link to paper](https://ieeexplore.ieee.org/abstract/document/8651742)

## Overall
* 주장하는 바에 대한 근거와 상세가 매우 부족함. 논문임에도 논리적으로 허술한 요소가 꽤 있으며, 무엇보다 블록 발행과 합의 과정의 적용에 대한 설명으로 미루어 public blockchain의 구조에 대해 잘 이해하지 못한 상태에서 서술한 것 같다는 느낌을 받음

## good sentence for sitation
* 다양한 consens methods가 고안(연구)되고 있는 이유:
    > To meet the requirement of the increasing application of blockchain, different consensus mechanism have been evolved over the last couble of years

## objective
* for a new consensus method for mobile-user-friendly blockchains.
* [problem]: imbalance of wealth and the security of the ledgers: mining is dominated by a small number of huge resource owners, who utilize ASIC.

## pros
* 합의 프로토콜에 대한 전반적인 지식과 문제점에 대한 흐름을 간략하게나마 알 수 있다. PoW, PoS, PoA, PoB, Proof of Space, PBFT에 대한 설명이 간단명료하게 잘 되어있음

## cons
* detail한 내용이 매우 부족하다. 논문의 핵심 기준인 Sincerity에 대한 factor부터 누락되어 있음. 그래서 sincerity는 어떤 기준에 어떤 값인데?
* 블록 생성에 대한 설명이 전혀 없으므로 블록 발생부터 합의까지 설명이 모호할 수 밖에 없음
* 논리상 오해려 51% attack에 vulunerable할 수 있음.
* machine(CPU, GPU, ASIC)에 대해 행해진 실험에 대한 조건 언급이 전혀 없기 때문에 그 결과를 신뢰할 수 없음

## summary
* proof of sincerity can be effectively used to protect the integrity of data in the blockchain by the mobile users' computation efforts
* assumption
    > sincerer user is willing to spend more resource than others for block verification and mining. can be used to represent how sincerely each user is participating in the blockchain system.
* replace difficulty of PoW to sincerity for fairer mining process
* different machines can show meaningfully different levels of sincerity with the same amount of time and we can use this to design our new consensus method
* the reward is distributed to the miner with the smallest sincerity level to ensure the rewarding to every miners
* our proposed scheme does not have the orphaned block problem by allowing multiple miners to remain vaild -> 확인할 수 없음
* more miners can participate and this increased participation will be helpful to prevent monopolistic misbehavior by the larger computing powered users as well as to maintain the high security level of the blockchain ledger
    > [criticism] what if, huge computing power를 구축할 자본으로 컴퓨터의 수를 늘리게 된다면? 그 경우 오히려 51% vulunerbility 문제에 더 취학할 것. 결과적으로 PoW에서의 문제를 해결하지 못하게 되는 것 아닌가 생각함. 1vote for 1cpu라는 원칙에서 네트워크를 유지할 수 있게 하는 computing power를 하향 평준화 시켜버릴 수 있기 때문.
* we can achieve the multiple rounds of verification of a single block
    > [criticism] 본문에서 전혀 언급이 없었던 내용이므로 논리적 구조가 매우 허술함을 알 수 있음. 더불어 이 feature는 오히려 Latency가 더 길어지는 요인이 되지 않을까.
* the proposed idea has promising applications maintained by mobile devices such as an online trading system where both sellers and buyers collaborate to protect the integrity of the transactions.