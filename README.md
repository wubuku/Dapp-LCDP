# A Dapp Low-Code Development Platform

English | [中文](README_CN.md)


[ToC]

## What we want to do

A **true** Low-code development platform (LCDP) that helps developers build decentralized applications ( Dapps ) that maximize the use of blockchains as technical infrastructure.

A low-code development platform that allows developers to build extremely complex decentralized applications with experiences that are very close to developing "traditional" applications.

In the initial phase, the platform will prioritize support for building Dapps running on the Move public blockchain.

In the longer term, the platform does not restrict developers to use any programming language to build Dapps, allowing them to focus on the implementation of the "business logic". Thus, developers of "traditional" applications can more easily enjoy the dividends of blockchain development; while "traditional" enterprise software and Web 2.0 Internet applications, which are already highly complex, can be migrated onto blockchains at low cost and become decentralized Web 3.0 applications.

## What is a "true" low-code development platform

"What is this 'true' low-code development platform you speak of?"

Here we think it is necessary to clarify the difference between "low-code" and "no-code". No-code refers more to a category of "end-user" oriented tools through which users can quickly assemble certain applications; for example, some Internet form tools, website building tools, etc. The low-code platform, on the other hand, we think is for professional developers.

We believe that a true low-code development platform should have the following key features.

* **Model driven** development. These models should ideally be "domain models" that are as far from "technology" and as close to "business" as possible. Because "communication" is the biggest cost in complex software development - even if the low-code platform is for developers and the "no-code" is for end users (business people).

* **Visual Development**. Visual modeling tools are an important part of the visual development toolbox for low-code platforms. However, it should be noted that if the modeling tool can save the model as a well-readable plain text, then the specification of this text is actually a DSL (domain-specific language), and such a DSL can actually be written manually by the developer (without the help of a visual modeling tool).

* Support the use of **expression languages**. An expression language should be simpler and easier to write business logic in than the general-purpose language (GPL). It should be functional programming style; it should be as declarative as possible - that is, for expressing "what is wanted" rather than "how it is done".

* **Systematic software engineering support**. The low-code platform should integrate best practices in the areas of software engineering including development, debug, testing, version control, DevOps, etc.

* **Applications are open to integration and are extensible**. Applications developed by low-code platforms should have open APIs as well as the ability to use external APIs and be extensible using general-purpose languages.

## Who we are

TBD...

## Technology architecture overview

TBD...

## Proof of concept: a demo domain name system

###  The purpose of the demo

In the grand scheme of things, we are actually trying to explore a development model that would significantly lower the barrier for traditional application developers to enter the Dapp space. The ideal "very low barrier" would be something like this: developers would only need to build domain models and write (pure) business logic codes. These codes should be able to migrate between different technical infrastructures such as L1 blockchain/L2 blockchain, on-chain/off-chain, centralized database/decentralized ledgers, etc. without requiring developers to manually modify them.

This is obviously a very challenging goal. Because different blockchains have different characteristics, can our low-code platform be designed to effectively meet the challenges posed by the diversity of technical infrastructures? We certainly have great confidence in this, and we will demonstrate this by developing a demo domain system.

We know that Move (Move VM) did not have a data structure like Solidity(EVM)'s `Mapping` before; even if Move will support `Table`(`Mapping`) next, it should not be abused.

The abuse of Mapping can cause the so-called blockchain state explosion problem. It is not a recommended practice to store large amounts of state data in Mapping on the L1 chain; they should be stored off-chain(outside the L1 chain), but at the same time they need to be verifiable and usable on-chain.

So, building a domain name system on a Move chain without using `Table`(`Mapping`) is a development task of considerable complexity; next we can see the DDD and DSL-based development pattern(a low-code platform) can greatly reduce the burden of developers to complete this task.

### How to prove it

In the first step(already done), we manually write the codes for the implementation of this demo application; which should be decoupled into three parts as follows.

1. libraries that can be reused and are independent of the business logic of the application domain(the domain name system).
2. boilerplate codes that can be generated from the models(described by the DSL).
3. pure business logic codes. It should be noted that the business logic of this demo is written in Move and executed on the Move blockchain(Starcoin L1), but there is potential to evolve a more complex implementation based on this. 

In the second step(to be completed), we will create code generation tools to templatize the codes in part 2 above. We can then remove the part 2 codes described above, regenerate these codes from the models(plus the code templates), and the application should compile and run properly.

It should be noted that although we have not yet completed the second step, any experienced developer can conclude with certainty by reading the source codes we completed in the first step: the real business logic codes (which do need to be written by developers) are very limited, and 90% of the source codes are boilerplate codes that can be generated from the models.

#### Source code of the demo

The source code for the demo is available here [GitHub repository](https://github.com/wubuku/StarcoinNSDemo).


### Features of the demo domain name system

To make the proof of concept in the limited time available, we have dreamed up some simple but "enough to make the point" feature requirements for the domain name system as follows.

* Support domain name registration and renewal. Submitting a domain name registration transaction requires a Non-Membership Proof of domain name state to be input to the contract on the chain; submitting a renewal transaction requires a Membership Proof of domain name state to be input.

* Only second-level domains need to be supported. This is to demonstrate the case where the entity ID is not a "primitive type", but a "complex" value object with two fields.

### Architecture of the demo system

The demo domain system consists of three parts.

![Demo Domain Name System Architecture](DemoDomainNameSysArch.jpeg)

- Client. Before submitting a transaction to the on-chain contracts, the client requests the off-chain service to get the state of the entity (domain name) and its proof of state.
- On-chain contracts. The on-chain contracts do not store the "current state" of all domain names, but only the SMT Root of all domain names. when the on-chain contract executes a transaction, it first verifies the state and the proof of state submitted by the client, and then executes the business logic and updates the SMT Root.
- Off-chain service. The off-chain service constructs the "current state" of all domains in the local database by pulling events from the chain. Anyone can run an instance of the off-chain service and cannot do evil (falsify state information), which ensures the decentralization of the system.


## Key risks

TBD...

