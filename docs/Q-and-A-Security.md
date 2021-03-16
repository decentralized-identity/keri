# Q&A about KERI's Security model and Guarantees


| --- |KERI logo| --- --- --- --- --- --- --- --- --- --- |
| -------- | -------- | --------------------------------- |
|     |![](../images/Keri_logo_color_on_white.png)|     |


This document is part two of [Q-and-A](./Q-and-A.md). Both files shares a common [Glossary](./Glossary.md)

**The questions are of a varied level: basic and detailed. The answers are mostly directed towards generally interested people and newbies.**\
*Q = one star question. Novice to KERI, advanced in DIDs\
**Q = two star question. Proficient in DIDs and advanced in KERI\
***Q = three star question. Expert in DIDs and proficient in KERI

Why should you read or step through the Q&A? To get a different angle to the same topic: KERI.

```
{TBW} means: to be written
{TBW prio 1} means to be written with the highest priority, 
3 = no urgency, 2 = intermediate
```
- [Q&A about KERI](#qa-about-keri)
    + [Disclaimer](#disclaimer)
    + [List of questions and definitions](#list-of-questions-and-definitions)
  * [Knowledge you should be confidently applying](#knowledge-you-should-be-confidently-applying)
  * [Actions you should be comfortable with](#actions-you-should-be-comfortable-with)
- [Jump table to categories](#jump-table-to-categories)

Inspired by presentation given and questions asked on the [SSI webinar May 2020](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/), but also issues raised and the progress made, here on Github (Turn on 'Watch' if you want to be notified of conversations).

Beware: A Q&A is always *work in progress*. Tips & help welcome.

### Disclaimer
None of the respondents in the **open** repo and presentations have been explicitly named as a source, except for ***Samuel M. Smith Ph.D.*** and ***@henkvancann***. If there is no reference added to the answers, then it's Samuel M. Smith who answered the question. Most of the editing is done by @henkvancann, which might have introduced ommission, errors, language glitches and such. Sorry for that, feel free to correct by submitting a pull request (PR).\
For practical reasons educational images uploaded by Github members have been downloaded. We de-personalised them by giving images a new name. Under these new names these images have been uploaded to github and used in the Q&A to clarify the questions and answers.

Keri's content is licensed under the [CC by SA 4.0. license](https://creativecommons.org/licenses/by-sa/4.0/). Parts of the video offered on SSI Meetup webinar 58 have been captured and uploaded to Github to support the answers to general questions about digital identity and more in depth answers to question about Keri.

We've done our best to protect the privacy of the Github by investigating the images we used. We haven't come across personal identifiable information (pii). However, should we have made a mistake after all, please let us know and we'll correct this immediately.

### List of questions and definitions

- [Definitions:](#definitions)
      - [Ambient verifiability](./Glossary.md#ambient-verifiability)
      - [Agent](./Glossary.md#agent)
      - [Agency](./Glossary.md#agency)
      - [Autonomic Identifier](./Glossary.md#autonomic-identifier)
      - [Autonomic Namespace](./Glossary.md#autonomic-namespace)
      - [Autonomic idenity system](./Glossary.md#autonomic-idenity-system)
      - [Content-addressable hash](./Glossary.md#content-addressable-hash)
      - [Controller](./Glossary.md#controller)
      - [Correlation](./Glossary.md#correlation)
      - [Cryptocurrency](./Glossary.md#cryptocurrency)
      - [Decentralized Identity](./Glossary.md#decentralized-identity)
      - [Derivation code](./Glossary.md#derivation-code)
      - [Duplicity](./Glossary.md#duplicity)
      - [Entropy](./Glossary.md#entropy)
      - [Establishment Event](./Glossary.md#establishment-event)
      - [End verifiable log](./Glossary.md#end-verifiable-log)
      - [Entity](./Glossary.md#entity)
      - [External consistency](./Glossary.md#external-consistency)
      - [Inception Event](./Glossary.md#inception-event)
      - [Inconsistency](./Glossary.md#inconsistency)
      - [Identity](./Glossary.md#identity)
      - [Internal inconsistency](./Glossary.md#internal-inconsistency)
      - [KERI Agreement Algorithm for Control Establishment](./Glossary.md#keri-agreement-algorithm-for-control-establishment)
      - [Key](./Glossary.md#key)
      - [Key Event Log](./Glossary.md#key-event-log)
      - [Key Event Receipt Log](./Glossary.md#key-event-receipt-log)
      - [Non-Establishment Event](./Glossary.md#non-establishment-event)
      - [Payload](./Glossary.md#payload)
      - [Public Key Infrastructure](./Glossary.md#public-key-infrastructure)
      - [Root of trust](./Glossary.md#root-of-trust)
      - [Seal](./Glossary.md#seal)
      - [Secret](./Glossary.md#secret)
      - [Self Addressing Identifier](./Glossary.md#self-addressing-identifier)
      - [Self Certifying Identifier](./Glossary.md#self-certifying-identifier)
      - [Self Sovereign Identity](./Glossary.md#self-sovereign-identity)
      - [Spanning layer](./Glossary.md#spanning-layer)
      - [Transfer](./Glossary.md#transfer)
      - [Trust-over-IP](./Glossary.md#trust-over-ip)
      - [Validator](./Glossary.md#validator)
      - [Verifiable Credential](./Glossary.md#verifiable-credential)
      - [W3C DID](./Glossary.md#w3c-did)
      - [(Digital Identity) Wallet](./Glossary.md#-digital-identity--wallet)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

## Knowledge you should be confidently applying
- The definitions in the [glossary](./Glossary.md)
- The Knowledge you should be confidently applying from part one of the [Q-and-A](./Q-and-A.md#knowledge-you-should-be-confidently-applying)
- Bitcoin Improvement Protocols: BIP32, BIP39, BIP44, BIP47, BIP49, BIP84, BIP174
- hierarchical deterministic derivation paths
- Base58
- Eliptic curves
- W3C DIDs thoroughly
## Actions you should be comfortable with
- The Actions you should be comfortable with from part one of the [Q-and-A](./Q-and-A.md#actions-you-should-be-comfortable-with)
- Amend knowledge and keep existing knowledge up to date

# Jump table to categories
## PART TWO SECURITY
- [KERI operational security](#qa-section-keri-operational-security)
- [Identifiers](#qa-section-identifiers)
- [Event logs](#qa-section-event-logs)
- [Inconsistency and duplicity](#qa-inconsistency-and-duplicity)
- [Key rotation](#qa-key-rotation)
- [KEL and KELR](#qa-section-kel-and-kerl)
- [Witness](#qa-section-Witness)
- [Watchers](#qa-section-watcher)
- [KERI and blockchain settled DIDs](#qa-keri-and-blockchain-settled-dids)
- [Security Guarantees](#qa-security-guarantees)
## PART ONE
- [General](./Q-and-A.md#qa-section-general)
- [Why the internet is broken](./Q-and-A.md#qa-section-why-the-internet-is-broken)
- [KERI and DIDs](./Q-and-A.md#qa-keri-and-dids)
- [Wallets](./Q-and-A.md#qa-section-wallets)
- [Signatures](./Q-and-A.md#qa-section-signatures)
- [Proofs](./Q-and-A.md#qa-section-proofs)
- [Private Key Management](./Q-and-A.md#qa-section-private-key-management)
- [Blockchain](./Q-and-A.md#qa-key-blockchain)
- [KERI operational](./Q-and-A.md#qa-section-keri-operational)
- [Root of trust](./Q-and-A.md#qa-section-root-of-trust)
- [Agencies](./Q-and-A.md#qa-key-agencies)
- [Virtual Credentials](./Q-and-A.md#virtual-credentials)


# Q&A section KERI operational security

## **Q: How can it be one solution, fit for all SSI problems? 
KERI uses plain old digital signatures from `PKI`, intentionally, so that it may be truly universally applied. KERI solves that hard problem of PKI, that is, key rotation in a standard way. Without a standard way of addressing key rotation, there is no interoperability between systems, they break when you rotate keys because no one knows how to verify the key rotation was done properly. `KERI` solves that problem.\
(_SamMSmith_)

## *Q: Where would you need something quite different than KERI?
`KERI` does one thing, it establishes control authority using verifiable portable proofs that are `KEL`s.\

#### Liveliness
If you need liveliness of fungible trust, like cryptocurrencies, you can't use KERI for this.\ 
In KERI we have compact security for the sake of liveliness, whick means there is no public ledger with total ordering of state. In KERI after duplicity is detected, you don't trust that identifier anymore. That means in KERI you don't have fungible trust. And that is a good thing for trust.

{TBW prio 2}
(_SamMSmith_)

## ***Q: KERI is inventing its own key representation and signature format. Why did you do that?
**(@OR13) argues the following:**\
_In order to share code / we would need shared building blocks. `Sidetree` is built on JWS / JWK. KERI is inventing its own key representation and signature format. These are the lowest level building blocks, so them being different will prevent a lot of potential code reuse._

In brief these are the reasons:
- the **desire to control the entire stack**, and not use anyone else's tooling
- DID and VC layers are the **appopriate layers for interopability**
- The **performance/security goals** of KERI drive its design which makes incompatible with Linked Data tooling

## ***Q: Why did KERI WG decide to reinvent multicodec?
**(@OR13) argues the following:**\
_There was a potential for KERI to align with Ceramic / IPFS / IPLD, but that door closed when the KERI WG decided to reinvent multicodec._

#### The **desire to control the entire stack**, and not use anyone else's tooling
Have a look at the [Kid0001Comment](https://github.com/henkvancann/keri/blob/master/kids/kid0001Comment.md#summary) Summary for why we needed to divert from `multicodec`. Multicodec may not be such a stable standard to be breaking or abandoning.

`Multicodec` is a draft standard, a rather chaotic mix of binary and text-based entries in a crowd-sourced registry/table. Most implementers are doing a subset of the Multicodec chart anyways, making it even more unstable for interoperability purposes.

To go in further detail why multicodec can't do for KERI: the length of item not included in encoding table - incompatible structure (Multicodec assumes enveloped data structure) Moreover we need KERI's composability (via concatenation) for framing events.
#### DID and VC layers are the appopriate layers for interoperability
- streaming support > interop at signature layer?
#### The performance/security goals of KERI drive its design which makes incompatible with Linked Data tooling
KERI can't use enveloped data formats:
 - enveloped data format -> signatures have to put on/outside the payload
 - MsgPack and CBOR-> work with block-delimited structures
 - JWS/JWK - also enveloped, also incompatable with streaming
 - framing events = better streaming support
 (@by_caballero and _@henkvancann_)

## *Q: Will KERI be interoperable with DID:peer and Sidetree?
You can implement did;peer and Sidetree with KERI but we can’t implement KERI with Sidetree or did:peer.\
Because KERI operates on a lower level.\
If we were to do that, we have to tunnel KERI identifiers to create corresponding Ledger-entries.\
(_SamMSmith_)

## ***Q: Will KERI be interoperable with DID:peer and Sidetree?
**(@OR13) argues the following:**\
Afaik this ship sailed when KERI decided to define its own event format. I don't think KERI shares any commonality with sidetree or did peer, and it's no longer possible to align them, so while you can start with the same key material, doing similar operations will very quickly result in totally different event structures.

I don't see a way for KERI events to be used by anything but KERI for now, certainly not Sidetree. In the future did:peer might use KERI events directly, but then did:peer would not be Sidetree compatible

...

The upside is that KERI could be much better than things built on JOSE. The down side is KERI won't be possible to implement with off the shelf JOSE crypto. Having spent a lot of time with linked data, It looks like KERI is setup to feel all the same kind of pain, regarding reinventing the wheel instead of starting with compatibility with JOSE.

...

I predict a few years from now we will have:

A. JOSE / JWS / JWK / jose based DIDs\
B. `Multicodec` / IPFS / IPLD / DAG_CBOR / JWS / JWK / ipld based DIDs\
C. Linked Data / JSON-LD / CBOR-LD / linked data based DIDs\
D. KERI / KERI keys / KERI signatures / keri event log based DIDs

There will be some overlap, for example KERI based DID Documents will likely support JWKs if they want to be useful with any legacy system, but internally KERI will use a different key representation. Similarly sidetree based dids will likely support linked data proofs but will only rely on JWS / JWK for internal operations.

As far as I know, the KERI design has specifically chosen not to build on JOSE, IPLD. or JSON-LD / CBOR-LD. So there won't be any opportunity for interop with KERI below the DID Document layer. Which is true of many other systems, including Ethereum, Bitcoin, Hyperledger based DIDs. Many of which don't share event log interopability.

Imo, if KERI used IPLD / JSON-LD / CBOR-LD, it would be better. Because not using them means reinventing the parts of them that are needed... which comes with the potential for better performance at the cost of inventing a faster wheel, and failing to pull developers / tooling from those established communities. However I can understand the desire to control the entire stack, and not use anyone else's tooling.

From an engineering management and interopability perspective, I would have decided to break compatibility after the whole system was built and working, and only in the areas where JWS / JWK or IPLD performance, documentation or library support was so bad it was justified.

...  We should target interop between KERI and Sidetree at the DID Core and VC Data Model layer.\
**End of (@OR13)'s plea.**

The DID and VC layers are the appopriate layers for interopability. The performance/security goals of KERI drive its design which makes incompatible with Linked Data tooling.\
(_SamMSmith_)

## **Q: How does KERI keep identifiers secure?
By the mechanism of availability, consistency, and duplicity.\
We have to handle `race conditions` too, just like any other distributed database or blockchain.\
(_SamMSmith_)

## *Q: How does KERI scale safely without comprising the security model
{TBW Prio 2}

## **Q: Is the KERL technically a blockchain/hashed data log, rather than a ledger that implies a balance?
Yes a KEL/KERL is a hash chained data structure. But not merely hash chained but also signed, so it's also a cryptographic proof of key state.\
It's not tracking balance, it's tracking key state.
(_SamMSmith_)

## **Q: According to the SSI Book KERI will never be able to substitute the internet conventional PKI infra. Right?
[SSI Book](https://livebook.manning.com/book/self-sovereign-identity/chapter-8/v-9/144): "As powerful as this (read KERI-like) solution appears, completely self-certifying identifiers have _one major Achilles heel_: the controller’s identifier needs to change every time the public key is rotated. As we will explain further in _Chapter 10_ on decentralized key management, key rotation—switching from one public/private key pair to a different one—is a fundamental security best practice in all types of PKI. Thus the inability for self-certifying identifiers alone to support key rotation has effectively prevented their adoption as an alternative to conventional PKI.\
{TBW prio 1}

## **Q: How are KERI witnesses and watchers incentived to spread KELs and KERLs and make them available?
{TBW prio 2}
## **Q: Could a KEL or KERL be pruned or charded?
Compared to blockchains KEL and KERL are lean and mean data structures. So pruning or charding might not be necessary. For the sake of security KEL and KERL can't be charded, because they are ambient available. However you could soft-prune a KEL because if you've verified to the root-of-trust once, you don't need to do that again up until the current key event in the KEL {The same holds for KERLs?}\
{TBW prio 2}\
_(@henkvancann)_

## **Q: Why does KERI demand signing and digesting the full over-the-wire serialization of a message?
The discussion of `KERI`s approach to *serializing messages and signing and digesting the full over-the-wire serialization* is inconvenient for implementers. The motivation for this approach I am calling Zero Message Malleability as a property of `KERI`. 
This is a "best practices" security first approach that prevents semantic leakage over time that becomes a transaction malleability vulnerability. Indeed `KERI` approach trades off some inconvenience in serialization for better security and reduces the inconvenience of needed to have tightly specified semantics to prevent transaction malleability.\
(_SamMSmith_)

## **Q: If the KERI resolver "relies on a distributed hash table (DHT) algorithm .. such as IPFS or GNUnet", isn't that a huge contradiction in terms?! 
_If KERI has this built-in reliance, then doesn't that contradict and defeat the whole purpose of KERI?_

KERI resolver - due to the KERI architecture we get rid of the "magic box" in a way that I don't have to trust any infrastructure component. `DHT` is just example how this can be done in decentralized fashion.\
But the point is that **I don't have to trust any node or network** that the statement is correct. I can cryptographically verify that everytime with KERI. Compare to current DID infrastructure where I have to trust resolution process in each DID-method because as soon as would get DID Document, I can't verify that this is the correct one. Think of it like `DID:peer` where I can always be 100% sure that the `DDO` which I have belongs to that DID. Not every DID method has this kind of properties. And I think this characteristic is crucial for adoption of DIDs.
(_RobertMitwicki_)

## **Q: Delegations in many systems are unilateral. KERI has cooperative delegation. What is that and why is it better?
In many system unilateral delegation is a single point of failure. if a delegated key's delegator gets compromised, you have no way to recover.\
Keys are in different infrastructures in KERI. Both the delegator and the delegatee have keys they manage. If one of them get compromised or lost, we still can recover. Each level of delegation allows delegation of the level above.
_(@henkvancann)_

# Q&A section Identifiers

## How is a KERI identifier different than a regular identifier in DID methods?
A self-sovereign identifier that is not self-certifying is dependent of infrastructure and is not fully autonomous and not fully porteable. KERI uses autonomic identifiers, fully cryptographically derivable and portable.
_(@henkvancann)_

## Is my KERI identifier public?
In the direct mode (peer to peer) KERI can be used to keep identifiers private to the peers or group involved. In the indirect mode all identifiers are public. The privacy of the individual, group or object described by the identifier is weak because anyone can bind and indentifier to a subject anytime and anywhere. Fortunately, this binding is weak too, As soon as controllers and verfiers sign statements / events related to an identifier, that's when the binding gets strong and subjects publicly exposed.\
_(@henkvancann)_

## Is a KERI identifier GDPR proof?
KERI enables support for protection against liability that could stem from gdpr’s right to be forgotten (passive approach) and the right of erasure (active approach). There are two exceptions to the general rule that you have to remove an identifier from your database, if a subject and / or controller requests so:
1. As long as you're a party in a transaction involving the identifier that has been revoked, then you can keep that identifier in your log.
2. For archival integrity - given that KERI’s whole reason for existence is keep track of duplicity in identity events it is important to know that an identifier has been erased before, because we don't lose that notion. Because somebody could come up with the same identitifier in the future and we wouldn't know that it existed before.

Within the assumption of both exceptions KERI complies with the GDPR rules: 
1. block-list of “deleted” KELs: a reciept of a request for erasure must naturally hold some PII, a two-party interaction might allow this to be recorded.
2. a need to maintain system integrity/archival purposes can be a reason for maintaining some info right of erasure versus right to be forgotten. This active and passive approach reflects two slightly different interpretations of the same article (which one people use is a hint of their school of thought).

Beware that most of GDPR rules are there to protect you from being exploited. So you're not being prossecuted or being labelled as a criminal activity. It might only be illegal and somebody could hold you liable for that.
_(@henkvancann)_

## What do I need a self-certifying identifier for?
It is a cryptographically derived, strong binding between a controller, a keypair and an identifier. No weak bindings introduced by administration present.
_(@henkvancann)_

## How does self addressing work for the identifier?
Using a content digest not only binds the inception statement to the identifier but also makes it easy to use the identifier prefix to retrieve the inception statement from a content addressable database. 

```
Mechanism:
**inception statement -> hashing -> #**

# points to a record in a database:
**# -> inception statement -> hashing -> # (proof of "address")**
```

This requires that the database store the signature with the inception data, so that a reader may cryptographically verify that the inception data is authoritative. Without the signa- ture the digest is repudiable by the controller. This approach also enables content or document specific but self-certifying identifiers. 
```
inception statement -> sig + derivation + public key + extra data
Check sig with public key -> 
non-repudiable unique attribution to the content by whoever controls the private key
```

## What do I need a self-addressing identifier for?
In brief: 
1. commitment: nonrepudiable unique attribution to the content creator as controller
2. confidentiality: a decryption key must be obtained from the controller

Self-addressing identifiers provide a mechanism for a content addressable database to enforce nonrepudiable unique attribution to the content creator as controller. This binds the content to the creator in the content address. Different creator means different address. This makes confidential (encrypted) content more usable as the content address is bound to the controller from whom a decryption key must be obtained.

## ***Q How can I prevent a direct mode interaction being published and breach a controller's privacy?
The assumption is that direct mode is meant to be private communication.
1. There is understanding when you use direct mode that it needs to stay private
2. There is a possibility to impose a liability, under consent at the time of issuance
3. There is no way to enforce the KEL from being kept private

## **Q: What is tombstoning and could it help to preserve privacy of identifiers in KERI?
Tombstoning in Self Sov Identity and DIDs has a very different meaning than in everyday's language (where it means _'the act of jumping in a straight, upright vertical posture into the sea or other body of water from a high jumping platform, such as a cliff, bridge or harbour edge.'_) 

It stems from the development of ledger-based identities like Sovrin. Tombstoning means "Burry the transactions" Because Sovrin is a permissioned ledger, the steward lets you read it - or won't let you read the transactions, depending of the situation whether the subject of the personal information has requested to be forgotten. A steward could say 'see, I've not published the personal information, so I am good.'. 
For other reasons, `tombstoning` has never been accepted as a viable solution to get rid of the liability issue.

Tombstoning does not apply to KERI because in indirect mode KEL and KERLs will be ambient available and in direct mode their are only to parties involved. If a third party would be involved in direct mode, somebody would breach the understanding that it's private communication by design.
_(@henkvancann)_

## What do I need a multi-sig self-addressing identifier for?
To get even more security in terms of your signing scheme.\
(_SamMSmith_)

## What do I need a delegated self-adressing identifier for?
To be able to horizontally scale your identifier system, that consists of a root identifier that manages a bunch of other delegated identifier. Created with a cryptographically derived strong binding, all the way through your infrastructure. Not dependent on any administration at all. \
(_SamMSmith_)

## What do I need a self-signing identifier for?
Often it is an efficiecy measure where the identifier includes the signature as your `content-addressable hash`.\
_(SamMSmith)_

## What do I need a non-transferable identifier for, as KERI supports transferable identifiers?
Its use is different. Many applications of self-certifying identifiers only require temporary use after which the identifier is abandoned. These are called ephemeral identifiers. Other applications may only attach a limited amount of value to the identifier such that replacing the identifier is not onerous.\
Because a non-transferable (ephemeral) identifier is not recoverable in the event of compromise, the only recourse is to replace the identifier with another identifier. In some applications this may be preferable, given the comparable simplicity of maintaining key state.\
In either of these cases a non-transferable self-certifying identifier is sufficient.

## Could you give an example of solely a cryptographically verifiable inception statement 
This is a basic self certifyin identifier (`SCI`). The identifier itself is derived from a public key that is in the identifier. Nothing is connecting that binding of the identifier to the inception statement. Someone could create an different inception statement with other fields, the only thing that need to be the same is the key list. Everything else in the inception statement could be different.\
So that means the only way to know which inception statement is the right one is duplicity detection. So `First seen`  becomes the only means you have to check which inception steatement is the authortiative for that identifier, in case you need an inception statement. 

## Could you give an example of strongly binding the inception statement to the identifier
This a self-addressing self-certifying identifier (`SASCI`) In this case the identifier itself is derived from the inception statement. Now there can only be one inception statement for this identifier. If you'd change just a single bit, other than the identifier field itself, and it's *different* identifier. You can't have duplicitious inception statements. It's not possible. It locks down at least the  inception part and that help in duplicity detection. There can only be one inception statement to start a duplicity log with. From that point on you can have duplicitous next events, but not before. But it still means the effort it takes has to engage in CreatING duplicity, becomes much harder because for example if you include witnesses in the inception statement then any duplicitous event has to publish through the witnesses, and that adds a barrier. Basically it locks down at least the inception part, You can't change it.\
In some cases it would be useful to be able to strongly bind the inception statement to the identifier and not merely rely on a cryptographically verifiable inception statement for the associated identifier. 

## Why ever go for a basic self-certifying identifier (`SCI`) when KERI offers self addressing SCI (`SASCI`) with a better security guarantee?
Because there are many applications where you don't want to have to depend on a KEL because a basic SCI is self-certifying without a KEL. It's more light-weight. For example the non-transferable version of a SCI you can still have an inception event so that basically any tracking anybody does there is still a nominal KEL for that identifier so you can look it up that way, discovering everything, there is always a legitimate version of an inception event for every identifier. 

In many cases you want identifiers that are ephemeral, that you know the only event that could be would be is the inception event. You don't need to see the inception event, if you're using it in an ephemeral context.\
E.g. witnesses use ephemeral SCIs so I don't need a key event log for a witness to verify a signature by a witness. You can do that with watchers as well. In applications like `IOT` where you need light-weight identifiers, you will mostly use SCI (1.). So you would use the basic version.

Want you don't need to do with the basic identifiers is you dont have to say 'I got an identifier but I can't verify the keys before I get the KEL so I dont know the key state'. For the witness there is no key state. There is only ever one key. If the witness is ever compromised, then you get rid of the witness. You can rotate keys or rotate identifiers.\
Rotating an identifier is allowing us to change the keys for an ephemeral identifier.\
In an ephemeral context rotating the keys is the equivalent to rotating the identifier.\

> Example BTC and ETH they are ephemeral public keys, you can't rotate keys in BTC without changing the identifier. You have to move all your funds.

In KERI the closest to 1. is DID:Key. Instead of having multiple DID methods, KERI unifies them all into one protocol.

Look for more info in the KERI slidedeck ["KERI for the DIDified"]({to do}).

# Q&A section Event logs

## What is a Key Event Log?
It's the basis of the source of truth for KERI identifiers. KERI enables cryptographic proof-of-control-authority (provenance) for each identifier. A proof is in the form of an identifier’s key event receipt log (KERL), after a validator verified the registered events, in the chain of events: the key event log (KEL).\
_(@henkvancann)_

## Why is a Key Event Log crucially important?
Without KELs, we wouldn't have a chain of registered and signed key events for an identifier. The availability and consistency of the KEL is crucial for next steps: verification of events and duplicity checks. Without verified KELs there will be no KERL for identifiers at hand.\
_(@henkvancann)_

## How do I create a KEL?
By a key [`inception event`](./Glossary.md#inception-event). A controller creates a key pair and binds this to his/her KERI identifier.
There will be wallet software and an API available in the course of code development and also a DID scheme (DID:UN) that invokes calls to those APIs during resolution of the DID.\
_(@henkvancann)_

## How can I trust a KEL?
It is secured by a `Distributed Hash Table`, so internal inconsistencies are cryptographically provable. If they they are internal consistent the first level of trust is established. Furthermore a KERL is end-verifiable to the root-of-trust. You don't need the whole KERL at all times [Read more why](https://github.com/henkvancann/keri/blob/master/docs/Q-and-A.md#do-i-need-to-show-the-full-log-kel-to-anybody-i-transact-with-even-though-id-only-like-to-show-a-part-of-it-for-example-a-virtual-credential). Together with the external consistency (duplicity check)
_(@henkvancann)_

# Q&A section Inconsistency and duplicity

## What kind of Inconsistencies do we have?
An internally inconsistent KEL, this simply won't verify. 
External inconsistency: two versions of the key event log (KEL).

## How can it be garantueed than an identifier represents a certain identity and not another one?
KERI takes advantage of its cryptographic root of trust with strong bindings, to get an inviable guarantee, based on both internal consistency for the cryptographic root of trust and external consistency using ambient duplicity detection.

## What is Duplicity?
See the [definition](#duplicity). What it means is that we have a way to make judgements about trust in entities.\
_(@henkvancann)_

## What does duplicity look like?
Duplicity takes two forms. In the first form, a `controller` may be deemed duplicitous whenever it produces an event message that is inconsistent with another event message it previously produced. In the second form, a witness may be deemed duplicitous when it produces an event _receipt_ that is in- consistent with another event receipt it previously produced.\
_(SamMSmith)_

## Why should we care about Duplicity?
Duplicity becomes a basis for distrust in a controller or its witnesses. _(SamMSmith)_

# Q&A section Key rotation

## What is Key Rotation?
Changing the key, i.e., replacing it by a new key. The places that use the key or keys derived from it (e.g., authorized keys derived from an identity key, legitimate copies of the identity key, or certificates granted for a key) typically need to be correspondingly updated.

the main purpose of key rotation it to either prevent or recover from a successful compromise of one or more private keys by an exploiter.\
[Source](https://csrc.nist.gov/glossary/term/Key_Rotation).

## Why bother about key rotation?
The primary purpose of rotating encryption keys is not to decrease the probability of a key being broken, but to reduce the amount of content encrypted with that key so that the amount of material leaked by a single key compromise is less.

However, for _signing keys_ there is a concrete reason: say it takes X months of computation (expected value given your threat model) to crack a key, and you rotate your signing key every 𝑋−1 months and revoke the old one, then by the time an attacker has cracked the key, any new signatures produced by the attacker will either be A) rejected by clients because of key expiry, or B) back-dated to before the key revocation (which should also raise warning in clients).\
[Source](https://crypto.stackexchange.com/questions/41796/whats-the-purpose-of-key-rotation).

## Why does KERI solve interoperability with its key rotation scheme? 
KERI uses plain old digital signatures from PKI, intentionally, so that it may be truly universally applied. KERI solves that hard problem of PKI, that is, key rotation in a standard way. Without a standard way of addressing key rotation, there is no interoperability between systems, they break when you rotate keys because no one knows how to verify the key rotation was done properly. KERI solves that problem.


## Wat is Pre-rotation?
Pre-rotation is a _cryptographical commitment (a hash)_ to the _next_ private key in the rotation-scheme. (_@henkvancann_)\
The pre-rotation scheme provides secure verifiable rotation that mitigates successful exploit of a given set of signing private keys from a set of (public, private) key-pairs when that exploit happens sometime **after** its creation _and_ its first use to issue a `self-certifying identifier`. In other words, it assumes that the private keys remains private **until after** issuance of the associated identifier.\
[Source: chapter Pre-rotation in whitepaper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf)

## Why hasn't pre-rotation or forward chaining been done before?
I first wrote about in 2018, it's been public knowledge ever since. I guess people just don't read.\
(_SamMSmith_)

# Q&A section KEL and KERL

## What is the difference between KEL and KERL?
The word 'Receipt' explains it all: the sender signs off the verification of the KEL done by the recipient. That _Receipt_ is hosted in the KERL and is the root-of-trust for KERI.\
<img src="../images/Direct-mode-kel-kerl.png" alt="Direct mode: kel and kerl difference charted" border="0" width="600" style="float:left">
The analogy is the difference between a _two-way_ - and a _three-way handshake_: Did I, the recepient, only verify that the sender's message was valid (two-way using KEL, arrow left to right) or did the sender _sign off the receipt_ of that verification by the recipient (three-way in KERL, arrow right to left)
_(@henkvancann)_



# Q&A section Witness
## Witnesses have no skin in the game, it’s a `nothing at stake` situation, no?
The [KERI slide deck](https://github.com/SmithSamuelM/Papers/blob/master/presentations/KERI2_Overview.web.pdf) has a section called the Duplicity Game.  I suggest reading through that first. Or see the [part of the SSI Meetup](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/) webinar that tackles this.\
(_SamMSmith_)
{TBW prio 2}

## What is the difference between Key Event Receipt Infrastructure (KERI), and distributed hash tables (DHTs)?
{TBW prio 3}

## As long as witnesses keep lying together no one will ever be able to prove them wrong? 
Witnesses do not make any statement about the content of what is being proved. KERI does not
enable someone to proof the *veracity* of a statement only the *authenticity* of the statement. {TBW} \
(_SamMSmith_)

## ***Q: Why does the Witness run in restricted mode?
It’s not **"first seen"** until it’s fully seen by the whole set of witnesses needed (threshold). In the meanwhile the witness in this instance, has to add an escrow. And wait for the witness receipts coming in. And then accept the KEL.
_(@henkvancann)_

## *Q: What is KAACE?
The primary purpose of the KA2CE algorithm is to protect the controller’s ability to promulgate the authoritative copy of its key event history despite external attack. This includes maintaining a sufficient degree of availability such that any validator may obtain an authoritative copy on demand.

# Q&A section Watchers

## How can we detect duplicity? Suppose controller has power over witnesses.
In a Public setting `duplicity detection` protects the validator from any duplicity on the part of the controller and any resources such as witness that are controlled by the controller.

Since a given controller in a public setting may not know who all a given validator is using for duplicity detection (watchers etc), the controller can't ensure that they will not be detected. And once detected any value that their public identifier had is now imperiled because *any entity with both copies can proof irrefutably to any other entity that the controller is duplicitous (i.e. not trustable)*. \
(_SamMSmith_)


# Q&A KERI and blockchain settled DIDs


## ***Q: Is it possible to create a KERI DID that is permanently locked to the "did:key" style / ephemeral?
It is. Sections 2.2.3 - 2.3.1 of the [white paper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf) explains transferrability and the "basic"-type identifier, which always represents a public key and may be either transferrable (can be updated) or non-transferrable (ephemeral/did:key style). section 14.2 actually details how these are encoded, basically check the first few chars of the identifier.\
_(CharlesCunningham)_

## ***Q: DID data model supports verification methods which are not based on public keys or even any cryptography at all. KERI can't do this? 
_In many ways KERI is "better" than DIDs, especially when it comes to proof-of-control. But I think this is one thing that DIDs can do that KERI can't: verification methods which are not based on public keys or even any cryptography at all._

KERI can support them, with some special event type, they use it to store CRDT ops.\
(_@OR13b_)
The point of KERI is to maintain to control of key-derived identifiers. It's not intended to provide all the capabilities of DID.\
(_@_stevetodd__)

## ***Q: Is it fair to say that DID resolution in general is a security weakness and then push forward KERI in that name? 
_Although some DIDs have not kept up with design goals* of DIDs, e.g. did:web, it is too strong to state this in general. It simply depends on the DID method?\
*decentralization, persistence, cryptographic verifiability._

In brief: we argue that the chain is as strong as its weakest ring.

Security is not build into the protocol but indeed as the eloborate question mentions, it depends on the DID method. Which overall is a huge risk for community as people needs to know the security level which each did method brings. From that perspective without unified security model brings us to the similar situation where, me having private email server in the basement to avoid spying by google, I send out my e-mail to you having it on gmail. I have high security and privacy but other side have just security without privacy. The outcome is that security model is applied in wrong place and KERI aims to fix it.\
_(RobertMitwicki)_

## ***Q: Because the DID data model theoretically allows DID methods and verification methods that may NOT be based on cryptographic keys, KERI is capable of spanning all DIDs?

We would like to see some examples of verification methods that are not based on cryptographic keys and are in the scope of DID. The KERI community would like to learn more about these methods. 
It's true KERI is all about cryptographic commitment. But KERI can also support hashed based identifiers e.g. a fingerprint of the content as unique identifier, without the control part.

## ***Q: How do I find all the DIDs that stand for apps, code modules, public businesses, and other entities that benefit from being publicly discoverable on a decentralized deterministically iterable registry?
_How might one build a decentralized deterministically iterable registry for such use cases where the entries are securely known to be from the matching Identifier?_\
_The reason I am asking is to get people to think about the system they'd inevitably need to create to support the 95% of use cases (given 95% of identity interactions are between personas of people, places, and things that are discoverable)_\
_Is it not a helpful exercise to game out the things required to support 95% of DID use cases with other DID system developers?_

It's considered a privacy property of KERI, that you cannot enumerate all identitiess, in the same way that finding all minorities of certain religious preference might not be a feature.\
(_@OR13b_)

Discovery is a layer on top of what KERI provides. KERI doesn't preclude DID, nor does it need to implement all of DID. KERI will participate in the DID ecosystem. (_@_stevetodd__)\
It doesn't need/want to solve/serve that slice of the use case pie.

#### Follow up question 1: Why does KERI rule out 95% of the DID-based use cases upfront, where we need public discoverability on a decentralized deterministically iterable registry?
```
The vast majority of users use apps and services that are exchanges between or about the well-known, 
publicly resolvable registered persona DIDs of people, places, or things? 
Let's list a few to see how much of human digital life it covers:
- All social media: Twitter, Facebook, Instagram, Telegram, Signal, etc.
- All public content creation: YouTube, SoundCloud, Spotify, etc.
-All current registries: NPM, all app stores, all things that use those registries 
    (basically every piece of software on the planet)
- All publicly registered objects: cars, boats, airplanes, etc.
Put it this way: very few use cases on this planet will not directly, or within them, 
rely on publicly iterable, globally registered persona DIDs. 
But that said, I'm interested in hearing other opinions or counter arguments to the contrary.
(_@csuwildcat_)
```
*There is an implicit need for the registry to track its entries as DIDs. I guess those 95% use cases will have to get other types of DIDs for that?*

It's possible to make a DID doc that represents a KERI identifier. If you want to resolve it, you can put it in any number of blockchains. That just publishes it. However, they don't have to be published to work. \
(_@_stevetodd__)

Or for example TOR hidden services, these are not designed to be discoverable. In fact, the whole point of tool is to provide anonymity. Anonymity is a property of set membership, and it's destroyed by making the sets small or enumerable.
(_@OR13b_)

 In many scenarii, what the elaborate question explains makes sense. I can understand a different design goal/priority for KERI, I think the rationale is quite clear in terms of where it stands in the DID space.
(_@fimbault_)

#### Follow up question 2: That's not deterministic?! 
_You can't have Registry A magically just trust that a DID from Other System B, it would need to be native to it?_
_Any registry with deterministically resolvable entries requires the entry controllers' IDs and resolutions be native to it. That's an empirical computer science wall type of requirement._ \
_Imagine I want to register a DID in a decentralized deterministically iterable registry - something anyone can run and deterministically know all entries registered with it, wherein the registry has no central entities or authorities that determine the bindings between entries and those who control them..._\
**_Nowhere in any paper on this planet is this a solved problem, because it's basically NP hard_**

It depends on what you mean by resolve. The [white paper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf) explains the points brought up in this question.
(_@_stevetodd__)

{TBW prio 1}


## Nowhere in any paper on this planet is this a solved problem, because it's basically NP hard
Orie Steele (Transmute)  12:30 AM\
its considered a privacy property of KERI, that you cannot enumerate all identitiess


# Q&A Security Guarantees

## What are the security risks of KERI with regard to the identity protocol?
Harm that can be done to the a `controller`: Unavailability, loss of control authority, externally forced duplicity\
Harm that can be done to a `validator`: _Inadvertent acceptance_ of verifiable - but forged or duplicitous events 

Breaking the promise of global consistemcy by a controller is a provable liability. However, global consistency may only matter after members of that community need to interact, not before.\
(_SamMSmith_)

## How secure is the KERI infrastructure?
KERI changes the discussion about security. From a discussion about the security of _infrastructure_ to a discussion about the security of your _key management infrastructure_. Most people when they think security, the think "oh, blockchain!": permissioned or permissionless, how hard is it to get 51% attack, etc.Non of that matters for KERI. KERI is all about "are your private keys private?!" And if _yes_, that drastically slims down the security discussion to brute force attacks to public keys. And because the next public keys are in fact protected by a hash, you have to brute force the hash algorithm, that is post-quantum secure.
So that is a very high level of infrastructural security.

So private key management and protection is the root of your security in KERI.

## Can I rotate keys with Tangem in KERI?
_Suppose I'd trust a Tangem card for generating public private key pairs at will and the NFC communication allowing to interact with a wallet app._

One of the main concerns is that there is a theoretical link (a binding) between the cards and a user, via the card-ID (CID). However the CID is used only for checking the authenticity and integrity of the chip itself. Tangem publishes and anchors a list of CIDs with corresponding public addresses in a public blockchain. When checking authenticity, the verifier looks up the pub CID and corresponding pub address in the published list, and verifies that the chip controls the correct pub address by means of a challenge-response scheme. 
Even though for blockchain or SSI interactions, a completely new wallet with new pub/priv keypair is generated, the pub/priv key of the CID is used when the authenticity of the chip is checked by means of a challenge response scheme. Everything happens in the client app (2021: iOS or Android; and the client code is open source), where there is no communication with Tangem, so Tangem is not able to see any activity conducted by this CID in an authenticity check.
The CID and corresponding key pairs are not used in any other interaction. A new wallet with new pub/private key pair is generated on chip, with these keys being used for any transactions, signing, etc. 

Q: With the chip firmware being proprietary, how can we be sure that the newly generated private keys for new wallets are not still linked somehow to the cards CID?
A: The firmware is audited by Kudelski and can be verified with a published hash. 
TBD: How can it be verified, when and by whom? If the firmware is not open source, then somebody has to draw a hash from it in an authorized situation. However, Tangem cards are EAL6+ and FIDO2 certified.

On the issue of Rotation:
{TBW prio 2}

## DHTs are not an immutable linear chronology oracle, which is the heart of the actual security problem. You claim KERI solves the security problem with DHTs?!
The immutable linear chronology is provided by the key event log (`KEL`) data structure itself. Getting a full copy is all you need. When retrieving a KEL over a network, then as you say a witness can prune some amount of the latest events, but every witness would have to be compromised for that to be undetectable.\
If parties are so concerned, they could establish a large collectivised set of witnesses that sign and distribute all key events presented to this network (this would essentially be a `Proof of Authority`/federated blockchain but would require (configurable)% compromise for undetectable pruning of recent history. Only PoA/federated because the witness sets are designated by the controllers, so you could not just use arbitrary witnesses who join and leave the network at leisure (afaik).

The difference between the chain and the DHT is that not all DHT nodes act as witnesses for all KELs in the system (in the sense that they dont provide receipts for every KEL and arent referenced in the witness sets of every KEL), but they could all (or at least the ones holding the KEL you seek) still provide availability for KELs and thus would have to all be compromised in order to hide a recent-history-pruning, only one has to transmit the new/complete version to prove all the other versions as being old/incomplete.\
_(CharlesCunningham)_

The point of KERI is to encapsulate all the guarantees within `KEL`s nothing else is needed. DHT is just for resolution process to find a place from where I can get it. This place can change as you like I could even get it in p2p interaction from someone else. DHT seems to be the most reasonable way to build solid infrastructure for resolution process but none of the nodes can actually inject or tamper KELs so you don't have to trust them or get any guarantees from them. Since if the node will miss behave it is very easy to detect that.\
_(RobertMitwicki)_

## You are arguing KERI affords greater security than a decentralized linear event system like Bitcoin?
_...you would be fundamentally arguing that you can record a singular, immutable linear event history more securely than Bitcoin, and I see nothing in KERI that would indicate that._

Read the answer to [this](#keri-is-basically-a-series-of-pay2publickeyhash-transactions) first.

If you read Szabo's paper on threshold structures, you get security of the same type when ever you use a threshold structure, be it MFA, Multi-Sig, or Distributed consensus. They all are using a combination of multiple relatively weak attack surfaces that must be simulatenously compromised for a successful attack. So multiplying simulatneous weak surfaces = functional equivalent of a stronger attack surface.  So when you look at KERI you see that the security is primarily due to cryptographic strength and the witnesses are not the primary source of security but merely secure one thing, that is the availability of the KEL for an identifier. Not the KEL itself. The KEL iteself is secured by signatures.\
From a Validator perspective their security is due to duplicity detection. Successful attack against duplicity detection requires an eclipse attack. Ledgers such as bitcoin are also susceptible to eclipse attacks. So in an apples to apples (resistance to eclipse attack) a KERI watcher network of comparable reach (1000's of watchers) would have comparable resistance to an eclipse attack.

#### ***Q: Differences between blockchain-based security and KERI security
- Where KERI doesn't need total ordering in its logs, blockchain do need that. What KERI needs is watchers that construct string of event in the relative order of reception of the KEL  {TBW please explain or improve this: what is this, why is it important?}
- Another characteristic is that KERI identifiers are transferable and blockchain-based identifiers are not, they are bound to their ledger.