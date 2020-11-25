# Q&A about KERI
<img src="../images/Keri_logo_color_on_white.png" alt="KERI logo" border="0" width="300">

- [Q&A about KERI](#qa-about-keri)
    + [Disclaimer](#disclaimer)
    + [List of questions and definitions](#list-of-questions-and-definitions)
  * [Knowledge you should be confidently applying](#knowledge-you-should-be-confidently-applying)
  * [Actions you should be comfortable with](#actions-you-should-be-comfortable-with)
- [Jump table to categories](#jump-table-to-categories)

Inspired by presentation given and questions asked on the [SSI webinar May 2020](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/), but also issues raised and the progress made, here on Github (Turn on 'Watch' if you want to be notified of conversations).

Beware: A Q&A is always *work in progress*. Tips & help welcome.


### Disclaimer
None of the respondents in the **open** repo and presentations have been explicitly named as a source, except for ***Samuel M. Smith Ph.D.*** and ***@henkvancann***. If there is no reference added to the answers, then it's Samuel M. Smith who answered the question. Most of the editing is done by @henkvancann, which might have introduced ommission, errors, language glitches and such. Sorry for that, feel free to correct by submitting a pull request (PR).<br/>
For practical reasons educational images uploaded by Github members have been downloaded. We de-personalised them by giving images a new name. Under these new names these images have been uploaded to github and used in the Q&A to clarify the questions and answers.

Keri's content is licensed under the [CC by SA 4.0. license](https://creativecommons.org/licenses/by-sa/4.0/). Parts of the video offered on SSI Meetup webinar 58 have been captured and uploaded to Github to support the answers to general questions about digital identity and more in depth answers to question about Keri.

We've done our best to protect the privacy of the Github by investigating the images we used. We haven't come across personal identifiable information (pii). However, should we have made a mistake after all, please let us know and we'll correct this immediately.

### List of questions and definitions

- [Definitions](#definitions)<br/>
- [Q&A section General](#qa-section-general)
  * [What is KERI?](#what-is-keri)
  * [Why use KERI?](#why-use-keri)
  * [In what programming languages is KERI available?](#In-what-programming-languages-is-keri-available)
- [Q&A section KERI operational](#qa-keri-operational)
  * [Where can I download KERI?](#where-can-i-download-keri)
- [Q&A section Userinterface](#qa-section-userinterface)
- [Q&A section Root of Trust](#qa-section-root-of-trust)
- [Q&A section Why the internet is broken](#qa-section-why-the-internet-is-broken)
- [Q&A section Identifiers](#qa-section-identifiers)
- [Q&A section Event logs](#qa-section-event-logs)
- [Q&A section Inconsistency and duplicity](#qa-inconsistency-and-duplicity)
- [Q&A section Key rotation](#qa-key-rotation)
- [Q&A section KEL and KERL](#qa-section-kel-and-kerl)
- [Q&A section Wallets](#qa-section-wallets)
- [Q&A section Signatures](#qa-section-signatures)
- [Q&A section Proofs](#qa-section-proofs)
- [Q&A section Private Key Management](#qa-section-private-key-management)
- [Q&A section Blockchain](#qa-blockchain)
- [Q&A section Agencies](#qa-key-agencies)
- [Q&A section Witness](#qa-section-Witness)
- [Q&A section Watchers](#qa-section-watcher)

## Knowledge you should be confidently applying
- The definitions above
- Public private key pairs
- Bitcoin Improvement Protocols: BIP32, BIP39, BIP44, BIP47, BIP49, BIP84, BIP174
- hierarchical deterministic derivation paths
- Base58
- Eliptic curves
## Actions you should be comfortable with
- Amend knowledge and keep existing knowledge up to date
- create a key pair safely and back it up safely
- recover from a seed
- sweep to a new wallet

# Jump table to categories
- [General](#qa-section-general)
- [KERI operational](#qa-section-keri-operational)
- [Userinterface](#qa-section-userinterface)
- [Root of trust](#qa-section-root-of-trust)
- [Why the internet is broken](#qa-section-why-the-internet-is-broken)
- [Identifiers](#qa-section-identifiers)
- [Event logs](#qa-section-event-logs)
- [Inconsistency and duplicity](#qa-inconsistency-and-duplicity)
- [Key rotation](#qa-key-rotation)
- [KEL and KELR](#qa-section-kel-and-kerl)
- [Wallets](#qa-section-wallets)
- [Signatures](#qa-section-signatures)
- [Proofs](#qa-section-proofs)
- [Private Key Management](#qa-section-private-key-management)
- [Blockchain](#qa-key-blockchain)
- [Agencies](#qa-key-agencies)
- [Witness](#qa-section-Witness)
- [Watchers](#qa-section-watcher)

# Definitions

## Abbreviations
In alphabetic order:<br/>
AID = [Autonomous Identifier](#autonomous-identifier)<br/>
DID = [Decentralized Identity](#decentralized-identity) or Digital Identity dependent of the context.<br/>
DIF = Decentralized Identity Foundation, https://identity.foundation
KEL = [Key Event Log](#key-event-log)<br/>
KERL = [Key Event Receipt Log](#key-event-receipt-log)<br/>
KERI = [Key Event Receipt Infrastructure](#key-event-receipt-infrastructure)<br/>
PKI = [Public Key Infrastructure]()<br/>
PR = Pull Request; github terminology<br/>
SAI = [Self Addressing Identifier](#self-addressing-identifier)<br/>
SCI = [Self Certifying Identifier](#self-certifying-identifier)<br/>
SSI = [Self Sovereign Identity](#self-sovereign-identity)<br/>


#### Agency
Agents can be people, edge computers and the functionality within [`wallets`](#digital-identity-wallet). The service an agent offers is agency.

#### Autonomous Identifier

#### Controller
The controller of an `autonomous identifier` is the entity (person, organization, or autonomous software) that has the capability, as defined by derivation, to make changes to an `Event Log`. This capability is typically asserted by the control of a single inception key. In DIDs this is typically asserted by the control of set of cryptographic keys used by software acting on behalf of the controller, though it may also be asserted via other mechanisms. In KERI an AID has one single controller. Note that a DID may have more than one controller, and the DID subject can be the DID controller, or one of them.

#### Decentralized Identity
DID; {TBW}
#### Duplicity
In `KERI` consistency is is used to described data that is internally consistent and cryptographically verifiably so. Duplicity is used to describe external inconsistency. Publication of two or more versions of a `KEL` log, each of which is internally consistent is duplicity. Given that signatures are non-repudiable any duplicity is detectable and provable given possession of any two mutually inconsistent versions of a `KEL`.  

#### Establishment Event

#### External consistency

#### Inception Event

#### Inconsistency

#### Internal inconsistency
In KERI we are protected against Internal inconsistency by the hash chain datastructure of the `KEL`, because the only authority that can sign the log is the controller itself. 

#### Key Event Log

#### Key Event Receipt Log

#### Non-Establishment Event

#### Public Key Infrastructure
A public key infrastructure (PKI) is a set of roles, policies, hardware, software and procedures needed to create, manage, distribute, use, store and revoke digital certificates and manage public-key encryption. [Wikipedia].(https://en.wikipedia.org/wiki/Public_key_infrastructure)

#### Root of trust
Replace human basis-of-trust with cryptographic root-of-trust. With verifiable digital signatures from asymmetric key crypto we may not trust in “what” was said, but we may trust in “who” said it.<br/>
The root-of-trust is consistent attribution via verifiable integral non-repudiable statements.

#### Seal
A seal is cryptographic anchor; we have:<br/>
1. Digist Event Seal
2. Hash tree root Seal
3. Event Seal
Seals deliver authenticity proofs in KERI.

#### Self Addressing Identifier

#### Self Certifying Identifier

#### Self Sovereign Identity

#### Spanning layer

#### Validator

#### (Digital Identity) Wallet
In our context it is software and sometimes hardware that serves as a key store and functionality. Keys can be private keys and public keys, hashes and pointers. Functionality can be signing, invoices (receive), send, virtual credentials, delegation, etc. This is the [`agency`](#agency) part of a wallet. <br/>
[More about digital ID Wallets](https://www.thalesgroup.com/en/markets/digital-identity-and-security/government/identity/digital-identity-services/digital-id-wallet)<br/>
[More about cryto Wallets](https://cryptocurrencyfacts.com/what-is-a-cryptocurrency-wallet/).

# Q&A section General

## What is KERI?
Key Event Receipt Infrastructure; a secure identifier overlay for the internet.

## Is KERI a DID?
KERI is not a DID method. The related DID method is [`did:un`](https://github.com/decentralized-identity/keri/blob/master/did_methods/un.md). A session at the recent **IIW31** presented by Jolocom’s *Charles Chunningham* examines overlap between data models of DID documents and KERI identifiers [here](https://jolocom.io/blog/as-seen-at-iiw31-keri/).

## Why use KERI?
Because there is no secure universal trust layer for the internet, currently (2020).

## Who is KERI? Is it a company or a not for profit?
KERI sits under the *Decentralized Identity Foundation*, [DIF](https://identity.foundation), and within that in the *Identity and Discovery* Workgroup.
Due to its licensing structure, KERI isn't owned by anyone and everyone at the same time. The Intellectual Property Right of KERI is hosted with DIF. It is an open source project.

On github KERI is - and will become even more - a thickening bunch of repositories:<br/>
 1. https://github.com/decentralized-identity/keri 
 2. https://github.com/decentralized-identity/keripy
 3. etc.
 Lastly, the important man, who founded KERI is *Samuel M. Smith Ph.D.*, operationing from his firm [prosapien.com](https://www.prosapien.com). 

## In what programming languages is KERI available?
In Python. It will be available in the coming year in Rust, Javascript and Go (2020).

## How KERI fit in [the 10 principles of SSI](https://medium.com/metadium/self-sovereign-identity-principle-6-portability-4a7105dd0381) by Christopher Allen?
KERI is not primarily about self-sovereign identity. KERI is primarily about autonomic identifiers, AIDs. That is identifiers that are self managing. KERI provides proof of control authority over the identifier. What one does with the identifier is not constrained by KERI. But because the primary root of trust of an AID is a KEL which can be hosted by any infrastructure, any identity system (SSI or otherwise) built on top of KERI may also be portable. <br/>So in my opnion portability of the associated identifiers is essential to any truly self-sovereign identity system. That portability, as such, is not one of the principles is a defect in the principles.

Christopher Allen is talking about *portability of information* related to the identity, not the *portability of the identifier itself* with respect to its supporting infrastructure (aka spanning layer).  Indeed, most `DID` methods, including those  that publicly claim to be `SSI` in accordance with the principles do not have portable identifiers. They are locked to a given ledger.

# Q&A section KERI operational

## Where can I download KERI?
On (sub)page(s of) [github](https://github.com/decentralized-identity/keri)

## Where can we find the code and how could a coder get started?
The homepage on github [README.md](../README.md) pretty much sums up all the possibilities to download the available code and how developers can engage in the development process currently. We welcome all help we can get.

## What would you see as the main drawback of Keri?
Its main drawback is that it's nascent.

## How can it one solution, fit for all SSI problems? 
KERI uses plain old digital signatures from `PKI`, intentionally, so that it may be truly universally applied. KERI solves that hard problem of PKI, that is, key rotation in a standard way. Without a standard way of addressing key rotation, there is no interoperability between systems, they break when you rotate keys because no one knows how to verify the key rotation was done properly. `KERI` solves that problem. 

## Where you would need something quite different than KERI?
`KERI` does one thing, it establishes control authority using verifiable portable proofs that are `KEL`s. 

# Q&A section Userinterface
## What does KERI look like?
Currently `KERI` is just code, that can be tested and executed in a terminal on the command line. Private key management of KERI will look like wallets and Key Event Logs and Key Event Receipt Log are files with lots of encrypted stuff in there.

## Is there a KERI course or webinar available?
The [SSI Meetup](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/) webinar on KERI took place in May 2020 and is a good lesson and source of information.

## Could Keri work for edge computers that need self sovereign identity? How to (selectively) share control over the `SCI`/`SAI` with the owners of the device?
Delegation could be used. There is an [issue about IoT](https://github.com/decentralized-identity/keri/issues/54) key and identifier management with `KERI` that answers this question profoundly.

# Q&A section Root of trust
## What do I need to trust in KERI?
Primary root of trust is KEL not secondary  (starts with self cert ID but then after first rotation if any must have KEL)

## KERI does not need a blockchain, but how does it establish the root of trust that we need for SSI? How does the data persist?
The KELs are what establishes the root of trust in KERI. So you have a SCI and a KEL. The KEL is ordered with respect to the SCI by the controller. You don't need total ordering with respect to other identifiers to establish the root of trust in KERI.<br/>
In blockchains you need total ordering, which you need for double spend protecting in cryptocurrencies, but not in KERI.<br/>
For people in blockchain this is a bit hard to grasp, but we don’t need hash chain data structure of events on single identifier nor the *ordering* those, I just need logs, I need *append-only logs of events* to establish the authority.<br/>
And so I defend myself against `duplicity`.

# Q&A section Why the internet is broken
# Q&A section Identifiers
# Q&A section Event logs
# Q&A section Inconsistency and duplicity
# Q&A section Key rotation
# Q&A section KEL and KERL
# Q&A section Wallets
# Q&A section Signatures
# Q&A section Proofs
## How can we verify that a statement by a controller is valid
We may verify that the controller of a private key, (the who), made a statement but not the `validity` of the statement itself.
## How can we trust what was said or written?
We may build trust over time in what was said via histories of verifiably attributable (to whom) consistent statements, i.e. `reputation`.

# Q&A section Private Key Management
# Q&A section Blockchain

## Does KERI use a blockchain?
No, but KERI uses the same cryptographical building blocks as blockchains do.

## What's the difference between KERI and blockchain?
`KERI` is a unordered hash-linked list of signed Key Event logs and blockchain is a timestamped ordered list of hash-linked blocks of signed transactions. What this means:<br/>
1. we don't need ordering in `KERI` and that frees us from consensus protocols in blockchains
2. Hash-linking is done on a lower level in `KERI` and preserves consistency and fuels revealance of duplicity.
3. In `KERI` proofs are cryptographically derived from the root of trust, being the autonomous controller, in blockchains the root-of-trust is a transaction on a ledger; that means the Identifier gets locked on the ledger.

# Q&A section Agencies

## How can KERI offer consistent services and truth?
A. In a pair-wise setting  each party only needs to be consistent with the other party. Witnesses are not used. It doesn't matter if they lie to each other as long as they lie consistently. KERI does not
enable someone to proof the *veracity* of a statement only the *authenticity* of the statement.

B. If 3 parties are involved in a transaction all they need do is query each other for the copy of the `KEL` that each is using for each other to ensure that there is no duplicity.

C. To **guarantee *undetectable* duplicity** requires a successful eclipse attack* on all the parties. `KERI` merely requires that there be sufficient duplicity detection in the ecosystem. <br/>
This would be a set of `watchers` that the validators trust that record any and all copies of key event logs (`KEL`) that they see.  Because these `watchers` can be anyone and anywhere, any controller of a public identifier is at peril should they choose to publish inconsistent copies of their `KEL`. This removes the incentive to be duplicitous.<br/>
'* Any blockchain system is also vulnerable to such an eclipse attack.

# Q&A section Witness
## Witnesses have no skin in the game, it’s a `nothing at stake` situation, no?
The [KERI slide deck](https://github.com/SmithSamuelM/Papers/blob/master/presentations/KERI2_Overview.web.pdf) has a section called the Duplicity Game.  I suggest reading through that first. Or see the [part of the SSI Meetup](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/) webinar that tackles this.

{TBW}
## As long as witnesses keep lying together no one will ever be able to prove them wrong? 
Witnesses do not make any statement about the content of what is being proved. KERI does not
enable someone to proof the *veracity* of a statement only the *authenticity* of the statement. {TBW}

# Q&A section Watchers

## How can we detect duplicity? Suppose controller has power over witnesses.
In a Public setting `duplicity detection` protects the validator from any duplicity on the part of the controller and any resources such as witness that are controlled by the controller.

Since a given controller in a public setting may not know who all a given validator is using for duplicity detection (watchers etc), the controller can't ensure that they will not be detected. And once detected any value that their public identifier had is now imperiled because *any entity with both copies can proof irrefutably to any other entity that the controller is duplicitous (i.e. not trustable)*.
