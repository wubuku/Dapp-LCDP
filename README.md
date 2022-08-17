# A Dapp Low-Code Development Platform

English | [中文](README_CN.md)

[ToC]

## What we want to do

A **true** Low-code development platform(LCDP) that allows developers to build extremely complex decentralized applications(Dapps) efficiently with experiences that are very close to developing "traditional" applications.

A low-code development platform that helps developers build decentralized applications that maximize the use of blockchains as technical infrastructure.

We know things can't be done overnight. In the initial phase, the platform will prioritize support for building Dapps running on Move public blockchains.

In the longer term, the platform does not restrict developers to use any programming language to build Dapps, allowing them to focus on the implementation of the "business logic". Thus, developers of "traditional" applications can more easily enjoy the dividends of blockchain development; while "traditional" enterprise software and Web 2.0 Internet applications, which are already highly complex, can be migrated onto blockchains at low cost and become decentralized Web 3.0 applications.

### What is a "true" low-code development platform

"What is this 'true' low-code development platform you speak of?"

Here we think it is necessary to clarify the difference between "low-code" and "no-code". No-code refers more to a category of "end-user" oriented tools through which users can quickly assemble certain applications; for example, some Internet form tools, website building tools, etc. The low-code platform, on the other hand, we think is for professional developers.

We believe that a true low-code development platform should have the following key features.

* **Model driven** development. These models should ideally be "domain models" that are as far from "technology" and as close to "business" as possible. Because "communication" is the biggest cost in complex software development - even if the low-code platform is for developers and the "no-code" is for end users(business people).

* **Visual Development**. Visual modeling tools are an important part of the visual development toolbox for low-code platforms. However, it should be noted that if the modeling tool can save the model as a well-readable plain text, then the specification of this text is actually a DSL(domain-specific language), and such a DSL can actually be written manually by the developer(without the help of a visual modeling tool).

* Support the use of **expression languages**. An expression language should be simpler and easier to write business logic in than the general-purpose language(GPL). It should be functional programming style; it should be as declarative as possible - that is, for expressing "what is wanted" rather than "how it is done".

* **Systematic software engineering support**. The low-code platform should integrate best practices in the areas of software engineering including development, debug, testing, version control, DevOps, etc.

* **Applications are open to integration and are extensible**. Applications developed by low-code platforms should have open APIs as well as the ability to use external APIs and be extensible using general-purpose languages.

In our opinion, a "true" low-code platform has yet to be born in the decentralized world. It is all up to us to deliver.

## Value proposition to the Move blockchain ecosystem

We love the revolutionary innovation of "resource-oriented programming" in the Move language. We believe that the combinability of resources can greatly accelerate the pace of innovation in the Move ecosystem, making it more likely that killer applications will emerge that have never been seen on other public blockchains.

But nevertheless, the overall development efficiency of a slightly complex Dapp today, even if the on-chain part(smart contracts) uses the Move language, is hardly satisfactory.

On the other hand, the value of low-code development platforms for developing "traditional" applications has been well proven and widely recognized. Many developers of "traditional" applications have already established deep insights into various domains and have no lack of software development experiences, and they are eager to utilize their talent and intelligence in the decentralized world as soon as possible.

In particular, we would like to highlight the enormous imagination that can be raised by the combination of low-code platforms and DAOs. DAOs, as "legal persons" existing in the blockchain world, are bound to require more "business activities" to be on-chain. The growth of DAOs will amplify the demands for blockchain "business applications". There is an urgent need to reduce the development cost of decentralized versions of "business applications" and improve development efficiency. Traditional low-code platforms are already particularly well suited for rapid development of traditional "enterprise applications", and we believe this will be the case in the Web3 era.

## Current state of low-code development platforms

When we look at traditional low-code development platforms for enterprise applications in the Web 2.0 era according to the above criteria for "true" low-code, there are relative leaders.

![Magic Quadrant for Traditional LCDPs](TraditionalLCDPsMagicQuadrant.png)

So, by the time of Web 3.0, the existing Dapp low-code platforms(if they exist at all), are there any very capable ones?

Unfortunately, by the rigorous "true" low-code criteria described above, we have not yet seen the existence of such a Dapp low-code platform.

"Is it so hard? Why don't they do it?"

### The “model-driven” of enterprise application LCDPs

Traditional enterprise application development platforms(including low-code platforms) are basically "driven" by the E-R(Entity-Relationship) models and/or relational models(the models used in SQL databases).

For example, see how OutSystems does it?

!["Model Driven" Of OutSystems](ModelDrivenOfOutSystems.png)

OutSystems uses both E-R models and relational(data) models; some enterprise application development platforms use only one or the other.

There is a fairly direct correspondence between the concepts used by the E-R models and the relational models, so their modeling results(the generated codes) can easily run on the traditional enterprise software technology infrastructures - SQL databases. But it's hard for them to run on brand new technology infrastructures such as blockchains - where the dominant smart contract platforms and "decentralized ledgers" are constructed too far from traditional SQL databases.

Clearly, the development of a "true" low-code platform requires long-term accumulation of skills and experience, and the technology routes used in traditional enterprise application low-code platforms make them difficult to be ported to the entirely new space of Dapp development.

As for the existing Dapp "low-code" platforms, "They don't have those features, but then what does it matter?"

### The importance of core values

The development of a true low-code - especially adhering to model-driven - is a hard way to go. The problem with existing Dapp “low-code” platforms is that they always try to take shortcuts.

> Never forget the original intention, the only way to get to the end.

A platform's potential is determined by its "core values". The core features expected of a professional low-code platform, such as model-driven, expression language, have values that are difficult to replace with other solutions that try to "bypass" them.

For example, "configurable smart contract templates" certainly have the value of improving the efficiency of developers copying, pasting, and modifying "readymade codes" - if indeed there are "readymade codes". If a developer wants to make some innovative applications and there are no readymade "smart contract templates" available, then it won't be helpful; when multiple chains need to be supported, it is also a big burden for platform developers to write and maintain such a library of "smart contract templates" in different languages(Solidity, Move, etc.) for different chains. Moreover, "smart contracts" are often only the on-chain part of an application, and decentralized applications often require off-chain parts as well.

There is also the "expression language", and although it may be difficult to implement this feature perfectly(the implementation priority can be lower) - for example, it requires developing compilers to compile the codes written in this expression language into instructions that can be executed by the virtual machines(EVM, MoveVM, etc.) of each chain - with it, developers can use only this "expression language" to write business logic, and the developed application can run directly on different chains. There is no need to learn and use each chain's programming language, which greatly saves the cost of application development and porting.

## Technology architecture overview

"Model-driven development" is the core feature of low-code development platforms.

As mentioned earlier, the traditional models used by low-code platforms for enterprise applications are relational and/or ER models; We choose the DDD([Domain-Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)) style domain models, which makes our platform so unique and powerful.

### The key is the modeling paradigm

The DDD domain models are OO(object-oriented) models in a relatively high level of abstraction.

![Mappings Between Models](MappingsBetweenModels.jpeg)

Mapping from the higher abstraction level DDD domain models to the lower abstraction level implementation object models(OO is the dominant paradigm for programming languages), relational models(the dominant paradigm for database models), etc. is relatively easy and can often be done by automated tools.

Mapping low-level models to each other is relatively difficult and often requires developers to step in and even write a lot of implementation codes.
Developers familiar with the ORM(Object-Relational Mapping) frameworks can easily understand this.

### Domain models as the core

The idea is that there should be a domain modeling language that can be used to accurately describe key concepts in the domain; the domain models described by this language can be used as the basis for communication across the application development team(both technical and domain experts) and should be conveniently mapped to the code implementation of the application.

This language should be a DSL that can be adopted by visualization tools as well as easy for humans to read and write.

With the domain models described by this DSL as the core, we make a toolchain to generate the implementation codes for various parts of applications from models and then run the applications on various technical infrastructures.

![Domain Models As the Core](DomainModelsAsTheCore.png)

### Domain-Driven Design Modeling Language(DDDML)

The question is whether we can find such a language as described above?

Fortunately we have found it - DDDML(Domain-Driven Design Modeling Language); more precisely, we invented it.

Eric Evans, founder of Domain-Driven Design, has said that he has always believed that DSL is the next big step in the evolution of domain-driven design.

DDDML takes this big solid step forward. You will see this in what follows.

## Who we are

"Theoretically you are all right, but why can you do it?"

Because, "using DDD-style domain models to drive development" is really the thing we've done in the Web 2.0 era!

![E-R Model/Retiaonl Model Driven Vs. Domain Model Driven](ERDrivenVsDDDModelDriven.png)

Even when implementing a low-code platform for developing traditional enterprise applications, using DDD-style domain models to drive development is a very bold and innovative move. But the path is through, we have had a lot of valuable experience accumulated. We even published a thick monograph to share the lessons learned with developers.

Here it is necessary to highlight the architect of our project: Jiefeng Yang. He has more than 20 years of software development experience, and is a well-deserved DDD expert, the creator of DDDML, and the author of the technical book "[Deep into DDD: Driving Complex Software Development by DSL](https://item.jd.com/12834017.html)". He is also one of the developers of, or has provided key technical support for, several important ecological fundamental projects on Starcoin, the first Move public blockchain(some ecological projects on Starcoin are developed by anonymous teams). 

It is in the book "Deep into DDD" that we detail the design of DDDML, the native DSL for DDD, and its related development toolchain, and how to use them to solve various aches in complex software development processes. This well-received bestseller was published in April 2021 and reprinted in September of the same year.

![The Book "Deep into DDD"](TheBookDeepIntoDDD.png)

That is, we have completed the construction of a complete theoretical system of key technologies that we have successfully put into practice; more than that, we have done a preliminary proof of concept on how to apply these experiences to the development of Dapps - as we will demonstrate in a demo system below.

## Proof of concept: a demo domain name system

###  The purpose of the demo

In the grand scheme of things, we are actually trying to explore a development model that would significantly lower the barrier for traditional application developers to enter the Dapp space. The ideal "very low barrier" would be something like this: developers would only need to build domain models and write(pure) business logic codes. These codes should be able to migrate between different technical infrastructures such as L1 blockchain/L2 blockchain, on-chain/off-chain, centralized database/decentralized ledgers, etc. without requiring developers to manually modify them.

This is obviously a very challenging goal. Because different blockchains have different characteristics, can our low-code platform be designed to effectively meet the challenges posed by the diversity of technical infrastructures? We certainly have great confidence in this, and we will demonstrate this by developing a demo domain system.

We know that Move(Move VM) did not have a data structure like Solidity(EVM)'s `mapping` before; even if Move will support `table`(`mapping`) next, it should not be abused.

The abuse of `mapping` can cause the so-called "blockchain state explosion" problem. It is not a recommended practice to store large amounts of state data in Mapping on the L1 chain; they should be stored off-chain(outside the L1 chain), but at the same time they need to be verifiable and usable on-chain.

So, building a domain name system on a Move chain without using `table`(`mapping`) is a development task of considerable complexity; next we can see the DDD and DSL-based development pattern(a low-code platform) can greatly reduce the burden of developers to complete this task.

### How to prove it

In the first step(already done), we manually write the codes for the implementation of this demo application; which should be decoupled into three parts as follows.

1. libraries that can be reused and are independent of the business logic of the application domain(the domain name system).
2. boilerplate codes that can be generated from the models(described by the DSL).
3. pure business logic codes. It should be noted that the business logic of this demo is written in Move and executed on the Move blockchain(Starcoin L1), but there is potential to evolve a more complex implementation based on this. 

In the second step(to be completed), we will create code generation tools to templatize the codes in part 2 above. We can then remove the part 2 codes described above, regenerate these codes from the models(plus the code templates), and the application should compile and run properly.

It should be noted that although we have not yet completed the second step, any experienced developer can conclude with certainty by reading the source codes we completed in the first step: the real business logic codes(which do need to be written by developers) are very limited, and 90% of the source codes are boilerplate codes that can be generated from the models.

#### Source code of the demo

The source code for the demo is available here [GitHub repository](https://github.com/wubuku/StarcoinNSDemo).


### Features of the demo domain name system

To make the proof of concept in the limited time available, we have dreamed up some simple but "enough to make the point" feature requirements for the domain name system as follows.

* Support domain name registration and renewal. Submitting a domain name registration transaction requires a Non-Membership Proof of domain name state to be input to the contract on the chain; submitting a renewal transaction requires a Membership Proof of domain name state to be input.

* Only second-level domains need to be supported. This is to demonstrate the case where the entity ID is not a "primitive type", but a "complex" value object with two fields.

### Architecture of the demo system

The demo domain system consists of three parts.

![Demo Domain Name System Architecture](DemoDomainNameSysArch.jpeg)

- Client. Before submitting a transaction to the on-chain contracts, the client requests the off-chain service to get the state of the entity(domain name) and its proof of state.
- On-chain contracts. The on-chain contracts do not store the "current state" of all domain names, but only the SMT Root of all domain names. when the on-chain contract executes a transaction, it first verifies the state and the proof of state submitted by the client, and then executes the business logic and updates the SMT Root.
- Off-chain service. The off-chain service constructs the "current state" of all domains in the local database by pulling events from the chain. Anyone can run an instance of the off-chain service and cannot do evil(falsify state information), which ensures the decentralization of the system.

It is to be noted that the implementation codes of the demo actually use the `StateFullTransaction` pattern mentioned in the Starcoin Layer 2/Layered network solution. The DDD concept of "aggregation" is a very powerful thought weapon to determine the boundary of the state involved in a transaction.

### Jobs that need to be done manually

First we need the developers to describe the domain model of the demo system using DSL(DDDML).

The domain model obtained in this step may look like the following.

```yaml
aggregates:
  DomainName:
    id:
      name: DomainNameId
      type: DomainNameId
    properties:
      ExpirationDate:
        type: u64
      Owner:
        type: AccountAddress
    methods:
      Register:
        parameters:
          Account:
            type: signer
            eventPropertyName: Owner
          RegistrationPeriod:
            type: u64
        eventName: Registered
        isCreationCommand: true
      Renew:
        parameters:
          Account:
            type: signer
          RenewPeriod:
            type: u64
        eventName: Renewed
        
valueObjects:
  DomainNameId:
    properties:
      TopLevelDomain: # TLD
        type: string
      SecondLevelDomain: # SLD
        type: string
```

* DomainNameId: A value object representing the domain name ID.

* DomainName: An aggregate that represents a "domain name", with only one aggregate root of the same name(entity DomainName), which has two methods.
  * Register, the method to register a domain name.
  * Renew, the method to renew the domain name.

The developers then need to write the business logic codes of the on-chain contracts.

The directory and file structure of the codes of the on-chain contracts is as follows.

```txt
./move-contracts/src/modules
├── domain-name # Codes of domain (domain name system)
│   ├── DomainName.move # Data models, DomainNameId, DomainNameState, etc.
│   ├── DomainNameAggregate.move # Glue codes for DomainName aggregation
│   ├── DomainNameRegisterLogic.move # Business logic of domain registration
│   ├── DomainNameRenewLogic.move # Business logic of domain renewal
│   └── DomainNameScripts.move # Entry functions
└── smt # Sparse Merkle Tree related codes
    ├── SMTHash.move
    ├── SMTProofUtils.move
    ├── SMTProofs.move # Verify "state proof", update the State Root, etc.
    ├── SMTUtils.move
    └── SMTreeHasher.move
```

A special note here is that only these two files are the "business logic" codes that need to be written manually **if a code generation tool is available**.

* DomainNameRegisterLogic.move
* DomainNameRenewLogic.move
  
The rest of the codes are libraries that can be reused(codes in the smt directory) or codes that can be generated from the models(described by DSL).

We need the developers to write the business logic(Move codes) for "`register` a domain name" manually as follows.

```Move
address 0x18351d311d32201149a4df2a9fc2db8a {
module DomainNameRegisterLogic {
//…

public fun verify(
    account: &signer,
    _domain_name_id: &DomainName::DomainNameId,
    registration_period: u64,
): (
    address, // Owner
    u64, // RegistrationPeriod
) {
    let amount = Account::withdraw<STC::STC>(account, 1000000);
    Account::deposit(DomainName::genesis_account(), amount);
    let e_owner = Signer::address_of(account);
    let e_registration_period = registration_period;
    (e_owner, e_registration_period)
}

public fun mutate(
    domain_name_id: &DomainName::DomainNameId,
    owner: address,
    registration_period: u64,
): DomainName::DomainNameState {
    let domain_name_state = DomainName::new_domain_name_state(
        domain_name_id,
        Timestamp::now_milliseconds() + registration_period,
        owner,
    );
    domain_name_state
}
```

* The `verify` function verifies the transaction parameters submitted by the client and returns the "event" properties if the verification passed. The event is emitted by DomainNameAggregate (using "cheap" in-chain event storage instead of expensive state storage).

* `mutate` should be a pure function that takes an event argument and returns the "modified"(in this case, newly created) domain state.


The business logic of "`renew` a domain name" need to be written by the developer manually is roughly as follows.

```Move
address 0x18351d311d32201149a4df2a9fc2db8a {
module DomainNameRenewLogic {
//…

public fun verify(
    account: &signer,
    _domain_name_state: &DomainName::DomainNameState,
    renew_period: u64,
): (
    address, // Account
    u64, // RenewPeriod
) {
    let amount = Account::withdraw<STC::STC>(account, 1000000);
    Account::deposit(DomainName::genesis_account(), amount);
    let e_account = Signer::address_of(account);
    let e_renew_period = renew_period;
    (e_account, e_renew_period)
}

public fun mutate(
    domain_name_state: &DomainName::DomainNameState,
    _account: address,
    renew_period: u64,
): DomainName::DomainNameState {
    let updated_domain_name_state = DomainName::new_domain_name_state(
        &DomainName::get_domain_name_state_domain_name_id(domain_name_state),
        DomainName::get_domain_name_state_expiration_date(domain_name_state) + renew_period,
        DomainName::get_domain_name_state_owner(domain_name_state),
    );
    updated_domain_name_state
}
```

* There is a slight difference between these two functions compared to the two functions for domain name registration. Since the domain name is renewed for an "existing" domain, there are arguments for the "old status" in the list of input parameters.

* The `mutate` method receives the old state and event data then returns the new state.

---

The above is **ALL** the codes that need to be written manually: one model file, two business logic files.

### Jobs that should be done automatically by tools

#### Codes of off-chain service

The demo off-chain service was written in Go. The directory and file structure of the project is as follows.

```txt
./off-chain-service
├── README.md
├── client # Go Client SDK for Domain Name System
│   ├── client.go
│   └── client_test.go # Unit tests
├── contract # Query interfaces of on-chain contracts
│   ├── contract.go
│   └── contract_test.go # Unit tests for the contract package
├── db
│   ├── bcs.go # BCS serialization/deserialization codes of data models
│   ├── db.go # Database constants and interface
│   ├── db_test.go # Unit tests for the db package
│   ├── models.go # Data models, DomainNameId, DomainNameEvent, etc.
│   ├── mysqldb.go # MySQL Implementation of Data Access Layer
│   └── smt_test.go # Unit tests on SMT codes
├── events
│   ├── events_test.go # Event unit tests
│   ├── lib.go # Event structs and their BCS serialization/deserialization codes
│   └── libext.go # Some extensions to the event codes generated by tool
├── go.mod
├── go.sum
├── handlers.go # Handlers implementing RESTful API, dependent on starcoinmanager.go
├── main.go # Program entry of off-chain service
├── manager
│   ├── starcoinmanager.go # Pulling on-chain events, updating off-chain states, monitoring and handling chain re-organization, etc.
│   └── starcoinmanager_test.go # Unit tests
├── serde-format
│   └── events.yaml # YAML doc. describing the format of the events in the chain, used by the SerdeGen tool to generate code
├── tools # Some tool code 
│   ├── restclient.go # RESTful client codes
│   ├── starcoinutil.go # Some wrappers and extensions to the Starcoin Go SDK
│   └── util.go # Other tools codes
├── transactions # Codes submitting transactions(that change the on-chain state)
│   ├── lib.go # Encoding methods for on-chain transactions
│   ├── transactions_test.go # Unit tests
│   └── util.go # Some tools for on-chain transactions
└── vo
    └── vo.go # Types(View Objects) of parameters and returns of RESTful API
```

* The implementation of the scheduled tasks and RESTful API can be traced from here: starcoinmanager.go

* A closer look at the code reveals that all the codes(of the entire off-chain service) can actually be generated by automation tools from the models(described by DSL).

#### Client SDKs, front-end applications and more

There is no doubt that we can create automation tools to generate Client SDKs for various languages from the DDD domain models, including Client SDK for Java, Client SDK for JavaScript, Client SDK for Go, Client SDK for any programming language you can name.

Tools can even generate front-end applications with user interfaces directly from the domain models, including Web front-end applications(we really did this in the Web 2.0 era), mobile apps, command-line client applications, and more. Maybe you think this is too promising, well, at least you can believe that there is no problem scaffolding codes for front-end applications.

#### Number of lines of codes in the demo

We have done a rough count of the lines of codes for this demo system as follows.

```txt
github.com/AlDanial/cloc v 1.92  T=0.08 s (604.0 files/s, 97263.5 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
Go                              24            459            390           4374
Move                            12            255            225           1323
JSON                             3              0              0            509
Markdown                         2             58              0            211
XML                              5              0              0            118
YAML                             2              5              0             66
TOML                             2             24              0             34
-------------------------------------------------------------------------------
SUM:                            50            801            615           6635
-------------------------------------------------------------------------------
```

### Conclusion from the Demo

With this demo, we can draw the following rough conclusions.

* The demo reveals that the low-code development pattern we advocate can efficiently develop Dapps running on different blockchains. Although we used the Move language(based on the Starcoin chain) for this proof-of-concept, it shows that it is also possible to use Solidity(based on Ethereum or other EVM-compatible chains), since Solidity also supports `struct` and Ethereum also provides event/log mechanisms. That is, the features of the Move language and the Starcoin chain that this proof-of-concept demo utilizes are also available on Ethereum.

* "Low-code" is a good way to shield the complexity of technology infrastructure utilization. The demo system stores states off-chain(outside the L1 chain) in order to solve the state explosion problem, which is a fairly complex architecture, but the application developer only needs to write business logic, and does not need to perceive the complexity of it at all.

* The improvement in Dapp development efficiency with the "low-code" approach is amazing. Using "low-code" development in the right place, development efficiency can be increased by more than ten times. Take the Demo system for example, the entire project has thousands of lines of code, but only two or three hundred lines of code need to be written manually by developers(after having the help of low-code platform in the near future).

It is important to note that the demo actually does not fully show the power of low-code development. We can use the expression capability of DSL(DDDML) to build quite complex domain models: value objects(non-fundamental types) embedded in value objects; aggregations containing multiple(multi-level) entities, etc. In the development of real "traditional" applications, we have used DSL to build much more complex aggregate models than the demo.

## Deliverables

This is certainly an ambitious project, but it doesn't make too much sense to discuss longer-term plans; we started by setting two small milestones for the project.

### Milestone I

We will create a command line tool or a set of tools. At a minimum, the tool will help developers generate on-chain Move contracts (the on-chain part of a Dapp), off-chain services (written in Java or Go), and even more from domain models, such as Client JavaScript SDKs, scaffolding codes of web front-end applications with user interfaces, etc.

It is expected that this milestone can be reached by two persons working for three months after the project starts.

### Milestone II

We will move the functionality of the command line tools created in Milestone I to the cloud, where developers can simply open their browsers and use them. We expect to provide a simple Web IDE for developers to write domain models, generate Dapp applications "with one click", write business logic codes, and deploy the applications to a test environment in the cloud.

It is expected that after reaching the first milestone, two persons working for three months can reach this second milestone.


