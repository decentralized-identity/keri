# Q&A about Keri
- [Q&A about Keri](#q-a-about-keri)
    + [Disclaimer](#disclaimer)
    + [List of questions and definitions](#list-of-questions-and-definitions)
  * [Knowledge you should be confidently applying](#knowledge-you-should-be-confidently-applying)
  * [Actions you should be comfortable with](#actions-you-should-be-comfortable-with)
- [Jump table to categories](#jump-table-to-categories)

Inspired by presentation given and questions asked on the [SSI webinar May 2020](https://ssimeetup.org/key-event-receipt-infrastructure-keri-secure-identifier-overlay-internet-sam-smith-webinar-58/), but also issues raised and the progress made, here on Github (Turn on 'Watch' if you want to be notified of conversations).

Beware: A Q&A is always *work in progress*. Tips & help welcome.


### Disclaimer
None of the respondents in the **open** repo and presentations have been explicitly named as a source, except for ***Samuel M. Smith Ph.D.*** and ***@henkvancann***. For practical reasons educational images uploaded by Github members have been downloaded. We de-personalised them by giving images a new name. Under these new names these images have been uploaded to github and used in the Q&A to clarify the questions and answers.

Keri's content is licensed under the [CC by SA 4.0. license](https://creativecommons.org/licenses/by-sa/4.0/). Parts of the video offered on SSI Meetup webinar 58 have been captured and uploaded to Github to support the answers to general questions about digital identity and more in depth answers to question about Keri.

We've done our best to protect the privacy of the Github by investigating the images we used. We haven't come across personal identifiable information (pii). However, should we have made a mistake after all, please let us know and we'll correct this immediately.

### List of questions and definitions

- [Definitions](#definitions)<br/>
- [Q&A section General](#q-a-section-general)
  * [What is Keri?](#what-is-keri-)
  * [Why use Keri?](#why-use-keri-)
  * [In what programming languages is Keri available?](#In-what-programming-languages-is-keri-available-)
- [Q&A section Userinterface](#q-a-section-userinterface)
- [Q&A section Keri operational](#q-a-section-keri-operational)
  * [Where can I download Keri?](#where-can-i-download-keri-)
- [Q&A section KEL and KELR](#q-a-section-kel-and-kerl)
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
- Base 58
- Eliptic curves
## Actions you should be comfortable with
- Amend knowledge and keep existing knowledge up to date
- create a key pair safely and back it up safely
- recover from a seed
- sweep to a new wallet

# Jump table to categories
- [General](#q-a-section-general)
- [Keri operational](#q-a-section-keri-operational)
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
KEL = [Key Event Log](#key-event-log)<br/>
KERL = [Key Event Receipt Log](#key-event-receipt-log)<br/>


#### Agency
Agents can be people, edge computers and the functionality within [`wallets`](#digital-identity-wallet). The service an agent offers is agency.
#### Duplicity

#### External consistency

#### Internal consistency

#### Key Event Log

#### Key Event Receipt Log

#### Root of trust

#### (Digital Identity) Wallet
In our context it is software and sometimes hardware that serves as a key store and functionality. Keys can be private keys and public keys, hashes and pointers. Functionality can be signing, invoices (receive), send, virtual credentials, delegation, etc. This is the [`agency`](#agency) part of a wallet. <br/>
[More about digital ID Wallets](https://www.thalesgroup.com/en/markets/digital-identity-and-security/government/identity/digital-identity-services/digital-id-wallet)<br/>
[More about cryto Wallets](https://cryptocurrencyfacts.com/what-is-a-cryptocurrency-wallet/).

# Q&A section General

## What is Keri?
Key Event Receipt Infrastructure; a secure identifier overlay for the internet.

## Why use Keri?
Because there is no secure universal trust layer for the internet, currently (2020).

## In what programming languages is Keri available?
In Python. It will be available in the coming year in Rust, Javascript and Go (2020).

##### Addition to point 1: example
Example image
<img src="./Images/FinalSolutionGW.png" alt="Final multisig solution" border="0" width="600">
<br/>

Example reference outside Keri github:

<small><i>[Answer provided in FullyNoded Q&A too](https://github.com/Fonta1n3/FullyNoded/blob/master/Docs/Q-and-A.md#question--gordian-wallet-there-is-no-add-manually-like-in-fullynoded) </i></small>

# Q&A section Keri operational
## Where can I download Keri?
On (sub)page(s of) [github](https://github.com/decentralized-identity/keri)
# Q&A section Userinterface
## What does Keri look like?
Currently `Keri` is just code, that can be tested and executed in a terminal on the command line. Private key management of KERI will look like wallets and Key Event Logs and Key Event Receipt Log are files with lots of encrypted stuff in there.

# Q&A section Root of trust
## What do I need to trust in Keri?
Primary root of trust is KEL not secondary  (starts with self cert ID but then after first rotation if any must have KEL)
# Q&A section Why the internet is broken
# Q&A section Identifiers
# Q&A section Event logs
# Q&A section Inconsistency and duplicity
# Q&A section Key rotation
# Q&A section KEL and KELR
# Q&A section Wallets
# Q&A section Signatures
# Q&A section Proofs
# Q&A section Private Key Management
# Q&A section Blockchain
## Does Keri use a blockchain?
No, but Keri uses the same cryptographical building blocks
## What's the difference between Keri and blockchain?
`Keri` is a unordered hash-linked list of signed Key Event logs and blockchain is a timestamped ordered list of hash-linked blocks of signed transactions. What this means:
1. we don't need ordering in `Keri` and that frees us from consensus protocols in blockchains
2. Hash-linking is done on a lower level in `Keri` and preserves consistency and fuels revealance of duplicity.
3. In `Keri` proofs are cryptographically derived from the root of trust, being the autonomous controller, in blockchains the root-of-trust is a transaction ledger.

# Q&A section Agencies

## W
# Q&A section Witness
# Q&A section Watchers