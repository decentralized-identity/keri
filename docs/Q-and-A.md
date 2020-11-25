# Q&A about KERI
- [Q&A about KERI](#q-a-about-keri)
    + [Disclaimer](#disclaimer)
    + [List of questions and definitions](#list-of-questions-and-definitions)
  * [Knowledge you should be confidently applying](#knowledge-you-should-be-confidently-applying)
  * [Actions you should be comfortable with](#actions-you-should-be-comfortable-with)
- [Jump table to categories](#jump-table-to-categories)

Inspired by presentation given and questions asked on the [SSI webinar May 2020](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/), but also issues raised and the progress made, here on Github (Turn on 'Watch' if you want to be notified of conversations).

Beware: A Q&A is always *work in progress*. Tips & help welcome.


### Disclaimer
None of the respondents in the **open** repo and presentations have been explicitly named as a source, except for ***Samuel M. Smith Ph.D.*** and ***@henkvancann***. If there is no reference added to the answers, then it's Samuel M. Smith who answered the question. Most of the editing is done by @henkvancann, which might have introduced ommission, errors, language glitches and such. Sorry for that, feel free to correct by submitting a pull request (PR)
For practical reasons educational images uploaded by Github members have been downloaded. We de-personalised them by giving images a new name. Under these new names these images have been uploaded to github and used in the Q&A to clarify the questions and answers.

Keri's content is licensed under the [CC by SA 4.0. license](https://creativecommons.org/licenses/by-sa/4.0/). Parts of the video offered on SSI Meetup webinar 58 have been captured and uploaded to Github to support the answers to general questions about digital identity and more in depth answers to question about Keri.

We've done our best to protect the privacy of the Github by investigating the images we used. We haven't come across personal identifiable information (pii). However, should we have made a mistake after all, please let us know and we'll correct this immediately.

### List of questions and definitions

- [Definitions](#definitions)<br/>
- [Q&A section General](#q-a-section-general)
  * [What is KERI?](#what-is-keri)
  * [Why use KERI?](#why-use-keri)
  * [In what programming languages is KERI available?](#In-what-programming-languages-is-keri-available)
- [Q&A section Userinterface](#q-a-section-userinterface)
- [Q&A section KERI operational](#q-a-section-keri-operational)
  * [Where can I download KERI?](#where-can-i-download-keri)
- [Q&A section KEL and KERL](#q-a-section-kel-and-kerl)
- [Q&A section Wallets](#q-a-section-wallets)
- [Q&A section Private Key Management](#q-a-section-private-key-management)
- [Q&A section Blockchain](#q-a-blockchain)
- [Q&A section Agencies](#q-a-key-agencies)
- [Q&A section Witness](#q-a-section-Witness)
- [Q&A section Watchers](#q-a-section-watcher)

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
- [General](#q-a-section-general)
- [KERI operational](#q-a-section-keri-operational)
- [Userinterface](#q-a-section-userinterface)
- [Root of trust](#q-a-section-root-of-trust)
- [Why the internet is broken](#q-a-section-why-the-internet-is-broken)
- [Identifiers](#q-a-section-identifiers)
- [Event logs](#q-a-section-event-logs)
- [Inconsistency and duplicity](#q-a-inconsistency-and-duplicity)
- [Key rotation](#q-a-key-rotation)
- [KEL and KELR](#q-a-section-kel-and-kerl)
- [Wallets](#q-a-section-wallets)
- [Signatures](#q-a-section-signatures)
- [Proofs](#q-a-section-proofs)
- [Private Key Management](#q-a-section-private-key-management)
- [Blockchain](#q-a-key-blockchain)
- [Agencies](#q-a-key-agencies)
- [Witness](#q-a-section-Witness)
- [Watchers](#q-a-section-watcher)

# Definitions

## Abbreviations
In alphabetic order:<br/>
AID = [Autonomous Identifier](#autonomous-identifier)<br/>
DID = [Decentralized Identity](#decentralized-identity) or Digital Identity dependent of the context.<br/>
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

#### Decentralized Identity
DID; {TBW}
#### Duplicity

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

#### (Digital Identity) Wallet
In our context it is software and sometimes hardware that serves as a key store and functionality. Keys can be private keys and public keys, hashes and pointers. Functionality can be signing, invoices (receive), send, virtual credentials, delegation, etc. This is the [`agency`](#agency) part of a wallet. <br/>
[More about digital ID Wallets](https://www.thalesgroup.com/en/markets/digital-identity-and-security/government/identity/digital-identity-services/digital-id-wallet)<br/>
[More about cryto Wallets](https://cryptocurrencyfacts.com/what-is-a-cryptocurrency-wallet/).

# Q&A section General

## What is KERI?
Key Event Receipt Infrastructure; a secure identifier overlay for the internet.

## Is KERI a DID?
KERI is not a DID method. The related DID method is [`did:un`](https://github.com/decentralized-identity/keri/blob/master/did_methods/un.md). A session at the recent **IIW31** presented by Jolocom’s *Charles Cunningham* examines overlap between data models of DID documents and KERI identifiers [here](https://jolocom.io/blog/as-seen-at-iiw31-keri/).

## Why use KERI?
Because there is no secure universal trust layer for the internet, currently (2020).

## In what programming languages is KERI available?
In Python. It will be available in the coming year in Rust, Javascript and Go (2020).

## How KERI fit in [the 10 principles of SSI](https://medium.com/metadium/self-sovereign-identity-principle-6-portability-4a7105dd0381) by Christopher Allen?
KERI is not primarily about self-sovereign identity. KERI is primarily about autonomic identifiers, AIDs. That is identifiers that are self managing. KERI provides proof of control authority over the identifier. What one does with the identifier is not constrained by KERI. But because the primary root of trust of an AID is a KEL which can be hosted by any infrastructure, any identity system (SSI or otherwise) built on top of KERI may also be portable.  So in my opnion portability of the associated identifiers is essential to any truly self-sovereign identity system. That portability, as such, is not one of the principles is a defect in the principles.

Christopher Allen is talking about *portability of information* related to the identity, not the *portability of the identifier itself* with respect to its supporting infrastructure (aka spanning layer).  Indeed, most `DID` methods, including those  that publicly claim to be `SSI` in accordance with the principles do not have portable identifiers. They are locked to a given ledger.

##### Addition to point 1: example
Example image
<img src="./Images/FinalSolutionGW.png" alt="Final multisig solution" border="0" width="600">
<br/>

Example reference outside KERI github:

<small><i>[Answer provided in FullyNoded Q&A too](https://github.com/Fonta1n3/FullyNoded/blob/master/Docs/Q-and-A.md#question--gordian-wallet-there-is-no-add-manually-like-in-fullynoded) </i></small>

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

# Q&A section Root of trust
## What do I need to trust in KERI?
Primary root of trust is KEL not secondary  (starts with self cert ID but then after first rotation if any must have KEL)

## KERI does not need a blockchain, but how does it establish the root of trust that we need for SSI? How does the data persist?
The KELs are what establishes the root of trust in KERI. So you have a SCI and a KEL. The KEL is ordered with respect to the SCI by the controller. You don't need total ordering with respect to other identifiers to establish the root of trust in KERI.<br/>
In blockchains you need total ordering, which you need for double spend protecting in cryptocurrencies, but not in KERI.<br/>
For people in blockchain this is a bit hard to grasp, but we don’t need hash chain data structure of events on single identifier nor the *ordering* those, I just need logs, I need *append-only logs of events* to establish the authority.
And so I detect myself against `duplicity`.

# Q&A section Why the internet is broken
# Q&A section Identifiers
# Q&A section Event logs
# Q&A section Inconsistency and duplicity
# Q&A section Key rotation
# Q&A section KEL and KERL
# Q&A section Wallets
# Q&A section Signatures
# Q&A section Proofs
# Q&A section Private Key Management
# Q&A section Blockchain

## Does KERI use a blockchain?
No, but KERI uses the same cryptographical building blocks
## What's the difference between KERI and blockchain?
`KERI` is a unordered hash-linked list of signed Key Event logs and blockchain is a timestamped ordered list of hash-linked blocks of signed transactions. What this means:
1. we don't need ordering in `KERI` and that frees us from consensus protocols in blockchains
2. Hash-linking is done on a lower level in `KERI` and preserves consistency and fuels revealance of duplicity.
3. In `KERI` proofs are cryptographically derived from the root of trust, being the autonomous controller, in blockchains the root-of-trust is a transaction on a ledger; that means the Identifier gets locked on the ledger.

# Q&A section Agencies
# Q&A section Witness
## Witnesses have no skin in the game, it’s a `nothing at stake` situation, no?
The [KERI slide deck](https://github.com/SmithSamuelM/Papers/blob/master/presentations/KERI2_Overview.web.pdf) has a section called the Duplicity Game.  I suggest reading through that first. Or see the [part of the SSI Meetup](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/)webinar that tackles this.

{TBW}
## As long as witnesses keep lying together no one will ever be able to prove them wrong? 
Witnesses do not make any statement about the content of what is being proved. {TBW}
# Q&A section Watchers