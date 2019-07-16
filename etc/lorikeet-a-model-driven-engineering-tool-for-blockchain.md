# Lorikeet: A Model-Driven Engineering Tool for Blockchain-Based Business Process Execution and Asset Management
> TRAN, An Binh; LU, Qinghua; WEBER, Ingo. Lorikeet: A Model-Driven Engineering Tool for Blockchain-Based Business Process Execution and Asset Management. In: BPM (Dissertation/Demos/Industry). 2018. p. 56-60.
> [Link to paper](https://pdfs.semanticscholar.org/5b07/b8de6f5b6badbce971f26672c441e2fbc7c1.pdf)

## Checkpoint
* MDE(Model Driven Engineering)에 대한 이해
* MDE를 통한 Well-tested Smartcontract 생성
* 전체적인 Architecture 구성 방법에 대한 이해

## key sentences
* 

## 1. Introduction
* introduces general blockchain features
* addresses the reason asset management field can be a killer application using blockchain
* addresses difficulties in utilizing blockchain on business
* introduces MDE(Model Driven Engineering) and its pros: generates well tested source code
* introduces Lorikeet

## 2. Tool Description
* composition
    * Web application with GUI
        * User models business process with GUI
    * BPMN(Business Process Model and Notation)
        * generates well tested smart contract from user input BPMN
        * generates informations such as call registry function, instantiate and execute the process model
    * Registry Generator
        * use fields(data structure information, registry type) and methods(basic, adv operations) as input
        * record registery actually
    * blockchain trigger
        * communicates with an Ethereum blockchain node, and handles compliation, deployment and interaction with Solidity smart contracts
* Front side(Web)
    * BPMN 2.0
        * Lorikeet extends BPMN 2.0 with 2 components which consists of new graphical notations and new XML attributes
            * RegisteryReference
                * represents an asset data store on a blockchain
            * ActionInvocation
                * shows the asset registry action to invoke
    * Registry Modellor
        * registry modeller provides **a form** for users to fill in the registry model input
            * 1. basic information
                * registry name
                * description
                * user-defined data fields and their types
            * 2. registry type
                * single or distributed
            * 3. basic operations
                * CRUD
                * exsistence checking for each record
            * 4. advanced operations
                * record lifecycle management
                * foreign key
        * provides option to allow individual registry record lifecycle actions to be managed by a process instance.
* Back side
    * BPMN translator
        * can automatically generate smart contract in Solidity from BPMN models
        * input: takes an exsisting BPMN business process model
        * output: smart contract
    * Registry Generator
        * ?? Creates Solidity smart contract based on the registry models. (calls를 creates로 잘못 쓴 것이 아닐까 하는 의심이 든다.)
        * input: data structure information, registry type, operations
    * Blockchain Trigger
        * communicates with an Ethereum blockchain node, and handles compliation, deployment and interaction with Solidity smart contracts

## 3. Maturity, Demo, and Screencast
* Lorikeet is a well-evaluated tool that is used for creating blockchain smart contracts in industry and academia. received positive feedback from clients
* there is demo which demonstrate Lorikeet, model 'grain title transfer process use case'
