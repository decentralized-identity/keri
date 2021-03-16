# Q&A about KERI

[![hackmd-github-sync-badge](https://hackmd.io/iDVDsqwkTXm16B-cIlVhvg/badge)](https://hackmd.io/iDVDsqwkTXm16B-cIlVhvg)

<img src="../images/KERI_logo_color_on_white.png" alt="KERI logo" border="0" width="300">

This document is part one. Part two is [Q-and-A Security](./Q-and-A-Security.md). Both files shares a common [Glossary](./Glossary.md)

Why should you read or step through the Q&A? To get a different angle to the same topic: KERI.

### Critical stance welcomed, just don't try to rewrite history, nor be lazy
KERI receives three types of scrutiny from domain experts:
1. "KERI can't do it"
2. "KERI doesn't do something new"
3. "DID:XYZ has been designed, KERI needs to explain how it's different"
 - Ad 1. When respected colleagues think KERI can't keep up to its promises, we value the well-founded questions and suggestions of domain experts __after__ they thoroughly read the KERI [whitepaper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf). We'll happilly keep explaining KERI because we'd hate it when respected experts misunderstand the design.\
 - Ad 2. After a while some experts say 'well then KERI doesn't do something new'. That's acceptable for us, because we're able proof the design history of KERI and that it simply hasn't been done before.\
 - Ad 3. However, we can't accept having to explain the differences to people who just "invented" new, someting similar to KERI, using the same terms and thereby spreading confusion. Let the newbees benchmark themselves against KERI, we are too busy for those kind of things. By the way, this Q&A may be able to help you out! 

**The questions are of a varied level: basic and detailed. The answers are mostly directed towards generally interested people and newbies.**\
*Q = one star question. Novice to KERI, advanced in DIDs\
**Q = two star question. Proficient in DIDs and advanced in KERI\
***Q = three star question. Expert in DIDs and proficient in KERI

```
{TBW} means: to be written
{TBW prio 1} means to be written with the highest priority, 3 = no urgency, 2 = intermediate}
```
- [Q&A about KERI](#qa-about-KERI)
    + [Disclaimer](#disclaimer)
    + [List of questions and definitions](#list-of-questions-and-definitions)
  * [Knowledge you should be confidently applying](#knowledge-you-should-be-confidently-applying)
  * [Actions you should be comfortable with](#actions-you-should-be-comfortable-with)
- [Jump table to categories](#jump-table-to-categories)

Inspired by presentation given and questions asked on the [SSI webinar May 2020](https://ssimeetup.org/key-event-receipt-infrastructure-KERI-secure-identifier-overlay-internet-sam-smith-webinar-58/), but also issues raised and the progress made, here on Github (Turn on 'Watch' if you want to be notified of conversations).

Beware: A Q&A is always *work in progress*. Tips & help welcome.


### Disclaimer
None of the respondents in the **open** repo and presentations have been explicitly named as a source, except for ***Samuel M. Smith Ph.D.*** and ***@henkvancann***. If there is no reference added to the answers, then it's Samuel M. Smith who answered the question. Most of the editing is done by @henkvancann, which might have introduced ommission, errors, language glitches and such. Sorry for that, feel free to correct by submitting a pull request (PR).\
For practical reasons educational images uploaded by Github members have been downloaded. We de-personalised them by giving images a new name. Under these new names these images have been uploaded to github and used in the Q&A to clarify the questions and answers.

KERI's content is licensed under the [CC by SA 4.0. license](https://creativecommons.org/licenses/by-sa/4.0/). Parts of the video offered on SSI Meetup webinar 58 have been captured and uploaded to Github to support the answers to general questions about digital identity and more in depth answers to question about KERI.

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
      - [KERI Agreement Algorithm for Control Establishment](./Glossary.md#KERI-agreement-algorithm-for-control-establishment)
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
- Public private key pairs
- Hashing and hashes
- Signatures
- W3C DIDs
## Actions you should be comfortable with
- Amend knowledge and keep existing knowledge up to date
- create a key pair safely and back it up safely
- sweep to a new wallet

# Jump table to categories
## PART ONE
- [General](#qa-section-general)
- [Why the internet is broken](#qa-section-why-the-internet-is-broken)
- [KERI and DIDs](#qa-KERI-and-dids)
- [Wallets](#qa-section-wallets)
- [Signatures](#qa-section-signatures)
- [Proofs](#qa-section-proofs)
- [Private Key Management](#qa-section-private-key-management)
- [Blockchain](#qa-key-blockchain)
- [Root of trust](#qa-section-root-of-trust)
- [KERI operational](#qa-section-KERI-operational)
- [Agencies](#qa-key-agencies)
- [Virtual Credentials](#virtual-credentials)
## PART TWO
- [KERI operational security](./Q-and-A-Security.md#qa-section-KERI-operational-security)
- [Identifiers](./Q-and-A-Security.md#qa-section-identifiers)
- [Event logs](./Q-and-A-Security.md#qa-section-event-logs)
- [Inconsistency and duplicity](./Q-and-A-Security.md#qa-inconsistency-and-duplicity)
- [Key rotation](./Q-and-A-Security.md#qa-key-rotation)
- [KEL and KELR](./Q-and-A-Security.md#qa-section-kel-and-kerl)
- [Witness](./Q-and-A-Security.md#qa-section-Witness)
- [Watchers](./Q-and-A-Security.md#qa-section-watcher)
- [KERI and blockchain settled DIDs](./Q-and-A-Security.md#qa-KERI-and-blockchain-settled-dids)
- [Security Guarantees](./Q-and-A-Security.md#qa-security-guarantees)


# Q&A section General

## *Q: What is KERI?
Key Event Receipt Infrastructure; a secure identifier overlay for the internet.

## *Q: Why use KERI?
Because there is no secure universal trust layer for the internet, currently (2020).\
KEI is both privacy preserving and context-independent extensible. That means KERI is interoperable accross areas of application on the internet. It does so securely, with minimal sufficient means.\
_(@henkvancann)_

## *Q: What does KERI look like?
Currently `KERI` is just code, that can be tested and executed in a terminal on the command line. Private key management of KERI will look like `wallets`.\
Key Event Logs (`KEL`) and Key Event Receipt Log (`KERL`) are files with lots of encrypted stuff in there.\
_(@henkvancann)_

## *Q: How does KERI match DIDs?
There is a whole section to answer this simple question that has many-sided answers.

## **Q: Why do you reinvent blockchains and claim it's something new?
To begin with KERI has no blockchain, and doesn't depend on blockchains. If an implementation of KERI depends on blockchains at all, KERI operates blockchain agnostic.
Secondly KERI doesn't support a crypto currency. It doesn't need currency because it can easily connect to one, if needed. And again, KERI is crypto currency agnostic while doing so.
Lastly KERI is fundamentally different from blockchains like Ripple (Permissioned PBFT consensus) or Stellar (imcomplete open public, non-permissioned PBFT consensus): it doesn't need **total ordering**, timestamping and Proof of Authority consensus on transactions registered on a ledger.

It's comparing apples and oranges. But we're happy to do that exercise for the hard-to-convince part of the SSI community.

```
KERI is nothing like we already know of. It's a mixtures of things. 
You can't say _"Oh, KERI lays eggs, so it must be a reptile"_ It's not a reptile. 
And then you go _"I see, but it gives birth, so it must be a mammal"_. 
It's also not a mammal. It's KERI. 
It may have the characteristics you describe, but it's a species of its own.
(_SamMSmith_)

```
#### **Q: How can you get away with not complying to the security model (and guarantees) of an open public blockchain?
KERI better fits the Identity space. Doing away the total ordering in blockchains is a huge performance - and throughput gain, plus less worry about goverance. There's also not such a thing as consensus forks.
KERI solves (or _"gets away with"_ if you wish) this with duplicity detection. Watchers are all that matter. They garuantee that logs are immutable by one very simple rule: **"first seen wins"**.

There is a separate [Q&A Security](./Q-and-A-Security.md) to answer the extensive list of Security related questions.

## ***Q: Could we see a `WASM` module in the near future for Sidetree and DID:peer interoperability?
 WASM is certainly on the roadmap, but for the main issue of Sidetree and did:peer interop, see the [core KERI spec repo issue](https://github.com/decentralized-identity/KERI/issues/79) for more info.\
_(CharlesCunningham)_

## *Q: How does KERI match the `trust-over-ip` model and in the `W3C DID standardization`?
[Trust-over-IP](#trust-over-ip):
- Its goal is to be the missing authentication layer of the internet. That's a pretty well matching objective.
- Layer 1 (settlement layer): Where other `DID`s use blockchains or databases to register identities and settle 'transactions' between between, `DDO`s, and `VC`s, KERI uses homegrown native structures: `KEL` and `KERL`.
_(@henkvancann)_
- Layer 2 (communication layer): Non existing in KERI, because KERI is end-verifiable. KERI can use any other means of communication between actors in the ecosystem
- Layer 3 (transaction layer): Since KERI focuses on the more fundamental part of authentication for the internet, you won't find matching functionality for usual trust-over-IP transaction like VCs or money.
- Layer 4 (application layer): {TBW}
_(@henkvancann)_

[W3C DID](https://www.w3.org/TR/did-core/):
1. The KERI developers provisionally design DID:UN, which might become a mixture of DID:KEY, DID:PEER, and DID:WEB, combinable with more functional DIDs in the Identity spectrum DID:SOV, DID:ETHR, etc.
2. No verifiable credentials
_(@henkvancann)_

## *Q: Why use KERI?
Because there is no secure universal trust layer for the internet, currently (2020).

## *Q: What problem is KERI solving? How? And why can't it be solved by other solutions?
KERI solves the problem of **secure attribution to identifiers**. By ambient availability of verifiable Key event Logs that prove authoritive control over identifier's private keys. It can't be solved by onther solutions known so far because those solution have not managed to span identifier interoperability over the internet.
_(@henkvancann)_
{TBW prio 1}

## *Q: Who is KERI? Is it a company or a not for profit?
KERI sits under the *Decentralized Identity Foundation*, [DIF](https://identity.foundation), and within that in the *Identity and Discovery* Workgroup.
Due to its licensing structure, KERI isn't owned by anyone and everyone at the same time. The Intellectual Property Right of KERI is hosted with `DIF`. It is an open source project.

On github KERI is - and will become even more - a thickening bunch of repositories:
 1. https://github.com/decentralized-identity/KERI 
 2. https://github.com/decentralized-identity/KERIpy
 3. etc

 Lastly, the important man, who founded KERI is *Samuel M. Smith Ph.D.*, operationing from his firm [prosapien.com](https://www.prosapien.com).
 _(@henkvancann)_

## *Q: In what programming languages is KERI available?
In Python. It will be available in the coming year in Rust, Javascript and Go (2020).
_(@henkvancann)_

## *Q: How does KERI fit in [the 10 principles of SSI](https://medium.com/metadium/self-sovereign-identity-principle-6-portability-4a7105dd0381) by Christopher Allen?
KERI is not primarily about self-sovereign identity. KERI is primarily about autonomic identifiers, AIDs. That is: identifiers that are self managing. KERI provides proof of control authority over the identifier. What one does with the identifier is not constrained by KERI. But because the primary root of trust of an AID is a KEL which can be hosted by any infrastructure, any identity system (SSI or otherwise) built on top of KERI may also be portable.\
So in my opnion portability of the associated identifiers is essential to any truly self-sovereign identity system.\
(_SamMSmith_)

Where Christopher Allen is talking about *portability of information* related to the identity, in KERI we take this a step further with the *portability of the identifier itself* with respect to its supporting infrastructure (aka spanning layer).  Most `DID` methods do not have portable identifiers. They are locked to a given ledger.\
(_SamMSmith_)

## *Q: Does KERI cooperate with other projects in the self-sovereign Identity field?
Yes, KERI sits under the *Decentralized Identity Foundation*, [DIF](https://identity.foundation), and is part of the *Identity and Discovery* Workgroup. There are also non-formal relation with the newly launched trust-over-ip foundation, and there's good reasons to fit KERI into trust-over-ip.\
(_SamMSmith_)

## *Q: What's the difference between a `normative` and `non-normative` description or theory?
See the [definitions](#normative) section for what both terms mean. For example, theories of ethics are generally `normative` - you should not kill, you should help that person, etc. Economics is most commonly `non-normative` - instead of asking “how should this person choose which goods to buy?”, we are often more interested in “how does this person choose which commodities they buy?”.

## **Q: What's the difference between the KERI whitepaper and the KIDs
The [whitepaper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf) is the historically grown and expanded design document of `KERI`.

A [KID](../kids) is focussed on Implementation; "this is how we do it"  We add commentary to the indivudual KIDs that elaborate on the why. It has been split from the _how_ to not bother implementors with the _why_.

## *Q: KERI has invented its own key representation and signature format. Why not conforn to current standards already available?
{TBW prio 1}

## *Q: In the KERI system design trade space you strike out features, so you must have stroked out application space too; which?
<img src="../images/trade-space-limitations.png" alt="trade-space-limitations" border="0" width="300">
{TBW prio 2}

## *Q: Are smart contracts possible with KERI?
Yes, KERI gives you the security. And by supplying secure state machines. But you have to gather the right transactions yourself.

Ledgers co-mingle secure state machines into one another, Ledger are total ordering. We don’t need totla ordering in KERI. The absence of a ledger  gives us the ability to create totally private smart contracts between Bob and Alice.

You use the KERI Duplicity detection to determine the authoritive key is used at a certain point in time. 

Since March 2021 KERI is a seperate DIF working group and it would possible to create a dedicated project within the working group to research smart contracting with KERI.
_(@henkvancann)_

# Q&A section Why the internet is broken

## *Q: Why would the internet be broken?
The Internet Protocol (IP) is broken because it has no security layer.\
<img src="../images/internet_broken.png" alt="Internet stack shows omissions" border="0" width="500">
(_SamMSmith_)

## **Q How can the internet be fixed?
Establish authenticity between the key pair and the identifier of IP packet’s message payload. [See more](https://ssimeetup.org/key-event-receipt-infrastructure-KERI-secure-identifier-overlay-internet-sam-smith-webinar-58/) in presentation.

<img src="../images/identity_system_security_overlay.png" alt="identity system security overlay" border="0" width="800">
(_SamMSmith_)

## *Q: What's wrong with SSL certificate intermediairies?
Administrative Identifier Issuance and Binding; especially the binding between keypair and identifier based on an assertion of an intermediairy administrator. This is what's weak and therefore wrong. [See more](https://ssimeetup.org/key-event-receipt-infrastructure-KERI-secure-identifier-overlay-internet-sam-smith-webinar-58/) in presentation.\
_(@henkvancann)_

## **Q: What's DNS Hijacking
A DNS hijacking wave is targeting companies at an almost unprecedented scale. Clever trick allows attackers to obtain valid TLS certificate for hijacked domains. [more](https://arstechnica.com/information-technology/2019/01/a-dns-hijacking-wave-is-targeting-companies-at-an-almost-unprecedented-scale/).\
_(@henkvancann)_

## *Q: What is 'platform locked trust' and why should we bother?
The `IPv4 layer` was become a standard internet transport layers over the years. It is a very strong structure. The transport layer has no security build into it. So the trust layer has to be something higher in the stack. However in the Support Application layers that sit on top of that IPv4, no standardization has taken place yet. It is a highly segmented layer and trust is therefore *locked* in those segments or platforms; it's not interoperable accross the internet. E.g. platform `Facebook` provides an identity system that only works within their domain. That's the same with for example `Google` or any number of blockchain.\
We don't have a trustable interoperability. And that leads to the idea that the internet is broken. We want to fix that, we don't want a domain segmented internet trust map, a bifurcated internet, we want to have a single trust map. This is the motivation for `KERI`.\
(_SamMSmith_)

## *Q: How to repair the internet trust layer?
With a waist and a neck. <img src="../images/platform_locked_trust.png" alt="Platform locked trust" border="0" width="400" style="float:left"><img src="../images/waist_neck.png" alt="Waist and neck" border="0" width="400" style="float:right">
_(@henkvancann)_

## *Q: What role does KERI play in the suggested "repair of the internet"?
Much of the operation of internet infrastructure is inherently decentralized, but control over the value transported across this infrastructure may be much less so.\
Centralized value capture systems concentrate value and power and thereby provide both strong temptations for malicious administrators to wield that concentrated power to extract value from participants. \
We believe that _decentralization of value transfer_ is essential to building trust. Consequently a key compo- nent for a decentralized foundation of trust is an interoperable decentralized identity system. [Source: whitepaper page 7](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf)

# Q&A section KERI and DIDs

## **Q: Is KERI a DID?
`KERI` is not a `DID` method. The proposed related `DID` method is [`did:un`](https://github.com/decentralized-identity/KERI/blob/master/did_methods/un.md). A session at the recent **IIW31** presented by Jolocom’s *Charles Chunningham* examines overlap between data models of DID documents and `KERI` identifiers [here](https://jolocom.io/blog/as-seen-at-iiw31-KERI/).\
However there are also votes for `did:KERI`: _Drummond Reed_ (Dec 2 2020): "at IIW we asked that question and  feedback overwhelmingly favored did:KERI. Furthermore, I’ve proposed that the KERI namespace be reserved within the method-specific ID spaces of other DID methods as well, The Indy community has agreed to reserve the KERI namespace in the Indy DID method."\
_(@henkvancann)_

## **Q: Some say that with KERI, a DID can be reduced to did:\<identifier>. But that’s not a valid DID?!
_Every DID must have a method name component before the method-specific ID._

The first paper mentioning the absence of the method is [Thinking of DID? KERI On](https://humancolossus.foundation/blog/thinking-of-did-KERI-on) by The Human Colossus Foundation, written by Robert Mitwicki. He addressed the concern in the question (the invalidity of the DID method) and made it more clear what the Foundation meant by that: "We look into the future and with that view we think that namespace could be dropped and we could keep only identifier, as the namespace seems to be one of the major drawbacks of decentralized identifiers at the moment. In my opinion `did:KERI:<identifiers>`  would be just intermediate step as the issue addressed by post would still hold. We see that KERI could be a major upgraded for DID; not replacement."

## **Q: Isn't it a bit arrogant of KERI to say "my new DID method is so good that it can replace all others for all eternity"?

_But by doing that you will also exclude a lot of existing identifier infrastructure._

I am not denying existence of existing DID infrastructure, but I agree a lot of them could be obsolete if we introduce KERI. A lot of business models which are build upon current model would be obsolete. I understand that a lot of people would not like that, but that is called progress.\
_(RobertMitwicki)_
# Q&A section Wallets

## *Q: Why do I need a wallet for KERI?
Yes. [Universal wallet](https://w3c-ccg.github.io/universal-wallet-interop-spec/) - would do - with a thin layer on top of it. \
A wallet needs to be adapted to KERI to be able to carry KERI identifiers.\
{TBW}\
(_SamMSmith_) / _(CharlesCunningham)_
## *Q: How can I backup the KERI identifiers in my wallet?
{TBW}
## Can I receive crypto money in my KERI wallet?
We don't need a crypto currency embedded in the KERI system, we can use any other crypto currency system for payment. So the design of the KERI system has left crypto token control out.\
_(@henkvancann)_

## *Q: Does a KERI wallet store virtual credentials connect to my identifiers?
The KERI whitepaper has little about virtual credentials and KERI's place in the W3C SSI space for DIDs and VCs. The reason is that KERI is mainly a level 1 and level 2 solution in the trust-over-ip framework.\
_(@henkvancann)_

In this presenation of Sam, there's a lot about the relation between KERI and VCs: https://github.com/SmithSamuelM/Papers/blob/master/presentations/GLEIF_with_KERI.web.pdf
# Q&A section Signatures

## **Q: Who can sign off my proofs and identifiers using KERI?
Depends on what you mean with proof. KERI is content agnostic, so any cryptographic proof can be referenced and signed in a KEL, even a third party signature. As far as KERI-internal proofs are concerned a subject-controller, a delegated controller and combination of (fractioned) multi-signatures can prove authoritative conrol over a key and over a pre-rotated key.
_(@henkvancann)_
{TBW prio 1}

## *Q: What is the practical use of signatures?
In general they can proof the control of a private key at a certain point back in time.
_(@henkvancann)_

## **Q: Do verifiers, validators, witnesses and watchers all sign off `payloads`?
Yes they do. For every cause there is a different payload. The main reason why all roles sign off cryptographical references is commitment to those sources (the payload in KERI is often a digest of sources) at a certain point in time.\
_(@henkvancann)_

# Q&A section Proofs

## *Q: What does KERI proof?
KERI has the ability to proof various things:
 - Control over an Autonomous identifier (`AID`).
 - Control over a pre-rotated key
 - Commitment to an Event Log
 - Content addressing by a hash
 - Delegation of control over a key
 - {TBW prio 2}

## *Q: Does KERI know whether any message in the Event Logs are valid or true?
No, KERI is data-agnostic. KERI does make no statement about the validity of the payload data.\
_(@henkvancann)_

## *Q: How can we verify that a statement by a controller is valid?
We may verify that the controller of a private key, made a statement but not the `validity` of the statement itself.\
(_SamMSmith_)
## *Q: How can we trust what was said or written?
We may build trust over time in what was said via histories of verifiably attributable (to whom) consistent statements, i.e. `reputation`.\
(_SamMSmith_)

## **Q: Do I need to show the full log (KEL) to anybody I transact with, even though I'd only like to show a part of it, for example a virtual credential?
Yes, because they can't verify the root of trust. They have to have access to the full log at some point in time. Once they verfied to the root of trust, once, they don't have to keep a copy of the full log. They have to keep the event they've seen and any event since, that they need to verify as they go.
(_SamMSmith_)

## **Q: What's the difference between interactive - and non-interactive proof (for example proof of Authentication)
Interactive proof of authentication requires both parties interacting, it uses bandwidth, I can't batch the interactions either. So it's not scalable.

Non-interactive proof of authentication -> digital signature with publ. private key-air.
Non-interactive has huge advantages for scalability. 

The weakness is of non-interactive proving is replay attack ( the interactive method has built-in mechanism to prevent replay attacks )
Replay attack is some adversary is replaying a request for access in your name after having gained access to your private keys.
Solution to replay attack is both `Uniqueness` and `Timeliness`.

#### Uniqueness
Uniqueness works with a nonce, that's being obtained by a challenge-response mechanism and the requester has to use that nonce to seal the request. 

#### Timeliness
Timeliness is even better because it can service both properties needed in one go. If we use a Date-time-stamp (monotonic) in time window we can be sure that the sender request is unique and has been established in an acceptable timeframe.

So therefore the non-interactive mechanism to replay attack prevention has been suggested in KERI implemented by Date-time-stamp (monotonic).\
The time window can be fairly large because you use monotonicity. 

# Q&A section Private Key Management

## **Q: How multi-tasking is the key infrastructure?
KERI has `univalent`, `bivalent` and `multivalent` infrastructures.\
<img src="../images/key-infra-valence.png" alt="Key Infrastruction Valence levels" border="0" width="600">
You need Key-pair Generation and Key-Event-Signing Infrastructure. And KERI doesn't care how you do it.\
From `bivalent` delegation {fill out?!} comes into play. But in fact you can have `multivalent` infrastructures, all with their own security garantuees and its own key management policies.\
It's all one KERI codebase to do all these infrastructures.\
(_SamMSmith_)

## *Q: Does your public-private-key format matter in KERI?
No, because the derivation code allows you to use whichever format you want. So anyone that sees an identifier looks at the first byte or two bytes prepended, it's a derived code, and you can tell exactly what type of public-private-key format we have, e.g. ecdsa.

When you rotate keys, you can always rotate to a different format.

## *Q: Can I use BIP32 Hierarchical deterministic keys in KERI to rotate?
Yes, you can derive your keys from that scheme. But KERI is agnostic about it, it wouldn't know.

## *Q: Not your keys, not your identity?
In KERI we say _identifier_, because **identity** is a loaded term, lots of misunderstanding around it.\
Pre rotated keys are best practise to keep control of your identifiers. \
If you lose unique control of a key right after inception, before rotation, are there no garantuees to be given for KERLs via witnesses / watchers or whatever. Is the only thing you can do about it, is revoke the key in that case?}\
_(@henkvancann)_

## *Q: A wallet is there to store my KERI private keys safely, no?
Currently _Universal wallet_ is aimed at to store KERI keys. The vast majority of security breaches or exposures of keys are originated by the behaviour of people: the way they use wallets. Most rarely due to errors in the wallet software.
{TBW prio 1}

## **Q: Are compound private keys (Shamir Secret Sharing) and multisignature schemes possible to incept identifiers?
Yes, complex fractional structures are natively possible in KERI. However only for the non-basic forms (for transferable identifiers).\
_(@henkvancann)_
{TBW prio 1}

## **Q: How to delegate control over my private keys that control my identifiers?
{TBW prio 3}

# Q&A section Blockchain

## *Q: Does KERI use a blockchain?
No, but KERI uses the same cryptographical building blocks as blockchains do. \
_(@henkvancann)_ \
However, KERI may be augmented with distributed consensus ledgers but does not require them. [Source: section conclusion in whitepaper](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf)


## **Q: What's the difference between KERI and blockchain?
`KERI` is a unordered hash-linked list of signed Key Event logs and blockchain is a timestamped ordered list of hash-linked blocks of signed transactions. What this means:
1. we don't need ordering in `KERI` and that frees us from consensus protocols in blockchains
2. Hash-linking is done on a lower level in `KERI` and preserves consistency and fuels revealance of duplicity.
3. In `KERI` proofs are cryptographically derived from the root of trust, being the autonomous controller, in blockchains the root-of-trust is a transaction on a ledger; that means the Identifier gets locked on the ledger.\
_(@henkvancann)_

## **Q: Why not register identities on an open public ledger like bitcoin, ethereum or soverin?
Because for our purposes we don't need to. Consider two distinct identifier to totally ordered, distributed consensus ledger:
1. the access identifier that allows you to access the ledger. This one is ussually a `SCI`. E.g. on bitcoin your bitcoin address is cryptographically derived from the public key from your keypair.
2. the register identifier that allows you to register an identifier on the ledger. The ledger transaction is validated registering of your identifier, not the cryptographic root-of-trust that the access identifier is using.

The identifier is now locked to that ledger. We want identifiers to be portable accross ledgers, so we don't want to use registration as the root-of-trust, we want to be self-certified all the way.
(_SamMSmith_)

## **Q: KERI is basically a series of Pay2PublicKeyHash transactions?
_that you send to witnesses, who observe them and attest to the particular line of operations they see?_

**In brief: for KERI that is an apples and oranges comparison.**

Because total linear ordering is not needed for a given identifier's event sequencing. Only linear order of that identifier's history. The history's from other events do not have to be ordered with respect to each other. So the secure ordering of a given identifier's history is a completely different class of problem than the secure total ordering of comingled history from multiple identifiers. The security demands are less for the former case. So the equivalent security may be obtained in other ways. While the latter as a side effect of total ordering gives local ordering (per identifier) for free. But securing total ordering may be much harder to do. So one has to be careful, because it's no longer an apples to apples comparison. 
(_SamMSmith_)

# Q&A section Root of trust

## **Q: What do I need to trust in KERI?
Primary root of trust is KEL not secondary (starts with self cert ID), but then after the first rotation, if any, you must have a KEL.\
(_SamMSmith_)

### **Q: What is the difference between a trust basis and a trust domain?
A trust basis binds controllers, identifiers, and key-pairs.\
A trust domain is the ecosystem of interactions that rely on a trust basis.

## ***Q: KERI does not need a blockchain, but how does it establish the root-of-trust that we need for SSI? How does the data persist?
The `KELs` are what establishes the root of trust in `KERI`. So you have a `SCI` and a `KEL`. The `KEL` is ordered with respect to the SCI by the controller. You don't need total ordering with respect to other identifiers to establish the root of trust in `KERI`, because the controller is the one and only, who orders events.\
In blockchains you have total ordering, which you need for double spend protecting in cryptocurrencies, but not in `KERI`.\
For people in blockchain this is a bit hard to grasp, but we don’t need hash chained data structure of events on single identifier nor the *ordering* those, I just need logs, I need *append-only logs of events* to establish the authority.\
And so I defend myself against `duplicity`.\
(_SamMSmith_)

## **Q: Why is end-verifiability such a big thing in KERI?
**In brief: with end-verifiability anyone can verify anywhere at anytime, without the need to trust anyone or anything in between.**

Because any copy of an `end-verifiable` record or log is sufficient, any infrastructure providing a copy is replaceable by any other infrastructure that provides a copy, that is, any infrastructure may do. Therefore the infrastructure used to maintain a log of transfer statements is merely a `secondary root-of-trust` for control establishment over the identifier. This enables the use of ambient infrastructure to provide a copy of the log. The _combination_ of end verifiable logs served by ambient infrastructure _enables_ ambient verifiability, that is, anyone can verify anywhere at anytime. This approach exhibits some of the features of certificate transparency and key transparency with end-verifiable event logs but differs in that each identifier has its own chain of events that are rooted in a self-certifying identifier.

# Q&A section KERI operational

## *Q: Where can I download KERI?
On (sub)page(s of) [github](https://github.com/decentralized-identity/KERI).

## *Q: Where can we find the code and how could a coder get started?
The homepage on github [README.md](../README.md) pretty much sums up all the possibilities to download the available code and how developers can currently engage in the development process. We welcome all help we can get.

## *Q: What would you see as the main drawback of KERI?
- Its main drawback is that it's nascent. (_SamMSmith_)\
- The field of cryptography is already complex by itself. KERI's extended complexity, combined with totally new terms and new process description make it a steep learning curve. It depends on your individual drive to want to know about KERI, to what extent the effort pays off. Maybe first try:
    1. [KERI made easy](./KERI-made-easy.md)
    2. The general [KERI Q&A](./Q-and-A.md)
    _(@henkvancann)_
- KERI is inventing its own lowest level building blocks. That will prevent a lot of potential code reuse. (@OR13)

## *Q: Where you would need something quite different than KERI?
`KERI` does one thing, it establishes control authority using verifiable portable proofs that are `KEL`s.\
(_SamMSmith_)

## *Q: How does KERI scale
`KEL`, `KERL` and `KAACE` might well be very lean alternatives to blockchain based solutions. The hard part is the ambient verifiable architecture.\
 _(@henkvancann)_

## *Q: Is KERI post-quantum secure?
**In brief: yes, pre-rotation with hashed public keys and strong one-way hash functions are post-quantum secure.**

Post-quantum cryptography deals with techniques that maintain their cryptographic strength despite attack from quantum computers. Because it is currently assumed that practical quantum computers do not yet exist, _post_-quantum techniques are forward looking to some future time when they do exist. A one-way function that is post- quantum secure will not be any less secure (resistant to inversion) in the event that practical quantum computers suddenly or unexpectedly become available. One class of post-quantum secure one-way functions are some cryptographic strength hashes. The analysis of D.J. Bernstein with regards the collision resistance of cryptographic one-way hashing functions concludes that quantum computation provides no advantage over non-quantum techniques.\
Strong one-way hash functions, such as 256 bit (32 byte) Blake2, Blake3 and SHA3, with 128 bits of pre-quantum strength maintain that strength post-quantum.\
[Source: whitepaper page 65](https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/KERI_WP_2.x.web.pdf)


## *Q: What happens if I or other people are offline?
Any controller can install a Service/Agent Log, controlled by them.

## *Q: How to handle multiple formats of KEL and KERL through time. Will they be backwards compatible?
{TBW prio 2}
## *Q: How to bootstrap KERI on the internet? Is it like fax machine; the more KELs there are, the more effective it is?
Any subject / controller can start creating KERI events in a KERI event log. Dependent of the objectives a controller has with KERI a more peer-to-peer (one-to-one) approach or contrary to that a one to many approach. In the latter case a set of witnesses and their services can emerge per controller. Subsequently one or more verifiers (and their watchers) can also enter the play.
The more entities are getting used to play the different KERI specific roles the more rapid and easy will the bootstrapping / flooding of KERI on the internet evolve.
{TBW prio 1}


## *Q: Is there a KERI course or webinar available?
The [SSI Meetup](https://ssimeetup.org/key-event-receipt-infrastructure-KERI-secure-identifier-overlay-internet-sam-smith-webinar-58/) webinar on KERI took place in May 2020 and is a good lesson and source of information.\
There is lots of course material available on [prosapien.com](https://www.prosapien.com).\
_(@henkvancann)_

## *Q: Could KERI work for edge computers that need self sovereign identity? How to (selectively) share control over the `SCI`/`SAI` with the owners of the device?
Delegation could be used. There is an [issue about IoT](https://github.com/decentralized-identity/KERI/issues/54) key and identifier management with `KERI` that answers this question profoundly.\
(_SamMSmith_)


# Q&A section Agencies

## **Q: What does the governance framework of KERI look like?
> Decentralized systems must coordinate across multiple parties, all acting independently in their own self-interest. This means that the rules of engagement and interaction must be spelled out and agreed to ahead of time, with incentives, disincentives, consequences, processes, and procedures made clear.
{TBW prio 3}
DRAFT BY _(@henkvancann)_

KERI is self-administered, self-governed. What aspects of KERI need governance?

Purist permissionless network proponents will argue that a real decentralized network does not need a governance framework since mathematics and cryptography make sure that proper governance is in place.

The Trust over IP stack includes both a governance stack and technology stack.
#### KERI governance roles at *Layer 1* can include: 
- Controller, Entropy hardware and software, KEL, KERL
#### Layer 2: Provider governance frameworks
- Governance of capabilities of digital wallets, agents, and agencies. So the need is primarily to establish baseline security, privacy, and data protection requirements, plus interoperability testing and certification programs, for the following roles:
- Hardware Developers: hardware security modules (HSMs)
- Software Developers: duplicity verification and internal consistency checks
- Agency: ambient availability of KELs and KERLs
#### Layer 3: Credential governance frameworks
KERI is not an outspoken credential issuance and verification framework. Having said that:
- Controller: inception proof, revocation, delegation proof
- Holders: availability
- Verfifier: external inconsistency proofs
#### Layer 4: Ecosystem governance framework
- KERIs objective  is to be the spanning trust infrastructure of the whole internet
- Portability of the identities and KERI interoperability between platforms is cryptographically secured
- Inconsistencies "reported" by meercats-like alert governance system

## **Q: How can KERI offer consistent services and truth?
A. In a pair-wise setting  each party only needs to be consistent with the other party. Witnesses are not used. It doesn't matter if they lie to each other as long as they lie consistently. KERI does not
enable someone to proof the *veracity* of a statement only the *authenticity* of the statement.\
(_SamMSmith_)

B. If 3 parties are involved in a transaction all they need do is query each other for the copy of the `KEL` that each is using for each other to ensure that there is no duplicity.\
(_SamMSmith_)

C. To **guarantee *undetectable* duplicity** requires a successful eclipse attack* on all the parties. `KERI` merely requires that there be sufficient duplicity detection in the ecosystem. \
This would be a set of `watchers` that the validators trust that record any and all copies of key event logs (`KEL`) that they see.  Because these `watchers` can be anyone and anywhere, any controller of a public identifier is at peril should they choose to publish inconsistent copies of their `KEL`. This removes the incentive to be duplicitous.\
'* Any blockchain system is also vulnerable to such an eclipse attack.\
(_SamMSmith_)

# Q&A Virtual Credentials

## *Q: Why doesn't KERI use certification as a root of trust?
Why do we want portable identifiers instead of the Ledger Locked IDs, since we have DIDs that can resolve a ledger locked Id uniformly? You say “We don’t want to use certification as a root of trust, we want to do it self-certified all the way” -> what about the issuance of a credential based on the ledger locking, isn’t that beneficial?

## *Q: Is Custodianship of KERI identifiers possible? 
_Or does (Delegated, Multi-sig) Self-Adressing do the job?_
{TBW Prio 2}